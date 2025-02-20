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

```bash
pip install opencv-python imgbeddings psycopg2-binary
