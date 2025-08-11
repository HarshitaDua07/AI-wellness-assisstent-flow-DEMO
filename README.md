# AI-wellness-assisstent-flow-DEMO
A simple FastAPI application that extracts symptoms from user input and returns possible related medical conditions.
This is not a diagnosis tool — for educational purposes only.

Features
Detects symptoms from a predefined keyword list.

Suggests related conditions based on matching symptoms.

Runs on Google Colab using ngrok for public access.

How to Run (Google Colab)
Clone this repository or copy the code into a Google Colab notebook.

Install dependencies:
!pip install fastapi uvicorn pyngrok nest_asyncio requests

Run the FastAPI server:

import nest_asyncio
from pyngrok import ngrok
import uvicorn
nest_asyncio.apply()
public_url = ngrok.connect(8000)
print("Public URL:", public_url)
uvicorn.run(app, host="0.0.0.0", port=8000)

Use the generated ngrok public URL to send requests.


import requests
url = "https://<ngrok-url>/api/v1/message"
user_message = input("Enter your message: ")
payload = {"text": user_message, "user_id": "demo_user"}
r = requests.post(url, json=payload)
print(r.json())

{
  "entities": ["tired", "dizzy"],
  "conditions": [
    {"condition": "Anemia", "score": 1},
    {"condition": "Chronic Fatigue Syndrome", "score": 1},
    {"condition": "Depression", "score": 1},
    {"condition": "Hypotension", "score": 1},
    {"condition": "Dehydration", "score": 1},
    {"condition": "Vertigo", "score": 1}
  ]
}
