## _Sindel_

---

Sindel is a bash script that watches your project's source for changes and runs any command on file changes.

> It's more generic than cargo-watch or nodemon in that it isn't language specific.

### Installation

> @note the script depends on the [fd](https://github.com/sharkdp/fd/releases/tag/v10.3.0)
> Its preferred over the gnu `find` due to parallelism support

---

```bash
url=""

[[ -d "${HOME}/.local/bin/" ]] && curl --create-dirs --output "${HOME}/.local/bin/sindel" "$url"

chmod u+x ~/.local/bin/sindel
## Add path to shell config file
## i.e
## echo "export PATH="${PATH}:/${HOME}/.local/bin/" >> config_file

```

### Usage

---

```bash
nodemon start

## Replaced with
sindel -l js \
  -c "nodemon" \
  -s "start"

cargo-watch -x "clippy" \
  -x "build" \
  -x "test" \
  -x "fmt"

  ## with
sindel -l rs \
     -c "cargo" \
     -s "build" \
     -s "test" \
     -s "run"

## Multi-lingual project
sindel -l rs \
  -l hs \
  -l make \
  -l js \
  -c "cargo check "\
  -c "make build" \
  -c "cabal build" \
  -c "npm start"

  ## Could also customize the search interval if its too fast
  # Changed watch interval from the default=7 -> 20seconds
   sindel -l make \
   -i 20
```
