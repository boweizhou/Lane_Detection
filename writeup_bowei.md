# **Finding Lane Lines on the Road** 



**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
1. Process the picture in a way easy to identify the lanes
2. Find lanes on the picture
3. Drawing lines on picture
4. Drawing one extended line based of all detected lane on picture
5. Apply the pipe line to the video 


### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

In my pipe line:
First, I converted the images to grayscale, gray the image turn image cell color into "one number", which is for better and quicker edge detection 

Second, I used Gaussian to smooth the image/ lower the noise

Third, I applied Canny to the image using low_threshold = 50, and high_threshold = 100 to define the edge of the image

Fourth, I used a a four sided polygon masked the area only for lanes

Fifth, I use Hough to define the lines in the image using the following parameter
    rho = 1
    theta = np.pi/180
    threshold = 20
    min_line_length = 20
    max_line_gap = 300

At this points, I have got image together with bunch of small "lines" as the lanes. not single line on left and right side.

Sixth, in order to draw a single line on the left and right lanes, I can think of two ways.

First method: we can find average slop, intercept on both right and left lines, then we can aquire two functions like y = ax +b. Using these two functions, we can draw two singal lines

Second method: using the set of the points, we can simple use "linear regression" to draw both right and left lanes

In the project I used the "First method"

Following is the outcome of the pipe line.


![alt text](https://github.com/boweizhou/Lane_Detection/blob/master/output_solidWhiteCurve.jpg?raw=true)
![alt text](https://github.com/boweizhou/Lane_Detection/blob/master/output_solidWhiteRight.jpg?raw=true)
![alt text](https://github.com/boweizhou/Lane_Detection/blob/master/output_solidYellowCurve.jpg?raw=true)
![alt text](https://github.com/boweizhou/Lane_Detection/blob/master/output_solidYellowCurve2.jpg?raw=true)
![alt text](https://github.com/boweizhou/Lane_Detection/blob/master/output_solidYellowLeft.jpg?raw=true)
![alt text](https://github.com/boweizhou/Lane_Detection/blob/master/output_whiteCarLaneSwitch.jpg?raw=true)


### 2. Identify potential shortcomings with your current pipeline

Potential shortcoming1: a lot of crake lines on top of the road, may cause the failure of detecting the real lanes

Potential shortcoming2: since the current softwaer can only draw two straight lines, it will not working when road is curving

### 3. Suggest possible improvements to your pipeline

Possible improvement 1: Define the conditions that apply to line detection. example: the angle of the line. 

Possible improvement 2: using Fitting Curves with Polynomial Terms in Linear Regression to draw the lanes instead

![alt text] (http://cdn2.content.compendiumblog.com/uploads/user/458939f4-fe08-4dbc-b271-efca0f5a2682/742d7708-efd3-492c-abff-6044d78e3bbd/Image/1f947e9a2d3aa341b40d37ce738926e6/quadratic.gif)
