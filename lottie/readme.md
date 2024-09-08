Lottie by Airbnb allows you to use JSON-based animations created in Adobe After Effects (with the Bodymovin plugin) on the web and mobile platforms. Here's how you can get started with Lottie, including examples for web usage.

### **Getting Started with Lottie**

**1. **Include Lottie in Your Project**

You can include Lottie via CDN or install it via npm.

- **CDN:**
  ```html
  <script src="https://cdnjs.cloudflare.com/ajax/libs/bodymovin/5.7.14/lottie.min.js"></script>
  ```

- **npm:**
  ```bash
  npm install lottie-web
  ```

**2. Create an Animation in After Effects**

1. Create your animation in Adobe After Effects.
2. Install the [Bodymovin plugin](https://aescripts.com/bodymovin/) for After Effects.
3. Export your animation as a JSON file using the Bodymovin plugin.

**3. Basic Example: Displaying a Lottie Animation**

**HTML:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lottie Example</title>
    <style>
        #lottie-container {
            width: 300px;
            height: 300px;
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <div id="lottie-container"></div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/bodymovin/5.7.14/lottie.min.js"></script>
    <script>
        // Load and display the animation
        const animation = lottie.loadAnimation({
            container: document.getElementById('lottie-container'), // Container for the animation
            renderer: 'svg', // Render as SVG
            loop: true, // Loop the animation
            autoplay: true, // Start playing the animation immediately
            path: 'path/to/your/animation.json' // Path to the JSON file
        });
    </script>
</body>
</html>
```

**4. Advanced Example: Controlling Animation**

You can control playback, speed, and other properties of the animation.

**HTML:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lottie Control Example</title>
    <style>
        #lottie-container {
            width: 300px;
            height: 300px;
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <div id="lottie-container"></div>
    <button onclick="playAnimation()">Play</button>
    <button onclick="pauseAnimation()">Pause</button>
    <button onclick="stopAnimation()">Stop</button>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/bodymovin/5.7.14/lottie.min.js"></script>
    <script>
        const animation = lottie.loadAnimation({
            container: document.getElementById('lottie-container'),
            renderer: 'svg',
            loop: true,
            autoplay: false, // Disable autoplay
            path: 'path/to/your/animation.json'
        });

        function playAnimation() {
            animation.play();
        }

        function pauseAnimation() {
            animation.pause();
        }

        function stopAnimation() {
            animation.stop();
        }
    </script>
</body>
</html>
```

**5. Advanced Example: Animation with Event Listeners**

You can listen for events and handle them accordingly.

**HTML:**
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lottie Event Example</title>
    <style>
        #lottie-container {
            width: 300px;
            height: 300px;
            margin: 0 auto;
        }
    </style>
</head>
<body>
    <div id="lottie-container"></div>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/bodymovin/5.7.14/lottie.min.js"></script>
    <script>
        const animation = lottie.loadAnimation({
            container: document.getElementById('lottie-container'),
            renderer: 'svg',
            loop: true,
            autoplay: true,
            path: 'path/to/your/animation.json'
        });

        // Listen for animation complete event
        animation.addEventListener('complete', function() {
            console.log('Animation completed');
        });

        // Listen for animation frame change event
        animation.addEventListener('enterFrame', function(e) {
            console.log('Frame:', e.currentTime);
        });
    </script>
</body>
</html>
```

### **Explanation**

- **Basic Example:** Displays a Lottie animation in a specified container.
- **Advanced Control:** Provides functions to play, pause, and stop the animation.
- **Event Listeners:** Adds event listeners for animation events, such as completion or frame changes.

Lottie is a powerful tool for adding high-quality animations to your web projects. It enables you to create complex animations in After Effects and integrate them easily into your website or application. For more details and advanced usage, you can refer to the [Lottie documentation](https://airbnb.io/lottie/).