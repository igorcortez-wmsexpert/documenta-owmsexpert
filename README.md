# WMSExpert
**Documentação de integração WMSExpert**

# Importação de dados cadastrais <br />

> As Views de cadastro tem como função principal integrar as duas bases de dados, permitindo que os cadastros sejam feitos apenas no Erp e que possam ser importados integralmente para o WMS Expert, sem retrabalho.

> ### View de cidades WMS_CIDADE

``` 
CREATE VIEW WMS_CIDADE AS 
SELECT 
codCidadeIBGE,
nomeCidade,
uf
FROM CIDADES
```

**codCidadeIBGE:** *O campo deve ser **inteiro**, o mesmo e chave primaria.* <br />
**nomeCidade:** *O campo deve ser **varchar(100)** e deve conter a descrição da cidade.* <br />
**uf:** *O campo deve ser **varchar(2)** e deve conter a abreviatura do estado da cidade.* <br />

> ### View de clientes WMS_CLIENTE

``` 
CREATE VIEW WMS_CLIENTE AS 
SELECT 
codClienteErp,
tipo,
cpfCnpj,
nomCliente,
nomFantasia,
codCidadeIbge,
endereco,
numEndereco,
bairro,
cep,
celular,
email,
codRota,
desRota,
latitude,
longitude,
shelf
FROM CLIENTES
```

**codClienteErp:** *O campo deve ser **varchar(20)**, contendo o codigo do cliente do ERP o campo e chave primaria e **obrigatorio**.* <br />
**tipo:** *O campo deve ser **inteiro** contendo 0 para pessoa fisica e 1 para pessoa juridica o campo e **obrigatorio**.* <br />
**cpfCnpj:** *O campo deve ser **varchar(14)** contendo a inscrição da pessoa fisica ou juridica o campo e **obrigatorio**.* <br />
**nomCliente:** *O campo deve ser **varchar(60)** contendo a razão social do cliente o campo e **obrigatorio**.* <br />
**nomFantasia:** *O campo deve ser **varchar(60)** contendo o nome fantasia do cliente o campo e **obrigatorio**.* <br />
**codCidadeIBGE:** *O campo deve ser **inteiro**, o mesmo e chave primaria o campo e **obrigatorio**.* <br />
**endereco:** *O campo deve ser **varchar(60)** contendo o endereço do cliente o campo e **obrigatorio**.* <br />
**numEndereco:** *O campo deve ser **varchar(10)** contendo o numero do endereço do cliente o campo e **obrigatorio**.* <br />
**bairro:** *O campo deve ser **varchar(30)** contendo a descrição do bairro do cliente o campo e **obrigatorio**.* <br />
**cep:** *O campo deve ser **varchar(8)** contendo o contendo o codigo postal do cliente o campo e **obrigatorio**.* <br />
**celular:** *O campo deve ser **varchar(10)** contendo o telefone do cliente.* <br />
**email:** *O campo deve ser **varchar(50)** contendo o e-mail do cliente.* <br />
**codRota:** *O campo deve ser **inteiro** contendo o codigo da rota.* <br />
**desRota:** *O campo deve ser **varchar(60)** contendo a descrição da rota.* <br />
**latitude:** *O campo deve ser **numeric(18,7)** contendo a latitudo do cliente.* <br />
**longitude:** *O campo deve ser **numeric(18,7)** contendo a longitude do cliente.* <br />
**shelf:** *O campo deve ser **inteiro** contendo a quantidade de dias do shelf do cliente.* <br /><br />


> ### View de embalagens WMS_EMBALAGEM

``` 
CREATE VIEW WMS_EMBALAGEM AS 
SELECT 
codEmbalagem,
codFilial,
codProdutoErp,
aux,
und,
qtdUnit,
embalagem,
pesoLiquido,
pesoBruto,
volume,
Ativo
FROM EMBALAGENS
```

