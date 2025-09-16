# Documento: Diagrama de Comunicação

## Introdução

O diagrama de comunicação (communication diagram) mostra como os objetos interagem entre si em certos cenários específicos. Ele foca nos links entre objetos e na ordem das mensagens trocadas, para cumprir um cenário de uso.

Este documento apresenta quatro cenários, cada um com seu respectivo diagrama de comunicação:

1. Usuário Curti Mensagem
2. Usuário Envia Mensagem de Texto
3. Usuário Bloqueia outro Usuário
4. Gameficação do Aplicativo com Usuário

---

## Elementos Gerais

* **Atores**: Usuário, Sistema (Backend), Banco de Dados
* **Objetos/Instâncias**: Interface de Usuário (UI), Controlador de Mensagens, Controlador de Segurança, Controlador de ..., etc.
* **Links**: Conexões entre objetos para trocas de mensagens
* **Mensagens**: chamadas de método / requisições (ex: `selecionarBloquear()`, `registrarBloqueio()`, etc.)

---

## Metodologia

O Diagrama de Comunicação, também chamado de Diagrama de Colaboração, foi utilizado para representar como os objetos do sistema se relacionam e trocam mensagens. Ele combina aspectos estruturais (semelhante ao Diagrama de Classes) e de interação (semelhante ao Diagrama de Sequência), sendo aplicado a cada cenário definido no projeto.

---


## Cenário 1: Usuário Reage com Emoticon

**Descrição**: Um usuário visualiza uma mensagem em um grupo e reage com uma curtida (👍). A reação é registrada, exibida para todos os participantes e o autor da mensagem é notificado.

**Participantes**:

| Papel        | Instância                    |
| ------------ | ---------------------------- |
| Ator         | Usuário                      |
| Interface    | InterfaceGrupo (UI)          |
| Backend      | ControladorMensagem          |
| Persistência | BancoDeDados                 |
| Informação   | Mensagem (Comunicação)       |
| Notificação  | Notificacao (Infraestrutura) |

**Fluxo de mensagens**:

1. Usuário → InterfaceGrupo: `selecionarCurtida(Mensagem, "👍")`
2. InterfaceGrupo → ControladorMensagem: `registrarCurtida(Mensagem, "👍")`
3. ControladorMensagem → BancoDeDados: `salvarCurtida(Usuario, Mensagem, "👍")`
4. ControladorMensagem → InterfaceGrupo: `atualizarCurtidaVisual(Mensagem, "👍")`
5. ControladorMensagem → Notificacao: `notificarAutor(Mensagem, "Seu post recebeu uma Curtida!")`

**Diagrama de Comunicação**:

![DIAGRAMA DE COMUNICAÇÃO] (../img/.jpg)

---

## Cenário 2: Bloquear um Usuário

**Descrição**: Um usuário decide bloquear outro usuário. O bloqueio é registrado no sistema e confirmado na interface do usuário que realizou a ação.

**Participantes**:

| Papel            | Instância            |
| ---------------- | -------------------- |
| Ator             | Usuario1            |
| Interface        | InterfacePerfil (UI) |
| Backend          | ControladorSeguranca |
| Persistência     | BancoDeDados         |
| Alvo do bloqueio | Usuario2             |

**Fluxo de mensagens**:

1. UsuarioA → InterfacePerfil: `selecionarBloquear(Usuario2)`
2. InterfacePerfil → ControladorSeguranca: `bloquearUsuario(Usuario2)`
3. ControladorSeguranca → BancoDeDados: `registrarBloqueio(Usuario1, Usuario2)`
4. ControladorSeguranca → InterfacePerfil: `confirmarBloqueio()`

**Diagrama de Comunicação**:

![DIAGRAMA DE COMUNICAÇÃO] (../img/.jpg)

---

## Cenário 3: Sistema de Gamificação

**Descrição**: Um usuário conclui uma atividade no aplicativo. A pontuação é registrada, o ranking é atualizado e a nova pontuação é exibida ao usuário.

**Participantes**:

| Papel        | Instância                        |
| ------------ | -------------------------------- |
| Ator         | Usuario                          |
| Interface    | InterfaceApp (UI)                |
| Backend      | ControladorGamificacao           |
| Persistência | AgenteDeDadosGamificacao (Dados) |
| Informação   | Ranking (Gamificação)            |

**Fluxo de mensagens**:

1. Usuario → InterfaceApp: `concluirAtividade()`
2. InterfaceApp → ControladorGamificacao: `registrarPontos()`
3. ControladorGamificacao → AgenteDeDadosGamificacao: `atualizarPontuacao()`
4. ControladorGamificacao → Ranking: `recalcularPosicao()`
5. ControladorGamificacao → InterfaceApp: `mostrarNovaPontuacao()`

**Diagrama de Comunicação**:

![DIAGRAMA DE COMUNICAÇÃO] (../img/.jpg)

---

## Cenário 4: Notificação de Nova Mensagem

**Descrição**: Um usuário envia uma mensagem para outro usuário. A mensagem é salva no banco de dados e o destinatário recebe uma notificação em tempo real.

