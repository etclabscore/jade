# jade

![](https://www.etclabs.org/dist/resources/images/v2/logo-top.png)
Supported by [ETC Labs](https://www.etclabs.org/)

All Projects:
1. follow pristine

Jade-*
1. No code, just readme and links to all the goods. This is the first thing you want a google of Jade Etc to see

Jade-*-{language}
1. written in `language`
2. Includes github pages / generated docs
3. not dependent on each other (directly). <-- Nice to have?

Jade-*-rpc
1. No code - readme indexing the various language implementations of RPC servers. Again, first place you want peoiple to see about RPC server for this project. 
2.Should define the OpenRPC schema file.

Jade-*-rpc-{language}
1. MUST expose functionality provided by Jade-*-{language} via json rpc server
2. exposes json rpc with service discovery

Jade-*-client-{language}
1. Library that implements a client to use the json rpc service.
2. one per language generated
3. packages are published to package manager based on language of implementation

Jade-*-ui
1. UI tailored to dapp users or developers that is built ontop of the json rpc
2. packaged as web application
3. web application electron wrapper
4. uses `Jade-*-client`s 
5. 

Jade-ui-{platform}-wrapper 
**note**: `platform` here is one of: 'electron', 'mobile'
1. Anything that takes the web based ui exported by jade-*-ui and produces a platform specific wrapper for it

The first Jade-* projects:
- Jade-signer
  - Jade-signer-rs
    - Jade-signer-rpc-rs
    - Jade-signer-client-rs
  - Jade-signer-js
    - Jade-signer-rpc-js
    - Jade-signer-client-js
  - Jade-signer-ui
      
2. Jade-evm
  3.  Jade-service-runner (name tentative)

Jade-signer
1. lightweight account management that doesn't require ethereum rpc.
2. Ideally is agnostic to the network onwhich the account would be used...
3. pretty much only has: account crud, signTransaction, signMessage
4.

Jade-service-runner
1. runs any jade-*  service on any platform
2. provides a 'meta rpc' or rpc gateway for any services being.
