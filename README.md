# [react-debounce-decorator](https://github.com/madou/react-debounce-decorator)

[![NPM version](http://img.shields.io/npm/v/react-debounce-decorator.svg?style=flat-square)](https://www.npmjs.com/package/react-debounce-decorator)
[![NPM downloads](http://img.shields.io/npm/dm/react-debounce-decorator.svg?style=flat-square)](https://www.npmjs.com/package/react-debounce-decorator)
[![Build Status](http://img.shields.io/travis/madou/react-debounce-decorator/master.svg?style=flat-square)](https://travis-ci.org/madou/react-debounce-decorator)
[![codecov](https://codecov.io/gh/madou/react-debounce-decorator/branch/master/graph/badge.svg)](https://codecov.io/gh/madou/react-debounce-decorator)
[![Dependency Status](http://img.shields.io/david/madou/react-debounce-decorator.svg?style=flat-square)](https://david-dm.org/madou/react-debounce-decorator)

Quick description of what it does!

<p align="center">
  <img src="https://github.com/madou/react-debounce-decorator/blob/master/example.gif?raw=true" style="margin:0 auto" />
</p>

## Installation

```sh
npm install react-debounce-decorator
```

## Usage

```javascript
// If using flow, grab the injected props type.

import type { InjectedProps } from 'react-debounce-decorator';
import debounceDecorator from 'react-debounce-decorator';

debounceDecorator(150)(
class TooltipTrigger extends Component {
  props: InjectedProps & {
    message: string,
  };

  show = (e) => {
    const { message, show, showTooltip } = this.props;

    // Call injected prop `show` when mouse enter. This will be called immedaitely.
    show(() => showTooltip(true, message));
  };

  hide = (e) => {
    const { hide, showTooltip } = this.props;

    // Call injected prop `hide` on mouse leave. This will be debounced.
    hide(() => showTooltip(false));
  };

  render () {
    return cloneElement(this.props.children, {
      onMouseEnter: this.show,
      onMouseLeave: this.hide,
    });
  }
})

```

## debounceDecorator(number): (Component) => Component


### React Story Book

To run the component in various modes, run the following command then go to `http://localhost:6006/`.

```bash
npm start
```

### Testing

```bash
npm test
```
