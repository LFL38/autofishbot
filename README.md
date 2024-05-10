# AFB - Autofishbot
Auto fishing bot made in Python 3 for [Virtual Fisher](https://virtualfisher.com/) Discord bot.

## Features
- Auto Fish 
- Menu (TUI)
- Captcha Bypass [*](#captcha-information)
- Full-featured (auto boosts, auto daily, auto sell, and +)
- Interactions (buttons and slash commands)

**Note**: the **experimental-2.0.0** (current) version is still under development, if you are having problems, a stable release (**1.2.1.1**) can be found [here](assets/stable-legacy/stable-1.2.1.1.zip).

## Demo
![demo](assets/images/demo.gif)

## Requirements
- Python [3.10.6](https://www.python.org/downloads/release/python-3106/) or [later versions](https://www.python.org/downloads/)
- [Git](https://git-scm.com/downloads) (optional)

## Installation and Update
(**With** Git) 
- Using the terminal, type:
```bash
git clone https://github.com/LFL38/autofishbot.git
cd autofishbot
python -m pip install -r requirements.txt
```
(**Without** Git)
- Download the repository [here](https://github.com/thejoabo/autofishbot/archive/refs/heads/main.zip)
- Extract the zip file
- Open a terminal window in the extracted folder and type:
```bash
python -m pip install -r requirements.txt
``` 
## Usage
Using the terminal, **in the repository folder**, type:
```bash
python autofishbot.py 
```
**Notes**:
- You can use ```python autofishbot.py config_name``` to run the bot with a specific config file.
- You can use ```python autofishbot.py --create``` to create a new config file.
- In the first startup, the bot will ask you to fill the configuration file name (which will be stored at '```{autofishbot directory}/configs/```' folder). After setting everything up, run the command again. In case of several config files, you will be prompted to choose one.

## Customization

You can easily customize the options listed below in the automatically generated [config file](assets/template.config):

```conf
#Example
[SYSTEM]
user_token = M@yToke_n123
user_cooldown = 5
channel_id = 123456
debug = False

[CAPTCHA]
ocr_api_key = MyK!ey12.3

[NETWORK]
user_agent = 
proxy_ip =
proxy_port =
proxy_auth_user = 
proxy_auth_password = 

[AUTOMATION]
boosts_length = 5
more_fish = True
more_treasures = False
fish_on_exit = True
auto_daily = True
auto_buy_baits = False
auto_sell = True
auto_update_inventory = False

[MENU]
compact_mode = False
refresh_rate = 0.3

[COSMETIC]
pet = dolphin
bait = fish
biome = ocean
```
Detailed information [here](assets/faq.md).


## Captcha Information
All captchas are solved using the OCR.SPACE API for image to text recognition. The reason for choosing an online API was to avoid the annoyance of forcing users to install heavy image recognition modules (and saving the unnecessary effort of creating a specific image recognition model for this type of captcha). Among the API options, the most practical and accessible for the user is OCR.SPACE and, furthermore, it presented a reasonable consistency in correctly identifying the text in the image in the tests performed. **Therefore, to automatically solve the captchas, you will need an [API KEY](#how-do-i-get-my-free-key-)**.

The methodology is quite straight forward, when a new captcha is detected:

1. A request is sent asynchronously to the API for each available OCR engine
2. The answers are filtered to assert those with reasonable certainty 
3. The filtered answers are tested

If all tests fail, a request to regenerate the captcha will be sent (up to 3 times). If the bot, ultimately, fails to solve all captchas, it will wait until you solve it manually.

Keep in mind that the captcha detection method is not flawless, unexpected events can cause some unusual behavior that could influence detection accuracy. Therefore, it should not be left alone without monitoring for longer periods of time.
### Demo (normal)
![captcha-demo](assets/images/captcha-demo.gif)

### Demo (with regen)
![captcha-demo-wrong-code](assets/images/captcha-with-regen.gif)

### HOW DO I GET MY **FREE** KEY ?

All you need to do is use [any](https://temp-mail.io/en) email to get it here: https://ocr.space/ocrapi/freekey.
