# Internet, Pacotes de Dados, Modelo OSI e TCP/IP

## 1. Internet

- A Internet é um **conjunto de redes interligadas**.
- Ela permite a comunicação entre computadores de forma **descentralizada**.
- Seu funcionamento é baseado no conjunto de protocolos **TCP/IP**.
- Sua origem remonta à **ARPANET**, criada em contexto militar e acadêmico.
- No Brasil, sua consolidação ocorreu com apoio da **RNP (Rede Nacional de Ensino e Pesquisa)**.
- A popularização da Internet cresceu com os **navegadores**, o uso comercial e as redes sociais.

### Ideia principal
- O usuário normalmente interage apenas com as **camadas mais altas**, como a camada de aplicação.
- As tecnologias físicas e de enlace ficam “escondidas” do usuário comum.



## 2. Pacote de Dados

- Um **pacote de dados** é a unidade básica de informação transmitida em uma rede.
- Quando enviamos uma mensagem, vídeo, áudio ou arquivo, a informação é **dividida em partes menores**, chamadas pacotes.

### Cada pacote contém:
- Parte do conteúdo
- Endereço de origem
- Endereço de destino
- Informações de controle

### Estrutura do pacote
O cabeçalho pode conter:
- IP de origem
- IP de destino
- Porta de origem
- Porta de destino
- Número de sequência
- Tipo de protocolo (TCP ou UDP)

### Campos importantes do cabeçalho IPv4
- **Versão**: indica se é IPv4 ou IPv6
- **TTL (Time to Live)**: limita o tempo de vida do pacote na rede
- **Protocolo**: informa o que está sendo transportado
- **IP de origem e destino**: identificam remetente e destinatário



## 3. Portas em Redes de Computadores

- A **porta** é um ponto lógico de comunicação.
- Ela permite identificar **qual programa ou serviço** deve receber os dados.
- Analogia:
  - **IP** = número do prédio
  - **Porta** = número do apartamento

### Exemplo
- Um mesmo computador pode:
  - acessar um site pela porta **443 (HTTPS)**
  - fazer videochamada por outra porta diferente

### Categorias de portas
- **0 a 1023**: Well-Known Ports  
  - usadas por serviços conhecidos
- **1024 a 49151**: Registered Ports  
  - usadas por aplicações e empresas
- **49152 a 65535**: Dynamic/Private Ports  
  - usadas temporariamente



## 4. Encapsulamento

- O **encapsulamento** é o processo em que cada camada adiciona suas informações aos dados.
- É como se os dados fossem recebendo “camadas” até estarem prontos para viajar pela rede.

### Etapas do encapsulamento
- **Aplicação**: gera os dados
- **Transporte**: adiciona informações como portas
- **Rede**: adiciona os endereços IP
- **Enlace**: adiciona o endereço MAC e controle de erro
- **Física**: transmite os bits pelo meio físico

### Unidades de dados
- Aplicação: **dados / mensagem**
- Transporte: **segmento**
- Rede: **pacote / datagrama**
- Enlace: **quadro / frame**
- Física: **bits**



## 5. Modelo de Camadas

- O modelo em camadas organiza a rede em níveis para **reduzir a complexidade**.
- Cada camada tem uma **função específica**.
- Cada camada oferece serviços para a camada acima.
- A comunicação acontece entre **camadas correspondentes** em máquinas diferentes.
- As regras dessa comunicação formam os **protocolos**.

### Tipos de serviço
#### Orientado à conexão
- Estabelece conexão antes de transmitir
- Garante maior controle e confiabilidade
- Exemplo de ideia: como uma ligação telefônica

#### Sem conexão
- Não estabelece conexão prévia
- Cada mensagem é enviada independentemente
- Exemplo de ideia: como enviar cartas pelo correio



# 6. Modelo OSI

- O modelo OSI foi criado pela **ISO**.
- É um **modelo de referência**, ou seja, serve para explicar como a comunicação em rede pode ser organizada.
- Ele possui **7 camadas**.
- Não define exatamente quais protocolos usar, mas define **o que cada camada deve fazer**.