**codEmbalagem:** *Enviar o campo como **NULL**.* <br />
**codFilial:** *O campo deve ser **inteiro**, o mesmo e chave primaria o campo e **obrigatorio**.* <br />
**codProdutoErp:** *O campo deve possuir a chave estrangeira do produto o campo e **obrigatorio**.* <br />
**aux:** *O campo deve ser **varchar(20)** contendo o codigo de barras do produto o campo e **obrigatorio**.* <br />
**und:** *O campo deve ser **varchar(3)** contendo a descrição reduzida da embalagem o campo e **obrigatorio**.* <br />
**qtdUnit:** *O campo deve ser **numerico(12,2)**, contendo o fator de conversão da unidade o campo e **obrigatorio** e tem de ser diferente de zero.* <br />
**embalagem:** *O campo deve ser **varchar(20)** contendo a descrição da embalagem o campo e **obrigatorio**.* <br />
**pesoLiquido:** *O campo deve ser **numeric(18,4)** contendo o peso liquido da embalagem.* <br />
**pesoBruto:** *O campo deve ser **numeric(18,4** contendo o peso bruto da embalagem.* <br />
**volume:** *O campo deve ser **numeric(18,2)** contendo a o volume em **m3** da embalagem.* <br />
**ativo:** *O campo deve ser **inteiro** contendo 1 para ativo e 0 para inativo o campo e **obrigatorio**.* <br /><br />

> ### View de estoque WMS_ESTOQUE

``` 
CREATE VIEW WMS_ESTOQUE AS 
SELECT 
codFilialErp,
codProdutoErp,
qtdEstoque,
lote,
validade,
numeroSerie
FROM ESTOQUE
```

**codFilialErp:** *O campo deve ser **inteiro**, o mesmo e chave primaria o campo e **obrigatorio**.* <br />
**codProdutoErp:** *Chave estrangeira do codigo do produto o campo e **obrigatorio**.* <br />
**qtdEstoque:** *O campo deve ser **numerico(18,2)**, contendo a quantidade de estoque do produto o campo e **obrigatorio**.* <br />
**lote:** *O campo deve ser **varchar(50)**, contendo o lote do produto.* <br />
**validade:** *O campo deve ser **date**, contendo a data de validade do produto.* <br />
**numeroSerie:** *O campo deve ser **varchar(50)**, contendo o numero de serie do produto.* <br /><br />

> ### View de filial WMS_FILIAL

``` 
CREATE VIEW WMS_FILIAL AS 
SELECT 
codFilialErp,
nomFilial,
nomFantasia,
cnpj,
ativo,
codCidadeIbge
FROM FILIAL
```

**codFilialErp:** *O campo deve ser **varchar(100)** contendo o codigo da filial esse campo e chave primaria e **obrigatorio**.* <br />
**nomFilial:** *O campo deve ser **varchar(50)** contendo o nome da filial o campo e **obrigatorio**.* <br />
**nomFantasia:** *O campo deve ser **varchar(50)** contendo a fantasia da filial o campo e **obrigatorio**.* <br />
**cnpj:** *O campo deve ser **varchar(17)**, contendo o cnpj da filial o campo e **obrigatorio**.* <br />
**ativo:** *O campo deve ser **inteiro**, contendo 1 para ativo e 0 para inativo o campo e **obrigatorio**.* <br />
**codCidadeIbge:** *O campo deve ser **inteiro**, contendo o codigo da cidadeIbge.* <br /><br />

> ### View de fornecedor WMS_FORNECEDOR

``` 
CREATE VIEW WMS_FORNECEDOR AS 
SELECT 
codFornecedorErp,
nomeFornecedor,
nomeFantasia,
tipo,
cnpjcpf,
endereco,
numEndereco,
bairro,
codCidadeIbge,
cep
FROM FORNECEDOR
```

**codFornecedorErp:** *O campo deve ser **varchar(20)**, contendo o codigo do fornecedor esse campo e chave primaria e **obrigatorio**.* <br />
**nomeFornecedor:** *O campo deve ser **varchar(60)** contendo a razão social do fornecedor o campo e **obrigatorio**.* <br />
**nomeFantasia:** *O campo deve ser **varchar(50)** contendo o nome fantasia do fornecedor o campo e **obrigatorio**.* <br />
**tipo:** *O campo deve ser **inteiro** contendo 0 para pessoa fisica e 1 para pessoa juridica o campo e **obrigatorio**.* <br />
**cpfCnpj:** *O campo deve ser **varchar(14)** contendo a inscrição da pessoa fisica ou juridica o campo e **obrigatorio**.* <br />
**endereco:** *O campo deve ser **varchar(60)** contendo o endereço do fornecedor.* <br />
**numEndereco:** *O campo deve ser **varchar(10)** contendo o numero do endereço do fornecedor.* <br />
**bairro:** *O campo deve ser **varchar(30)** contendo a descrição do bairro do fornecedor.* <br />
**codCidadeIBGE:** *O campo deve ser **inteiro**, o mesmo e chave primaria o campo e **obrigatorio**.* <br />
**cep:** *O campo deve ser **varchar(8)** contendo o contendo o codigo postal do fornecedor.* <br /><br />


> ### View de funcionario WMS_FUNCIONARIO

``` 
CREATE VIEW WMS_FUNCIONARIO AS 
SELECT 
codFuncionarioErp,
nomefuncionario,
ativo
FROM FUNCIONARIO
```

**codFuncionarioErp:** *O campo deve ser  **varchar(20)**, contendo o codigo do funcionario esse campo e chave primaria e **obrigatorio**.* <br />
**nomefuncionario:** *O campo deve ser **varchar(60)** contendo o nome do funcionario o campo e **obrigatorio**.* <br />
**ativo:** *O campo deve ser **inteiro** contendo 0 para inativo e 1 para ativo o campo e **obrigatorio**.* <br /><br />

> ### View de grupo de produto WMS_GRUPO

``` 
CREATE VIEW WMS_GRUPO AS 
SELECT 
codGrupoErp,
desGrupo,
ativo
FROM GRUPO
```

**codGrupoErp:** *O campo deve ser **varchar(25)**, contendo o codigo do grupo esse campo e chave primaria e **obrigatorio**.* <br />
**desGrupo:** *O campo deve ser **varchar(50)** contendo o nome do grupo o campo e **obrigatorio**.* <br />
**ativo:** *O campo deve ser **inteiro** contendo 0 para inativo e 1 para ativo o campo e **obrigatorio**.* <br /><br />

> ### View de produto WMS_PRODUTO

``` 
CREATE VIEW WMS_PRODUTO AS 
SELECT 
codProdutoERP,
descProd,
situacao,
revenda,
vlrUltimaCompra,
codFornecedorErp,
codGrupoErp,
fracionado,
qtdPallet,
qtdCx,
controlaLote,
controlaValidade,
controlaFabricacao,
controlaNumSerie,
Shelf,
diasVencimento
FROM PRODUTO
```

**codProdutoErp:** *O campo deve ser **vatchar(30)**, contendo o codigo do produto do ERP esse campo e chave primaria e **obrigatorio**.* <br />
**descProd:** *O campo deve ser **varchar(50)** contendo a descrição do produto o campo e **obrigatorio**.* <br />
**situacao:** *O campo deve ser **inteiro** contendo 0 para inativo e 1 para ativo o campo e **obrigatorio**.* <br />
**revenda:** *O campo deve ser **inteiro** contendo 0 para inativo e 1 para ativo.* <br />
**vlrUltimaCompra:** *O campo deve ser **numerico(10,2)** contendo o preço de custo do produto.* <br />
**codFornecedorErp:** *O Campo deve conter o codigo do fornecedor do produto.* <br />
**codGrupoErp:** *O campo deve conter o codigo do grupo do produto o campo e **obrigatorio**.* <br />
**fracionado:** *O campo deve ser **inteiro**, contendo 1 se o produto permitir quantidade fracionadas e 0 para não.* <br />
**qtdPallet:** *O campo deve ser **numerico(10,2)**, contendo a quantidade que o palete suporta da menor unidade de estoque do produto.* <br />
**qtdCx:** *O campo deve ser **numerico(10,2)**, contendo a quantidade da embalagem master do produto.* <br />
**controlaLote:** *O campo deve ser **inteiro**, contendo 1 para controla e 0 para não controla.* <br />
**controlaValidade:** *O campo deve ser **inteiro**, contendo 1 para controla e 0 para não controla.* <br />
**controlaFabricacao:** *O campo deve ser **inteiro**, contendo 1 para controla e 0 para não controla.* <br />
**controlaNumSerie:** *O campo deve ser **inteiro**, contendo 1 para controla e 0 para não controla.* <br />
**Shelf:** *O campo deve ser **inteiro**, contendo a quantidade de dias de shelf do produto.* <br />
**diasVencimento:** *O campo deve ser **inteiro**, contendo a quantidade de dias para geração do vencimento automatico do produto.* <br /><br /><br />

> ### View de subgrupo de produto WMS_SUBGRUPO

``` 
CREATE VIEW WMS_SUBGRUPO AS 
SELECT 
codSubGrupoErp,
desSubGrupo,
ativo
FROM SUBGRUPO
```

**codSubGrupoErp:** *O campo deve ser **varchar(25)**, contendo o codigo do subgrupo esse campo e chave primaria e **obrigatorio**.* <br />
**desSubGrupo:** *O campo deve ser **varchar(50)** contendo o nome do subgrupo o campo e **obrigatorio**.* <br />
**ativo:** *O campo deve ser **inteiro** contendo 0 para inativo e 1 para ativo o campo e **obrigatorio**.* <br /><br />

> ### View de transportadora WMS_TRANSPORTADORA

``` 
CREATE VIEW WMS_TRANSPORTADORA AS 
SELECT 
codTransportadoraErp,
nomeTransportadora,
nomeFantasia,
cpfCnpj,
ativo
FROM VEICULOS
```

**codTransportadoraErp:** *O campo deve ser **varchar(25)**, contendo o codigo da transportadora, esse campo e chave primaria e **obrigatorio**.* <br />
**nomeTransportadora:** *O campo deve ser **varchar(100)**, contendo o nome da transportadora esse campo e **obrigatorio**.* <br />
**nomeFantasia:** *O campo deve ser **varchar(100)**, contendo o nome fantasia da transportadora, esse campo e **obrigatorio**.* <br />
**cpfCnpj:** *O campo deve ser **varchar(20)**, contendo a cpf ou cnpj da transportadora o campo e **obrigatorio**.* <br />
**ativo:** *O campo deve ser **inteiro**, contendo 1 para ativo e 0 para inativo esse campo e **obrigatorio**.* <br /><br />

> ### View de veiculos de produto WMS_VEICULO

``` 
CREATE VIEW WMS_VEICULOS AS 
SELECT 
codVeiculoErp,
codTransportadoraErp,
placa,
descricao,
pesoLiquido,
pesoBruto,
volume
FROM VEICULOS
```

**codVeiculoErp:** *O campo deve ser **varchar(25)**, contendo o codigo do veiculo, esse campo e chave primaria e **obrigatorio**.* <br />
**codTransportadoraErp:** *O campo deve ser **varchar(25)**, contendo o codigo da transportadora do veiculo.* <br />
**placa:** *O campo deve ser **varchar(20)**, contendo a placa do veiculo o campo e **obrigatorio**.* <br />
**descricao:** *O campo deve ser **varchar(100)**, contendo o nome do veiculo o campo e **obrigatorio**.* <br />
**pesoLiquido:** *O campo deve ser **numeric(10,4)**, contendo o peso liquido do veiculo.* <br />
**pesoBruto:** *O campo deve ser **numeric(10,4)**, contendo o peso bruto do veiculo.* <br />
**volume:** *O campo deve ser **numeric(10,4)**, contendo o volume em m3 do veiculo.* <br /><br />


# Importação de movimentos <br />

> As Views de entrada de produtos são todas as que compreendem processos aonde a mercadoria será recebida, como por exemplo: Recebimento de notas fiscais de fornecedores, devoluções de clientes, devoluções de garantia.

> ### View de carga de entrada WMS_CARGA

``` 
CREATE VIEW WMS_CARGA AS 
SELECT 
codCarga,
codFilialErp,
data
FROM BONUSCAB
```

**Somente deve conter essa View em caso de possuir o processo de agrupamentos de notas de entrada** <br />

**codCarga:** *O campo deve ser **varchar(20)**, contendo o numero da carga de recebimento esse campo e **obrigatorio**.* <br />
**codFilialErp:** *O campo deve conter a chave da filial o campo e **obrigatorio**..* <br />
**data:** *O campo deve ser **data** e deve conter a data de montagem do bonus o campo e **obrigatorio**.* <br /><br />

> ### View de notas fiscais de entrada WMS_NOTAFISCALENTRADA

``` 
CREATE VIEW WMS_NOTAFISCALENTRADA AS 
SELECT 
codNotaFiscalErp,
codFilialErp,
codCarga,
codFornecedorErp,
dadosAdicionais,
tipo,
dtEmissao,
valTotProduto,
valTotNotaFiscal,
serie
FROM NOTAFISCALENTRADA
```

**Somente colocar o campo codCarga se a importação for por carga.** <br />

**codNotaFiscalErp:** *O campo deve ser **varchar(20)**, contendo o numero da nota fiscal esse campo e **obrigatorio**.* <br />
**codFilialErp:** *O campo deve conter a chave da filial de origem.* <br />
**codCarga:** *O campo deve ser **inteiro**, contendo o numero do bonus, o campo e **obrigatorio**.* <br />
**codFornecedorErp:** *O Campo deve conter o codigo do fornecedor da nota, o campo e **obrigatorio**.* <br />
**dadosAdicionais:** *O campo deve ser **varchar(200)**, e deve contes complementos da nota.* <br />
**tipo:** *O campo deve ser **inteiro**, contendo o modelo do documento: Compra = 55, Devolução = 9, Transferencia = 8 e Produção = 11, Expresso = 2, o campo e **obrigatorio**.* <br />
**dtEmissao:** *O campo deve ser **data** e deve conter a data de entrada da nota, campo e **obrigatorio**.* <br />
**valTotProduto:** *O campo deve ser **numerico(18,2)** contendo a soma do valor total dos produtos, o campo e **obrigatorio**.* <br />
**valTotNotaFiscal:** *O campo deve ser **numerico(15,2)** contendo o valor total da nota fiscal de entrada, o campo e **obrigatorio**.* <br />
**serie:** *O campo deve ser **inteiro** contendo a serie da nota fiacal, o campo e **obrigatorio**.* <br /><br />

> ### View de notas fiscais de entrada WMS_NOTAFISCALITEMENTRADA

``` 
CREATE VIEW WMS_NOTAFISCALITEMENTRADA AS 
SELECT 
codNotaFiscalErp,
codFilialErp,
codCarga,
codFornecedorErp,
tipo,
codProdutoErp,
unidade,
quantidade,
valUnitario,
serie
FROM NOTAFISCALITEMENTRADA
```

**Somente colocar o campo codCarga se a importação for por carga.** <br />

**codNotaFiscalErp:** *O campo deve ser **varchar(20)**, contendo o numero da nota fiscal, o campo e **obrigatorio**.* <br />
**codFilialErp:** *O campo deve conter a chave da filial de origem.* <br />
**codCarga:** *O campo deve ser **inteiro**, contendo o numero do bonus, o campo e **obrigatorio**.* <br />
**codFornecedorErp:** *O Campo deve conter o codigo do fornecedor da nota, o campo e **obrigatorio**.* <br />
**tipo:** *O campo deve ser **inteiro**, contendo o modelo do documento: Compra = 55, Devolução = 9, Transferencia = 8 e Produção = 11, Expresso = 2, o campo e **obrigatorio**.* <br />
**codProdutoErp:** *Chave estrangeira do codigo do produto, o campo e **obrigatorio**.* <br />
**unidade:** *O campo deve ser **varchar(3)** contendo a abreviação da embalagem.* <br />
**quantidade:** *O campo deve ser **numerico(12,4)** contendo a quantidade do produto, o campo e **obrigatorio**.* <br />
**valUnitario:** *O campo deve ser **numerico(16,2)** contendo o valor unitario do produto, o campo e **obrigatorio**.* <br />
**serie:** *O campo deve ser **inteiro)** contendo a serie da nota fiscal de entrada, o campo e **obrigatorio**.* <br /><br />

