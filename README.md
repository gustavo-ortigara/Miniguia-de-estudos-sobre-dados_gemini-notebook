# 📚 Mini Guia de Estudos: Fundamentos de Bancos de Dados e Análise de Dados com SQL

> Mini guia de estudos desenvolvido como parte do desafio de consolidação de aprendizado, utilizando fontes abertas e curadoria com suporte do NotebookLM e Inteligência Artificial.

---

## 🎯 Contexto e Objetivos

### Contexto
A área de dados cresceu exponencialmente e exige compreensão sólida sobre como a informação é armazenada, modelada e consultada. Escolhi o tema de **Bancos de Dados Relacionais e Linguagem SQL aplicados à Análise de Dados** por ser a base fundamental indispensável tanto para Analistas de Dados quanto para Engenheiros e Cientistas de Dados. 

Este repositório consolida conceitos essenciais de modelagem relacional, linguagem SQL para manipulação e análise, além de boas práticas no tratamento de dados.

### Objetivos de Aprendizado
- [x] Entender a arquitetura e o funcionamento de Bancos de Dados Relacionais (SGBDs).
- [x] Domínio de comandos fundamentais em SQL (`SELECT`, `JOIN`, `GROUP BY`, `WINDOW FUNCTIONS`).
- [x] Compreender os princípios de modelagem de dados (Normalização x Desnormalização).
- [x] Estruturar um glossário de termos e criar prompts reutilizáveis para estudos futuros com IA.

---

## 📚 Curadoria de Fontes

Para alimentar o NotebookLM e extrair as sínteses deste guia, foram selecionadas as seguintes fontes abertas e oficiais:

