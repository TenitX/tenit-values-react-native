# tenit-values-react-native
React Native compatible library for interacting with the Tenit Values tool for continuous configuration

## Installation 
```bash
# Yarn
yarn add tenit-values-react-native

# NPM
npm install tenit-values-react-native
```

## Usage
As early in your app's lifecycle you'll want to initialize the library with the `init()` function. For most, this will be in the `App.js` file of your project.
```js
import * as Values from "tenit-values-react-native";


Values.init("yourApiKey", "yourCoordinateValue", ["LIST", "OF", "VALUES", "TO", "LOAD"]);

```

Once you've initalized the library in your app, at launch the library will attempt to fetch the specified values, and will store them in a global value so that
they are available throughout the lifecycle of your app. The values are also stored on the device using the [@react-native-async-storage/async-storage](https://github.com/react-native-async-storage/async-storage)
library. This is used as a way to support "offline" usage, and to improve reliabilty in the case of an outage on the tenit values side of things. This storage allows us to 
fallback to the last fetched values in the case that we can't access fresh values. 

At the moment the react native library supports 3 types, `String`, `Number` and `Boolean`, and they are all accessed in a similar fashion:
```js
import * as Values from "tenit-values-react-native";

// String
Values.getString("MY_VALUE", "fallback string");

//Number
Values.getNumber("MY_VALUE", 0);

//Boolean
Values.getBoolean("MY_VALUE", false);

```

## Tenit Values
Not yet using Tenit Values to power continous configuration in your apps? Check out https://values.tenitx.com
