### Proxy Sites
- [KuaiDaili](https://www.kuaidaili.com/free/) (快代理，literal meaning: Quick Proxy)
- [YunDaili](http://www.ip3366.net/) (云代理，literal meaning: Cloud Proxy)


### Proxy in `requests`

We can simply encapsulate the proxies inside a dict, then make the request with the dict:
```python
url = 'https://httpbin.org/ip'

proxies = {
    # '(http|https)': '[<username>:<password>@]<ip><port>'
    'https': 
}

requests.get(url, proxies=proxies)
```

---

### Cookie
In short, **cookie** is a piece of data servers used for tracking sessions and identifying users. Although it is typically stored on users' computers, there can be exceptions to it: 

HTTP is often known as a **stateless** protocol due to the fact that it processes each request independently, without regards to the previous ones. However, with the advent of cookies, the improved version of HTTP —— namely, HTTPS —— becomes a **stateful** protocol. This improvement fundamentally changes the way client interacts with the server: Using cookie, the server is able to "remember" the information carried by previous requests and treats the current request accordingly.

### Cookie with `requests`

Here are some basic steps to follow:
1. Get the URL of the login page (the page where you need to enter your username and password)
2. Create a `session` object using `requests.Session()`
3. Make a post request to URL in Step 1 (e.g. `session.post(url, data={'username': ABC, 'password': 123})` [1]
4. Get the URL of the target page (the page that is only accessible after login)
5. Using the same `session` in Step 3 and 2, make a get request to that URL

[1]: This step will save the cookies to the `session` object you created in Step 2.
