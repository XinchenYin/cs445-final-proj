# File Organizational Structure

- NST
  - FProjRenderImages
  - images
  - FProj_coloraware.ipynb
  - FProjRenderImages.ipynb
- FAST_NST
  - content
  - models
  - output
  - images
    - out
  - requirements.txt
  - stylze.py
  - train.py
  - transformer.py
  - utils.py
  - vgg.py
  - video.py

# Running Basic Neural Style Transfer

1. Under NST directory, run the FProj_coloraware.ipynb to generate images with NST
2. Run FProjRenderImages.ipynb for further presentation of results

# Running Fast Neural Style Transfer (with video style transfer):

1. Under the FAST_NST directory, save an .mp4 content file in the directory.
2. Go to the video.py file and update the INPUT_VIDEO_PATH variable to the file path of the video.
3. Update the STYLE_MODEL variable to any keys defined in STYLE_MODEL_PATHS to select the model ("mosaic", "starry", "picasso")
4. Update the OUTPUT_VIDEO_PATH variable to the name of the output video.
5. Click run. It will first convert the input video to frames and save all frames in the content folder. Once all frames are saved, the stylize function will load all the frames in the content folder and apply Fast NST and save the frames to the output folder. Once all frames are processed, an .MP4 output video will be generated from all the frames in the output folder.
6. If you want to run a Fast NST on one picture/ frame, you can just save the picture as a .jpg in the content folder (and make sure there are no other pictures that you don't want to generate). You can then comment out lines 116, 118, and 119 and only run the stylize function, which will NST the image and save the single image in the output folder.
7. Example Content videos and Output Videos can be found in this DropBox link: https://www.dropbox.com/scl/fo/0vlez3q6guwl6dmqgt4bm/h?rlkey=96yy83r4dswevzl6c38ayxcda&dl=0. In the outputs folder, there are output videos trained under relu2 and one output video with pretrained model with relu3.

# How to Train Your Own Stylizer

1. Download coco dataset from http://images.cocodataset.org/zips/train2014.zip, unzip it under `dataset` directory.
2. Put your style image under `images` directory.
3. Modify `STYLE_IMAGE_PATH` of `train.py` to the style image of yours. 
5. Modify any parameters in `train.py` to whatever you want.
6. Under the `FAST_NST` directory, run `train.py` without any parameters using function `train()`.
7. After training, you can test the effects on a single image by changing `TEST_INPUT` and `TEST_MODEL` in `train.py` to your input image path and your model path and utilize the function `test_stylize()` instead of `train()`.