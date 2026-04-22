<<<<<<< HEAD
# Introdução ao LINUX

**O que é um Sistema Operacional (SO) ?**

- O **SO** é o software que gerencia todo o **hardware e software** do computador.

⋆˙⟡ Ele atua como um **intermediário** entre o usuário e a máquina.

**Funções principais:** 

- Gerencia **processos** em execução.
- Controla o uso da **memória RAM**.
- Organiza **arquivos e diretórios**.
- Coordena o uso de **dispositivos** (teclado, mouse, impressora).
- Oferece uma **interface** (GUI ou CLI) para o usuário interagir.

**Tipos de interface:**

**⤷ ゛GUI — Graphical User Interface  ˎˊ˗**

- Interface visual com janelas, ícones e menus.
- **Vantagens:** fácil, intuitiva e visual.
- **Desvantagens:** consome mais memória e é ruim pra automação.

**⤷ ゛CLI — Command Line Interface  ˎˊ˗**

- Interface baseada em **comandos de texto**.
- **Vantagens:** rápida, leve e poderosa.
- **Desvantagens:** exige memorização e cuidado com erros.

### **LINUX**

- Criado em **1991** por **Linus Torvalds**.
- Baseado no conceito de **software livre** e **colaboração comunitária**.
- Usado em **servidores, supercomputadores, Android e sistemas embarcados**.

**Componentes principais:** 

- **Kernel:** o núcleo que conversa com o hardware.
- **Shell (Terminal):** interpreta os comandos do usuário.
- **FHS (Estrutura de Diretórios):** organiza os arquivos do sistema.

**𐔌   .  ⋮ Distribuições LINUX .ᐟ  ֹ   ₊ ꒱**

- As **distros** são versões completas do Linux (kernel + programas + interface).
    - Cada uma é adaptada para um tipo de usuário.

*exemplos:*

- **Ubuntu:** fácil e amigável, ideal pra iniciantes.
- **Linux Mint:** simples e parecido com Windows.
- **Fedora:** moderno e inovador, voltado pra profissionais.
- **Debian:** super estável, usado em servidores.

**⋆˚࿔  Comandos Básicos 𝜗𝜚˚⋆**

| **Comando** | **Função** |  **Exemplo** |
| --- | --- | --- |
| `pwd` | Mostra o diretório atual | `pwd` |
| `ls` | Lista arquivos e pastas | `ls -l` |
| `cd` | Muda de diretório | `cd Documentos` |
| `mkdir` | Cria uma pasta nova | `mkdir projetos` |
| `touch` | Cria um arquivo vazio | `touch resumo.txt` |
| `cp` | Copia arquivos/pastas | `cp a.txt b.txt` |
| `mv` | Move ou renomeia | `mv a.txt pasta/` |
| `rm` | Remove arquivos | `rm a.txt` |

**⋆˚࿔  Leitura e Edição de Arquivos 𝜗𝜚˚⋆**

| **Comando** |  **Função** | **Exemplo** |
| --- | --- | --- |
| `cat` | Mostra o conteúdo completo | `cat arquivo.txt` |
| `less` | Lê arquivos grandes (setas ↑↓, sai com `q`) | `less arquivo.txt` |
| `head` | Mostra as 10 primeiras linhas | `head arquivo.txt` |
| `tail` | Mostra as 10 últimas linhas | `tail arquivo.txt` |
| `echo` | Escreve texto em arquivo | `echo "Oi" > texto.txt` |

> **Dica:**
> 
> - `>` → cria/substitui o arquivo
> - `>>` → adiciona texto ao final

**⋆˚࿔  Permissões de Arquivos (cmod) 𝜗𝜚˚⋆**

Cada arquivo tem 3 grupos de acesso:

- 👤 **Dono (u)**
- 👥 **Grupo (g)**
- 🌐 **Outros (o)**

**Tipos de permissão:**

- `r` → leitura
- `w` → escrita
- `x` → execução

**Modo Numérico:**

- `r=4`, `w=2`, `x=1`
- *Exemplo:*
    - `chmod 755 script.sh` → dono pode tudo, outros só leem e executam.

**Modo Simbólico:**

- `chmod u+x arquivo` → adiciona execução ao dono.
- `chmod g-w arquivo` → remove escrita do grupo.

**⋆˚࿔  Monitoramento do Sistema 𝜗𝜚˚⋆**
| **Comando** | **Função** |
| --- | --- |
| `ps` | Mostra processos em execução |
| `top` | Exibe uso de CPU e memória em tempo real |
| `uptime` | Mostra tempo ligado e carga do sistema |
| `free -h` | Mostra uso da memória RAM |
=======
# Introdução ao LINUX

