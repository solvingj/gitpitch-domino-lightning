## Project Domino

![Image](./assets/BcCube128.png)

---
### Find Us Online

https://opencollective.com/bincrafters
https://bincrafters.github.io
https://twitter.com/bincrafters

---
### Domino - Universal CI Dependencies
- A CI-agnostic Project-Level Dependency System
- Upstream library release trigger downstream CI 
	- downstream dependency libraries
	- downstream package manager repos
	- flexible build policies for downstream consumers 
- Like Libraries.io - take action rather than sending emails

### Domino - Prior Art
- Libraries.io - Simple, good indicator of demand
- Numerous other recent competitors to Libraries.io
- Fedora - https://release-monitoring.org/projects
- Most Mature CI Systems can trigger from "upstream builds"
- All proprietary implementations of a simple concept

### Domino - Motivation
- Conan : C++ has unique property of ABI compatibility 
- Bincrafters : Above + Boost + 100 More Packages
- Realized our needs are universal among package managers
	- Apt/Yum/Brew/Conda/Vcpkg/Choco/Onepkg/etc
- Realized it's needed in enterprise just as much as OSS
- Great candidate to generalize and open-source

### Domino - Another Perspective
- A CI agnostic dependency definition layer
- Not just release branches - build develop against develop
- For Enterprise
	- Build based on both internal libs and OSS dependencies
- For OSS
	- Single source of truth for Travis/Appveyor/CircleCI/Etc

### Domino - Impementation Ideas
- Relatively easy business logic (pub/sub)
- Define extensible schema for upstream-to-downstream events
- Include commit message parsing as a signaling mechanism 
- Yaml spec for defining "dependencies" and "build_filters"
- Inspired by "build_policy" parsing of Conan Package Tools
- Define standard keywords for downstream "[build_filter=]":
	- "skip_deps_transitive" | "skip_deps_<project_names>"
- Allow customizable keywords and behavior for enterprise:
	- "clear_cache" | "force_docker_pull"

### Domino - Project Profile - Phase 1 OSS
- Start with dedicated pub/sub apps on Github marketplace 
	- Early version can trigger builds with empty git commit
	- Later send webhooks direct to CI's (requires more auth logic)
	
### Domino - Project Profile - Phase 2 Enterprise
- CI Specific integrations around the webhooks
	- Jenkins/Bamboo/TFS Plugins Etc
	- Eventually displace proprietary upstream/downstream definitions

