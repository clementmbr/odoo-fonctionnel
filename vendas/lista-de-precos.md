# Lista de Preços de venda

As listas de preços de venda permitem vender um produto com preços diferentes dependendo do cliente \(para **promoções limitadas no tempo**, promoções para **varejistas** ou simplesmente para vendas em **moedas diferentes**\).

{% embed url="https://www.odoo.com/documentation/user/12.0/sales/products\_prices/prices/pricing.html" %}

## Como modificar o preço de venda segundo o cliente ?

Primeiro precisa ativar a opção "_Múltiplos Preços de Venda por Produto_" e "_Múltiplos preços por produto_" no menu _Vendas_ &gt; _Configuração_ &gt; _Configurações_ &gt; _Preços_.

![](../.gitbook/assets/image%20%282%29.png)

Isso faz aparecer uma lista de preços na aba Vendas de um produto \(que deve ter a opção "_Pode ser Vendido_" ativada, claro\) :

![](../.gitbook/assets/image%20%2814%29.png)

Com essa lista de preços preenchida, ao criar uma nova cotação desse produto para um cliente que faz parte de um desses grupos de clientes, o **preço sugerido será automaticamente definido seguindo essa tabela** \(pensar em verificar se a cotação se encaixa bem nas condições de quantidade Mínima e datas de validades das promoções da tabela\).

{% hint style="danger" %}
Esses "grupos de clientes" são \(lamentavelmente\) denominadas como "_**Lista de Preço**_" em Odoo.
{% endhint %}

É possível escolher o "grupo de um cliente" editando o campo "Lista de Preço" na aba "Compras e Vendas" da ficha do cliente :

![](../.gitbook/assets/image%20%2811%29.png)

Isso vai preencher automaticamente o campo "Lista de Preço" de uma nova cotação para esse cliente \(e vai sugerir o preço da cotação relativo a ambos essa "Lista de Preço" e o produto vendido\) :

![](../.gitbook/assets/image%20%2819%29%20%281%29.png)

{% hint style="info" %}
Mesmo se esse campo "Lista de Preço" e "Preço Unitário" foram preenchidos automaticamente, sempre **é possível modificar eles manualmente**.
{% endhint %}

## Definição dos grupos de clientes

Podemos definir esses "grupos de clientes" mal denominadas de "Lista de preços" clicando embaixo da opção "_Múltiplos Preços de Venda por Produto_" nas _Configurações_ do aplicativo de Vendas :

![](../.gitbook/assets/image%20%286%29.png)

Na prática, uma "_Lista de preço_" é apenas **apenas um nome para diferenciar determinados clientes ou cotações** de outros.

Caso a opção _Multi-Moedas_ estiver ativada nas configurações do modulo _Faturamento_, **esse nome vai definir também a** _**Moeda**_ **de cada "preço de venda"** na aba _Vendas_ dos produtos \(e respectivamente a _Moeda_ das cotações usando essa "_Lista de preço_"\) :

![](../.gitbook/assets/image%20%2829%29.png)

Enfim, cada "Lista de preço" vai ter um campo "_Grupo de países_" que, se for definido, permite preencher automaticamente a "_Lista de preço_" dos novos contatos criados com um país desse grupo :

![](../.gitbook/assets/image%20%2810%29.png)

