# AudioRecorder Plugin

Record MPEG4/AAC encoded audio from your hybrid app.

Audio is recorded at 44.1kHz with a bitrate of 32kbps, which is good enough for speech.

This plugin defines a global ( `navigator.device.audiorecorder` ) object which you can use to access the public API.


## Plugin

Although `audiorecorder` is globally acessible, it isn't usable until `deviceready` event is called.

As with all the cordova plugins, you can listen to `deviceready` event as follows: 

```javascript
document.addEventListener("deviceready", onDeviceReady, false);
function onDeviceReady() {
    // ...
}
```

## Supported Platforms

 - iOS
 - Android 


## Installation
- Run the following command:

```shell
    cordova plugin add cordova-plugin-audio-recorder
``` 
---

## API Reference

### AudioRecorder (`navigator.device.audiorecorder`)

 - [`.recordAudio(successCallback, errorCallback, durationLimit, viewColor, backgroundColor)`](#recordAudio)
 - [`.deleteAudioFile(successCallback, errorCallback, filepath)`](#deleteAudioFile)
 
---

<a name="recordAudio"></a>
#### Record Audio file

Calling this method opens the native GUI for the recorder.

| Param             | Type      | Description |
| ---               | ---       | --- |
| successCallback   | [`Function`](#successCallback)  | Callback function called when successfully recorded an audio file. |
| errorCallback     | [`Function`](#errorCallback)    | Callback function called when an error occurs |
| durationLimit     | Integer    | Duration, in seconds, of the recording. Recording stop when reaching the duration limit. |

<a name="deleteAudioFile"></a>
#### Delete Audio file

Deletes an audio file given its filepath

| Param             | Type      | Description   |
| ---               | ---       | ---           |
| successCallback   | Function  | Callback function called when the file is successfully deleted |
| errorCallback     | Function  | Callback function called when an error occurs while deleting the file |
| filepath          | String    | File path to the desired file. Usually the filepath returned by the successCallback from [`recordAudio`](#recordAudio) |

*Note*: On iOS, since we are saving the recordings into the temporary directory, all files will be deleted when the application is restarted. 

<a name="successCallback"></a>
#### Success Callback

Signature: 

```javascript
function(data){
    // ...
};
```

where `data` parameter is a JSON object:

```javascript
{
    "full_path":"",
    "file_name":""
}
```

<a name="errorCallback"></a>
#### Error Callback

Signature: 

```javascript
function(err){
    // ...
};
```

where `err` parameter is a JSON object:

```javascript
{
    "error_code":"",
    "error_message":""
}
```

Possible `error_code` values:

 - `OS_USER_CANCELLED` - Integer Value 1. User cancelled the recording session.
 - `OS_INTERNAL_ERROR` - Integer Value 2. An internal (native) error occurred.
 - `OS_INVALID_ARGS` - Integer Value 3. Invalid arguments were given.
 - `OS_PERMISSION_DENIED` - Integer Value 50.  _(iOS only.)_

---

#### How it looks


Recording screen <br />
![Imgur](http://i.imgur.com/EnMi0XDm.png =50x50)

Stop recording screen <br />
![Imgur](http://i.imgur.com/kzT2mugm.png=50x50)

Play recording screen <br />
![Imgur](http://i.imgur.com/s10ijTbm.png =50x50)


---

#### Contributors
- OutSystems - Mobility Experts
    - João Gonçalves, <joao.goncalves@outsystems.com>
    - Rúben Gonçalves, <ruben.goncalves@outsystems.com>
    - Vitor Oliveira, <vitor.oliveira@outsystems.com>
    - Danilo Costa, <danilo.costa@outsystems.com>

- Colin Anderson, [Github](https://github.com/cocowalla)

#### Document author
- João Gonçalves, <joao.goncalves@outsystems.com>

###Copyright OutSystems, 2016

---

LICENSE
=======


[The MIT License (MIT)](http://www.opensource.org/licenses/mit-license.html)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
