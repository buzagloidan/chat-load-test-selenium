# Chat Load Test

## Overview
This repository contains a Python script for performing load testing on a chatbot application using Selenium. The script simulates multiple concurrent user sessions that interact with the chatbot, logs browser errors, and saves chatbot responses.

## Features
- **Automated Login**: Logs into the chatbot platform using provided credentials.
- **Simulated Conversations**: Sends predefined test prompts to the chatbot.
- **Error Logging**: Captures and logs browser, UI, and network errors during interactions.
- **Concurrent Sessions**: Runs multiple chatbot sessions concurrently using threads.
- **Response Storage**: Saves chatbot responses to local text files.

## Prerequisites
- Python 3.7+
- Google Chrome browser
- ChromeDriver

### Required Python Libraries
Install the dependencies using the following command:
```bash
pip install selenium webdriver-manager
```

## Directory Structure
```
chat_load_test/
├── chat_load_test.py   # Main script
├── responses/         # Directory for saving chatbot responses
```

## Setup and Usage

### 1. Configure Test Prompts
Modify the `TEST_PROMPTS` list in the script to include your desired chatbot prompts. These will be used during the test sessions.

### 2. Update Login Credentials
Replace the placeholders in the `login()` function:
```python
email_input.send_keys("your_email@example.com")
password_input.send_keys("your_password")
```

### 3. Run the Script
Execute the script using the following command:
```bash
python chat_load_test.py
```

### 4. View Responses
Chatbot responses are saved in the `responses/` directory with filenames indicating the session thread.

### 5. Stop the Script
To stop the script, press `Ctrl+C` in the terminal. You will be prompted to confirm the exit.

## Key Functions

### setup_driver()
Configures the Selenium WebDriver with necessary options.

### login(driver)
Logs into the chatbot platform.

### send_prompt_and_wait(driver, prompt, thread_num)
Sends a test prompt to the chatbot and waits for the response.

### check_for_errors(driver, thread_num)
Checks for browser, UI, and network errors during interactions.

### upload_file(driver)
Uploads a file to the chatbot platform (optional).

### run_chat_session(thread_num)
Runs a single chatbot session in a thread.

### main()
Entry point for the script. Sets up directories, starts threads, and manages the test lifecycle.

## Notes
- Adjust the number of sessions (`num_sessions`) in the `main()` function based on your testing requirements.
- Ensure the correct selectors for elements like login inputs and buttons in the `login()` and `send_prompt_and_wait()` functions.

## Troubleshooting
- **WebDriverException**: Ensure you have the latest version of ChromeDriver that matches your Chrome browser.
- **TimeoutException**: Increase the WebDriver wait times if elements take longer to load.
- **Errors in Threads**: Check the logs printed by each thread for specific issues.

## License
This project is licensed under the MIT License. See the LICENSE file for details.
