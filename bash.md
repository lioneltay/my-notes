# Bash Notes

- `$(<bash commands>)`
  - Runs the bash commands and places the result in place of `$(...)`
  - Examples:
    - Remove all docker containers
      - `docker container rm $(docker container ls -a -q)`

- `export <variable-name>=<value>`
  - Sets an environment variable for all child processes
    - Examples:
      - `export TEST=5`, `echo $TEST` (prints out 5)

- `unset <variable-name>`
  - Removes an environment variable for all child processes (opposite of export)
    - Examples:
      - `unset TEST=5`, `echo $TEST` (prints out nothing)