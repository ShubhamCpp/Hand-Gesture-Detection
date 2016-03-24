# Hand-Gesture-Detection
A Hand Gesture Detection and Tracking Algorithm with OpenCV and Python.
This Algorithm uses OpenCV 3.0 and Python 2.7.

# Working and Implementation

## 1.	Detection of Hand Movements using OpenCV :
	
### a.	Capture the Video Frames, convert them to Grayscale and find the Region of Interest:-

We convert an image from RGB to grayscale and then to binary in order to find the ROI i.e. the portion of the image we are further interested for Image Processing. By implementing this our decision becomes binary, i.e., "yes the pixel is of interest" or "no the pixel is not of interest".

### b.	Reduce Noise : 
•	The Technique of Gaussian Blurring is used on the original image. For smoothing the image and to reduce noise and details from the image, we must blur it first. We are not interested in the details of the image but in the shape of the object we want to track.

•	By blurring, we create smooth transition from one color to another and reduce the edge content. We use Thresholding for image segmentation,i.e., to create binary images from grayscale images.

### c.	Thresholding :-

•	In very basic terms, thresholding is like a Filter(Low/High), i.e., by allowing only particular color values to appear as white, while the other colors are suppressed by showing them as black.

•	If pixel value is greater than a threshold value, it is assigned one value (may be white), else it is assigned another value (may be black).

•	One can use Guassian Adaptive Thresholding for this scenario. In this, the algorithm calculates the threshold for small regions of the image. So we get different thresholds for different regions of the same image and it gives us better results for images with varying illumination. 

•	However, I've used Otsu's Binarization method. In this method, OpenCV automatically calculates/approximates the threshold value of a bimodal (bimodal image is an image whose histogram has two peaks) image from its image histogram. This however, will only be approximate for a non-bimodal image. Therefore, for optimal results, we may need a clear background in front of the webcam which sometimes may not be possible.

### d.	Find convex hull and convexity defects :
We now find the convex points and the defect points. The convex points are generally, the tip of the fingers. But there are other convex point too. So, we find convexity defects, which is the deepest point of deviation on the contour. By this we can find the number of fingers extended and then we can perform different functions according to the number of fingers extended.

### e.	Find the Area under the Contour and the Points where the Hand’s Contour is Detected:-

We need to find the Points where the Hand is Recognized. This will help us to detect the swipe of the hand and hence make the corresponding transitions, making the Core of the Game.
