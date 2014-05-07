Cordova Crypto Ecc Plugin
======================

This plugin was forked from https://github.com/aerogear/aerogear-crypto-cordova and it is intend to support ecc ( http://de.wikipedia.org/wiki/Elliptic_Curve_Cryptography) for iOS and Android.

It relies on the "curve25519xsalsa20poly1305" curve and aimed to have a simple interface and compatibility between iOS and Android.

## Current development status
Work in Progress, use at your own risk!

## Changes between aerogear-crypto-cordova
### General
- removed jQuery dependency
- changed cordova.exec methods

### iOS
- removed coocoapods dependency
- added static lib from https://github.com/aerogear/aerogear-crypto-ios
- added additional headers from https://github.com/mochtu/libsodium-ios
 
### Android
- added jnacl from https://github.com/DATAWERK/jnacl (initial created by Neil Alexander)

## API

### getRandomValue
```js
// default with 16 byte
cordova.exec(function(result){console.log(result)}, null, 'cryptoEcc', 'getRandomValue', [{}]);

// with custom byte lenght
cordova.exec(function(result){console.log(result)}, null, 'cryptoEcc', 'getRandomValue', [{length:24}]);
```

### deriveKey
```js
var options = {
  password:'test', 
  salt:'45c947d6230f6853381b2e8a9e30baa1'
};
cordova.exec(function(result){console.log(result)}, null, 'cryptoEcc', 'deriveKey', [options]);
```

### validateKey
```js
var options = {
  password:'test', 
  encryptedPassword:'f18683cb5394962fc1c301fd58f60a6575bcb26c3726f2d397ebe1ade99c495f',
  salt:'45c947d6230f6853381b2e8a9e30baa1'
};
cordova.exec(function(result){console.log(result)}, null, 'cryptoEcc', 'validateKey', [options]);
```

### generateKeyPair
```js
cordova.exec(function(result){console.log(result)}, null, 'cryptoEcc', 'generateKeyPair', []);
```

### encrypt
```js
var options = {
  publicKey:'3509f100e0490f5bd809ab5f7ebe8b1dc159a41dd7b434c9e7a9ff8513b3ea48',
  privateKey:'3e1acea6ab442ce92f3f92fa815199f5ce0ecdaaff91d588ac35d58f63d105b5',
  nonce:'69696EE955B62B73CD62BDA875FC73D68219E0036B7A0B37', 
  data:'test'
};
cordova.exec(function(result){console.log(result)}, null, 'cryptoEcc', 'encrypt', [options]);
```

### decrypt
```js
var options = {
  publicKey:'3509f100e0490f5bd809ab5f7ebe8b1dc159a41dd7b434c9e7a9ff8513b3ea48',
  privateKey:'3e1acea6ab442ce92f3f92fa815199f5ce0ecdaaff91d588ac35d58f63d105b5',
  nonce:'69696EE955B62B73CD62BDA875FC73D68219E0036B7A0B37', 
  data:'31fd6028233b3043e2985c57b788cce971533408'
};
cordova.exec(function(result){console.log(result)}, null, 'cryptoEcc', 'decrypt', [options]);
```




