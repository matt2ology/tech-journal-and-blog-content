---
authors:
  - Matt2ology
categories:
  - blog
  - python
  - START
date: 2025-01-30T09:27:34-08:00
draft: false
notes: blog
related-notes:
tags:
  - selenium
title: Testing Frontend Forms with Selenium and Python
---

## My first experience testing a web app from the user end

<!-- [Propose edits or changes on GitHub](link to GitHub repo of file) -->

### Situation

Our team has requested the development team’s assistance in creating an internal web
form application. This app will enable IT managers and group leads to propose projects that
introduce new services or significantly enhance existing systems in response to business
challenges.

### Task

The task is to systematically complete the web form, verify that the submitted proposal
request is properly recorded in the application, confirm that a notification email arrives in
our unit’s group folder, and conduct other user acceptance tests.

### Action

To ensure the functionality of the web form application, I developed an automated test
script in Python using the `unittest` library and Selenium. This script systematically fills out
and submits the form, verifying that all required fields function correctly and that the
submitted proposal request appears accurately in the system.

I documented the test results, identified any issues, and reported my
findings to the development team for further improvements.

### Result

The automated test script successfully executed the form submission process, verifying that
required fields were properly validated and that submitted proposals appeared correctly in
the system. The script also confirmed that notification emails were consistently delivered to
the unit’s designated folder. During user acceptance testing, minor issues were identified,
including occasional delays in form submission and inconsistencies in error handling. These
findings were documented and shared with the development team, leading to further
refinements and improvements in the application’s functionality.

### Takeaway (what I Learned)

## Related blogs


-
