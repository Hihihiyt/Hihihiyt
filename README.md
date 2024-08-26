from selenium import webdriver
from selenium.webdriver.common.keys import Keys
import random
import string

# Set up the Selenium WebDriver
driver = webdriver.Chrome()

# Navigate to the email website
driver.get("https://www.emailwebsite.com/signup")

# Generate a random username and password
username = ''.join(random.choices(string.ascii_letters + string.digits, k=10))
password = ''.join(random.choices(string.ascii_letters + string.digits, k=15))

# Find the fields for entering username and password and enter the generated values
username_field = driver.find_element_by_id("username")
username_field.send_keys(username)

password_field = driver.find_element_by_id("password")
password_field.send_keys(password)

# Find the submit button and click it
submit_button = driver.find_element_by_id("signup-button")
submit_button.click()

# Wait for the page to load after creating the account
driver.implicitly_wait(10)

# Close the browser
driver.quit()

print(f"Account created with username: {username} and password: {password}")
