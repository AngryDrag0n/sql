**ESTRUTURA DE UMA CONSULTA**

**SELECT** Lista de atributos  
**FROM** Lista de tabelas  
**WHERE** Condições

Para verificar se as consultas estão corretas, utilize o banco de dados chamado codeacademy que foi disponibilizado.

Exercícios:

1) Listar todas as informações dos produtos cadastrados.  
   SELECT* from produto;`  
 


2) Listar o código, nome fantasia, endereço, telefone e código da cidade dos fornecedores cadastrados.  
   SELECT `codFornecedor`, `nomeFantasia`, `endereco`, `telefone`, `codCidade` FROM `fornecedor`; ``  
     
     
3) Listar o código da venda, data de venda de todas as vendas com status de ‘Despachada’.  
   SELECT codVenda, codVendedor, dataVenda from venda WHERE status = 'despachada';
     
     
4) Listar todas as informações da tabela de pessoas jurídicas.  
   SELECT* from clienteJuridico;
     
     
5) Listar o número do lote dos produtos que estão com a data de validade vencida.  
   SELECT numeroLote from produtoLote WHERE dataValidade < CURRENT_DATE;  
 


6) Listar o nome dos departamentos.

	SELECT nome from departamento;

