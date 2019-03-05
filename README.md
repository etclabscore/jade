# The Jade Specification

![](https://www.etclabs.org/dist/resources/images/v2/logo-top.png)
Supported by [ETC Labs](https://www.etclabs.org/)

### Table of Contents
<!-- TOC depthFrom:1 depthTo:5 withLinks:1 updateOnSave:1 orderedList:0 -->

- [Contributing](#contributing)
- [Definitions](#definitions)
- [Introduction](#introduction)
   - [What are the goals of Jade](#what-are-the-goals-of-jade)
   - [What influenced the design decisions](#what-influenced-the-design-decisions)
   - [What are the tradeoffs](#what-are-the-tradeoffs)
- [Jade Specification](#jade-specification)
   - [Jade Common](#jade-common)
      - [Jade](#jade)
      - [Jade-service-runner](#jade-service-runner)
      - [Jade-ui-{platform}-wrapper](#jade-ui-platform-wrapper)
   - [An Individual Jade Project Architecture](#an-individual-jade-project-architecture)
      - [Jade-{project}](#jade-{project})
         - [Jade-{project}-{language}](#jade-{project}-{language})
         - [Jade-{project}-rpc](#jade-{project}-{language})
            - [Jade-{project}-client-{language}](#jade-{project}-client-{language})
         - [Jade-{project}-ui](#jade-{project}-ui)
   - [Proposed 1.0.0](#proposed-1.0.0)

<!-- /TOC -->

# Contributing

# Definitions

# Introduction

## What are the goals of the Jade

The goal of Jade is to enable the creation of decentralized, peer to peer applications built for ethereum classic.

Jade should solve the following problems:
1. dapp users should have control over their accounts. This means fine grain controls over:
  - Where the private keys are stored. (local or remote?, via 3rd party service? Hardware?)
  - When and how the private key may be used to sign transactions/messages.
1. dapp developers should have uniformly documented interfaces for the blockchain, accounts and all other software required to build dapps. They should use OpenRPC.
1. dapp developers should have an easy way of deploying their applications. This means reducing scope of concerns, and enabling dapp developers to ignore the problem of where to get blockchain info from, or where the users account lives.
1. dapps should be able to run nearly anywhere -- browsers, phones, desktops, etc.
1. dapp users should choose the security model that fits them, not the dapp developer.
1. dapp users should have tools at their disposal that makes all of the above **easy enough for your grandpa**

## What influenced the design decisions

## What are the tradeoffs

# Jade Specification

All Projects:
1. follow [pristine](https://github.com/etclabscore/pristine)

### Jade Common 

#### Jade

1. No code, just readme and links to all the goods. This is the first thing you want a google of Jade Etc to see
1. contains github pages site that would be the root of the projects subdomaining (jade.etclabs.org)

#### Jade-service-runner

1. runs any jade-{project}-rpc service on any platform
1. provides a 'meta rpc' or rpc gateway for any services being. It would be an aggregate of all the jade-{project}s that it is currently running
1. provides a configuration layer for easily maintaining data directories / named environments. In practice, this would be used for things like dev env that has seperate accounts / chain data / etc

**note**: `platform` here is one of: 'electron', 'mobile'

1. Anything that takes the web based ui exported by jade-{project}-ui and produces a platform specific wrapper for it
1. web application electron wrapper

### An Individual Jade Project Architecture

#### Jade-{project}
1. Top level of a project. 
1. place you want people to see first
1. contains github pages site that would be the root of the projects subdomaining ({projectname}.jade.etclabs.org)

#### Jade-{project}-{language}

1. Exports a package for the language specified by `language`.
1. May use a compiled and wrapped build to provide the requisite functions of the project. For example, a jade-{project}-js where the js package is really just the jade-{project}-rust crate compiled to wasm and documented / pushed to npm
1. Includes github pages / generated docs.

#### Jade-{project}-rpc

1. First place you want people to see about RPC server for this project.
1. Should define the OpenRPC schema file.
1. contains github pages site that would be the root of the projects subdomaining ((docs | playground).{projectname}.jade.etclabs.org)
1. MUST expose functionality provided by Jade-{project}-{language} via json rpc server
1. exposes json rpc with service discovery

#### Jade-{project}-client-{language}

1. Library that implements a client to use the json rpc service.
1. one per language generated
1. packages are published to package manager based on language of implementation

#### Jade-{project}-ui

1. UI tailored to dapp users or developers that is built ontop of the json rpc
1. packaged as web application
1. uses `Jade-{project}-client-{language}`s

## proposed 1.0.0

The first Jade-{project}:
- Jade-signer
  - Jade-signer-rs
  - Jade-signer-rpc
  - Jade-signer-client-rs
  - Jade-signer-client-js
  - Jade-signer-ui
- Jade-evm
  - Jade-evm-rs
  - Jade-evm-rpc
  - Jade-evm-ui ??
- Jade-ui-electron-wrapper
- Jade-service-runner
- Jade-wallet

Jade-wallet
 - web app
 - listens to window.postMessage for ECLIPXXXX spec transaction messages
 - is wrapped in electron protocol handler magico
 - uses a configurable manifest file to hint service runner what to run
 - works without service runner via a default, etclabs supported public service runner (with in mem accounts???)

Jade-signer
1. lightweight account management that doesn't require ethereum rpc.
1. Ideally is agnostic to the network onwhich the account would be used...
1. pretty much only has: account crud, signTransaction, signMessage

Jade-service-runner
1. runs any jade-{project} service on any platform
1. provides a 'meta rpc' or rpc gateway for any services being.
