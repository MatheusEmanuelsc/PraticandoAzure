### Resumo: Como Criar um Banco de Dados SQL na Nuvem no Azure

Aqui está um passo a passo para criar e configurar um banco de dados SQL na nuvem utilizando o **Microsoft Azure**. Esse processo inclui a criação de um grupo de recursos, banco de dados, servidor, e a configuração de redes e regras de firewall para acesso remoto.

---

### Passo a Passo

#### 1. Acessando o Menu

1. No portal do **Azure**, clique no **menu** (ícone de três linhas no canto superior esquerdo).
2. Selecione **“Criar um recurso”**.

---

#### 2. Criando um Banco de Dados SQL

1. Na barra de pesquisa ou na lista de opções, selecione **“SQL Database”**.
2. Preencha os detalhes do banco de dados:
   - **Grupo de recursos**: Crie um novo grupo de recursos ou selecione um existente.
   - **Nome do banco de dados**: Escolha um nome para o banco.

---

#### 3. Configurando o Servidor SQL

1. **Servidor**: Você pode criar um novo servidor ou selecionar um existente.
   - Ao criar um novo servidor, você precisa definir um **nome**, **login de administrador**, e **senha**.
   - Se já tiver um servidor, basta selecionar o existente e continuar.

---

#### 4. Configurando a Rede e Permissões de Acesso

1. **Acesse a etapa "262347"** durante a configuração do banco de dados, onde você ajustará as configurações de rede.
2. Na seção **Rede**, escolha a opção **“Extremidade pública”** para permitir o acesso ao banco de dados de fora do Azure.
   - Isso é necessário para acessar o banco remotamente.

---

#### 5. Configurando Regras de Firewall

1. No painel de **Regras de Firewall**, marque as seguintes opções:

   - **Permitir que serviços e recursos do Azure acessem este servidor**.
   - **Adicionar o IP do cliente atual** (para que o seu IP tenha permissão de acesso ao banco).

2. Clique em **Salvar** para aplicar as configurações.

---

#### 6. Ajustes Pós-Criação

1. Se você esqueceu de configurar as regras de firewall durante a criação, ou deseja modificar:
   - Vá até o **Grupo de Recursos** que contém seu banco de dados SQL.
   - Selecione o banco de dados SQL.
   - Clique na opção **Rede** e depois em **Regras de firewall**.
   - Adicione o **IP do cliente** para garantir que seu dispositivo tenha acesso ao banco de dados.

---

Após seguir esses passos, seu banco de dados SQL estará criado e configurado para acesso remoto, com as permissões de rede e firewall devidamente ajustadas para que você possa conectá-lo a partir do seu ambiente de trabalho.
