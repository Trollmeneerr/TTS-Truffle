## ✨ Features

* Text-to-speech for Tuffle chat
* Filters out banned messages
* Easy to switch between TTS voice models
* Fast response time using local Piper models
* Fully customizable and open-source
* Fully customizable HOTKEYS

This is a tool that reads messages from Truffle chat out loud using Piper TTS. 

**Not available for Youtube or Twitch directly right now!**

It's perfect for streamers who want chat interactions to be heard in real time.

## Setting up truffle and repository
If you're new to Truffle, here’s a quick guide to get you started.

(Optional, but recommend) Install the extension from the Chrome Web Store:

    https://chromewebstore.google.com/detail/truffle/bkkjeefjfjcfdfifddmkdmcpmaakmelp?pli=1

**Setting Up Your Account**

* Go to https://app.truffle.vip
* Sign up and link your platforms (like Twitch, YouTube, etc.)
* Create an organization
* In your org, go to Apps enable chat

**Configure the Chat App**
* Go to Settings of the chat App
* Click on Manage OBS 
* Create a scene
* Copy the Browser Source Link
* Enable Hide old messaged [90s]

**You can skip customizing the chat if you don't want to use it**

Clone the Repository
Start by cloning this GitHub repository:

    # Using git
    git clone https://github.com/Trollmeneerr/TTS-Truffle.git
    cd TTS-Truffle

## Install Python 3.10

This project requires Python 3.10. **Other versions (like 3.11 or 3.12) are not Tested and may break the application.**

Download Python 3.10 from the official page:
    
    https://www.python.org/downloads/release/python-31012/

-**Important: During installation, check the box that says:
"Add Python to PATH"**

Verify the installation:

    # Run in terminal

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
    SITE          = "https://chat.truffle.vip/browser-source/your-org/scene-x"     <-----------
    SPOKEN_FILE   = "spoken_messages.json"`
    LINK_PATTERN  = re.compile(r"https?://\S+|www\.\S+")

Change it to your own Truffle chat URL, my URL for example:

    SITE = "https://chat.truffle.vip/browser-source/the-fridge/scene-1"

## Create filter.json
The reason why i can't add this, is because there are words in there that i can't openly share on github, but i have made some instructions here to create your own!

Create a file in the root of the project called "filter.json" with the following format:

    {
    "banned_words": ["Example1", "Example2", "Example3"]
    }

This will filter out inappropriate messages from being spoken.

P.S. It can trigger false positives in my case i had 95% accuracy!

## Changing key binds/perfixes
These are your controls for the TTS while it is running.

If you want to change them here is a guide:

Edit TTS.py and look for this section

    # ─── HOTKEYS ──────────────────────────────────────
    PREFIX        = "!tts" 
    HOTKEY_SKIP   = ";"
    HOTKEY_TOGGLE_PREFIX = "ctrl+alt+p"
    HOTKEY_TOGGLE_TTS = "ctrl+alt+t"

Here you can change:
* The prefix that a message must start with to trigger TTS.
* The hotkey for skipping the current message.
* The hotkey for toggling whether the prefix is required.
* The hotkey to pause or resume TTS.

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
    SITE          = "https://chat.truffle.vip/browser-source/the-fridge/scene-1"     
    SPOKEN_FILE   = "spoken_messages.json"
    LINK_PATTERN  = re.compile(r"https?://\S+|www\.\S+")

And change it to you prefferd voice model you want to use, for example:

    PIPER_MODEL = "./models/donwloaded_model-medium.onnx"

The config file should be automatically be loaded aswel

## Run the Program

After everything is configured you can run the program in your terminal like this:

    # MAKE SURE YOU'RE IN: path-to-folder/TTS-Truffle:
    Python.exe -m TTS
    or
    Python3 -m TTS

Once running it will connect to the specified chat URL.

New messages will be read aloud using your selected TTS voice.

You might see messages like this in your terminal:

    [ERROR:device_event_log_impl.cc:198] USB: SetupDiGetDeviceProperty failed
    [ERROR:registration_request.cc:291] Registration response error message: PHONE_REGISTRATION_ERROR

These are Chrome-related debug messages and can be safely ignored.

To close the program you need to select the terminal and press ctrl+c or close the terminal window.

🙌 Credits

truffle.vip
Piper TTS
Vibe Coded by @Trollmeneerr