# Criando e Configurando uma Conta de Armazenamento no Azure

## Índice
- [Introdução](#introdução)
- [Passo 1: Criar uma Conta de Armazenamento](#passo-1-criar-uma-conta-de-armazenamento)
- [Passo 2: Configurar a Conta de Armazenamento](#passo-2-configurar-a-conta-de-armazenamento)
- [Passo 3: Criar e Configurar um Contêiner](#passo-3-criar-e-configurar-um-contêiner)
- [Conclusão](#conclusão)

---

## Introdução
O Azure oferece uma solução de armazenamento na nuvem escalável e segura para diversos tipos de arquivos, como documentos, imagens, vídeos, entre outros. Neste tutorial, explicaremos como criar uma conta de armazenamento no Azure, configurar as principais opções e criar um contêiner, que será utilizado para organizar e armazenar seus arquivos.

---

## Passo 1: Criar uma Conta de Armazenamento

### 1.1 Acessar a Plataforma do Azure
- **Login**: Acesse o portal do Azure [portal.azure.com](https://portal.azure.com) e faça login com sua conta.
- **Pesquisa**: Na barra de pesquisa no topo da página, procure por “Contas de Armazenamento” ou clique em **Mais Serviços** e, em seguida, selecione **Contas de Armazenamento**.

### 1.2 Criar uma Nova Conta
- Clique no botão **Criar** para iniciar o processo de criação de uma nova conta de armazenamento.
- Preencha as configurações iniciais, como **Grupo de Recursos**, **Região**, **Nome da Conta de Armazenamento**, e selecione o tipo de desempenho (padrão ou premium).

---

## Passo 2: Configurar a Conta de Armazenamento

Após a criação da conta, algumas configurações precisam ser ajustadas:

### 2.1 Configurações Básicas
- **Replicação**: Escolha o tipo de replicação que deseja, como **LRS** (Local-Redundant Storage) ou **GRS** (Geo-Redundant Storage).
- **Redundância**: Define como os dados serão replicados para garantir alta disponibilidade.

### 2.2 Finalizar a Criação
Após configurar todas as opções, clique em **Revisar + Criar** e, depois, em **Criar**. O processo de criação pode levar alguns segundos. Quando concluído, você será notificado.

---

## Passo 3: Criar e Configurar um Contêiner

Um **Contêiner** no Azure é semelhante a uma pasta que organiza e armazena arquivos no **Blob Storage**.

### 3.1 Criar o Contêiner
- Na conta de armazenamento recém-criada, vá até a opção **Contêineres** no painel à esquerda.
- Clique em **+ Contêiner** e forneça um nome. Este nome será usado para identificar e organizar os arquivos dentro da conta de armazenamento.

### 3.2 Definir o Nível de Acesso
- Ao criar o contêiner, você deverá escolher o nível de acesso:
  - **Privado**: O contêiner e seus blobs (arquivos) só podem ser acessados pelo proprietário da conta.
  - **Blob**: Os arquivos podem ser acessados publicamente, mas o contêiner em si não.
  - **Contêiner**: Tanto o contêiner quanto os arquivos podem ser acessados publicamente.
  
Escolha a opção que melhor se adequa às suas necessidades e clique em **Criar**.

---

## Conclusão

Após criar e configurar a conta de armazenamento e os contêineres, você poderá organizar seus arquivos de forma segura e flexível. O Azure oferece diversas opções de níveis de acesso, permitindo controle detalhado sobre quem pode visualizar e interagir com os dados.