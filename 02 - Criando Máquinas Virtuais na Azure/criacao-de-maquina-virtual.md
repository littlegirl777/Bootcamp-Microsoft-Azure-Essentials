# Criação de Máquina Virtual na Azure 🌐


### Primeiro, entendendo redundância e SLA:

A criação de uma VM no Azure deve considerar **redundância** e o **SLA** para garantir alta disponibilidade e confiabilidade. A redundância envolve replicar recursos em diferentes zonas de disponibilidade ou conjuntos de disponibilidade, reduzindo riscos de falhas. O **SLA** especifica a garantia de tempo de operação do serviço, que aumenta com configurações de redundância adequadas. Assim, escolher a configuração correta é essencial para atingir os níveis de disponibilidade desejados.

![image](https://hackmd.io/_uploads/rkvGhGje1x.png)

🔗[SLA Microsoft](https://learn.microsoft.com/pt-br/azure/well-architected/reliability/metrics)

---
# Criando a VM (Máquina Virtual):

## 1. Acessando o Portal do Azure

Acesse o [portal do Azure](https://portal.azure.com). 


## 2. Iniciando a Criação da VM 

![image](https://hackmd.io/_uploads/Hy5BpGolJe.png)


No painel do Azure, siga os passos abaixo para começar o processo de criação da sua máquina virtual:

- Na barra de pesquisa, digite "Máquinas Virtuais" ou "Virtual Machines" e selecione a opção no menu suspenso.
- Clique no botão **"Criar"** e escolha **"Máquina Virtual"**.

---

## 3. Configurando os Detalhes Básicos 📝

Agora você será redirecionado para a página de configuração da VM. Preencha as informações conforme a necessidade da vm que você precisa criar:

- **Assinatura**: Selecione a assinatura correta que será usada para os custos da VM.
- **Grupo de Recursos**: Escolha um grupo de recursos existente ou crie um novo. O grupo de recursos organiza todos os seus recursos relacionados, facilitando a gestão.
- **Nome da VM**: Escolha um nome significativo que ajude a identificar a função ou o propósito da VM.
- **Região**: Escolha a região mais próxima de seus usuários ou da sua localização. Considere usar regiões com suporte a **Zonas de Disponibilidade (Availability Zones)** para garantir alta disponibilidade.
  - *Exemplo*: East US, West Europe.
- **Opção de Disponibilidade**: Para maior resiliência, selecione:
  - **Conjunto de Disponibilidade (Availability Set)** ou
  - **Zonas de Disponibilidade (Availability Zones)** – para isolar sua VM contra falhas de hardware localizadas.
- **Imagem**: Selecione o sistema operacional desejado, como:
  - Windows Server 2019
  - Ubuntu 20.04 LTS
  - Outros sistemas no marketplace.
- **Tamanho**: Escolha o tamanho da VM com base em suas necessidades de CPU, memória e armazenamento. O Azure oferece uma vasta gama de tamanhos otimizados para diferentes cargas de trabalho.
  - *Exemplo*: **Standard_D2s_v3** (2 vCPUs, 8 GB RAM) para pequenas aplicações.

---

## 4. Configurando a Rede 

Agora é hora de configurar as opções de rede para garantir conectividade e segurança adequadas:

- **Rede Virtual**: Crie uma nova rede virtual ou selecione uma existente. Isso permitirá a comunicação entre sua VM e outros recursos do Azure.
  - *Dica*: Use uma arquitetura de rede segmentada com sub-redes para maior controle.
- **Sub-rede**: Selecione a sub-rede onde a VM será conectada. Para melhores práticas de segurança, configure diferentes sub-redes para diferentes tipos de recursos (por exemplo, back-end e front-end).
- **Endereço IP Público**: Configure um endereço IP público, se necessário. Este será usado para acessar a VM externamente.
- **Grupo de Segurança de Rede (NSG)**: Defina as regras de firewall para proteger a VM. Certifique-se de configurar permissões de entrada e saída adequadas para suas necessidades.
  - *Exemplo*: Permitir conexões SSH (porta 22) ou RDP (porta 3389) de fontes específicas.

---

## 5. Definindo as Credenciais de Acesso 

Agora configure o acesso à sua VM:

- **Autenticação**: Escolha o método de autenticação:
  - **Chave SSH** (recomendado para VMs Linux) ou
  - **Senha** (para VMs Windows e Linux).
- **Nome de Usuário e Senha**: Crie um nome de usuário e uma senha forte. No caso de usar chave SSH, faça o upload da sua chave pública.
  - *Dica*: Evite usar nomes comuns como "admin" ou "root" por razões de segurança.

---

## 6. Armazenamento e Redundância 

Configure as opções de armazenamento para garantir a redundância dos dados:

- **Disco do Sistema Operacional**: O Azure oferece discos gerenciados para maior confiabilidade. Escolha entre:
  - **Standard HDD**: Opção mais barata, com menor desempenho.
  - **Standard SSD**: Um equilíbrio entre custo e desempenho.
  - **Premium SSD**: Altamente recomendado para cargas de trabalho críticas que exigem alta performance.
- **Discos de Dados**: Adicione discos extras conforme necessário. Para melhor desempenho e redundância, utilize discos **Premium SSD** ou **Ultra Disk**.
- **Redundância de Armazenamento**: Opte por replicação local (LRS), replicação geográfica (GRS) ou outra estratégia dependendo dos requisitos de disponibilidade.

---

## 7. Revisão e Criação 🔍

Revise todas as configurações com atenção para garantir que atendam às suas necessidades de performance e disponibilidade:

- **Validação**: O portal do Azure realiza uma validação automática das configurações. Se houver erros, eles serão destacados aqui.
- Clique em **"Criar"**. O processo pode levar alguns minutos enquanto o Azure provisiona os recursos.

---

## 8. Conectando-se à Sua Máquina Virtual 🌟

Depois que a VM for criada, você pode se conectar a ela para começar a gerenciar e operar o ambiente:

- **Windows**: Use o **Remote Desktop Protocol (RDP)**. No portal, selecione a VM, clique em "Conectar" e baixe o arquivo RDP. Em seguida, insira suas credenciais.
- **Linux**: Conecte-se via **SSH**. Use um terminal e o seguinte comando:
  ```bash
  ssh usuario@<endereço-ip-público>
