# minimal-zet

Create notes with minimal effort and maximal searchability.
This is a minimal version of [cmd-zet](https://github.com/rwxrob/cmd-zet).

Note: 💥 cmd-zet is deprecated: [keg/kn](https://github.com/rwxrob/keg) is the successor.

# What does it?

Each note creation triggers the creation of a folder with the current timestamp as name. In the folder, a `Readme.md`-"master"-file gets created, where you can write your notes, and give it a title. Additionally, you can add any files, like screenshots or audio files into the same folder. This goes very nicely with the Zettelkasten-method, but also with the search of remote repository platforms like github or gitlab.

# How to use it?

## Step 0 Dependencies
- Make sure, you installed `Bash 4.0` and `pandoc`

## Step 1 Create git-repositories and corresponding bash variables
- Each directory with your notes (or zettels in a Zettelkasten) has to be a git-repository. For short, we will refer to all those directories as `zet`-directories. If you do not want to use a remote repository in the internet, you can initialize one on your machine with `git init --bare`, see https://stackoverflow.com/a/31590993. 
- Each `zet`-directory has to have an initialized config-variable by `${CONF[zet.<directory name>] := <directory path>}`. Look at the `private`-`zet`-directory in the `zet`-code for example.
- After this setup, you are ready to use the `minimal-zet`-tool

---

## CRUD operations:
- Change current `zet`-directory by `zet use <directory name>` (Now all commands affect the current `zet`-directory. If you forgot in which one you are, you can check by `zet current`)
- Create a new note by `zet create <note name>`. After you saved the file, a git-commit is automatically triggered
- The same holds for `zet delete <note name>`
- Analogously, you can edit a note by `zet edit <note name>` or `zet edit <timestamp>`. If nothing changed, nothing gets committed.

- You can check the total number of notes in the current `zet`-directory by `zet count`

## Searching:

- By `zet find <xyz>` you can trigger a pcre-search for `xyz` in the note titles
- More sophisticated search options have to be added... For now, you can always jump in the current `zet`-directory and "`grep`" your way to your notes. For that I suggest aliases of the form `zet use <directory.name> && cd <directory>` in your `.zshrc`/`.bashrc`.

# Changes summary

Contains the minimum of "core" functionalities of `cmd-zet`. The following things changed:
- All video casting features for youtube are removed (This removes the dependency on `yt`)
- `zet`-directories are matched exactly and not partly when switching the current `zet`-directory (e.g. "zet.work" and "zet.work1" are different)
- category-features are removed. You do not need fancy categories, if you have an awesome search
- URL-features are removed

# Legal

Copyright of the original code belongs to Rob Muhlestein rob@rwx.gg  
Released under Apache-2.0 License  
See also https://youtube.com/rwxrob  
