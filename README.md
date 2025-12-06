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

`build/libs/SchemConvert-1.3.0-all.jar`

## Batch Converter Tool

The project includes a Python helper script to mass-convert files, which can be built into a standalone executable.

### Building the Executable

**Requirements:**

- Python installed
- `pyinstaller` installed (`pip install pyinstaller`)

To build the executable, run the provided batch script:

```batch
.\build_executable.bat
```

This will create `convert_all.exe` inside `build_artifacts\dist\`. This folder is excluded from git to keep the repository clean.

### Batch Tool Usage

The batch converter recursively scours directories for schematic files and converts them using the main `SchemConvert` JAR.

**Syntax:**

```bash
convert_all.exe -j <path_to_jar> [options]
```

**Options:**

- `-j`, `--jar`: Path to the `SchemConvert` JAR file (Required).
- `-d`, `--directory`: Root directory to scan for files (Default: current directory).
- `-o`, `--output`: Directory to save converted files (Default: same as input).
- `-e`, `--extensions`: Comma-separated list of extensions to convert (Default: `.schem,.schematic,.nbt,.dp`).

**Example:**

```bash
convert_all.exe -j SchemConvert-1.3.0-all.jar -d ./my_schematics -o ./converted_blueprints
```
