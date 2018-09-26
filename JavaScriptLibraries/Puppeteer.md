# Puppeteer

Puppeteer is a headless chrome browser that is run on NodeJS. The offical documentation can be found here <a href="https://www.npmjs.com/package/puppeteer">https://www.npmjs.com/package/puppeteer</a>

In The Big Crunch Puppeteer can be used to import values from websites into the cells.

Here's an example where the domain `example.com` is being scraped.

```JavaScript
var result = '';
puppeteer.launch({args:['--no-sandbox', '--disable-setuid-sandbox']}).then(browser => {
  var page;
  return browser.newPage()
      .then(p => {
  		page = p;
        return page.goto('https://example.com', {waitUntil: 'networkidle2'});
	  })
      .then(resp => page.evaluate(() => document.querySelector('h1').textContent))
      .then(a =>  {
          result = a;
          return browser.close()
  	  }).then(b => {
      	  return result;
      });
});
```
