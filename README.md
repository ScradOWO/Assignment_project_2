# Assignment Project-2
## Process Monitoring Using Video Analytics
### Objective: Implement a vision system to monitor operator assembly processes and ensure the correct execution of steps.

## **1. System Architecture:**
### **Hardware:**
- Nvidia Jetson nano, as mentioned in the project document.
- A capable machine to install the above device in, with at least 16GB of ram for seamless training of the model and a 6/8 core CPU with an SSD.
- A CCTV Camera which will be used to capture the videos of the operation area
- A display to monitor and view the captured video and to provide real-time feedback
- Sensors such as ultrasonic or motion detectors to trigger the detection system
### **Software:**
- OS (Operating system) such as Linux/Windows, Linux preferred
- A stable python installation
- Libraries such as TensorFlow, Numpy, PyTorch
- OpenCV for the image processing part.
- A User Interface, to monitor and configure the program.
- Integration with Manufacturing Systems; integrate the system with the control systems to take corrective actions or log data.

The Nvidia Jetson Nano will be used at the heart of the computer vision system. It will do all the heavy lifting, which is image processing and deep learning. It is a single board computer designed specifically for AI/ML/DL applications. It's fast, efficient and has high capabilities in the field. 

## **2. Video Analysis and Process Identification:**
### **Approach:**
- Analyse the video using techniques such as object detection, tracking. 
- Implement frame differencing and motion detection to identify when a step is being executed.
### **AI for Process Identification:**
- Training a model to differentiate and segregate all the steps taken by the operator assembly.
- Use a sequence-to-sequence model if the order of steps is crucial.
- Object detection may also be used if specific components need to be identified
### **Algorithm/Methodology::**
- Develop logic that compares detected steps with predefined correct sequences or conditions.
- Alert user when a wrong step is taken, of if one of the steps is skipped, etc.

## **3. AI Training and Development:**
### **Data Collection:**
- For this project, we need to collect a vast number of videos of the operation in progress, where we have both correct and incorrect outputs.
- We need to ensure diversity in the data to cover a wide range of cases and machineries depending on the requirement.
- This may include videos taken in different conditions at different times and at different angles with variable lightning, and angles for highest coverage.
### **Annotation:**
- The annotation process is where we will annotate and tag the videos as either 'correct execution', or 'incorrect execution'.
- Doing this process manually would be preferred as we are dealing with safety here first and foremost.
- Labelling the annotation boxes with the relevant info.
- Making sure all the data is annotated and labelled correctly before training the model.
### **AI Training Pipeline:**
- Choosing a pretrained model may help in execution speeds.
- Choosing the DL framework; in our case, I have selected tensorflow as my approach to this project.
- Implement data augmentation techniques (e.g., frame jittering, lighting variations) to improve model robustness.
- Data preparation and preprocessing; we preprocess our annotated data before we train the model.

### **Training and Validation:**
- Train the model to recognize each step in the correct order.
- We split the dataset into 3 sets, training, validation and testing.
- Training Process: Train the model using the training dataset. Implement the following training steps:
  - Forward pass: Pass sequences of frames through the model to obtain predictions.
  - Calculate loss: Compute the loss between the predicted and ground truth labels.
  - Backpropagation: Update model weights through gradient descent to minimize the loss.
- Repeat these steps for multiple epochs, adjusting hyperparameters as needed.
- The training process is where we will try to adjust the weights and such to get the highest accuracy.
- We can also adjust the number of epochs to see which gives us the lowest rate of error.
- The model can then be evaluated and checked for metrics such as mAP (Mean Average Precision) to monitor the speed and accuracy according to our requirements.

## **4. Deployment Planning:**
### **Deployment Strategy:**
- This is to be deployed on the Nvidia Jetson Nano/Xavier for the real-time video analysis.
- We need to integrate our system with the sensors to trigger the system when necessary.
- Alert the operator or person near the machinery with an alarm and on the display as an extra measure when incorrect step is taken, or skipped.
### **Real-time Performance Considerations:**
- Optimize model inference for real-time performance, possibly using TensorRT for Jetson Nano/Xavier.
- Implement multi-threading or asynchronous processing for efficient data handling.
- Monitoring the system in real time for resource usage and optimizing as needed wherever possible.
### **Challenges and Limitations:**
- Reflections, lightning, position can pose as challenges in the system, as theyre never constant, this could be counteracted by adding an additional check during training for reflective surfaces or training the model on a dataset which contains them.
- False positives and false negatives may occur and need to be minimized.
- Real-world deployment may face challenges like dust, vibrations, or extreme temperatures, which could affect the hardware and/or the sensors.

## Explanatory Diagram:
![](https://i.ibb.co/L8Gr2zY/flowchart.jpg)
