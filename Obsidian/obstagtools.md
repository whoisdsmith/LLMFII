---
tags:
  - "#python"
  - "#developer-tools"
  - "#software-development"
  - "#open-source"

  - "#obsidian"
  - "#markdown"
  - "#yaml"
---
# Obsidian Tag & Metadata Tools (`obstagtools`)

Some tools for working with [Obsidian.md][Obsidian]-flavor (YAML frontmatter + Markdown content) notes files.

**This should be considered 'developer-grade' software, and almost certainly has bugs.**
Problem reports and pull requests welcome.

This project is packaged with [Poetry][Poetry].
You may want to refer to the [Python Poetry Cheat Sheet][ppcs] for commands; taking advantage of Poetry
requires that you have it installed (verify with `poetry --version`), after which you should be
able to run `poetry install` and have it download all required dependencies.

To run a particular tool, simply execute `poetry run SCRIPTNAME.py`, where `SCRIPTNAME.py` is the filename
of the tool you wish to run (e.g. `obs-filter-vault.py`), followed by its required arguments and options.

[Obsidian]: https://obsidian.md/
[Poetry]: https://python-poetry.org/
[ppcs]: https://gist.github.com/CarlosDomingues/b88df15749af23a463148bd2c2b9b3fb

## obs-add-tag.py

Simple, quick-and-dirty tool for batch-adding tags to a Markdown document,
meant for scripting.

Minimal dependencies: only `sys`, `argparse`, and `logging`.

### Usage  

```Text
usage: add_tag.py [-h] [--tag TAG [TAG ...]] [--debug] inpath [outpath]

Add YAML frontmatter tags to Obsidian-style Markdown files

positional arguments:
  inpath                Input file to add tags to
  outpath               Output file to write to (in-place modification if not given)

optional arguments:
  -h, --help            show this help message and exit
  --tag TAG [TAG ...], -t TAG [TAG ...]
                        Tag values to add to the document
  --debug               Enable debug mode (verbose output)
```

**Effect**:  
- _Prepends_ one or more specified tag values (`tag1`, `tag2`) to the list of tags in the YAML frontmatter.

Note that there are two distinct modes of operation, "in-place" and "copy-on-write".
Copy-on-write, where the user supplies an output file path, is _significantly safer_ 
and does not write to the target file (`targetfile.md` in the examples below) at all.

- In-place modification: `./add_tag.py targetfile.md -t tag1 tag2`  
- Copy-on-write (safer!): `./add_tag.py targetfile.md copyfile.md -t tag1 tag2`

Tags can be either single-level (e.g. `cats`) or nested (`predators/cats`).
If a desired tag contains spaces, enclose it in double-quotes;
otherwise, tags are assumed to be space-delimited.

Although specifying one or more tags with `--tag` or `-t` is _technically_ optional,
(and the tool will exit with status 0 if none are given), it's not especially useful.
In practical terms, it's a required argument.

### Scripted Use Example

Example goal: add some tags to all Obsidian Markdown (`*.md`) files, 
starting in a specified directory, recursively,
that are 'newer' (have a more recent `mtime`) than a specified file:

```shell
find ~/MyVault.obs/ \
-type f \
-name "*.md" \
-newer ~/MyVault.obs/Travel/san-diego-departure.md \
-exec /path/to/obstagtools/add_tag.py {} -t vacation places/sandiego \;
```

## obs-filter-vault.py

Copy or move documents from an existing Obsidian vault into a new, similarly-structured folder tree.
Useful for "filtering" a vault's contents, creating a copy that only contains (or excludes) documents with a specified
metadata field:value.

### Usage

