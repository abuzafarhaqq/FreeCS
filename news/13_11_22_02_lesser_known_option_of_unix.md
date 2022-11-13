### Lesser known option in Linux

---

### Recursive Directory Creation and Saving Permission with mkdir
we often use `mkdir` to create folders. We can create multiple dirs at once.
```mkdir -p api/filesystem/impl```
we can create multiple dirs under one dirs.
```mkdir -p api/{filesystem,os,process}/{impl,include}```
It'll create like,
api
  1. filesystem
    - impl
    - include
  2. os
    - impl
    - include
  3. process
    - impl
    - include
Now we can skip using `chmod` for newly created dirs by using `-m` options.
```mkdir -m 777 public```

## Running Python Code from Bash Scripts
Bash doesn't offer modern language features, and we can't operating system C APIs directly in Bash. Therefore, some developers tend to write automotion scripts in Python/NodeJS because of these drawbacks in Bash.
We can create a subshell and start python interpreter and get output to bash:
```sh
#!/bin/bash
a=10
b=20
code="
import json;
print(json.dumps({'a':$a,'b':$b},
indent=2))
"
json=$(python3 -c "$code")
# Use json content
echo -e "$json" >output.json
```
This script uses python to generate a pretty printed json document from several bash variables. In python 3.9 we can use `--indent` switch for `json.tool` module to pretty-print JSON:
```
echo '{"a":10}' | python3 -m json.tool --indent 2
```
similarly, we can use any language interpreter. example: `node -e` to run javascript within bash.


