## Project: Search and Sample Return
### Writeup Template: You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---


**The goals / steps of this project are the following:**  

**Training / Calibration**  

* Download the simulator and take data in "Training Mode"
* Test out the functions in the Jupyter Notebook provided
* Add functions to detect obstacles and samples of interest (golden rocks)
* Fill in the `process_image()` function with the appropriate image processing steps (perspective transform, color threshold etc.) to get from raw images to a map.  The `output_image` you create in this step should demonstrate that your mapping pipeline works.
* Use `moviepy` to process the images in your saved dataset with the `process_image()` function.  Include the video you produce as part of your submission.

**Autonomous Navigation / Mapping**

* Fill in the `perception_step()` function within the `perception.py` script with the appropriate image processing functions to create a map and update `Rover()` data (similar to what you did with `process_image()` in the notebook).
* Fill in the `decision_step()` function within the `decision.py` script with conditional statements that take into consideration the outputs of the `perception_step()` in deciding how to issue throttle, brake and steering commands.
* Iterate on your perception and decision function until your rover does a reasonable (need to define metric) job of navigating and mapping.  

## [Rubric](https://review.udacity.com/#!/rubrics/916/view) Points
### Here I will consider the rubric points individually and describe how I addressed each point in my implementation.  

---
### Writeup / README

#### 1. Provide a Writeup / README that includes all the rubric points and how you addressed each one.  You can submit your writeup as markdown or pdf.  

You're reading it!

### Notebook Analysis
#### 1. Run the functions provided in the notebook on test images (first with the test data provided, next on data you have recorded). Add/modify functions to allow for color selection of obstacles and rock samples.
Here is an example of how to include an image in your writeup.




#### 2. Populate the `process_image()` function with the appropriate analysis steps to map pixels identifying navigable terrain, obstacles and rock samples into a worldmap.  Run `process_image()` on your test data using the `moviepy` functions provided to create video output of your result.






### Autonomous Navigation and Mapping

#### 1. Fill in the `perception_step()` (at the bottom of the `perception.py` script) and `decision_step()` (in `decision.py`) functions in the autonomous mapping scripts and an explanation is provided in the writeup of how and why these functions were modified as they were.

For this project the data capture of the `perception_step()` goes to the instance of the class `RoverState()`. All functions we develop during the quizzes were really helpful in order to develop this function. The `perception.py` had all the functions, in the 'perception_step' we applied the functions to determine the rock samples, obstacles, and the navigable terrain.

* First of all we needed to find the rocks samples, for this we use certain values for the threshold in order to identify which objects are rocks, the simulation make it easy to do this because the rocks color is yellow. The `find_rocks` use the values of the threshold and the current image (`Rover.img`) and if conditions are true, it will show the rock sample.

* We did almost the same steps as in the Jupyter notebook, we defined our source and description points, then we applied the `perspect_transform` to the current image and we created a mask, after that we mapped the rover coords with the functions `rover_coords` and pass them into the `pix_to_world`.

#### 2. Launching in autonomous mode your rover can navigate and map autonomously.  Explain your results and how you might improve them in your writeup.  

* Screen resolution: 1920x1080; Graphics quality: Good; FPS output to terminal: 13-15.

* Rover performance is good enough, it mapped 75-95% of the world with 60-70% fidelity. However, the problem is that the `decision.py` is not completetly develop, the decision making of the rover is too simple and also the velocity of the rover is quite slow.

![Last Frame](RoverSimu.png)

* In order to make the rover more efficient, many improvements are needed: First, the rover can throttle whenever the path has a lot of navigable terrain. Another important change might be that the rover can remembered the paths that he already visited and to make the decision with that information.
