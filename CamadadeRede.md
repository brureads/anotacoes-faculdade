# Camada de Rede, IP, Sub-rede, VLSM e Interconexão

## 1. Camada de Rede

- A **camada de rede** é a camada 3 do modelo OSI.
- Ela é responsável pelo **direcionamento e encaminhamento de pacotes** entre redes diferentes.
- O principal equipamento dessa camada é o **roteador**.
- O roteador conecta redes distintas e escolhe o melhor caminho para os pacotes chegarem ao destino.

### Funções principais
- endereçamento lógico
- roteamento
- encaminhamento de pacotes
- interligação de redes diferentes
- controle de percurso entre origem e destino



## 2. Endereço IP

- O endereço **IP** identifica logicamente um dispositivo em uma rede.
- Diferente do **MAC**, que atua na camada de enlace e identifica fisicamente a interface, o IP atua em um nível mais alto.
- O IP permite a **comunicação entre redes diferentes**.

### Funções do endereço IP
- **Identificação**: cada dispositivo possui um IP
- **Roteamento**: os roteadores usam o IP para escolher caminhos
- **Subnetting**: permite dividir uma rede em sub-redes menores



## 3. MAC x IP

### Endereço MAC
- atua na **camada de enlace**
- é um endereço **físico**
- normalmente é atribuído pelo **fabricante**
- tem alcance **local**
- identifica a interface de rede

### Endereço IP
- atua na **camada de rede**
- é um endereço **lógico**
- pode ser atribuído manualmente ou por **DHCP**
- tem alcance maior, podendo ser usado entre redes
- identifica o dispositivo e ajuda no roteamento



## 4. IPv4 e IPv6

### IPv4
- possui **32 bits**
- é dividido em **4 octetos**
- exemplo: `192.168.1.10`

### IPv6
- foi criado por causa da escassez de endereços IPv4
- possui **128 bits**
- usa notação **hexadecimal**
- oferece um espaço de endereçamento muito maior



## 5. ARP

- O **ARP (Address Resolution Protocol)** faz a tradução entre **endereço IP** e **endereço MAC**.
- Ele é usado quando um dispositivo quer descobrir o MAC correspondente a um IP na mesma rede.

### Funcionamento do ARP
- o dispositivo consulta sua tabela ARP
- se já souber o MAC, envia direto
- se não souber, envia uma solicitação ARP
- o dispositivo dono do IP responde com seu MAC
- a tabela ARP é atualizada

### Ideia principal
- **IP identifica logicamente**
- **MAC identifica fisicamente**
- **ARP liga os dois**



## 6. Tipos de endereços IP

### Públicos
- usados por dispositivos conectados diretamente à internet

### Privados
- usados em redes locais
- não são roteados diretamente na internet

### Multicast
- usados para enviar dados a um grupo de dispositivos

### Broadcast
- usados para enviar dados a todos os dispositivos da rede



## 7. Classes de endereços IP

> Observação: o material apresenta classes A, B, C, D e E, mas também informa que esse modelo é considerado obsoleto e foi substituído pelo CIDR.

### Classe A
- faixa: `1.0.0.0` a `126.255.255.255`
- máscara padrão: `255.0.0.0`
- rede grande
- 8 bits de rede e 24 bits de host
- hosts por rede: `2²⁴ - 2 = 16.777.214`

### Classe B
- faixa: `128.0.0.0` a `191.255.255.255`
- máscara padrão: `255.255.0.0`
- rede média
- 16 bits de rede e 16 bits de host
- hosts por rede: `2¹⁶ - 2 = 65.534`

### Classe C
- faixa: `192.0.0.0` a `223.255.255.255`
- máscara padrão: `255.255.255.0`
- rede pequena
- 24 bits de rede e 8 bits de host
- hosts por rede: `2⁸ - 2 = 254`

### Classe D
- faixa: `224.0.0.0` a `239.255.255.255`
- usada para **multicast**

### Classe E
- faixa: `240.0.0.0` a `255.255.255.255`
- reservada para fins experimentais



## 8. Separação entre rede e host

Em um endereço IPv4, uma parte identifica a **rede** e outra identifica o **host**.

### Exemplos
- Classe A: `10.1.1.10`
  - rede: `10`
  - host: `1.1.10`

- Classe B: `172.16.10.1`
  - rede: `172.16`
  - host: `10.1`

- Classe C: `192.168.0.1`
  - rede: `192.168.0`
  - host: `1`



## 9. IPs privados ou restritos

- São endereços reservados para uso interno em redes locais.
- **Não podem ser roteados diretamente na internet pública**.
- São muito usados em:
  - redes domésticas
  - redes corporativas
  - laboratórios

