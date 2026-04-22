# Camada de Enlace e Interconexão

## 1. Encapsulamento e Decapsulamento

### Encapsulamento
- É o processo de **adicionar informações de controle** aos dados em cada camada da rede.
- Funciona como se a mensagem fosse sendo **embrulhada em várias camadas** até poder ser transmitida.

### Etapas do encapsulamento
- **Aplicação**: gera os dados originais, como texto, e-mail ou imagem.
- **Transporte**: divide os dados em segmentos e adiciona portas de origem e destino.
- **Rede**: encapsula os segmentos em pacotes e adiciona os endereços IP.
- **Enlace de Dados**: transforma os pacotes em quadros (frames) e adiciona endereços MAC.
- **Física**: transmite os bits pelo meio físico.

### Decapsulamento
- É o processo inverso.
- No destino, cada camada **remove seu cabeçalho** até recuperar os dados originais.

### Etapas do decapsulamento
- **Enlace de Dados**: verifica o endereço MAC.
- **Rede**: verifica o endereço IP.
- **Transporte**: verifica as portas.
- **Aplicação**: entrega os dados ao programa final.



## 2. Protocolos de Comunicação

- Toda comunicação em rede segue **protocolos**.
- Protocolos são **regras** que definem como os dispositivos se comunicam.
- Eles podem ser implementados em:
  - software
  - hardware
  - ambos

### Tipos de protocolos
- **Comunicação em rede**: permitem a troca de dados entre dispositivos
- **Segurança da rede**: fornecem autenticação, integridade e criptografia
- **Roteamento**: ajudam a escolher o melhor caminho para os dados
- **Descoberta de serviço**: detectam automaticamente dispositivos e serviços

### Funções dos protocolos
- **Endereçamento**: identifica remetente e destinatário
- **Confiabilidade**: garante entrega
- **Controle de fluxo**: ajusta a taxa de envio
- **Sequenciamento**: organiza os dados na ordem correta
- **Detecção de erros**: identifica corrupção nos dados
- **Interface de aplicação**: permite comunicação entre aplicativos



## 3. Protocolos de Enlace de Dados

- São regras que determinam como os dados são transmitidos entre **dois dispositivos diretamente conectados**.
- Fazem parte da **camada de enlace de dados** do modelo OSI.
- Suas principais funções são:
  - transmissão de quadros
  - controle de erros
  - controle de fluxo
  - endereçamento físico

### Principais protocolos

#### Ethernet
- É o protocolo mais usado em redes locais (LANs).
- Usa **endereços MAC** para identificar dispositivos.
- Os dados são transmitidos em **quadros**.

#### Wi-Fi (IEEE 802.11)
- Permite comunicação sem fio em redes locais.
- Também usa endereço MAC.
- Compartilha o meio com vários dispositivos.

#### PPP
- Usado em conexões ponto a ponto.
- Pode encapsular diferentes protocolos.
- Foi muito usado em internet discada.

#### Frame Relay
- Usado em redes WAN.
- Transmite dados em quadros variáveis.
- Foi importante em conexões corporativas a longa distância.

#### MPLS
- Usa **rótulos (labels)** para encaminhar dados com mais eficiência.
- Muito usado por provedores de internet.

#### HDLC
- Protocolo confiável de enlace de dados.
- Controla fluxo e erros.
- Bastante usado em enlaces dedicados.

#### Token Ring
- Desenvolvido pela IBM.
- Só transmite quem estiver com o **token**.

#### FDDI
- Usa fibra óptica.
- Trabalha com **dois anéis**, oferecendo redundância e confiabilidade.


## 4. Camada de Enlace

- Na camada de enlace, os dados são transformados em **quadros (frames)**.
- Essa camada trabalha com **endereços MAC**.
- O dispositivo mais comum nela é o **switch**.

### Funções do switch
- Conectar dispositivos em uma LAN
- Encaminhar dados para a porta correta
- Reduzir colisões
- Melhorar o desempenho da rede

### Estrutura do quadro
Um quadro pode conter:
- endereço MAC de origem
- endereço MAC de destino
- tipo de quadro
- dados
- FCS (Frame Check Sequence), para detectar erros

### Tipos de transmissão
- **Unicast**: para um único dispositivo
- **Broadcast**: para todos os dispositivos da rede
- **Multicast**: para um grupo específico

### Endereço MAC
- É um identificador **único** da interface de rede.
- Fica associado à **placa de rede**.
- É atribuído pelo fabricante.



## 5. Controle de Acesso ao Meio (MAC)

- É o conjunto de métodos usados para controlar **como vários dispositivos compartilham o meio de transmissão**.
- Seu objetivo é evitar **colisões**.

### Como funciona
- Cada dispositivo tem um endereço MAC único.
- Como o meio é compartilhado, é preciso decidir **quem pode transmitir e quando**.
- O MAC organiza esse acesso.

### Principais métodos

#### CSMA/CD
- Usado em redes Ethernet antigas.
- O dispositivo escuta o meio antes de transmitir.
- Se houver colisão, espera um tempo aleatório e tenta novamente.

#### CSMA/CA
- Usado em redes Wi-Fi.
- Tenta **evitar a colisão antes que ela aconteça**.

#### Token Passing
- Um token circula pela rede.
- Só transmite quem estiver com o token.
- Evita colisões, mas é mais complexo.

#### Polling
- Um controlador central pergunta, um por um, quem deseja transmitir.
- Muito usado em ambientes industriais.



## 6. Controle de acesso ao meio e qualidade da rede

O método escolhido afeta diretamente a qualidade da rede.

