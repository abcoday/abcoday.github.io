---
layout: post
title: "python 抓取"
date: 2016-07-11 11:01:51 +0800
description: "python 抓取学习记录"
category: 
tags: []
---

## 虚拟环境创建
> `virtualenv`

- [文档 http://virtualenv-chinese-docs.readthedocs.io/en/latest/](http://virtualenv-chinese-docs.readthedocs.io/en/latest/)

- `pip install virtualenv` 安装工具

- `virtualenv scrapingEnv` 创建虚拟环境

> `conda`
    
- 安装 <https://www.continuum.io/downloads#_windows>

- 包查询 <https://anaconda.org/>

- pip包查询 <https://pypi.python.org/pypi>

- `conda create -n xxx bbb`  xxx 虚拟环境名称  bbb 安装的模块

> 启用和关闭虚拟环境

- `activate xxx ` 开启   `deactivate` 关闭

## Installing BeautifulSoup

[文档 https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/](https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/)

` pip3 install beautifulsoup4 or python3 setup.py install`

> 例子-1

    from urllib.request import urlopen
    from bs4 import BeautifulSoup
    html = urlopen("http://www.pythonscraping.com/pages/page1.html")
    bsObj = BeautifulSoup(html.read())
    print(bsObj.h1)

> 例子-2

    from urllib.request import urlopen
    from io import StringIO
    import csv
    data = urlopen("http://pythonscraping.com/files/MontyPythonAlbums.csv")
                .read().decode('ascii', 'ignore')
    dataFile = StringIO(data)
    csvReader = csv.reader(dataFile)
    for row in csvReader:
        print(row)

## Scrapy <http://doc.scrapy.org/en/latest/intro/tutorial.html>

> 例子-1

    import scrapy

    class DmozSpider(scrapy.Spider):
        name = "dmoz"
        allowed_domains = ["dmoz.org"]
        start_urls = [
            "http://www.dmoz.org/Computers/Programming/Languages/Python/Books/",
            "http://www.dmoz.org/Computers/Programming/Languages/Python/Resources/"
        ]

        def parse(self, response):
            filename = response.url.split("/")[-2] + '.html'
            with open(filename, 'wb') as f:
                f.write(response.body)


## 自然语言 NLTK

## Python Requests Library

[文档 http://www.python-requests.org/en/master/](http://www.python-requests.org/en/master/)

> 例子-1

    import requests
    files = {'uploadFile': open('../files/Python-logo.png', 'rb')}
    r = requests.post("http://pythonscraping.com/pages/processing2.php",
    files=files)
    print(r.text)

> 例子-2

    import requests
    session = requests.Session()
    params = {'username': 'username', 'password': 'password'}
    s = session.post("http://pythonscraping.com/pages/cookies/welcome.php", params)
    print("Cookie is set to:")
    print(s.cookies.get_dict())
    print("-----------")
    print("Going to profile page...")
    s = session.get("http://pythonscraping.com/pages/cookies/profile.php")
    print(s.text)

> 例子-3

    import requests
    from requests.auth import AuthBase
    from requests.auth import HTTPBasicAuth
    auth = HTTPBasicAuth('ryan', 'password')
    r = requests.post(url="http://pythonscraping.com/pages/auth/login.php", auth=
    auth)
    print(r.text)

## Scraping JavaScript 抓取javascript生成的内容

> Selenium <http://www.seleniumhq.org/>

- `pip install selenium`

> PhantomJS <http://phantomjs.org/download.html>

- 把安装包（exe） 存放在根目录下

> 例子-1

    from selenium import webdriver
    import time
    driver = webdriver.PhantomJS(executable_path='')
    driver.get("http://pythonscraping.com/pages/javascript/ajaxDemo.html")
    time.sleep(3)
    print(driver.find_element_by_id("content").text)
    driver.close()

> 例子-2

    from selenium.webdriver.common.by import By
    from selenium.webdriver.support.ui import WebDriverWait
    from selenium.webdriver.support import expected_conditions as EC
    driver = webdriver.PhantomJS(executable_path='')
    driver.get("http://pythonscraping.com/pages/javascript/ajaxDemo.html")
    try:
    element = WebDriverWait(driver, 10).until(
    EC.presence_of_element_located((By.ID, "loadedButton")))
    finally:
    print(driver.find_element_by_id("content").text)
    driver.close()

## Image Processing and Text Recognition

> Pillow <http://pillow.readthedocs.io/en/3.3.x/>

> Tesseract

    <https://github.com/tesseract-ocr/tesseract>
    <https://github.com/UB-Mannheim/tesseract/wiki>

> NumPy

## Testing Your Website with Scrapers

> 例子-1

    from urllib.request import urlopen
    from bs4 import BeautifulSoup
    import unittest

    class TestWikipedia(unittest.TestCase):
        bsObj = None
        def setUpClass():
            global bsObj
            url = "http://en.wikipedia.org/wiki/Monty_Python"
            bsObj = BeautifulSoup(urlopen(url))

        def test_titleText(self):
            global bsObj
            pageTitle = bsObj.find("h1").get_text()
            self.assertEqual("Monty Python", pageTitle);

        def test_contentExists(self):
            global bsObj
            content = bsObj.find("div",{"id":"mw-content-text"})
            self.assertIsNotNone(content)
    
    if __name__ == '__main__':
        unittest.main()

> 例子-2

    from selenium.webdriver import ActionChains
    import unittest
    class TestAddition(unittest.TestCase):
        driver = None
        def setUp(self):
            global driver
            driver = webdriver.PhantomJS(executable_path='<Path to Phantom JS>')
            url = 'http://pythonscraping.com/pages/javascript/draggableDemo.html'
            driver.get(url)

        def tearDown(self):
            print("Tearing down the test")

        def test_drag(self):
            global driver
            element = driver.find_element_by_id("draggable")
            target = driver.find_element_by_id("div2")
            actions = ActionChains(driver)
            actions.drag_and_drop(element, target).perform()
            self.assertEqual("You are definitely not a bot!", 
                driver.find_element_by_id("message").text)

    if __name__ == '__main__':
        unittest.main()

## Scraping Remotely

> Tor <https://www.torproject.org/download/download>

> PySocks

- `pip install PySocks`