> As Views de saída de produtos são todas as que compreendem processos aonde a mercadoria será separada para entrega, como por exemplo: Pedidos de venda, pedidos de
devolução de produtos a fornecedores, pedidos de demonstração.

> ### View de carregamento WMS_CARREGAMENTO

``` 
CREATE VIEW WMS_CARREGAMENTO AS 
SELECT 
codCarregamentoErp,
CodFilialERP,
totalPedidos,
dtGeracao,
codVeiculo,
destino,
codTransportadora
FROM PEDIDOSCAB
```

**codCarregamentoErp:** *O campo deve ser **varchar(20)**, contendo o numero do carregamento, esse campo e chave primaria e **obrigatorio**.* <br />
**CodFilialERP:** *O campo deve conter a chave da filial de origem esse campo e **obrigatorio**.* <br />
**totalPedidos:** *O Campo deve ser **inteiro**, contendo a quantidade de pedidos do carregamento, esse campo e **obrigatorio**.* <br />
**dtGeracao:** *O Campo deve **datetime**, contendo a data de geração do carregamento, esse campo e **obrigatorio**.* <br />
**codVeiculo:** *O campo deve conter a chave do veiculo.* <br />
**destino:** *O campo deve ser **varchar(100)**, contendo a descrição do destino do carregamento.* <br />
**codTransportadora:** *O campo deve conter a chave da transportadora.* <br /><br />

