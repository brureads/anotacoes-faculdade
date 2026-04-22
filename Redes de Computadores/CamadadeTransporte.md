# Camada de Transporte

## 1. Revisão rápida da Camada 3

Antes de entrar na camada de transporte, o material relembra alguns protocolos importantes da camada de rede:

### IP
- É o principal protocolo da Internet.
- Faz o **endereçamento** e a **fragmentação de pacotes**.
- **IPv4**:
  - usa endereços de 32 bits
  - depende bastante de NAT
- **IPv6**:
  - usa endereços de 128 bits
  - foi criado para resolver a escassez de IPs
  - oferece maior espaço de endereçamento e mais recursos nativos de segurança
- O IP é **best effort**, ou seja, **não garante a entrega**.

### ICMP
- Não transporta dados do usuário.
- Serve para:
  - reportar erros
  - fornecer informações operacionais
- É usado em comandos como:
  - `ping`
  - `tracert`

### ARP
- Faz a ponte entre a camada 3 e a camada 2.
- Resolve um **IP** em um **MAC**.

### Protocolos de roteamento
- **OSPF**
- **BGP**
- **RIP**



## 2. OSPF e RIP

O material também faz uma revisão dos protocolos de roteamento.

### OSPF
- Usa o algoritmo de **Dijkstra**
- Escolhe o caminho com **menor custo**
- O custo é baseado em **largura de banda**
- É muito usado em redes corporativas
- Tem visão mais completa da rede

### RIP
- Usa o algoritmo de **Bellman-Ford**
- Escolhe o caminho com **menor número de saltos**
- Não considera a velocidade do link
- Limite de **15 saltos**
- É mais simples, mas menos eficiente em redes maiores

### Comparação rápida
- **OSPF**:
  - métrica: custo
  - melhor para redes grandes
  - atualiza quando há mudanças
- **RIP**:
  - métrica: saltos
  - melhor para redes pequenas
  - atualiza periodicamente



## 3. Camada de Transporte

- A **camada de transporte** é a **camada 4 do modelo OSI**.
- Sua função principal é garantir uma comunicação **eficiente e confiável entre hosts**.
- Ela cuida da transmissão correta dos dados, independentemente da rede física usada.

### Funções principais
- segmentação e reagregação
- controle de fluxo
- controle de erros
- multiplexação e demultiplexação
- controle de conexão
- controle de congestionamento



## 4. Segmentação x Fragmentação

Esse é um ponto muito importante.

### Segmentação
- Acontece na **camada 4**
- Geralmente é feita pelo **TCP**
- Ocorre no **host de origem**
- Divide um grande fluxo de dados em **segmentos**
- O tamanho depende do **MSS**
- Se um segmento for perdido, o TCP pode retransmiti-lo

### Fragmentação
- Acontece na **camada 3**
- É feita pelo **IP**
- Pode ocorrer no host de origem ou em roteadores
- Acontece por causa do **MTU**
- Divide um pacote IP em **fragmentos**

### Diferença principal
- **Segmentação** = organização dos dados para transporte
- **Fragmentação** = adaptação do pacote ao limite físico da rede

### Observação importante
- No **IPv4**, roteadores podem fragmentar
- No **IPv6**, roteadores **não** fragmentam



## 5. TCP

- O **TCP (Transmission Control Protocol)** é um protocolo:
  - **confiável**
  - **orientado à conexão**
- Ele garante:
  - entrega correta
  - entrega em ordem
  - sem perda
  - sem duplicação

### Características do TCP
- confiável: **sim**
- orientado à conexão: **sim**
- controle de fluxo: **sim**
- controle de congestionamento: **sim**
- correção de erros: **sim**
- comunicação: **unicast**



## 6. Handshake de três vias

Antes de enviar dados, o TCP cria uma conexão.

### Etapas
1. **SYN**
   - o cliente inicia a conexão
2. **SYN-ACK**
   - o servidor responde confirmando
3. **ACK**
   - o cliente confirma

### Resultado
- a conexão é estabelecida
- os dois lados ficam prontos para trocar dados



## 7. Funcionalidades do TCP

