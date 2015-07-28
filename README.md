# Artifact Detection: Bubbles

##Requirements:

This code uses the following libraries: 
 - ipython notebook
 - json
 - pandas
 - numpy
 - glob
 - OpenCV

##Narrative for deciding on library:

I conducted a quick google search to investigate what methods are being used to image processing/ image detection. After browing a few tutorials, it appeared that OpenCV is a popular library.

I downloaded the OpenCV library to my computer, and explored the potential functions:


- Install OpenCV and associated supporting packages for your operating system
    - `conda install opencv` worked for my setup. I use Anaconda. 
 
 
- I experimented with the following functions in OpenCV:
    - SimpleBlobDetector
    - Hough Circle Transform
    - Contour Detection
    
- I found I was getting the closest results with contour dectection, so I played around some with optimizing the settings. 
    - http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_imgproc/py_contours/py_contours_begin/py_contours_begin.html
    - The contour detection function identifies white objects as defined by a dark surrounding, which may work well for these images, as the bubbles have a dark rim and white interior.
    
##Script Details:
 - Place image files into the 'data/images' folder. The ipython notebook 'artifact_detection' loads and processes images in the data/images folder. 
 - The output folder contains example output from running the python program. A green circle is drawn around every contour suspected to be a 'bubble', and an image is written to the 'output' folder, with the image and potential bubble overlayed for inspection. Inside the folder are example image where bubbles were correctly identified, and examples were bubbles were not captured. 

##Future Improvements:

The processing of images is incomplete, and needs more troubleshooting be finetuned for accuracy.

 	 - The images themselves could be further processed, such as by reducing the contrast and/or brightening the images.  Because bubbles are marked by dark rings, this should minimize detection of contours in low contrast areas. 
 	 - Because the OpenCV library finds contours by identifying white spaces framed by black, it may be possible to adjust the threshold the function uses for defining a contour. 
 	 - The existing functions I wrote to filter potential 'contours' need to be fine-tuned. For instance, the acceptable size range of bubbles could be improved.