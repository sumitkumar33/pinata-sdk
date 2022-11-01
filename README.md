
## Laravel Pinata API Provider

This is a Laravel/Lumen provider for interacting with [Pinata](https://pinata.cloud/) API. 

## Note: Special thanks to Daniel Isac (danielcrt) for providing package.

### Install

  

Require this package with composer using the following command:

  

```bash
composer require desnake/pinata-laravel-v9
```

### Installation

Add your API credentials to ```pinata``` array in the ```config/services.php``` config file as follows:

```php
return [

    ...

    'pinata' => [

        'api_key' => env('PINATA_API_KEY'),
        'secret_key' => env('PINATA_API_SECRET')
    ]
]
```

#### Laravel

Add the service provider to the ```providers``` array in the ```config/app.php``` config file as follows:

```php
'providers' => [

    ...

    \Pinata\Providers\PinataServiceProvider::class,
]
```

#### Lumen

Add the following snippet to the ```bootstrap/app.php``` file under the providers section as follows:

```php

$app->configure('services');
$app->register(Pinata\Providers\PinataServiceProvider::class);

```

### Usage
  
Pin a File to IPFS

```php
  use Pinata\Facades\Pinata;

  $file_path = '';

  $response = Pinata::pinFileToIPFS($file_path);
```  
  
Pin a JSON to IPFS

```php
  use Pinata\Facades\Pinata;

  $json = [];

  $response = Pinata::pinJSONToIPFS($json);
```  


Unpin

```php
  use Pinata\Facades\Pinata;

  $ipfs_hash = '';

  $response = Pinata::removePinFromIPFS($ipfs_hash);
```  

For more details about request parameters and responses please visit the official documentation: [https://docs.pinata.cloud](https://docs.pinata.cloud)

### Available methods

  
* addHashToPinQueue

* pinFileToIPFS

* pinHashToIPFS

* pinJobs

* pinJSONToIPFS

* removePinFromIPFS

* userPinnedDataTotal

* userPinList
