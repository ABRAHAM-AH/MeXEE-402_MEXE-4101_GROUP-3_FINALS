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
### File name of the image
```
file_name = "file name of the image"
```
### Load the image for face recognition
```
unknown_image = face_recognition.load_image_file(file_name)
unknown_image_to_draw = cv2.imread(file_name)
```
### Detect face locations and encodings in the image
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

<p>𝐀𝐬 𝐭𝐡𝐞 𝐩𝐫𝐞𝐬𝐢𝐝𝐞𝐧𝐭𝐬 𝐨𝐟 𝐭𝐡𝐞𝐢𝐫 𝐫𝐞𝐬𝐩𝐞𝐜𝐭𝐢𝐯𝐞 𝐮𝐧𝐢𝐯𝐞𝐫𝐬𝐢𝐭𝐢𝐞𝐬, 𝐃𝐫. 𝐓𝐢𝐫𝐬𝐨 𝐑𝐨𝐧𝐪𝐮𝐢𝐥𝐥𝐨 𝐨𝐟 𝐁𝐚𝐭𝐚𝐧𝐠𝐚𝐬 𝐒𝐭𝐚𝐭𝐞 𝐔𝐧𝐢𝐯𝐞𝐫𝐬𝐢𝐭𝐲, 𝐀𝐧𝐠𝐞𝐥𝐨 𝐉𝐢𝐦𝐞𝐧𝐞𝐳 𝐨𝐟 𝐭𝐡𝐞 𝐔𝐧𝐢𝐯𝐞𝐫𝐬𝐢𝐭𝐲 𝐨𝐟 𝐭𝐡𝐞 𝐏𝐡𝐢𝐥𝐢𝐩𝐩𝐢𝐧𝐞𝐬, 𝐁𝐫. 𝐁𝐞𝐫𝐧𝐚𝐫𝐝 𝐎𝐜𝐚 𝐨𝐟 𝐃𝐞 𝐋𝐚 𝐒𝐚𝐥𝐥𝐞 𝐔𝐧𝐢𝐯𝐞𝐫𝐬𝐢𝐭𝐲, 𝐃𝐫. 𝐃𝐨𝐝𝐣𝐢𝐞 𝐌𝐚𝐞𝐬𝐭𝐫𝐞𝐜𝐚𝐦𝐩𝐨 𝐨𝐟 𝐌𝐚𝐩ú𝐚 𝐔𝐧𝐢𝐯𝐞𝐫𝐬𝐢𝐭𝐲, 𝐚𝐧𝐝 𝐅𝐫. 𝐑𝐨𝐛𝐞𝐫𝐭𝐨 𝐘𝐚𝐩 𝐨𝐟 𝐀𝐭𝐞𝐧𝐞𝐨 𝐝𝐞 𝐌𝐚𝐧𝐢𝐥𝐚 𝐔𝐧𝐢𝐯𝐞𝐫𝐬𝐢𝐭𝐲 𝐩𝐥𝐚𝐲 𝐚𝐧 𝐢𝐦𝐩𝐨𝐫𝐭𝐚𝐧𝐭 𝐫𝐨𝐥𝐞 𝐢𝐧 𝐬𝐡𝐚𝐩𝐢𝐧𝐠 𝐭𝐡𝐞𝐢𝐫 𝐞𝐝𝐮𝐜𝐚𝐭𝐢𝐨𝐧𝐚𝐥 𝐢𝐧𝐬𝐭𝐢𝐭𝐮𝐭𝐢𝐨𝐧𝐬' 𝐚𝐜𝐚𝐝𝐞𝐦𝐢𝐜 𝐚𝐧𝐝 𝐢𝐧𝐬𝐭𝐢𝐭𝐮𝐭𝐢𝐨𝐧𝐚𝐥 𝐬𝐞𝐭𝐭𝐢𝐧𝐠𝐬. 𝐓𝐡𝐞𝐲 𝐚𝐫𝐞 𝐫𝐞𝐬𝐩𝐨𝐧𝐬𝐢𝐛𝐥𝐞 𝐟𝐨𝐫 𝐟𝐨𝐬𝐭𝐞𝐫𝐢𝐧𝐠 𝐚 𝐯𝐢𝐛𝐫𝐚𝐧𝐭 𝐥𝐞𝐚𝐫𝐧𝐢𝐧𝐠 𝐞𝐧𝐯𝐢𝐫𝐨𝐧𝐦𝐞𝐧𝐭, 𝐞𝐧𝐬𝐮𝐫𝐢𝐧𝐠 𝐚𝐜𝐚𝐝𝐞𝐦𝐢𝐜 𝐞𝐱𝐜𝐞𝐥𝐥𝐞𝐧𝐜𝐞, 𝐚𝐧𝐝 𝐠𝐮𝐢𝐝𝐢𝐧𝐠 𝐭𝐡𝐞 𝐬𝐭𝐫𝐚𝐭𝐞𝐠𝐢𝐜 𝐝𝐢𝐫𝐞𝐜𝐭𝐢𝐨𝐧 𝐨𝐟 𝐭𝐡𝐞𝐢𝐫 𝐮𝐧𝐢𝐯𝐞𝐫𝐬𝐢𝐭𝐢𝐞𝐬. 𝐓𝐡𝐞𝐬𝐞 𝐥𝐞𝐚𝐝𝐞𝐫𝐬 𝐚𝐫𝐞 𝐜𝐨𝐦𝐦𝐢𝐭𝐭𝐞𝐝 𝐭𝐨 𝐮𝐩𝐡𝐨𝐥𝐝𝐢𝐧𝐠 𝐭𝐡𝐞 𝐯𝐚𝐥𝐮𝐞𝐬 𝐚𝐧𝐝 𝐭𝐫𝐚𝐝𝐢𝐭𝐢𝐨𝐧𝐬 𝐨𝐟 𝐭𝐡𝐞𝐢𝐫 𝐢𝐧𝐬𝐭𝐢𝐭𝐮𝐭𝐢𝐨𝐧𝐬 𝐰𝐡𝐢𝐥𝐞 𝐚𝐝𝐚𝐩𝐭𝐢𝐧𝐠 𝐭𝐨 𝐭𝐡𝐞 𝐞𝐯𝐨𝐥𝐯𝐢𝐧𝐠 𝐧𝐞𝐞𝐝𝐬 𝐨𝐟 𝐭𝐡𝐞 𝐚𝐜𝐚𝐝𝐞𝐦𝐢𝐜 𝐜𝐨𝐦𝐦𝐮𝐧𝐢𝐭𝐲 𝐚𝐧𝐝 𝐬𝐨𝐜𝐢𝐞𝐭𝐲 𝐚𝐭 𝐥𝐚𝐫𝐠𝐞. 𝐓𝐡𝐫𝐨𝐮𝐠𝐡 𝐭𝐡𝐞𝐢𝐫 𝐥𝐞𝐚𝐝𝐞𝐫𝐬𝐡𝐢𝐩, 𝐭𝐡𝐞𝐲 𝐜𝐨𝐧𝐭𝐫𝐢𝐛𝐮𝐭𝐞 𝐬𝐢𝐠𝐧𝐢𝐟𝐢𝐜𝐚𝐧𝐭𝐥𝐲 𝐭𝐨 𝐭𝐡𝐞 𝐝𝐞𝐯𝐞𝐥𝐨𝐩𝐦𝐞𝐧𝐭 𝐨𝐟 𝐟𝐮𝐭𝐮𝐫𝐞 𝐠𝐞𝐧𝐞𝐫𝐚𝐭𝐢𝐨𝐧𝐬 𝐨𝐟 𝐬𝐭𝐮𝐝𝐞𝐧𝐭𝐬 𝐚𝐧𝐝 𝐭𝐡𝐞 𝐚𝐝𝐯𝐚𝐧𝐜𝐞𝐦𝐞𝐧𝐭 𝐨𝐟 𝐤𝐧𝐨𝐰𝐥𝐞𝐝𝐠𝐞 𝐰𝐢𝐭𝐡𝐢𝐧 𝐭𝐡𝐞𝐢𝐫 𝐫𝐞𝐬𝐩𝐞𝐜𝐭𝐢𝐯𝐞 𝐮𝐧𝐢𝐯𝐞𝐫𝐬𝐢𝐭𝐢𝐞𝐬.</p>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/3a317468-6e9c-40bb-9106-d04783f70b6c.png" width="800" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143602067/db7ae171-bcd2-4fc3-85e2-f101a29b69b2.png" width="800" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143602067/ef8f8901-61fb-413e-8323-9ee45399d44e.png" width="800" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143602067/e9b99401-02b3-4ff1-bfd3-6ad84b18a251.png" width="800" height="500">
</div>

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143602067/01aa238d-7532-46b5-8435-fe5901664be4.png" width="800" height="500">
</div>

