Observação: As tabelas descritas abaixos estão incompletas, nos pŕoximos dias iremos completar elas conforme novos conteúdos são estudados.

Tabela departamento:

* O campo codDepartamento é de numeração automática (SERIAL)  
* O campo nome é de texto, de tamanho variável máximo 40, sendo uma chave candidata (UNIQUE), de preenchimento obrigatório;  
* O campo descricaoFuncional é de texto, de tamanho variável máximo 80, sendo um campo de preenchimento opcional;  
* O campo localizacao é de texto, de tamanho ilimitado.  
    
  create TABLE departamento(  
  	codDepartamento int PRIMARY KEY not null,  
  	nome varchar(40) not null UNIQUE,  
  	descricaoFuncional varchar(80),  
  	localizacao text      
  );	

Tabela estado:

* O campo siglaEstado é de texto, de tamanho fixo 2;  
* O campo nome é de texto, de tamanho variável máximo 30, sendo uma chave candidata de preenchimento obrigatório.  
    
  create TABLE estado(  
  	siglaEstado char(2),  
  	nome varchar(30) not null  
  );

Tabela cidade:

* O campo codCidade é de numeração automática  
* O campo nome é texto, de tamanho variável máximo 50, sendo uma chave candidata, de preenchimento obrigatório;  
* O campo siglaEstado é de texto, de tamanho fixo 2 e de preenchimento obrigatório

	create TABLE cidade(  
	codCidade int,  
	nome varchar(50) unique not null,  
	siglaEstado char(2) not null  
      
);

Tabela vendedor:

* O campo codVendedor é de numeração automática;  
* O campo nome é de texto, de tamanho variável máximo 60, de preenchimento obrigatório;  
* O campo dataNascimento é um campo tipo data;  
* O campo endereco é de texto, de tamanho variável máximo 60;  
* O campo cep é tamanho fixo máximo 8;  
* O campo telefone é caracter, de tamanho variável máximo 20;  
* O campo codCidade é inteiro;  
* A dataContratacao é um campo data, que terá como valor padrão a data atual de inserção do registro, no caso de uma data não ter sido especificada;  
* O campo codDepartamento é inteiro;  
*   
  CREATE TABLE vendedor (  
  	codVendedor INT PRIMARY KEY AUTO\_INCREMENT,  
  	nome VARCHAR(60) NOT NULL,  
  	dataNascimento DATE,  
  	endereco VARCHAR(60),  
  	cep CHAR(8),  
  	telefone CHAR(20),  
  	codCidade INT,  
  	codDepartamento INT,  
  	dataContratacao DATE DEFAULT NULL,  
  	FOREIGN KEY (codCidade) REFERENCES cidade(codCidade),  
  	FOREIGN KEY (codDepartamento) REFERENCES departamento(codDepartamento)  
  );


Tabela cliente:

* O campo codCliente é um campo de numeração automática;  
* O campo endereco é de texto, de tamanho variável máximo 60;  
* O campo codCidade é inteiro e de preenchimento obrigatório;  
* O campo telefone é de texto, de tamanho variável máximo 20;  
* O campo tipo é caracter, de tamanho fixo máximo 1, sendo que pode assumir somente os valores F ou J;   
* A dataCadastro é um campo data, que terá como valor padrão a data atual de cadastro, no caso de uma data não ter sido especificada;  
* O campo cep é tamanho fixo máximo 8;  
  CREATE TABLE cliente(  
  	codCliente INT PRIMARY KEY AUTO\_INCREMENT,  
  	endereco varchar(60),  
  	codCidade int NOT null,  
  	telefone varchar(20),  
  	tipo CHAR(1) CHECK (tipo in ('F', 'J')),  
  	dataCadastro DATE DEFAULT(CURRENT\_DATE()),  
  	cep CHAR(8),  
  	FOREIGN KEY (codCidade) REFERENCES cidade(codCidade)  
  );




Tabela clienteFisico:

* O campo codCliente é um inteiro;  
* O campo nome é de texto, de tamanho variável máximo 50, de preenchimento obrigatório;  
* O campo dataNascimento é um campo data;  
* O campo cpf é caracter, de tamanho variável máximo 11, de preenchimento obrigatório, sendo uma chave candidata;  
* O campo rg é caracter, de tamanho variável máximo 8;  
  CREATE TABLE clienteFisico(  
  	codCliente INT PRIMARY KEY,  
  	nome varchar(50) not null,  
  	dataNascimento date,  
  	cpf char(11) unique not null,  
  	rg varchar(8)  
  	FOREIGN KEY(codCliente) REFERENCES cliente(codCliente)  
  	  
  );

