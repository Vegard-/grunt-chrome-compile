#Inspired by original grunt-chrome-compile by scarrillo
Original didn't works on my Windows 7x64 PC due spaces in files names, so I've adapted tasks.

# grunt-contrib-build-crx
> Package a google chrome extension.

## Getting Started
This plugin requires Grunt `~0.4.1`

If you haven't used [Grunt](http://gruntjs.com/) before, be sure to check out the [Getting Started](http://gruntjs.com/getting-started) guide, as it explains how to create a [Gruntfile](http://gruntjs.com/sample-gruntfile) as well as install and use Grunt plugins. Once you're familiar with that process, you may install this plugin with this command:

```shell
npm install grunt-contrib-build-crx --save-dev
```

One the plugin has been installed, it may be enabled inside your Gruntfile with this line of JavaScript:

```js
grunt.loadNpmTasks('grunt-contrib-build-crx');
```

## The "chrome_compile" task

### Overview
In your project's Gruntfile, add a section named `chrome-extension` to the data object passed into `grunt.initConfig()`.

```js
grunt.initConfig({
    'manifest': grunt.file.readJSON('manifest.json'),
    'chrome-extension': {
        options: {
            name: "Demo Extension <%= manifest.version %>",
            chrome: 'C:\\Program Files (x86)\\Google\\Chrome\\Application\\chrome.exe',
            certPath: '../demoExtension.pem',
            crxPath: '../demoExtension <%= manifest.version %>.crx',
            buildDir: '../demoExtensionBuild',
            zipPath: '../demoExtension <%= manifest.version %>.zip',
            clean: true,
            cleanPath: '../demoExtensionBuild',
            resources: [
                "_locales/**",
                "css/**",
                "img/**",
                "js/**",
                "*.html",
                "manifest.json",
                "*.md"
            ]
        }
    }
})
```
### Options

#### options.name
Type: `String`
Default value: `demo-ext`

The name of your google chrome extension

#### options.chrome
Type: `String`
Default value: OSX Path

The path to your Google Chrome installation.
* OSX: /Applications/Google Chrome.app/Contents/MacOS/Google Chrome
* OSX Canary: /Applications/Google Chrome Canary.app/Contents/MacOS/Google Chrome Canary
* Windows: C:\Users\user\AppData\Local\Google\Chrome\Application\chrome.exe

#### options.certPath
Type: `String`

Relative location to your extension's certificate.

#### options.crxPath
Type: `String`

.CRX will be created here.

#### options.buildDir
Type: `String`
Default value: `build`

Relative location to your build directory.

#### options.zipPath
Type: `String`

.ZIP will be created here.

#### options.clean
Type: `String`

Remove build files or not.

#### options.cleanPath
Type: `String`

Path to temporary files

#### options.resources
Type: `array`

Project resources that should be packaged into the final .zip and .crx.

__Caution__: Make sure your cert files are not included here

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality. Lint and test your code using [Grunt](http://gruntjs.com/).
