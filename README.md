# Spoofax Bootstrapping

This repository contains the source code of Spoofax's eight meta-languages that we successfully bootstrap with seven changes.

This repository contains submodules for meta-language definitions, which are essentially links to a specific commit in repository of the meta-language.
Clicking the link will navigate to the commit with the change.

We list the source code and baseline for each change tagged with a version.

* v2.1.0: [sources](https://github.com/spoofax-bootstrapping/bootstrapping/tree/ca59c5fab337aa6358e541aa3ffca181beebf75f), [produced baseline](https://github.com/spoofax-bootstrapping/bootstrapping/releases/tag/v2.1.0), [fixpoint bootstrapping log](https://github.com/spoofax-bootstrapping/bootstrapping/releases/download/v2.1.0/bootstrap-2.1.0.txt)
* v2.1.1: [sources](https://github.com/spoofax-bootstrapping/bootstrapping/tree/636a2c294d0505e82d17922da8abef14867f0ca4), [produced baseline](https://github.com/spoofax-bootstrapping/bootstrapping/releases/tag/v2.1.1)
* v2.1.2: [sources](https://github.com/spoofax-bootstrapping/bootstrapping/tree/5988a5d6e9a75eb0bbebc1075833125f7dbca4a6), [produced baseline](https://github.com/spoofax-bootstrapping/bootstrapping/releases/tag/v2.1.2)
* v2.1.3: [sources](https://github.com/spoofax-bootstrapping/bootstrapping/tree/437dcba972e7c867eb83a1fd7baf8fc57a3e4191), [produced baseline](https://github.com/spoofax-bootstrapping/bootstrapping/releases/tag/v2.1.3)
* v2.1.4: [sources](https://github.com/spoofax-bootstrapping/bootstrapping/tree/9c97ce4d397209dae824bd4c046d5f39599452e5), [produced baseline](https://github.com/spoofax-bootstrapping/bootstrapping/releases/tag/v2.1.4), [fixpoint bootstrapping log](https://github.com/spoofax-bootstrapping/bootstrapping/releases/download/v2.1.4/bootstrap-2.1.4.txt)
* v2.1.5: [sources](https://github.com/spoofax-bootstrapping/bootstrapping/tree/bb4d7f087788e08b31f4fd349c1867953f5463ad), [produced baseline](https://github.com/spoofax-bootstrapping/bootstrapping/releases/tag/v2.1.5), [fixpoint bootstrapping log](https://github.com/spoofax-bootstrapping/bootstrapping/releases/download/v2.1.5/bootstrap-2.1.5.txt)
* v2.1.6: [sources](https://github.com/spoofax-bootstrapping/bootstrapping/tree/b0edab91fad109726ff0119e6746d9b18cd547c1), [produced baseline](https://github.com/spoofax-bootstrapping/bootstrapping/releases/tag/v2.1.6)
* v2.1.7: [sources](https://github.com/spoofax-bootstrapping/bootstrapping/tree/116492420805658803ded605fd80c9a5a98bda96), [produced baseline](https://github.com/spoofax-bootstrapping/bootstrapping/releases/tag/v2.1.7), [fixpoint bootstrapping log](https://github.com/spoofax-bootstrapping/bootstrapping/releases/download/v2.1.7/bootstrap-2.1.7.txt)


## Implementation source code

We have implemented the bootstrapping method in the Spoofax language workbench. We link to several parts of the source code that implement important parts.

* Compile: [Builder.java](https://github.com/spoofax-bootstrapping/spoofax/blob/master/org.metaborg.core/src/main/java/org/metaborg/core/build/Builder.java)
* Bootstrap: [BootstrapJob.java](https://github.com/spoofax-bootstrapping/spoofax-eclipse/blob/bootstrapping/org.metaborg.spoofax.eclipse.meta/src/main/java/org/metaborg/spoofax/eclipse/meta/bootstrap/BootstrapJob.java), with the following parts:
  * [Fixpoint loop](https://github.com/spoofax-bootstrapping/spoofax-eclipse/blob/bootstrapping/org.metaborg.spoofax.eclipse.meta/src/main/java/org/metaborg/spoofax/eclipse/meta/bootstrap/BootstrapJob.java#L154-L245)
  * [Rollback and cancellation](https://github.com/spoofax-bootstrapping/spoofax-eclipse/blob/bootstrapping/org.metaborg.spoofax.eclipse.meta/src/main/java/org/metaborg/spoofax/eclipse/meta/bootstrap/BootstrapJob.java#L252-L265), which undo's changes using a command pattern:
    * [Setting/reverting the version of a language definition](https://github.com/spoofax-bootstrapping/spoofax-eclipse/blob/bootstrapping/org.metaborg.spoofax.eclipse.meta/src/main/java/org/metaborg/spoofax/eclipse/meta/bootstrap/BootstrapSetVersionChange.java)
    * [Setting/reverting versions of dependencies in a language definition](https://github.com/spoofax-bootstrapping/spoofax-eclipse/blob/bootstrapping/org.metaborg.spoofax.eclipse.meta/src/main/java/org/metaborg/spoofax/eclipse/meta/bootstrap/BootstrapSetDepVersionChange.java)
    * [Storing/deleting binary of a language implementation](https://github.com/spoofax-bootstrapping/spoofax-eclipse/blob/bootstrapping/org.metaborg.spoofax.eclipse.meta/src/main/java/org/metaborg/spoofax/eclipse/meta/bootstrap/BootstrapStoreBinaryChange.java)
    * [Loading/unloading a language implementation](https://github.com/spoofax-bootstrapping/spoofax-eclipse/blob/bootstrapping/org.metaborg.spoofax.eclipse.meta/src/main/java/org/metaborg/spoofax/eclipse/meta/bootstrap/BootstrapLoadLangChange.java)
  * [Setting versions](https://github.com/spoofax-bootstrapping/spoofax-eclipse/blob/bootstrapping/org.metaborg.spoofax.eclipse.meta/src/main/java/org/metaborg/spoofax/eclipse/meta/bootstrap/BootstrapJob.java#L399-L424)
  * [Compiling, storing, comparing](https://github.com/spoofax-bootstrapping/spoofax-eclipse/blob/bootstrapping/org.metaborg.spoofax.eclipse.meta/src/main/java/org/metaborg/spoofax/eclipse/meta/bootstrap/BootstrapJob.java#L427-L460)
* Binary comparison: [ResourceComparer.java](https://github.com/spoofax-bootstrapping/spoofax-eclipse/blob/bootstrapping/org.metaborg.spoofax.eclipse.meta/src/main/java/org/metaborg/spoofax/eclipse/meta/bootstrap/ResourceComparer.java)
