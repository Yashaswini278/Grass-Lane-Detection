# Grass Lane Detection
The objective of this project was to implement a method to automatically keep an autonomous ground vehicle within a lane defined by white chalked lines on grass. I developed the method using Computer Vision and implemented it using Python. <br/> <br/> The video used as input to the method can be found here: https://www.youtube.com/watch?v=A9BVr7kltl8  <br/> <br/> The code has been uploaded to this repository as a .ipynb file, <br/> <br/> The output video can be found here: https://youtu.be/blcDK1o2MrM 

## Key Learnings
1. Different color spaces other than RGB - HSV and HSL
2. Image segmentation via color spaces
3. Masking in opencv
4. Morphological Transformations
## Challenges and Workarounds
### 1. Choosing the right method
Through this project, I came across several lane line detection techniques like via color spaces, via texture, Canny edge detection + Hough line transform, and so on. I tried all of the above methods and came to the conclusion that segmentation via color space would be an easy to implement and effective method for tackling this problem. 
### 2. Selecting the right color space
While trying to filter out the white lanes on grass, I came across different color spaces like HSV and HSL. Initially, I was experimenting with the 
grayscale image and rgb image. Finally I found the HSV color space best suitable for this task.
### 3. Getting rid of the white stripes on the orange obstacles
I tried various methods to avoid detecting the white stripes on orange obstacles, such as histogram backprojection, blackening the column of pixels whenever an orange pixel is found and so on. The method which gave the best result was the one in which, first the result frame was converted to grayscale, then fixing the upper and lower bounds of the lanes as "greenish white" (see shaded region in image below), and finally applying morphological operations on the masked result frame. 
![IMG_0574](https://user-images.githubusercontent.com/77488107/117620880-90ef3400-b18e-11eb-8aa4-8f09420251f5.jpg)
</p>
<p>  Source: https://stackoverflow.com/questions/10948589/choosing-the-correct-upper-and-lower-hsv-boundaries-for-color-detection-withcv </p>

## Scope for improvement
### 1. Border of obstacles and white stripes could not be completely removed
In the output video, when the obstacles start appearing, small white flickers are observed. Thus the task of detecting only lanes is left incomplete.
### 2. Discontinuities in the lane were found
There are some discontinuities in the detected lane.
### 3. White lane on the ramp could not be detected
Instead of the lane lines on the ramp, the border of the ramp is detected. This is a major problem in the code which I could not fix, but I hope to 
fix it in the future. 
### 4. The lane lines after the ramp could not be detected
In the frames after the ramp, there is a blind spot in which nothing is detected. However, after a few frames, a few of the white lanes are detected.

## Conclusion
Overall this project was quite challenging. I spent quite a lot of time to first understand the conventional lane detection methods but upon applying them to this video,I did not get satisfactory results. So I changed my strategy and took up image segmentation via color space method. There is a lot of scope for improvement in the code and I hope to achieve better results in the future. 
