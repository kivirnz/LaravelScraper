# LaravelScraper
Scrapes Laravel error pages via Shodan, downloads and parses the results, then displays all credentials reported in the error page and (optionally) reports them to a Telegram bot


## Description
LaravelScraper is a small script to scrape Laravel error pages using the Shodan API and extract valuable information\
It is incredibly useful for gaining access to random databases and credentials for different services

Features:
- **Uses the Shodan API and allows you to search through pages of results**
- **Resolves IP addresses to hostnames**
- **Allows you to save all of your results to a file**

## Requirements
Python 3 (duh)\
argparse\
datetime\
os\
requests\
re\
pyfiglet\
urllib3\
sys\
socket\
bs4\
contextlib\

**You can install all of the dependencies by cloning the repository and running: ```pip install -r requirements.txt```

## Usage
Run normally: ```python laravelscraper.py -k YOUR_SHODAN_API_KEY_HERE```\
Add results to SQLite database: ```python laravelscraper.py -k YOUR_SHODAN_API_KEY_HERE -d database.sql```\
Send results to telegram: ```python laravelscraper.py -k YOUR_SHODAN_API_KEY_HERE -t YOUR_BOT_TOKEN YOUR_CHAT_ID -d database.sql```\

Output the results to a file called output.txt: ```python laravelscraper.py -k YOUR_SHODAN_API_KEY_HERE -o output.txt```\

Scroll through pages of Shodan results to page 13: ```python laravelscraper.py -k YOUR_SHODAN_API_KEY_HERE -p 13```\

## Arguments
- ```-k``` or ```--api_key``` | This is required. This is where you put your Shodan API key.
- ```-p``` or ```--page``` | Shodan only prints 100 results by default per page, so if you want more results, change this parameter to go to a different page.
- ```-o``` or ```--output``` | Outputs whatever results to stdout AS WELL AS to a file of your choice.
- ```-d``` or ```--database``` | Saves the hits to a local SQLite database
- ```-t``` or ```--telegram``` | Sends the hits to your Telegram bot. Please follow -t with your Telegram bot token and your chat ID (seperated by a space)

## To Do
- [x] Add feature to save all results to a local SQLite database or a CSV file
- [x] Add Telegram feature
- [ ] Allow --all argument to download all results from Shodan (i tried implementing this but it gave me a headache)
- [ ] Intergrate with other services (Hunter, CriminalIP, ZoomEye etc)
- [ ] Implement automatic testing of DBs, SMTP logins, AWS keys to test if they work
- [ ] Add -e argument to allow for extra queries to the dork

## Disclaimer
This is to be used for educational purposes only blah blah (insert boilerplate shite here)

## License
This code was proudly written and published under the <a href=https://plusnigger.org>+NIGGER license</a>, a modified version of Daddy Stallmans <a href="https://www.gnu.org/licenses/gpl-3.0.txt">GPL v3 license</a>
