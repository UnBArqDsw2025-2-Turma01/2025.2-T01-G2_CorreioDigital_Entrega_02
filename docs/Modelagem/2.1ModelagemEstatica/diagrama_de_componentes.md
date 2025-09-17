# Diagrama de Componentes

## Introdução  

O diagrama de componentes tem como propósito ilustrar a visão arquitetural do sistema, destacando como os módulos principais interagem entre si e com elementos externos. Esse tipo de diagrama é essencial para compreender a separação de responsabilidades, a modularidade e os pontos de integração do sistema. No contexto deste projeto, o diagrama de componentes foi elaborado para representar de forma clara as dependências entre funcionalidades como avaliação de conversa, gerenciamento de perfis, comunicação entre usuários e suporte às interações sociais.

## Objetivo/Metodologia

O objetivo deste diagrama de componentes é representar de forma clara a arquitetura modular do sistema, evidenciando como os diferentes subsistemas, Frontend/Interface, Dados e Operações se relacionam e trocam informações para oferecer as funcionalidades esperadas pelos usuários. Buscando demonstrar a separação de responsabilidades entre interface, lógica de negócios e persistência de dados, fazendo uso da evidenciação dos principais componentes que compõem cada subsistema.

A elaboração do diagrama de componentes seguiu uma metodologia estruturada baseada em boas práticas de modelagem UML e engenharia de software:  
**Frontend/Interface**: foco na interação com o usuário.  
**Operações**: tratamento da lógica de negócio e serviços de apoio.  
**Dados**: gerenciamento da persistência das informações.  
- **Modelagem de dependências**: definição das relações entre os componentes, especificando como a interface consome operações e como operações acessam os dados.  
- **Validação de modularidade**: verificação de que os subsistemas são coesos internamente e possuem baixo acoplamento entre si, garantindo maior flexibilidade e manutenção futura.  
- **Representação gráfica em UML**: utilização da notação de diagrama de componentes para evidenciar claramente os módulos, suas interfaces e as conexões entre eles.  

## Desenvolvimento

**Figura 1:** Diagrama de componentes  

![Diagrama de componentes do projeto](../../assets/diagrama_de_componentes.png)  

**Autores:**  [Túlio](https://github.com/TulioCeleri) e [Pedro](https://github.com/G0ndim).  

O diagrama de componentes apresentado organiza o sistema em três principais subsistemas: **Frontend/Interface**, **Dados** e **Operações**, cada um responsável por uma parte específica da aplicação. Essa estrutura evidencia a modularidade do sistema e como os diferentes blocos se interligam para oferecer funcionalidades completas ao usuário.

### Subsistema Frontend/Interface

Este subsistema reúne os módulos responsáveis pela interação direta com o usuário. Ele funciona como a “porta de entrada” do sistema, oferecendo a interface para execução de funcionalidades centrais, como:
- **PerfilUsuário**: gerenciamento e edição das informações de perfil.
- **AdicionaAmigo**: funcionalidade para enviar e gerenciar solicitações de amizade.
- **FazerPost**: publicação de conteúdos no feed.
- **RealizaConversa**: módulo que permite o envio de mensagens e o início de interações entre usuários.
- **AvaliaConversa**: avaliação de interações, incentivando a melhoria das experiências sociais.

Esses componentes enviam requisições para os subsistemas de **Dados** e **Operações**, sendo responsáveis por traduzir ações do usuário em chamadas para funcionalidades mais profundas.

### Subsistema Dados

Este subsistema é responsável pela persistência e manipulação das informações, atuando como repositório central do sistema. Ele é dividido em três módulos principais:

- **dadosUsuários**: armazena e mantém informações de perfis, credenciais e conexões.
- **dadosConversas**: registra conversas, mensagens e interações realizadas no chat.
- **dadosPosts**: concentra postagens, curtidas e comentários no feed.

O **subsistema de Dados** é acessado tanto pelo **Frontend/Interface** quanto pelo **subsistema de Operações**, servindo de base para todas as transações e interações.

### Subsistema Operações

Este subsistema concentra os serviços que dão suporte às funcionalidades de negócio. Ele opera como a “camada de lógica” do sistema, intermediando a comunicação entre interface e dados. Os módulos principais são:

- **Notificações**: envio de alertas e atualizações para os usuários.
- **Autenticação**: validação de login, logout e gerenciamento de sessões.
- **Chat**: suporte às conversas em tempo real, conectando-se com o subsistema de dados de conversas.
- **SugerirAmigos**: algoritmo que recomenda conexões com base em afinidades ou interações.

### Integração entre Subsistemas

- O **Frontend/Interface** solicita operações que, dependendo da natureza, podem ser direcionadas ao subsistema de **Operações** (para execução de lógica de negócio) ou diretamente ao subsistema de **Dados** (para persistência e recuperação).
- O subsistema de **Operações**, por sua vez, pode consumir dados armazenados ou gerar novas entradas no **subsistema de Dados**.
- Esse fluxo garante que as responsabilidades estejam bem distribuídas: a interface cuida da experiência do usuário, as operações processam a lógica e os dados centralizam o armazenamento.

Esse diagrama evidencia a modularidade e escalabilidade do sistema, permitindo que cada subsistema seja desenvolvido, testado e mantido de forma relativamente independente. Além disso, mostra claramente os pontos de integração e dependência, facilitando o entendimento da arquitetura geral.

## Bibliografia  

Conjunto de obras consultadas.  

> Diagrama de componentes UML: o que é, como fazer e exemplos. Disponível em: <http://lucidchart.com/pages/pt/diagrama-de-componentes-uml>. Acesso em: 17 set. 2025.

## Histórico de Versões

| Versão |     Data    | Descrição   | Autor(es) | Revisor(es) | Detalhes da revisão | 
| ------ | ----------- | ----------- | --------- | ----------- | --------------------|
| `1.0`  | 17/09/2025  | Criação do documento | [Julia Gabriela](https://github.com/JuliaGabP) | - | - |
| `1.0`  | 12/09/2025  | Criação do diagrama | [Túlio](https://github.com/TulioCeleri) e [Pedro](https://github.com/G0ndim) | - | - |
