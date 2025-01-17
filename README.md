# FreeCAD Workbench Starter Kit

Template for generating FreeCAD workbenches.

## Dependencies

* python3
* [cookiecutter](https://cookiecutter.readthedocs.io)

## Quick Start

### Create a workbench

Launch cookiecutter and point it at the template repo:

```bash
$ cookiecutter https://github.com/FreeCAD/freecad.workbench_starterkit.git
```

Answer the questions:

```bash
  [1/13] workbench_project_name (cool_wb): 
  [2/13] workbench_module_name (cool_wb): 
  [3/13] workbench_class_name (CoolWorkbench): 
  [4/13] workbench_menu_text (cool workbench): 
  [5/13] workbench_tooltip (FreeCAD workbench to make cool parametric objects): 
  [6/13] workbench_icon (cool.svg): 
  [8/13] workbench_maintainer_name (me): 
  [9/13] workbench_maintainer_email (me@foobar.com): 
  [10/13] workbench_project_url (https://foobar.com/me/coolWB): 
  [11/13] workbench_description (The cool WB creates cool parametric objects): 
  [12/13] workbench_dependencies ('numpy',): 
  [13/13] workbench_version (0.1.0): 
```

Voila, the workbench has been created in a directory under the current directory:

```bash
$ find cool_wb/
```

Shows...

```bash
cool_wb/
cool_wb/setup.py
cool_wb/docs
cool_wb/docs/HISTORICAL_README.md
cool_wb/docs/commands.md
cool_wb/MANIFEST.in
cool_wb/freecad
cool_wb/freecad/cool_wb
cool_wb/freecad/cool_wb/init_gui.py
cool_wb/freecad/cool_wb/translate_utils.py
cool_wb/freecad/cool_wb/version.py
cool_wb/freecad/cool_wb/__init__.py
cool_wb/freecad/cool_wb/my_numpy_function.py
cool_wb/freecad/cool_wb/resources
cool_wb/freecad/cool_wb/resources/cool.svg
cool_wb/freecad/cool_wb/resources/translations
cool_wb/freecad/cool_wb/resources/translations/{{cookiecutter.workbench_module_name}}_es-ES.ts
cool_wb/freecad/cool_wb/resources/translations/update_translation.sh
cool_wb/freecad/cool_wb/resources/translations/{{cookiecutter.workbench_module_name}}_es-ES.qm
cool_wb/README.md
cool_wb/LICENSE
```

### Install the workbench

The easiest way (I've found) to install a newly created workbench is to just symlink it into the `Mod` directory.

```bash
# cd to the Mod directory of your FreeCAD installation]
cd [FreeCAD installation directory]/Mod
ln -s [path to the created workbench] CoolWB
cd ..
./bin/FreeCAD
```

Look for the workbench in the FreeCAD -> View -> Workbenches, it should be there.

## Documentation

For much deeper documentation, see the generated docs/HISTORICAL_README.md.

## For Installation into FreeCAD source

1. Add option to build this app here

cMake/FreeCAD_Helpers/InitializeFreeCADBuildOptions.cmake
```cmake
option(BUILD_COOLWB "Build the FreeCAD CoolWB module" ON)
```

2. Condition on that option here

src/Mod/CMakeLists.txt
```cmake
+if(BUILD_COOLWB)
+    add_subdirectory(CoolWB)
+endif(BUILD_COOL_WB)
```

## For Installation into the AddOnManager

See instructions here:
https://github.com/FreeCAD/FreeCAD-addons/blob/master/README.md


## Maintainer

ToddG : freecad.ascension109@passinbox.com