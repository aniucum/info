### How to Exit When Errors Occur in Bash Scripts
- https://www.geeksforgeeks.org/how-to-exit-when-errors-occur-in-bash-scripts/

### Understanding and Ignoring Errors in Bash
- https://www.geeksforgeeks.org/understanding-and-ignoring-errors-in-bash/

### What does `set -x` do?
- https://stackoverflow.com/questions/36273665/what-does-set-x-do
```
set -x enables a mode of the shell where all executed commands are printed to the terminal. In your case it's clearly used for debugging, which is a typical use case for set -x: printing every command as it is executed may help you to visualize the control flow of the script if it is not functioning as expected.

set +x disables it.
```

### Automatic exit from Bash shell script on error [duplicate]
- https://stackoverflow.com/questions/2870992/automatic-exit-from-bash-shell-script-on-error
Use the set -e builtin:
```
#!/bin/bash
set -e
# Any subsequent(*) commands which fail will cause the shell script to exit immediately
```
Alternatively, you can pass -e on the command line:
```
bash -e my_script.sh
```
You can also disable this behavior with set +e.
You may also want to employ all or some of the the -e -u -x and -o pipefail options like so:
```
set -euxo pipefail
```
-e exits on error, -u errors on undefined variables, -x prints commands before execution, and -o (for option) pipefail exits on command pipe failures. Some gotchas and workarounds are documented well here(https://vaneyckt.io/posts/safer_bash_scripts_with_set_euxo_pipefail/).
(*) Note:
```
The shell does not exit if the command that fails is part of the command list immediately following a while or until keyword, part of the test following the if or elif reserved words, part of any command executed in a && or || list except the command following the final && or ||, any command in a pipeline but the last, or if the command's return value is being inverted with !
```
### Get current directory or folder name (without the full path)
- https://stackoverflow.com/questions/1371261/get-current-directory-or-folder-name-without-the-full-path
```
result=${PWD##*/}          # to assign to a variable
result=${result:-/}        # to correct for the case where PWD=/

printf '%s\n' "${PWD##*/}" # to print to stdout
                           # ...more robust than echo for unusual names
                           #    (consider a directory named -e or -n)

printf '%q\n' "${PWD##*/}" # to print to stdout, quoted for use as shell input
                           # ...useful to make hidden characters readable.
```

### Bash For Loop Array: Iterate Through Array Values
- https://www.cyberciti.biz/faq/bash-for-loop-array/