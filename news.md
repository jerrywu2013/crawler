# crawler
```
import requests
import re
from bs4 import BeautifulSoup

from requests.packages.urllib3.exceptions import InsecureRequestWarning
requests.packages.urllib3.disable_warnings(InsecureRequestWarning)

def getNews():
    url = 'https://news.google.com/?sdm=FADEOUT&authuser=0&q=裕隆'
    req = requests.get(url, verify=False)
    soup = BeautifulSoup(req.text,'html.parser')

    for link in soup.find_all('a', {'class':'article'}): 
        href = 'https://news.google.com/'+ link.get('href')  
        title = link.string
        print(href)
        print(title)

getNews()
```
