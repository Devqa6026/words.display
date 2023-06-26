# words.display
How to display words display in chrome interface using python

from selenium import webdriver
from selenium.webdriver.chrome.options import Options

# Configure Chrome options
chrome_options = Options()
chrome_options.add_argument("--headless")  # Run Chrome in headless mode (without GUI)

# Set path to your chromedriver executable
chromedriver_path = "/path/to/chromedriver"

# Initialize Chrome webdriver
driver = webdriver.Chrome(executable_path=chromedriver_path, options=chrome_options)

# Open a new tab
driver.execute_script("window.open('about:blank', '_blank');")

# Switch to the newly opened tab
driver.switch_to.window(driver.window_handles[1])

# Navigate to a webpage (e.g., Google)
driver.get("https://www.google.com")

# Find the search box element and input a word
search_box = driver.find_element_by_name("q")
search_box.send_keys("Hello World")

# Submit the search query
search_box.submit()

# Wait for a few seconds to see the result (optional)
driver.implicitly_wait(5)

# Close the browser window
driver.quit()
