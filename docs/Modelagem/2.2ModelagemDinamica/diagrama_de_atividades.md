# Diagrama de Atividades

## Introdução

O **Diagrama de Atividades** é um dos diagramas da **UML (Unified Modeling Language)** utilizado para representar o **fluxo de atividades** dentro de um processo ou sistema.  
Ele mostra **ações, decisões, paralelismos e fluxos de controle**, permitindo visualizar **como o trabalho é executado** desde o início até a conclusão.  

Esse tipo de diagrama é especialmente útil para:  
- 📌 **Modelar processos de negócio** e rotinas organizacionais;  
- 📌 **Descrever o comportamento de casos de uso**;  
- 📌 **Representar algoritmos ou fluxos de sistema**;  
- 📌 **Identificar pontos de decisão e atividades paralelas**.  

Em resumo, o diagrama de atividades ajuda a compreender **o passo a passo das ações** e facilita a comunicação entre desenvolvedores, analistas e usuários, já que apresenta de forma **visual e intuitiva** a lógica do processo.

## Metodologia

Dois membros foram responsáveis pela elaboração dos diagramas de atividade, desenvolvidos no [draw.io](https://www.drawio.com/). 

Para elaborar um Diagrama de Atividades, utiliza-se um conjunto de símbolos específicos que representam diferentes aspectos do fluxo. Esses símbolos incluem elementos destinados a iniciar, encerrar, fundir ou receber etapas dentro do processo.
A tabela a seguir apresenta os principais elementos da UML aplicados nos diagramas de atividade, juntamente com seus símbolos, nomes e descrições.

| Símbolo                            | Nome                   | Descrição                                                                                                                                                                    |
|------------------------------------|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| ![Início](../../assets/diagramas_de_atividades/Circle.png)  | Nodo Inicial           | Representa o ponto de início do fluxo de atividades. É simbolizado por um círculo branco                                                                       |
| ![Fim](../../assets/diagramas_de_atividades/nofinal.png)        | Nodo Final             | Indica o término do fluxo de atividades. É representado por um círculo preenchido em preto dentro de outro círculo.                                                          |
| ![Atividade](../../assets/diagramas_de_atividades/activity.png) | Atividade              | Representa uma tarefa ou ação específica no fluxo. É simbolizada por um retângulo que contêm a descrição da tarefa.                                      |
| ![Conector](../../assets/diagramas_de_atividades/seta.png)   | Conector      | Mostra o fluxo de direção, ou fluxo de controle, da atividade. |
| ![Decisão](../../assets/diagramas_de_atividades/losango.png)     | Nodo de Decisão        | Indica um ponto de decisão no fluxo onde diferentes caminhos podem ser tomados. É representado por um losango.                                                               |
| ![Barra](https://d2slcw3kip6qmk.cloudfront.net/marketing/pages/chart/uml/activity-diagram/join-66x57.PNG)          | Barra de Sincronização | Indica um ponto do processo em que o fluxo pode ser dividido em atividades paralelas (fork) ou reunido em um único caminho (join). É simbolizada por uma barra preta horizontal.                 |
| ![Condicao](../../assets/diagramas_de_atividades/conditiontext.png)   | Texto de Condição      | Representa a condição que determina qual caminho o fluxo deve seguir quando encontra um ponto de decisão. É escrito na linha que sai do losango de decisão. |

## Diagramas de Atividades das Páginas do Site

### SignUp e Login

<center>

**Figura 1:** Diagrama de Atividade de SignUp e LogIn

![SignUp e Login](../../assets/diagramas_de_atividades/login.png)

**Autores:** [Pedro Ferreira Gondim](https://github.com/G0ndim) e [Túlio Augusto Celeri](https://github.com/TulioCeleri).
</center>

### Chat

<center>

**Figura 2:** Diagrama de Atividade do Chat

![Chat](../../assets/diagramas_de_atividades/chat.png)

**Autores:** [Pedro Ferreira Gondim](https://github.com/G0ndim) e [Túlio Augusto Celeri](https://github.com/TulioCeleri).
</center>

### Perfil de Usuário

<center>

**Figura 3:** Diagrama de Atividade do Perfil de Usuário

![Perfil de Usuário](../../assets/diagramas_de_atividades/user-prof.png)

**Autores:** [Pedro Ferreira Gondim](https://github.com/G0ndim) e [Túlio Augusto Celeri](https://github.com/TulioCeleri).
</center>

### Perfil do Próprio Usuário

<center>

**Figura 4:** Diagrama de Atividade do Perfil do Próprio Usuário

![Perfil do Próprio Usuário](../../assets/diagramas_de_atividades/user-own-prof.png)

**Autores:** [Pedro Ferreira Gondim](https://github.com/G0ndim) e [Túlio Augusto Celeri](https://github.com/TulioCeleri).
</center>

### Explorar

<center>

**Figura 5:** Diagrama de Atividade da aba Explorar

![Explorar](../../assets/diagramas_de_atividades/explore.png)

**Autores:** [Pedro Ferreira Gondim](https://github.com/G0ndim) e [Túlio Augusto Celeri](https://github.com/TulioCeleri).
</center>

## Referências Bibliográficas

>1. <a id="ref1"></a> BÓSON TREINAMENTOS. **O que é um Diagrama de Atividade UML - Introdução**. YouTube, 2022. Disponível em: <https://www.youtube.com/watch?v=_1vHj_j3zDY>. Acesso em: 15 de setembro de 2025. 

>2. <a id="ref2"></a> Milene Serrano. **06c - VideoAula - DSW-Modelagem - Atividades**. Sharepoint, 2020. Disponível em: <https://unbbr-my.sharepoint.com/:v:/g/personal/mileneserrano_unb_br/Ed9k-OvMH7hMlNMj6CGVenMBSyeVrDBOdg84Czx_aHI9gw?e=78GaZi&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0%3D>. Acesso em: 15 de setembro de 2025. 

## Histórico de Versões


| Versão |     Data    | Descrição   | Autor(es) | Revisor(es) | Detalhes da revisão | 
| ------ | ----------- | ----------- | --------- | ----------- | --------------------|
| `1.0` | 15/09/2025 | Criação esqueleto do documento | [Pedro Ferreira Gondim](https://github.com/G0ndim) | [Túlio Augusto Celeri](https://github.com/TulioCeleri) | O esqueleto do documento foi criado corretamente |
| `1.1` | 15/09/2025 | Adição dos diagramas de atividades | [Pedro Ferreira Gondim](https://github.com/G0ndim) e [Túlio Augusto Celeri](https://github.com/TulioCeleri) | - | - |
| `1.2` | 15/09/2025 | Adição da introdução e metodologia | [Pedro Ferreira Gondim](https://github.com/G0ndim) e [Túlio Augusto Celeri](https://github.com/TulioCeleri) | - | - |