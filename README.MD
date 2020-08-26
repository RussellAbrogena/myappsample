# [My sample App]

##### The React-based front-end framework for building experiences for Office and Office 365.

Fabric React is a responsive, mobile-first collection of robust components designed to make it quick and simple for you to create web experiences using the Office Design Language.

### Tutorial
[Here is a step by step tutorial](https://github.com/OfficeDev/office-ui-fabric-react/blob/master/ghdocs/README.md) on how to build a simple React app with an Office UI Fabric React component.

### Integrate into an existing project
Integrating components into your project depends heavily on your setup. The recommended setup is to use a bundler such as Webpack which can resolve NPM package imports in your code and can bundle the specific things you import.

Within an npm project, you should install the package and save it as a dependency:

```
npm install --save office-ui-fabric-react
```

This will add the fabric-react project as a dependency in your package.json file, and will drop the project under node_modules/office-ui-fabric-react.

The library includes commonjs entry points under the lib folder. To use a control, you should be able to import it and use it in your render method:

```js
import * as React from 'react';
import * as ReactDOM from 'react-dom';
import { Button } from 'office-ui-fabric-react/lib/Button';

const MyPage = () => (<div><Button>I am a button.</Button></div>);

ReactDOM.render(<MyPage />, document.body.firstChild);
```

## Rendering Fabric components on the server (SSR)

If you need to render Fabric components on the server side in a node environment, there is a way to do this. The basic idea is that you need to tell the styles loader to pipe styles into a variable, which you can later use to inject into your page. Example:

```ts
import { configureLoadStyles } from '@microsoft/load-themed-styles';

// Store registered styles in a variable used later for injection.
let _allStyles = '';

// Push styles into variables for injecting later.
configureLoadStyles((styles: string) => {
  _allStyles += styles;
});

import * as React from 'react';
import * as ReactDOMServer from 'react-dom/server';
import { Button } from 'office-ui-fabric-react/lib/Button';

let body = ReactDOMServer.renderToString(<Button>hello</Button>);

console.log(
  `
  <html>
  <head>
    <style>${ _allStyles}</style>
  </head>
  <body>
    ${ body}
  </body>
  </html>
  `);
```


## Browser support

Fabric React supports many commonly used browsers. See the [browser support doc](https://github.com/OfficeDev/office-ui-fabric-react/blob/master/ghdocs/BROWSERSUPPORT.md) for more information.


## Contribute to Fabric React

We're excited to share our development of this project with folks outside of the company, but please keep in mind that we're moving towards a v1 state which requires that we stay focused on reaching that goal. With this in mind, take a look at our [contribution guidelines](https://github.com/OfficeDev/office-ui-fabric-react/blob/master/ghdocs/CONTRIBUTING.md) for more info on how we plan to look at issues, how to structure your commit messages, and more.