> ### View de pedidos WMS_PEDIDOSCAB

``` 
CREATE VIEW WMS_PEDIDOSCAB AS 
SELECT 
CodPedidoERP,
CodFilialERP,
codClienteErp,
codFuncionarioErp,
tipoPedido,
odemPedido,
dtGeracao,
qtdTotalItens,
valorTotal,
obs,
codRota,
desRota,
codCarregamentoErp
FROM PEDIDOSCAB
```

**CodPedidoERP:** *O campo deve ser **varchar(20)**, contendo o numero do pedido, esse campo e chave primaria e **obrigatorio**.* <br />
**CodFilialERP:** *O campo deve conter a chave da filial de origem (somente usar em casos de multi filial).* <br />
**codClienteErp:** *O Campo deve conter o codigo do cliente do pedido, o campo e **obrigatorio**.* <br />
**codFuncionarioErp:** *O Campo deve conter o codigo do funcionario da pedido, o campo e **obrigatorio**.* <br />
**tipoPedido:** *O campo deve ser **varchar(20)**, contendo a descrição do tipo do pedido EX: Venda, Balcão, Bonificação, etc, o campo e **obrigatorio**.* <br />
**odemPedido:** *O campo deve ser **inteiro**, contendo o nivel de prioridade do pedido, 0 – Urgente, 1 – Alta, 2 -Media, 3 – Baixa.* <br />
**dtGeracao:** *O campo deve ser **data** e deve conter a data de emissão do pedido.* <br />
**qtdTotalItens:** *O campo deve ser **inteiro** contendo a quantidade de itens no documento, o campo e **obrigatorio**.* <br />
**valTotProduto:** *O campo deve ser **numerico(16,2)** contendo o valor total do documento, o campo e **obrigatorio**.* <br />
**obs:** *O campo deve ser **nvarchar(1000)**, contendo a observação do pedido.* <br />
**codRota:** *O campo deve ser **inteiro**, contendo o codigo da rota do pedido.* <br />
**desRota:** *O campo deve ser **varchar(100)**, contendo a descrição da rota do pedido.* <br />
**desRota:** *O campo deve conter a chave do carregamento.* <br /><br />


