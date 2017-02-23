#**Finding Lane Lines on the Road** 


###1. Pipeline

The pipeline consists of following steps:
- conversion to grayscale
- canny edge detection
- definition of the region of interest. The positions of the vertices are defined relative to the size of the image. This makes the pipeline insensitive to the image resolution.
- hough transformation
- filtering, averaging and drawing of the lines to the original image

The drawing function draws one line for the left side and one for the right side. To achieve this, the lines found by the hough transformation are devided into a left list and a right list. To devide into left and right the start/lower point of each line is considered but also it's slope. Only lines with a slope in a defined range are added to the corresponding list (for example horizontal lines will be ignored since the lane lines never become horizontal).
After this, for the lines in the left and right list slope, center and their average is computed. From this, two averaged lines for the left and right side can be computed. If the variable "draw_all" is set to "True", all the lines from the hough transformation will be drawn to the picture besides the averaged lines.


###2. Shortcomings

One potential shortcoming would be what would happen when camera angle changes. The cropping of the region of interest is done quite aggresively.

Another shortcoming could be that the averaged lines are too jumpy.


###3. Improvements

A possible improvement would be to make the region of interest bigger but implement a better filter for the lines. Using color information could be a help here. Maybe YUV-colorspace could help.

Another potential improvement could be to average between consecutive images/frames. Especially for the challenge this would probably improve the results a lot.
