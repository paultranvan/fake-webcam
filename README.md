# Fake webcam

Taken from this [blog post](https://elder.dev/posts/open-source-virtual-background/)
Replace the video webcam background by an image. The person is extracted thanks to [BodyPix](https://blog.tensorflow.org/2019/11/updated-bodypix-2.html) using a CNN on TensorFlow.

Note the [tensorflow-cpu](https://github.com/tensorflow/tfjs/tree/master/tfjs-node) for node.js was used, but the resulting video is quite slow and not smooth. A GPU would be better, as used in the blog post.

Tested with skype and zoom.

## Run it

It is composed of a a Node.js server and a Python script:

* Node.js server: receive the image from the python script, execute the Tensorflow image segmentation and return the result.
* Python script: setup a fake webcam device, send the real webcam frames to the server, apply post-treatment to the frame and send it to the fake webcam.

The image background is the image found in `./background.jpg`. There are some examples in the `backgrounds` directory.

## Node.js

`npm install`
`node body-pix.js`

## Python
`pip install -r requirements.txt`
`python webcam.py`

## Fake webcam

The fakewebcam device requires some installation and permissions. See the [repo](https://github.com/jremmons/pyfakewebcam).
