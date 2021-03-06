# Image Picker plugin for Flutter

[![pub package](https://img.shields.io/pub/v/image_picker.svg)](https://pub.dartlang.org/packages/image_picker)

A Flutter wrapper for the native image picker.

This enables picking images from the image library, or to take new pictures with the camera.

*Note*: This plugin is still under development, and some APIs might not be available yet. [Feedback welcome](https://github.com/flutter/flutter/issues) and [Pull Requests](https://github.com/flutter/plugins/pulls) are most welcome!

## Usage
To use this plugin, add `image_picker` as a [dependency in your pubspec.yaml file](https://flutter.io/platform-plugins/).

Next, to make the app build for android, open the file `android/build.gradle`, and add the `jitpack.io` line shown below:

```
allprojects {
   repositories {
       jcenter()
       maven { url "https://jitpack.io" }    // Enable getting dependencies from jitpack.io.
   }
}
```

### Example

``` dart
class _MyHomePageState extends State<MyHomePage> {
  File imageFile;

  getImage() async {
    var _fileName = await ImagePicker.pickImage();
    setState(() {
      imageFile = _fileName;
    });
  }

  @override
  Widget build(BuildContext context) {
    return new Scaffold(
      appBar: new AppBar(
        title: new Text('Image Picker Example'),
      ),
      body: new Center(
        child: imageFile == null
            ? new Text('No image selected.')
            : new Image.file(imageFile),
      ),
      floatingActionButton: new FloatingActionButton(
        onPressed: getImage,
        tooltip: 'Pick Image',
        child: new Icon(Icons.add_a_photo),
      ),
    );
  }
}
```
