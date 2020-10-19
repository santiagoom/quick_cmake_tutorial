








set
```

Set a normal, cache, or environment variable to a given value. See the cmake-language(7) variables documentation for the scopes and interaction of normal variables and cache entries.

Signatures of this command that specify a <value>... placeholder expect zero or more arguments. Multiple arguments will be joined as a semicolon-separated list to form the actual variable value to be set. Zero arguments will cause normal variables to be unset. See the unset() command to unset variables explicitly.

Set Normal Variable
set(<variable> <value>... [PARENT_SCOPE])
Sets the given <variable> in the current function or directory scope.

If the PARENT_SCOPE option is given the variable will be set in the scope above the current scope. Each new directory or function creates a new scope. This command will set the value of a variable into the parent directory or calling function (whichever is applicable to the case at hand). The previous state of the variable’s value stays the same in the current scope (e.g., if it was undefined before, it is still undefined and if it had a value, it is still that value).

```

add_executable
```

Contents

add_executable

Normal Executables

Imported Executables

Alias Executables

Add an executable to the project using the specified source files.

Normal Executables
add_executable(<name> [WIN32] [MACOSX_BUNDLE]
               [EXCLUDE_FROM_ALL]
               [source1] [source2 ...])
Adds an executable target called <name> to be built from the source files listed in the command invocation. (The source files can be omitted here if they are added later using target_sources().) The <name> corresponds to the logical target name and must be globally unique within a project. The actual file name of the executable built is constructed based on conventions of the native platform (such as <name>.exe or just <name>).

By default the executable


```


add_library
```
Contents

add_library

Normal Libraries

Object Libraries

Interface Libraries

Imported Libraries

Alias Libraries

Add a library to the project using the specified source files.

Normal Libraries
add_library(<name> [STATIC | SHARED | MODULE]
            [EXCLUDE_FROM_ALL]
            [<source>...])
Adds a library target called <name> to be built from the source files listed in the command invocation. (The source files can be omitted here if they are added later using target_sources().) The <name> corresponds to the logical target na
```


```
find_library
A short-hand signature is:

find_library (<VAR> name1 [path1 path2 ...])
The general signature is:

find_library (
          <VAR>
          name | NAMES name1 [name2 ...] [NAMES_PER_DIR]
          [HINTS path1 [path2 ... ENV var]]
          [PATHS path1 [path2 ... ENV var]]
          [PATH_SUFFIXES suffix1 [suffix2 ...]]
          [DOC "cache documentation string"]
          [REQUIRED]
          [NO_DEFAULT_PATH]
          [NO_PACKAGE_ROOT_PATH]
          [NO_CMAKE_PATH]
          [NO_CMAKE_ENVIRONMENT_PATH]
          [NO_SYSTEM_ENVIRONMENT_PATH]
          [NO_CMAKE_SYSTEM_PATH]
          [CMAKE_FIND_ROOT_PATH_BOTH |
           ONLY_CMAKE_FIND_ROOT_PATH |
           NO_CMAKE_FIND_ROOT_PATH]
         )
This command is used to find a library. A cache entry named by <VAR> is created to store the result of this command. If the library is found the result is stored in the variable and the search will not be repeated unless the variable is cleared. If nothing is found, the result will be <VAR>-NOTFOUND. The REQUIRED option stops processing with an error message if nothing is found, otherwise the search will be attempted again the next time find_library is invoked with the same variable.



```

find_package
```
Contents

find_package

Basic Signature and Module Mode

Full Signature and Config Mode

Version Selection

Search Procedure

Package File Interface Variables

Find an external project, and load its settings.

Basic Signature and Module Mode
find_package(<PackageName> [version] [EXACT] [QUIET] [MODULE]
             [REQUIRED] [[COMPONENTS] [components...]]
             [OPTIONAL_COMPONENTS components...]
             [NO_POLICY_SCOPE])
Finds and loads settings from an external project. <PackageName>_FOUND will be set to indicate whether the package was found. When the package is found package-specific information is provided through variables and Imported Targets documented by the package itself. The QUIET option disables informational messages, including those indicating that the package cannot be found if it is not REQUIRED. The REQUIRED option stops processing with an error message if the package cannot be found.

A package-specific list of required components may be listed after the COMPONENTS option (or after the REQUIRED option if present). Additional optional components may be listed after OPTIONAL_COMPONENTS. Available components and their influence on whether a package is considered to be found are defined by the target package.
```