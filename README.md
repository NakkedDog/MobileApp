# News Application React-Native

## Contents


- [Description](#description)
- [Requirements](#requirements)
- [API](#api)


## Description

For this project, we intended to create a news application that tells a news story with its database. A news app that has various categories can help each reader decide and understand what is going on in our country. 


## Requirements

We used React Navigation to create various different screens for our application

```js
npm install @react-navigation/native

expo install react-native-screens react-native-safe-area-context
```

Then to install the Bottom Tabs part of our application

```js
npm install @react-navigation/bottom-tabs
```

in our App.js file, we need to import Bottom Tabs in order to use it.

```js
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
```

For the icons, we installed an icon library which requires react-native-elements.

```js
npm install react-native-elements
```
To make it look nicer, we imported Stylesheet from React Native

```js
import { View, Text, StyleSheet } from 'react-native';
```

We also imported moment.js package fot the date format to make it readable and easier to interpret

```js
npm install moment --save
```

Then, import it in our All.js screen

```js
<Text style={styles.date}>
  {moment(item.publishedAt).format('LLL')}
</Text>
```



## API

We called the News API form from https://newsapi.org/. So we were fetching the news data by using our endpoint, and appending the category. We passed the category as general because that would be our default category. We also pass the API_key in the header.

Then, we convert the response, or incoming data, into JSON format and storing it in a result variable.

And lastly, we are returning it using the return keyword.

```js
import { API_KEY, endpoint, country } from '../config/config';

export async function services(category = 'general') {
    let articles = await fetch(`${endpoint}?country=${country}&category=${category}`, {
        headers: {
            'X-API-KEY': API_KEY
        }
    });

    let result = await articles.json();
    articles = null;

    return result.articles;
}
```
and import this service into our All.js file

```js
import { services } from '../services/services';
```



