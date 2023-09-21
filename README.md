# Telerecon
Telerecon is a comprehensive reconnaissance framework for researching and investigating Telegram for OSINT purposes.

![image](https://github.com/sockysec/Telerecon/assets/121141737/096861e9-5f4d-42cb-8360-9a59676460ce)


# Installation 

1. Download all files and save them to the directory of choice.

2. Ensure your system is up to date (recommended)
```
sudo apt update
sudo apt upgrade
```
3. Navigate to the primary Telerecon directory and install the requirements.
```
pip install -r requirements.txt
```
4. Download and install spaCy NER language model (optional, but required for NER parsing feature) 
```
 python3 -m spacy download en_core_web_sm 
```
5. Obtain your Telegram API details from my.telegram.org noting your API key, hash, and phone number.
6. In terminal, navigate to the installation directory (eg, Telerecon-main) and run setup.py
```
python3 setup.py
```
7. As prompted by the script, input your Telegram API key, hash, and phone number (these details will be saved locally).
8. Telegram may message you a verification code, to confirm setup. If so input the verification code.
9. If prompted to "Please enter your phone (or bot token):" then you may need to re-input your account phone number. Telegram will then message you the code (in Telegram) to verify your login "Please enter the code you received:".

10. Telerecon is now installed, run launcher.py to use.


# Use

1. Run launcher.py
```
python3 launcher.py
```
2. Select an option from the menu

# Options

1. **Get user information:**  Search a @username and return any public user information (username, first name, last name, phone number, UserID, Bio, Online status, profile picture).

2. **Check user activity across a list of channels:**  Iterate through a txt/csv directory list of Telegram channels, looking for any messages by the target username. (Assumes directory list is in the primary Telerecon directory).

3. **Collect user messages from a target channel:**  Collect and compile any messages from the target username in a target channel. Option to also download media. 

4. **Collect user messages from a list of target channels:**  iterate through a txt/csv directory list of Telegram channels, collecting and compiling any messages by the target username. Option to also download media. (Assumes directory list is in the primary Telerecon directory).

5. **Scrape all messages within a channel:**  Collect and compile messages in a target channel. Download full history, last 24 hours, or custom date range.

6. **Scrape all t.me URLs from within a channel:**  parses a channel and extracts all t.me URLs mentioned within. This is designed to easily create a Telegram directory.

7. **Scrape forwarding relationships into target channel:**  Scrape forwarding relationships into a target channel. Exporting a Gephi optimised adjacency list, and URL directory of the discovered channels.

8. **Scrape forwarding relationships into a list of target channels:** Iterate through a txt/csv directory list of Telegram channels, scraping forwarding relationships. Exporting a Gephi optimised adjacency list, and URL directory of the discovered channels. Afterwards can use terminal commands to merge outputs. (i.e. merge URLs lists = cat *.csv | sort | uniq > combined.csv)

9. **Identify possible user associates via interaction network map:** Assumes user messages have already been collected. Constructs a network visualisation showing replies/interactions with other users (useful for identifying possible associates).  

![image](https://github.com/sockysec/Telerecon/assets/121141737/12e1aef9-b6a1-4bfb-969f-39e892a73099)

10. **Parse user messages to extract selectors/intel:** Outputting a report containing any potential phone numbers, emails, or other selectors based on regex and key phrase targeting (the report includes citations for ease of verification). Key phrases are customizable by editing the script.

![image](https://github.com/sockysec/Telerecon/assets/121141737/55877564-3b30-47d5-abc6-ad9e3837abd9)

11. **Extract GPS data from collected user media:** Assumes user messages have already been collected. Creates a compiled spreadsheet of extracted EXIF metadata from all images, and a map visualization displaying any extracted GPS metadata.

![image](https://github.com/sockysec/Telerecon/assets/121141737/ff2bbf31-24a6-4c8d-be57-a0e6c1585d48)


12. **Create visulisation report from collected user messages:** Assumes user messages have already been collected. Creates a comprehensive analytics report showing user postage patterns over time (useful for pattern of life analysis etc).

![image](https://github.com/sockysec/Telerecon/assets/121141737/689f4105-0aad-4be8-9eaa-884885f3f3ca)

13. **Extract named entities from collected user messages:** Assumes user messages have already been collected. Creates a report containing extracted Person, Organisation, Location, and date entities extracted by named entity recognition. While not perfect, this function can be useful in identifying key entities for further investigation within big datasets.

![image](https://github.com/sockysec/Telerecon/assets/121141737/464650ce-5e4b-4ddd-b37c-28117708121c)

14. **Conduct a subscriber census across a list of target channels:** Iterate through a txt/csv directory list of Telegram channels, reporting the number of subscribers/members.


# Example Targeting Workflow

**Directory creation** - Telerecon allows you to search across multiple channels and groups for a target user's activity/posts. However, this requires the creation of a directory of target Telegram channels to search across (Ex. This may be all chats in a geographic area or a target ideological grouping.). If you know the URLs of specific channels, you can manually create your own directory by simply making a csv/txt file with the list of target Telegram URL's on each line. Option '6' can allow you to scrape URLs from pre-existing Telegram directories (i.e. nzdirectory) to quickly build a list. Option '7' utilizes exploratory forward mapping to discover related channels/chat groups and produce a list. Option '8' can be used for a more comprehensive list.

Targeting
1. Run launcher.py
2. Select '1' and input a target username (i.e. @Johnsmith), return to the launcher
3. Select '2', input target username (i.e. @Johnsmith), input target channel list (i.e. targetchats.txt)
4. When asked whether you would like to scrape posts, select 'y'. Alternatively, select '4'. Input target username (i.e. @Johnsmith) and channel list (i.e. targetchats.txt). Choose whether or not to include media (media will take longer). After running, return to the launcher.
5. Select '9', input target username (i.e. @Johnsmith). After running, return to the launcher.
6. Select '10', input target username (i.e. @Johnsmith). After running, to the launcher.
7. Select '11', input target username (i.e. @Johnsmith). After running, to the launcher.
8. Select '12', input target username (i.e. @Johnsmith) and define a timezone. After running, return to the launcher.
7. Select '13', input target username (i.e. @Johnsmith). After running, return to the launcher.
   

# Usage Notes

- Running the advanced reports and analytics (9, 10, 11, 12, 13) assume that you have already collected the target user's posts.
- You can speed up collection by decreasing the "REQUEST_DELAY =" however this may result in temporary API rate limiting.
- Choosing to download media will significantly slow down collection. 


# Known Issues
- Return to launcher and rerunning the same script option, can cause a crash. Simply reboot the launcher if this occurs and it will work.


# Credit

Credit to Jordan Wildon's (@jordanwildon) Telegram Scraper for the initial inspiration. https://github.com/TechRahul20/TelegramScraper



# MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
