**Exclusivity Checker Tool**

**Overview**

This tool helps publishers monitor and detect potential exclusivity breaches on their websites. It analyzes landing pages with high Taboola traffic to identify if competing content recommendation platforms are also present, which could violate exclusivity agreements.

**Features**

Identifies top 10 landing pages with highest Taboola traffic in the last 7 days
Scans page source code for presence of competing content recommendation platforms
Detects multiple ad networks including Outbrain, MGID, Revcontent, and Nativo
Captures full-page screenshots as evidence when exclusivity breaches are detected
Provides API endpoint for integration with other systems

**Requirements**

Python 3.6+
Flask
Vertica Python
Beautiful Soup
Selenium
Chrome WebDriver
Flask-CORS
Requests

**Installation**

# Clone the repository
git clone https://github.com/yourusername/exclusivity-checker.git
cd exclusivity-checker

# Create and activate virtual environment (optional but recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install flask flask-cors vertica_python requests beautifulsoup4 selenium

**Configuration**
Before running the tool, you need to configure the Vertica database connection details in **server.py**:

host = 'your_vertica_host'
port = 5433
database = 'your_database_name'
username = 'your_username'
password = 'your_password'

Make sure Chrome WebDriver is installed and available in your system PATH.
**Usage**

**Running the Server**

{
  "input_data": "12345"
}

The response will include analysis of top landing pages and exclusivity status:

{
  "extractedData": [
    {
      "URL": "https://example.com/article1",
      "exclusivity_breach": "Yes"
    },
    {
      "URL": "https://example.com/article2",
      "exclusivity_breach": "No"
    }
  ]
}

**Project Structure**

server.py: Main application file containing the Flask app and all functionality
screenshots/: Directory where breach evidence screenshots are stored

**How It Works**

1. The tool queries a Vertica database to find the top 10 landing pages with the highest Taboola traffic for a specified publisher
For each URL, it:

2.Retrieves the page source code
  a. Searches for Taboola markers and competing ad platforms
  b. Identifies potential exclusivity breaches
  c. Captures full-page screenshots as evidence when breaches are found

3. Returns results via API endpoint

**License**

MIT License
