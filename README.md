# Facial Recognition with OpenCV and PostgreSQL

## Overview

This project performs facial recognition using **OpenCV's Haar Cascade**, extracts facial embeddings using **imgbeddings**, and stores the embeddings in a **PostgreSQL database**. The goal is to identify and match faces based on stored facial embeddings.

## Requirements

Ensure you have the following installed:

- Python 3.x
- OpenCV
- imgbeddings
- psycopg2-binary
- PostgreSQL (Aiven Cloud-hosted in this case)

## Installation

To install the necessary dependencies, run:

```
pip install opencv-python imgbeddings psycopg2-binary
```

## Project Structure
```
FacialRecognition/
│── haarcascade_frontalface_default.xml
│── oppenheimer-cast.jpg
│── florence_pugh.jpg
│── stored-faces/
│── FacialRecog1.ipynb
│── README.md
```
## How it works
1. Face Detection
   - OpenCV loads a Haar Cascade model to detect faces in an image.
   - Detected faces are cropped and saved in the stored-faces/ directory.
2. Embedding Generation & Database Storage
   -  Each cropped face is processed using imgbeddings to generate an embedding.
   -  The embeddings and filenames are inserted into a PostgreSQL database.
3. Face Matching
   - A new image is processed and compared with stored embeddings.
   - The closest match is retrieved from the database using a similarity metric.
   - The matching face is displayed.

## Usage
1. Open the Notebook
Run the following command to start Jupyter Notebook:
```
jupyter notebook
```
Open FacialRecog1.ipynb and execute the cells step by step.

2. Detect Faces & Store Embeddings
Execute the notebook cells to:
- Detect faces in oppenheimer-cast.jpg
- Store cropped face images in stored-faces/
- Generate embeddings and store them in the PostgreSQL database

3. Match a Face
Run the corresponding notebook cell to:
- Compute the embedding for florence_pugh.jpg
- Compare it with stored embeddings in the database
- Display the closest match

## Database Connection
The PostgreSQL database is hosted on Aiven.

Ensure your database schema has a pictures table:
```
CREATE TABLE pictures (
    filename TEXT PRIMARY KEY,
    embedding VECTOR(512)
);
```

## Notes
- The haarcascade_frontalface_default.xml file is used for face detection.
- The PostgreSQL database stores face embeddings as vectors.
- The similarity metric used is the L2 distance (<-> operator in PostgreSQL).
