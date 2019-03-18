# case-study-xhyzzZ
Today, I am going to do case study on one of the most popular technology used in today -- React Native.  
## Introduction to React Native
First, let me introduce what react native is. React Native is a framework for building native apps with React and Javascript. It means that you can build your native mobile app using purely JSX syntax without using mobile programming language like Swift, Objective-C in iOS and Java in Android. This technology is historical because it makes JS programmer easily step into mobile area without learning other languages. The learning curve is smooth, you don’t need to learn all knowledge in a short time. Everything is learning by progress.  
I will using the same language if the project is starting today. I will compare React Native to prove what i am thinking. I will mainly talk two important areas.  

**React Native vs Apache Cordova**
- Performance: Apps developed using React Native are faster than Cordova apps
- Extensions and Community: React Native is much better than Cordova because it has more contributors and is developed by Facebook, 
- When to use: Use React Native when you want to develop cross-platform apps with a more native feel and faster performance.  

Cordova is best suited when you want to quickly convert your web application into a cross-platform but it comes with a cost of less native feel and slow performance.
In a nutshell, even if Cordova is easier to write, but I will choose React Native to build my project because in the two main areas, React Native is better.  

**React Native vs Flutter**
- Performance: There is no big difference between React Native and Flutter.
- Extensions and Community: same as area 1  

In a nutshell, in view of almost same as two areas , when compared this two languages, Flutter is based on Dart, which is quite new to the developers, but javascript is common to almost every developer, so React native is better than Flutter in my opinion.  

**React Native vs NativeScript**
- Performance: React Native provides the user experience that is as close to native as ever possible, and React Native applications show top performance. Rendering slows down a NativeScript application.
- Extensions and Community: React Native more than 1600 contributors; NativeScript 109 contributors at the moment.

In a nutshell, I would prefer using React Native rather than NativeScript.
React native just use Android SDK to build Android project and Xcode to build iOS project. There is no build system or something else.  

React Native is some kind of the fastest in its category of mobile app, because it is based on React properties, which is the most popular web framework developed by Facebook, it use native components instead of web components as building blocks which make it faster.  

## Unit test and test framework in React Native
In React Native, we use Jest to do unit test for our project and Jest is the main test framework. Jest is a delightful JavaScript Testing Framework with a focus on simplicity. Below is the example of jest and how to use jest in React Native to test the code in order to make sure that the testing is meaningful.  
### Set up:  
Starting from react-native version 0.38, a Jest setup is included by default when running `react-native init`. The following configuration should be automatically added to your package.json file:
```javascript
// package.json
  "scripts": {
    "test": "jest"
  },
  "jest": {
    "preset": "react-native"
  }
```
Note: If you are upgrading your react-native application and previously used the `jest-react-native` preset, remove the dependency from your `package.json` file and change the preset to `react-native` instead.

Simply run `yarn test` to run tests with Jest.
### Snapshot Test
```javascript
// Intro.js
import React, {Component} from 'react';
import {StyleSheet, Text, View} from 'react-native';

const styles = StyleSheet.create({
  container: {
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
    flex: 1,
    justifyContent: 'center',
  },
  instructions: {
    color: '#333333',
    marginBottom: 5,
    textAlign: 'center',
  },
  welcome: {
    fontSize: 20,
    margin: 10,
    textAlign: 'center',
  },
});

export default class Intro extends Component {
  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.welcome}>Welcome to React Native!</Text>
        <Text style={styles.instructions}>
          This is a React Native snapshot test.
        </Text>
      </View>
    );
  }
}
```
Now let's use React's test renderer and Jest's snapshot feature to interact with the component and capture the rendered output and create a snapshot file:  
```javascript
// __tests__/Intro-test.js
import React from 'react';
import Intro from '../Intro';

import renderer from 'react-test-renderer';

test('renders correctly', () => {
  const tree = renderer.create(<Intro />).toJSON();
  expect(tree).toMatchSnapshot();
});
```
When you run `yarn test` or `jest`, this will produce an output file like this:
```javascript
// __tests__/__snapshots__/Intro-test.js.snap
exports[`Intro renders correctly 1`] = `
<View
  style={
    Object {
      "alignItems": "center",
      "backgroundColor": "#F5FCFF",
      "flex": 1,
      "justifyContent": "center",
    }
  }>
  <Text
    style={
      Object {
        "fontSize": 20,
        "margin": 10,
        "textAlign": "center",
      }
    }>
    Welcome to React Native!
  </Text>
  <Text
    style={
      Object {
        "color": "#333333",
        "marginBottom": 5,
        "textAlign": "center",
      }
    }>
    This is a React Native snapshot test.
  </Text>
</View>
`;
```
The next time you run the tests, the rendered output will be compared to the previously created snapshot. The snapshot should be committed along code changes. When a snapshot test fails, you need to inspect whether it is an intended or unintended change. If the change is expected you can invoke Jest with `jest -u` to overwrite the existing snapshot.  
### CI 
When we use React Native, in some way, it’s hard for us to do some CI in project, but right now we have two platforms that we can do CI for React Native.  

**Visual Studio App Center**: 
App Center is a platform that allows you to continuously build, test, release, and monitor apps. It supports GitHub, Bitbucket, and Visual Studio Team Services. That means you can connect your code repo to any of these services. So every time you push some changes to a specific branch, it will automatically build your app.
