# Grass-Lane-Detection
This task was assigned to me as part of the selection process for the Autonomous Ground Vehicle Research Group software team at IIT Kharagpur.
## Key Learnings
1. Different color spaces other than RGB - HSV and HSL
2. Image segmentation via color spaces
3. Masking in opencv
4. Morphological Transformations
## Challenges and Workarounds
### 1. Choosing the right method
Through this task, I came across several lane line detection techniques like via color spaces, via texture, canny edege detection + hough line transform, and so on. 
I tried out all of the above methods and came to the conclusion that segmentation via color space would be an easy to implement and understand
yet effective method for tackling this problem. 
### 2. Selecting the right color space
While trying to filter out the white lanes on grass, I came across different color spaces like HSV and HSL. Initially, I was trying to do this task by experimenting with the 
grayscale image and rgb image. Finally, I found the HSV color space best suitable for this task.
### 3. Getting rid of the white stripes on the orange obstacles
I tried various methods to avoid detecting the white stripes on orange obstacles, such as histogram backprojection, blackening the column of pixels wheneve an orange pixel is found and so on. The method which gave the best result was the one in which, first the result frame was converted to grayscale, then fixing the upper and lower bounds of the 
lanes as "greenish white"(see shaded region in image below), and finally applying morphological operations on the masked result frame. 
![IMG_0574](https://user-images.githubusercontent.com/77488107/117620880-90ef3400-b18e-11eb-8aa4-8f09420251f5.jpg)
</p>
<p>  Source: https://stackoverflow.com/questions/10948589/choosing-the-correct-upper-and-lower-hsv-boundaries-for-color-detection-withcv </p>

## Scope for improvement
### 1. Border of obstacles and white stripes not completely removed
In the output video during the obstacles, small flickers of white is observed. Thus, the task of detecting only lanes is left incomplete.
### 2. Discontinuties in lane detected
The detected lane is not continous and there are some discontinuties.
### 3. White lane on ramp not detected
Instead of the lane lines on the ramp, the border of the ramp is detected. This is a major problem in the code which I could not fix, but I hope to 
fix it in the future. 
### 4. After the ramp, lane lines are not detected
In the frames following after the ramp, there is a blind spot in which nothing is detected. However, after a few frames, a few of the white lanes are detected

## Conclusion
Overall this was quite a challenging task for me. I spent quite a lot of time firt understanding the conventional lane detection methods but upon applying them to this video,
I did not get satisfactory results. That is when I changed my strategy and took up image segmentation via color space method. There is a lot of scope for improvement in this 
task and I hope to achieve better results in the future. 
