# Jibri "Audio Only" (Docker version instructions)

This build is an exact copy of the original **Jibri** Java executable minus the video recording options of the embedded **ffmpeg**

## What is Jibri

Jibri provides services for recording or streaming a Jitsi Meet conference.

It works by launching a Chrome instance rendered in a virtual framebuffer and capturing and encoding the output with ffmpeg. It is intended to be run on a separate machine (or a VM), with no other applications using the display or audio devices. Only one recording at a time is supported on a single jibri.

## Replacing Jibri with the "Audio Only" build
To use this custom build you just need to replace the **jibri.jar** file inside the **"/opt/jitsi/jibri/"** folder inside the Docker Jitsi container, you can replace the file using Dockerfile or by mounting a volume inside the docker-compose file (normally: jibri.yml)

```
volumes:
    - ./jibri/custom-jibri.jar:/opt/jitsi/jibri/jibri.jar
```

## Need to modify the build?
Just clone the repo, make your changes and then from the root folder launch the command **"mvn package"** (after installing apache maven)

You'll find the .jar file inside **"$CLONED-REPO-DIR/target"** folder as **"jibri-X.x-SNAPSHOT-jar-with-dependencies.jar"**
