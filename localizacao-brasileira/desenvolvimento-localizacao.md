---
description: Atualizado em novembro de 2020.
---

# Desenvolvimento da localização

Desde 2009, a [Akretion](https://github.com/akretion) está liderando a [comunidade de desenvolvedores brasileiros](https://github.com/OCA/l10n-brazil/graphs/contributors) que adaptam o software Odoo de maneira livre e colaborativa à complexidade da realidade brasileira.

Tentamos resumir aqui o andamento atual desse imenso trabalho listando :

* 🟢 as funcionalidades **totalmente operacionais**, porém que necessitam uma certa parametrização para ser adaptadas com cada usuário\)
* 🟡 as funcionalidades que **necessitam ainda um pouco de desenvolvimento**, porém já sabemos "como desenvolver", a arquitetura do código atual já está pronta para receber essa funcionalidade.
* 🔴 as funcionalidades que **necessitam ainda muito desenvolvimento**. Mesmo se um trabalho já foi realizado para definir "como teria que ser desenvolvido essa funcionalidade", ainda falta escrever todo o código do módulo.

Todos os módulos citados aqui podem ser baixados e usados livremente a partir do [repositório da localização brasileira](https://github.com/OCA/l10n-brazil) no perfil github da [Odoo Community Association \(OCA\)](https://odoo-community.org/) :

{% embed url="https://github.com/OCA/l10n-brazil" %}

## Fiscalidade

**Módulo :** [l10n\_br\_fiscal](https://github.com/OCA/l10n-brazil/tree/12.0/l10n_br_fiscal) \| **Liderado por :** [Akretion](https://github.com/akretion)

### Cálculo dos Impostos

* 🟢 Para todos os tipos de empresas ! Simples Nacional e Normais.
* 🟢 Registro de substituições tributárias

O coração da complexidade fiscal brasileira necessário para toda a gestão dos documentos fiscais e da contabilidade ! CNAE, Perfil Fiscal, NCM, CEST, Desoneração do ICMS, Crédito do PIS/COFINS... Não falta nenhuma opção para o cálculo exato dos impostos brasileiros.

### Conciliação Bancária

* 🟢 Importação automática dos extratos bancários no Odoo clicando num botão 2 vezes por semana.
* 🟢 Conciliação automática entre os extratos e os lançamentos contábeis no Odoo. Essa funcionalidade da conciliação automática é operacional, porém necessita sempre muito trabalho de parametrização para ser adaptada com cada usuário.
* 🔴 Sincronização em tempo real dos extratos bancários com Odoo. Essa funcionalidade envolve questões de segurança extremas que demandaria um investimento muito alto.

### Documentos fiscais

* 🟢 Arquitetura pensada para receber teoricamente qualquer tipo de campo fiscal para a construção de qualquer documento fiscal
* 🟢 Emissão e Importação das NF-e de produtos
* 🟢 Emissão e Importação das NF-e de remessa
* 🟡 50% das NF-e de serviço
* 🟡 80% dos outros documentos fiscais \(MDFE, CTE...\)

### Integração dos campos fiscais brasileiros com os outros módulos Odoo

* 🟢 Integração com os módulos de venda, compra, estoque e manufatura.
* 🟡 A integração com os outros módulos ainda não está realizada, porém a arquitetura do módulo `l10n_br_fiscal` permite a realização dessas futuras integrações muito facilmente.

## Pagamentos

### Boleto e CNAB de recebimento





## Relatórios contábeis

## Folhas de Pagamento

## Campos especiais

## Cálculo dos custos de entrega



