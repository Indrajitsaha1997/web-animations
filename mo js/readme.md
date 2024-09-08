**Mo.js** is a powerful, fast, and customizable JavaScript motion graphics library that is perfect for complex animations, with flexibility and performance in mind. It provides a variety of modules such as shapes, bursts, and timeline management for creating intricate animations.

### **Getting Started with Mo.js**

You can include Mo.js in your project using a CDN link:

```html
<script src="https://cdn.jsdelivr.net/npm/@mojs/core"></script>
```

### **Example 1: Basic Shape Animation**

In this example, we will create a simple circle animation using Mo.js.

#### **HTML Example:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mo.js Basic Example</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f4f4f4;
    }
  </style>
</head>
<body>
  <script src="https://cdn.jsdelivr.net/npm/@mojs/core"></script>
  <script>
    // Create a circle shape with Mo.js
    const circle = new mojs.Shape({
      shape: 'circle',
      fill: 'none',
      stroke: 'cyan',
      strokeWidth: { 20: 0 },
      radius: { 0: 100 },
      duration: 2000,
      easing: 'cubic.out'
    });

    // Play the animation
    circle.play();
  </script>
</body>
</html>
```

**Explanation:**
- **mojs.Shape()**: Creates a new shape. The options define the type of shape (`circle`), the fill/stroke colors, the stroke width, and the radius animation.
- **play()**: Starts the animation.
- **strokeWidth: { 20: 0 }**: Animates the stroke width from 20 to 0.
- **radius: { 0: 100 }**: Animates the radius from 0 to 100.
- **duration**: Specifies the time (2000ms or 2 seconds) for the animation.

### **Example 2: Burst Animation**

In this example, we'll create a burst effect where multiple lines shoot out from the center.

#### **HTML Example:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mo.js Burst Animation</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f4f4f4;
    }
  </style>
</head>
<body>
  <script src="https://cdn.jsdelivr.net/npm/@mojs/core"></script>
  <script>
    // Create a burst animation with Mo.js
    const burst = new mojs.Burst({
      radius: { 0: 150 },
      count: 10,
      children: {
        shape: 'line',
        stroke: 'blue',
        strokeWidth: { 10: 0 },
        duration: 1000
      }
    });

    // Play the burst animation
    burst.play();
  </script>
</body>
</html>
```

**Explanation:**
- **mojs.Burst()**: Creates a burst animation with multiple lines shooting out.
- **radius: { 0: 150 }**: Sets the radius animation from 0 to 150.
- **count: 10**: Creates 10 lines in the burst.
- **children**: Defines the individual properties for each line (e.g., shape, stroke, strokeWidth).

### **Example 3: Timeline Control**

Mo.js provides powerful timeline management, allowing you to control when animations start and stop. This example shows how to synchronize two animations using a timeline.

#### **HTML Example:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mo.js Timeline Example</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f4f4f4;
    }
  </style>
</head>
<body>
  <script src="https://cdn.jsdelivr.net/npm/@mojs/core"></script>
  <script>
    // First animation: expanding circle
    const circle = new mojs.Shape({
      shape: 'circle',
      fill: 'none',
      stroke: 'red',
      radius: { 0: 100 },
      strokeWidth: { 20: 0 },
      duration: 2000
    });

    // Second animation: square rotation
    const square = new mojs.Shape({
      shape: 'rect',
      fill: 'none',
      stroke: 'green',
      strokeWidth: { 20: 0 },
      radius: 50,
      duration: 2000,
      angle: { 0: 180 }
    });

    // Create a timeline and add both animations
    const timeline = new mojs.Timeline();
    timeline.add(circle, square);

    // Play the timeline
    timeline.play();
  </script>
</body>
</html>
```

**Explanation:**
- **mojs.Timeline()**: Allows you to sequence animations.
- **timeline.add(circle, square)**: Adds the circle and square animations to the timeline.
- Both the circle and square animations will play together when `timeline.play()` is called.

### **Example 4: Burst on Click Event**

In this example, we'll trigger a burst animation when the user clicks on the page.

#### **HTML Example:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mo.js Burst on Click</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f4f4f4;
    }
  </style>
</head>
<body>
  <script src="https://cdn.jsdelivr.net/npm/@mojs/core"></script>
  <script>
    // Burst animation on click
    const burst = new mojs.Burst({
      radius: { 0: 150 },
      count: 8,
      children: {
        shape: 'circle',
        fill: ['cyan', 'magenta', 'yellow'],
        radius: { 20: 0 },
        duration: 1500
      }
    });

    // Trigger burst animation on click event
    document.addEventListener('click', (e) => {
      burst.tune({ x: e.pageX, y: e.pageY }).replay();
    });
  </script>
</body>
</html>
```

**Explanation:**
- **document.addEventListener('click', ...)**: Listens for the click event and triggers the burst animation at the clicked position.
- **burst.tune({ x: e.pageX, y: e.pageY })**: Moves the burst animation to the mouse click location before replaying it.
- **replay()**: Restarts the animation from the beginning.

### **Example 5: Polygon Animation with Easing**

In this example, we will animate a polygon shape with a bounce easing effect.

#### **HTML Example:**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Mo.js Polygon Animation</title>
  <style>
    body {
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
      margin: 0;
      background-color: #f4f4f4;
    }
  </style>
</head>
<body>
  <script src="https://cdn.jsdelivr.net/npm/@mojs/core"></script>
  <script>
    // Create a polygon animation with bounce easing
    const polygon = new mojs.Shape({
      shape: 'polygon',
      points: 6, // Creates a hexagon
      fill: 'none',
      stroke: 'purple',
      radius: { 0: 100 },
      strokeWidth: { 20: 0 },
      duration: 2000,
      easing: 'bounce.out' // Easing effect
    });

    // Play the polygon animation
    polygon.play();
  </script>
</body>
</html>
```

**Explanation:**
- **shape: 'polygon'**: Creates a polygon shape. The `points` property defines the number of vertices (6 for a hexagon).
- **easing: 'bounce.out'**: Applies a bounce easing effect to the animation.

---

### **Summary of Mo.js Features:**
- **Shapes**: Mo.js provides customizable shapes (e.g., circle, polygon) with advanced control over their properties.
- **Bursts**: Create burst animations with lines, circles, or other shapes.
- **Timeline**: Easily control multiple animations in a timeline, allowing for complex