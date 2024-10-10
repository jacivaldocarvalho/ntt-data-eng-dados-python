# Desafio DIO - Modelagem Dimensional Star Schema

## Objetivo

Este projeto visa criar um diagrama dimensional no formato *Star Schema* com foco na análise de dados dos professores. A tabela fato foi elaborada pela ferramenta [SQLdbm](https://app.sqldbm.com/)
 e reflete informações relevantes sobre os professores, cursos que ministram, alunos e os departamentos a que pertencem.

 ## Índice

- [Desafio DIO - Modelagem Dimensional Star Schema](#desafio-dio---modelagem-dimensional-star-schema)
  - [Objetivo](#objetivo)
  - [Índice](#índice)
  - [Diagrama Relacional](#diagrama-relacional)
  - [Diagrama Dimensional](#diagrama-dimensional)
    - [1. Tabela Fato: Fato\_Professor\_Cursos](#1-tabela-fato-fato_professor_cursos)
    - [2. Tabelas Dimensão](#2-tabelas-dimensão)
      - [2.1 Dimensão: D\_Professor](#21-dimensão-d_professor)
      - [2.2 Dimensão: D\_Curso](#22-dimensão-d_curso)
      - [2.3 Dimensão: D\_Departamento](#23-dimensão-d_departamento)
      - [2.4 Dimensão: D\_Data](#24-dimensão-d_data)
      - [2.4 Dimensão: D\_Aluno](#24-dimensão-d_aluno)
  - [Considerações Finais](#considerações-finais)
  - [Conclusão](#conclusão)

## Diagrama Relacional

<div style="text-align: center;">
    <img src="/PowerBI/Desafio4/figure/der_universidade.png" alt="Diagrama Relacional" width="500" height="400">
</div>

## Diagrama Dimensional

O diagrama desenvolvido segue abaixo:

<div style="text-align: center;">
    <img src="/PowerBI/Desafio4/figure/diagrama_dimensional.png" alt="Diagrama Relacional" width="600" height="500">
</div>

### 1. Tabela Fato: Fato_Professor_Cursos

A tabela fato chamada `Fato_Professor_Cursos` conterá os seguintes campos:

- **ID_Professor**: Identificador único do professor (chave estrangeira para a dimensão Professor).
- **ID_Curso**: Identificador único do curso ministrado (chave estrangeira para a dimensão Curso).
- **ID_Departamento**: Identificador do departamento ao qual o professor pertence (chave estrangeira para a dimensão Departamento).
- **Data_Oferta**: Data em que o curso foi oferecido (chave estrangeira para a dimensão Data).
- **ID_Aluno**: Identificador sobre os alunos do professor (chave estrangeira para a dimensão Data).

### 2. Tabelas Dimensão

#### 2.1 Dimensão: D_Professor

Esta tabela contém informações sobre os professores.

- **ID_Professor**: Identificador único do professor.
- **Nome**: Nome completo do professor.
- **Sobrenome**: Sobrenome do professor.

#### 2.2 Dimensão: D_Curso

Esta tabela contém detalhes sobre os cursos.

- **ID_Curso**: Identificador único do curso.
- **Nome_Curso**: Nome do curso.
- **Descrição**: Descrição do curso.
- **Créditos**: Número de créditos do curso.

#### 2.3 Dimensão: D_Departamento

Esta tabela contém informações sobre os departamentos.

- **ID_Departamento**: Identificador único do departamento.
- **Nome_Departamento**: Nome do departamento.

#### 2.4 Dimensão: D_Data

Esta tabela fornece informações sobre datas relevantes.

- **ID_Data**: Identificador único da data.
- **Data**: Data no formato YYYY-MM-DD.
- **Dia**: Dia da data.
- **Mês**: Mês da data.
- **Ano**: Ano da data.
- **Trimestre**: Trimestre do ano.
- **Dia_da_Semana**: Nome do dia da semana.
- 
#### 2.4 Dimensão: D_Aluno

Esta tabela fornece informações sobre os alunos do professor.

- **ID_Aluno**: Identificador único do aluno.
- **Nome**: Nome do aluno.
- **Sobrenome**: Sobrenome do aluno.


## Considerações Finais

O modelo em estrela proposto oferece uma estrutura clara para a análise de dados relacionados aos professores, permitindo consultas eficientes e insights valiosos. A tabela fato é o núcleo do esquema, enquanto as tabelas de dimensão enriquecem os dados contextuais necessários para uma análise abrangente.


## Conclusão

Este README fornece uma visão geral da modelagem dimensional proposta, com foco na análise dos dados dos professores.