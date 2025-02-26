# Introduction to Bash Scriptiong

## Shebang (`#!`)

A **shebang** (`#!`) is the first line in a script that tells the operating system which interpreter to use to execute the script.

### Syntax
```bash
#!/path/to/interpreter
```
- The `#` symbol starts a comment, but when combined with `!`, it signals the system to use a specific shell or interpreter.<br>
- The path after `#!` should point to the executable of the interpreter.

### Common Shebangs
| Shebang | Interpreter |
|---------|------------|
| `#!/bin/bash` | Bash shell |
| `#!/bin/sh` | Bourne shell (generic shell) |
| `#!/usr/bin/python3` | Python 3 interpreter |
| `#!/usr/bin/perl` | Perl interpreter |

### Examples
```bash
#!/bin/bash
echo "This script runs using Bash!"
```

---


