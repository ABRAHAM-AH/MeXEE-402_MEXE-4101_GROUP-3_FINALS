# MeXEE-402_MEXE-4101_GROUP-3_FINALS

### Clone the GitHub repository
```
!git clone https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS.git
```
### Install the face_recognition library
```
!pip install face_recognition
```
### Change directory to the cloned repository
```
%cd MeXEE-402_MEXE-4101_GROUP-3_FINALS
```
### Setting up Face Recognition
```
import face_recognition
import numpy as np
from google.colab.patches import cv2_imshow
import cv2
```
### Creating the encoding profiles
```
face_1 = face_recognition.load_image_file("Dr. Tirso Ronquillo.png")
face_1_encoding = face_recognition.face_encodings(face_1)[0]

face_2 = face_recognition.load_image_file("Angelo Jimenez.jpg")
face_2_encoding = face_recognition.face_encodings(face_2)[0]

face_3 = face_recognition.load_image_file("Br. Bernard Oca.jpg")
face_3_encoding = face_recognition.face_encodings(face_3)[0]

face_4 = face_recognition.load_image_file("Dr. Dodjie Maestrecampo.png")
face_4_encoding = face_recognition.face_encodings(face_4)[0]

face_5 = face_recognition.load_image_file("Fr. Roberto Yap.jpg")
face_5_encoding = face_recognition.face_encodings(face_5)[0]
```
### List of facial encodings for known individuals
```
known_face_encodings = [
                        face_1_encoding,
                        face_2_encoding,
                        face_3_encoding,
                        face_4_encoding,
                        face_5_encoding
]
```
### Corresponding names for the known facial encodings
```
known_face_names = [
                    "Dr.Tirso Ronquillo",
                    "Angelo Jimenez",
                    "Br.Bernard Oca",
                    "Dr.Dodjie Maestrecampo",
                    "Fr.Roberto Yap"
]
```
### File name of the unknown image
```
file_name = "file name of the image"
```
### Load the unknown image for face recognition
```
unknown_image = face_recognition.load_image_file(file_name)
unknown_image_to_draw = cv2.imread(file_name)
```
### Detect face locations and encodings in the unknown image
```
face_locations = face_recognition.face_locations(unknown_image)
face_encodings = face_recognition.face_encodings(unknown_image, face_locations)
```
### Loop through detected faces and compare with known faces
```
for (top,right, bottom, left), face_encoding in zip(face_locations, face_encodings):
```
### Compare the face encoding with known face encodings
```
      matches = face_recognition.compare_faces(known_face_encodings, face_encoding)
```
### Default name for an unknown face
```
      name = "Unknown"
```
### Calculate face distances and find the best match
 ```
      face_distances = face_recognition.face_distance(known_face_encodings, face_encoding)
      best_match_index = np.argmin(face_distances)
```
### If there is a match, update the name
```
      if matches[best_match_index]:
        name = known_face_names[best_match_index]
```
### Draw rectangle and display the name on the image
 ```
# For Green Rectangle
      cv2.rectangle(unknown_image_to_draw, (left, top), (right, bottom),(0,255,0),3)
      cv2.putText(unknown_image_to_draw,name, (left, top-20), cv2.FONT_HERSHEY_SIMPLEX,1,(255,255,255),2, cv2.LINE_AA)
# For Red Rectangle
      cv2.rectangle(unknown_image_to_draw, (left, top), (right, bottom),(0,0,255),3)
      cv2.putText(unknown_image_to_draw,name, (left, top-20), cv2.FONT_HERSHEY_SIMPLEX,1,(255,255,255),2, cv2.LINE_AA)
```
### Display the annotated image with face recognition results
```
cv2_imshow(unknown_image_to_draw)
```

# Known Images
<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/7ae4049f-5246-4bfd-9df7-7975976c85ac.png" width="500" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/4215d911-ac8d-4eee-af60-dea9c5fa6b25.jpg" width="500" height="700">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/e184f65b-b98c-4098-8265-2e37ab3a8e71.jpg" width="500" height="600">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/1e3ef5e3-43e2-4352-8c38-460dca63ae23.png" width="500" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/dabaa64a-f096-4695-9d7c-67c6de180325.jpg" width="350" height="500">
</div>

# Unknown Images
<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/935dc334-e013-43f1-ace2-52f3988778e4.png" width="500" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/41349421-4894-4a32-a58c-47689bb77bae.jpg" width="500" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/33d450c6-bc5f-4478-b97a-a4e7b25b6cc9.png" width="400" height="600">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/beb5527a-b947-49eb-abb1-edb4ce2620d5.jpg" width="600" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/195c8c2a-0888-4cb8-9919-4bb9086543df.jpeg" width="500" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/4e49f46e-c9a8-42e8-84d1-f6c9cb158095.jpg" width="500" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/83cb97e6-3618-4f05-9486-26b7e9a010a9.jpg" width="500" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/fd81fcce-c323-4242-8ac8-35e91f92b64a.jpg" width="500" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/7823d5a8-67b3-45cc-82d9-2b6d042caf32.jpg" width="500" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/3386b7e4-5e28-4c8a-8c97-33f310069c03.jpg" width="600" height="500">
</div>

