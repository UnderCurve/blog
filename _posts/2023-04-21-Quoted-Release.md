# Quoted Release
So I made a little web app called Quoted using the https://quotable.io/ API. The main reason why I did this was to expand my knowledge of APIs and PWAs. So I did a bit of coding and made my first PWA Quoted.
## PWAs Explained sorta.
You start with a manifest.json which looks a bit like the code below
`manifest.json`
```
{
        "name": "Quoted • Your Daily Quote",
        "short_name": "Quoted",
        "start_url": "/Quoted",
        "icons": [
            {
              "src": "icons/manifest-icon-192.maskable.png",
              "sizes": "192x192",
              "type": "image/png",
              "purpose": "any"
            },
            {
              "src": "icons/manifest-icon-192.maskable.png",
              "sizes": "192x192",
              "type": "image/png",
              "purpose": "maskable"
            },
            {
              "src": "icons/manifest-icon-512.maskable.png",
              "sizes": "512x512",
              "type": "image/png",
              "purpose": "any"
            },
            {
              "src": "icons/manifest-icon-512.maskable.png",
              "sizes": "512x512",
              "type": "image/png",
              "purpose": "maskable"
            }
          ],
        "theme_color": "#000000",
        "background_color": "#FFFFFF",
        "display": "fullscreen",
        "orientation": "portrait"
}
```
and load it into your html with `<link rel="manifest" href="manifest.json">`.
then you need a service worker or:
`sw.js`
```
importScripts('https://storage.googleapis.com/workbox-cdn/releases/6.4.1/workbox-sw.js');

workbox.routing.registerRoute(
    ({request}) => request.destination === 'image',
    new workbox.strategies.NetworkFirst()
);
```
and you load that in with:
```
    <script>
        if ('serviceWorker' in navigator) {
            navigator.serviceWorker.register('sw.js');
        }
    </script>
```
and boom you have a PWA app.
But if you want to learn more about PWAs I would recommend [PWAs in 100 Seconds by Fireship](https://youtu.be/sFsRylCQblw).

But see ya 👋
