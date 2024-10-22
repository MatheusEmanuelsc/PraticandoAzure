# Integração de Tabelas no Azure Storage Account em um Projeto .NET

## Índice
- [Introdução](#introdução)
- [Configurações no `appsettings.json`](#configurações-no-appsettingsjson)
- [Chaves de Acesso no Azure](#chaves-de-acesso-no-azure)
- [Pacotes Necessários](#pacotes-necessários)
- [Controller com Métodos para Gerenciar Tabelas](#controller-com-métodos-para-gerenciar-tabelas)
  - [Inserir Registro na Tabela](#inserir-registro-na-tabela)
  - [Obter Registro da Tabela](#obter-registro-da-tabela)
  - [Listar Registros da Tabela](#listar-registros-da-tabela)
  - [Deletar Registro da Tabela](#deletar-registro-da-tabela)
- [Conclusão](#conclusão)

---

## Introdução

Neste tutorial, vamos explicar como configurar e utilizar **Tabelas** em uma **Conta de Armazenamento** do Azure em um projeto .NET, utilizando chaves de acesso e gerenciando dados de forma semelhante ao exemplo com blobs. Aqui, você aprenderá a criar, inserir, consultar e deletar dados nas tabelas do Azure.

---

## Configurações no `appsettings.json`

No arquivo `appsettings.json`, você precisará adicionar as configurações relacionadas à **Conta de Armazenamento** e à **Tabela** que será utilizada.

### Exemplo de Configuração

```json
{
  "AzureStorage": {
    "AccountName": "nome-da-sua-conta",
    "AccountKey": "chave-de-acesso-da-sua-conta",
    "TableName": "nome-da-sua-tabela",
    "TableServiceEndpoint": "https://nome-da-sua-conta.table.core.windows.net/"
  }
}
```

---

## Chaves de Acesso no Azure

1. Acesse o **Portal do Azure** e vá até a sua **Conta de Armazenamento**.
2. No painel à esquerda, clique em **Chaves de Acesso**.
3. Copie a **chave de acesso** que será utilizada no `appsettings.json`.
4. Confirme o **nome da tabela** que você criou ou deseja utilizar.

---

## Pacotes Necessários

Para integrar o **Azure Table Storage** no seu projeto, instale o pacote NuGet:

```bash
dotnet add package Azure.Data.Tables
```

Esse pacote é utilizado para interagir com o armazenamento de tabelas no Azure.

---

## Controller com Métodos para Gerenciar Tabelas

Vamos criar um **Controller** chamado `TableController` com os métodos para manipulação dos dados em uma tabela no **Azure Table Storage**.

### Exemplo de `TableController`

```csharp
using Azure;
using Azure.Data.Tables;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using System;
using System.Collections.Generic;
using System.Threading.Tasks;

[ApiController]
[Route("api/[controller]")]
public class TableController : ControllerBase
{
    private readonly TableClient _tableClient;

    public TableController(IConfiguration configuration)
    {
        var tableServiceEndpoint = configuration.GetSection("AzureStorage:TableServiceEndpoint").Value;
        var accountName = configuration.GetSection("AzureStorage:AccountName").Value;
        var accountKey = configuration.GetSection("AzureStorage:AccountKey").Value;
        var tableName = configuration.GetSection("AzureStorage:TableName").Value;

        var credential = new TableSharedKeyCredential(accountName, accountKey);
        _tableClient = new TableClient(new Uri(tableServiceEndpoint), tableName, credential);
    }

    // Inserir Registro na Tabela
    [HttpPost("insert")]
    public async Task<IActionResult> InsertEntity([FromBody] MyEntity entity)
    {
        await _tableClient.CreateIfNotExistsAsync();
        await _tableClient.AddEntityAsync(entity);
        return Ok(new { message = "Registro inserido com sucesso" });
    }

    // Obter Registro da Tabela
    [HttpGet("get/{partitionKey}/{rowKey}")]
    public async Task<IActionResult> GetEntity(string partitionKey, string rowKey)
    {
        try
        {
            var entity = await _tableClient.GetEntityAsync<MyEntity>(partitionKey, rowKey);
            return Ok(entity.Value);
        }
        catch (RequestFailedException)
        {
            return NotFound(new { message = "Registro não encontrado" });
        }
    }

    // Listar Registros da Tabela
    [HttpGet("list")]
    public async Task<IActionResult> ListEntities()
    {
        var entities = new List<MyEntity>();

        await foreach (var entity in _tableClient.QueryAsync<MyEntity>())
        {
            entities.Add(entity);
        }

        return Ok(entities);
    }

    // Deletar Registro da Tabela
    [HttpDelete("delete/{partitionKey}/{rowKey}")]
    public async Task<IActionResult> DeleteEntity(string partitionKey, string rowKey)
    {
        await _tableClient.DeleteEntityAsync(partitionKey, rowKey);
        return Ok(new { message = "Registro deletado com sucesso" });
    }
}

// Classe de Entidade
public class MyEntity : ITableEntity
{
    public string PartitionKey { get; set; }
    public string RowKey { get; set; }
    public DateTimeOffset? Timestamp { get; set; }
    public ETag ETag { get; set; }

    // Propriedades adicionais
    public string Nome { get; set; }
    public int Idade { get; set; }
}
```

### Explicação dos Métodos

#### Inserir Registro na Tabela
- Recebe um objeto da classe `MyEntity`, que representa um registro na tabela.
- Cria a tabela, caso ela não exista, e insere o registro.

#### Obter Registro da Tabela
- Busca um registro específico na tabela com base nas chaves de partição (`partitionKey`) e de linha (`rowKey`).
- Retorna o registro encontrado ou uma mensagem de erro caso não encontre.

#### Listar Registros da Tabela
- Lista todos os registros presentes na tabela e retorna uma lista de objetos da entidade.

#### Deletar Registro da Tabela
- Deleta um registro específico com base nas chaves de partição e de linha.

---

## Conclusão

Com esses passos, você agora tem um **Controller** funcional para interagir com o **Azure Table Storage**, permitindo inserir, buscar, listar e deletar registros na tabela. Esta solução é ideal para cenários em que você precisa de um armazenamento eficiente para dados estruturados no Azure.