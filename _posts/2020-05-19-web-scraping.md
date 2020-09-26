---
layout: post
title: Web Scraping in Python
subtitle: How to scrape store locations using Python 3
tags: [python, json]
---

In this post, I will show you how to extract the details of store locations available at different websites. We will look at _**Uniqlo**_ locations in China first.

### Rendering the Data
Open any browser and google Uniqlo store locator. Once you enter the page right-click on any link on the page and choose - Inspect Element. The browser will open a toolbar and show the HTML content of the web page. Click **Clear** on the **Network** panel to clear all requests from the request table. Select **XHR** and then refresh the page. Now you should see a request starting with _**stores?**_ in the panel - click on that. Copy the [request URL](http://d.uniqlo.cn/p/hmall-store-service/i/site/queryAllstoreToJson/zh_CN) and paste it in a new tab (I would suggest using Firefox as it will format JSON nicely). 

Now you should be able to see the data in the raw form. To view the data in JSON format, download the extension JSON formatter. In Firefox, simply switch tab from **Raw Data** to **JSON**.

### Loading Python Pacakges
```python
import csv
import requests
import json
import argparse
import traceback
import numpy as np, pandas as pd
import warnings
warnings.filterwarnings("ignore")
```

### Building the Scraper
Let's first define the scraper function. URL here should be replaced with your ***request URL*** where locations are stored in JSON. Headers information can be found in **Header** tab. Modify that accordingly. In ```data = { }``` select metrics that you'd like to retreive.

```python
def locate_stores():
    url = "http://d.uniqlo.cn/p/hmall-store-service/i/site/queryAllstoreToJson/zh_CN"

    headers = { 'accept':'text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8',
                'accept-encoding':'gzip, deflate, br',
                'accept-language':'en-US,en;q=0.5',
                'upgrade-insecure-requests':'1',
                'user-agent':'Mozilla/5.0 (Windows NT 10.0; WOW64; rv:68.0) Gecko/20100101 Firefox/68.0'
    }
    stores = []
    print("retrieving stores")
    for retry in range(10):          
            stores_data = requests.get(url, headers=headers, verify=False).json().get("resp",[])
            
            if not stores_data:
                print("no stores found")
                data = {
                    "storeName":"",
                    "address":"",
                    "city":"",
                    "state":"",
                    "country":""
                }
                stores.append(data)

            for store in stores_data:
                    storeName: store.get('displayName'),
                    address: store.get('fullAddress'),
                    city: store.get('city'),
                    state: store.get('state'),
                    country: store.get('country')

                data = {
                    "storeName": storeName,
                    "address": address,
                    "city": city,
                    "state": state,
                    "country": country
                }
                stores.append(data)
            return stores
        except:
            print(trackback.format_exc())
    
    return []
```

Next, let's run the function

```python
rlt = locate_stores()
pd.DataFrame(rlt)
```

You shoule get a table that lists all stores with selected metrics if previous code run correctly. You can do some further data cleaning to make sure no **NaN** exists or filter on country to make sure only stores in China are selected. Final data table can be exported into a CSV.

### Tricky Locator

Some website may ask users to first select country/region or enter a zipcode in order to find store locations. In these cases, we will need to modify our function a little bit.

#### Country/Region

Instead of insetring a fixed, unchanged request URL, we will make the url dynamic - setting the countrycode argument to change the URL accordingly depends on what region we're looking for. For example, here is the request URL for _**H&M**_, later we can call function ```locate_stores(countryCode='GB')``` if we need to search for locations in Great Britain specifically.

```python
def locate_stores(countryCode):

    url = "https://hm.storelocator.hm.com/rest/storelocator/stores/1.0/locale/en_US/country/%s?_type=json"%(countryCode)
    ...

rlt = locate_stores(countryCode='GB')
pd.DataFrame(rlt)
```

#### Lat/lon

Now we set two arguments **lat** and **lon** instead. Here's an example for _**Bershka**_ stores in Poland:

```python
def locate_stores(lat,lon):
    url = "https://www.bershka.com/itxrest/2/bam/store/44009506/physical-store?latitude=%s&longitude=%s"%(lat,lon)
    ...

# Poland: lat 49.3 ~ 54.7, long 14.2 ~ 23.9
lat = range(48,55,1)
lon = range(13,25,1)

df = pd.DataFrame([])
for lat0 in (lat):
    for lon0 in (lon):
        data = locate_stores(lat0,lon0)
        df = df.append(data, ignore_index=True)
```

We can define a range of lat/lon for a specific region or country then loop through the function to retrive all nearby stores. Other steps are pretty similar to what we did to _**Uniqlo**_ store locations.

