# Using Software Modules on Laguna HPC

## Overview
Laguna provides a **module system** to manage software installations efficiently. 
Instead of manually setting paths and dependencies, users can dynamically load, unload, and switch between software packages.

## Checking Available Modules
To see what software is available, use:
```sh
module avail
```
The output will depend on the currently loaded modules.

### Example Output:
```sh
$ module list

Currently Loaded Modules:
 1) gcc/13.3.0      3) openblas/0.3.28   5) usc/13.3.0
 2) python/3.11.9   4) openmpi/5.0.5
```

## Loading Modules
To load a software module, use:
```sh
module load <module_name>
```
For example, to load Python:
```sh
module load python
```

You can then verify the loaded software:
```sh
which python
```



### Example Output After Loading:
```sh
$ module load python
$ which python
/apps/spack/2406/apps/linux-rocky8-x86_64_v3/gcc-13.3.0/python-3.11.9-x74mtjf/bin/python
```

## Searching for Modules
If a module is not immediately available, you can search for it using:
```sh
module spider <software_name>
```
For example, searching for R:
```sh
module spider r/4.4.2
```

### Example Output:
```sh
-----------------------------------------------------
  r: r/4.4.2
-----------------------------------------------------
    You will need to load all module(s) on any one of the lines below before the "r/4.4.2" module is available to load.
      gcc/13.3.0
```

This indicates that **GCC 13.3.0** must be loaded before loading R 4.4.2.

## Unloading Modules
To unload a module:
```sh
module unload <module_name>
```
For example, unloading Python:
```sh
module unload python
```

To remove all loaded modules:
```sh
module purge
```

## Saving Frequently Used Modules
If you frequently use the same set of modules, you can save them as a default environment:
```sh
module save my_defaults
```
Later, you can restore them using:
```sh
module restore my_defaults
```

## Summary
- Use `module avail` to list available modules.
- Use `module load <module_name>` to load a module.
- Use `module spider <software_name>` to find hidden modules.
- Use `module unload <module_name>` to remove a module.
- Use `module save` and `module restore` to manage frequently used sets.

For further assistance, contact **LAGUNA-SUPPORT@USC.EDU**.
