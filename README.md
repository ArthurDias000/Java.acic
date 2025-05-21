# SCACIC (Sistema de Consulta e Análise de Cadastros Instituicional para Controle)
## Tecnologias Utilizadas
* Versão Java: 23
* Sistema Operacional: Linux - Windows
* Bibliotecas Adicionais: RS componentes, IText (PDF);
* Banco de dados (SGDB): PostGreSQL
* IDE: NetBeans

## Instalação
### Requerimentos
* Java 23
* Apache NetBeans IDE 23
* PostgreSQL
### Passos
1. Clone o repositório
```bash
git clone https://github.com/Leo-Santos17/JavaACICapp.git
```
2. Importe o projeto no NetBeans
3. Configure o banco de dados em [Conexão pelo postgres](#conexao-postgres)
4. Configure a conexão no código, se necessário, alterando as credenciais do banco de dados, caso não use um localhost ou possua senha e nome de usuários diferente demonstrados.
   * User: acicUSER (Opcional, só alterar no código)
   * Senha: 123 (Opcional, só alterar no código)
   * Database: acicDATA (Opcional, só alterar no código)
   * 

## Como importar a biblioteca (VIDEO)
[![Youtube](https://i1.ytimg.com/vi/u0rKzvETito/hqdefault.jpg)](https://www.youtube.com/watch?v=u0rKzvETito)

OBS: Sem ela o código não funcione

<h2 id="conexao-postgres">Conexão pelo PostgreSQL</h2>
* Tables

```sql
CREATE TABLE acic_cads (
    id SERIAL PRIMARY KEY,
    email VARCHAR(200) NOT NULL,
    senha VARCHAR(100) NOT NULL,
    usuar VARCHAR(50)
);
```

```sql
CREATE TABLE acic_table (
    id SERIAL PRIMARY KEY,
    service VARCHAR(140) NOT NULL,
    descri VARCHAR(300),
    data DATE,
    id_cad INTEGER,
    FOREIGN KEY (id_cad) REFERENCES acic_cads(id)
);
```

```sql
CREATE TABLE public.acic_events (
    id SERIAL PRIMARY KEY,
    nome VARCHAR(200),
    id_cad INTEGER,
    FOREIGN KEY (id_cad) REFERENCES acic_cads (id)
);
```
