# Docker Image Build

To build an image open a project inside a docker container

1. Create a project folder and note down the name. ie. `proj1`

2. Open the folder in IDE. ie. `VS Code`

3. You will need the docker extension to be installed.

4. Navigate to the same folder in terminal.

5. Create a `Dockerfile` with this exact name in the project root.

 5.1 How this dockerfile works is simple. The dockerfile contains the instructions when the container initially runs the commands mentioned in this file. 

     - init command is always the sys image pull. ie. 
     ```
     FROM ros:humble
     ```

     The commands ran in the container is defaults to root user. So no need to write `sudo` command. (sudo is used just to represent the root privilege command)
     The images we pull here has nothing at all as utility apps. Not even a text editor.

     - To install the nano inside the container : 
     ```
     RUN apt-get update && apt-get install nano && rm -rf /var/lib/apt/lists/*
     ```
     `RUN` command runs the command in the terminal of the image.

     - To copy some files to the root of the image : 
     ```
     COPY <sourceDir> <destinationDir>
     ```
     Source Dir is always referencing the current working dir. In our case `proj1`. So if we want to copy the folder `proj1/config` then the `sourceDir` will be `./Config`
     Destination Dir is always referencing the root of the image. in our case `/`
     - So the final command will look like this :
     ```
     COPY ./Config /
     ```

6. Because we are in the same folder as the dockerfile we can reference it in terminal. So, to build the image :
   ```
   docker image build -t <imageName> <imagePath>
   ```
   `docker build` is a short form.
   -t allows to name the image. ie `firstImage` and because we are referencing the same dir, the image path is `.` So the final command will look like this.
   ```
   docker image build -t first_image .
   ```
   note : dot (`.`) is actually the current dir path and not a mistake in command.
          the name of the image must be in lower cases.


Image built and Ready to run the container !!!






run this command to run this image container :
```
docker run first_image
```

to check this image :
```
docker images
```

To interact with the terminal of this image :
```
docker run -it first_image
```
     

  
