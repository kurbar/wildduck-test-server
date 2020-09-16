# Wildduck test server as a package

This is a helper package for writing tests that interact with the Wildduck API or other parts in some way. It exposes a test server script via the vendor/node_modules bin directory to
easily link it with your NPM or Compose flows.

## Installation

Via NPM:
```bash
npm install --save-dev kurbar/wildduck-test-server
```

Via Composer:
```bash
composer require --dev kurbar/wildduck-test-server
```

## Usage

It can be used in different ways.

1) As a standalone script
NPM:
```bash
node_modules/bin/wildduck-test-server start|stop
```

Composer:
```bash
vendor/bin/wildduck-test-server start|stop
```

2) Or tied into your package.json/composer.json flow
NPM:
```json
{
  "scripts": {
    "test:wd": "wildduck-test-server start && npm test && wildduck-test-server stop"
  }
}
```

Composer (Note: it is recommended to disable process timeout since on first start it might take a while and Composer will time out executing):
```json
{
  "scripts": {
    "test": [
      "Composer\\Config::disableProcessTimeout",
      "wildduck-test-server start",
      "phpunit",
      "wildduck-test-server stop"
    ]
  }
}
```
