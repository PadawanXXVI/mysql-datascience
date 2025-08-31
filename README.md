# Projeto de Banco de Dados Relacional + Ciência de Dados (Olist)

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-8.0+-4479A1?logo=mysql&logoColor=white)
![VSCode](https://img.shields.io/badge/VSCode-ready-007ACC?logo=visualstudiocode&logoColor=white)
![Status](https://img.shields.io/badge/status-em%20desenvolvimento-yellow)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)

Este projeto utiliza o **Olist Dataset** (Kaggle), que contém informações de pedidos, clientes, produtos, vendedores, pagamentos e avaliações do e-commerce brasileiro.  
O objetivo é **modelar, popular e analisar** os dados em **MySQL**, estruturando um **MER** (Modelo Entidade-Relacionamento) e um **MMD** (Modelo Multidimensional em estrela), além de gerar análises e visualizações em **SQL e BI**.

---

## 📊 Dataset
O dataset é composto por **9 arquivos CSV**, localizados em `data/raw/`:

- `olist_customers_dataset.csv` → informações dos clientes  
- `olist_geolocation_dataset.csv` → geolocalização de CEPs  
- `olist_order_items_dataset.csv` → itens de pedidos  
- `olist_order_payments_dataset.csv` → pagamentos dos pedidos  
- `olist_order_reviews_dataset.csv` → avaliações dos pedidos  
- `olist_orders_dataset.csv` → cabeçalho de pedidos  
- `olist_products_dataset.csv` → catálogo de produtos  
- `olist_sellers_dataset.csv` → vendedores  
- `product_category_name_translation.csv` → tradução de categorias  

Fonte oficial: [Brazilian E-Commerce Public Dataset by Olist](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)

---

## 🗂️ Estrutura Prevista do Projeto
- **Modelagem Conceitual e Lógica**
  - Criação do **MER (3FN)** no MySQL Workbench
  - Normalização das tabelas (clientes, pedidos, produtos, vendedores, etc.)
- **ETL**
  - Pipeline em **Python (Pandas + SQLAlchemy)** para popular o banco MySQL a partir dos CSVs
- **Modelo Multidimensional (MMD)**
  - Construção de um esquema estrela para análises
  - Dimensões: clientes, produtos, tempo, vendedores
  - Fato: vendas/pedidos
- **Consultas SQL Analíticas**
  - KPIs de negócio (ticket médio, vendas por estado, top produtos, etc.)
- **BI**
  - Conexão do MySQL ao **Power BI** ou visualizações em Flask/Plotly
  - Criação de dashboards para insights

---

## 🛠️ Tecnologias Utilizadas
- **MySQL** → Banco relacional
- **MySQL Workbench** → MER/MMD
- **Python (Pandas, SQLAlchemy, PyMySQL)** → ETL
- **VS Code** → Ambiente de desenvolvimento (SQL + Python)
- **Power BI** → Visualização dos dados (dashboards)
- **Flask (opcional)** → Painel web interativo

---

## 👨‍🏫 Coordenação
Este projeto está sendo desenvolvido em colaboração com:

- **Professor Ygor Rio Pardo Felix**  
  GitHub: [@YgorFelix](https://github.com/YgorFelix)  
  📧 E-mail: ygor.pardo@gmail.com  
  🔗 LinkedIn: [linkedin.com/in/ygor-felix-ba6400166](https://www.linkedin.com/in/ygor-felix-ba6400166)

---

## 👨‍💻 Autor / Orientado
- **Anderson de Matos Guimarães**  
  📧 E-mail: anderson.m.guimaraes@icloud.com  

---

## 📌 Observações
- O projeto **não está vinculado a nenhuma instituição**.  
- O objetivo é **portfólio pessoal** do autor e do Professor Ygor.  
- Todos os artefatos (scripts SQL, notebooks, ETL, painéis BI) estarão neste repositório.  

---

## 📄 Licença
Este projeto está sob a licença **MIT**.  
Sinta-se livre para usar, adaptar e compartilhar.