### Faixas privadas IPv4
- `10.0.0.0 a 10.255.255.255` → `/8`
- `172.16.0.0 a 172.31.255.255` → `/12`
- `192.168.0.0 a 192.168.255.255` → `/16`

### Importância dos IPs privados
- economizam endereços IPv4
- aumentam a segurança
- dão flexibilidade para redes internas

### Como acessam a internet
- por meio de **NAT (Network Address Translation)** no roteador/gateway



## 10. IPs com funções específicas

### Loopback
- faixa associada a `127.0.0.0`
- usada para testes internos
- exemplo comum: `127.0.0.1`

### APIPA
- faixa: `169.254.0.1` a `169.254.255.254`
- usada quando o DHCP falha
- permite comunicação local limitada

### 0.0.0.0
- indica ausência de endereço definido
- pode ser usado temporariamente na inicialização
- também pode significar “todas as interfaces”

### 255.255.255.255
- endereço de **broadcast limitado**
- envia dados para todos os dispositivos da rede local
- não é roteado para fora da rede



## 11. Máscara de sub-rede

- A máscara de sub-rede define **qual parte do IP pertence à rede e qual parte pertence ao host**.
- Ela funciona como um filtro.

### Exemplo
- IP: `192.168.1.10`
- Máscara: `255.255.255.0`
- Isso significa que:
  - `192.168.1` identifica a rede
  - o último octeto identifica os hosts

### Regra importante
- Uma máscara válida deve ter **1s contínuos seguidos de 0s**
- Exemplo válido:
  - `11111111.11111111.11111111.00000000`
- Exemplo inválido:
  - `11111111.00001111.00000000.00000000`

### Valores válidos em octetos da máscara
- `255`
- `254`
- `252`
- `248`
- `240`
- `224`
- `192`
- `128`
- `0`



## 12. Prefixos CIDR mais comuns

### /24
- máscara: `255.255.255.0`
- 8 bits para host
- hosts disponíveis: `254`

### /25
- máscara: `255.255.255.128`
- 7 bits para host
- hosts disponíveis: `126`

### /27
- máscara: `255.255.255.224`
- 5 bits para host
- hosts disponíveis: `30`

### /28
- máscara: `255.255.255.240`
- 4 bits para host
- hosts disponíveis: `14`



## 13. Sub-rede

- Uma **sub-rede** é uma divisão lógica de uma rede maior.
- Serve para organizar melhor a rede e controlar melhor o tráfego.

### Vantagens
- melhora a organização
- reduz congestionamento
- aumenta a segurança
- facilita o gerenciamento

### Exemplo
Rede original:
- `192.168.1.0/24`

Divisão em duas sub-redes:
- `192.168.1.0/25`
- `192.168.1.128/25`



## 14. Cálculo de hosts

### Fórmula
- **Número de hosts = 2^n - 2**
- onde **n** é a quantidade de bits para hosts

### Por que subtrair 2?
- um endereço é reservado para a **rede**
- outro é reservado para o **broadcast**



## 15. Exemplo de sub-rede com /27

### Dados do exercício
- IP: `192.168.40.26`
- Máscara: `255.255.255.224`
- Gateway: `192.168.40.25`

### Passos principais
- `255.255.255.224` corresponde a **/27**
- o salto é:
  - `256 - 224 = 32`

### Sub-redes geradas
- `192.168.40.0`
- `192.168.40.32`
- `192.168.40.64`
- `192.168.40.96`
- ...

### Primeira sub-rede
- rede: `192.168.40.0`
- hosts: `192.168.40.1` até `192.168.40.30`
- broadcast: `192.168.40.31`

Como o IP do professor é `192.168.40.26`, ele está nessa primeira sub-rede.  
Então outro computador poderia usar, por exemplo:
- `192.168.40.27`
- `192.168.40.28`
- `192.168.40.29`
- `192.168.40.30`



## 16. VLSM

- **VLSM (Variable Length Subnet Masking)** permite criar sub-redes com tamanhos diferentes.
- Isso evita desperdício de IPs.
- Em vez de usar a mesma máscara para tudo, cada setor pode receber uma máscara adequada ao número de hosts.

### Vantagens do VLSM
- melhor aproveitamento dos IPs
- mais flexibilidade
- mais escalabilidade
- menos desperdício

### Exemplo do material
Rede base:
- `192.168.10.0/24`

Necessidades:
- Laboratório A: 80 hosts
- Laboratório B: 55 hosts
- Marketing: 28 hosts
- Financeiro: 12 hosts

