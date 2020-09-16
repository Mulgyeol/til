# Logic

## Layouts with Flexbox in React Native
RN의 Flex 박스는 FlexDirection이 기본값으로 Column(세로) 방향이다.

> Column - 열 - 세로 - Verticla
> Row - 행 - 가로 - Horizontal

- 컨테이너 안에서 flex : 1이면 즉, RN에서는 default가 Column 이므로 세로로 1줄씩 내려온다.
- flexDirection을 Row로 바꾸면 텍스트를 추가로 입력했을 때 가로로 붙는다.

## how RN handle flex layout
- `<view>`는 `<div>`와 같은 기능을 한다고 보면 됨
- 부모 컨테이너는 `flex:1` : 모든 공간 사용가능하다는 의미
- pinkView와 skyblueView는 각자 원하는 만큼(flex) 상대적으로 공간 차지
- pinkView가 5/6 skyblueView가 1/6 차지 중
- 항상 flex로 layout을 코딩하는 것을 권장

```javascript
    import { StatusBar } from 'expo-status-bar';
    import React from 'react';
    import { StyleSheet, Text, View } from 'react-native';

    export default function App() {
    return (
        <View style={styles.container}>
            <View style={styles.skyblueView}>
                <Text style={styles.text}>Hello!!</Text>
            </View>
            <View style={styles.pinkView}>
                <Text style={styles.text}>Hello!!</Text>
            </View>
        </View>
    );
    }

    const styles = StyleSheet.create({
    container: {
        flex: 1,
    },

    pinkView: {
        flex:5,
        backgroundColor:'pink'
    },

    skyblueView:{
        flex: 1,
        backgroundColor : 'skyblue'
    },

    text: {
        color : "white"
    }
    });
```

## Loading Screen
1. Loading.js 생성
2. Loading.js
```javascript
    import React from "react";
    import { StyleSheet, Text, View } from 'react-native';


    export default function Loading(){
        return (
            <View style={styles.container}>
                <Text style={styles.text}>Getting the weather</Text>
            </View>
        );
    }

    const styles = StyleSheet.create({
        container: {
            flex: 1,
            justifyContent: "flex-end", //위치 값
            paddingHorizontal: 30, //사이드 여백
            paddingVertical: 100, //위아래 여백
            backgroundColor: "skyblue"
        },
        text: {
            color : "black",
            fontSize: 30,
        }

    });
```
3. App.js
```
import React from 'react';
import Loading from "./Loading";

export default function App() {
  return  <Loading />;
  
}
```

