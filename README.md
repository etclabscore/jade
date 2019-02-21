# jade

![](https://www.etclabs.org/dist/resources/images/v2/logo-top.png)
Supported by [ETC Labs](https://www.etclabs.org/)

All Projects:
1. follow pristine

Jade-\*
1. No code, just readme and links to all the goods. This is the first thing you want a google of Jade Etc to see

Jade-service-runner
1. runs any jade-\*  service on any platform
1. provides a 'meta rpc' or rpc gateway for any services being.

Jade-ui-electron-wrapper
1. takes any jade-\*-ui and wraps it in a platform-specific application wrapper such as electron, cordova, etc.

Jade-*-{language}
1. written in `language`
1. Includes github pages / generated docs
1. not dependent on each other (directly). <-- Nice to have?
1. Where possible, should provide ffi bindings.

Jade-\*-rpc
1. No code - readme indexing the various language implementations of RPC servers. Again, first place you want peoiple to see about RPC server for this project. 
1.Should define the OpenRPC schema file.

Jade-\*-rpc-{language}
1. MUST expose functionality provided by Jade-*-{language} via json rpc server
1. exposes json rpc with service discovery

Jade-\*-client-{language}
1. Library that implements a client to use the json rpc service.
1. one per language generated
1. packages are published to package manager based on language of implementation

Jade-\*-ui
1. UI tailored to dapp users or developers that is built ontop of the json rpc
1. packaged as web application
1. uses `Jade-*-client`s  

Jade-ui-{platform}-wrapper 
**note**: `platform` here is one of: 'electron', 'mobile'
1. Anything that takes the web based ui exported by jade-\*-ui and produces a platform specific wrapper for it
1. web application electron wrapper

Jade-service-runner
1. runs any jade-\*  service on any platform
2. provides a 'meta rpc' or rpc gateway for any services being.


The first Jade-* projects:
- Jade-signer
  - Jade-signer-rs
  - Jade-signer-js
  - Jade-signer-rpc-rs
  - Jade-signer-rpc-js
  - Jade-signer-client-rs
  - Jade-signer-client-js
  - Jade-signer-ui
- Jade-evm
  - Jade-evm-rs
  - Jade-evm-rpc-rs
  - Jade-evm-ui ??
- Jade-ui-electron-wrapper
- Jade-service-runner     

Jade-signer
1. lightweight account management that doesn't require ethereum rpc.
1. Ideally is agnostic to the network onwhich the account would be used...
1. pretty much only has: account crud, signTransaction, signMessage

Jade-service-runner
1. runs any jade-\*  service on any platform
1. provides a 'meta rpc' or rpc gateway for any services being.
