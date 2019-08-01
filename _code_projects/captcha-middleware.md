---
human_title: CAPTCHA Middleware
link: https://github.com/owen9825/captcha-middleware
image: https://media.giphy.com/media/gaDBMncAI7HEs/giphy.gif
alt: "A robot becoming self-aware"
---
[Here](https://github.com/owen9825/captcha-middleware) I used computer vision to read the distorted [CAPTCHA](https://en.wikipedia.org/wiki/CAPTCHA) images and thereby prevent human slaves from having to do the work of curious bots that just want to fetch data in a repeatable way.

It fits in nicely with [Scrapy](https://scrapy.org/), checking for the presence of a CAPTCHA image and solving the test; and fetching the page that was intended to be seen; before giving that back to Scrapy seamlessly.
