---
layout: default
---
# MarkethubBundle

Integração de SDKs para Marketplaces com aplicações Symfony

## Marketplaces disponíveis

- B2W
- Cnova
- Zattini

## Requisitos

* PHP >= *5.6*
* [Symfony](http://symfony.com/) >= *2.8*
* [curl extension](http://php.net/manual/en/intro.curl.php)

## Licença

Este componente está sob a [licença MIT](https://github.com/gpupo/common-sdk/blob/master/LICENSE)

## Indicadores de qualidade

[![Build Status](https://secure.travis-ci.org/gpupo/MarkethubBundle.png?branch=master)](http://travis-ci.org/gpupo/MarkethubBundle)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/gpupo/MarkethubBundle/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/gpupo/MarkethubBundle/?branch=master)
[![SensioLabsInsight](https://insight.sensiolabs.com/projects/e4572276-e535-43b3-88ff-0bbc3cdcff3f/small.png)](https://insight.sensiolabs.com/projects/e4572276-e535-43b3-88ff-0bbc3cdcff3f)

## Agradecimentos

* A todos os que [contribuiram com patchs](https://github.com/gpupo/MarkethubBundle/contributors)
* Aos que [fizeram sugestões importantes](https://github.com/gpupo/MarkethubBundle/issues)
* A todos os desenvolvedores que criaram as [bibliotecas utilizadas neste componente](https://github.com/gpupo/MarkethubBundle/blob/master/Resources/doc/libraries-list.md)


 _- [Gilmar Pupo](http://www.g1mr.com/)_

---

## Instalação

Usando [Composer](http://getcomposer.com):

    composer require gpupo/markethub-bundle:~1.3

Registre o bundle no Kernel:

```php
<?php
// app/AppKernel.php
// ...
class AppKernel extends Kernel
{
    public function registerBundles()
    {
        return array(
            //...
            new Gpupo\Bundle\MarkethubBundle\MarkethubBundle(),
        );
    }
    // ...
}
```

## Setup

app/config/parameters.yml :

```yaml
parameters:
    #...
    markethub_submarino_api_token: 'MyApiToken'
```

app/config/config_dev.yml:

```yaml
markethub:
    submarino:
        api_token: 'MySandbox@ApiToken'
```

app/config/config_prod.yml:

```yaml
markethub:
    submarino:
        api_token: %markethub_submarino_api_token%
        api_version: 'api'
```

## Serviços disponíveis

(considere ``%nome_marketplace%`` como valor a ser preenchido)

- markethub.%nome_marketplace%.factory
- markethub.%nome_marketplace%.client
- markethub.%nome_marketplace%.product.manager
- markethub.%nome_marketplace%.product.sku.manager
- markethub.%nome_marketplace%.order.manager

## Contrutores disponíveis

- createProduct
- createSku
- createOrder

Uso:

```php
<?php
///...
    $this->get('markethub.%nome_marketplace%.factory')->createProduct($data);
```

## Exemplo de uso: B2W Marketplace

É utilizando gpupo/submarino-sdk, com a diferença da disponibilidade de
services no escopo onde Container está presente.

### Exemplos de manutenção de Produtos

```php
<?php
///...

// Acesso a lista de produtos cadastrados, utilizando SF2 service:
$produtosCadastrados = $this->get('markethub.submarino.order.manager')->fetch(); // Collection de Objetos Product

// Acesso a informações de um produto cadastrado e com identificador conhecido:
$produto = $this->get('markethub.submarino.product.manager')->findById(9)); // Objeto Produto

echo $product->getName(); // Acesso ao nome do produto #9



// Criação de um produto:
$data = [];
$product = $this->get('markethub.submarino.factory')->createProduct($data);

foreach ($data['sku'] as $item) {
    $sku = $this->get('markethub.submarino.factory')->createSku($item);
    $product->getSku()->add($sku);
}

$this->get('markethub.submarino.product.manager')->save($product);

//Adicionando SKU ao produto:
$skuData = [];
$novoSku = $this->get('markethub.submarino.factory')->createSku($skuData);
$product->getSku()->add($novoSku);
$this->get('markethub.submarino.product.manager')->save($product);

```

## Desenvolvimento

    git clone --depth=1  git@github.com:gpupo/MarkethubBundle.git

    cd MarkethubBundle;

    ant;
