# React Native CacheImage (remobile)
    A cache-image for react-native
* When use web image, this module will find the web image's url corresponding image file is exist or not, if exist, it will use local exist file, and check this CacheImage's old url and new url, if old url is the same as new url, do noting. if not, sub old url's ref and add new url's ref, if old url's ref is 0, delete old url corresponding image file.
* it also will check total storage, total storage is 1024*1024*50, when local file total size is above total storage, it will delete the oldest local file and clear corresponding record.

## Installation
```sh
npm install @remobile/react-native-cache-image --save
```
## Usage

### Example
```js
'use strict';

var React = require('react');
var ReactNative = require('react-native');
var {
    StyleSheet,
    View,
} = ReactNative;

var CacheImage = require('@remobile/react-native-cache-image');

var SERVER = 'http://192.168.1.117:3000/';

module.exports = React.createClass({
    render: function() {
        return (
            <View style={styles.container}>
                <CacheImage
                    resizeMode='stretch'
                    defaultSource={app.img.tabnav_list}
                    url={SERVER+"1.png"}
                    style={styles.image}
                    />
                <CacheImage
                    resizeMode='stretch'
                    defaultSource={app.img.tabnav_list}
                    url={SERVER+"2.png"}
                    style={styles.image}
                    />
                <CacheImage
                    resizeMode='stretch'
                    defaultSource={app.img.tabnav_list}
                    url={SERVER+"3.png"}
                    style={styles.image}
                    />
            </View>
        );
    }
});

var styles = StyleSheet.create({
    container: {
        flex: 1,
        justifyContent: 'center',
        alignItems: 'center',
        backgroundColor: '#F5FCFF',
    },
    image: {
        width:200,
        height:200,
    }
});
```

#### Props
This module supports react-native Image's props all.
- `defaultSource : PropTypes.string.isRequired` - local image for default image
- `url : PropTypes.string.isRequired` - the url of web image
    * format: 'http://{server}/{name}.png' or 'http://{server}/{name}.jpg'
    * must have jpg or png suffix
    * {name} must have version. e.g: first version is verison1.jpg, when you want to update image, you can use verison2.jpg, otherwise this module will not download image
