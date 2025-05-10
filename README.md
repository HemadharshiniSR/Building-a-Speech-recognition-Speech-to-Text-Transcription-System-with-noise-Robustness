# Building-a-Speech-recognition-Speech-to-Text-Transcription-System-with-noise-Robustness
This project implements a basic Speech-to-Text Transcription System in Python using the speech_recognition library. The system captures audio input from a microphone and transcribes it into text using the Google Web Speech API.

🧠 Features
🎙️ Real-time speech recognition via microphone

🔊 Handles background noise with adjustable sensitivity

🌐 Uses Google's robust online speech recognition API

❌ Graceful handling of unrecognized or erroneous speech

🛠️ Requirements
Python 3.6+

Libraries:

speechrecognition

pyaudio (for microphone input)

Install dependencies:

bash
Copy
Edit
pip install SpeechRecognition pyaudio
If you face issues installing pyaudio, try:

bash
Copy
Edit
pip install pipwin
pipwin install pyaudio
📦 Installation
Clone the repository:

PIP INSTALL
git clone https://github.com/hemadharshini/speech-recognition-system.git
cd speech-recognition-system
Install the required packages (see above).


Run the script:
python speech_to_text.py
You’ll be prompted to speak. The system listens, then prints what it recognized:

Output
Please say something...
You said: Hello world
If the speech is not understood:


Sorry, I could not understand the audio.
If there's an issue with the API:

csharp
Could not request results from Google API.

🧰 Code Overview
python

import speech_recognition as sr

recognizer = sr.Recognizer()

with sr.Microphone() as source:
    print("Please say something...")
    
    # Improve noise robustness
    recognizer.adjust_for_ambient_noise(source)
    
    audio = recognizer.listen(source)

    try:
        text = recognizer.recognize_google(audio)
        print("You said: " + text)
    except sr.UnknownValueError:
        print("Sorry, I could not understand the audio.")
    except sr.RequestError:
        print("Could not request results from Google API.")
🧪 Noise Robustness Tips
Use recognizer.adjust_for_ambient_noise(source, duration=1) before listening to calibrate for background noise.

Use a quality microphone.

Test in various environments for real-world robustness.

📌 TODO
Add offline recognition using CMU Sphinx

Implement GUI using Tkinter or PyQT

Save transcriptions to text files

Add language support

📄 License
This project is open source and available under the MIT License.

