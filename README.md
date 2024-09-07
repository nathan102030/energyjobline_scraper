Overview
This project provides a Python script that scrapes job listings from the EnergyJobline, Nextera, and Betchel websites using Selenium. The script iterates through job pages, extracts job titles and descriptions, and saves the data into a CSV file. It handles popups and includes retry mechanisms for fetching page elements, making it resilient to temporary loading issues.
Prerequisites
Before running the script, ensure you have the following installed:
Python 3.x
Google Chrome Browser
ChromeDriver (compatible with your Chrome version)
Required Python packages:
selenium
csv
os
time
random
logging
You can install the required packages using the following commands:
bash
Copy code
pip install selenium

Setup
ChromeDriver
Download ChromeDriver from here, ensuring the version matches your installed version of Chrome.
Place the chromedriver binary in the same directory as the script or provide the full path in the script when initializing the WebDriver.
CSV File
The script writes job data to a CSV file named job_data_energyjobline.csv. If the file does not exist or is empty, it will create a new file with the appropriate headers. Ensure that the script has the necessary permissions to write to this file.
Script Usage
Running the Script
You can run the script by executing the following command in your terminal:
bash
Copy code
python job_scraper.py

How It Works
Initialization:
The script initializes a Chrome WebDriver instance and disables notifications and popups.
CSV File Handling:
The script checks if the file job_data_energyjobline.csv exists. If it doesn't exist or is empty, it creates the file and writes the headers.
Scraping Logic:
The script iterates through job listings from the EnergyJobline website by visiting paginated URLs.
For each job, it scrapes the job title and description by opening the job link in a new tab.
The job data is then written to the CSV file.
Popups Handling:
The script tries to close any popup that appears during navigation. This ensures the script isn't interrupted by popups while scraping.
Retry Mechanisms:
The script implements retry mechanisms when accessing page elements or fetching text to handle intermittent issues like stale references or elements not loading.
Logging:
Logging is set to INFO level, which provides helpful output in the terminal about the script's progress, including details about successfully scraped jobs or errors encountered.
Delays:
To avoid overwhelming the server, random delays between 1 to 3 seconds are added between requests.
Customization
Base URL: The base URL for the job search is defined in the variable base_url. You can modify this URL to adjust the job search parameters, such as job titles, location, and radius.
Retries and Timeouts: The number of retries for fetching elements and the sleep durations can be adjusted based on network conditions and page load times.
Error Handling
Popup Handling: The script tries to close popups if they appear. If the popup cannot be closed, the script continues execution without interruption.
Retries: In case of stale element references or other page loading issues, the script retries the action up to three times before moving on to the next job.
Error Logging: All errors are logged to the console, allowing you to track which pages or jobs caused issues.
Output
The script outputs job data in a CSV file with the following columns:
Job Title: The title of the job listing.
Job Description: The description of the job, including qualifications and responsibilities.
Sample Output
csv
Copy code
Job Title,Job Description
Wind Technician,This position involves...
Renewable Energy Engineer,Looking for an experienced engineer...

