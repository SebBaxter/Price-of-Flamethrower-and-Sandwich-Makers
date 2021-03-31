# Price-of-Flamethrower-and-Sandwich-Makers
This is from the web scraping module of Automate the Boring Stuff 

import bs4, requests

def getFlameThrowerPrice(productUrl):
        res = requests.get(productUrl)
        res.raise_for_status()

soup = bs4.BeautifulSoup(res.text, 'html.parser')
        elems = soup.select('#prcIsum')
        return elems[0].text.strip()


def getSandwichMakerPrice(productUrl):
        res = requests.get(productUrl)
        res.raise_for_status()

soup = bs4.BeautifulSoup(res.text, 'html.parser')
        elems = soup.select('#tab-panel-0-w2 > div > span.item-price > h2')
        return elems[0].text.strip()

FFprice = getFlameThrowerPrice('https://www.ebay.com/itm/The-Boring-Company-s-ORIGINAL-Not-A-Flamethrower-Elon-Musk-Manual-/173605477011')

SMPrice = getSandwichMakerPrice('https://www.ebay.co.uk/p/3019375530?iid=112476712340')

print('The Price of a flamethrower is ' + FFprice + '.\nThe price of a sandwich maker is ' + SMPrice)

