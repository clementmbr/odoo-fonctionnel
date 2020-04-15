# Modos de Pagamento

Um _Modo de Pagamento_ é um tipo de objeto Odoo adicionado às _Faturas_ pelo módulo OCA [account\_payment\_mode](https://github.com/OCA/bank-payment/tree/12.0/account_payment_mode) que **permite rastrear "como" são realizados os pagamentos** \(de um cliente ou para um fornecedor\).

![](../.gitbook/assets/image%20%2828%29.png)

Junto com o módulo [account\_payment\_partner](https://github.com/OCA/bank-payment/tree/12.0/account_payment_partner) ele permite associar cada _Contato_ a um "Modo de Pagamento do Cliente" e/ou "Modo de Pagamento do Fornecedor", que permite preencher esse campo "Modo de Pagamento" das _Faturas_ associadas ao _Contato_ automaticamente, além de poder **realizar ações grupadas em todas as faturas com o mesmo** _**Modo de Pagamento**_ :

![](../.gitbook/assets/image%20%2839%29.png)

É possível adicionar ou editar Modos de Pagamento no menu _Faturamento &gt; Configuração &gt; Payment Modes_ :

![](../.gitbook/assets/image%20%2846%29.png)