> ### View de itens dos pedidos WMS_PEDIDOSITEM

``` 
CREATE VIEW WMS_PEDIDOSITEM AS 
SELECT 
itemPedido,
codPedidoErp,
codFilialErp,
codProduto,
valorUnitario,
qtdProduto,
valorTotal,
lote
FROM PEDIDOSITEM
```

**itemPedido:** *O campo deve ser **vatchar(10)**, conter o sequencial do item no pedido Ex: 0, 1, 2, 3, o campo e **obrigatorio**.* <br />
**codPedidoErp:** *O campo deve conter a chave estrangeira do pedido, o campo e **obrigatorio**.* <br />
**codFilialErp:** *O campo deve conter a chave da filial, o campo e **obrigatorio**.* <br />
**codProdutoErp:** *Chave estrangeira do codigo do produto, o campo e **obrigatorio**.* <br />
**valorUnitario:** *O campo deve ser **numerico(12,2)** contendo o valor unitario do produto, o campo e **obrigatorio**.* <br />
**qtdProduto:** *O campo deve ser **numerico(12,4)** contendo a quantidade do produto, o campo e **obrigatorio**.* <br />
**valorTotal:** *O campo deve ser **numerico(12,2)** contendo o valor total do produto, o campo e **obrigatorio**.* <br />
**lote:** *O campo deve ser **varchar(15)**, conter a informação do lote que deve ser separado.* <br />