Tabela clienteJuridico:

* O campo codCliente é um inteiro;  
* O campo nomeFantasia é de texto, de tamanho variável máximo 80, sendo uma chave candidata;  
* O campo razaoSocial é de texto, de tamanho variável máximo 80, sendo uma chave candidata, de preenchimento obrigatório;  
* O campo ie (inscrição estadual) é de texto, de tamanho variável máximo 20, de preenchimento obrigatório, sendo uma chave candidata;  
* O campo cgc é de texto, de tamanho variável máximo 20, sendo uma chave candidata, de preenchimento obrigatório;  
  CREATE TABLE pessoaJuridica(  
  	codCliente INT PRIMARY KEY,  
  	nomeFantasia varchar(80) unique,  
  	razaoSocial varchar(80) unique not null,  
  	ie varchar(20) unique not null,  
  	cgc varchar(20) unique not null,  
  	FOREIGN KEY(codCliente) REFERENCES cliente(codCliente)  
  );

Tabela classe:

* O campo codClasse é um campo de numeração automática;  
* O campo sigla é de texto, de tamanho variável máximo 12;  
* O campo nome é de texto, de tamanho variável máximo 40, com preenchimento obrigatório;  
* O campo descricao é de texto, de tamanho variável máximo 80\.  
  CREATE TABLE pessoaJuridica(  
  	codCliente INT PRIMARY KEY,  
  	nomeFantasia varchar(80) unique,  
  	razaoSocial varchar(80) unique not null,  
  	ie varchar(20) unique not null,  
  	cgc varchar(20) unique not null,  
  	FOREIGN KEY(codCliente) REFERENCES cliente(codCliente)  
  );


  
Tabela produto:

* O campo codProduto é um campo de numeração automática;  
* O campo descrição é de texto, de tamanho variável máximo 40, sendo de preenchimento obrigatório;  
* O campo unidadeMedida é de texto, de tamanho fixo máximo 2;  
* O campo embalagem é de texto, de tamanho variável máximo 15, que terá como valor padrão padrão ‘Fardo’, no caso de uma embalagem não ter sido especificada;  
* O campo codClasse é um inteiro;  
* O campo precoVenda é um numérico com tamanho 14, com 2 casas decimais;  
* O campo estoqueMinimo é um numérico com tamanho 14, com 2 casas decimais;  
  create TABLE produto(  
  	codProduto INT PRIMARY KEY AUTO\_INCREMENT,  
  	descricao varchar(40) not null,  
  	unidadeMedia char(2),  
  	embalagem varchar(15) DEFAULT('Fardo'),  
  	codClasse INT,  
  	precoVenda decimal(16,2),  
  	estoqueMinino decimal (16, 2),  
  	FOREIGN KEY (codClasse) REFERENCES classe(codClasse)  
  );

Tabela produtoLote:

* O campo codProduto é um campo inteiro;  
* O campo numeroLote é um campo inteiro;  
* O campo quantidadeAdquirida é um numérico com tamanho 14, com 2 casas decimais;  
* O campo quantidadeVendida é um numérico com tamanho 14, com 2 casas decimais;  
* O campo precoCusto é um numérico com tamanho 14, com 2 casas decimais;  
* O campo dataValidade é um campo de data;  
  CREATE TABLE produtoLote(  
  	codProduto INT,  
  	numeroLote INT,  
  	quantidadeAdquirida decimal(16,2),  
  	quantidadeVendida decimal (16,2),  
  	precoCusto decimal(16,2),  
  	datavalidade date,  
  	``PRIMARY KEY(`numeroLote`)``  
      	FOREIGN KEY (codProduto) REFERENCES produto(codProduto)  
  );

Tabela venda:

