### Resumo: Como Criar um Servidor Web no Server Manager (Windows) Utilizando o IIS

Neste guia, você aprenderá como configurar um servidor web utilizando o **Server Manager** no Windows e instalar o **IIS (Internet Information Services)**, que permite hospedar sites no servidor.

---

### Passo a Passo

#### 1. Abrindo o Server Manager

- Abra o **Server Manager** no seu servidor Windows. Ele geralmente é aberto automaticamente ao fazer login em uma máquina com funções de servidor.

---

#### 2. Adicionando Funções e Recursos (Add Roles and Features)

1. No **Server Manager**, clique em **"Add roles and features"** (Adicionar funções e recursos). Essa opção geralmente aparece no painel principal ou no menu de **Gerenciamento** (Manage).

2. **Selecione a segunda opção** no assistente de configuração de funções. Isso permite que você adicione funções diretamente ao servidor em que está logado.

---

#### 3. Navegando no Assistente de Funções e Recursos

- Continue clicando em **“Next”** (Avançar) até chegar à etapa **“Server Roles”** (Funções do Servidor).

---

#### 4. Selecionando Web Server (IIS)

1. Na lista de funções do servidor, **marque a opção “Web Server (IIS)”**.

   - Essa função permite que o servidor atue como um servidor web, hospedando sites e aplicativos.

2. Depois de selecionar o **IIS**, clique em **“Next”**.

---

#### 5. Instalando o IIS

1. Continue clicando em **“Next”** para passar pelas configurações padrão.

   - As configurações padrões do IIS são geralmente suficientes para um servidor web básico.

2. Clique em **“Install”** para iniciar a instalação da função de **Web Server (IIS)**.

---

#### 6. Acessando o IIS

1. Após a instalação, você poderá acessar o **IIS**.

   - Abra o **Server Manager** novamente, e no painel **Dashboard**, clique em **“Tools”** (Ferramentas).
   - Selecione **“Internet Information Services (IIS) Manager”**.

2. No **IIS Manager**, você verá as informações sobre o servidor web e o site padrão criado.

---

#### 7. Verificando o Site

- Agora, abra um navegador web e digite o **endereço IP** ou **localhost** do servidor.
- Se tudo estiver configurado corretamente, você verá a **página padrão do IIS**, confirmando que o servidor web está ativo e funcional.

---

Agora seu servidor está configurado com o IIS e pronto para hospedar sites!
