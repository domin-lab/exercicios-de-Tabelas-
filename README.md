🗂️ Estrutura do Banco de Dados — Projeto SQL

Este repositório contém a estrutura completa das tabelas do banco de dados utilizadas no sistema.
Tudo foi organizado com separações claras, explicações e comentários para facilitar manutenção e entendimento.

📌 1. Tabela favoritos
CREATE TABLE IF NOT EXISTS favoritos(
    id INTEGER PRIMARY KEY,
    email VARCHAR(50) UNIQUE,
    valor DECIMAL(4,2) CHECK (valor > 0),
    status CHAR DEFAULT 'p',
    fk_vendas INTEGER,
    FOREIGN KEY (fk_vendas) REFERENCES vendas (venda_id)
);


Função:
Registra favoritos vinculados a vendas.
Inclui validação para valores acima de zero.

📌 2. Tabela itens_notas_fiscais
CREATE TABLE IF NOT EXISTS itens_notas_fiscais(
    numero INTEGER,
    id_item INTEGER,
    data_emissao DATE,
    produto_codigo VARCHAR(20),
    produto_descriacao VARCHAR(200),
    quantidade DECIMAL(10,3),
    valor_total DECIMAL(10,2),
    valor_unitario DECIMAL(10,2)
);


Função:
Armazena todos os itens incluídos nas notas fiscais (produtos, valores e quantidades).

📌 3. Tabela produtos
CREATE TABLE IF NOT EXISTS produtos(
    produto_id SERIAL,
    codigo VARCHAR(20),
    descricao VARCHAR(200),
    preco DECIMAL(10,2),
    estoque INTEGER
);


Função:
Define os produtos cadastrados no sistema, com preço, estoque e códigos.

📌 4. Tabela notas_fiscais
CREATE TABLE IF NOT EXISTS notas_fiscais(
    numero INTEGER PRIMARY KEY,
    data_emissao DATE,
    valor_total DECIMAL(10,2),
    valor_unitario DECIMAL(10,2),
    cliente_id INTEGER,
    FOREIGN KEY (cliente_id) REFERENCES clientes (cliente_id)
);


Função:
Armazena dados da nota fiscal referente a um cliente específico.

📌 5. Tabela clientes
CREATE TABLE clientes (
    cliente_id SERIAL PRIMARY KEY,
    nome VARCHAR(100) NOT NULL,
    cpf VARCHAR(14) UNIQUE,
    email VARCHAR(100),
    telefone VARCHAR(15)
);


Função:
Tabela para cadastro de clientes, com CPF único e dados de contato.

📌 6. Inserção de Dados
INSERT INTO clientes(nome, email, telefone, cpf)
VALUES ('ana', 'analuisa2525@gmail.com', '31997702277', '14563018963');

SELECT * FROM clientes;
