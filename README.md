## Website Performance Optimization portfolio project



####Part 1: Optimize PageSpeed Insights score for index.html

1. Open index.html.

To set up a web server:

  ```bash
  $> cd /path/to/your-project-folder
  $> python -m SimpleHTTPServer 8080
  ```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ngrok 8080
  ```

1. Copy the public URL ngrok gives you and try running it through PageSpeed Insights!

To optimize this site, I:
1. Copied the Latin font definitions of http://fonts.googleapis.com/css?family=Open+Sans:400,700 into index.html
1. Copied the contents of css/style.css into index.html
1. Set the media of css/print.css to "print"
1. Made the requests for http://www.google-analytics.com/analytics.js and js/perfmatters.js asynchronous.
1. Resized the images using gimp down to the dimensions shown on the page.

####Part 2: Optimize Frames per Second in pizza.html

1. Open views/pizza.html.

My primary optimizations were:
1. In updatePositions(), I fetched the document.body.scrollTop before entering the loop in order to avoid redrawing the page on each iteration in the loop.
1. Used requestAnimationFrame() instead of scroll events to fire updatePositions().  This causes the browser to do more work overall, but I am guaranteed to run at the proper phase in the rendering cycle.
1. When creating the animated pizzas, put each one in its own layer using style.willChange = 'transform'.