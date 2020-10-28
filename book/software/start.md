# Software

We have a large amount of software installed on both ARC3 and ARC4. These are available through the module system which allows users to load the specific software they need for their work.

On both ARC3 and ARC4 software is broken up into 4 categories:

- Applications - Software applications
- Infrastructure - Common libraries available to your programs and applications
- Compilers - Compilers and interpreters for a range of languages
- Libraries - Useful system utilities

## Module system

A large number of applications are available through the module system and can be loaded with the `add` command, in this example where `name_of_module` is the name of the module you wish to load:

```bash
module add name_of_module
```

By default this will load the latest (highest version number) of the software available. To use a specific version number, you should explicitly state this in the module statement, so to use AMBER v12, specify:

```bash
module add amber/12
```

To see a full list of the available modules use:

```bash
module avail
```

You can also find the modules you currently have loaded with the module command `list`, for instance:

```bash
module list
```

```{note}
Loaded modules are specific to a given login session of your shell. This means you'll find modules you've loaded previously are not automatically loaded when you next login. You can automatically load a module when you login by adding the `module add name_of_module` line to bottom of your `~/.bashrc`.
```

You can also remove modules with the `remove` command, in this example `name_of_module` is the name of the module we wish to remove:

```bash
module remove name_of_module
```

Sometimes we want to switch a loaded module for another, for instance we might want to swap the automatically loaded intel compiler for a gnu compiler. We can do this with the `switch` command:

```bash
module switch intel gnu/6.3.0
```

If you require additional software or applications installing, please [contact us](https://leeds.service-now.com/it?id=sc_cat_item&sys_id=48d5a6d70f275f00a82247ece1050ea0). However, we do not install all software as modules and may provide you guidance about how to install your desired application yourself.