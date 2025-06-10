^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Changelog for package canboat_vendor
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Forthcoming
-----------
* Add "How to Use" section to README.md
* Bugfix: update ExternalProject_Add statement for compliance with older CMake versions
* Bugfix: swap to HTTPs URL so cloning possible w/o git SSH key
* Add the Makefile to .gitignore
* Remove the Makefile from git
* Switch to letting CMake download the Canboat repo at build time with ExternalProject_Add
* Contributors: Severn Lortie

0.0.1 (2025-05-14)
------------------
* Update README.md to use new name: canboat_vendor
* Add license file
* Use static build directory instead of matching platform name
* Merge commit 'f39affbd619aba803c074b5237357a14b100d688' as 'canboat'
* Squashed 'canboat/' content from commit 27cc989
  git-subtree-dir: canboat
  git-subtree-split: 27cc98974fbe05a97175882a50033aca370ea210
* bugfix(CMakeLists.tx): use a custom install target to copy over Canboat's binaries instead of Ament install()
* Move over to using ExternalProject with CMake rather than git submodules for user QoL
* Remove canboat submodule
* Add README.md
* Initial commit
* Contributors: Severn Lortie
