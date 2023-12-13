# MeXEE-402_MEXE-4101_GROUP-3_FINALS

!git clone https://github.com/ABRAHAM-AH/MeXEE-402_MEXE-4101_GROUP-3_FINALS.git

!pip install face_recognition

%cd MeXEE-402_MEXE-4101_GROUP-3_FINALS

import face_recognition

import numpy as np

from google.colab.patches import cv2_imshow

import cv2

## Creating the encoding profiles

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


## List of facial encodings for known individuals

known_face_encodings = [

                        face_1_encoding,
                        
                        face_2_encoding,
                        
                        face_3_encoding,
                        
                        face_4_encoding,
                        
                        face_5_encoding
                        
]


## Corresponding names for the known facial encodings

known_face_names = [

                    "Dr.Tirso Ronquillo",
                    
                    "Angelo Jimenez",
                    
                    "Br.Bernard Oca",
                    
                    "Dr.Dodjie Maestrecampo",
                    
                    "Fr.Roberto Yap"
                    
]
