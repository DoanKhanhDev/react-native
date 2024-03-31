# React Native Basic

## 1. Create develop environment.

- Build app run command(Should add argument --template to create app with TS or JS):

```
npx create-expo-app my-app —template
```

- To start app, run command:

```
npx expo start
```

**Note:** Please cache clear simulator before build or rebuild app.

**Result:**

![result setup](</Documents/images/result_setup.png>)

## 2. Core component

### 2.1 View

- The `View` component in React Native is a fundamental container component that supports various layout styles. It is the equivalent of a div element in HTML and can be used to create and style containers for various elements. It is a versatile component that can handle various user interactions, including touch events, as well as serving as a decorative and functional piece in your mobile application.

  For example:

  ```typescript
  import React from 'react';
  import { StyleSheet, View, Text } from 'react-native';

  function App() {
    return (
      <View style={styles.container}>
        <Text>Hello, World!</Text>
      </View>
    );
  }

  const styles = StyleSheet.create({
    container: {
      flex: 1,
      backgroundColor: '#fff',
      alignItems: 'center',
      justifyContent: 'center',
    },
  });

  export default App;
  ```

#### 2.1.1 SafeAreaView

- `SafeAreaView` is a React Native core component that helps to adjust your app’s UI elements and layout to accommodate the notches, curved edges, or home indicator on iOS devices. It is particularly useful for the iPhone X and newer iPhone models, as it ensures that content is rendered within the visible portion of the screen.

  **For Example:**

  ```typescript
  import { SafeAreaView, StyleSheet, Text, View } from 'react-native';

  export default function App() {
    return (
      // <View style={styles.container}>
      //   <Text >Open up App.tsx to start working on your app!</Text>
      //   <StatusBar style="auto" />
      // </View>
      <SafeAreaView style={styles.container}>
        <Text>Hello World!</Text>
      </SafeAreaView>

    );
  }

  const styles = StyleSheet.create({
    container: {
      // flex: 1,
      // backgroundColor: '#fff',
      // alignItems: 'center',
      // justifyContent: 'center',
    },
  });
  ```

#### 2.1.2 KeyboardAvoidingView

- `KeyboardAvoidingView` is a built-in React Native component that automatically adjusts its children components’ position when the keyboard opens, preventing them from being obscured by the on-screen keyboard. It’s a useful component, particularly for forms and input fields where the user needs to see the text they’re typing.

- To use the `KeyboardAvoidingView`, simply wrap the desired components that need to avoid the keyboard with the `KeyboardAvoidingView` component. The prop behavior is used to specify the type of animating behavior the component will use. This behavior differs depending on the platform and can be one of ‘height’, ‘position’, ‘padding’, or a custom defined behavior.

  For example:

  ```typescript
  import React from 'react';
  import { View, TextInput, StyleSheet, KeyboardAvoidingView } from 'react-native';

  const App = () => {
    return (
      <KeyboardAvoidingView
        style={styles.container}
        behavior="padding" // Additional padding when the keyboard is open.
      >
        <TextInput
          placeholder="Type something here"
          style={styles.textInput}
        />
      </KeyboardAvoidingView>
    );
  }

  const styles = StyleSheet.create({
    container: {
      flex: 1,
      justifyContent: 'center',
    },
    textInput: {
      borderWidth: 1,
      borderColor: 'black',
      padding: 10,
      margin: 20,
    },
  });

  export default App;
  ```
## 2.2 Listings

### 2.3.1 ScrollView

- In React Native, the ScrollView is a generic scrolling container used to provide a scrollable view to its child components. It is useful when you need to display scrollable content larger than the screen, such as lists, images, or text. A ScrollView must have a bounded height in order to properly work.

  For example:

  ```typescript
  import React from "react";
  import { ScrollView, Text, SafeAreaView } from "react-native";

  const App = () => {
    return (
      <SafeAreaView>
        <ScrollView>
          <Text>Item 1</Text>
          <Text>Item 2</Text>
          <Text>Item 3</Text>
          <Text>Item 4</Text>
          <Text>Item 5</Text>
          <Text>Item 6</Text>
        </ScrollView>
      </SafeAreaView>
    );
  };

  export default App;
  ```
