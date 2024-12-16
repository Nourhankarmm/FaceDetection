# FaceDetection
What is face detection and how does it work?
Face detection, also called facial detection, is a computer technology that identifies human faces in digital images and video. It clearly distinguishes those faces from other objects and establishes their boundaries. Face detection is used in a variety of fields, including security, biometrics, law enforcement, entertainment and social media. For example, face detection is often used for surveillance and tracking people in real time.

Face detection plays a vital role in face tracking, face analysis and facial recognition:

### Face tracking
A face tracking system extends face detection by making it possible to detect and track more detailed features in human faces that appear in images, videos or real-time camera feeds.

### Face analysis
Face analysis begins with face detection to locate faces in an image or video and then analyzes facial features to determine characteristics such as age, gender and emotions.

### Facial recognition
A facial recognition system relies on face detection to identify faces within an image or video so a faceprint can be created and compared to stored faceprints

## Face detection vs. face recognition
The terms face detection and face recognition are often used interchangeably, but they represent two different approaches to facial identification. Face detection is concerned primarily with detecting and locating faces. Facial recognition takes this a step further by identifying individuals based on their facial features.

Facial recognition software starts by using face detection to distinguish a face from other objects. Once a face is identified, the system generates a faceprint of that image, based on biometric indicators that provide a unique map of the face. The faceprint is then compared to a database containing faceprints of other individuals to see whether there is a match.

Facial recognition is one of the most significant applications of face detection. Facial recognition is used to unlock mobile devices and apps and to support other forms of biometric verification. The banking, retail and transportation industries use facial recognition routinely as part of their security strategies to discourage criminal behavior, protect sensitive resources and identify potential suspects if an incident occurs.


## How face detection works
Face detection software typically uses AI and ML algorithms, along with statistical analysis and image processing, to find human faces within larger images and distinguish them from nonface objects, such as landscapes, buildings or other human body parts. Before face detection begins, the analyzed media might be preprocessed to improve its quality and remove objects that could interfere with detection.

Face detection algorithms usually start by searching for human eyes, one of the easiest features to detect. They then try to detect other facial landmarks, such as eyebrows, mouth, nose, nostrils and irises. Once the algorithm concludes that it has found a facial region, it performs additional tests to confirm that it has detected a face.

To ensure a high degree of accuracy, the algorithms are trained on large data sets that incorporate hundreds of thousands of positive and negative images. The training improves the algorithms' ability to determine whether there are faces in an image and exactly where their boundaries are.

