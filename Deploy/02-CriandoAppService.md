### Resumo: Como Hospedar uma Aplicação ASP.NET no Azure com SQL Server

Este resumo explica como hospedar uma aplicação ASP.NET no Azure, configurar o banco de dados SQL, gerenciar cadeias de conexão e realizar o deploy da aplicação utilizando o Visual Studio e Visual Studio Code, seguindo as práticas recomendadas.

#### Índice

1. [Criando o Serviço de Aplicativos no Azure](#criando-o-serviço-de-aplicativos-no-azure)
2. [Configurando o Banco de Dados SQL no Azure](#configurando-o-banco-de-dados-sql-no-azure)
3. [Configurando a Cadeia de Conexão](#configurando-a-cadeia-de-conexão)
4. [Publicando o Código](#publicando-o-código)
5. [Deploy via Visual Studio Code (VS Code)](#deploy-via-visual-studio-code)
6. [Deploy via Visual Studio](#deploy-via-visual-studio)

---

### 1. Criando o Serviço de Aplicativos no Azure

1. **Acesse o Azure Portal**:

   - Faça login no [portal do Azure](https://portal.azure.com).

2. **Criar um Recurso**:

   - No painel esquerdo, clique em “**Criar um Recurso**”.
   - Procure por “**App Service**” e clique para abrir.

3. **Configuração do Aplicativo Web**:

   - Defina o nome da sua aplicação, que será o URL temporário (por exemplo: `minhaaplicacao.azurewebsites.net`).
   - Escolha o **Sistema Operacional** (Linux ou Windows) e a **Pilha de Execução** (como .NET Core, Node.js, etc.).
   - Certifique-se de que a **Região** seja a mesma onde seu banco de dados e o servidor estão hospedados.

4. **Revisar e Criar**:
   - Clique em “Revisar + Criar” e depois em “Criar” para provisionar o serviço.

Agora, seu site já estará no ar, com o link disponibilizado na interface do Azure.

---

### 2. Configurando o Banco de Dados SQL no Azure

1. **Acesse o Serviço SQL**:

   - No Azure, clique em “**Bancos de Dados SQL**” e selecione o banco de dados que deseja usar.

2. **Encontrar a Cadeia de Conexão**:

   - No menu lateral esquerdo, clique em “**Cadeia de Conexão**”.
   - Copie a cadeia de conexão **SQL Server**.

3. **Configurar o Login e Senha**:
   - Dentro da cadeia de conexão, adicione seu **login** e **senha** nos respectivos campos.

---

### 3. Configurando a Cadeia de Conexão

Agora, configure a string de conexão em seu arquivo `appsettings.json`:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=tcp:<seu-servidor>.database.windows.net,1433;Initial Catalog=<seu-banco>;Persist Security Info=False;User ID=<seu-usuario>;Password=<sua-senha>;MultipleActiveResultSets=False;Encrypt=True;TrustServerCertificate=False;Connection Timeout=30;"
}
```

- No `appsettings.json`, configure a cadeia de conexão no modo **produção** e, se necessário, ajuste também no modo **development** para testes locais.

4. **Aplicar Migrations**:
   - Execute os comandos do Entity Framework para aplicar as migrations:
   ```bash
   dotnet ef database update
   ```

---

### 4. Publicando o Código

#### Deploy via **Visual Studio Code**:

1. **Instalar Extensão do Azure**:

   - Abra o Visual Studio Code.
   - Instale a extensão **Azure Tools**:
     - Vá em **Extensões** (ícone de cubo na barra lateral).
     - Procure por “Azure Tools” e instale.

2. **Login no Azure**:

   - Após a instalação, faça login no Azure diretamente pelo VS Code:
     - Abra a barra de comandos (Ctrl+Shift+P) e procure por “**Azure: Sign In**”.

3. **Selecionar App Service**:

   - Na aba do Azure no VS Code, localize o serviço de aplicativos que você criou no Azure.

4. **Deploy do Código**:
   - Clique com o botão direito sobre o nome da aplicação no App Service e selecione “**Deploy to Web App**”.
   - Confirme o diretório do projeto e aguarde o upload do código.

Agora, sua aplicação estará disponível online.

---

### 5. Deploy via Visual Studio

1. **Abrir o Projeto**:

   - Abra o Visual Studio e carregue o projeto que você deseja publicar.

2. **Publicação para o Azure**:

   - Com o botão direito no nome do projeto, selecione “**Publicar**”.
   - Escolha “**Azure App Service (Windows)**” e clique em “**Avançar**”.

3. **Configuração do App Service**:

   - Selecione o **App Service** que você criou no portal do Azure.
   - Clique em “**Concluir**” para iniciar a publicação.

4. **Confirmação do Deploy**:
   - O Visual Studio começará a enviar os arquivos para o Azure e, ao final, abrirá o navegador com o link do site publicado.

---

Agora, sua aplicação ASP.NET estará hospedada no Azure, conectada ao banco de dados SQL Server e disponível para os usuários.
