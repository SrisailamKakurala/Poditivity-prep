# 🚀 **React Native Concepts - From Basics to Advanced**  

React Native is a **JavaScript framework** used for building **cross-platform mobile apps** (iOS & Android) using **React**.

---

## 📌 **1. Installation & Setup**
```sh
# Install Expo CLI
npm install -g expo-cli

# Create a new project
expo init MyApp
cd MyApp
npm start
```
For a **bare React Native project** (without Expo):
```sh
npx react-native init MyApp
cd MyApp
npx react-native start
npx react-native run-android  # For Android
npx react-native run-ios      # For iOS
```

---

## 🏗 **2. Project Structure**
```
MyApp/
│── src/                  # Source folder
│   │── components/       # Reusable components
│   │── screens/          # Screens
│   │── navigation/       # Navigation setup
│── App.js                # Entry point
│── package.json          # Dependencies
```

---

## 📲 **3. Core Components**
React Native provides built-in components like:
```jsx
import { View, Text, Button, TextInput, Image, ScrollView } from 'react-native';

const App = () => (
  <View>
    <Text>Hello, React Native!</Text>
    <TextInput placeholder="Enter text" />
    <Button title="Click me" onPress={() => alert('Clicked!')} />
    <Image source={{ uri: "https://example.com/image.png" }} style={{ width: 100, height: 100 }} />
  </View>
);
```

---

## 🎨 **4. Styling in React Native**
React Native uses **Flexbox** and a styling system similar to CSS.
```jsx
import { StyleSheet } from 'react-native';

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#f8f8f8',
  },
  text: {
    fontSize: 20,
    color: 'blue',
  },
});
```
Usage:
```jsx
<View style={styles.container}>
  <Text style={styles.text}>Hello, World!</Text>
</View>
```

---

## 🛤 **5. Navigation in React Native**
Using **React Navigation**:
```sh
npm install @react-navigation/native @react-navigation/stack react-native-screens react-native-safe-area-context react-native-gesture-handler react-native-reanimated
```
Example:
```jsx
import { createStackNavigator } from '@react-navigation/stack';
import { NavigationContainer } from '@react-navigation/native';
import HomeScreen from './screens/HomeScreen';

const Stack = createStackNavigator();

const App = () => (
  <NavigationContainer>
    <Stack.Navigator>
      <Stack.Screen name="Home" component={HomeScreen} />
    </Stack.Navigator>
  </NavigationContainer>
);
```

---

## ⚡ **6. State Management**
### **useState Hook**
```jsx
import { useState } from 'react';

const App = () => {
  const [count, setCount] = useState(0);

  return (
    <View>
      <Text>Count: {count}</Text>
      <Button title="Increase" onPress={() => setCount(count + 1)} />
    </View>
  );
};
```

### **useEffect Hook**
```jsx
import { useEffect } from 'react';

useEffect(() => {
  console.log("Component Mounted!");
}, []);
```

### **Context API**
```jsx
const ThemeContext = createContext();

const App = () => (
  <ThemeContext.Provider value={{ theme: "dark" }}>
    <HomeScreen />
  </ThemeContext.Provider>
);
```

---

## 📡 **7. Fetching API Data**
```jsx
import { useEffect, useState } from 'react';

const App = () => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/posts/1")
      .then(response => response.json())
      .then(json => setData(json));
  }, []);

  return <Text>{data?.title}</Text>;
};
```

---

## 🔥 **8. AsyncStorage (Local Storage)**
```sh
npm install @react-native-async-storage/async-storage
```
```jsx
import AsyncStorage from '@react-native-async-storage/async-storage';

const saveData = async () => {
  await AsyncStorage.setItem('username', 'Sri');
};

const getData = async () => {
  const value = await AsyncStorage.getItem('username');
  console.log(value);
};
```

---

## 📍 **9. Permissions & Camera**
```sh
npm install expo-camera
```
```jsx
import { Camera } from 'expo-camera';

const [hasPermission, setHasPermission] = useState(null);

useEffect(() => {
  (async () => {
    const { status } = await Camera.requestPermissionsAsync();
    setHasPermission(status === 'granted');
  })();
}, []);
```

---

## 🔗 **10. Push Notifications**
Using **Expo Notifications**:
```sh
npm install expo-notifications
```
Example:
```jsx
import * as Notifications from 'expo-notifications';

const scheduleNotification = async () => {
  await Notifications.scheduleNotificationAsync({
    content: {
      title: "Reminder!",
      body: "Don't forget your task!",
    },
    trigger: { seconds: 10 },
  });
};
```

---

## 🚀 **11. Deployment**
### Android:
```sh
expo build:android
```
### iOS:
```sh
expo build:ios
```

---

## 🔥 **12. Interview Questions**
- What is React Native?  
- How does React Native work?  
- What are the core components in React Native?  
- How does navigation work in React Native?  
- Explain React Native’s architecture.  
- How do you handle global state in React Native?  
- How do you optimize performance in React Native?  

---

🚀 **Master React Native & Build Cross-Platform Apps!**