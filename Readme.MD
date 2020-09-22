Leadwallet API Documentation
=============================

Note that URLs should be prefixed with **/api/v1/wallet**. For example, to create a wallet, URL should be in the form **/api/v1/wallet/:route** where *route* could be any of the following:

| Route | Method | Description                       | Parameters |
|-------|--------|-----------------------------------|------------|
|create | POST   |Generates a wallet.         |<table><tr><th>Parameter</th><th>In</th><th>Description</th></tr><tr><td>recoveryPhrase</td><td>body</td><td>An array of phrases from which to generate wallet's private key</td></tr></table>                        |
|retrieve| GET   |Returns a wallet using a key pair. |<table><tr><th>Parameter</th><th>In</th><th>Description</th></tr><tr><td>Authorization</td><td>headers</td><td>A bearer token that contains the key pair from which a private key would be gotten.</td></tr></table> |
|import  | POST  |Imports or recovers a wallet.      | <table><tr><th>Parameter</th><th>In</th><th>Description</th></tr><tr><td>recoveryPhrase</td><td>body</td><td>An array of phrases. A private key is generated from this and a wallet with a matching key is returned.</td></tr></table> |