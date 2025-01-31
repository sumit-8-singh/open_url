name: Open URL in Chrome (Loop)

on:
  workflow_dispatch:  # Allows manual start

jobs:
  open_url:
    runs-on: ubuntu-latest
    steps:
      - name: Install Chrome & Dependencies
        run: |
          sudo apt update
          sudo apt install -y wget unzip xvfb
          wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
          sudo dpkg -i google-chrome-stable_current_amd64.deb || sudo apt -f install -y
          google-chrome --version

      - name: Install Python & Selenium
        run: |
          pip install selenium webdriver-manager

      - name: Create Python Script
        run: |
          echo 'from selenium import webdriver
          from selenium.webdriver.chrome.service import Service
          from webdriver_manager.chrome import ChromeDriverManager
          import time

          options = webdriver.ChromeOptions()
          options.add_argument("--headless")  # Run without UI
          options.add_argument("--no-sandbox")
          options.add_argument("--disable-dev-shm-usage")

          service = Service(ChromeDriverManager().install())
          driver = webdriver.Chrome(service=service, options=options)

          while True:
              driver.get("https://cdn.qw03.xyz/h/910001002.html?code=31WC3Q&uid=130159769")
              print("Page opened successfully!")
              driver.quit()
              time.sleep(60)  # Wait 1 minute before the next request' > open_url.py

      - name: Run Selenium Script in a Loop
        run: |
          python3 open_url.py
