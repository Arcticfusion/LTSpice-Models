# LTSpice Resources

These are resources that I have made to simulate components in LTSpice.

Models are based on datasheets and PSpice models. No guarantees that the models behave as expected.

This resource is intended for educational purposes.

## 1. Data Sources

Resources have been created using instructions from [this tutorial](http://www.simonbramble.co.uk/lt_spice/ltspice_lt_spice_tutorial_6.html) by Simon Bramble.

All datasheets have been found publicly online. You can find the specific referenced files in `references.md`.

To get the original PSpice files, you need access to the PSpice application. You can get a trial [here](https://www.orcad.com/pspice-free-trial). It is only available for Windows machines.

## 2. Adding Resources to LTSpice

Models and Libraries can be inserted into a single project or they can be added to the default libraries. To add to a file, simply add a `SPICE directive` element to your circuit `.asc` file. Locate the file that contains the required resource. Then input the following, modifying the path and file name as necessary. Note, a local path originates from the directory the circuit file is located.

```SPICE
.include local/path/to/file.spi
```

OR

```SPICE
.include /absolute/path/to/file.spi
```

To add to the default library, you will need to find the application data for LTSpice.

On MacOS: `~/Library/Application Support/LTSpice/`
On Windows: `\???`

Consider this the root directory for the following instructions.

### 2.1 Adding Symbols `.asy`

When adding an independent symbol from a `.asy` file, just put a copy of the file in `lib/sym/`. You can add subfolders as desired. All are accessible inside LTSpice's component picker.

### 2.2 Adding Libraries `.lib`

When adding a `.lib` file, these can be added a couple different ways.

For single line models, there is likely a default library that can be modified. Simply add the line to the file.

For a contrived single line example:

```SPICE
.model EXAMPLE_MODEL CONSTRUCTOR(a=1 b=2 c=3)
```

These models can be found in `lib/cmp` where there are several `standard.<extension>` files. Each extension is a different component type. Each component type has its own `CONSTRUCTOR()` which you can observe in the file. Any models added to these files should also use the same constructor.

If any of the default libraries have been modified, the application will need to be restarted to access these values.
