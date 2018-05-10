## Dockerfile for testing OpenCV assets:

Steps:

Build docker image

```sh
$ docker build -t test-image .
$ docker run -it test-image:latest  /bin/bash
```

And testing:

```py
$ python3.5
import cv2
img = cv2.imread("image.png")
gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
cv2.Laplacian(gray, cv2.CV_64F).var()
# => 6724.722702382197
```
