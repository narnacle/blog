+++
date = '2025-07-17T14:00:00+03:00'
draft = false
title = 'Python Selenium Tutorial - Automate Websites and Create Bots'
tags = ["Automation", "Programming", "Python"]
+++

Automating a web browser with Selenium allows you to control a browser (like Chrome, Firefox, etc.) using Python code. This is useful for tasks like web scraping, testing, or automating repetitive tasks like filling out forms or interacting with web elements.

Here’s a basic guide to get you started:

### 1. **Set up your environment**

To use Selenium with Python, you'll need to install the `selenium` package and a web driver for the browser you want to control.

#### Install Selenium:

```bash
pip install selenium
```

#### Download a WebDriver:

- **Chrome**: You need to download [ChromeDriver](https://sites.google.com/a/chromium.org/chromedriver/downloads).
    
- **Firefox**: You can use [geckodriver](https://github.com/mozilla/geckodriver/releases).
    

Make sure to place the WebDriver in a location that’s part of your system's `PATH` or specify the path directly in your script.

### 2. **Basic Example**

Below is a simple example to open a browser, navigate to a page, and interact with elements:

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.common.keys import Keys

# Set up the WebDriver (assuming using Chrome)
driver = webdriver.Chrome(executable_path='/path/to/chromedriver')  # Adjust the path if necessary

# Open a website
driver.get("https://www.google.com")

# Find the search box and type something
search_box = driver.find_element(By.NAME, "q")
search_box.send_keys("Selenium Python")
search_box.send_keys(Keys.RETURN)  # Simulate hitting Enter

# Wait for the results to load (you can also use WebDriverWait for more precision)
driver.implicitly_wait(5)

# Perform actions on the result (e.g., click a link)
first_result = driver.find_element(By.CSS_SELECTOR, ".LC20lb")
first_result.click()

# Close the browser after some time
driver.quit()
```

### 3. **Important Concepts in Selenium:**

- **WebDriver**: The core component to interact with the browser.
    
- **Locating Elements**: You can find elements on a page using different strategies like `find_element_by_id`, `find_element_by_class_name`, `find_element_by_xpath`, etc. The example above uses `By.NAME` and `By.CSS_SELECTOR`.
    
- **Interactions**: You can simulate actions like `send_keys` (typing), `click()`, `submit()`, etc.
    
- **Waiting**: Selenium can wait for elements to appear using `implicitly_wait()`, or for more fine-tuned control, use `WebDriverWait` and expected conditions.
    

### 4. **Handling Popups and Alerts:**

To handle popups or JavaScript alerts, you can use:

```python
# Accept an alert
alert = driver.switch_to.alert
alert.accept()

# Dismiss an alert
alert.dismiss()
```

### 5. **Advanced Features:**

- **Taking screenshots**:
    

```python
driver.save_screenshot("screenshot.png")
```

- **Executing JavaScript**: You can execute custom JavaScript in the browser:
    

```python
driver.execute_script("alert('Hello, world!')")
```

- **Handling multiple windows**: If your script opens multiple tabs/windows, you can switch between them using `driver.switch_to.window(window_handle)`.
    

### 6. **Headless Mode (Optional)**

If you don't want the browser to open visibly, you can run the browser in "headless" mode. For Chrome, it looks like this:

```python
from selenium.webdriver.chrome.options import Options

options = Options()
options.headless = True  # Run in headless mode

driver = webdriver.Chrome(executable_path='/path/to/chromedriver', options=options)
```

### 7. **Troubleshooting**

- **Element not found**: Check if the page is fully loaded. Use `WebDriverWait` for dynamic content.
    
- **Version mismatch**: Ensure your WebDriver matches your browser version.