---
aliases:
  - lava
tags:
  - obsidian-plugin
  - markdown
  - template
---
# LAVA MARKUP GENRATION TOOL
Lava is a markup generation tool built for obsidian
Version: 0.0.5
creator: Joshua Davis

**STILL IN VERY EARLY DEVELOPMENT**
**NOT RECOMMENDED FOR PERSONAL USE**

> open lava-about in obisidian for developer information on the development of LAVA

```
npm i lava-md -g
```

## Inline Lava
all inline lava starts with **%%|** and ends with **|%%**.

form:
%%| params call -> lifecycle |%%

### params
a inline json object to be passed into to call function
```
ex: {
    "hello": "world"
}
```

### call
a call is a name of a template that will be injected under the inline lava

### lifecycle
the lifecycle of a inline lava tells the parser weather to ignore, delete, or update the data.

implemented now are...

pre-render (will be rendered once and turn into a rendered tag. same as if left blank)
rendered (will never be updated. Data already rendered)
auto (data will be updated whenever the file is saved and lava run is called again)

ex: %%| {"hello", "world"} make_title -> auto |%%

## Lava Templates

templates use the extension .lava
templates will be copied under inline lava tags and end with a %%| end |%% tag.

lava template data use a different starting and ending tags for injecting data of "%%!" and "!%%"

### Basic parameters
to inject paramaters into inline lava use the params json object

// passed into inline call
```json
{
    "cool": {
        "hello": "world"
    },
    "apples": ["Red", "Green", "Fuji"],
    "people": ["Josh", "John", "Alice"]

}
```
// inside a .lava template
ex: %%! params.cool.hello !%%

### Objects

Inline calls allow you to concatenate objects to your input objects 

// passed into inline call
```json
{
    ...(apples.json), 
    "people": ["Josh", "John", "Alice"],
    "name": "John"
}
```

concatinating objects happens at runtime and updates everytime the object is run.
This allows persistent data to be used in mutiple template calls.

### Looping
// loop over arrays
```
%%!FOR apple in params.apples {
    I like %%! apple !%% apples!
}!%%
```

>output:
>I like Red apples!
>I like Green apples!
>I like Fuji apples!

//nested for loops
```
%%!FOR apple in params.apples {
    %%!FOR person in params.people {
        %%! person !%% like's %%! apple !%% apples!
    }!%%
}!%%
```
### Conditionals
Currently the only conditionals supported in templates are simple IF statements
```
%%!IF apple == "Red" {
    APPLE IS RED!
}!%%
```
### Scripts
**Not Implemented Yet**
Scripts **ONLY** run when run by *lava script* or in *lava-watch* interface.
They do **NOT** run when the template is called.
```
%%# o/apples.json
    PUSH apples.types "round" 
    ADD job "Apple picker"
    ADD favorite %%!apple!%%
    RUN create-apple-tree 
#%%
%%# n/cs170/%%!apple!%%
    RUN create-apple-tree apples.json
#%%
```

### Comments
%%@ hello this is a comment in a .lava file @%%

## Executing Commands
run:
```bash
lava run # after init
lava run -n [notes-directory] -t [templates-directory]
lava run -n [notes-directory] -t [templates-directory] -o [objects-directory]
```
- runs lava on notes directory with templates 

watch:
```bash
lava watch # after init
lava watch -n [notes-directory] -t [templates-directory]
lava watch -n [notes-directory] -t [templates-directory] -o [objects-directory]
```
- runs lava run periodically (on changes)
- shows terminal that allows you to run lava scripts

init:
```bash
lava init # prompts user to input directories
lava init -n [notes-directory] -t [templates-directory] -o [objects-directory]
```
- run in encapsulating directory and sets up paths to directories

**Not Implemented yet**

script:
```bash
lava script [script-name] [args...]  # runs a template script
```