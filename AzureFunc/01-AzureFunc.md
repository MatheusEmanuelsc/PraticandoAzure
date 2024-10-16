## Resumo: Como Criar uma Azure Function (VS Code, Visual Studio e Azure Portal)  

Este resumo explicará como criar uma **Azure Function** utilizando três ambientes diferentes: **VS Code**, **Visual Studio** e o **Azure Portal**. Também abordaremos como configurar corretamente permissões (Admin, Anônimo ou Function) e opções para usar HTTP Triggers com ou sem Swagger.  

---

### **Índice**  
1. [Requisitos](#requisitos)  
2. [Criando uma Azure Function no VS Code](#azure-function-no-vs-code)  
3. [Criando uma Azure Function no Visual Studio](#azure-function-no-visual-studio)  
4. [Criando uma Azure Function pelo Azure Portal](#azure-function-no-azure-portal)  
5. [Deploy da Azure Function](#deploy-da-azure-function)  

---

<a id="requisitos"></a>
## 1. Requisitos  
Antes de começar, é necessário ter algumas ferramentas instaladas e configuradas:  

- **Conta do Azure**: Crie uma [conta gratuita no Azure](https://azure.microsoft.com/free/) caso ainda não tenha.  
- **Azure CLI**: Para facilitar a autenticação e comandos de deploy.  
- **Visual Studio Code** com a **extensão Azure Functions** instalada.  
- **Visual Studio 2022** (ou mais recente) com a **workload Azure Development**.  

---

<a id="azure-function-no-vs-code"></a>
## 2. Criando uma Azure Function no VS Code  

### **Passo 1: Instalar a Extensão do Azure Functions**  
1. Abra o **VS Code**.  
2. Vá em **Extensions (Ctrl+Shift+X)** e pesquise por **Azure Functions**.  
3. Instale a extensão e, se necessário, reinicie o VS Code.

### **Passo 2: Autenticar com o Azure**  
1. Abra o **Command Palette (Ctrl+Shift+P)**.  
2. Digite **Azure: Sign In** e faça o login na sua conta do Azure.  

### **Passo 3: Criar uma Nova Azure Function**  
1. No **Explorer (barra lateral)**, clique no ícone do Azure.  
2. Em **Workspace**, selecione **Create a Function**.  
3. Escolha as configurações abaixo:  
   - **Template**: HTTP Trigger (com ou sem API Key).  
   - **Authorization Level**: Escolha entre **Anonymous**, **Function**, ou **Admin** (conforme o projeto).  
   - **Language**: Escolha entre C#, JavaScript, Python, ou Node.js.

4. Se desejar usar **Swagger** para documentação, adicione-o como dependência.  

### **Passo 4: Deploy para o Azure**  
1. No **Explorer**, clique com o botão direito na função e escolha **Deploy to Function App**.  
2. Escolha ou crie um **Function App** no Azure.  
3. Aguarde até que o deploy seja concluído.  

---

<a id="azure-function-no-visual-studio"></a>
## 3. Criando uma Azure Function no Visual Studio  

### **Passo 1: Criar um Novo Projeto**  
1. Abra o **Visual Studio**.  
2. Selecione **Create a new project**.  
3. Procure por **Azure Functions** na lista de templates.  

### **Passo 2: Configurar o Projeto**  
1. Escolha o template **HTTP Trigger**.  
2. Defina o **nível de autorização**: **Anonymous**, **Function**, ou **Admin**.  
3. Selecione **.NET** como linguagem.  

### **Passo 3: Rodar Localmente e Fazer Deploy**  
1. Execute o projeto localmente para garantir que a função esteja funcionando.  
2. No **Solution Explorer**, clique com o botão direito no projeto e escolha **Publish**.  
3. Selecione **Azure** como destino de publicação.  

---

<a id="azure-function-no-azure-portal"></a>
## 4. Criando uma Azure Function pelo Azure Portal  

### **Passo 1: Criar um Recurso**  
1. No **Azure Portal**, vá em **Create a resource**.  
2. Pesquise por **Function App** e clique em **Create**.  

### **Passo 2: Configurações da Function App**  
1. Preencha as informações básicas:  
   - **Subscription**: Escolha a assinatura.  
   - **Resource Group**: Crie ou selecione um existente.  
   - **Function App Name**: Escolha um nome único.  
   - **Runtime Stack**: Selecione o ambiente (ex.: .NET, Node.js, Python).  
   - **Region**: Escolha a região mais próxima para melhor performance.  

2. Clique em **Review + Create** e aguarde a criação do recurso.  

---

<a id="deploy-da-azure-function"></a>
## 5. Deploy da Azure Function  

### **Deploy pelo VS Code**  
1. No **VS Code**, clique com o botão direito na função e selecione **Deploy to Function App**.  
2. Escolha o **Function App** criado no Azure.  

### **Deploy pelo Visual Studio**  
1. No **Solution Explorer**, clique em **Publish**.  
2. Escolha a opção **Azure** e selecione a Function App.  

### **Verificar o Deploy no Azure Portal**  
1. No **Azure Portal**, vá em **Resource Groups**.  
2. Selecione seu **Function App**.  
3. A função estará disponível e pronta para ser invocada através da URL pública.  

---

### **Conclusão**  
Este guia mostrou como criar uma **Azure Function** utilizando **VS Code**, **Visual Studio**, e **Azure Portal**. Escolha o ambiente que melhor atende ao seu projeto. Lembre-se de ajustar as permissões e definir se a função será **Anonymous**, **Function**, ou **Admin**, dependendo do nível de segurança necessário. Com o deploy concluído, sua Azure Function estará pronta para ser consumida por outros serviços ou aplicações.