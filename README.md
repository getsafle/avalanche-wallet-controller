# vault-avalanche-controller<code><a href="https://www.docker.com/" target="_blank"><img height="50" src="https://assets-global.website-files.com/632993e1d1acbfa5635afd0b/6351544c2e41652a8bf6a2af_Logo%20Full%20Red.svg"></a></code>

[![npm version](https://badge.fury.io/js/@getsafle%2Fvault-avalanche-controller.svg)](https://badge.fury.io/js/@getsafle%2Fvault-avalanche-controller) <img alt="Static Badge" src="https://img.shields.io/badge/License-MIT-green">   [![Discussions][discussions-badge]][discussions-link]
 <img alt="Static Badge" src="https://img.shields.io/badge/avalanche_controller-documentation-purple">   

A Module written in javascript for managing various keyrings of Avalanche accounts, encrypting them, and using them.

- [Installation](#installation)
- [Initialize the Avalanche Controller class](#initialize-the-avalanche-controller-class)
- [Methods](#methods)
  - [Generate Keyring with 1 account and encrypt](#generate-keyring-with-1-account-and-encrypt)
  - [Restore a keyring with the first account using a mnemonic](#restore-a-keyring-with-the-first-account-using-a-mnemonic)
  - [Add a new account to the keyring object](#add-a-new-account-to-the-keyring-object)
  - [Export the private key of an address present in the keyring](#export-the-private-key-of-an-address-present-in-the-keyring)
  - [Sign a transaction](#sign-a-transaction)
  - [Sign a message](#sign-a-message)
  - [Get balance](#get-balance)


## Installation

`npm install --save @getsafle/vault-avalanche-controller`

## Initialize the Avalanche Controller class

```
const { KeyringController, getBalance } = require('@getsafle/vault-avalanche-controller');

const avalancheController = new KeyringController({
  encryptor: {
    // An optional object for defining encryption schemes:
    // Defaults to Browser-native SubtleCrypto.
    encrypt(password, object) {
      return new Promise('encrypted!');
    },
    decrypt(password, encryptedString) {
      return new Promise({ foo: 'bar' });
    },
  },
});
```

## Methods

### Generate Keyring with 1 account and encrypt

```
const keyringState = await avalancheController.createNewVaultAndKeychain(password);
```

### Restore a keyring with the first account using a mnemonic

```
const keyringState = await avalancheController.createNewVaultAndRestore(password, mnemonic);
```

### Add a new account to the keyring object

```
const keyringState = await avalancheController.addNewAccount(keyringObject);
```

### Export the private key of an address present in the keyring

```
const privateKey = await avalancheController.exportAccount(address);
```

### Sign a transaction

```
const signedTx = await avalancheController.signTransaction(rawTx, privateKey);
```

### Sign a message

```
const signedMsg = await avalancheController.signMessage(msgParams);
```

### Sign a message

```
const signedObj = await avalancheController.sign(msgParams, pvtKey, web3Obj);
```

### Sign Typed Data (EIP-712)

```
const signedData = await avalancheController.signTypedMessage(msgParams);
```

### Get balance

```
const balance = await getBalance(address, web3);
```
[discussions-badge]: https://img.shields.io/badge/Code_Quality-passing-rgba
[discussions-link]: https://github.com/getsafle/vault-avalanche-controller/actions