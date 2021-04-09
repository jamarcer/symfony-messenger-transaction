# Symfony Messenger Middleware for Transactional Database connections

This library is based on [Transaction](https://github.com/PcComponentes/transaction).

## Installation

Install via [composer](https://getcomposer.org/)

```shell script
composer require jamarcer/symfony-messenger-transaction
```

## Usage

It is necessary to have a previously created [ElasticApmTracer](https://github.com/zoilomora/elastic-apm-agent-php) instance.

```shell script
apm.tracer:
    class: ZoiloMora\ElasticAPM\ElasticApmTracer
    factory: ['App\Service\ApmService', 'instantiate']
    arguments: ['apm-devel','http://localhost:7200','devel']
```

### Service Container

```shell script
Jamarcer\APM\Symfony\Component\Console\ElasticAPMSubscriber:
    class: Jamarcer\APM\Symfony\Component\Console\ElasticAPMSubscriber
    autoconfigure: true
    arguments:
        $elasticApmTracer: '@apm.tracer'
```
## Development

Prepare the development environment. 

```shell script
make build
```

```shell script
make composer-install
```

Or you can access directly to bash ...
```shell script
make start
```

... and test the library
```shell script
/var/app/vendor/bin/phpunit --configuration /var/app/phpunit.xml.dist 
```

## License
Licensed under the [MIT license](http://opensource.org/licenses/MIT)

Read [LICENSE](LICENSE) for more information
