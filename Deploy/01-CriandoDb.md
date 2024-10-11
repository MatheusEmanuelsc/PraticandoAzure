### Resumo: Como Criar um Banco de Dados SQL na Nuvem no Azure

Este tutorial detalha os passos para criar e configurar um banco de dados SQL na nuvem utilizando o **Microsoft Azure**. Inclui a criação de um grupo de recursos, banco de dados, servidor SQL, além da configuração de redes e regras de firewall para acesso remoto seguro.

---

### Índice

1. [Acessando o Menu](#1-acessando-o-menu)
2. [Criando um Banco de Dados SQL](#2-criando-um-banco-de-dados-sql)
3. [Configurando o Servidor SQL](#3-configurando-o-servidor-sql)
4. [Configurando a Rede e Permissões de Acesso](#4-configurando-a-rede-e-permissões-de-acesso)
5. [Configurando Regras de Firewall](#5-configurando-regras-de-firewall)
6. [Ajustes Pós-Criação](#6-ajustes-pós-criação)

---

### 1. Acessando o Menu

1. Acesse o portal do **Azure**.
2. No canto superior esquerdo, clique no **menu** (ícone de três linhas).
3. Selecione **“Criar um recurso”** para iniciar a criação do banco de dados.

---

### 2. Criando um Banco de Dados SQL

1. No campo de pesquisa ou nas opções, busque por **“SQL Database”**.
2. Preencha os campos obrigatórios:
   - **Grupo de recursos**: Selecione um grupo existente ou crie um novo.
   - **Nome do banco de dados**: Insira um nome significativo para o banco.

---

### 3. Configurando o Servidor SQL

1. Ao configurar o banco, será solicitado um **Servidor SQL**:
   - **Criar novo servidor**: Defina um **nome de servidor**, **login de administrador**, e uma **senha**.
   - **Selecionar servidor existente**: Caso já tenha um servidor SQL, selecione-o na lista.

> **Observação**: O nome do servidor deve ser único em toda a infraestrutura do Azure.

---

### 4. Configurando a Rede e Permissões de Acesso

1. Durante a criação do servidor, configure as opções de rede:
   - Selecione a opção **Público** para permitir o acesso externo ao banco de dados.
2. Após configurar o acesso público, você poderá adicionar o **IP do cliente** para garantir que seu dispositivo tenha permissão de conexão ao banco.

---

### 5. Configurando Regras de Firewall

1. No painel de **Regras de Firewall**, configure as permissões de acesso:
   - Marque a opção **Permitir que serviços e recursos do Azure acessem este servidor**.
   - Clique em **Adicionar IP do cliente atual** para liberar o acesso do seu endereço IP ao banco de dados.
2. Após configurar as regras, clique em **Salvar** para aplicar as alterações.

---

### 6. Ajustes Pós-Criação

Se você não configurou as regras de firewall no momento da criação ou deseja modificar as permissões:

1. Acesse o **Grupo de Recursos** associado ao seu banco de dados SQL.
2. Selecione o banco de dados SQL.
3. No menu lateral, vá em **Rede** e clique em **Regras de firewall**.
4. Adicione o **IP do cliente** para permitir o acesso ao banco a partir do seu dispositivo.
5. **Salvar** as alterações para que as configurações entrem em vigor.

---

### Conexão ao Banco de Dados

1. No portal do Azure, abra a seção de **Banco de Dados SQL** e copie o **Nome do Servidor**.
2. Para se conectar ao banco de dados, utilize o nome do servidor, seu **login** e **senha**. Caso não tenha configurado anteriormente, você poderá redefinir as credenciais diretamente no painel do servidor SQL.

---

Seguindo esses passos, seu banco de dados SQL estará configurado para acesso remoto, com as permissões de rede e firewall devidamente ajustadas para garantir segurança e conectividade no Azure.
