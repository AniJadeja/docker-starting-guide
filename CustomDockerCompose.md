# This setup will create custom commands for docker.

## Assumes that user is on linux system. Suitable replacement for windows and mac can be obtained from chatgpt by giving this script and asking for the replacement for the selected system.
## I personally do not have mac or windows to test the replacement scripts

Add this function to `~/.bashrc` 
```
# Custom command config for Docker only
function dc() {
  case "$1" in
    up)
      if [[ "$2" == "-c" ]]; then
        # Run cleanup first if "-c" is passed as the second argument
        docker system prune -a --volumes -f
      fi
      docker-compose down
      docker-compose up --build
      ;;
    down)
      docker-compose down
      ;;
    *)
      echo "Usage: dc {up [-c]|down}"
      return 1
      ;;
  esac
}

```

This will configure three aliases. 

1. `dc up` : which will run `docker-compose down` and then `docker-compose up --build`
2. `dc down` : which will run `docker-compose down`

## use this with caution 

3. `dc up -c` : which will clean everything inside docker system. All the images, containers, volumes no matter they are in use or not. 
                   It will run `docker system prune -a -f` and then `docker-compose up --build`.
