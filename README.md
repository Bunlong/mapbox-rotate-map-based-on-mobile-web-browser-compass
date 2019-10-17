# Mapbox rotate map based on mobile web browser compass

```html
<!DOCTYPE html>
<html>
  <body>
    <div id="display" />

    <script>
      // ...

      const easing = t => t * (2 - t);

      if (window.DeviceOrientationEvent) {
        window.addEventListener('deviceorientation', event => {
          let compassdir;

          if (event.webkitCompassHeading) {
            // Safari browser
            compassdir = event.webkitCompassHeading;
          } else {
            compassdir = event.alpha;
          }

          myMap.easeTo({
            bearing: 360 - compassdir,
            easing: easing
          })
        })
      } else {
        alert("Sorry, your browser doesn't support Device Orientation");
      }
    </script>
  </body>
</html>
```