```Text
usage: obs-filter-vault.py [-h] [--attachments] [--force] [--debug]
                           inpath outpath {COPY,MOVE} filterfield
                           {EXCLUDE,INCLUDE} fieldvalue

Filter an Obsidian vault based on document metadata

positional arguments:
  inpath             Source vault path
  outpath            Destination path (must be empty unless --force is used)
  {COPY,MOVE}        Command to execute
  filterfield        Metadata field to filter by (e.g. "tags")
  {EXCLUDE,INCLUDE}  Whether output must INCLUDE or EXCLUDE the specified
                     field value from output set
  fieldvalue         Field value (e.g. "personal")

optional arguments:
  -h, --help         show this help message and exit
  --attachments, -a  Copy attachments (from ATTACHMENT_DIRS) linked by output
                     document set
  --force            Perform operation even if outpath is not empty (WARNING:
                     will clobber!)
  --debug            Enable debug mode (verbose output)
```

### Use Cases

#### Create Vault Without Personal Files

**Scenario:** I have a Obsidian Vault full of work notes, `Worknotes/` that I would
like to pass along to a colleague, _except for_ the notes that are specifically tagged as 'personal' 
(i.e. they have a YAML frontmatter field named `tags` which contains the value `personal`).

```shell
$ obs-filter-vault.py Worknotes/ Worknotes-filtered/ COPY tags EXCLUDE personal --attachments
```

This command reads recursively from `Worknotes/`, writes to `Worknotes-filtered/`,
and will `COPY` notes _except_ if they have a metadata field `tags` with a value `personal`, in which case they
will be **excluded** (due to the `EXCLUDE` option) from the copy.
Because of the `--attachments` option, it will also copy those files located in specified Attachments directories
(default: `Attachments/`, inside the input vault)
which have links to them from documents in the output set.

#### Extract Personal Files From Vault

**Scenario:** Similar to the above, I have a `Worknotes/` vault containing some notes tagged 'personal'.
But this time, I'd like to _move_ those personal notes out of Worknotes and into a new directory tree, rooted
at `Personal.obs` (which must either not exist, or be empty, unless `--force` is selected).

```shell
$ obs-filter-vault.py Worknotes/ Personal/ MOVE tags INCLUDE personal
```

This command `MOVE`s notes meeting the criteria (`tags INCLUDE personal`), so any note tagged as 'personal'
in its frontmatter will be moved out of Worknotes and into Personal.
Note that the `.obsidian` directory (containing Vault-specific settings, caches, etc.), `Attachments`, and `Templates`
are _not copied_ or moved by default.

## obs-add-taxonomy.py

This tool updates the metadata fields in an Obsidian document's frontmatter
to match the fields provided in a 'taxonomy' file (by default named `metadata.yaml`
and located in the working directory).

Requires `oyaml` (try `pip install oyaml`).
Future versions will probably switch to `ruamel.yaml` instead.

### Operation

The following rules are used when combining metadata from the document and the
taxonomy file:

- If a field is in the taxonomy _and_ the document frontmatter, include it in the output and and use the document value
- If a field is in taxonomy _but not_ in the document frontmatter, include it and use the taxonomy value
- If a field is in the document frontmatter _but not_ in the taxonomy, then the behavior depends on whether the `--clean` flag is set:
  - IF NOT `--clean`: Include the field and use the document value in the output, effectively passing it through (this is normal operation!)
  - IF `--clean`: Remove the field from the output (destructive operation!)

In short, selecting `--clean` will remove any extraneous metadata from the output, and ensure that the only fields contained in the output's frontmatter are those fields in the taxonomy.

### Usage

Similar to `add_tag.py` (see above), `add_taxonomy.py` can either write to a specified output file, or if one is not provided, it will do an in-place modification of the input file.
This is provided for ease of updating large Obsidian vaults via scripts, but use carefully, and make a backup of the entire vault (if you are not using version control) before starting!

The `--taxonomy` or `-T` argument is optional, and if used should be a path to a taxonomy file, which is basically just a freestanding Obsidian frontmatter section.
If this argument is not supplied, the tool defaults to looking for `metadata.yaml` in the working directory.
An example `metadata.yaml` is provided, and can be used as a starting point for modification.

