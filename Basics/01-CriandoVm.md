### Resumo: Como Criar uma Máquina Virtual no Azure

Este tutorial detalha o passo a passo para criar uma máquina virtual (VM) no **Microsoft Azure**, utilizando os serviços e configurações padrões fornecidos pela plataforma. Vamos explorar cada etapa desde a criação do recurso até a configuração básica da VM.

---

### Índice

1. [Acessando o Portal do Azure](#acessando-o-portal-do-azure)
2. [Criando um Novo Recurso](#criando-um-novo-recurso)
3. [Selecionando a Máquina Virtual](#selecionando-a-máquina-virtual)
4. [Configurando a Máquina Virtual](#configurando-a-máquina-virtual)
   - Assinatura
   - Grupo de Recursos
   - Detalhes da Instância
5. [Revisão e Criação](#revisão-e-criação)
6. [Conclusão](#conclusão)

---

### 1. Acessando o Portal do Azure

Primeiramente, acesse o portal do Azure através do link [portal.azure.com](https://portal.azure.com/). Você precisará fazer login com suas credenciais da Microsoft.

---

### 2. Criando um Novo Recurso

Após fazer o login no Azure, siga os seguintes passos:

1. **No painel de navegação à esquerda**, clique em **“Criar um recurso”**.
2. No campo de busca, digite **“Máquina Virtual”** e pressione **Enter**.

---

### 3. Selecionando a Máquina Virtual

1. A lista de resultados mostrará a opção **"Máquina Virtual"**. Clique nela.
2. Em seguida, clique no botão **“Criar”** para iniciar o processo de configuração da nova máquina virtual.

---

### 4. Configurando a Máquina Virtual

Agora você será redirecionado para uma tela onde poderá configurar os parâmetros da sua máquina virtual.

#### 4.1 Assinatura

- **Assinatura**: Mantenha a assinatura padrão que já estará configurada. Ela corresponde ao plano de pagamento que você está utilizando na plataforma.

#### 4.2 Grupo de Recursos

- **Grupo de Recursos**: Crie um novo grupo de recursos para organizar seus ativos no Azure.
  - Clique em **“Criar novo”**.
  - Dê um nome para o grupo de recursos, como "GrupoVMExemplo".
  - Confirme clicando em **OK**.

#### 4.3 Detalhes da Instância

- **Nome da VM**: Escolha um nome que identifique a sua máquina virtual. Exemplo: "VMExemplo".
- **Região**: Selecione a região mais próxima de você ou aquela que melhor atenda às suas necessidades. O Azure oferece várias regiões globais.
- **Disponibilidade**: Mantenha as configurações padrões ou, se preferir, configure opções de alta disponibilidade.
- **Imagem**: Escolha o sistema operacional que será instalado. As opções mais comuns são:
  - Windows Server
  - Ubuntu
- **Tamanho da VM**: Selecione o tamanho da máquina virtual de acordo com suas necessidades. As configurações padrão são suficientes para testes e pequenas aplicações.

#### 4.4 Autenticação

- **Tipo de autenticação**: Selecione se deseja usar **chave SSH** ou **senha**.
  - **Senha**: Escolha um nome de usuário e senha para acessar a máquina virtual via RDP ou SSH.
  - **Chave SSH**: Se preferir, adicione uma chave SSH para maior segurança.

#### 4.5 Disco de Armazenamento

- Escolha o tipo de disco. Para cenários simples, o **disco SSD padrão** é uma boa escolha.

#### 4.6 Rede

- Mantenha as configurações de rede padrão. Uma rede virtual será criada automaticamente para sua máquina virtual.

---

### 5. Revisão e Criação

1. Depois de configurar todos os parâmetros, clique em **“Revisar e Criar”**.
2. O Azure fará uma validação das configurações. Se tudo estiver correto, o botão **"Criar"** ficará habilitado.
3. Clique em **“Criar”** para finalizar o processo.

---

### 6. Conclusão

Após clicar em **“Criar”**, o Azure começará a provisionar a máquina virtual. O processo pode levar alguns minutos. Quando estiver concluído, você terá acesso à sua VM via SSH ou RDP, dependendo das configurações de autenticação escolhidas.

Agora sua máquina virtual está pronta para ser utilizada!

---

Este guia básico cobre os principais passos para criar uma máquina virtual no Azure com as configurações padrões. Dependendo das suas necessidades, você pode explorar outras opções de customização oferecidas pela plataforma.
