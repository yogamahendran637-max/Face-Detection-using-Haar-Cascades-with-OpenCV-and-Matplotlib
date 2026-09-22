# Aim
To write a Python program using OpenCV to perform the following image manipulations:
i) Extract ROI from an image.
ii) Perform face detection using Haar Cascades in static images.
iii) Perform eye detection in images.
iv) Perform face detection with label in real-time video from webcam.

# Software Required
Anaconda - Python 3.7 or above

OpenCV library (opencv-python)

Matplotlib library (matplotlib)

Jupyter Notebook or any Python IDE (e.g., VS Code, PyCharm)

# Algorithm
# I) Load and Display Images

Step 1: Import necessary packages: numpy, cv2, matplotlib.pyplot

Step 2: Load grayscale images using cv2.imread() with flag 0

Step 3: Display images using plt.imshow() with cmap='gray'

# II) Load Haar Cascade Classifiers

Step 1: Load face and eye cascade XML files

# III) Perform Face Detection in Images
Step 1: Define a function detect_face() that copies the input image

Step 2: Use face_cascade.detectMultiScale() to detect faces

Step 3: Draw white rectangles around detected faces with thickness 10

Step 4: Return the processed image with rectangles

# IV) Perform Eye Detection in Images
Step 1: Define a function detect_eyes() that copies the input image

Step 2: Use eye_cascade.detectMultiScale() to detect eyes

Step 3: Draw white rectangles around detected eyes with thickness 10

Step 4: Return the processed image with rectangles

# V) Display Detection Results on Images
Step 1: Call detect_face() or detect_eyes() on loaded images

Step 2: Use plt.imshow() with cmap='gray' to display images with detected regions highlighted

# VI) Perform Face Detection on Real-Time Webcam Video
Step 1: Capture video from webcam using cv2.VideoCapture(0)

Step 2: Loop to continuously read frames from webcam

Step 3: Apply detect_face() function on each frame

Step 4: Display the video frame with rectangles around detected faces

# PROGRAM:

# Name : YOGAMAHENDRAN G
# Reg no : 212225040500

```
import cv2
import matplotlib.pyplot as plt
%matplotlib inline

withglass = cv2.imread('/content/Screenshot 2025-11-13 212818.png', 0)
group = cv2.imread('/content/Screenshot 2025-11-13 213045.png', 0)

plt.imshow(withglass, cmap='gray')
plt.title("With Glasses")
plt.show()

plt.imshow(group, cmap='gray')
plt.title("Group Image")
plt.show()

face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_frontalface_default.xml')
eye_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_eye.xml')

if face_cascade.empty():
    raise IOError("Error loading face cascade XML file")
if eye_cascade.empty():
    raise IOError("Error loading eye cascade XML file")

def detect_face(img, scaleFactor=1.1, minNeighbors=5):
    face_img = img.copy()
    face_rects = face_cascade.detectMultiScale(face_img, scaleFactor=scaleFactor, minNeighbors=minNeighbors)
    for (x, y, w, h) in face_rects:
        cv2.rectangle(face_img, (x, y), (x + w, y + h), (255, 255, 255), 2)
    return face_img

def detect_eyes(img):
    face_img = img.copy()
    eyes = eye_cascade.detectMultiScale(face_img)
    for (x, y, w, h) in eyes:
        cv2.rectangle(face_img, (x, y), (x + w, y + h), (255, 255, 255), 2)
    return face_img

result_withglass_faces = detect_face(withglass)
plt.imshow(result_withglass_faces, cmap='gray')
plt.title("Faces in With Glasses Image")
plt.show()

result_group_faces = detect_face(group)
plt.imshow(result_group_faces, cmap='gray')
plt.title("Faces in Group Image")
plt.show()

result_withglass_eyes = detect_eyes(withglass)
plt.imshow(result_withglass_eyes, cmap='gray')
plt.title("Eyes in With Glasses Image")
plt.show()

result_group_eyes = detect_eyes(group)
plt.imshow(result_group_eyes, cmap='gray')
plt.title("Eyes in Group Image")
plt.show()

```
# OUTPUT:



<img width="425" height="363" alt="513971125-3bc33d15-7567-45e2-aefa-6a97dd496ad5" src="https://github.com/user-attachments/assets/b3e67277-64ba-4438-89b0-699cc0f64ec2" />
<img width="290" height="362" alt="513970977-0cb19cfb-796b-4332-82d2-63408c1f26ae" src="https://github.com/user-attachments/assets/d3a0d564-eb5b-4a82-a660-e11db58d0d17" />
<img width="397" height="357" alt="513970705-531cb320-53ec-4824-a649-8c7f3febaffa" src="https://github.com/user-attachments/assets/4de7cad4-ef33-427d-9ff0-582db78806bc" />
<img width="298" height="362" alt="513970485-af278112-473f-4c5f-b9d4-c643d5a7c339" src="https://github.com/user-attachments/assets/8b87e942-000f-4be8-be1f-67e8e72cf9e8" />
<img width="397" height="358" alt="513970148-26cbe3a2-ecd4-480d-9ce8-801d125a421b" src="https://github.com/user-attachments/assets/8b742c74-07f6-4e39-b56b-3f02be5eaba8" />
<img width="296" height="353" alt="513969930-22fc2707-d290-450e-817f-e553a7fc58d5" src="https://github.com/user-attachments/assets/108ae5b7-9fc5-48a1-82cf-3ed3feff9dfa" />

# RESULT:

Thus executed successfully.












Step 5: Exit loop and close windows when ESC key (key code 27) is pressed
Step 6: Release video capture and destroy all OpenCV windows
Program
