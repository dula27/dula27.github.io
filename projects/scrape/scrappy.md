---
layout: post
title: /web-crawler
permalink: /projects/scrape/
categories: projects
---
# Project Title: Scrappy/Selenium Web Crawler Script
# Project Description
The project is a Python script that scrapes data from the INTERPOL Red Notices website using the Selenium library. The script extracts data from the website and stores it in a JSON file for later use.

The script first uses ChromeDriver to load the INTERPOL Red Notices website and waits for it to load before scraping data. It then identifies all links on the page with the class "redNoticeItem__labelLink" and adds them to a list of URLs.

The script then iterates through the URLs in the list, loads each page using ChromeDriver, and waits for it to load. Once the page has loaded, the script extracts information about the individual associated with the red notice.

The information extracted includes the person's name, date of birth, place of birth, nationality, and gender. The script stores this information as a dictionary for each individual, with keys representing the different data fields and values representing the actual data.

Once the script has finished iterating through all the URLs and extracting data for each individual, it formats the collected data into a JSON object. The JSON object includes information about the source of the data (INTERPOL Red Notices website), the source URL, and the data itself.

The final JSON file is written to disk, where it can be used for various purposes such as analysis or visualization.

Overall, this project demonstrates how Python can be used to scrape data from websites and store it in a structured format for later use. It also highlights the use of the Selenium library for web scraping, and the JSON file format for storing and sharing structured data.

# JSON File Output After Scraping
`+-------------------------------------------------------------------------------------+`
```json
{
    "source_code": "INTERPOL_RN",
    "source_name": "INTERPOL Red Notices",
    "source_url": "https://www.interpol.int/How-we-work/Notices/View-Red-Notices",
    "persons": [
    
        {
            "firstname": "AMINAT",
            "lastname": "KHABICHEVA",
            "about": {
                "date_of_birth": "16/02/1981",
                "place_of_birth": "ZIMNIAYA STAVKA NEFTEKUMSKIY AREA STAVROPOL REGION , Russia",
                "nationality": "Russia",
                "gender": "Female"
            },
            "other": {}
        },

        {
            "firstname": "SHAMARI",
            "lastname": "OCCONOR",
            "about": {
                "date_of_birth": "01/06/1994",
                "place_of_birth": "EWARTON, ST CATHERINE , Jamaica",
                "nationality": "Jamaica",
                "gender": "Male"
            },
            "other": {}
        }
    ]
}
```
`+-------------------------------------------------------------------------------------+`
# About Python Scraping Scripts
Web scraping is one of my favorite things to do with Python! It's fascinating to see how you can extract valuable information from websites and use it for various purposes. I find it empowering to be able to automate the process of collecting and organizing data that would otherwise take hours or even days to gather manually. Plus, the possibilities are endless with web scraping – from creating custom datasets to automating tedious tasks, the sky's the limit!

# Technologies Used
- Python
- Selenium Library
- JSON
- HTML

# Features
- Scrapes information from INTERPOL's website on wanted persons
- Uses Selenium WebDriver for web automation and scraping
- Extracts personal information, such as name, date of birth, place of birth, nationality, and gender, from individual wanted person pages
- Outputs the extracted data in a structured JSON format
- Can easily be adapted to scrape other websites with similar structures
