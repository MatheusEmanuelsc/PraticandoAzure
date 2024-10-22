# Integração de Conta de Armazenamento Azure em um Projeto .NET

## Índice
- [Introdução](#introdução)
- [Configurações no `appsettings.json`](#configurações-no-appsettingsjson)
- [Chaves de Acesso no Azure](#chaves-de-acesso-no-azure)
- [Pacotes Necessários](#pacotes-necessários)
- [Controller com Métodos de Upload, Download, Listar e Deletar Arquivos](#controller-com-métodos-de-upload-download-listar-e-deletar-arquivos)
  - [Upload de Arquivo](#upload-de-arquivo)
  - [Download de Arquivo](#download-de-arquivo)
  - [Listar Arquivos](#listar-arquivos)
  - [Deletar Arquivo](#deletar-arquivo)
- [Conclusão](#conclusão)

---

## Introdução

Este tutorial irá guiá-lo na integração de uma **Conta de Armazenamento** do Azure em um projeto .NET, além de configurar o `appsettings.json` e criar um **Controller** com métodos para **upload**, **download**, **listagem** e **deleção de arquivos**.

---

## Configurações no `appsettings.json`

Após criar o projeto no Visual Studio, adicione as configurações da **Conta de Armazenamento** e do **Contêiner** no arquivo `appsettings.json`.

### Exemplo de Configuração

```json
{
  "AzureStorage": {
    "AccountName": "nome-da-sua-conta",
    "AccountKey": "chave-de-acesso-da-sua-conta",
    "ContainerName": "nome-do-seu-conteiner",
    "BlobServiceEndpoint": "https://nome-da-sua-conta.blob.core.windows.net/"
  }
}
```

---

## Chaves de Acesso no Azure

1. Acesse o **Portal do Azure** e vá até a sua **Conta de Armazenamento**.
2. No painel à esquerda, clique em **Chaves de Acesso**.
3. Copie a **chave de acesso** que será utilizada no `appsettings.json`.
4. Confirme o **nome do contêiner** que você criou para garantir que ele seja referenciado corretamente.

---

## Pacotes Necessários

Para integrar o Azure Blob Storage no seu projeto, instale os seguintes pacotes NuGet:

```bash
dotnet add package Azure.Storage.Blobs
dotnet add package Microsoft.Extensions.Configuration
```

Esses pacotes permitirão o gerenciamento de blobs e o acesso às configurações do projeto.

---

## Controller com Métodos de Upload, Download, Listar e Deletar Arquivos

Vamos criar um **Controller** chamado `BlobController` com os métodos para manipulação dos arquivos no Azure Blob Storage.

### Exemplo de `BlobController`

```csharp
using Azure.Storage.Blobs;
using Azure.Storage.Blobs.Models;
using Microsoft.AspNetCore.Mvc;
using Microsoft.Extensions.Configuration;
using System.IO;
using System.Threading.Tasks;

[ApiController]
[Route("api/[controller]")]
public class BlobController : ControllerBase
{
    private readonly BlobServiceClient _blobServiceClient;
    private readonly string _containerName;

    public BlobController(IConfiguration configuration)
    {
        var blobConnectionString = configuration.GetSection("AzureStorage:BlobServiceEndpoint").Value;
        var accountName = configuration.GetSection("AzureStorage:AccountName").Value;
        var accountKey = configuration.GetSection("AzureStorage:AccountKey").Value;

        _blobServiceClient = new BlobServiceClient(blobConnectionString);
        _containerName = configuration.GetSection("AzureStorage:ContainerName").Value;
    }

    // Upload de Arquivo
    [HttpPost("upload")]
    public async Task<IActionResult> UploadFile(IFormFile file)
    {
        var containerClient = _blobServiceClient.GetBlobContainerClient(_containerName);
        var blobClient = containerClient.GetBlobClient(file.FileName);

        using (var stream = file.OpenReadStream())
        {
            await blobClient.UploadAsync(stream, true);
        }

        return Ok(new { message = "Upload realizado com sucesso" });
    }

    // Download de Arquivo
    [HttpGet("download/{fileName}")]
    public async Task<IActionResult> DownloadFile(string fileName)
    {
        var containerClient = _blobServiceClient.GetBlobContainerClient(_containerName);
        var blobClient = containerClient.GetBlobClient(fileName);

        var download = await blobClient.DownloadAsync();
        return File(download.Value.Content, download.Value.ContentType, fileName);
    }

    // Listar Arquivos
    [HttpGet("list")]
    public async Task<IActionResult> ListFiles()
    {
        var containerClient = _blobServiceClient.GetBlobContainerClient(_containerName);
        var blobs = containerClient.GetBlobsAsync();
        var fileList = new List<string>();

        await foreach (var blob in blobs)
        {
            fileList.Add(blob.Name);
        }

        return Ok(fileList);
    }

    // Deletar Arquivo
    [HttpDelete("delete/{fileName}")]
    public async Task<IActionResult> DeleteFile(string fileName)
    {
        var containerClient = _blobServiceClient.GetBlobContainerClient(_containerName);
        var blobClient = containerClient.GetBlobClient(fileName);

        await blobClient.DeleteIfExistsAsync();
        return Ok(new { message = "Arquivo deletado com sucesso" });
    }
}
```

### Explicação dos Métodos

#### Upload de Arquivo
- Recebe um arquivo via `IFormFile`.
- Cria um `BlobClient` e faz o upload do arquivo para o contêiner.

#### Download de Arquivo
- Busca um arquivo pelo nome no contêiner e retorna o arquivo para o cliente.

#### Listar Arquivos
- Lista todos os blobs (arquivos) dentro do contêiner e retorna os nomes dos arquivos.

#### Deletar Arquivo
- Recebe o nome do arquivo como parâmetro, busca no contêiner e o deleta.

---

## Conclusão

Com essas etapas, você agora possui uma integração funcional com o **Azure Blob Storage** em seu projeto .NET, incluindo a capacidade de fazer upload, download, listar e deletar arquivos.