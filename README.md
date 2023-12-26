<h1>Python Dark Web / Hacker Forum Monitoring Script</h1>

 
<h2>Description</h2>
This tool is designed to monitor the dark web for mentions of an organization's name, key personnel, or critical assets. It includes a basic sentiment analysis to gauge potential threats. Please ensure that your use of this tool complies with all applicable laws and ethical guidelines.<br />


<h2>Languages and Utilities Used</h2>

- <b>Python</b> 
- <b>BeautifulSoup</b>

<h2>Environments Used </h2>

- <b>Linux/Windows</b> 

<h2>Program walk-through:</h2>

<p align="center">
Step 1: Import Necessary Libraries <br/>
<img src="https://imgur.com/RgvOFeu.png" height="80%" width="80%" alt="Disk Sanitization Steps"
<br />
<br />
Step 2: Define the Main Function



    def fetch_dark_web_mentions(organization_name, key_personnel, critical_assets):

    
    # Defines a function named fetch_dark_web_mentions that takes three parameters: organization_name, key_personnel, and critical_assets.

Step 3: Set Dark Web URL and Make a GET Request



    dark_web_url = "YOUR_DARK_WEB_URL_HERE"
    headers = {"User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.124 Safari/537.36"}
    response = requests.get(dark_web_url, headers=headers)

    
      #  dark_web_url: Replace "YOUR_DARK_WEB_URL_HERE" with the actual dark web URL to monitor.
        headers: Simulates a user-agent to avoid potential blocking.
        requests.get(): Sends a GET request to the dark web URL and stores the response.

Step 4: Check Response Status



    if response.status_code == 200:

    
       # Checks if the HTTP response status code is 200 (OK), indicating a successful request.

Step 5: Parse HTML Content with BeautifulSoup



        soup = BeautifulSoup(response.text, 'html.parser')

    
       # Creates a BeautifulSoup object, soup, to parse the HTML content of the dark web page.

Step 6: Extract Text Content



        dark_web_text = soup.get_text()

    
       #  Uses get_text() to extract the text content from the HTML, which will be analyzed for mentions and sentiment.

Step 7: Perform Sentiment Analysis



        sentiment_score = len([word for word in dark_web_text.split() if word.lower() in ["threat", "attack", "danger"]])

    
     #  Performs basic sentiment analysis by counting occurrences of predefined threat-related keywords.

Step 8: Check for Potential Threat


        if sentiment_score > 0:
            print("Potential Threat Detected!")

    
      #  If the sentiment score is greater than 0, prints a message indicating a potential threat.

Step 9: Check for Mentions



        if any(keyword.lower() in dark_web_text.lower() for keyword in [organization_name] + key_personnel + critical_assets):

      #  Checks for mentions of the organization's name, key personnel, or critical assets in the dark web content.

Step 10: Print Mentions



            print("Mentions found on the dark web:")
            for keyword in [organization_name] + key_personnel + critical_assets:
                if keyword.lower() in dark_web_text.lower():
                    print(f"- {keyword}")

    
       # Prints a message indicating that mentions were found and lists the specific keywords that were mentioned.

Step 11: Handle Failed Request


    else:
        print(f"Failed to fetch data from the dark web. Status Code: {response.status_code}")

       # If the request to the dark web URL fails, prints an error message along with the HTTP status code.

Step 12: Main Program Execution



    if __name__ == "__main__":
    organization_name = "Acme Corp"
    key_personnel = ["John Doe", "Jane Smith"]
    critical_assets = ["Project X", "Trade Secrets"]
    fetch_dark_web_mentions(organization_name, key_personnel, critical_assets)

    
       # Sets up the main program execution.
        Defines sample information for the organization's name, key personnel, and critical assets.
        Calls the fetch_dark_web_mentions function with the provided information.

This step-by-step tutorial explains each part of the script, from importing libraries to executing the main program. Adjust the dark web URL and organization information as needed for your specific use case.

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
Here's an example of me running the script on a news website talking about breaches in 2023 for ethical reasons.. I put the company as Boeing and had it search for keywords such as "Breach", "Ransom", etc.
<br/>
<img src="https://imgur.com/Ihq1alS.png" height="80%" width="80%" alt="Disk Sanitization Steps"
<br />
<br />

