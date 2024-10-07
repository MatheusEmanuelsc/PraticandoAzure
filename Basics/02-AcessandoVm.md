### Acessando a Máquina Virtual no Azure e Conectando via Windows

Depois de criar a sua máquina virtual no Azure, siga os passos abaixo para visualizar o status da VM e acessá-la a partir de um sistema operacional Windows.

---

### Visualizando o Recurso da Máquina Virtual

1. **Após a criação da VM**, você será redirecionado para uma página de confirmação no Azure.
2. Clique no botão **“Ver recurso”** para visualizar as informações e o status da sua máquina virtual.
   - Aqui, você pode verificar o status atual da VM, como **em execução** ou **parada**.
   - Também é possível ver detalhes como endereço IP público, nome da máquina, e opções de conexão.

---

### Acessando a Máquina Virtual via Windows

Se você está em um sistema operacional **Windows** e definiu login e senha para acessar a VM, siga estes passos:

1. **Baixando o arquivo de Conexão RDP**:

   - Na página de detalhes da VM, clique em **“Conectar”** e escolha a opção **RDP** (Conexão de Área de Trabalho Remota).
   - O Azure fornecerá um arquivo `.rdp`. Clique em **baixar** para obter o arquivo de conexão.

2. **Conectando à VM**:

   - Abra o arquivo `.rdp` baixado, o que abrirá o programa de Conexão de Área de Trabalho Remota.
   - Clique em **“Conectar”**.
   - Será solicitado que você insira o **nome de usuário** e **senha** que você configurou ao criar a VM.

3. **Acessando o Sistema**:
   - Após inserir suas credenciais, você será conectado à máquina virtual.
   - Agora você pode configurar e instalar os serviços necessários, de acordo com suas necessidades.

---

Com esses passos simples, você estará conectado à sua máquina virtual no Azure a partir do seu sistema Windows, pronto para começar a trabalhar na VM.
