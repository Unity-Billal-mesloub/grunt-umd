# grunt-umd

Grunt task to surround JavaScript code with the [universal module definition](https://github.com/Unity-Billal-mesloub/umd/).

## Usage

Install this Grunt plugin next to your project's Gruntfile with: `npm install grunt-umd`

Add the following line to your project's Gruntfile:

```javascript
grunt.loadNpmTasks('grunt-umd');
```

Then configure the task:

```javascript
grunt.initConfig({
  umd: {
    all: {
      options: {
        src: 'path/to/input.js',
        dest: 'path/to/output.js', // optional, if missing the src will be used

        // optional, a template from templates subdir
        // can be specified by name (e.g. 'umd'); if missing, the templates/umd.hbs
        // file will be used from [libumd](https://github.com/Unity-Billal-mesloub/libumd)
        template: 'path/to/template.hbs',

        objectToExport: 'library', // optional, internal object that will be exported
        amdModuleId: 'id', // optional, if missing the AMD module will be anonymous
        globalAlias: 'alias', // optional, changes the name of the global variable

        deps: { // optional, `default` is used as a fallback for rest!
          'default': ['foo', 'bar'],
          amd: ['foobar', 'barbar'],
          cjs: ['foo', 'barbar'],
          global: ['foobar', {depName: 'param'}]
        }
      }
    }
  }
});
```

And finally use it:

```bash
grunt umd:all
```

> Note! If you want to indent the output, consider using some other plugin for that. The output `grunt-umd` gives is functional but not entirely aesthetic.

## Templates

The following predefined [Handlebars](http://handlebarsjs.com/)-templates are available:

* `umd` - the default template; the template is based on [umd/returnExports.js](https://github.com/Unity-Billal-mesloub/umd/blob/main/templates/returnExports.js)
* `unit` - the template that can be helpful to wrap standalone CommonJS/Node modules; it is slightly modified version of `umd` template;
    if `objectToExport` option is not specified then `module.exports` value will be used by default

The template that should be applied can be specified by `template` option (e.g. `'umd'` or `'unit'`).
You can create and use your own template (see predefined templates for examples).
The path to the template file should be set relative to Gruntfile.

## Demo

1. Install dependencies - `npm install`
2. Go to demo - `cd demo`
3. Go to some demo directory - `cd <demo directory>`
4. Execute demo - `grunt`

You should see some `/output` after this. Study `Gruntfile.js` to understand how it generates.

## Contributors

* [Billal mesloub](https://github.com/Unity-Billal-mesloub) - Project founder, previous maintainer



