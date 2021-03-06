# react-native-create-thumbnail

iOS/Android thumbnail generator with support for both local and remote videos. `react-native-create-thumbnail` is a wrapper around
[`AVAssetImageGenerator`](https://developer.apple.com/documentation/avfoundation/avassetimagegenerator?language=objc) (iOS) and [`MediaMetadataRetriever`](https://developer.android.com/reference/android/media/MediaMetadataRetriever) (Android)

[![npm](https://img.shields.io/npm/v/react-native-create-thumbnail.svg)](https://npmjs.com/package/react-native-create-thumbnail) [![npm](https://img.shields.io/npm/dm/react-native-create-thumbnail.svg)](https://npmjs.com/package/react-native-create-thumbnail) [![License](https://img.shields.io/npm/l/react-native-create-thumbnail.svg)](https://www.npmjs.com/package/react-native-create-thumbnail)

## Getting started

1. Install library from `npm`

   ```bash
   yarn add react-native-create-thumbnail
   ```

   or

   ```bash
   npm i react-native-create-thumbnail
   ```

2. Link native code

   With autolinking (react-native 0.60+)

   ```bash
   cd ios && pod install
   ```

   Pre 0.60

   ```bash
   react-native link react-native-create-thumbnail
   ```

## Usage

```javascript
import { createThumbnail } from "react-native-create-thumbnail";

createThumbnail({
  url: "<path to video file>",
  type: "local"
  timeStamp: 5
})
  .then(response => {
    console.log({ response });
    this.setState({
      status: "Thumbnail received",
      thumbnail: response.path
    });
  })
  .catch(err => console.log({ err }));
```

## Request Object

| Property  |            Type             | Description                                        |
| --------- | :-------------------------: | :------------------------------------------------- |
| url       |     `String` (required)     | Path to video file (local or remote)               |
| timeStamp |   `Number` (default `1`)    | Thumbnail timestamp (in seconds)                   |
| type      | `String` (default `remote`) | Resource type, can be one of: `remote`, or `local` |
| format    |  `String` (default `jpeg`)  | Thumbnail format, can be one of: `jpeg`, or `png`  |

## Response Object

| Property |   Type   | Description                 |
| -------- | :------: | :-------------------------- |
| path     | `String` | Path to generated thumbnail |
| width    | `Number` | Thumbnail width             |
| height   | `Number` | Thumbnail height            |

#### Notes

Requires following Permissions on android

```bash
READ_EXTERNAL_STORAGE, WRITE_EXTERNAL_STORAGE
```

#### Limitations

Remote videos aren't supported on android sdk_version < 14

#### Credits

- [`react-native-thumbnail`](https://www.npmjs.com/package/react-native-thumbnail) - A great source of inspiration
- This project was bootstrapped with [`create-react-native-module`](https://github.com/brodybits/create-react-native-module)

#### Maintenance Status

**Active:** Bug reports, feature requests and pull requests are welcome.
