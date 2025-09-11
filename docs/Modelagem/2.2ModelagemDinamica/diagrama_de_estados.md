# Diagrama de Estados

## Introdução
O Diagrama de Estados é uma ferramenta fundamental da modelagem de sistemas, utilizada para representar o ciclo de vida dos objetos, descrevendo os estados possíveis em que eles podem se encontrar e os eventos que provocam mudanças entre esses estados. No contexto deste projeto, voltado para o desenvolvimento de um sistema de um Correio Digital, o diagrama auxilia na visualização das transições que os usuários podem realizar durante sua interação com o aplicativo, como iniciar conversas, gerenciar amizades, interagir com o feed e personalizar seus perfis. A importância desse diagrama reside na sua capacidade de representar, de forma clara e estruturada, o comportamento dinâmico do sistema, permitindo que a equipe compreenda melhor os fluxos de interação e antecipe possíveis problemas ou inconsistências de navegação.

## Objetivo/ Metodologia
O objetivo do diagrama de estados é mapear os principais estados e transições do usuário dentro do sistema, visando oferecer uma visão geral do comportamento do aplicativo ao longo do tempo. Assim, buscamos identificar os estados mais relevantes que os usuários podem assumir, tanto quanto descrições das ações e eventos que provocam mudanças de estado.  
 
A elaboração do diagrama de estados seguiu as seguintes etapas:   
**Levantamento de requisitos**: As entrevistas realizadas com potenciais usuários foram analisadas para identificar eventos, ações e comportamentos recorrentes que impactam a navegação no sistema.  
**Definição dos estados principais**: Foram mapeados os estados mais relevantes, como ocioso, conversando, interagindo no feed, gerenciando perfil e gerenciando amizades.  
**Mapeamento das transições**: Com base nos cenários de uso, foram descritos os eventos e condições que provocam mudanças entre os estados.  
**Modelagem visual**: Utilizando a notação de diagramas UML, foi construído o diagrama de estados, no mesmo estilo visual padronizado adotado nos demais artefatos do projeto.  
**Validação em par**: O diagrama foi discutido em dupla e ajustado, garantindo que as representações correspondessem às expectativas dos membros desenvolvedores do seguinte artefato e às necessidades do sistema.  

## Desenvolvimento

A seguir, apresenta-se o diagrama de estados desenvolvido para o sistema de Correio Digital, ilustrando os principais estados e transições que os usuários podem experimentar durante sua interação com o aplicativo.

**Figura 1:** Diagrama de Estados  

![Diagrama de estados do projeto](../../assets/diagrama_de_estados.png)  