### Máscaras escolhidas
- Laboratório A → `/25` → `255.255.255.128`
- Laboratório B → `/26` → `255.255.255.192`
- Marketing → `/27` → `255.255.255.224`
- Financeiro → `/28` → `255.255.255.240`

### Tabela resultante
- `192.168.10.0` → hosts `1 a 126` → broadcast `192.168.10.127`
- `192.168.10.128` → hosts `129 a 190` → broadcast `192.168.10.191`
- `192.168.10.192` → hosts `193 a 222` → broadcast `192.168.10.223`
- `192.168.10.224` → hosts `225 a 238` → broadcast `192.168.10.239`



## 17. Pacote de dados na camada de rede

- Na camada de rede, a informação trafega em **pacotes**.
- Cada pacote contém:
  - endereço IP de origem
  - endereço IP de destino
  - protocolo
  - número de sequência
  - checksum

### Número de sequência
- ajuda a garantir a ordem correta dos dados

### Checksum
- verifica se houve corrupção de dados durante a transmissão



## 18. Função do roteador

- O roteador determina o **melhor caminho** para os pacotes.
- Ele usa o endereço IP de destino e consulta sua **tabela de roteamento**.

### Etapas básicas do funcionamento
1. recebe o pacote
2. lê o IP de destino
3. consulta a tabela de roteamento
4. escolhe o próximo salto (**next hop**)
5. encaminha o pacote
6. pode fragmentar o pacote se necessário
7. decrementa o TTL

### TTL
- **Time to Live**
- diminui a cada salto
- quando chega a zero, o pacote é descartado
- evita loops infinitos



## 19. Tabela de roteamento

- É como um mapa usado pelo roteador.
- Cada rota geralmente contém:
  - rede de destino
  - máscara de sub-rede
  - gateway
  - métrica

### Métrica
- valor numérico usado para comparar rotas
- rotas com menor métrica tendem a ser preferidas



## 20. Importância do roteamento

- conecta redes diferentes
- permite a existência da internet
- ajuda na segurança com regras de firewall
- otimiza o tráfego
- melhora disponibilidade e adaptação a falhas



## 21. Protocolos de roteamento

### RIP
- protocolo de vetor de distância
- usa contagem de saltos
- troca tabelas a cada 30 segundos
- máximo de 15 saltos
- simples, mas limitado
- melhor para redes pequenas

### OSPF
- protocolo de estado de enlace
- usa algoritmo de Dijkstra
- convergência rápida
- mais escalável
- ideal para redes grandes

### BGP
- usado entre sistemas autônomos na internet
- é o protocolo que sustenta o roteamento entre provedores
- altamente escalável
- convergência mais lenta
- muito importante para ISPs e grandes redes



## 22. Interconexão de redes

- Interconexão é o processo de conectar redes diferentes para que possam trocar dados.
- Pode envolver LANs, WANs e MANs.
- É essencial quando há diferentes provedores, diferentes redes e necessidade de comunicação entre elas.

### Objetivo
- permitir comunicação entre redes distintas
- compartilhar recursos
- expandir a infraestrutura de forma eficiente



## 23. Componentes de interconexão

### Roteadores
- conectam redes diferentes
- operam na camada 3

### Switches
- conectam dispositivos dentro da mesma rede local
- operam na camada 2

### Gateways
- conectam redes com protocolos diferentes
- podem traduzir protocolos
- podem fazer NAT, filtragem e segurança

### Bridges
- conectam redes locais para funcionar como uma única rede

### Proxies
- atuam como intermediários entre cliente e servidor
- ajudam em segurança, cache e controle de tráfego



## 24. Gateway

- O gateway funciona como um “portal” entre redes diferentes.
- Ele pode:
  - traduzir protocolos
  - rotear pacotes
  - aplicar filtragem e segurança
  - fazer NAT

### Exemplos
- roteador doméstico
- firewall
- servidor VPN



## 25. Exemplos de interconexão

- filiais de empresas conectadas entre si
- provedores de internet interligando suas redes
- campus universitários integrando laboratórios, departamentos e bibliotecas


## 26. Topologias de rede

- O material comenta a evolução das topologias em direção a estruturas mais resilientes.
- As redes modernas buscam:
  - mais velocidade
  - mais redundância
  - menos ponto único de falha

### Topologia em malha (Mesh)
- vários dispositivos conectados entre si
- não há um único ponto central de falha
- se um caminho falhar, outro pode ser usado
- aumenta a resiliência e a confiabilidade

### Vantagens
- caminhos redundantes
- fácil expansão
- maior disponibilidade
- muito usada em data centers e redes mesh Wi-Fi
