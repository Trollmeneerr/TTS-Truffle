## TTS Twitch and Truffle

TTS Twitch and Truffle is a tool that reads messages from Twitch or Truffle chat out loud using Piper TTS. It's perfect for streamers who want chat interactions to be heard in real time.
Clone the Repository
Start by cloning this GitHub repository:
git clone https://github.com/Trollmeneerr/TTS-Twitch-and-Truffle.git
cd TTS-Twitch-and-Truffle

## Install Python 3.10

This project requires Python 3.10. Other versions (like 3.11 or 3.12) are not Tested and may break the application.

How to Install Python 3.10:
Download Python 3.10 from the official page:
https://www.python.org/downloads/release/python-31012/

Run the installer.
Important: During installation, check the box that says:
"Add Python to PATH"
Verify the installation:
python --version
or
python3 --version
Should return: Python 3.10.12

## Python Packages

(Optional) Create a Virtual Environment:
python -m venv venv
For Windows: venv\Scripts\activate

Install Requirements:
pip install -r requirements.txt
Make sure your terminal is in the project directory when running this command.

## Install Google Chrome or Chrome for Testing

You must have a working version of Google Chrome OR Chrome for Testing.

Option 1: Google Chrome
Download from: https://www.google.com/chrome/

Option 2: Chrome for Testing (If you don't want chrome or don't have it)
Download from: https://googlechromelabs.github.io/chrome-for-testing/

Ensure you also have the correct version of ChromeDriver that matches your browser version.

## Set Your Chat URL
Open TTS.py and look for this Section:
CONFIG ─────────────────────────────────────────
PIPER_EXE     = "./piper/piper.exe"
PIPER_MODEL   = "./models/en_US-amy-medium.onnx"
SITE          = "https://twitch.tv/YOURCHANNEL"     <-----------
SPOKEN_FILE   = "spoken_messages.json"

Change it to your own Twitch or Truffle chat URL:

site = "https://www.twitch.tv/YOUR_CHANNEL_NAME"
or
site = "https://chat.truffle.vip/browser-source/your-org/scene-x"

## Create filter.json
The reason why i can't add this, is because there are words in there that i can't openly share on github. But i have made some instructions here to create your own!
Create a file in the root of the project called "filter.json" with the following format:

{
  "banned_words": ["slur", "swear", "filterd_word"]
}

This will filter out inappropriate messages from being spoken.

## (OPTIONAL) Install other Piper TTS Models

Go to: https://huggingface.co/rhasspy/piper-voices

Choose a model (example: en_US-amy-low)

Download and extract it into the models/ folder:

models/
    ├── donwloaded_model-medium.onnx       | Model
    └── donwloaded_model-medium.onnx.json  | Config

Open TTS.py and look for this Section:
CONFIG ─────────────────────────────────────────
PIPER_EXE     = "./piper/piper.exe"
PIPER_MODEL   = "./models/en_US-amy-medium.onnx"
SITE          = "https://twitch.tv/YOURCHANNEL"     <-----------
SPOKEN_FILE   = "spoken_messages.json"

And change it to you prefferd voice model you want to use, for example:
PIPER_MODEL = "./models/donwloaded_model-medium.onnx"

The config file should be automatically be loaded aswel

## Run the Program

After everything is configured you can run the program in your terminal like this:
Python.exe -m TTS
or
Python3 -m TTS

MAKE SURE YOUR IN: path-to-folder/TTS-Twitch-and-Truffle:

Once running it will connect to the specified chat URL.
New messages will be read aloud using your selected TTS voice.

You might also get a few errors from chrome like:
[31844:17848:0719/025158.469:ERROR:components\device_event_log\device_event_log_impl.cc:198] [02:51:58.468] USB: usb_service_win.cc:105 SetupDiGetDeviceProperty({{A45C254E-DF1C-4EFD-8020-67D146A850E0}, 6}) failed: Element not found. (0x490)
[31844:28552:0719/025158.760:ERROR:google_apis\gcm\engine\registration_request.cc:291] Registration response error message: PHONE_REGISTRATION_ERROR
[31844:28552:0719/025158.761:ERROR:google_apis\gcm\engine\registration_request.cc:291] Registration response error message: PHONE_REGISTRATION_ERROR
[31844:28552:0719/025158.761:ERROR:google_apis\gcm\engine\registration_request.cc:291] Registration response error message: PHONE_REGISTRATION_ERROR

THIS IS NORMAL AND ISN'T ANYTHING TO WORRY ABOUT

🙌 Credits

Piper TTS

Vibe Coded by @Trollmeneerr