# Unknown Images

### Image 1
*An analysis of the image “Image 1.png” using an advanced face recognition algorithm revealed faces that are not recognized.*

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/935dc334-e013-43f1-ace2-52f3988778e4.png" width="600" height="500">
</div>

### Image 2
*An analysis of the image “Image 2.jpg” using an advanced face recognition algorithm revealed faces that are not recognized.*

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/41349421-4894-4a32-a58c-47689bb77bae.jpg" width="500" height="500">
</div>

### Image 3
*An analysis of the image “Image 3.png” using an advanced face recognition algorithm revealed faces that are not recognized.*

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/33d450c6-bc5f-4478-b97a-a4e7b25b6cc9.png" width="450" height="600">
</div>

### Image 4
*An analysis of the image “Image 4.jpg” using an advanced face recognition algorithm revealed faces that are not recognized.*

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/beb5527a-b947-49eb-abb1-edb4ce2620d5.jpg" width="650" height="500">
</div>

### Image 5
*An analysis of the image “Image 5.jpeg” using an advanced face recognition algorithm revealed faces that are not recognized.*

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/195c8c2a-0888-4cb8-9919-4bb9086543df.jpeg" width="500" height="500">
</div>

### Image 6
*An analysis of the image “Image 6.jpg” using an advanced face recognition algorithm revealed faces that are not recognized.*

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/4e49f46e-c9a8-42e8-84d1-f6c9cb158095.jpg" width="500" height="500">
</div>

### Image 7
*An analysis of the image “Image 7.jpg” using an advanced face recognition algorithm revealed faces that are not recognized.*

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/83cb97e6-3618-4f05-9486-26b7e9a010a9.jpg" width="500" height="500">
</div>

### Image 8
*An analysis of the image “Image 8.jpg” using an advanced face recognition algorithm revealed faces that are not recognized.*

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/fd81fcce-c323-4242-8ac8-35e91f92b64a.jpg" width="500" height="500">
</div>

### Image 9
*An analysis of the image “Image 9.jpg” using an advanced face recognition algorithm revealed faces that are not recognized.*

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/7823d5a8-67b3-45cc-82d9-2b6d042caf32.jpg" width="500" height="500">
</div>

### Image 10
*An analysis of the image “Image 10.jpg” using an advanced face recognition algorithm revealed faces that are not recognized.*

<div align="center">
  <img src="https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS/assets/143601880/3386b7e4-5e28-4c8a-8c97-33f310069c03.jpg" width="600" height="500">
</div>

