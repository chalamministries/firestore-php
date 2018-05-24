# Firestore SDK for PHP without gRPC

[![Current version](https://img.shields.io/packagist/v/kreait/firebase-php.svg)](https://packagist.org/packages/kreait/firebase-php)
[![Build Status](https://img.shields.io/circleci/project/morrislaptop/vue-web3.svg)](https://circleci.com/gh/morrislaptop/vue-web3)

## @todo

- [x] Get
- [x] Set
- [ ] Delete
- [ ] Add
- [ ] Transactions (beginTransaction, commit, rollback)
- [ ] Reference value support
- [ ] Batch Get
- [ ] List Documents
- [ ] Query
- [ ] Order
- [ ] Limit
- [ ] Indexes (create, delete, list, get)

## Installation

The recommended way to install is with Composer.

    composer require morrislaptop/firestore-php

## Usage

```php

use Morrislaptop\Firestore\Factory;
use Kreait\Firebase\ServiceAccount;

// This assumes that you have placed the Firebase credentials in the same directory
// as this PHP file.
$serviceAccount = ServiceAccount::fromJsonFile(__DIR__ . '/google-service-account.json');

$firebase = (new Factory)
    ->withServiceAccount($serviceAccount)
    ->create();

$firestore = $firebase->getFirestore();

$collection = self::$firestore->getCollection('users');
$user = $collection->getDocument('123456');

// Save a document
$user->set(['name' => 'morrislaptop', 'role' => 'developer']);

// Get a document
$snap = $user->getSnapshot();
echo $snap['name']; // morrislaptop

```