**Participantes**:

| Papel               | Instância                              |
| ------------------- | -------------------------------------- |
| Ator (Remetente)    | UsuarioA                               |
| Ator (Destinatário) | UsuarioB                               |
| Informação          | Mensagem (Comunicação)                 |
| Persistência        | BancoDeDados                           |
| Notificação         | SistemaDeNotificacoes (Infraestrutura) |

**Fluxo de mensagens**:

1. UsuarioA → Mensagem: `enviar("Oi!")`
2. Mensagem → BancoDeDados: `salvarMensagem()`
3. BancoDeDados → SistemaDeNotificacoes: `novaMensagem(UsuarioB)`
4. SistemaDeNotificacoes → UsuarioB: `pushNotification("Você recebeu uma mensagem!")`

**Diagrama de Comunicação**:

![DIAGRAMA DE COMUNICAÇÃO] (../img/.jpg)

---

## Especificação dos Pacotes e Componentes

### Pacote **Frontend/Interface**

* **InterfaceGrupo**: Permite ao usuário visualizar mensagens em grupos e reagir a elas com emoticons.
* **InterfacePerfil**: Permite ao usuário visualizar perfis de outros usuários e realizar ações de moderação, como bloquear usuários.
* **InterfaceApp**: Disponibiliza funcionalidades do aplicativo, incluindo gamificação, visualização de pontuação e ranking.

### Pacote **Comunicação e Gamificação**

* **ControladorMensagem**: Gerencia as reações dos usuários em mensagens, incluindo curtidas e notificações de reação.
* **ControladorSeguranca**: Gerencia ações de segurança e moderação, como bloqueio de usuários.
* **ControladorGamificacao**: Gerencia pontuação, atividades concluídas e atualização do ranking.
* **Mensagem**: Representa o conteúdo das mensagens enviadas entre usuários.
* **Ranking**: Mantém a posição e pontuação dos usuários no sistema de gamificação.

### Pacote **Dados**

* **BancoDeDados**: Persistência de curtidas, bloqueios, mensagens e pontuações.
* **AgenteDeDadosGamificacao**: Armazena pontuação e histórico de atividades gamificadas.

### Pacote **Infraestrutura**

* **Notificacao**: Envia alertas aos usuários, como notificações de novas mensagens ou curtidas.
* **SistemaDeNotificacoes**: Envia notificações push para usuários destinatários de mensagens.

---

## Relações Principais (Resumo)

| Origem                 | Destino                  | Descrição                                                      |
| ---------------------- | ------------------------ | -------------------------------------------------------------- |
| InterfaceGrupo         | ControladorMensagem      | Reage a mensagens com emoticons.                               |
| ControladorMensagem    | BancoDeDados             | Persiste reações (curtidas) dos usuários.                      |
| ControladorMensagem    | InterfaceGrupo           | Atualiza visualmente as curtidas na interface.                 |
| ControladorMensagem    | Notificacao              | Notifica o autor da mensagem sobre novas reações.              |
| InterfacePerfil        | ControladorSeguranca     | Solicita bloqueio de outro usuário.                            |
| ControladorSeguranca   | BancoDeDados             | Registra o bloqueio entre usuários.                            |
| ControladorSeguranca   | InterfacePerfil          | Confirma bloqueio realizado.                                   |
| InterfaceApp           | ControladorGamificacao   | Informa conclusão de atividades e solicita registro de pontos. |
| ControladorGamificacao | AgenteDeDadosGamificacao | Atualiza pontuação do usuário.                                 |
| ControladorGamificacao | Ranking                  | Recalcula posições no ranking de usuários.                     |
| ControladorGamificacao | InterfaceApp             | Mostra nova pontuação ao usuário.                              |
| UsuarioA / Mensagem    | BancoDeDados             | Persiste mensagens enviadas.                                   |
| BancoDeDados           | SistemaDeNotificacoes    | Notifica destinatário sobre nova mensagem.                     |
| SistemaDeNotificacoes  | UsuarioB                 | Envia push notification sobre nova mensagem recebida.          |


---

## Bibliografia  

> ApresentaçãoSlide - Diagrama de Comunicação, Eduardo Figueiredo. Disponibilizado por, Milene Serrano, 2025 em: <https://homepages.dcc.ufmg.br/~figueiredo/disciplinas/aulas/uml-diagrama-comunicacao_v01.pdf>

## Histórico de Versões

| Versão | Data       | Descrição  | Autor(es) | Revisor(es) | Detalhes |
|--------|-----------|-----------------------------|-----------|-------------|----------|
| `1.0`  | 16/09/2025 | Criação inicial do documento e Criação e evolução do documento com inclusão progressiva dos cenários de Curtida, Bloqueio de Usuário, Gamificação e Notificação de Mensagem, incluindo fluxos, diagramas e consolidação da especificação de pacotes e componentes com suas relações principais. |[Esther Sena](https://github.com/esmsena) | [Mariiana Siqueira Neris](https://github.com/Maryyscreuza) | Estrutura inicial |