**O campo lote somente deve ser preenchido se o produto controlar lote e se somente puder ser separado o lote informado do produto.** <br /><br />

# Retorno de movimentos <br />

> Os retornos de movimentos podem ser divididos em 3 tipos, retorno após a importação, retorno após a exclusão e retorno após a finalização do processo, os retornos servem para garantir que o processo ocorra em sintonia e sem necessidade de ações manuais no Erp.

> ### Retorno após a importação de movimentos 

> Após a importação de um movimento o Wms precisa retornar para o Erp que o movimento especifico ja foi recebido, esse retorno deve ocorrer por meio de uma stored procedure contendo os parametros necessarios para validação, uma vez executado o processo corretamente o movimento importado deve sair da View.

**Após realizar a importação do movimento de entrada o Wms ira executar uma stored procedure passando como parametro os campos codFiliaErp, codNotaFiscalErp, codFornecedorErp e serie, o Erp precisa gravar em sua tabela que o mesmo foi importado e retirar da View de WMS_NOTAFISCALENTRADA.**

``` 
CREATE procedure [dbo].[sp_RetornoImpEntrada] 
@codFiliaErp varchar(20), @codNotaFiscalErp vatchar(20), @codFornecedorErp varchar(20), @serie int as

begin
  update NOTAFISCALENTRADA SET WMS = 1 
  WHERE 
	codFilialERP = @codFiliaErp and 
	codNotaFiscalErp = @codNotaFiscalErp and 
	codFornecedorErp = @codFornecedorErp and
  serie = @serie
end
```
<br /><br />
**Após realizar a importação do movimento de saida o Wms ira executar uma stored procedure passando como parametro os campos codFiliaErp e codPedidoErp o Erp precisa gravar em sua tabela que o mesmo foi importado e retirar da View de WMS_PEDIDOSCAB.**

