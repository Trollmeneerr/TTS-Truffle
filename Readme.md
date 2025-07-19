## TTS Twitch and Truffle

## ✨ Features

* Text-to-speech for Twitch & Truffle chat
* Filters out banned messages
* Easy to switch between TTS voice models
* Fast response time using local Piper models
* Fully customizable and open-source

TTS Twitch and Truffle is a tool that reads messages from Twitch or Truffle chat out loud using Piper TTS. 

**Not available for Youtube right now!**

It's perfect for streamers who want chat interactions to be heard in real time.

Clone the Repository
Start by cloning this GitHub repository:

    # Using git
    git clone https://github.com/Trollmeneerr/TTS-Twitch-and-Truffle.git
    cd TTS-Twitch-and-Truffle

## Install Python 3.10

This project requires Python 3.10. **Other versions (like 3.11 or 3.12) are not Tested and may break the application.**

Download Python 3.10 from the official page:
    
    https://www.python.org/downloads/release/python-31012/

-**Important: During installation, check the box that says:
"Add Python to PATH"**

Verify the installation:

    python --version
    # or
    python3 --version
Should return: Python 3.10.x

## Python Packages

(Optional) Create a Virtual Environment:

    # Run in terminal

    python -m venv venv
    venv\Scripts\activate

Install Requirements:

    # Run in terminal

    pip install -r requirements.txt

Make sure your terminal is in the project directory when running this command.

## Install Google Chrome or Chrome for Testing

You must have a working version of Google Chrome **OR** Chrome for Testing.

**You don't need both**

Option 1: Google Chrome
Download from: 

    https://www.google.com/chrome/

Option 2: Chrome for Testing (If you don't want chrome or don't have it)
Download from: 

    https://googlechromelabs.github.io/chrome-for-testing/

Ensure you also have the correct version of ChromeDriver that matches your browser version.

## Set Your Chat URL
Edit TTS.py and look for this Section:

    # ─── CONFIG ───────────────────────────────────────
    PIPER_EXE     = "./piper/piper.exe" 
    PIPER_MODEL   = "./models/en_US-amy-medium.onnx"
    SITE          = "https://twitch.tv/YOURCHANNEL"     <-----------
    SPOKEN_FILE   = "spoken_messages.json"`
    LINK_PATTERN  = re.compile(r"https?://\S+|www\.\S+")

Change it to your own Twitch or Truffle chat URL:

    site = "https://www.twitch.tv/YOUR_CHANNEL_NAME"
    # or
    site = "https://chat.truffle.vip/browser-source/your-org/scene-x"

## Create filter.json
The reason why i can't add this, is because there are words in there that i can't openly share on github, but i have made some instructions here to create your own!

Create a file in the root of the project called "filter.json" with the following format:

    {
    "banned_words": ["Example1", "Example2", "Example3"]
    }

This will filter out inappropriate messages from being spoken.

P.S. It can trigger false positives in my case i had 95% accuracy!

## (OPTIONAL) Install other Piper TTS Models

You can find models at:

    https://huggingface.co/rhasspy/piper-voices

Choose a model (example: downloaded-medium)

Download and extract it into the models/ folder:

    models/
    ├── downloaded_model-medium.onnx       | Model
    └── downloaded_model-medium.onnx.json  | Config

Edit TTS.py and look for this Section:

    #─── CONFIG ──────────────────────────────────────
    PIPER_EXE     = "./piper/piper.exe"
    PIPER_MODEL   = "./models/en_US-amy-medium.onnx"    <-----------
    SITE          = "https://twitch.tv/YOURCHANNEL"     
    SPOKEN_FILE   = "spoken_messages.json"
    LINK_PATTERN  = re.compile(r"https?://\S+|www\.\S+")

And change it to you prefferd voice model you want to use, for example:

    PIPER_MODEL = "./models/donwloaded_model-medium.onnx"

The config file should be automatically be loaded aswel

## Run the Program

After everything is configured you can run the program in your terminal like this:

    # MAKE SURE YOUR IN: path-to-folder/TTS-Twitch-and-Truffle:
    Python.exe -m TTS
    or
    Python3 -m TTS



Once running it will connect to the specified chat URL.

New messages will be read aloud using your selected TTS voice.

You might see messages like this in your terminal:

    [ERROR:device_event_log_impl.cc:198] USB: SetupDiGetDeviceProperty failed
    [ERROR:registration_request.cc:291] Registration response error message: PHONE_REGISTRATION_ERROR

These are Chrome-related debug messages and can be safely ignored.

🙌 Credits

Piper TTS

Vibe Coded by @Trollmeneerr