### Conexão confiável
- estabelece uma sessão lógica entre os dispositivos

### Transmissão confiável
- usa:
  - números de sequência
  - ACKs
- se um segmento for perdido, ele é retransmitido

### Controle de fluxo
- evita sobrecarregar o receptor

### Controle de congestionamento
- ajusta a taxa de envio conforme a condição da rede

### Entrega ordenada
- garante que os dados cheguem na ordem correta

### Segmentação e reagregação
- divide os dados em segmentos menores
- reorganiza tudo corretamente no destino



## 8. Uso do TCP

O TCP é indicado para aplicações que precisam de alta confiabilidade.

### Exemplos
- HTTP / HTTPS
- FTP
- SMTP
- SSH

### Ideia principal
- quando perder dados é um problema, o TCP é a melhor escolha



## 9. UDP

- O **UDP (User Datagram Protocol)** é um protocolo:
  - **não orientado à conexão**
  - **não confiável**
- Ele prioriza a **velocidade** e a **baixa latência**

### Características do UDP
- confiável: **não**
- orientado à conexão: **não**
- controle de fluxo: **não**
- controle de congestionamento: **não**
- correção de erros: **não**
- comunicação:
  - unicast
  - broadcast
  - multicast



## 10. Funcionalidades do UDP

### Sem conexão
- não faz handshake
- envia os dados diretamente

### Baixa sobrecarga
- cabeçalho menor que o TCP
- menos processamento

### Entrega não garantida
- os dados podem:
  - se perder
  - chegar fora de ordem
  - não chegar

### Sem controle de fluxo e congestionamento
- a aplicação precisa lidar com isso, se necessário



## 11. Uso do UDP

O UDP é ideal quando a latência importa mais que a confiabilidade.

### Exemplos
- jogos online
- streaming de vídeo
- VoIP
- transmissões ao vivo

### Ideia principal
- melhor perder um pacote do que travar toda a comunicação



## 12. Comparação entre TCP e UDP

### TCP
- confiável
- orientado à conexão
- usa handshake
- faz controle de fluxo
- faz controle de congestionamento
- maior overhead
- usado em aplicações que exigem precisão

### UDP
- não confiável
- sem conexão
- sem handshake
- sem controle de fluxo
- sem controle de congestionamento
- menor overhead
- usado em aplicações em tempo real



## 13. Outros protocolos da camada de transporte

### SCTP
- combina características do TCP e do UDP
- é confiável como o TCP
- suporta múltiplos fluxos independentes
- usado em telecomunicações e VoIP

### DCCP
- é sem conexão
- possui controle de congestionamento
- foi pensado para aplicações em tempo real



## 14. Funções principais da camada de transporte

### 1. Segmentação e reagregação
- divide grandes blocos em partes menores
- reorganiza no destino

### 2. Controle de fluxo
- regula quanto o emissor pode enviar
- evita sobrecarga no receptor

### 3. Controle de erros
- usa checksums
- pode solicitar retransmissão

### 4. Multiplexação e demultiplexação
- usa portas para identificar aplicações
- permite várias comunicações ao mesmo tempo

### 5. Controle de conexão
- pode ser:
  - orientado à conexão (TCP)
  - sem conexão (UDP)



## 15. Tamanho dos pacotes em TCP e UDP

- O tamanho dos pacotes **não é fixo** e **não depende apenas do protocolo**.
- Ele depende de:
  - aplicação
  - configuração da rede
  - MTU

### Importante
- o UDP **não é mais rápido porque usa pacotes menores**
- ele é mais rápido porque tem **menos mecanismos de controle**



## 16. UDP em transmissão de vídeo

O material destaca o uso do UDP em vídeos em tempo real.

### O que o UDP faz
- envia dados continuamente
- não espera confirmação
- não verifica ordem de chegada
- não retransmite automaticamente

### Vantagem
- reduz latência

### Desvantagem
- pode haver perda de pacotes

### Resultado prático
- em vídeo e áudio ao vivo, isso costuma ser melhor do que esperar retransmissões



## 17. Controle de fluxo

