# jade

![](https://www.etclabs.org/dist/resources/images/v2/logo-top.png)
Supported by [ETC Labs](https://www.etclabs.org/)

Jade-*
1. written in any language
2. exposes json rpc with service discovery
3. can be run via docker
4. follows pristine
5. Includes github pages / generated docs
6. not dependent on each other (directly).
7. MUST expose methods via json rpc server

Jade-*-client-{language}
1. Library that implements a client to use the json rpc service.
2. one per language generated
3. packages are published to package manager based on language of implementation

Jade-*-ui
1. UI tailored to dapp users or developers that is built ontop of the json rpc
2. packaged as web application
3. web application electron wrapper



The first Jade-* projects:
1. Jade-signer
2. Jade-evm
  3.  Jade-service-runner (name tentative)

Jade-signer
1.  lightweight account management that doesn't require ethereum rpc.
2. Ideally is agnostic to the network onwhich the account would be used...
3. pretty much only has: account crud, signTransaction, signMessage
4.

Jade-service-runner
1. runs any jade-*  service on any platform
2. provides a 'meta rpc' or rpc gateway for any services being.
