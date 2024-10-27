# Configurando Recursos e Dimensionamentos em Máquinas Virtuais na Azure

## Configuração e dimensionamento de VMs

Vá na barra lateral do portal Azure, procure por 'Máquina virtual' e depois clique em '+ Criar'. Escolha o Grupo de Recursos, dê um nome para sua VM e escolha a região.

![image](https://github.com/user-attachments/assets/4e72c1c3-6f9e-4447-a5b0-702212f9adf9)

Ao clicar em 'Opções de disponibilidade' o menu dropdown oferecerá três opções. A depender do seu objetivo, se escolher a opção 'Conjunto Dimensionamento de Máquinas Virtuais', você poderá criar um novo 
conjunto para projetar uma arquitetura de aplicativo altamente disponível e escalável.

![image](https://github.com/user-attachments/assets/c22307cc-c384-44d5-8396-a6ca370f895e)


### Configurar os dicos de armazenamento e criptografia
Clique em 'Avançar: Disco' para configurar os dicos de armazenamento e criptografia. Garanta que a opção 'Excluiur com VM' esteja selecionada para não ter surpresas com custos ocultos depois.

![image](https://github.com/user-attachments/assets/29568062-295d-47c6-bbe7-1e9436cbe8eb)

### Configurando a Rede

Avanace para a aba 'Rede', escolha uma redes ou crie uma nova no botão 'Criar novo'. Os endereços IP públicos e as NICs persistem independentemente da máquina virtual. Você pode optar por excluir
automaticamente o endereço IP público e a NIC quando a máquina virtual associada for excluída se marcar a opção.

![image](https://github.com/user-attachments/assets/5a820cfd-3c64-4e29-9abe-f180cf527163)

### Gerenciando permissões
Avance para a opção 'Gerenciamento'. Nesta aba, será tratada questões de segurança, acesso, desligamento automático, backup e atualizações do SO convidado.

![image](https://github.com/user-attachments/assets/b061c142-3033-4eeb-9829-f8259e7399c0)
![image](https://github.com/user-attachments/assets/fbae9fa8-fd22-4595-b4ae-0d4c07c962ab)

### Monitorando os recursos
Avance para 'Monitoramento'. Nesta aba você pode: habilitar 'Alertas' para ser notificado sobre eventos importantes que ocorrem em seu recurso, 'Diagnóstico' para solucionar problemas de falha de
inicialização de imagens personalizadas ou de plataforma e, por fim, 'Integridade' para habilitar o monitoramento de integridade para o conjunto de dimensionamento. 

![image](https://github.com/user-attachments/assets/b97b9f09-c981-472c-a246-3fe7f4e4309f)

### Analises adicionais
Na aba 'Avançado' você pode adicionar configuração, agentes, scripts ou aplicativos adicionais por meio de extensões da máquina virtual ou cloud-init.

![image](https://github.com/user-attachments/assets/626121d4-02de-44f9-9828-3aff29d61936)
![image](https://github.com/user-attachments/assets/881358cc-50d8-467c-978c-a52587c5f431)

### utilizando tags para o faturamento consolidado
Em 'Marcas', classifique recursos e exiba o faturamento consolidado aplicando a mesma marca a vários recursos e grupos de recursos.

![image](https://github.com/user-attachments/assets/28022972-0616-43b1-b8ec-42eb399da39c)

### Revisão
Agora chegou a hora de revisar toda a configuração feita até aqui, verificar o cursto mensal e finalmente criar a sua VM.

![image](https://github.com/user-attachments/assets/536060cf-2268-467a-b10b-6dcfc7eafa87)

### Bloqueio de recurso impede que os recursos sejam excluídos ou alterados acidentalmente.

Mesmo com as políticas do controle de acesso baseado em função do Azure (RBAC do Azure) em vigor, ainda há um risco de que as pessoas com o nível correto de acesso possam excluir recursos de nuvem críticos. Os bloqueios de recursos impedem que recursos sejam excluídos ou atualizados, dependendo do tipo de bloqueio. Os bloqueios de recursos podem ser aplicados a recursos individuais, grupos de recursos ou até mesmo a toda uma assinatura. Os bloqueios de recursos são herdados, o que significa que, se você colocar um bloqueio de recurso em um grupo de recursos, todos os recursos do grupo de recursos também terão o bloqueio de recurso aplicado.

### Tipos de Bloqueios de Recursos
Há dois tipos de bloqueios de recursos, um que impede que os usuários excluam e outro que impede que os usuários alterem ou excluam um recurso.

A exclusão significa que os usuários autorizados ainda poderão ler e modificar um recurso, mas não poderão excluir o recurso.
ReadOnly significa que os usuários autorizados poderão ler um recurso, mas não poderão excluir ou atualizar o recurso. Aplicar esse bloqueio é semelhante ao restringir todos os usuários autorizados para as permissões concedidas pela função Leitor.

![image](https://github.com/user-attachments/assets/cd7232cb-2d0b-48fe-ad2f-2492c01c1714)
