## Desafio de Projeto: Modelagem de Dados em Star Schema

Criar um modelo de dados baseado em star schema a partir da tabela Financial Sample, utilizando DAX para definir a tabela de calendário e outras funcionalidades necessárias

### Índice

- [Desafio de Projeto: Modelagem de Dados em Star Schema](#desafio-de-projeto-modelagem-de-dados-em-star-schema)
  - [Índice](#índice)
  - [Tabelas Criadas](#tabelas-criadas)
    - [D\_Produtos](#d_produtos)
    - [D\_Produtos\_Detalhes](#d_produtos_detalhes)
    - [D\_Descontos](#d_descontos)
    - [D\_Detalhes](#d_detalhes)
    - [D\_Calendário](#d_calendário)
    - [F\_Vendas](#f_vendas)
  - [Etapas do Projeto](#etapas-do-projeto)
  - [Funcionalidades e Funções DAX Utilizadas](#funcionalidades-e-funções-dax-utilizadas)
- [Conclusão](#conclusão)
- [Autor](#autor)

---

### Tabelas Criadas

#### D_Produtos
- **Colunas**:
  - ID_produto
  - Produto
  - Média de Unidades Vendidas
  - Média do valor de vendas
  - Mediana do valor de vendas
  - Valor máximo de Venda
  - Valor mínimo de Venda

#### D_Produtos_Detalhes
- **Colunas**:
  - ID_produtos
  - Discount Band
  - Sale Price
  - Units Sold
  - Manufactoring Price

#### D_Descontos
- **Colunas**:
  - ID_produto
  - Discount
  - Discount Band

#### D_Detalhes
- **Colunas**:
  - A definir com informações adicionais que não foram contempladas nas demais tabelas.

#### D_Calendário
- **Criação**:
  - Utilizando a função DAX `CALENDAR()` para gerar uma tabela de datas abrangendo o período das vendas.

#### F_Vendas
- **Colunas**:
  - SK_ID
  - ID_Produto
  - Produto
  - Units Sold
  - Sales Price
  - Discount Band
  - Segment
  - Country
  - Sales (Vendedores)
  - Profit
  - Date (campos)

---

### Etapas do Projeto

1. **Análise da Tabela Original**:
   - Examinar a tabela Financials_origem para identificar as colunas relevantes para o modelo de dados.

2. **Criação das Tabelas Dimensão e Tabela Fato**:
   - Selecionar e agregar dados da tabela original para formar as tabelas de dimensão (D_Calendário, D_Categoria, D_Descontos, D_Detalhes, D_Produtos_Detalhes, D_Produtos).

   - Montar a tabela F_Vendas, que contém as métricas e os indicadores chave.
  
    <div style="text-align: center;">
    <img src="/PowerBI/Desafio5/figure/figure1_tabelas_criadas.png" alt="Tabelas criadas" width="300" height="200">
    </div>

3. **Definição da Tabela Calendário**:
   - Utilizar a função DAX `CALENDAR()` para criar uma tabela de calendário que permitirá análises temporais. O código criado segue abaixo.
  
    ```dax
    D_Calendario = 
    VAR DataInicial = DATE(2020, 1, 1)  // Defina a data inicial
    VAR DataFinal = DATE(2024, 12, 31)  // Defina a data final
    RETURN
    ADDCOLUMNS (
        CALENDAR (DataInicial, DataFinal),
        "Ano", YEAR([Date]),
        "Mês", FORMAT([Date], "MMMM"),
        "MêsNúmero", MONTH([Date]),
        "Trimestre", "Q" & QUARTER([Date]),
        "Dia da Semana", FORMAT([Date], "dddd"),
        "Dia", DAY([Date]),
        "AnoMês", FORMAT([Date], "YYYY-MM")
    )
    ```

4. **Visualização do Esquema em Estrela**:
   - Representar graficamente a estrutura do modelo em star schema, mostrando as relações entre tabelas de fato e de dimensão. Segue abaixo.
    
    <div style="text-align: center;">
    <img src="/PowerBI/Desafio5/figure/figure2_schema.png" alt="modelo em star schema" width="900" height="600">
    </div>

---

### Funcionalidades e Funções DAX Utilizadas

- **CALENDAR()**: Para gerar uma tabela de calendário abrangendo as datas de vendas.
- **SUM()**: Para calcular total de vendas.
- **AVERAGE()**: Para calcular a média de unidades vendidas e preços.
- **MEDIAN()**: Para calcular a mediana dos valores de vendas.
- **MAX() e MIN()**: Para determinar os valores máximo e mínimo de vendas.

---

## Conclusão

O projeto de modelagem de dados em star schema realizado com base na tabela Financial Sample demonstra uma abordagem estruturada e eficaz para organizar e analisar dados financeiros. A criação das tabelas de dimensão e da tabela fato proporciona uma visualização clara das relações entre diferentes elementos, facilitando análises detalhadas sobre vendas, produtos e descontos. A utilização de funções DAX, como `CALENDAR()`, `SUM()`, `AVERAGE()`, entre outras, não só enriquece o modelo, mas também potencializa a capacidade de extração de insights relevantes. Esse modelo, ao permitir uma análise temporal e categórica, oferece uma base sólida para tomadas de decisão informadas e estratégias de negócio mais eficazes.

## Autor

Jacivaldo Carvalho [LinkedIn](https://www.linkedin.com/in/jacivaldocarvalho/)