---
layout: default
---



# MarkethubBundle

Integração de SDKs para Marketplaces com aplicações Symfony

## Marketplaces disponíveis

- B2W
- Cnova
- Netshoes









## Indicadores de qualidade

[![Build Status](https://secure.travis-ci.org/gpupo/MarkethubBundle.png?branch=master)](http://travis-ci.org/gpupo/MarkethubBundle)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/gpupo/MarkethubBundle/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/gpupo/MarkethubBundle/?branch=master)
[![SensioLabsInsight](https://insight.sensiolabs.com/projects/e4572276-e535-43b3-88ff-0bbc3cdcff3f/small.png)](https://insight.sensiolabs.com/projects/e4572276-e535-43b3-88ff-0bbc3cdcff3f)



---

## Agradecimentos

* A todos os que [contribuiram com patchs](https://github.com/gpupo/MarkethubBundle/contributors);
* Aos que [fizeram sugestões importantes](https://github.com/gpupo/MarkethubBundle/issues);
* Aos desenvolvedores que criaram as [bibliotecas utilizadas neste componente](https://github.com/gpupo/MarkethubBundle/blob/master/Resources/doc/libraries-list.md).

 _- [Gilmar Pupo](http://www.g1mr.com/)_




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















---

## Desenvolvimento

    git clone --depth=1  git@github.com:gpupo/MarkethubBundle.git
    cd netshoes-sdk;
    ant;

Personalize a configuração do ``phpunit``:

    cp phpunit.xml.dist phpunit.xml;

Personalize os parâmetros!



*Dica*: Verifique os logs gerados em ``var/log/main.log``









Gpupo\Bundle\MarkethubBundle\Tests\Factory\CnovaFactory


- [x] Falha ao acessar factory inexistente
- [x] Acesso a servicos de sdk 
- [x] Centraliza criacao de objetos 

Gpupo\Bundle\MarkethubBundle\Tests\Factory\NetshoesFactory


- [x] Falha ao acessar factory inexistente
- [ ] Acesso a servicos de sdk 
- [ ] Centraliza criacao de objetos 

Gpupo\Bundle\MarkethubBundle\Tests\Factory\SubmarinoFactory


- [x] Falha ao acessar factory inexistente
- [x] Acesso a servicos de sdk 
- [x] Centraliza criacao de objetos 





## Lista de dependências (libraries)

Name | Version | Description
-----|---------|------------------------------------------------------
codeclimate/php-test-reporter | v0.3.2 | PHP client for reporting test coverage to Code Climate
doctrine/annotations | v1.2.7 | Docblock Annotations Parser
doctrine/cache | v1.6.0 | Caching library offering an object-oriented API for many cache backends
doctrine/collections | v1.3.0 | Collections Abstraction library
doctrine/common | v2.5.3 | Common Library for Doctrine projects
doctrine/inflector | v1.1.0 | Common String Manipulations with regard to casing and singular/plural rules.
doctrine/instantiator | 1.0.5 | A small, lightweight utility to instantiate objects in PHP without invoking their constructors
doctrine/lexer | v1.0.1 | Base library for a lexer that can be used in Top-Down, Recursive Descent Parsers.
gpupo/cache | 1.3.0 | Caching library that implements PSR-6
gpupo/cnova-sdk | 1.3.0 | SDK Não Oficial para integração a partir de aplicações PHP com as APIs da Cnova Marketplace
gpupo/common | 1.6.6 | Common Objects
gpupo/common-sdk | 2.0.11 | Componente de uso comum entre SDKs para integração a partir de aplicações PHP com Restful webservices
gpupo/netshoes-sdk | 1.0.1 | SDK Não Oficial para integração a partir de aplicações PHP com APIs da Netshoes Marketplace
gpupo/submarino-sdk | 2.4.1 | SDK Não Oficial para integração a partir de aplicações PHP com as APIs do Submarino Marketplace
guzzle/guzzle | v3.8.1 | Guzzle is a PHP HTTP client library and framework for building RESTful web service clients
monolog/monolog | 1.19.0 | Sends your logs to files, sockets, inboxes, databases and various web services
myclabs/deep-copy | 1.5.1 | Create deep copies (clones) of your objects
phpdocumentor/reflection-common | 1.0 | Common reflection classes used by phpdocumentor to reflect the code structure
phpdocumentor/reflection-docblock | 3.1.0 | With this component, a library can provide support for annotations via DocBlocks or otherwise retrieve information that is embedded in a DocBlock.
phpdocumentor/type-resolver | 0.2 | 
phpspec/prophecy | v1.6.1 | Highly opinionated mocking framework for PHP 5.3+
phpunit/php-code-coverage | 4.0.0 | Library that provides collection, processing, and rendering functionality for PHP code coverage information.
phpunit/php-file-iterator | 1.4.1 | FilterIterator implementation that filters files based on a list of suffixes.
phpunit/php-text-template | 1.2.1 | Simple template engine.
phpunit/php-timer | 1.0.8 | Utility class for timing
phpunit/php-token-stream | 1.4.8 | Wrapper around PHP's tokenizer extension.
phpunit/phpunit | 5.4.6 | The PHP Unit Testing framework.
phpunit/phpunit-mock-objects | 3.2.3 | Mock Object library for PHPUnit
psr/cache | 1.0.0 | Common interface for caching libraries
psr/log | 1.0.0 | Common interface for logging libraries
satooshi/php-coveralls | v1.0.1 | PHP client library for Coveralls API
sebastian/code-unit-reverse-lookup 1.0.0 | Looks up which function or method a line of code belongs to
sebastian/comparator | 1.2.0 | Provides the functionality to compare PHP values for equality
sebastian/diff | 1.4.1 | Diff implementation
sebastian/environment | 1.3.7 | Provides functionality to handle HHVM/PHP environments
sebastian/exporter | 1.2.2 | Provides the functionality to export PHP variables for visualization
sebastian/global-state | 1.1.1 | Snapshotting of global state
sebastian/object-enumerator | 1.0.0 | Traverses array structures and object graphs to enumerate all referenced objects
sebastian/peek-and-poke | dev-master a8295 | Proxy for accessing non-public attributes and methods of an object
sebastian/recursion-context | 1.0.2 | Provides functionality to recursively process PHP variables
sebastian/resource-operations | 1.0.0 | Provides a list of PHP built-in functions that operate on resources
sebastian/version | 2.0.0 | Library that helps with managing the version number of Git-hosted PHP projects
symfony/config | v3.1.1 | Symfony Config Component
symfony/console | v3.1.1 | Symfony Console Component
symfony/debug | v3.1.1 | Symfony Debug Component
symfony/dependency-injection | v3.1.1 | Symfony DependencyInjection Component
symfony/event-dispatcher | v3.1.1 | Symfony EventDispatcher Component
symfony/filesystem | v3.1.1 | Symfony Filesystem Component
symfony/http-foundation | v3.1.1 | Symfony HttpFoundation Component
symfony/http-kernel | v3.1.1 | Symfony HttpKernel Component
symfony/monolog-bridge | v3.1.1 | Symfony Monolog Bridge
symfony/monolog-bundle | 2.11.1 | Symfony MonologBundle
symfony/phpunit-bridge | v3.1.1 | Symfony PHPUnit Bridge
symfony/polyfill-mbstring | v1.2.0 | Symfony polyfill for the Mbstring extension
symfony/stopwatch | v3.1.1 | Symfony Stopwatch Component
symfony/yaml | v3.1.1 | Symfony Yaml Component
twig/twig | v1.24.1 | Twig, the flexible, fast, and secure template language for PHP
webmozart/assert | 1.0.2 | Assertions to validate method input/output with nice error messages.