- O **controle de fluxo** evita que o transmissor envie dados mais rápido do que o receptor consegue processar.
- Ele é importante principalmente no **TCP**.

### Objetivos
- evitar perda de dados
- evitar sobrecarga do receptor
- melhorar a eficiência da comunicação



## 18. Como funciona o controle de fluxo no TCP

### 1. Estabelecimento da conexão
- no handshake, os lados trocam informações
- entre elas, o tamanho da **janela de recepção**

### 2. Envio em segmentos
- o transmissor envia dados em segmentos TCP
- respeitando a janela informada pelo receptor

### 3. Recepção e ACKs
- o receptor recebe os dados
- envia ACKs confirmando recebimento

### 4. Ajuste dinâmico da janela
- se o receptor estiver sobrecarregado, ele reduz a janela
- se estiver livre, pode aumentá-la

### 5. Limitação do envio
- o transmissor só envia a quantidade permitida pela janela

### 6. Retransmissão
- se não chegar ACK no tempo esperado, o transmissor retransmite

### 7. Janela zero
- o receptor pode informar **janela zero**
- isso manda o transmissor pausar o envio

### 8. Finalização
- ao fim da comunicação, o TCP encerra a conexão com **four-way handshake**



## 19. Importância do controle de fluxo

- evita perda de dados
- melhora desempenho
- torna a comunicação mais confiável
- ajuda o receptor a trabalhar no seu próprio ritmo

### Controle de fluxo no UDP
- o UDP **não implementa controle de fluxo**



## 20. Controle de congestionamento

- O **controle de congestionamento** evita que a rede fique sobrecarregada.
- É um mecanismo fundamental do **TCP**.

### Objetivos
- reduzir perdas
- reduzir latência
- evitar colapso da rede
- ajustar a taxa de transmissão



## 21. Janela de congestionamento (cwnd)

- O TCP usa a **janela de congestionamento (cwnd)** para controlar quantos dados podem ser enviados sem ACK.
- Essa janela começa pequena e vai sendo ajustada conforme a resposta da rede.



## 22. Slow Start

- O TCP começa enviando poucos pacotes.
- À medida que recebe ACKs, aumenta rapidamente a quantidade enviada.

### Ideia principal
- crescer aos poucos no início
- testar a capacidade da rede sem causar congestionamento logo de cara



## 23. Detecção de congestionamento

O TCP percebe congestionamento quando:
- um ACK não chega no tempo esperado
- chegam vários ACKs duplicados

### Quando isso acontece
- ele reduz a taxa de envio
- ajusta sua janela de congestionamento



## 24. Evitação de congestionamento

Depois de detectar congestionamento:
- o TCP para de crescer de forma exponencial
- passa a crescer de forma **linear**

### Resultado
- evita voltar a sobrecarregar a rede muito rápido



## 25. SSThresh

- **SSThresh (Slow Start Threshold)** é o limite usado para decidir entre:
  - slow start
  - congestion avoidance

### Regra
- se `cwnd < SSThresh` → slow start
- se `cwnd > SSThresh` → crescimento linear

### Após congestionamento
- o SSThresh é ajustado para a metade do `cwnd`


## 26. Fast Retransmit e Fast Recovery

### Fast Retransmit
- quando o transmissor recebe **3 ACKs duplicados**
- ele retransmite logo o segmento perdido
- não espera timeout

### Fast Recovery
- após a retransmissão rápida
- o TCP tenta se recuperar sem voltar tão agressivamente ao início


## 27. Resumo final

- A **camada de transporte** é a camada 4 do modelo OSI
- Ela fornece comunicação eficiente entre hosts
- **Segmentação** ocorre na camada 4
- **Fragmentação** ocorre na camada 3
- **TCP** é confiável, orientado à conexão e usa controle de fluxo e congestionamento
- **UDP** é mais simples, rápido e sem garantia de entrega
- O TCP usa:
  - handshake de 3 vias
  - ACKs
  - números de sequência
  - janela de recepção
  - janela de congestionamento
- O UDP é ideal para aplicações em tempo real
- O TCP é ideal para aplicações que exigem entrega correta e ordenada