## Camadas do Modelo OSI

### 1. Física
- Trabalha com **bits**
- Trata da transmissão no meio físico
- Lida com cabos, conectores, sinais, frequência e modulação
- Exemplo de equipamento citado: **Hub**
- Exemplo de tecnologias: Ethernet, Wi-Fi, Bluetooth, fibra óptica

### 2. Enlace de Dados
- Trabalha com **quadros**
- Controla o acesso ao meio
- Trata erros de transmissão
- Usa **endereços MAC**
- Exemplo de equipamento: **Switch**
- Exemplos de técnicas: CSMA/CD, CSMA/CA e ALOHA

### 3. Rede
- Trabalha com **pacotes**
- Faz o **roteamento**
- Usa **endereços IP**
- Exemplo de equipamento: **Roteador**
- Exemplos de protocolos: IP, IPv6, ICMP e BGP

### 4. Transporte
- Trabalha com a comunicação fim a fim
- Pode garantir entrega ordenada e controle de erros
- Principais protocolos:
  - **TCP**: confiável, orientado à conexão
  - **UDP**: não confiável, sem conexão
  - **SCTP**: também citado como protocolo da camada

### 5. Sessão
- Estabelece, gerencia e encerra sessões de comunicação
- Organiza o início e o fim da comunicação
- Exemplos: RDP, SIP e H.323

### 6. Apresentação
- Prepara os dados para a aplicação
- Faz:
  - codificação
  - compressão
  - criptografia
- Exemplos citados: SSL/TLS, MIME

### 7. Aplicação
- É a camada mais próxima do usuário
- Oferece serviços de rede para os programas
- Exemplos:
  - HTTP
  - SMTP
  - POP
  - FTP
  - DHCP
  - DNS



## 7. Exemplo de envio de dados no modelo OSI

### Física
- Converte dados em sinal elétrico ou óptico

### Enlace
- Adiciona endereço MAC
- Verifica erros de transmissão

### Rede
- Define o caminho do pacote
- Pode fragmentar os dados

### Transporte
- Controla fluxo e erros
- Garante entrega, dependendo do protocolo

### Sessão
- Abre, gerencia e encerra a comunicação

### Apresentação
- Pode comprimir e criptografar os dados

### Aplicação
- Entrega a informação ao software usado pelo usuário



# 8. Modelo TCP/IP

- O modelo TCP/IP surgiu a partir da experiência prática da **ARPANET** e da Internet.
- Recebe esse nome por causa dos protocolos **TCP** e **IP**.
- É o modelo mais usado na prática para explicar o funcionamento da Internet.

## Características principais
- O modelo TCP/IP é mais **prático**
- O modelo OSI é mais **conceitual**
- O TCP/IP se tornou a base real da Internet

## Camadas do modelo TCP/IP

### 1. Aplicação
- Fornece serviços usados pelo usuário
- Exemplos: HTTP, FTP, SMTP, Telnet

### 2. Transporte
- Controla a comunicação fim a fim
- Faz multiplexação
- Pode controlar fluxo e erros
- Exemplos: TCP e UDP

### 3. Rede
- Faz endereçamento lógico e roteamento
- Encaminha pacotes entre hosts
- Exemplos: IP, OSPF, ICMP

### 4. Enlace
- Faz a ligação entre a camada lógica e a tecnologia física
- Exemplo: Ethernet

### 5. Física
- Trata do hardware, circuitos e transmissão de bits
- Depende do meio físico usado



## 9. Relação entre OSI e TCP/IP

- O modelo **OSI** tem **7 camadas**
- O modelo **TCP/IP** tem **5 camadas** na abordagem estudada
- As camadas de **Sessão** e **Apresentação** do OSI normalmente ficam incorporadas à **Aplicação** no TCP/IP
- Mesmo com diferenças, os dois modelos se correspondem em vários pontos

### Comparação geral
- **OSI**
  - mais teórico
  - mais conceitual
  - importante para estudo
- **TCP/IP**
  - mais prático
  - baseado em protocolos reais
  - usado de fato na Internet