### Latência
- **CSMA/CD**: pode variar bastante
- **Token Passing**: mais previsível
- **ALOHA**: alta latência

### Taxa de perda de pacotes
- **CSMA/CD**: baixa em carga normal, mas pode aumentar
- **Token Passing**: baixa
- **ALOHA**: alta

### Jitter
- **CSMA/CD**: maior variação
- **Token Passing**: menor variação
- **ALOHA**: maior variação

### Relação com QoS
- **Baixa latência**: Token Passing e redes determinísticas
- **Alta taxa de transferência**: Ethernet comutada
- **Alta disponibilidade**: protocolos redundantes, como STP



## 7. Interconexão de Redes

- Interconexão é a ligação entre **redes diferentes**.
- Surge da necessidade de permitir comunicação entre usuários de redes distintas.
- A Internet é o maior exemplo de interconexão.

### Objetivos da interconexão
- permitir comunicação entre redes diferentes
- compartilhar recursos
- aumentar alcance da infraestrutura
- melhorar resiliência da rede
- criar rotas alternativas

### Desafios da interconexão
- **heterogeneidade**: redes diferentes usam tecnologias diferentes
- **escalabilidade**: redes maiores ficam mais complexas
- diferenças em:
  - endereçamento
  - tamanho de pacotes
  - serviço orientado ou não à conexão
  - confiabilidade
  - segurança
  - qualidade de serviço



## 8. Dispositivos de interconexão

### Repetidores e hubs
- Operam na **camada física**
- Apenas movem bits
- Não analisam protocolos superiores

### Bridges e switches
- Operam na **camada de enlace**
- Trabalham com quadros e endereços MAC
- São melhores para conectar redes do mesmo tipo

### Roteadores
- Operam na **camada de rede**
- São os principais dispositivos para interconectar redes diferentes
- Trabalham com pacotes e endereços IP



## 9. Camada comum e IP

- Para interligar redes diferentes, é importante ter uma **camada comum lógica**.
- Essa camada comum é, na prática, o **protocolo IP**.
- O IP oferece um formato de pacote universal reconhecido pelos roteadores.

### Observações
- Outros protocolos existiram, como:
  - IPX
  - SNA
  - AppleTalk
- Hoje o IP é o principal.
- **IPv4 e IPv6 não são diretamente compatíveis**.



## 10. Exemplo de interconexão

Um exemplo mostrado no material envolve:
- rede **802.11**
- rede **MPLS**
- rede **Ethernet**

### Ideia principal
- O pacote sai da rede 802.11
- passa por uma rede MPLS intermediária
- chega à rede Ethernet

### O que pode acontecer no caminho
- mudança de tecnologia de rede
- necessidade de circuito virtual no MPLS
- fragmentação do pacote ao entrar em uma rede com MTU menor
- remontagem no destino



## 11. Roteador x Switch

### Switch
- Trabalha com o **quadro inteiro**
- Usa **endereço MAC**
- Não precisa entender o protocolo de rede

### Roteador
- Remove o pacote do quadro
- Analisa o **endereço de rede (IP)**
- Decide o próximo salto

### Resumo da diferença
- **Switch**: comuta quadros na camada de enlace
- **Roteador**: roteia pacotes na camada de rede



## 12. Roteador multiprotocolo

- É um roteador capaz de lidar com **mais de um protocolo de rede**.
- Pode usar tabelas de roteamento diferentes para protocolos diferentes.

### Problemas
- Traduzir protocolos diferentes é difícil
- Muitas conversões são incompletas
- Exemplo clássico: dificuldade de compatibilizar **IPv4 e IPv6**



## 13. Tunelamento

- Tunelamento é uma técnica usada para transportar dados de um protocolo através de uma rede com outro protocolo.
- Funciona encapsulando **um pacote dentro de outro pacote**.

### Exemplo
- Uma rede IPv6 em Paris precisa se comunicar com uma rede IPv6 em Londres.
- Entre elas existe uma rede IPv4.
- O roteador encapsula o pacote IPv6 dentro de um pacote IPv4.
- No outro lado, o roteador remove o cabeçalho IPv4 e entrega o pacote IPv6 original.

### Vantagem
- Permite interligar redes isoladas usando uma rede intermediária diferente.

### Desvantagem
- Os hosts dentro do túnel não podem ser acessados no meio do caminho.
- Só as extremidades do túnel enxergam o pacote original.



## 14. Fragmentação de pacotes

- Fragmentação é a divisão de um pacote grande em partes menores chamadas **fragmentos**.
- Isso acontece quando a próxima rede não suporta o tamanho original do pacote.

### MTU
- O tamanho máximo de pacote que uma rede suporta é chamado de **MTU (Maximum Transmission Unit)**.

### Etapas da fragmentação
1. O roteador verifica o tamanho do pacote
2. Compara com o MTU da interface de saída
3. Se o pacote for maior, ele é fragmentado
4. Cada fragmento recebe um novo cabeçalho IP
5. Os fragmentos são enviados separadamente
6. No destino, os fragmentos são remontados

### Informações importantes no cabeçalho
- **ID do pacote**
- **Offset do fragmento**
- **Flag “mais fragmentos”**

### Limitações
- aumenta a sobrecarga
- aumenta a latência
- se um fragmento se perder, o pacote todo pode ser perdido

### Observação importante
- Em redes modernas, a fragmentação é evitada sempre que possível.
- No **IPv6**, roteadores não fazem fragmentação intermediária.
- Para evitar isso, usa-se **Path MTU Discovery (PMTUD)**.
