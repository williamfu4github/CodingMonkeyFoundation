### Maven Overview
- **Apache Maven** is a **build tool** mainly **for Java**
  - manage dependencies
  - manage build
  - manage versioning
  - open source
  - cross platform
- Other popular build tools
  - Make for C/C++
    - not cross platform
  - Apache ANT
    - designed as replacement for Make
- Maven vs ANT
  - Maven
    - black box
    - convention over configuration
    - better IDE integration
  - ANT
    - easily trace
    - low reusability

---

### Maven Basic Structure
- default project directories:
  - source code: src/main/java/
  - test code: src/test/java/
  - output: target/
  - configuration: pom.xml
- the artifact 3-tuple
  - groupId: same as package prefix
  - artifactId: same as project name
  - version
    - release version
    - SNAPSHOT: non-release up-to-date build
- default path to local repo (artifact storage): ~/.m2/repository
  - artifacts are shared among projects
    - to avoid duplication
  - if some lib is missing in local repo, it will be downloaded
    - from default remote
      - repo.maven.apache.org
    - from corporate repos
    - from dependency repos

---

### Maven Dependencies
- add dependency by 3-tuple
- dependency can have scope
  - compile (default): available all time
  - provided: available during build time only
  - runtime: available during run time only
  - test: available during test phases only
    - ex. JUnit

---

### Maven Phases, Goals and Plugins
- build phases
  - **validate**
    - validate project and structure
    - download required artifact
      - dependencies and **transitive dependencies**
  - **compile**
    - compile source code (not test code)
  - **test**
    - compile test code
    - run unit tests
  - **package**
    - put classes into package (ex. jar)
  - **integration-test**
    - run integration tests
  - **verify**
    - validations before install and deploy
  - **install**
    - copy package into local repo
  - **deploy**
    - copy package into remote repo
- default goals
  - **compile / package / install / deploy**
    - execute build phases up to this phase
  - **clean**
- **super pom** has default behaviour of goals defined
  - inherently added to **effective pom**
  - use **plugin** to override behaviour