1. **[PostgreSQL Official Documentation - Tutorial](https://www.postgresql.org/docs/current/tutorial.html)**
   - *Descrição:* Tutorial oficial cobrindo conceitos de tabelas, consultas, joins e agregação em bancos relacionais.
2. **[Database Design Concepts - W3Schools](https://www.w3schools.com/sql/)**
   - *Descrição:* Material de referência prática sobre sintaxe SQL, tipos de dados e chave primária/estrangeira.
3. **[Google Cloud: Documentação de Análise de Dados](https://docs.cloud.google.com/docs/data?hl=pt-br)**
   - *Descrição:* Visão geral oficial do ecossistema de análise de dados, arquitura de dados e ferramentas de Business Intelligence (BI).
4. **[An Introduction to Database Systems - Open Textbook](https://open.umn.edu/opentextbooks)**
   - *Descrição:* Capítulo focado em normalização de dados (1FN, 2FN, 3FN) e álgebra relacional.


---

## 🛠️ Engenharia de Prompts & "Cicatrizes" (Troubleshooting)

Abaixo estão registrados os testes e refinamentos de prompts realizados no NotebookLM durante a análise das fontes.

### Prompts Estratégicos Testados & Variações

| Objetivo do Prompt | Variação A (Inicial) | Variação B (Refinada) | Resultado Obtido |
| :--- | :--- | :--- | :--- |
| **Explicar JOINs** | *"Explique os JOINs do SQL"* | *"Atuando como Engenheiro de Dados Senior, explique INNER, LEFT, RIGHT e FULL JOIN usando uma metáfora visual simples e exemplos de tabelas 'Clientes' e 'Pedidos'"* | A Variação B gerou uma resposta muito mais didática, com tabelas em Markdown e caso de uso claro. |
| **Resumir Normalização** | *"O que é normalização de banco de dados?"* | *"Com base nos documentos carregados, resuma 1FN, 2FN e 3FN em tópicos, destacando o problema que cada forma normal resolve"* | A resposta refinada evitou teorias excessivas e focou na solução prática de anomalias de dados. |

### 🩹 "Cicatrizes" e Desafios Encontrados (Troubleshooting)

- **Desafio 1: Confusão entre Window Functions e GROUP BY.**
  - *Sintoma:* Inicialmente a IA tendeu a tratar `OVER(PARTITION BY ...)` como sinônimo de `GROUP BY`, omitindo o detalhe de que Window Functions não colapsam linhas.
  - *Solução:* Ajuste no prompt solicitando explicitamente: *"Compare `GROUP BY` e `PARTITION BY` em termos de granularidade das linhas de saída (linhas agrupadas vs. linhas preservadas)"*.
- **Desafio 2: Mistura de sintaxes SQL específicas de fornecedores.**
  - *Sintoma:* A IA gerou exemplos misturando sintaxe específica de T-SQL (SQL Server) com PostgreSQL.
  - *Solução:* Adicionado constraint ao prompt: *"Utilize estritamente o padrão ANSI SQL compatível com PostgreSQL e BigQuery"*.

---

## 📝 Mini Guia de Estudo (Entrega Final)

### 1. Resumos Estruturados do Assunto

#### Módulo I: Arquitetura e Modelagem Relacional
- **SGBD (Sistema Gerenciador de Banco de Dados):** Software responsável por gerenciar o acesso, armazenamento e integridade dos dados (ex: PostgreSQL, MySQL).
- **Chave Primária (PK) vs. Chave Estrangeira (FK):**
  - **PK:** Identificador único de um registro em uma tabela (ex: `id_cliente`).
  - **FK:** Campo que estabelece relação entre a tabela atual e a PK de outra tabela (ex: `id_cliente` na tabela de `pedidos`).
- **Normalização de Dados:** Processo de organização das tabelas para reduzir redundância e eliminar anomalias de inserção, atualização e exclusão (garantindo as Formas Normais 1FN, 2FN e 3FN).

#### Módulo II: Linguagem SQL para Análise de Dados
- **Sublinguagens SQL:**
  - **DDL (Data Definition Language):** Define estruturas (`CREATE`, `ALTER`, `DROP`).
  - **DML (Data Manipulation Language):** Manipula dados (`INSERT`, `UPDATE`, `DELETE`).
  - **DQL (Data Query Language):** Consulta dados (`SELECT`).
- **Junções de Tabelas (JOINs):**
  - `INNER JOIN`: Retorna apenas os registros com correspondência em ambas as tabelas.
  - `LEFT JOIN`: Retorna todos os registros da tabela à esquerda e os correspondentes da direita.
- **Funções de Agregação e Agrupamento:**
  - `SUM()`, `AVG()`, `COUNT()`, `MAX()`, `MIN()` combinados com `GROUP BY` para gerar métricas de negócio.
  - O filtro em dados agregados deve ser feito via `HAVING`, e não `WHERE`.

---

### 📖 2. Glossário de Conceitos

- **ANSI SQL:** Padrão universal da linguagem SQL mantido pelo Instituto Americano de Padrões Nacionais.
- **Data Warehouse (DW):** Repositório central de dados otimizado para leitura e análise de grandes volumes (ex: BigQuery, Snowflake), diferente dos bancos transacionais (OLTP).
- **ETL / ELT (Extract, Transform, Load):** Processo de extração de dados de fontes, transformação/limpeza e carga no banco de destino para análise.
- **OLTP vs. OLAP:**
  - *OLTP (Online Transaction Processing):* Foco em transações rápidas do dia a dia (ex: sistemas bancários, e-commerce).
  - *OLAP (Online Analytical Processing):* Foco em consultas complexas e análise de inteligência de negócios.
- **Window Functions (Funções de Janela):** Funções SQL que realizam cálculos em um conjunto de linhas relacionadas ao registro atual sem agrupar as linhas em um único resultado (`ROW_NUMBER()`, `RANK()`, `SUM() OVER()`).

---

### 🔄 3. Prompts Reutilizáveis para Revisões Futuras

Guarde estes prompts para utilizar em novos estudos de SQL e Análise de Dados no NotebookLM ou ChatGPT/Gemini:

1. **Prompt para Explicação de Consultas Complexas:**
   > *"Atue como um especialista em SQL. Analise a consulta abaixo e explique passo a passo o fluxo de execução lógico (FROM, WHERE, GROUP BY, HAVING, SELECT, ORDER BY): [Insira a Query Aqui]"*

2. **Prompt para Otimização de Queries (Performance):**
   > *"Assuma o papel de DBA / Data Engineer. Identifique possíveis gargalos de performance no código SQL a seguir e sugira melhorias utilizando índices ou reestruturação da consulta: [Insira a Query Aqui]"*

3. **Prompt de Treino e Desafios Práticos:**
   > *"Com base nos esquemas de tabelas fornecidos nas fontes, crie 3 exercícios práticos de análise de dados com SQL (um nível fácil, um médio e um difícil). Não mostre a resposta até que eu envie minha tentativa."*

---

## 🤝 Como Usar Este Repositório
Você pode clonar este repositório para utilizar o resumo e os prompts durante seus estudos práticos de bancos de dados:

```bash
git clone [https://github.com/gustavo-ortigara/Miniguia-de-estudos-sobre-dados_gemini-notebook.git](https://github.com/gustavo-ortigara/Miniguia-de-estudos-sobre-dados_gemini-notebook.git)
