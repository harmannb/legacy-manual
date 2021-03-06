---
title: Responsive Applications
layout: layout.html
---

# Responsive Applications

## Application JavaScript

```js
new Window.apply('ApplicationSomethingWindow', {
  width: 400,
  height: 300,
  media_queries: {
    myattr: function(w, h, ref) {
      return w <= 500;
    }
  }
}, app, scheme);
```

## Application Stylesheet

```css
/* Default rules */
.ApplicationSomethingWindow[data-media="mobile"] application-window-content {
  background: yellow;
}
.ApplicationSomethingWindow[data-media="tablet"] application-window-content {
  background: orange;
}
.ApplicationSomethingWindow[data-media=""] application-window-content {
  background: blue;
}

/* Custom rule: 500px or below */
.ApplicationSomethingWindow[data-media="myattr"] application-window-content {
  background: red;
}
```

## Global rules


You can also add/modify global rules. See `src/conf/114-windowmanager.json`.

These rules are checked with `val <= window_width`.

### Base Config

```json
{
  "client" : {
    "WM" : {
      "args": {
        "defaults": {
          "mediaQueries": {
            "mobile": 320,
            "tablet": 800
          }
        }
      }
    }
  }
}
```

Run `node osjs build:config` if you change these settings.

### Base CSS

```css
application-window[data-media="mobile"] application-window-content {
  background: yellow;
}
application-window[data-media="tablet"] application-window-content {
  background: orange;
}
application-window[data-media=""] application-window-content {
  background: blue;
}
```
