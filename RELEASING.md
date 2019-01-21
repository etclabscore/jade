![](https://www.etclabs.org/dist/resources/images/v2/logo-top.png)
Supported by [ETC Labs](https://www.etclabs.org/)

# Jade Project Releasing

#### Version 1.0.0

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [BCP 14](https://tools.ietf.org/html/bcp14) [RFC2119](https://tools.ietf.org/html/rfc2119) [RFC8174](https://tools.ietf.org/html/rfc8174) when, and only when, they appear in all capitals, as shown here.

This document is licensed under [The Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.html).

when using the name 'version' we mean the versioning scheme described in [VERSIONING.md](VERSIONING.md)

## Introduction

This document is to describe how a jade project is to structure its build output such that common tooling may be used to generate releases.

We propose:
 - a folder name convention for build artifacts
 - a Build folder structure
 - a set of release targets that are allowable
 - a pipeline for handling the release folder's artifacts

It is NOT the purpose of this document to describe how a project might create a build. It is only describing a strcture in which jade projects MUST write build artifacts to.

## Release Folder Name
The cannonical folder for releases SHALL be named `releases` and be located at the root of the project repository.
Each project MUST gitignore the `releases` folder.

## Release Folder Structure
The folder structure is as follows:
```
.
└── releases
    └── {version}
        └── {platform}
            └── {project-name}.exe
```

It is the responsibilty of the build tooling to write artifacts to the appropriate location.

Below is an example:
```
.
└── releases
    └── 1.0.0
        └── windows
            └── jade-signer.exe
```


## Build Targets
below is a list of build targets
1. windows
2. linux
3. osx

## Release Targets
1. github
2. (tentative) docker

## Release Pipeline
1. sign the releases

## Release Template
### Github release
| field name       | content                                                        |
| tag version      | the name of version folder                                     |
| title            | same as tag                                                    |
| description      | {changelog}                                                    |
| release binaries | for each platform: `{project-name}-{platform}-{version}.{ext}` |
