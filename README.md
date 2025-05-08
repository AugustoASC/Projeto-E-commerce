# 🛒 Projeto E-commerce

### Descrição Geral

Este repositório apresenta a modelagem lógica e a implementação de um banco de dados para um sistema de E-commerce, aplicando conceitos do modelo EER (Extended Entity-Relationship). O objetivo é simular um ambiente real de comércio eletrônico, com entidades como clientes, pedidos, produtos, fornecedores, entregas e pagamentos, considerando suas relações e restrições.

### Principais Requisitos e Regras de Negócio:

* Um cliente pode ser Pessoa Física (PF) ou Pessoa Jurídica (PJ), mas não ambas.
* Cada pedido pode ter uma ou mais formas de pagamento.
* As entregas possuem código de rastreio e status.
* Vendedores podem também ser fornecedores, sendo essa relação representada por uma tabela associativa.

### 🔧 Estrutura do Banco de Dados

As tabelas criadas neste projeto incluem:

* **Clientes**: Armazena dados de clientes PF e PJ.
* **Pedidos**: Contém as informações dos pedidos realizados.
* **Produtos**: Catálogo de produtos disponíveis.
* **Fornecedores**: Empresas fornecedoras dos produtos.
* **Pagamentos**: Registro de formas de pagamento por pedido.
* **Entregas**: Status e rastreamento dos pedidos.
* **Vendedores**: Pessoas que atuam como vendedores.
* **Fornecedor\_Vendedor**: Relação entre vendedores e fornecedores.

### 📜 Explicação do Código SQL

#### Criação de Tabelas

* `CREATE TABLE Clientes`: define a estrutura básica dos clientes, com controle de CPF/CNPJ e tipo de pessoa.
* `CREATE TABLE Pedidos`: relaciona cada pedido ao cliente, com data, status e valor total.
* `CREATE TABLE Produtos`: define os produtos, com preço, estoque e fornecedor.
* `CREATE TABLE Fornecedores`: armazena os dados das empresas fornecedoras.
* `CREATE TABLE Pagamentos`: registra uma ou mais formas de pagamento de cada pedido.
* `CREATE TABLE Entregas`: guarda o status e o código de rastreio da entrega.
* `CREATE TABLE Vendedores`: dados de vendedores, podendo se relacionar com fornecedores.
* `CREATE TABLE Fornecedor_Vendedor`: tabela associativa entre vendedores e fornecedores.

#### Inserção de Dados

* Comandos `INSERT INTO` populam as tabelas com dados fictícios para simulação e testes.

#### Queries Avançadas

1. **Pedidos por cliente**:

```sql
SELECT ClienteID, COUNT(PedidoID) AS QuantidadePedidos FROM Pedidos GROUP BY ClienteID;
```

2. **Vendedor também é fornecedor**:

```sql
SELECT Vendedores.Nome, Fornecedores.Nome FROM Vendedores JOIN Fornecedor_Vendedor ON ...
```

3. **Produtos, fornecedores e estoque**:

```sql
SELECT Produtos.Nome, Fornecedores.Nome, Produtos.Estoque FROM Produtos JOIN Fornecedores ON ...
```

4. **Relação fornecedor-produto**:

```sql
SELECT Fornecedores.Nome, Produtos.Nome FROM Produtos JOIN Fornecedores ON ...
```

5. **Produtos com estoque < 10**:

```sql
SELECT Nome, Preço, Estoque FROM Produtos WHERE Estoque < 10 ORDER BY Preço ASC;
```

6. **Pedidos sem pagamento**:

```sql
SELECT Clientes.Nome, Pedidos.PedidoID FROM Pedidos JOIN Clientes ON ... LEFT JOIN Pagamentos ON ... WHERE Pagamentos.PagamentoID IS NULL;
```

7. **Total por forma de pagamento**:

```sql
SELECT FormaPagamento, SUM(ValorPago) FROM Pagamentos GROUP BY FormaPagamento;
```

### 🎯 Objetivo Didático

O projeto foi desenvolvido como parte de um desafio prático para consolidar conhecimentos em modelagem de dados, criação de schemas SQL e escrita de consultas complexas utilizando `JOIN`, `WHERE`, `GROUP BY`, `HAVING`, `ORDER BY`, e expressões derivadas.

### 🧠 Conhecimentos Aplicados

* Modelagem de dados EER
* SQL DDL (Data Definition Language)
* SQL DML (Data Manipulation Language)
* Consultas SQL intermediárias e avançadas

---

> Desenvolvido como parte do desafio de projeto da [DIO - Digital Innovation One](https://www.dio.me/)

---

🐍 Powered by SQL + Lógica de Modelagem
