# Guia de Contribuição

Obrigado por contribuir com este projeto **MySQL + Data Science (Olist)**.  
Aqui estão as regras práticas para colaborar com segurança e velocidade.

---

## 🔧 Como rodar localmente (setup rápido)

1. **Clone/Atualize**
   ```bash
   git switch main
   git pull origin main
   ```
2. **Python (venv)**
   ```bash
   python -m venv .venv
   source .venv/Scripts/activate
   pip install -r requirements.txt
   python -m ipykernel install --user --name=mysql-datascience --display-name "Python (mysql-datascience)"
   ```
3. **MySQL**
   - Requer MySQL 8.x em `localhost:3306`.
   - Crie `.env` na raiz:
     ```ini
     MYSQL_HOST=localhost
     MYSQL_PORT=3306
     MYSQL_USER=dsapp
     MYSQL_PASSWORD=TroqueEstaSenha!
     MYSQL_DB_OLTP=retail_oltp
     MYSQL_DB_DW=retail_dw
     ```
   - Use as **Tasks** do VS Code: `DDL OLTP`, `DDL DW`, `ETL OLTP`.

4. **Dados**
   - CSVs do Olist ficam em `data/raw/`.
   - Evite subir dados muito grandes. Se necessário, utilize *releases* ou links de origem.

---

## 🌿 Branches

- **main**: estável.  
- **feature/**_tarefa_ → novas funcionalidades  
- **fix/**_correcao_ → correções  
- **docs/**_documentacao_ → apenas documentação

Exemplo:
```bash
git switch -c feature/etl-load-oltp
```

---

## ✍️ Commits (Conventional Commits)

Formato:
```
tipo(escopo): descrição curta no imperativo

corpo opcional (o que e por quê)
```

Tipos comuns: `feat`, `fix`, `docs`, `chore`, `refactor`, `test`, `build`.

Exemplos:
- `feat(sql): add OLTP schema for orders, items and payments`
- `docs(readme): add badges and coordination section`
- `chore(vscode): add tasks to run MySQL DDL`

---

## 🔁 Pull Requests

1. Abra PR da sua branch para `main`.  
2. Descreva objetivo, evidências (prints/logs) e impactos.  
3. **Revisor padrão:** **Prof. Ygor Rio Pardo Felix (@YgorFelix)**.  
4. Exija pelo menos **1 aprovação** antes de *merge*.  
5. Proíba *merge* direto na `main` sem PR.

**Checklist de PR**
- [ ] Passos para reproduzir testados  
- [ ] Tabelas/índices com FKs/UNIQUE quando aplicável  
- [ ] ETL idempotente (pode rodar mais de uma vez)  
- [ ] Views não usam `SELECT *`

---

## 🗃️ Padrões de Banco/SQL

- **Nomes:** `snake_case`, singular para dimensões (`product`, `customer`); tabelas fato no plural quando fizer sentido.  
- **Chaves:** PK em todas as tabelas; FKs explícitas; `UNIQUE` para chaves naturais (`sku`, `email`).  
- **Índices:** crie para colunas usadas em *joins* e filtros frequentes.  
- **Tipos:** valores monetários em `DECIMAL(12,2)`; datas em `DATE/DATETIME`.  
- **Views:** prefixo `vw_` e **nunca** `SELECT *`.  
- **Scripts padrão:**  
  - `sql/01_schema_oltp.sql`  
  - `sql/02_constraints_indexes.sql`  
  - `sql/03_schema_dw.sql`

---

## 🐍 Padrões de Python

- Organização em `etl/` com scripts idempotentes.  
- Use `python-dotenv` para ler `.env`.  
- Conexão com MySQL via **SQLAlchemy + PyMySQL**.  
- Logging simples no console; evite `print` solto para etapas críticas.

---

## 🧪 Qualidade

Antes de abrir PR:
```sql
-- contagens básicas
SELECT COUNT(*) FROM orders;
SELECT COUNT(*) FROM order_items;

-- exemplo de checagem de órfãos
SELECT *
FROM order_items oi
LEFT JOIN orders o ON o.order_id = oi.order_id
WHERE o.order_id IS NULL;
```

---

## 🏷️ Issues, Labels e Milestones

- **Milestones** sugeridas: `M1-Setup`, `M2-OLTP`, `M3-ETL`, `M4-DW`, `M5-BI`.  
- **Labels**: `feat`, `bug`, `etl`, `sql`, `schema`, `docs`, `help wanted`, `good first issue`.  
- Cada issue deve ter escopo claro, *acceptance criteria* e, se possível, link para PR.

---

## 🤝 Código de Conduta

Seja respeitoso e colaborativo. Feedbacks técnicos são bem-vindos.  
Violação de conduta pode levar à restrição de participação.

---

## 👥 Contatos

- **Autor / Orientado:** Anderson de Matos Guimarães — anderson.m.guimaraes@icloud.com  
- **Coordenação:** Prof. **Ygor Rio Pardo Felix** — GitHub [@YgorFelix](https://github.com/YgorFelix) — ygor.pardo@gmail.com

---

## 📜 Licença

MIT. Consulte `LICENSE`.
