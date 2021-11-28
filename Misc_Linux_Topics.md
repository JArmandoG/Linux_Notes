To-do:
* Include ROP C Man Pages
* Include source, Logic operators, stdout/stderror, $, $_, $?, !!, etc. Process substitution operations, piping & redirectors.

---

## General use Debuggers & profilers:

**GDB : PWNDBG**

Python application -> Github -> Activation via .gdbinit

**PYTHON DEBUGGERS**

1.- PDB

- Default python debugger

```
pdb my_program.py
```

2.- IPDB 

- **I**mproved pdb

```bash
pip3 install ipdb

Run:
python -m ipdb my_program.py
```

**(PYTHON) LINTERS - vim + python**

(ALE TOOLS):

- Install i.e. flake8 or pyflake
- .vimrc -> ale tools (Plug 'w0rp/ale')
- .vimrc configured
- `ALEToggle` (on/off)

### Time - user/real/sys

```bash
user@host:~/code$ cat time.py
#!/usr/bin/python

import time

time.sleep(7)
user@host:~/code$ time python3 time.py

real	0m7.034s
user	0m0.023s
sys	0m0.008s
```

**PERF: Tracing Program stats:**

```bash
root : /home/user/code >> perf stat python3 shell.py
# sleep 2
# exit

 Performance counter stats for 'python3 shell.py':

             39.02 msec task-clock                #    0.003 CPUs utilized          
                27      context-switches          #    0.692 K/sec                  
                 9      cpu-migrations            #    0.231 K/sec                  
             1,758      page-faults               #    0.045 M/sec                  
        45,658,036      cycles                    #    1.170 GHz                    
        43,580,502      instructions              #    0.95  insn per cycle         
         9,649,258      branches                  #  247.296 M/sec                  
           428,845      branch-misses             #    4.44% of all branches        

      13.585309315 seconds time elapsed

       0.033763000 seconds user
       0.006815000 seconds sys
```
