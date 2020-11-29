# Python intersting extra commands or chunks of codes for easier access in future

## 1. options -u and -m
-u 
:is used to force stdin, stdout and stderr to be totally unbuffered, which otherwise is line buffered on the terminal
*Usage*
``` python -u python_run.py > outfile.txt ```

-m 
:searches sys.path for the named module and runs the corresponding .py file as a script. An example would be timeit module. 
The command python -m timeit "python script" would return the time taken for the script to execute.