The `--clean` option is discussed in detail above; if used, it will strip any additional fields that may exist in the input document from the output, if they are not included in the taxonomy.
This might be useful when preparing documents for publication online, but it is off by default.
The default behavior passes through _all_ metadata on the input document, adding fields in order to ensure it conforms to the taxonomy (i.e. all documents' fields will be a superset of the taxonomy).

The `--noindent` option stops the tool from adding two spaces to the beginning of every nested YAML sequence (in Python terms, a list) that is inside a top-level mapping (Python dict).
For Obsidian documents, this mostly affects the `tags` field, which I use with a two-space indent for readability.
Selecing this option results in the output from `yaml.dump()` being written to the output unmolested.

```Text
usage: add_taxonomy.py [-h] [--taxonomy TAXONOMY] [--clean] [--noindent] [--debug] inpath [outpath]

Reformat Obsidian frontmatter to conform to a specified taxonomy

positional arguments:
  inpath                Input file to read from
  outpath               Output file to write to (if not provided, modify input file in-place)

optional arguments:
  -h, --help            show this help message and exit
  --taxonomy TAXONOMY, -T TAXONOMY
                        YAML taxonomy file (default: metadata.yaml)
  --clean               Remove all input document fields not present in taxonomy (DESTRUCTIVE!)
  --noindent            Do not indent YAML sequences (may break other tools)
  --debug               Enable debug mode (verbose output)
```

## obs-wikify-yake.py
**Very experimental** auto-keyword-linking tool, which uses YAKE to extract keywords from an Obsidian document's
content, and then makes occurrences of each keyword into Obsidian-style [[double bracket]] links.
The intended use is for creating knowledge graphs and finding unknown linkages between documents, but it is not
well-suited for that purpose yet.

### Usage

```Text
usage: obs-wikify-yake.py [-h] [--debug] inpath [outpath]

Use YAKE to make wikilinks from [[keywords]] in an Obsidian document

positional arguments:
  inpath      Input file to read from
  outpath     Output file to write to (if not provided, modify input file in-place)

optional arguments:
  -h, --help  show this help message and exit
  --debug     Enable debug mode (verbose output)
```

### Limitations

Currently this tool only analyzes a single document for keyword extraction, so there's no guarantee that keywords found in one document will be found anywhere else, limiting the usefulness of the internal wiki-style links it generates.
Also, it has some significant flaws and limitations:

- If a keyword consists of multiple words (which happens if `MAX_KEYWORD_SIZE` > 1) and it's broken across more than one line in the text, it won't be linked.
- Also if `MAX_KEYWORD_SIZE` > 1, it is possible for one keyword to be a subset of another (e.g. 'memory allocation' and 'memory' might both be extracted as keywords from the same document), which will result in nested wikilinks in the output (e.g. "The buddy [[[[memory]] allocation]] technique"), which Obsidian doesn't like.

While of admittedly limited utility as a standalone program, the `get_keywords()` function might be useful for other, more complex applications, like building up a list of keywords across multiple documents prior to wikification.

## General Info

### Required Structure

The specified input file(s) must be "well formed" YAML+Markdown documents, consisting of: 

- The string `---\n` (that's three hyphens, followed by a line ending character such as LF), **and nothing else**, on the first line of the file; followed by 
- YAML data, specifically containing a sequence named 'tags' with one or more values, represented using block-style YAMP (_not_ flow!) syntax_; then
- Another `---` on a line by itself (note this is _not_ valid YAML, and marks the end of the YAML frontmatter)
- The content, formatted with Markdown
- EOF

### YAML Block vs. Flow Style

**YAML Block Style**  
This is the style I use for all Obsidian tags.

```yaml
---
tags:
  - toys
  - gifts
---
# Heading
Content begins here...
```

**YAML Flow Style**  
Alternative, compact style that is still valid YAML, but handling
it is not a very high priority for these tools. 
This is particularly the case for the tools
designed to have minimal dependencies, which don't have an actual
YAML parser.

```yaml
---
tags: [toys, gifts]
---
# Heading
Content begins here...
```
