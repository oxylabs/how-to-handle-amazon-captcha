# How to Bypass Amazon CAPTCHA When Scraping

[![Oxylabs promo code](https://raw.githubusercontent.com/oxylabs/amazon-scraper/refs/heads/main/Scrape%20Amazon%20data%20with%20Web%20Scraper%20API.png)](https://oxylabs.io/products/scraper-api/ecommerce/amazon?utm_source=877&utm_medium=affiliate&groupid=877&utm_content=how-to-bypass-amazon-captcha-github&transaction_id=102f49063ab94276ae8f116d224b67)

[![](https://dcbadge.limes.pink/api/server/Pds3gBmKMH?style=for-the-badge&theme=discord)](https://discord.gg/Pds3gBmKMH) [![YouTube](https://img.shields.io/badge/YouTube-Oxylabs-red?style=for-the-badge&logo=youtube&logoColor=white)](https://www.youtube.com/@oxylabs)

Take a look at the process of bypassing CAPTCHAs when collecting public data from Amazon with [Amazon Scraper API](https://oxylabs.io/products/scraper-api/ecommerce/amazon) (**one-week free trial**). You can find the full guide on our [blog](https://oxylabs.io/blog/bypass-amazon-captcha).

## Setting up a simple scraper

This scraper will likely encounter a CAPTCHA.

```python
import requests

custom_headers = {
    "Accept-language": "en-GB,en;q=0.9",
    "Accept-Encoding": "gzip, deflate, br",
    "Cache-Control": "max-age=0",
    "Connection": "keep-alive",
    "User-agent": "Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/17.1 Safari/605.1.15",
}

url = "https://www.amazon.com/SAMSUNG-Border-Less-Compatible-Adjustable-LS24AG302NNXZA/dp/B096N2MV3H?ref_=Oct_DLandingS_D_fe3953dd_2"

response = requests.get(url, headers=custom_headers)

with open('with_captcha.html', 'w') as file:
    file.write(response.text)
```

## Using Amazon Scraper API

The API is designed to avoid CAPTCHAs.

```python
import requests
from pprint import pprint


payload = {
    'source': 'amazon',
    'url': 'https://www.amazon.com/dp/B096N2MV3H',
    'parse': True
}

response = requests.request(
    'POST',
    'https://realtime.oxylabs.io/v1/queries',
    auth=('username', 'password'),
    json=payload,
)


pprint(response.json())

with open('without_captcha.json', 'w') as file:
    file.write(response.text)
```

## Final word

Follow our technical [documentation](https://developers.oxylabs.io/scraper-apis/e-commerce-scraper-api/amazon) for all available API parameters.

In case of any issues, please contact us at support@oxylabs.io

Looking to scrape more other Amazon data? [Amazon Review Scraper](https://github.com/oxylabs/amazon-review-scraper), [Amazon ASIN Scraper](https://github.com/oxylabs/amazon-asin-scraper), [How to Scrape Amazon Prices](https://github.com/oxylabs/how-to-scrape-amazon-prices), [Scraping Amazon Product Data](https://github.com/oxylabs/how-to-scrape-amazon-product-data)
