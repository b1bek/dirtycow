# dirtycow

This exploit uses the pokemon exploit of the dirtycow vulnerability as a base and automatically generates a new passwd line.
The user will be prompted for the new password when the binary is run.
The original /etc/passwd file is then backed up to /tmp/passwd.bak and overwrites the root account with the generated line.
After running the exploit you should be able to login with the newly created user.

To use this exploit modify the user values according to your needs.

The default user being created is `root`.

Original exploit (dirtycow's ptrace_pokedata "pokemon" method):
  https://github.com/dirtycow/dirtycow.github.io/blob/master/pokemon.c

Compile with:

```bash
gcc -pthread dirty.c -o dirty -lcrypt
```
If any error then try this and re-compile as above:
```bash
PATH=$PATH:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/lib/gcc/x86_64-linux-gnu/4.8/;export PATH
```

Then run the newly create binary by either doing:
```bash
./dirty
```

or

```bash
 ./dirty my-new-password
 ```
Afterwards, you can either `su firefart` or `ssh firefart@...`

**DON'T FORGET TO RESTORE YOUR /etc/passwd AFTER RUNNING THE EXPLOIT!**

```bash
mv /tmp/passwd.bak /etc/passwd
```

Exploit adopted by Christian "FireFart" Mehlmauer

https://firefart.at
