# Linux commands that helps.
---
## 1. Tee
Reads from standard input and write to standard output and files

*Usage : *
``` ls | tee [OPTIONS] [FILENAME] ```

## 2. *python -u*
-u is used to force stdin, stdout and stderr to be totally unbuffered, which otherwise is line buffered on the terminal

*Usage : *
``` python -u python_run.py > filename.txt ```
To save the output as soon as the output is in stdout
