# vault-avalanche-controller

## Install

`npm install --save @getsafle/vault-avalanche-controller`

## Initialize the Avalanche Controller class

```
const controller = require('@getsafle/vault-avalanche-controller');

const avalancheController = new controller({
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
const signedTx = await avalancheController.signTransaction(avalancheTx, _fromAddress);
```

### Sign a message

```
const signedMsg = await avalancheController.signMessage(msgParams);
```

### Sign Typed Data (EIP-712)

```
const signedData = await avalancheController.signTypedMessage (msgParams);
```