``` 
CREATE procedure [dbo].[sp_RetornoImpPedido] 
@codFiliaErp varchar(20), @codPedidoErp vatchar(20) as

begin
  update PEDIDO SET WMS = 1 
  WHERE 
	codFilialERP = @codFiliaErp and 
	codPedidoErp = @codPedidoErp
end
```
<br /><br />
> ### Retorno após a exclusão de movimentos

> Após a exclusão de um movimento o Wms precisa retornar para o Erp que o movimento especifico foi excluido, esse retorno deve ocorrer por meio de uma stored procedure contendo os parametros necessarios para validação, uma vez executado o processo corretamente o movimento excluido deve retornar para a View.

**Após realizar a exclusão do movimento de entrada o Wms ira executar uma stored procedure passando como parametro os campos codFiliaErp, codNotaFiscalErp, codFornecedorErp e serie, o Erp precisa gravar em sua tabela que o mesmo esta disponivel e apresentar o movimento na view WMS_NOTAFISCALENTRADA.**

``` 
CREATE procedure [dbo].[sp_RetornoLiberaEntrada] 
@codFiliaErp varchar(20), @codNotaFiscalErp vatchar(20), @codFornecedorErp varchar(20), @serie int as

begin
  update NOTAFISCALENTRADA SET WMS = 0 
  WHERE 
	codFilialERP = @codFiliaErp and 
	codNotaFiscalErp = @codNotaFiscalErp and 
	codFornecedorErp = @codFornecedorErp and
  	serie = @serie
end
```
<br /><br />
**Após realizar a exclusão do movimento de saida o Wms ira executar uma stored procedure passando como parametro os campos codFiliaErp e codPedidoErp o Erp precisa gravar em sua tabela que o mesmo foi esta disponivel e apresentar o movimento na View WMS_PEDIDOSCAB.**

``` 
CREATE procedure [dbo].[sp_RetornoLiberaPedido] 
@codFiliaErp varchar(20), @codPedidoErp vatchar(20) as

begin
  update PEDIDO SET WMS = 0
  WHERE 
	codFilialERP = @codFiliaErp and 
	codPedidoErp = @codPedidoErp
end
```
<br /><br />

> ### Retorno após a finalização de movimentos

> Após a finalização de um movimento o Wms precisa retornar para o Erp que o movimento especifico ja foi finalizado, esse retorno deve ocorrer por meio de uma stored procedure contendo os parametros necessarios para validação, uma vez executado o processo corretamente o Erp precisa realizar as alterações necessarias para que o fluxo de seu processo ocorra normalmente.

**Após realizar a finalização do movimento de entrada o Wms ira executar uma stored procedure passando como parametro os campos codFiliaErp, codNotaFiscalErp, codFornecedorErp e serie, o Erp precisa gravar em sua tabela os dados retornados referentes ao cabeçalho e itens das notas fiscais.** <br />

