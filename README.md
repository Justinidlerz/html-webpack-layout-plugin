Layout extension for the HTML Webpack Plugin
========================================

Enhances [html-webpack-plugin](https://github.com/ampedandwired/html-webpack-plugin)
functionality by adding the `{layout: 'layoutPath', replace : 'replaceStr'}` option.

This is an extension plugin for the [webpack](http://webpack.github.io) plugin [html-webpack-plugin](https://github.com/ampedandwired/html-webpack-plugin) - a plugin that simplifies the creation of HTML files to serve your webpack bundles.

Installation
------------
You must be running webpack on node 0.12.x or higher

Install the plugin with npm:
```shell
$ npm install --save-dev html-webpack-layout-plugin
```

Basic Usage
-----------
Add the plugin to your webpack config as follows:

```javascript
plugins: [
  new HtmlWebpackPlugin(),
  new HtmlWebpackLayoutPlugin()
]  
```
The above configuration will actually do nothing due to the configuration defaults.

As soon as you now set `layout` to a path the generated output of the HtmlWebpackPlugin will
always add a layout. 
```javascript
plugins: [
  new HtmlWebpackPlugin({
		layout: path.join(__dirname, 'layout.html')
	}),
  new HtmlWebpackLayoutPlugin()
]  
```

layout.html   
```html
<html>
	<head></head>
	<body>
		{{content}}
	</body>
</html>

```

Even if you generate multiple files make sure that you add the HtmlWebpackLayoutPlugin **only once**:

```javascript
plugins: [
  new HtmlWebpackPlugin({
		layout: path.join(__dirname, 'layout.html')
	}),
  new HtmlWebpackPlugin({
		layout: path.join(__dirname, 'layout.html'),
		filename: 'demo.html'
	}),
  new HtmlWebpackPlugin({
		layout: path.join(__dirname, 'layout.html'),
		filename: 'test.html'
	}),
  new HtmlWebpackLayoutPlugin()
]  
```
