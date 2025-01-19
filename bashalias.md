# Bash Alias
## docker stop all containers
```
alias dockersa='docker stop $(docker ps -aq)'
```

## docker remove all containers

```
alias dockerra='docker rm $(docker ps -aq)'
```