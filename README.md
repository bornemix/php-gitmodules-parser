PHP .gitmodules parser
============================

Small API for parsing .gitmodules file.

Submodule object
----------------------------

The API returns instances of [stdClass](http://lmgtfy.com/?q=stdClass) with the following properties:

* ```$submodule->parent_gitmodules_path``` is the path to the .gitmodules file where this submodule is mapped. Used for nested submodules, and translating ```$submodule->path``` to a real path.
* ```$submodule->name``` is the name of the submodule. Not really used for anything.
* ```$submodule->path``` is the local, relative path of the folder that has the submodule contents.
* ```$submodule->url``` is the URL to the repo.
* ```$submodule->dir_exists``` is true if the directory to the submodule exists.
* ```$submodule->is_github``` is true if the submodule points to a GitHub repo.
* ```$submodule->author``` is the GitHub username who owns the repo (url is parsed by Regex). Will be unset if not a GitHub repo.
* ```$submodule->repo``` is the GitHub repo name (url is parsed by Regex). Will be unset if not a GitHub repo.

Functions
----------------------------

### gitmodules_get_all($dir = '.')

Returns an array of all Submodule objects referenced in the ```.gitmodules``` file located in the directory ```$dir```. No trailing slash is necessary.

### gitmodules_get_all($name, $dir = '.')

Returns the Submodule objects named $name referenced in the ```.gitmodules``` file located in the directory ```$dir```. No trailing slash is necessary.