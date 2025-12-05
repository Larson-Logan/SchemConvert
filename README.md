# SchemConvert

A lightweight and powerful tool to convert between different Minecraft schematic formats.

**This tool requires Java 21 or later.**

## Supported Formats

- **`.nbt`**: Vanilla Minecraft Structure blocks.
- **`.schem`**: Modern Sponge schematic format (used by WorldEdit, MCEdit Unified).
- **`.litematic`**: Litematica mod format.
- **`.bp`**: Axiom mod blueprints.
- **`.schematic`**: Legacy MCEdit/WorldEdit format (Supports reading & writing).

## Features

- **Cross-Format Conversion**: Convert freely between any of the supported formats.
- **Legacy Support**: Full support for reading and writing the classic `.schematic` format, automatically handling block ID to BlockState conversions using built-in mappings.
- **CLI & GUI**: Run from the command line for batch processing or automation, or launch without arguments for a graphical interface.

## Usage

### Command Line Interface (CLI)

Run the tool from the terminal:

```bash
java -jar build/libs/SchemConvert-1.2.5-all.jar -input <input_file> -format <output_format> -output <output_file>
```

**Arguments:**

- `-input`: Path to the source file to convert.
- `-format`: (Optional) Desired output format/extension (e.g., `schem`, `litematic`, `bp`, `nbt`, `schematic`). If omitted, it attempts to infer from the output filename.
- `-output`: (Optional) Path for the converted file. If omitted, saves to the same directory with the new extension.

**Examples:**

Convert a legacy file to a modern Sponge schematic:

```bash
java -jar SchemConvert.jar -input house.schematic -format schem -output house.schem
```

Convert a Litematic to Axiom Blueprint:

```bash
java -jar SchemConvert.jar -input castle.litematic -format bp
```

### Graphical User Interface (GUI)

Simply double-click the JAR file or run it without arguments:

```bash
java -jar SchemConvert.jar
```

## Building from Source

To build the project yourself, clone the repository and run the Gradle build command:

```bash
./gradlew build
```

The executable JAR file will be generated at:
`build/libs/SchemConvert-1.2.5-all.jar`
