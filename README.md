# Heroku-16 stack buildpack with OpenCV.

## How

A complete environment was created using the Dockerfile file based on the heroku stack v16.

This includes the following:
- Opencv-3.4.1.
- Supporting Go lang binding. ([gocv](https://github.com/hybridgroup/gocv))

Go lang setup:

```
heroku buildpacks:add --index=1 https://github.com/onboardiq/heroku16-buildpack-opencv3.git
heroku buildpacks:add --index=2 https://github.com/onboardiq/heroku-buildpack-go.git
```

Python setup:

```
heroku buildpacks:add --index=1 https://github.com/onboardiq/heroku16-buildpack-opencv3.git
heroku buildpacks:add --index=2 heroku/python
```

## Development

You can build your own OpenCV buildpack via Docker. For more details, please read:
- [How to compile OpenCV](Dockerfiles/opencv/README.md).
- [How to test compiled result](Dockerfiles/test-image/README.md).
