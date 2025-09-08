# info Command-Line Tool

`info` is a simple command-line tool for saving short pieces of information to markdown files.

**Version: 1.0**

## Usage

There are three ways to use the `info` tool:

### 1. Appending to the common file

To append a sentence to the default `common.md` file, simply provide the sentence as an argument:

```bash
info Your sentence here
```

This will append "Your sentence here" to the file located at `~/Development/info/common.md`.

### 2. Appending to a specific file

To append a sentence to a specific markdown file, provide the filename (ending with `.md`) as the first argument, followed by the sentence:

```bash
info yourfile.md Your sentence here
```

This will append "Your sentence here" to the file located at `~/Development/info/yourfile.md`.

To work with a file in the current directory, prefix the filename with `./`:

```bash
info ./yourfile.md Your sentence here
```

### 3. Showing file content

You can also use the `info` tool to display the content of the markdown files.

#### a. Showing the common file

To show the content of the default `common.md` file:

```bash
info show
```

To search for specific words within the `common.md` file, provide them as a search string after the `show` command. The search is case-insensitive and will show lines that contain at least one of the words.

```bash
info show "your search string"
```

#### b. Showing a specific file

To show the content of a specific markdown file, provide the filename as the first argument, followed by `show`:

```bash
info yourfile.md show
```

Similarly, you can search within a specific file by providing a search string after `show`:

```bash
info yourfile.md show "your search string"
```

To show a file in the current directory, prefix the filename with `./`:

```bash
info ./yourfile.md show
```

### 4. Getting help

To see the tool's syntax and options, use the `help` command:

```bash
info help
```

### 5. Editing files

You can open the common file or a specific file in the `nano` editor.

#### a. Editing the common file

To edit the `common.md` file:

```bash
info edit
```

#### b. Editing a specific file

To edit a specific markdown file:

```bash
info yourfile.md edit
```

To edit a file in the current directory, prefix the filename with `./`:

```bash
info ./yourfile.md edit
```

## Output

- If the information is saved successfully, the tool will output: `Saved to: filename.md`
- In case of an error, an error message will be displayed in red.

## Development Workflow

The `info` script is located in `/usr/local/bin/`. To make changes:

1.  Copy the script from `/usr/local/bin/info` to this directory (`/Users/hans-jorgjodike/Development/Info/src`).
2.  Make your changes to the local copy.
3.  Copy the modified script back to `/usr/local/bin/info`.

**Note:** I have remembered the development workflow, so you don't have to repeat it every time.