**Autores:** [João Pedro Costa](https://github.com/johnaopedro) e [Julia Gabriela](https://github.com/JuliaGabP).  

## Descrição dos Estados

Abaixo pode-se ver a tabela 1 que descreve os estados principais e seus subestados, juntamente com uma breve descrição de cada um. É valioso para entender o fluxo de navegação e as possíveis ações que os usuários podem realizar dentro do sistema.

**Tabela 1 — Estados e Subestados**

|     Estado Principal    |               Subestados              |                      Descrição                     |
|-------------------------|---------------------------------------|----------------------------------------------------|
| **NaoAutenticado**      |                   —                   | Usuário não está logado no sistema.                |
| **Autenticado.Ocioso**  |                   —                   | Usuário autenticado, mas sem executar ações ativas.|
| **Conversando**         |   Ativo → Compartilhando / Avaliando  | Usuário está em uma conversa ativa, podendo compartilhar mensagens ou avaliar o chat. |
| **InteragindoFeed**     | Visualizando → Publicando / Reagindo  | Usuário está navegando no feed, podendo criar posts ou reagir a outros. |
| **GerenciarPerfil**     |                 Editando              | Usuário está alterando dados do seu perfil.        |
| **GerenciarAmizades**   | ListaAmigos → Adicionando / Removendo | Usuário está visualizando a lista de amigos, podendo adicionar ou remover amizades. |
| **Gamificacao**         |                Pontuando              | Usuário está recebendo recompensas de pontos, experiência ou badges.  |

## Critérios de Entrada e Saída

Em relação aos critérios de entrada e saída, a tabela 2 detalha as condições que levam o sistema a transitar entre os estados descritos anteriormente. Esses critérios são essenciais para garantir que as mudanças de estado ocorram de maneira lógica e previsível, alinhadas com as ações dos usuários.

**Tabela 2 — Critérios para cada estado**

| Estado                            |        Critérios de Entrada        |           Critérios de Saída         |
|-----------------------------------|------------------------------------|--------------------------------------|
| **NaoAutenticado**                | Acesso inicial ao app ou logout()  | login() bem-sucedido                 |
| **Autenticado.Ocioso**            | login() bem-sucedido               | Qualquer ação de navegação           |
| **Conversando.Ativo**             | iniciarConversa()                  | encerrarConversa() e sairConversa()  |
| **Conversando.Compartilhando**    | compartilharMensagem()             | voltarConversa()                     |
| **Conversando.Avaliando**         | encerrarConversa()                 | avaliarConversa()                    |
| **InteragindoFeed.Visualizando**  | acessarFeed()                      | sairFeed()                           |
| **InteragindoFeed.Publicando**    | criarPost()                        | publicar()                           |
| **InteragindoFeed.Reagindo**      | curtirOuComentar()                 | reagir()                             |
| **GerenciarPerfil.Editando**      | editarPerfil()                     | salvarAlteracoes()                   |
| **GerenciarAmizades.ListaAmigos** | gerenciarAmizades()                | voltar()                             |
| **GerenciarAmizades.Adicionando** | adicionarAmigo()                   | confirmado()                         |
| **GerenciarAmizades.Removendo**   | desfazerAmizade()                  | confirmado()                         |
| **Gamificacao.Pontuando**         | avaliarConversa() / +pontos, publicar() / +xp, adicionarAmigo() / +badge | atualizarNivel() ou fim do processamento |

## Transições Principais

A tabela 3 apresenta as principais transições entre os estados, detalhando os eventos ou ações que provocam essas mudanças. Essas transições são fundamentais para compreender como os usuários interagem com o sistema e como suas ações influenciam o estado atual do aplicativo.

**Tabela 3 — Principais transições entre estados**

| Evento / Ação              | De                                | Para                 |
|-----------------------------|-----------------------------------|----------------------|
| login()                     | —                                 | Ocioso               |
| logout()                    | qualquer estado                   | NaoAutenticado       |
| iniciarConversa()           | Ocioso                            | Conversando.Ativo    |
| compartilharMensagem()      | Conversando.Ativo                 | Conversando.Compartilhando |
| voltarConversa()            | Conversando.Compartilhando        | Conversando.Ativo    |
| encerrarConversa()          | Conversando.Ativo                 | Conversando.Avaliando|
| avaliarConversa()           | Conversando.Avaliando             | Ocioso               |
| acessarFeed()               | Ocioso                            | InteragindoFeed.Visualizando |
| criarPost()                 | InteragindoFeed.Visualizando      | InteragindoFeed.Publicando |
| publicar()                  | InteragindoFeed.Publicando        | InteragindoFeed.Visualizando |
| curtirOuComentar()          | InteragindoFeed.Visualizando      | InteragindoFeed.Reagindo |
| reagir()                    | InteragindoFeed.Reagindo          | InteragindoFeed.Visualizando |
| sairFeed()                  | InteragindoFeed                   | Ocioso               |
| editarPerfil()              | Ocioso                            | GerenciarPerfil.Editando |
| salvarAlteracoes()          | GerenciarPerfil.Editando          | Ocioso               |
| gerenciarAmizades()         | Ocioso                            | GerenciarAmizades.ListaAmigos |
| adicionarAmigo()            | GerenciarAmizades.ListaAmigos     | GerenciarAmizades.Adicionando |
| confirmado()                | GerenciarAmizades.Adicionando     | GerenciarAmizades.ListaAmigos |
| desfazerAmizade()           | GerenciarAmizades.ListaAmigos     | GerenciarAmizades.Removendo |
| confirmado()                | GerenciarAmizades.Removendo       | GerenciarAmizades.ListaAmigos |
| voltar()                    | GerenciarPerfil / GerenciarAmizades | Ocioso             |
| sairConversa()              | Conversando                       | Ocioso               |
| avaliarConversa() / +pontos | Conversando.Avaliando             | Gamificacao.Pontuando |
| publicar() / +xp            | InteragindoFeed.Publicando        | Gamificacao.Pontuando |
| adicionarAmigo() / +badge   | GerenciarAmizades.Adicionando     | Gamificacao.Pontuando |
| atualizarNivel()            | Gamificacao.Pontuando             | Gamificacao          |

## Bibliografia  

Conjunto de obras consultadas.  

> O que é um diagrama de máquina de estados? Disponível em: <https://www.lucidchart.com/pages/pt/o-que-e-diagrama-de-maquina-de-estados-uml>.
> DANIEL, D.; ABDALA. [s.l: s.n.]. Disponível em: <https://www.facom.ufu.br/~abdala/DAS5312/Diagrama%20de%20Estados.pdf>.

## Histórico de Versões

| Versão |     Data    | Descrição   | Autor(es) | Revisor(es) | Detalhes da revisão | 
| ------ | ----------- | ----------- | --------- | ----------- | --------------------|
| `1.0`  | 11/09/2025  | Criação do documento | [Julia Gabriela](https://github.com/JuliaGabP) | - | - |
| `1.1`  | 11/09/2025  | Criação do diagrama | [João Pedro Costa](https://github.com/johnaopedro) e [Julia Gabriela](https://github.com/JuliaGabP) | - | - |
| `1.2`  | 11/09/2025  | Adicionando chamada as tabelas e figura e complementando com descrições e critérios | [João Pedro Costa](https://github.com/johnaopedro) e [Julia Gabriela](https://github.com/JuliaGabP) | - | - |
