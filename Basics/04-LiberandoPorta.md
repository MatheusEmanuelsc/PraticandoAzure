### Resumo: Como Liberar a Rede e Tornar o Site Acessível no Azure

Depois de configurar o IIS no servidor e verificar que o servidor está online, é necessário liberar o acesso à rede para permitir que o site seja acessado externamente. Este guia mostra como criar uma regra de segurança no Azure para liberar o tráfego HTTP.

---

### Passo a Passo

#### 1. Verificando o IP do Servidor

1. **Servidor Online**: Certifique-se de que sua máquina virtual (VM) no Azure está online e que o IIS foi corretamente instalado.
2. **Copiar o Endereço IP**: No **Server Manager**, anote o **endereço IP público** da máquina virtual.

   - Você pode encontrar o IP na seção de detalhes da sua VM no Azure.

3. **Verificar no Navegador**: Abra um navegador web e cole o **endereço IP** na barra de endereço. Neste momento, o site ainda **não estará acessível**, porque a regra de firewall ainda não foi configurada.

---

#### 2. Criando uma Regra de Segurança no Azure

1. **Acessando o Portal do Azure**:

   - No portal do Azure, vá até a seção **Redes**.
   - Localize a **Máquina Virtual** que você criou e clique nela para acessar as configurações de rede.

2. **Criando uma Nova Regra de Segurança**:

   - No painel lateral, selecione **“Configurações de rede”** ou **“Segurança de rede”**.
   - Clique em **“Adicionar regra de segurança de entrada”** para permitir o tráfego HTTP.

3. **Configurar a Regra HTTP**:
   - Em **Protocolo**, escolha **“HTTP”**.
   - Defina a **porta 80**, que é a porta padrão para tráfego HTTP.
   - Em **Ação**, selecione **“Permitir”**.
   - Confirme as configurações clicando em **“Adicionar”**.

---

#### 3. Verificando se o Site Está Online

1. **Volte ao Navegador**: Após a criação da regra, volte ao navegador e acesse novamente o **endereço IP** público da VM.
2. **Site Online**: Agora, o site padrão do **IIS** deverá aparecer, confirmando que o servidor web está acessível externamente.

---

Seu site está agora online e acessível via HTTP a partir da internet!
