# Jade Project Versioning

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [BCP 14](https://tools.ietf.org/html/bcp14) [RFC2119](https://tools.ietf.org/html/rfc2119) [RFC8174](https://tools.ietf.org/html/rfc8174) when, and only when, they appear in all capitals, as shown here.

This document is licensed under [The Apache License, Version 2.0](https://www.apache.org/licenses/LICENSE-2.0.html).

## Introduction
This document is to describe how a jade project is to version its releases

It also describes standardized tooling around manipulating the version

## Semver
A Jade project MUST use Semantic Versioning [semver](https://semver.org). Build metadata MAY NOT be used in a jade project. Build metadata SHOULD be ignored.

A Basic summary of Semantic Versioning taken from: [semver.org(https://semver.org)

### Summary:

Given a version number MAJOR.MINOR.PATCH, increment the:

MAJOR version when you make incompatible API changes,
MINOR version when you add functionality in a backwards-compatible manner, and
PATCH version when you make backwards-compatible bug fixes.
Additional labels for pre-release and build metadata are available as extensions to the MAJOR.MINOR.PATCH format.

## Standardized tooling

each project should implement `bin/bump-version.sh {newVer}`
