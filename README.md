### Introduction

This project implements Bitcoin Cash signature algorithm. It is based on [bitcoinj](https://github.com/bitcoinj/bitcoinj) and forked from [PR-1422](https://github.com/bitcoinj/bitcoinj/pull/1422).

### Installation

Clone the source code and run

```
mvn install -Dmaven.test.skip=true
```

Be sure you have already installed JCE Unlimited Strength Jurisdiction Policy Files for your JDK version. For more information, please see [this](https://stackoverflow.com/questions/6481627/java-security-illegal-key-size-or-default-parameters)

### FAQ

## How to sign Bitcoin Cash transaciton
```
// Sign an input whose value is 5 BCCs
Sha256Hash hash = tx.hashForSignature(i, scriptPubKey, Transaction.SigHash.ALL, false, 500000000L);
ECKey.ECDSASignature sig = ecKey.sign(hash);

// the last boolean 'true' argument indicates it uses replay-protected signature hash for BCC
TransactionSignature signature = new TransactionSignature(sig, Transaction.SigHash.ALL, false, true);
Script inputScript = ScriptBuilder.createInputScript(signature, ecKey);
```