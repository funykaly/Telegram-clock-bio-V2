

# Telegram-clock-bio-V2
> This script is designed to update your Telegram profile status every minute and display the time along with the user's chosen timezone in the profile status.

## Setup Guide

**Step 1: Obtain API ID and Hash**

1. First, go to the website [telegram.org](https://my.telegram.org/auth) and log in with your Telegram account credentials.

2. Create a new application to obtain the API ID (`api_id`), API hash (`api_hash`), and application title (`app_title`).
![API](https://github.com/funykaly/Telegram-clock-bio-V2/blob/main/images/API.png)
> If you encounter any issues during the application creation, make sure to disable your VPN or ad blocker or use a VPN with an IP that hasn't been used to create an application before.

**Step 2: Register on Replit**

1. Go to the website [replit](https://replit.com/) and sign up for an account.

2. Create a new Repl and use the "Import from GitHub" option to upload the project files by providing the GitHub link to the project.

>In step 2-1, your repl must be private, and to enable the private option, you need to purchase it. Therefore, it is recommended to use step 2-2, which is completely free.

Step 2-1:

3. Enter the API ID (`api_id`) in line 10, API hash (`api_hash`) in line 11, and application title (`app_title`) in line 22 of the code. Also, specify your country's time zone in line 19 and feel free to modify the bio text in line 27.

or

Step 2-2(recommended):

3. On the Replit website, go to the "Secrets" section and click on "New Secret." Enter "api_id" in the "Key" field and enter your Telegram API ID in the "Value" field. Do the same for "api_hash," and enter your Telegram API hash in the corresponding "Value" field.

4. Add `import os` to the beginning of the code. Now, instead of `api_id = <api_id>`, replace it with `api_id = os.environ['api_id']`, and do the same for `api_hash = "<api_hash>"`.The code will look like this:
```python
import os
import pytz
import asyncio
from datetime import datetime
from telethon import TelegramClient
from telethon.tl.functions.account import UpdateProfileRequest


api_id = os.environ['api_id']
api_hash = os.environ['api_hash']
```
>In method 2-2, you can still customize the time zone, bio text, and app title according to your preferences.

**Step 3: Install Packages and Configure the Package**

1. After providing the required details, run the code once to install the necessary packages automatically.

2. Except for the "Packages" section in Replit, manually install the `Telethon-repl` package. Wait for the previous packages to be installed automatically before installing this package.

>purchase and enable the "Always On" option for your repl or continue with steps 4 and 5:

**Step 4: Keep the Code Running 24/7**

1. In the `main.py` file, add the line `from keep_alive import keep_alive` at the beginning of the code.

2. Add the `keep_alive()` function call above `api_id = <api_id>` line. The code will look like this:
```python
import os
import pytz
import asyncio
from datetime import datetime
from keep_alive import keep_alive
from telethon import TelegramClient
from telethon.tl.functions.account import UpdateProfileRequest

keep_alive()

api_id = os.environ['api_id']
api_hash = os.environ['api_hash']

# Rest of the code...
```

3. Run the code again, and copy the domain shown in the image below for the next step.
![API](https://github.com/funykaly/Telegram-clock-bio-V2/blob/main/images/domain.webp)

**Step 5: Connect to the Domain and Display the Clock in Bio**

1. Sign up on the website [UptimeRobot](https://uptimerobot.com/).

2. Create a new monitor and set the monitor type to "HTTP." Enter a custom name for the monitor.

3. In the URL field, enter the copied domain.(Please make sure to include `https://` before the domain, otherwise the monitor will not be created.)

4. Leave the other settings as they are and create the monitor.

5. Now, you can display the clock in your Telegram bio, and the bio will update every minute.


## License

This project is licensed under the [BSD-3-Clause License](LICENSE). For more information about the license, please see the [LICENSE](https://github.com/funykaly/Telegram-clock-bio-V2/blob/main/LICENSE) file.

### Note

- Ensure that your Telegram API authentication details are correctly set up in the `main.py` file and never share them with others.
- This script can run in the background, and due to frequent updates, your Telegram profile might be hidden for an extended period. You can modify the value of `await asyncio.sleep(60)` in the `update_profile` function to change this behavior.


### Warning

Continuous and unauthorized use of this script might violate Telegram API terms of service and lead to issues with your account. Please use this script with caution and in compliance with the regulations. The script author bears no responsibility for improper use of this script.