![mobile_computing-mobile biometrics_03](https://github.com/user-attachments/assets/58b4d363-11ef-4df3-95a9-f2d962ad0780)


### Common approaches to face detection
Face detection software uses different methods to detect faces in an image. The following approaches are some of the more common ones used for face detection:

## Knowledge- or rule-based.
These approaches describe a face based on a set of rules, although creating well-defined, knowledge-based rules can be a challenge.
## Feature-based or feature-invariant. 
These methods use features such as a person's eyes or nose to detect a face, but the process can be negatively affected by noise and light.
## Template matching. 
This method is based on comparing images with previously stored standard face patterns or features and correlating the two to detect a face. However, this approach struggles to address variations in pose, scale and shape.
## Appearance-based. 
This method uses statistical analysis and ML to find the relevant characteristics of face images. The appearance-based method can struggle with changes in lighting and orientation.
Face detection also uses other techniques to identify faces in images or videos. For example, it might use one of more of the following approaches to help with the process:

## Background removal.
If an image has a plain, monochrome background or a predefined, static one, removing the background might reveal the face boundaries.
## Skin color.
In color images, skin color can sometimes be used to find faces, although this approach might not work with all complexions.
## Motion. 
Using motion to find faces is another option. In real-time video streaming, a face is almost always moving, so users of this method must calculate the moving area. One drawback of this approach is the risk of confusion with other objects moving in the background.
A combination of these strategies can help provide a more comprehensive face detection solution.


# Face detection technologies
Face detection software has evolved over time, incorporating advanced technologies to achieve more accurate results and better performance.

One of the earliest efforts was based on the Viola-Jones algorithm, which trains a model to understand what is and isn't a face. Although the framework is still popular for recognizing faces in real-time applications, it has problems identifying faces that are covered or not properly oriented.

As AI technologies have improved, so too have face detection capabilities. Many of these systems now use machine learning and deep learning when searching for faces. They also incorporate convolutional neural networks (CNNs), a type of deep learning algorithm that analyzes visual data, using linear algebra to identify patterns and features within an image.

One CNN-based approach to face detection is region-based CNN (R-CNN). In this model, the CNN algorithm localizes and classifies objects in images and then generates proposals on a framework. The proposals focus on areas, or regions, in an image that are similar to other areas, such as the pixelated region of an eye. If the eye region matches other regions of the eye, the algorithm knows it has found a match. More recent approaches to facial recognition include Fast R-CNN and Faster R-CNN.

One of the challenges with R-CNN facial recognition and its derivatives is their tendency to become so complex that they overfit, which means they match regions of noise in the training data and not the intended patterns of facial features. Another issue with CNN-based approaches is that they tend to experience bottlenecks, in large part because the software makes two passes over the CNN: one for generating region proposals and one for detecting the object of each proposal.

The single-shot detector (SSD) method helps to address this issue by requiring only one pass over the network to detect objects within the image. As a result, the SSD method is faster than R-CNN. However, the SSD method has difficulty detecting small faces or faces farther away from the camera.


# Bounding boxes augmentation for object detection¶
## Different annotations formats¶
Bounding boxes are rectangles that mark objects on an image. There are multiple formats of bounding boxes annotations. Each format uses its specific representation of bounding boxes coordinates. Albumentations supports four formats: pascal_voc, albumentations, coco, and yolo .

Let's take a look at each of those formats and how they represent coordinates of bounding boxes.

As an example, we will use an image from the dataset named Common Objects in Context. It contains one bounding box that marks a cat. The image width is 640 pixels, and its height is 480 pixels. The width of the bounding box is 322 pixels, and its height is 117 pixels.

The bounding box has the following (x, y) coordinates of its corners: top-left is (x_min, y_min) or (98px, 345px), top-right is (x_max, y_min) or (420px, 345px), bottom-left is (x_min, y_max) or (98px, 462px), bottom-right is (x_max, y_max) or (420px, 462px). As you see, coordinates of the bounding box's corners are calculated with respect to the top-left corner of the image which has (x, y) coordinates (0, 0).


![bbox_example](https://github.com/user-attachments/assets/5ab0cca4-b7f5-42e2-8039-aa0b80c0ad30)


## pascal_voc
pascal_voc is a format used by the Pascal VOC dataset. Coordinates of a bounding box are encoded with four values in pixels: [x_min, y_min, x_max, y_max]. x_min and y_min are coordinates of the top-left corner of the bounding box. x_max and y_max are coordinates of bottom-right corner of the bounding box.

Coordinates of the example bounding box in this format are [98, 345, 420, 462].

## albumentations
albumentations is similar to pascal_voc, because it also uses four values [x_min, y_min, x_max, y_max] to represent a bounding box. But unlike pascal_voc, albumentations uses normalized values. To normalize values, we divide coordinates in pixels for the x- and y-axis by the width and the height of the image.

Coordinates of the example bounding box in this format are [98 / 640, 345 / 480, 420 / 640, 462 / 480] which are [0.153125, 0.71875, 0.65625, 0.9625].

Albumentations uses this format internally to work with bounding boxes and augment them.

## coco
coco is a format used by the Common Objects in Context COCO dataset.

In coco, a bounding box is defined by four values in pixels [x_min, y_min, width, height]. They are coordinates of the top-left corner along with the width and height of the bounding box.

Coordinates of the example bounding box in this format are [98, 345, 322, 117].

## yolo
In yolo, a bounding box is represented by four values [x_center, y_center, width, height]. x_center and y_center are the normalized coordinates of the center of the bounding box. To make coordinates normalized, we take pixel values of x and y, which marks the center of the bounding box on the x- and y-axis. Then we divide the value of x by the width of the image and value of y by the height of the image. width and height represent the width and the height of the bounding box. They are normalized as well.

Coordinates of the example bounding box in this format are [((420 + 98) / 2) / 640, ((462 + 345) / 2) / 480, 322 / 640, 117 / 480] which are [0.4046875, 0.840625, 0.503125, 0.24375].

![bbox_formats (1)](https://github.com/user-attachments/assets/33ec4297-eeaf-4427-ace5-7e63947a6db4)


# Bounding boxes augmentation
Just like with images and masks augmentation, the process of augmenting bounding boxes consists of 4 steps.

(1)You import the required libraries.

(2)You define an augmentation pipeline.

(3)You read images and bounding boxes from the disk.

(4)You pass an image and bounding boxes to the augmentation pipeline and receive augmented images and boxes.


