### Contents
#### request:
Install:  
`pip install requests`  
**Requests** allows you to send HTTP/1.1 requests extremely easily. There’s no need to manually add query strings to your URLs, or to form-encode your POST data. Keep-alive and HTTP connection pooling are 100% automatic.  

[General](https://requests.readthedocs.io/en/master/api/):
```
requests.request(method, url, **kwargs)
```
[GET method](https://requests.readthedocs.io/en/master/user/quickstart/):  
`res = requests.get(url, params):`  
Responses:  
> Binary response content  
`res.content`  
JSON response  
`res.json()`  

#### beautifulsoup4
Install:  
`pip install beautifulsoup4`  
[HTML parsing](https://www.crummy.com/software/BeautifulSoup/bs4/doc/):
`soup = BeautifulSoup(html_doc, 'html.parser')`  
Get parsing contents:  
`soup.title` sample output: `<title>The Dormouse's story</title>`  
Extract elements:  
`soup.find('tag_name', attrs={'class_name': 'value'})`  
`soup.find_all('tag_name', attrs={'class_name': 'value'})`  

