---
title: "npm vs yarn"
date: 2021-10-10T09:55:46+05:30
draft: false
categories:
- "package manager"
tags:
- "npm"
- "yarn"
- "package manager"
---

npm vs. yarn
============

In the days before package managers, it was commonplace for JavaScript engineers to rely on a small number of dependencies stored directly in their projects or served by a CDN.

The primary function of any package manager is to install some package --- a piece of code that serves a particular purpose --- from a global registry into an engineer's local environment. Each package may or may not depend on other packages. A typical project could have tens, hundreds, or even thousands of packages within its tree of dependencies. These dependencies are versioned and installed based on semantic versioning (semver).

npm is one of the most popular package managers in the world. The other package managers are jspm, Yarn, etc.

npm and Yarn are both package managers for JavaScript programming language. npm is a software registry that host packages of free, reusable code. Within the npm registry, you can search and find libraries like jQuery, Bootstrap, Angular and React, and JavaScript components. You can host your own private software registry in your company and host private libraries in the registry for access within the team. Yarn depends on the npm registry. Engineers still have to access the npm registry, but they can install packages more quickly and manage dependencies consistently across machines or in secure offline environments.

npm and Yarn can be used to package reusable code for private or public projects, that can be shared and distributed among teams around the world. The code is shared through a package aka. module. A package contains all the code being shared as well as a package.json file which describes the package. The code contains developers' solutions to different problems, making it easier for other developers to develop their software.

They help in managing dependencies in the projects.

### Problems with npm Client

-   `npm install` needs internet connection to retrieve dependencies from the npm registry. In case of large projects and slow network, this activity could consume a lot of time.
-   It is cumbersome to version control node_modules. It would take hours to update a package, resolve conflicts and check-in to the repository. It also adds a lot of metadata from the packages to the repository. npm's shrinkwrap feature can be used to lock down dependency versions to prevent adding node_modules to a repository.
-   npm client executes code from some of the dependencies automatically
-   It is difficult to install dependencies across different machines and users

Why Yarn?
---------

Yarn is a fast, reliable, and secure alternative to npm client.

Node Package Manager (npm)
--------------------------

npm is licensed and distributed under The Artistic License 2.0. It is the default package manager for the JavaScript runtime environment Node.js. npm is automatically included when Node.js is installed. It consists of a command line client, also called npm, and an online database of public packages, called the npm registry. The registry is accessed via the client, and the available packages can be browsed and searched via the npm client or npm website.

All dependencies get placed within a `node_modules` directory in your project. The npm client installs dependencies into the node_modules directory non-deterministically. This means that based on the order dependencies are installed, the structure of a node_modules directory could be different from one person to another.

Yarn Package Manager
--------------------

Yarn is licensed and distributed under BSD License. Yarn uses `lockfiles` and an `install algorithm` that is deterministic and reliable. These lockfiles lock the installed dependencies to a specific version, and ensure that every install results in the exact same file structure in node_modules across all machines. The written lockfile uses a concise format with ordered keys to ensure that changes are minimal and review is simple.

```
yarn --version # prints version number

yarn info jquery # fetch information about jQuery package and return it in a tree format
yarn info jquery description # fetch description from jQuery package
yarn info jquery@2.1.1 # fetch information about a specific version of jQuery package
yarn info jquery readme # fetch README information from jQuery

yarn init # initialize development of a package; creates package.json, yarn.lock and node_modules folder

yarn add jquery@3.2.1 # add jQuery version 3.2.1 as project dependency
yarn add bootstrap@3.3.7 # add Bootstrap package to use in your current package
yarn add angular@1.6.4 # equivalent to `npm install --save angular@1.6.4`
yarn add mocha --dev # add Mocha package as developer dependency
yarn remove mocha # remove unused Mocha package from your current package

yarn # reads package.json, fetches packages from npm registry, and populate node_modules folder
yarn install # install all dependencies defined in package.json

yarn why jquery # identifies why jQuery has been installed, detailing which other packages depend upon it
yarn publish # publish package to a package manager (private or public npm registry)
```

Resources
---------

-   [npm package manager - Official website](https://www.npmjs.com/)
-   [npm package manager - GitHub](https://github.com/npm/npm)
-   [npm documentation](https://lakum.in/blog/docs.npmjs.com)
-   [Yarn package manager - Official website](https://yarnpkg.com/)
-   [Yarn package manager - GitHub](https://github.com/yarnpkg/yarn)
-   [Yarn: a new package manager for JavaScript](https://code.facebook.com/posts/1840075619545360)
-   [Dependency Hell - npm](http://npm.github.io/how-npm-works-docs/theory-and-design/dependency-hell.html)
-   [Dependency Hell - Wikipedia](https://en.wikipedia.org/wiki/Dependency_hell)
-   [Semantic Versioning](http://semver.org/)

Definitions
-----------

#### Content Delivery Network or Distribution Network

CDN is a globally distributed network of proxy servers deployed in multiple data centers. The goal of a CDN is to serve content to end-users with high availability and high performance.

#### Dependency Hell

Dependency Hell is where you are when version lock and/or version promiscuity prevent you from easily and safely moving your project forward. The dependency issue arises around shared packages or libraries on which several other packages have dependencies but where they depend on different and incompatible versions of the shared packages. If the shared package or library can only be installed in a single version, the user may need to address the problem by obtaining newer or older versions of the dependent packages. This, in turn, may break other dependencies and push the problem to another set of packages.

#### Semantic Versioning

Semver specification is authored by Tom Preston-Werner, inventor of Gravatars and cofounder of GitHub. It is proposed as a simple set of rules and requirements to solve `Dependency Hell`. Semantic Versioning scheme dictates how version numbers are assigned and incremented for software packages. In this scheme, version numbers and the way they change convey meaning about the underlying code and what has been modified from one version to the next. Consider a version format of X.Y.Z (Major.Minor.Patch). Bug fixes not affecting the software - increment the patch version, backwards compatible software additions/changes increment the minor version, and backwards incompatible software changes increment the major version.

##### Packaging

> Given a version number MAJOR.MINOR.PATCH, increment the:

-   MAJOR version when you make incompatible API changes,
-   MINOR version when you add functionality in a backwards-compatible manner, and
-   PATCH version when you make backwards-compatible bug fixes.

-- semver.org

```
"lodash": ~1.2.3 # >=1.2.3-0 <1.3.0-0 (match reasonably close version)
"lodash": ^1.2.3 # >=1.2.3-0 <2.0.0-0 (match compatible version)
"lodash": 1.2.3 # exact match
"lodash": latest # latest version
```

##### Links on Semver:

-   [npm, no longer defaults to tildes](http://fredkschott.com/post/2014/02/npm-no-longer-defaults-to-tildes/)
-   [Semantic versioning](https://semver.npmjs.com/)
-   [Semver, GitHub repository](https://github.com/npm/node-semver)
-   [Semver, npm docs](https://docs.npmjs.com/misc/semver)
-   [Cheatsheet on Semver](https://bytearcher.com/goodies/semantic-versioning-cheatsheet/)
-   [Semver explained: why there's a caret in my package.json](https://bytearcher.com/articles/semver-explained-why-theres-a-caret-in-my-package-json/)

-   [Github](https://www.github.com/kranthilakum)
-   [Linkedin](https://www.linkedin.com/in/kranthilakum/)
-   [StackOverflow](https://stackoverflow.com/users/1509209/kranthi-lakum)
-   [Twitter](https://twitter.com/krantlak)
-   [Facebook](https://www.facebook.com/kranthilakum)
-   [Instagram](https://www.instagram.com/krantlak)