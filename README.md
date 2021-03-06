# Bows
![Colors](https://raw.github.com/latentflip/bows/master/example/cols.png)
Safe, production happy, colourful logging for chrome - makes reading your logs _much_ easier.


(Rain)bows makes logging debug messages in your apps much nicer.
- It allows you to create custom loggers for each module in your app, that prefix all log messages with the name of the app, so that you can scan the messages more easily.
- It colors the prefix differently and distinctly for each logger/module so that it's even easier to read.
- It can be safely used in production, where logging will be disabled by default, so that you can leave log messages in your code.
- Loggers safely wrap console.log, to maintain the line number from where they are called in the console output.

![Example Output](https://raw.github.com/latentflip/bows/master/example/realexample.png)

## Installation.

If you are using browserify, you'll want something like:

```
npm install bows --save
```

If you aren't using browserify, download either [bows.js](https://raw.github.com/latentflip/bows/master/dist/bows.js) or [bows.min.js](https://raw.github.com/latentflip/bows/master/dist/bows.min.js).

## Usage
- Works great in browserify and the browser.
- Creating a new logger:
  - Browserify: `var log = require('bows')("My Module Name")`
  - Browser: `var log = bows("My Module Name")`
- Then using it is easy:
  - `log("Module loaded") //-> "My Module Name | Module Loaded"`
  - `log("Did something") //-> "My Module Name | Did something"`
- Typically each seperate module/view/etc in your app would create it's own logger. It will be assigned it's own color to make it easy to spot logs from different modules.
- Logging is disabled by default. To enable logging, set `localStorage.debug = true` in your console and refresh the page.
- You can leave the code in in production, and log() will just safely no-op unless localStorage.debug is set.

## Example

```javascript
  //Should be set in your console to see messages
  localStorage.debug = true
  //Configure the max length of module names (optional)
  bows.config({ padLength: 10 })

  var logger1 = bows('Module 1')
  var logger2 = bows('Module 2')
  var logger3 = bows('Module 3')

  logger1("We started up")
  logger2("We did something too")
  logger3("I'm here")
  logger3("I'm still here")
  logger2("I'm tired")
  logger1("We're done here")
```

Result:

![Example Output](https://raw.github.com/latentflip/bows/master/example/example.png)

## License

MIT

Copyright Philip Roberts [latentflip.com](http://latentflip.com)


## Contributing

Please feel free to raise issues, or make contributions:

```bash
git clone https://github.com/latentflip/bows.git
cd bows
npm install #install dependencies
#edit bows.js
node build.js #build dist/bows.js and dist/bows.min.js
```

