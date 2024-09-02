# Sistema de Controle de Estoque

## Descrição

Este projeto envolve o desenvolvimento de um Sistema de Controle de Estoque para gerenciar produtos, fornecedores e pedidos de reposição. O sistema armazena informações sobre produtos disponíveis em estoque, fornecedores que os fornecem e os pedidos de reposição realizados para manter o estoque adequado.

## Estrutura do Banco de Dados

O banco de dados `SistemaControleEstoque` inclui três tabelas principais:

1. **Fornecedores**
   - `id_fornecedor` (INT, AUTO_INCREMENT, PRIMARY KEY)
   - `nome` (VARCHAR(100))
   - `contato` (VARCHAR(100))
   - `telefone` (VARCHAR(20))

2. **Produtos**
   - `id_produto` (INT, AUTO_INCREMENT, PRIMARY KEY)
   - `nome` (VARCHAR(100))
   - `preco` (DECIMAL(10,2))
   - `quantidade_estoque` (INT)
   - `id_fornecedor` (INT, FOREIGN KEY referenciando `Fornecedores`)

3. **PedidosReposicao**
   - `id_pedido` (INT, AUTO_INCREMENT, PRIMARY KEY)
   - `id_produto` (INT, FOREIGN KEY referenciando `Produtos`)
   - `quantidade` (INT)
   - `data_pedido` (DATE)

## Comandos SQL Utilizados

- `CREATE DATABASE` para criar o banco de dados.
- `CREATE TABLE` para definir as tabelas e suas colunas.
- `INSERT INTO` para adicionar dados às tabelas.
- `SELECT` para consultar dados.
- `UPDATE` para atualizar dados existentes.
- `DELETE` para remover dados.
- `JOIN` para combinar dados de múltiplas tabelas em consultas.

## Consultas SQL

1. **Mostrar todos os produtos em estoque:**
   ```sql
   SELECT * FROM Produtos;
   
2. Mostrar todos os pedidos de reposição realizados:
SELECT PedidosReposicao.id_pedido, Produtos.nome AS Produto, PedidosReposicao.quantidade, PedidosReposicao.data_pedido
FROM PedidosReposicao
JOIN Produtos ON PedidosReposicao.id_produto = Produtos.id_produto;

3. Mostrar informações sobre os fornecedores e os produtos fornecidos por eles:
SELECT Fornecedores.nome AS Fornecedor, Produtos.nome AS Produto, Produtos.preco, Produtos.quantidade_estoque
FROM Produtos
JOIN Fornecedores ON Produtos.id_fornecedor = Fornecedores.id_fornecedor;

Atualizações e Exclusões de Dados
Atualizar a quantidade de produtos em estoque após receber um novo pedido de reposição.
Deletar produtos descontinuados.
Deletar fornecedores que não fornecem mais produtos.
Instalação e Uso
Execute o script SQL para criar o banco de dados e as tabelas.
Insira os dados de exemplo conforme fornecido no script.
Utilize as consultas para verificar e gerenciar o estoque.
Licença
Este projeto é de domínio público.