**OBS: Os dados citados abaixo são somente para orientação eles devem ser ajustados para a realidade do Erp.** <br />

``` 
CREATE procedure [dbo].[sp_RetornoExpEntrada] 
@codFiliaErp varchar(20), @codNotaFiscalErp vatchar(20), @codFornecedorErp varchar(20), @serie int, @dataFimConferencia datetime as

begin
  update NOTAFISCALENTRADA SET DataFimConferencia = '20220901 00:00:00' 
  WHERE 
	codFilialERP = @codFiliaErp and 
	codNotaFiscalErp = @codNotaFiscalErp and 
	codFornecedorErp = @codFornecedorErp and
  	serie = @serie
end
```
<br />

``` 
CREATE procedure [dbo].[sp_RetornoExpEntradaItem] 
@codFiliaErp varchar(20), @codNotaFiscalErp vatchar(20), @codFornecedorErp varchar(20), 
@serie int, @codProdutoErp = varchar(20), @qtdRecebida = numeric(10,4),
@codFuncConf = varchar(20), @dtConferencia = datetime
as

Declare ItensEntrada Cursor for
  Select codProdutoErp, qtdRecebida, codFuncConf, dtConferencia
    from ItensNotaFiscalEntrada
   where 
   	codFiliaErp = @codFiliaErp and 
	codNotaFiscalErp = @codNotaFiscalErp and 
	codFornecedorErp = @codFornecedorErp and 
	serie = @serie
Open ItensEntrada
fetch next from ItensEntrada into @codProdutoErp, @qtdRecebida, @codFuncConf, @dtConferencia
while @@Fetch_Status = 0
begin
  Update ItensNotaFiscalEntrada set
    qtdRecebida = @qtdRecebida,
    codFuncConf = @codFuncConf,
    dtConferencia = @dtConferencia
  where codProdutoErp = @codProdutoErp
end
```

<br /><br />


**Após realizar a finalização do movimento de saida o Wms ira executar uma stored procedure passando como parametro os campos codFiliaErp e codPedidoErp, o Erp precisa gravar em sua tabela os dados retornados referentes ao cabeçalho e itens dos pedidos.** <br />

**OBS: Os dados citados abaixo são somente para orientação eles devem ser ajustados para a realidade do Erp.** <br />

``` 
CREATE procedure [dbo].[sp_RetornoExpPedido] 
@codFiliaErp varchar(20), @codPedidoErp vatchar(20), @dataFimConferencia datetime, @dataFimSeparacao datetime as

begin
  update NOTAFISCALENTRADA SET 
  	DataFimConferencia = @dataFimConferencia,
	DataFimConferencia = @dataFimSeparacao 
  WHERE 
	codFilialERP = @codFiliaErp and 
	codPedidoErp = @codPedidoErp
end
```
<br />

``` 
CREATE procedure [dbo].[sp_RetornoExpEntradaItem] 
@codFiliaErp varchar(20), @codPedidoErp vatchar(20), @codProdutoErp = varchar(20), @item = varchar(5), @qtdSeparada = numeric(10,4), @qtdConferida = numeric(10,4),
@codFuncConf = varchar(20), @codFuncSep = varchar(20), @dtFimConferencia = datetime, @dtFimSeparacao = datetime
as

Declare ItensPedido Cursor for
  Select codProdutoErp, qtdSeparada, qtdConferida, codFuncConf, codFuncSep, dtFimConferencia, dtFimSeparacao, item
    from ItensPedido
   where 
   	codFiliaErp = @codFiliaErp and 
	codPedidoErp = @codPedidoErp
Open ItensPedido
fetch next from ItensPedido into @codProdutoErp, @qtdSeparada, @qtdConferida, @codFuncConf, @codFuncSep, @dtFimConferencia, @dtFimSeparacao, @item
while @@Fetch_Status = 0
begin
  Update ItensPedido set
    qtdSeparada = @qtdSeparada,
    qtdConferida = @qtdConferida,
    codFuncConf = @codFuncConf,
    codFuncSep = @codFuncSep,
    dtFimConferencia = @dtFimConferencia,
    dtFimSeparacao = @dtFimSeparacao
  where 
  	codProdutoErp = @codProdutoErp and
	item = @item
end
```

<br /><br />
