---
authors:
  - Matt2ology
categories:
  - blog
  - python
  - START
  - automated-testing
date: 2025-01-30T09:27:34-08:00
draft: false
notes: blog
related-notes:
  - "[[python-decorators-classmethod-staticmethod]]"
tags:
  - selenium
  - unittest
title: Testing Frontend Forms with Selenium and Python
---

## My first experience testing a web app from the user end

<!-- [Propose edits or changes on GitHub](link to GitHub repo of file) -->

### Situation

Our team has requested the development team’s assistance in creating an
internal web form application. This app will enable IT managers and group leads
to propose projects that introduce new services or significantly enhance
existing systems in response to business challenges.

### Task

The task is to systematically complete the web form, verify that the submitted
proposal request is properly recorded in the application, confirm that a
notification email arrives in our unit’s group folder, and conduct other
user acceptance tests.

### Action

To ensure the functionality of the web form application, I developed an
automated test script in Python using the [`unittest` library](https://realpython.com/python-unittest/) and [Selenium](https://selenium-python.readthedocs.io/getting-started.html).
This script systematically fills out and submits the form, verifying that all
required fields function correctly and that the submitted proposal request
appears accurately in the system.

I documented the test results, identified any issues, and reported my findings
to the development team for further improvements.

### Result

The automated test script successfully executed the form submission process,
verifying that required fields were properly validated and that submitted
proposals appeared correctly in the system.

During user acceptance testing, minor issues were identified, including
occasional delays in form submission and inconsistencies in error handling.
These findings were documented and shared with the development team, leading to
further refinements and improvements in the application’s functionality.

### Takeaway (what I Learned)

Through this process, I learned the importance of both automated and manual
testing in ensuring the functionality of new applications.

Automating the form submission with Python and Selenium made it possible to
efficiently validate the core features of the application, saving time and
improving accuracy.

However, it was also clear that some issues, like delays and error handling
inconsistencies, only became apparent during user acceptance testing.
This emphasized the value of comprehensive testing, which combines automation
for efficiency with real-user scenarios for a more thorough evaluation.

Additionally, communicating issues clearly to the development team is essential
for driving continuous improvement.

## Code example

### base_test.py

```python
# BaseTest class (shared setup and teardown logic)

from datetime import datetime
from selenium import webdriver
from selenium.webdriver.chrome.options import Options
from selenium.webdriver.common.by import By
import csv
import logging
import os
import unittest


class BaseTest(unittest.TestCase):
    # Generate the log file name with a timestamp
    log_file = f"{datetime.now().strftime('%Y%m%dT%H%M')}_test_results.csv"

    @classmethod
    def setUpClass(cls):
        cls.logger = logging.getLogger(
            cls.__class__.__name__)  # Logger per test class
        cls.logger.setLevel(logging.INFO)
        cls._initialize_csv_log()
        cls.driver = webdriver.Chrome()
        cls.driver.get("https://dev.app.com")
        cls._login(cls.driver)
        cls._verify_login(cls.driver)

    @staticmethod
    def _login(driver):
        username_field = driver.find_element(By.ID, "loginUsername")
        login_button = driver.find_element(By.TAG_NAME, "button")
        username_field.send_keys("my_username")
        login_button.click()

    @staticmethod
    def _verify_login(driver):
        dashboard_element = driver.find_element(By.ID, "dashboard")
        assert dashboard_element.is_displayed(), "Dashboard not visible: Login failed."

    @classmethod
    def tearDownClass(cls):
        cls.driver.quit()

    @classmethod
    def _initialize_csv_log(cls):
        """Initializes the CSV log file with a timestamped name."""
        if not os.path.exists(cls.log_file):
            with open(cls.log_file, mode="w", newline="") as file:
                writer = csv.writer(file)
                writer.writerow(["Test Name", "Status", "Message"])

    @classmethod
    def _log_to_csv(cls, test_name, status, message: str = ""):
        status: str = "Success" if status == "True" else "Failed"
        """Logs test results to the CSV file."""
        cls.logger.info(f"{test_name} - {status}: {message}")
        with open(cls.log_file, mode="a", newline="") as file:
            writer = csv.writer(file)
            writer.writerow([test_name, status, message])
```

### base_form_request_test.py

```Python
from base_test import BaseTest


class BaseBtpRequest(BaseTest):
    @classmethod
    def setUpClass(cls):
        super(BaseBtpRequest, cls).setUpClass()  # Correct way to call super in a class method
        cls.driver.get(
            "https://dev.app.com/submission/edit")
```

### test_form_request.py

```Python
from base_btp_request_test import BaseBtpRequest
from selenium.webdriver.common.by import By


class TestBtpRequest(BaseBtpRequest):
    def test_btp_request_objectives_textarea_is_editable(self):
        test_name: str = "Test form request objectives other textarea"
        try:
            # locate checkbox
            self.driver.find_element(
                By.ID,
                "needs_type_OTHR"
            ).click()

            self.driver.implicitly_wait(1)

            # Locate the textarea element
            textarea = self.driver.find_element(By.ID, "other_bus_needs")
            test_text = "Testing Selenium Input"
            textarea.send_keys(test_text)  # Send keys to the textarea

            # Verify if the text was entered correctly
            test_result = textarea.get_attribute("value") == test_text
            self.assertTrue(test_result, "Textarea is not editable!")
            self._log_to_csv(test_name, test_result)

        except Exception as e:
            self._log_to_csv(test_name, test_result, e)
            raise
```

## Related blogs

- [Python Decorators `classmethod` and `staticmethod`]({{< ref "python-decorators-classmethod-staticmethod.md" >}})
