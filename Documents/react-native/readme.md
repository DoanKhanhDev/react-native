# React Native Basic

- [React Native Basic](#react-native-basic)
  - [1. Create develop environment.](#1-create-develop-environment)
  - [2. Core component](#2-core-component)
    - [2.1 View](#21-view)
      - [2.1.1 SafeAreaView](#211-safeareaview)
      - [2.1.2 KeyboardAvoidingView](#212-keyboardavoidingview)
  - [2.2 Listings](#22-listings)
    - [2.3.1 ScrollView](#231-scrollview)
    - [2.3 Refresh Control](#23-refresh-control)
  - [2.4 Text Component](#24-text-component)
  - [2.5 Text Input](#25-text-input)
  - [2.6 Button](#26-button)
  - [2.7 Image](#27-image)
  - [2.8 ImageBackground](#28-imagebackground)
  - [2.9 Switch](#29-switch)
  - [2.10 StatusBar](#210-statusbar)
    - [2.11 Activity Indicator](#211-activity-indicator)
    - [2.12 Modal](#212-modal)
    - [2.13 Pressable](#213-pressable)


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
### 2.3 Refresh Control

- `RefreshControl` is a component in React Native that is used to provide pull-to-refresh functionality for scrollable components like `ScrollView`, `ListView`, and `FlatList`.

  For example:

  ```typescript
  import React, { useState } from 'react';
  import { FlatList, RefreshControl, Text } from 'react-native';

  const App = () => {
      const [refreshing, setRefreshing] = useState(false);

      const fetchData = () => {
          // Fetch the data and update your state accordingly
      };

      const onRefresh = () => {
          setRefreshing(true);
          fetchData().then(() => {
              setRefreshing(false);
          });
      };

      return (
          <FlatList
              data={['Item 1', 'Item 2', 'Item 3']}
              renderItem={({ item }) => <Text>{item}</Text>}
              refreshControl={
                  <RefreshControl refreshing={refreshing} onRefresh={onRefresh} />
              }
          />
      );
  };

  export default App;
  ```


## 2.4 Text Component

- The Text component is a basic element in React Native used to display text content on the screen. While it has some basic styling properties, you usually nest it inside other components (e.g., View) to create more complex UIs.


  For example:

  ```typescript
  import React from 'react';
  import { Text, StyleSheet } from 'react-native';

  const App = () => {
    return (
      <Text style={styles.text} numberOfLines={2} onPress={() => alert('Hello')}>
        This is an example of a Text component in React Native. Tap on me!
      </Text>
    );
  };

  const styles = StyleSheet.create({
    text: {
      fontSize: 16,
      color: 'blue',
      textAlign: 'center',
      margin: 10,
      fontFamily: 'Arial',
    },
  });

  export default App;
  ```

## 2.5 Text Input

- `TextInput` is a core component in React Native that allows the user to enter text. It is commonly used to collect user data, like emails or passwords. You can customize the appearance of TextInput by using various props such as placeholder, multiline, maxLength, and more.

  For example:

  ```typescript
  import React, { useState } from 'react';
  import { TextInput, View, Button } from 'react-native';

  const App = () => {
    const [text, setText] = useState('');

    const handleSubmit = () => {
      alert('You entered: ' + text);
    };

    return (
      <View>
        <TextInput
          style={{ height: 40, borderColor: 'gray', borderWidth: 1 }}
          onChangeText={text => setText(text)}
          value={text}
          placeholder="Enter text here"
        />
        <Button
          onPress={handleSubmit}
          title="Submit"
        />
      </View>
    );
  };
  ```

## 2.6 Button

- A `Button` is a built-in React Native component used to create clickable buttons. It is a simple, customizable and easy-to-use component that captures touches and triggers an onPress event when pressed.

  For example:

  ```typescript
  import React from 'react';
  import { Button } from 'react-native';

  const MyButton = () => {
    const onPressHandler = () => {
      alert('Button Pressed');
    };

    return (
      <Button
        title="Click me"
        color="#841584"
        onPress={onPressHandler}
      />
    );
  };

  export default MyButton;
  ```
## 2.7 Image

- The `Image` component is used to display images in a React Native application. It allows you to load and display local as well as remote images, providing essential props and methods for better image handling and customization.

- To display a local image in the application,you have to require it in the `source` props of the `image` component. Place the image file in your project directory and use the following syntax:

  ```typescript
  <Image source={require('./path/to/your/image.png')} />
  ```

- To display a remote image from a URL, you need to sett the source props with a `uri` object:

  ```typescript
  <Image source={{ uri: 'https://path/to/your/remote/image.png' }} />
  ```
- Keep in mind that you need to define the dimensions(`width` and `height`) when using remote images:

  ```typescript
  <Image source={{ uri: 'https://path/to/your/remote/image.png' }} style={{ width: 200, height: 200 }} />
  ```

- You can set image scaling and positioning with `resizeMode` props.

  ```typescript
  <Image source={require('./path/to/your/image.png')} resizeMode="contain" />
  ```

## 2.8 ImageBackground

- `ImageBackground` is a React Native core component the allows you to display as image a background while still being able to  place content inside the component. This helps in creating beautiful layouts with image and text or other content on top.

  For example:

  ```typescript
  import React from 'react';
  import { View, Text, ImageBackground, StyleSheet } from 'react-native';

  const App = () => (
    <ImageBackground
      source={{ uri: 'https://some-image-url.com/background.jpg' }}
      style={styles.background}
      resizeMode="cover"
    >
      <Text style={styles.text}>Hello, World!</Text>
    </ImageBackground>
  );

  const styles = StyleSheet.create({
    background: {
      flex: 1,
      justifyContent: 'center',
    },
    text: {
      color: 'white',
      fontSize: 42,
      lineHeight: 84,
      fontWeight: 'bold',
      textAlign: 'center',
    },
  });

  export default App;
  ```

## 2.9 Switch

- A `Switch` is a core component in React Native used to implement a “toggle” or “on-off” input. It provides a UI for the user to switch between two different states, typically true or false. The primary use case is to enable or disable a feature or setting within an application.

  For example:

  ```typescript
  import React, {useState} from 'react';
  import {View, Switch, Text} from 'react-native';

  const App = () => {
    const [isEnabled, setIsEnabled] = useState(false);

    const toggleSwitch = () => setIsEnabled(previousState => !previousState);

    return (
      <View>
        <Text>Enable Feature:</Text>
        <Switch
      trackColor={{ false: "#767577", true: "#81b0ff" }}
      thumbColor={isEnabled ? "#f5dd4b" : "#f4f3f4"}
        onValueChange={toggleSwitch}
        value={isEnabled}
        />
      </View>
    );
  };

  export default App;
  ```

## 2.10 StatusBar

- The `StatusBar` component is used to control the appearance of the status bar on the top of the screen. It may strike as a bit unusual since, unlike other React Native components, it doesn’t render any visible content. Instead, it sets some native properties that can help customize the look of status bars on Android, iOS, or other platforms.

  For example:

  ```typescript
  import React from 'react';
  import { View, StatusBar } from 'react-native';

  const App = () => {
    return (
      <View>
        <StatusBar barStyle="dark-content" backgroundColor="#F0F0F0" />
        {/* Your other components */}
      </View>
    );
  };

  export default App;
  ```
### 2.11 Activity Indicator

- The `ActivityIndicator` is a core component in React Native that provides a simple visual indication of some ongoing activity or loading state within your application. It shows a spinning animation, which gives the user feedback that something is happening in the background. This component is particularly useful when fetching data from an external source, like a server, or while performing time-consuming operations.

  For example:

  ```typescript
  import React from 'react';
  import { ActivityIndicator, View, Text } from 'react-native';

  const LoadingScreen = () => (
    <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
      <Text>Loading, please wait...</Text>
      <ActivityIndicator size="large" color="#0000ff" />
    </View>
  );

  export default LoadingScreen;
  ```

### 2.12 Modal

- A `Modal` is a component that displays content on top of the current view, creating an overlay that can be used for various purposes, such as displaying additional information, confirmation messages, or a selection menu.

  For example:

  ```typescript
  import React, {useState} from 'react';
  import {Modal, Text, TouchableHighlight, View, Alert} from 'react-native';

  const App = () => {
    const [modalVisible, setModalVisible] = useState(false);

    return (
      <View>
        <Modal
          animationType="slide"
          transparent={true}
          visible={modalVisible}
          onRequestClose={() => {
            Alert.alert('Modal has been closed.');
            setModalVisible(!modalVisible);
          }}>
          <View>
            <View>
              <Text>Hello, I am a Modal!</Text>

              <TouchableHighlight
                onPress={() => {
                  setModalVisible(!modalVisible);
                }}>
                <Text>Hide Modal</Text>
              </TouchableHighlight>
            </View>
          </View>
        </Modal>

        <TouchableHighlight
          onPress={() => {
            setModalVisible(true);
          }}>
          <Text>Show Modal</Text>
        </TouchableHighlight>
      </View>
    );
  };

  export default App;
  ```

### 2.13 Pressable

- `Pressable` is a core component in React Native that makes any view respond properly to touch or press events. It provides a wide range of event handlers for managing user interactions, such as onPress, onPressIn, onPressOut, and onLongPress. With Pressable, you can create custom buttons, cards, or any touchable elements within your app.

  For example:

  ```typescript
  import React from 'react';
  import { Pressable, Text, StyleSheet } from 'react-native';

  export default function CustomButton() {
    return (
      <Pressable
        onPress={() => console.log('Pressed!')}
        style={({ pressed }) => [
          styles.button,
          pressed ? styles.pressedButton : styles.normalButton,
        ]}
      >
        <Text style={styles.buttonText}>Press me</Text>
      </Pressable>
    );
  }

  const styles = StyleSheet.create({
    button: {
      padding: 10,
      borderRadius: 5,
    },
    normalButton: {
      backgroundColor: 'blue',
    },
    pressedButton: {
      backgroundColor: 'darkblue',
    },
    buttonText: {
      color: 'white',
      textAlign: 'center',
    },
  });
  ```

