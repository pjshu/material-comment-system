# material-comment-system

> a comment system component based on material-ui

[![NPM](https://img.shields.io/npm/v/material-comment-system.svg)](https://www.npmjs.com/package/material-comment-system) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

## Install

```bash
npm install --save material-comment-system
```

## Usage

```jsx
import React, {useCallback} from 'react';
import {initData, newData} from "./mock";


import {Comments, Editor, Provider} from 'material-comment-system';
import 'material-comment-system/dist/index.css';

const App = () => {
  const initApi = useCallback(() => new Promise((resolve) => {
    setTimeout(() => {
      // mock fetch data
      resolve(initData);
    }, 500);
  }), []);

  const loadMoreAPi = useCallback(() => new Promise(resolve => {
    setTimeout(() => {
      resolve(newData);
    }, 500);
  }), []);

  const submitApi = useCallback((data) => {
    console.log('submit data', data);
    //post data
  }, []);

  return (
    <Provider>
      <div>
        <Editor submitApi={submitApi}/>
      </div>
      <div style={{marginTop: 20}}>
        <Comments initApi={initApi} loadMoreAPi={loadMoreAPi}/>
      </div>
    </Provider>
  );
};

export default App;
```


## License

MIT © [pjshu](https://github.com/pjshu)
