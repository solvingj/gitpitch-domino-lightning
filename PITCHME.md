## Project Domino
*A CI-agnostic Project-Level Dependency System*

![Image](./assets/BcCube128.png)

---
### Bincrafters OSS Team

Find us online...
* https://bincrafters.github.io
* https://twitter.com/bincrafters
* https://github.com/bincrafters
* https://opencollective.com/bincrafters

---
### Universal CI Dependencies
* Upstream library release trigger downstream CI 
	* downstream dependency libraries
	* downstream package manager repos
	* flexible build policies for downstream consumers 
* Like Libraries.io - but trigger jobs instead of email

---
### Prior Art
* Libraries.io - Simple, good indicator of demand
* Numerous other recent competitors to Libraries.io
* Fedora - https://release-monitoring.org/projects
* Some CI Systems can trigger from "upstream builds"
* All proprietary implementations of a simple concept

---
### Motivation
* Conan : C++ has "ABI compatibility" challenge 
* Bincrafters : Above + Boost + 100 More Packages
* Realized our needs are universal among PM's
	* Apt/Yum/Brew/Conda/Vcpkg/Choco/Onepkg/etc
* Realized it's needed in enterprise as much as OSS
* Great candidate to generalize and open-source

---
### Another Perspective
* A CI agnostic dependency definition layer
* For Enterprise
	* Build based on OSS and internal deps
* For OSS
	* Single source of truth for multiple CI:
		* Travis/Appveyor/CircleCI/Etc

---
### Domino - Impementation Ideas
* Relatively easy business logic (pub/sub)
* Define schema for upstream-to-downstream events
* Include commit message parsing for control 
* Yaml spec for defining "dependencies" and "filters"
* Like "build_policy" from Conan Package Tools
* Define standard keywords like "[build_filter=]":
	* "skip_deps_transitive" | "skip_deps_abc"
* Allow customizable keywords and behavior:
	* "clear_cache" | "force_docker_pull"

---
### Phase 1 - OSS
* Tune into Libraries.io to capture events
* Start with subscribe app on Github marketplace 
	* Trigger builds with empty git commit
	* Later send webhooks direct to CI's
---
	
### Phase 2 - Enterprise
* CI Specific integrations around the webhooks
	* Jenkins/Bamboo/TFS Plugins Etc
	