**O que é um Sistema Operacional (SO) ?**

- O **SO** é o software que gerencia todo o **hardware e software** do computador.

⋆˙⟡ Ele atua como um **intermediário** entre o usuário e a máquina.

**Funções principais:** 

- Gerencia **processos** em execução.
- Controla o uso da **memória RAM**.
- Organiza **arquivos e diretórios**.
- Coordena o uso de **dispositivos** (teclado, mouse, impressora).
- Oferece uma **interface** (GUI ou CLI) para o usuário interagir.

**Tipos de interface:**

**⤷ ゛GUI — Graphical User Interface  ˎˊ˗**

- Interface visual com janelas, ícones e menus.
- **Vantagens:** fácil, intuitiva e visual.
- **Desvantagens:** consome mais memória e é ruim pra automação.

**⤷ ゛CLI — Command Line Interface  ˎˊ˗**

- Interface baseada em **comandos de texto**.
- **Vantagens:** rápida, leve e poderosa.
- **Desvantagens:** exige memorização e cuidado com erros.

### **LINUX**

- Criado em **1991** por **Linus Torvalds**.
- Baseado no conceito de **software livre** e **colaboração comunitária**.
- Usado em **servidores, supercomputadores, Android e sistemas embarcados**.

**Componentes principais:** 

- **Kernel:** o núcleo que conversa com o hardware.
- **Shell (Terminal):** interpreta os comandos do usuário.
- **FHS (Estrutura de Diretórios):** organiza os arquivos do sistema.

**𐔌   .  ⋮ Distribuições LINUX .ᐟ  ֹ   ₊ ꒱**

- As **distros** são versões completas do Linux (kernel + programas + interface).
    - Cada uma é adaptada para um tipo de usuário.

*exemplos:*

- **Ubuntu:** fácil e amigável, ideal pra iniciantes.
- **Linux Mint:** simples e parecido com Windows.
- **Fedora:** moderno e inovador, voltado pra profissionais.
- **Debian:** super estável, usado em servidores.

**⋆˚࿔  Comandos Básicos 𝜗𝜚˚⋆**

| **Comando** | **Função** |  **Exemplo** |
| --- | --- | --- |
| `pwd` | Mostra o diretório atual | `pwd` |
| `ls` | Lista arquivos e pastas | `ls -l` |
| `cd` | Muda de diretório | `cd Documentos` |
| `mkdir` | Cria uma pasta nova | `mkdir projetos` |
| `touch` | Cria um arquivo vazio | `touch resumo.txt` |
| `cp` | Copia arquivos/pastas | `cp a.txt b.txt` |
| `mv` | Move ou renomeia | `mv a.txt pasta/` |
| `rm` | Remove arquivos | `rm a.txt` |

**⋆˚࿔  Leitura e Edição de Arquivos 𝜗𝜚˚⋆**

| **Comando** |  **Função** | **Exemplo** |
| --- | --- | --- |
| `cat` | Mostra o conteúdo completo | `cat arquivo.txt` |
| `less` | Lê arquivos grandes (setas ↑↓, sai com `q`) | `less arquivo.txt` |
| `head` | Mostra as 10 primeiras linhas | `head arquivo.txt` |
| `tail` | Mostra as 10 últimas linhas | `tail arquivo.txt` |
| `echo` | Escreve texto em arquivo | `echo "Oi" > texto.txt` |

> **Dica:**
> 
> - `>` → cria/substitui o arquivo
> - `>>` → adiciona texto ao final

**⋆˚࿔  Permissões de Arquivos (cmod) 𝜗𝜚˚⋆**

Cada arquivo tem 3 grupos de acesso:

- 👤 **Dono (u)**
- 👥 **Grupo (g)**
- 🌐 **Outros (o)**

**Tipos de permissão:**

- `r` → leitura
- `w` → escrita
- `x` → execução

**Modo Numérico:**

- `r=4`, `w=2`, `x=1`
- *Exemplo:*
    - `chmod 755 script.sh` → dono pode tudo, outros só leem e executam.

**Modo Simbólico:**

- `chmod u+x arquivo` → adiciona execução ao dono.
- `chmod g-w arquivo` → remove escrita do grupo.

**⋆˚࿔  Monitoramento do Sistema 𝜗𝜚˚⋆**
| **Comando** | **Função** |
| --- | --- |
| `ps` | Mostra processos em execução |
| `top` | Exibe uso de CPU e memória em tempo real |
| `uptime` | Mostra tempo ligado e carga do sistema |
| `free -h` | Mostra uso da memória RAM |
>>>>>>> de8e56e (Fundamentos em SI)
