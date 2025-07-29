# Silento-Emergency-Alert-
FILE: main.py

from gesture_detector import detect_blink_gesture from location_sender import send_alert from gui import start_gui

if name == "main": print("Starting Silento Emergency Alert System...")

blink_detected = detect_blink_gesture()

if blink_detected:
    print("Emergency gesture detected!")
    send_alert()
    start_gui()
else:
    print("No emergency detected.")

FILE: gesture_detector.py

def detect_blink_gesture(): print("Simulating blink gesture detection...") user_input = input("Did user blink 3 times? (y/n): ").strip().lower() return user_input == 'y'

FILE: location_sender.py

import geocoder import smtplib from email.mime.text import MIMEText

def get_location(): g = geocoder.ip('me') lat, lng = g.latlng print(f"Location found: {lat}, {lng}") return f"https://www.google.com/maps?q={lat},{lng}"

def send_alert(): location_url = get_location() sender = "youremail@example.com" receiver = "trusted@example.com" password = "your-app-password"  # Use App Password or OAuth

subject = "Emergency Alert - SILENTO"
body = f"Emergency Triggered!\nLocation: {location_url}"

msg = MIMEText(body)
msg['Subject'] = subject
msg['From'] = sender
msg['To'] = receiver

try:
    server = smtplib.SMTP_SSL('smtp.gmail.com', 465)
    server.login(sender, password)
    server.sendmail(sender, receiver, msg.as_string())
    server.quit()
    print("Alert sent successfully to trusted contact.")
except Exception as e:
    print("Failed to send alert:", e)

FILE: gui.py

from tkinter import *

def start_gui(): root = Tk() root.title("Silento Emergency") root.geometry("300x150")

Label(root, text="\ud83d\udea8 Emergency Alert Sent!", font=("Arial", 14)).pack(pady=20)
Button(root, text="Close", command=root.destroy).pack(pady=10)

root.mainloop()

FILE: requirements.txt

geocoder tk

FILE: README.md

SILENTO - Silent Emergency Alert System

\ud83d\udd12 Description

Silento is a silent emergency alert system that uses AI gestures like eye blinks or hand signs to detect danger and sends your real-time location to a trusted contact via email or SMS.

\ud83d\ude80 Features

Gesture-triggered alerts

Live IP-based GPS location

GUI notification

No noise or physical button needed


\ud83d\udca0 Tech Stack

Python

OpenCV (optional for gesture)

Geocoder

smtplib (Email)

Tkinter GUI


\ud83e\uddea How to Run

1. Install dependencies:



pip install -r requirements.txt

2. Set your email and password in location_sender.py


3. Run the system:



python main.py

\u2705 Output Example

Starting Silento Emergency Alert System...
Simulating blink gesture detection...
Emergency gesture detected!
Location found: 11.0082, 76.9616
Alert sent successfully to trusted contact.

\ud83d\udccc Future Scope

Real-time OpenCV detection

WhatsApp API integration

Flutter mobile version



