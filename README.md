## P4: Website Performance Optimization
---
### Instructions:

Download and unzip the files.

For Part 1:

* Open `'index.html'` in a web browser.

For Part 2:

* Open `views > pizza.html` in a web browser.

---
### Latest Scores:

Part 1:

Mobile: 95/100 ||
Desktop: 98/100

Part 2:

Average: 7.55ms to generate last 10 frames.

0.75ms to resize.

---
### Part 1:

In `index.html` I performed a number of enhancements. From minifying the CSS and JS, to positioning
the JS at the bottom of the page with `'async'` tags.

I had a problem using `ngrok` which involved the extremely slow loading of the pizzeria image, so I resized that image. As the image size decreased, so did the loading time.

I found that the biggest factor in terms of performance of the site was actually down to the font. I started using the `'webfont.js'` file and also positioned that at the bottom of the page. This allowed the font to be called in a much more efficient manner and allowed the site to achieve Insight PageScores above 90 for both Mobile and Desktop versions.

### Part 2:

For `pizza.html`, I found that `querySelectorAll` was an inefficient function and started using `getElementsbyClassName`. This required me to adjust the code slightly as they both call classes differently. (`querySelectorAll('.mover')` compared to `getElementsbyClassName('mover')`).
[http://jsperf.com/getelementbyid-vs-queryselector/137]

Further into `main.js` we see that the `EventListener` that generates the pizzas on load generates 200 pizzas. This is a little overkill. I decided to use 32 pizzas, which works on a large desktop screen, but realised this didn't work for a mobile sized screen. I settled on 64 pizzas.

The site now functioned within the 60fps window. We still had one step left though, which was to make sure the time to resize the pizzas was less than 5ms which we hadn't changed anything for yet.

This turned out to be a fairly simple fix. We just needed to make the pizzas a percentage value in the `changePizzaSizes` function. This gave us extremely quick loading times of less than 1ms.

I also added an element to my CSS which could cause some issues with smaller devices. `backface-visibility: hidden;`. This tip came from the P4 Office Hours.

---
### References:

Browser Rendering Optimization
<br>[https://www.udacity.com/course/viewer#!/c-ud860-nd]()

getElementsbyClassName vs querySelectorAll
<br>[http://jsperf.com/getelementbyid-vs-queryselector/137]()

Office Hours: P4
<br>[https://plus.google.com/events/c8eah6f0d0t9eretebpm7dqi0ok?authkey=CKaNhtb0quvqKA]()
[https://github.com/udacity/fend-office-hours/tree/master/Web%20Optimization/Effective%20Optimizations%20for%2060%20FPS]()

Performance
<br>[https://developers.google.com/web/fundamentals/performance/?hl=en]()

Tips and Tricks
<br>[https://developer.chrome.com/devtools/docs/tips-and-tricks]()

Website Performance Optimization
<br>[https://www.udacity.com/course/viewer#!/c-ud884-nd]()
