 Malaria Detection Web App (Colab Deployed)
       This project is a web-enabled deep learning system for detecting malaria-infected blood cells using InceptionV3 (Keras).
      It runs completely in Google Colab, making it lightweight and accessible without local setup. Deployment is handled via Flask and ngrok.

 About the Project
We developed and deployed a malaria detection system that uses a trained CNN to identify whether a blood smear image shows infected or uninfected cells.
A web interface built using Flask is accessible via ngrok and runs entirely inside a Colab notebook. The app supports single and multiple image uploads, real-time predictions, and CSV export.

Dataset
* Used NIH’s Malaria Cell Images Dataset (split into Parasitized and Uninfected folders)
* Dataset was processed within Colab
* Not included here due to size; use your own or load from Drive

System Architecture
1. Frontend (HTML via Flask)
o Web form for image upload
o Displays prediction with confidence score
2. Backend (Flask + Colab)
o Runs inside Colab
o Loads trained InceptionV3 model
o Accepts image input, preprocesses, and returns result
3. Deployment (Ngrok)
o Tunnels the Colab-hosted Flask app to the web
o Public URL is generated automatically

 Project Structure

malaria_colab/
??? app.ipynb              # Main notebook for Flask + ngrok deployment
??? real.ipynb             # Detailed app logic and HTML integration
??? InceptionV3.h5         # Trained Keras model file (loaded from Google Drive)
??? templates (inline)     # index.html and result.html defined as Python strings

 How to Run in Colab
1. Install Required Packages
python
!pip install flask pyngrok tensorflow pillow pandas

2. Mount Google Drive
python
from google.colab import drive
drive.mount('/content/drive')
Place your trained model (InceptionV3.h5) in your Drive.

3. Set Ngrok Token
python
!ngrok authtoken YOUR_NGROK_AUTH_TOKEN
Get your token from: https://dashboard.ngrok.com/get-started/setup

4. Launch the Web App
In the Colab notebook:
python
from pyngrok import ngrok
public_url = ngrok.connect(5000)
print(" * ngrok URL:", public_url)

!python app.py
Ngrok will output a URL like:
https://abc123.ngrok.io
Open this in your browser to access the app.

 Code Overview
 app.py logic inside notebook:
* Loads InceptionV3 model from Drive
* Defines routes for:
o / – landing page
o /index – image upload + prediction
o /download_csv – batch results export
* Embedded HTML via render_template_string() for portability

 Testing
1. Run app in Colab and access via ngrok
2. Upload .jpg / .png image(s)
3. View predicted class: Infected or Uninfected
4. If batch upload, download results as malaria_predictions.csv

Optional: Training Accuracy Visualization
python
import matplotlib.pyplot as plt
plt.plot(train_acc_list, label="Train")
plt.plot(val_acc_list, label="Validation")
plt.title("Model Accuracy Over Epochs")
plt.legend()
plt.grid()
plt.show()

 Authors
* Rajesh R
* Shenjin S A Solomon
* Santhosh Kumar S
* Tharun Raj R
Institution: Government College of Engineering, Dharmapuri
Supervisor: Mrs. R. Narmatha,M.E.,Assistant Professor

 Contact
Security Email Alert Sender: iamrajeshreddy@gmail.com

