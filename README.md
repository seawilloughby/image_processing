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
    - The contour detection function identifies white objects as defined by a dark surrounding, which may work will for these images, as the bubbles have a dark outside and white inside
    
##Script Details:
 - The accompanying notebook loads the images present in the data/images folder. 
 - It iterates through every image in the image folder, and runs the function 'bubble_detector'. 
 - A green circle is drawn around every contour suspected to be a 'bubble', and an image is written to the 'output' folder, with the image and potential bubble overlayed for inspection.

 ##Future Improvements:

 In its current form, this image procesing is far from perfect. Many bubbles are missed, and many bubbles are incorrectly identified.

 Further modifications and troubleshooting is needed. 
 	 - Try brightening the images, or reducing contrast. This may reduce mis-identification of bubbles, since they are marked by a dark ring.
 	 - Investigate if the threshold for local contrast to determine a 'contour' can be altered.
 	 - Create a more fine-tuned range of acceptable 'bubbles' in the existing functions. For instance, the acceptable size range of bubbles could be improved.