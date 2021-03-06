## `ern cauldron add miniapps`

#### Description

* Add one or more MiniApps to a non-released native application version in a Cauldron  
* Perform multiple checks, including MiniApp dependencies analysis, to ensure compatibility with the target native application container  
* Generate and publish a new Container version  

#### Syntax

`ern cauldron add miniapps <miniapps..>`  

**Arguments**

`<miniapps..>`

* One or more package path to MiniApps (delimited by spaces) to add to a target native application version in the Cauldron.
* Any MiniApp path (but file path) will be added to the Container in the Cauldron, as such, with the exception of a git path including a branch. In that case, the MiniApp path that will be added to the Container in the Cauldron will contain the commit SHA of the HEAD of the branch, rather than the branch itself.
* The following types of MiniApp paths are not supported by this command :
  - File path (ex `file://Users/foo/MiniApp`)
  - Git path missing branch/tag or commit sha (ex: `https://github.com/foo/MiniApp.git`)
  - Registry path missing version (ex: `MiniApp`)
  - Registry path using a version range (ex: `MiniApp@^1.0.0`)

**Example**  

`ern cauldron add miniapps MyFirstMiniApp@1.0.0 MySecondMiniApp@2.0.0`

**Options**  

`--containerVersion/-v <version>`

* Specify a version for the new container  
* **Default**  Increment the patch digit of the current container version  

`--descriptor/-d <descriptor>`

* Add the MiniApp to a given target native application version in the Cauldron matching the provided native application descriptor.  
* You can only pass a complete native application descriptor as the MiniApp added through this command targets only a specific single native application version.  
**Default**  Lists all non-released native application versions from the Cauldron and  prompts you to choose one to add to the MiniApp.  
**Example** `ern cauldron add miniapps <miniapps..> -d MyNativeApp:android:1.0.0`  

`--force/-f`

* Bypass compatibility checks and force-add the MiniApp to the Cauldron.  
**Caution**  Before using the `--force/-f` option, be sure that you can bypass compatibility checks.

#### Remarks
 
* If one MiniApp does not pass compatibility checks, the MiniApp is not added to the Cauldron and a new container version is not generated.

#### Related commands

[ern cauldron update miniapps] | Updates the version of an existing MiniApp

_________
[ern cauldron update miniapps]: ../update/miniapps.md