* O campo codVenda é um campo inteiro;  
* O campo codCliente é um campo inteiro;  
* O campo codVendedor é um campo inteiro;  
* O campo dataVenda é um campo de data, que tem como valor padrão a data atual, sendo que outras datas podem ser especificadas;  
* O campo enderecoEntrega é caracter, de tamanho variável máximo 60;  
* O campo status é caracter, de tamanho variável máximo 30;  
  CREATE TABLE venda(  
  	codVenda int PRIMARY KEY,  
  	codCliente int,  
  	codVendedor int,  
  	dataVenda date DEFAULT(CURRENT\_DATE()),  
  	enderecoEntrega varchar(60),  
  	situacao varchar(30),  
  	FOREIGN KEY(codVendedor) REFERENCES vendedor(codVendedor),  
  	FOREIGN KEY(codCliente) REFERENCES cliente(codCliente)  
  );

Tabela itemVenda:

* O campo codVenda é um campo inteiro;  
* O campo codProduto é um campo inteiro;  
* O campo numeroLote é um campo inteiro;  
* O campo quantidade é um numérico com tamanho 14, com 2 casas decimais, sendo seu preenchimento obrigatório e com valor positivo;  
  CREATE TABLE itemVenda(  
  	codVenda INT,  
  	codProduto INT,  
  	numeroLote INT,  
  	quantidade decimal (16,2) not null CHECK(quantidade \> 0),  
  	FOREIGN KEY (numeroLote) REFERENCES produtoLote(numeroLote),  
  	FOREIGN KEY (codProduto) REFERENCES produto(codProduto),  
  	FOREIGN KEY (codVenda) REFERENCES venda(codVenda)  
        
  );

Tabela fornecedor:

* O campo codFornecedor é um inteiro;  
* O campo nomeFantasia é caracter, de tamanho variável máximo 80, sendo uma chave candidata;  
* O campo razaoSocial é caracter, de tamanho variável máximo 80, sendo uma chave candidata, de preenchimento obrigatório;  
* O campo ie (inscrição estadual) é caracter, de tamanho variável máximo 20, de preenchimento obrigatório, sendo uma chave candidata;  
* O campo cgc é caracter, de tamanho variável máximo 20, sendo uma chave candidata, de preenchimento obrigatório;  
* O campo endereco é caracter, de tamanho variável máximo 60;  
* O campo telefone é caracter, de tamanho variável máximo 20;  
* O campo codCidade é inteiro;  
  CREATE TABLE fornecedor(  
* 	codFornecedor INT PRIMARY KEY,  
* 	nomeFantasia varchar(80) unique,  
* 	razaoSocial varchar(80) unique not null,  
* 	ie varchar(20) not null unique,  
* 	cgc varchar(20) not null unique,  
* 	endereco varchar(60),  
* 	telefone varchar(20),  
* 	codCidade int,  
* 	FOREIGN KEY (codCidade) REFERENCES cidade(codCidade)  
* );


  
Tabela pedido:

* O campo codPedido é serial;  
* O campo dataRealizacao é um campo de data, que tem como valor padrão a data atual, sendo que outras datas podem ser especificadas;  
* O campo dataEntrega é um campo de data;  
* O campo codFornecedor é um campo inteiro;  
* O campo valor é um campo numérico de tamanho 20 com duas casas decimais;  
  CREATE TABLE pedido(  
  	codPedido INT AUTO\_INCREMENT PRIMARY KEY,  
  	dataRealizacao date DEFAULT(CURRENT\_DATE()),  
  	dataEntrega date,  
  	codFornecedor INT,  
  	valor decimal(20,2),  
  	FOREIGN KEY (codFornecedor) REFERENCES fornecedor(codFornecedor)  
  );


Tabela itemPedido:

* O campo codPedido é inteiro  
* O campo codProduto é inteiro;  
* O campo quantidade é um numérico com tamanho 14, com 2 casas decimais, sendo seu preenchimento obrigatório e com valor positivo.  
  [CREATE TABLE](http://localhost:8088/url.php?url=https://dev.mysql.com/doc/refman/8.0/en/create-table.html) itemPedido( codPedido INT, codProduto INT, quantidade DECIMAL(16, 2\) [NOT](http://localhost:8088/url.php?url=https://dev.mysql.com/doc/refman/8.0/en/logical-operators.html%23operator_not) NULL CHECK (quantidade \> 0), PRIMARY KEY(codPedido, codProduto), FOREIGN KEY (codPedido) REFERENCES pedido (codPedido), FOREIGN KEY (codProduto) REFERENCES produto (codProduto) );


