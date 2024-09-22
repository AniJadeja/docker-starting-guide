# This setup will create custom commands for docker.

## Assumes that user is on linux system. Suitable replacement for windows can be obtained from chatgpt

Add this function to `~/.bashrc` 
```

#custom command config for docker only
function dc() {
  case "$1" in
    up)
      docker-compose up --build
      ;;
    down)
      docker-compose down
      ;;
    clean-up)
      docker system prune -a --volumes -f
      docker-compose up --build
      ;;
    *)
      echo "Usage: dkr {up|down|clean-up}"
      return 1
      ;;
  esac
}
```

This will configure three aliases. 

1. `dc up` : which will run `docker-compose up --build`
2. `dc down` : which will run `docker-compose down`

## use this wil caution 

3. `dc clean-up` : which will clean everything inside docker system. All the images, containers, volumes no matter they are in use or not. 
                   It will run `docker system prune -a -f` and then `docker-compose up --build`.
