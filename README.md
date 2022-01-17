# Do you have questions How to integrate ReactJS or VueJS with Magento 2 frontend? This Magento module will help you
React Magento 2 implementation. This Simple module explains how to add and use React Components with Magento 2 and forgot about Knockout/JQuery Magento 2 UI.
![React + Magento 2](https://github.com/Genaker/reactmagento2/blob/master/KnockoutMagento2React.png)

# Updates:
- New improved version with the React 17 is available as a **react-17** branch (https://github.com/Genaker/reactmagento2/tree/react-17)
- This version provides stand-along React 17 without using RequireJS
- Default branch changed to **react-17**
- Composer package creted **composer require genaker/magento-reactjs**
- VueJS implementation 
- Magento Configuration enable React, VueJS  

It is not PWA or headless implementation which is impossible to use with an existing website. Also Single Page Application (SPA) PWA Magento 2 implementations have issues with Magento 2 API performance - too slow. This implementation is High-Performance Hybrid React integration with magento2 (with Magento 1 also easy to use) it uses inline JSON directly from the page. The same approach is used in Magento 2 backend and frontend checkout, color swatches by default. Also can use Ajax HTTP call to fetch data (not the best solution Magento API is slow and will increase the load on your backend server). Or you can use my future project "Microservices Magento" to fetch data.
Our simplest Magento 2 module uses WebPack for React Components Compilation and automatic static content deployment into the Magento pub/static folder.

You can develop React components even without Magento installation at all. You can just copy your component inside Magento Module and add some fixes into sources to work with Require JS and use React Component as Magento UI component.

# Install Magento ReactJS/VueJS extension via composer:
```
composer require genaker/magento-reactjs
```

# Magento 2 Admin module built with ReactJS instead of the legacy default JS:

(https://github.com/Genaker/Magento2OPcacheGUI)

# How to use WebPack for React with Magento 2

Install Node.JS (https://github.com/nodesource/distributions/blob/master/README.md) From the extension root (React/React) folder run:

```
npm install
npm start
```

Web Puck compiles everything automatically into React/React/view/base/web/js/index_bundle.js and deploys to pub/static without running static:deploy ssh command. LiveReload Plugin will reload Magento 2 pages automatically (not recommended solution by React Community. F5  more reliable solution). What you need just disable the Cache of your browser during development. Also, You can disable caching for single react bundle files via Nginx config.

# Easy deployment 

Usage of the web-pack sometimes is too difficult for Magento developers. I have created another way to use React with Magento without any compilation/complication.
Simply add these files to the Magento installation:
```
// React JS itself 
<script src='https://npmcdn.com/react-dom@15.3.0/dist/react-dom.min.js'></script>
// Babel to avoid compilation 
<script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>

//Add to the page to render React component
<div id = "magentoReactApp"> </div>

//Write you scripts using babel 
<script type="text/babel">

var App = React.createClass({
	render: function() {
		return(
			<div className="App">
	             {/*Your APP code there */}
			</div>
		);
	}
});
ReactDOM.render(
	<App />,
	document.getElementById('magentoReactApp')
);
</script>
```

# What is Babel for Magento?
Babel is a JavaScript compiler
Babel is a toolchain that is mainly used to convert ECMAScript 2015+ code into a backward-compatible version of JavaScript in current and older browsers or environments. Here are the main things Babel can do for you:

Transform syntax:
- Polyfill features that are missing in your target environment (through @babel/polyfill)
- Source code transformations (codemods)

# JSX and React with Magento 1,2 

JSX is an XML-like syntax extension to ECMAScript without any defined semantics. It's NOT intended to be implemented by engines or browsers. It's NOT a proposal to incorporate JSX into the ECMAScript spec itself. It's intended to be used by various preprocessors (transpilers) to transform these tokens into standard ECMAScript. In our case transpiler is Babel. 
Babel can convert JSX syntax!

Use Bable for Magento via UNPKG: https://unpkg.com/@babel/standalone/babel.min.js. This is a simple way to embed it on a webpage without having to do any other setup.

When loaded in a browser, @babel/standalone will automatically compile and execute all Magento’s script tags with type 'text/babel' or 'text/jsx'

# Magento 2 live reload

This project aims to solve the case where you want assets served by your Magento app server, but still want reloads triggered from web packs build pipeline.

Add a script tag to your page pointed at the livereload server

```
<script src="http://localhost:35729/livereload.js"></script>
```
For development purpose better disable browser caching (https://www.technipages.com/google-chrome-how-to-completely-disable-cache)

Disable react bundle caching for development purpose using Nginx (not tested yet):

```
location ~ index_bundle\.js {
    add_header Cache-Control no-cache;
    expires 0;
  }
```

# Similar Projects:
Magento 2 Admin module built with ReactJS instead of legacy Magento default JS: (https://github.com/Genaker/Magento2OPcacheGUI)

Good Magento 2 react approach from a good guy: (https://github.com/yireo-training/Yireo_ReactMinicart)

Something similar from integer_net GmbH : (https://github.com/integer-net/magento2-reactapp)


## A lot of Big e-commerce companies Already Use this React Approach :
BestBuy.mx
beautycounter.com
icuracao.com
bloomnation.com
plantt.com
gap.com
walmart.com
