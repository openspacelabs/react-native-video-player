# React Native Video Player

A React Native video player with a few controls. This player uses
react-native-video for the video playback.

This project is a fork of
[the original react-native-video-player](https://github.com/cornedor/react-native-video-player)
mainly to remove its dependency on `react-native-vector-icons`. Here instead of getting out-of-the-box icons,
users must supply the component with `iconRenderers` to render the icons.

![demo gif](https://raw.githubusercontent.com/cornedor/react-native-video-player/master/demo.gif 'Demo GIF')

## Installation

In your `package.json`

```
"react-native-video-player": "git+ssh://git@github.com:openspacelabs/react-native-video-player.git#{some commit hash}",
```

## Example

```jsx
<VideoPlayer
  video={{
    uri: 'http://commondatastorage.googleapis.com/gtv-videos-bucket/sample/BigBuckBunny.mp4',
  }}
  videoWidth={1600}
  videoHeight={900}
  thumbnail={{ uri: 'https://i.picsum.photos/id/866/1600/900.jpg' }}
  iconRenderers={{
    play: () => <Text>▶️</Text>,
    pause: () => <Text>⏸</Text>,
    audioOff: () => <Text>[audio off icon]</Text>,
    audioOn: () => <Text>[audio on icon]</Text>,
    start: () => <Text>▶️</Text>,
  }}
/>
```

## Props

| Prop                    | Description                                                                                                                                  |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| video                   | The video source to pass to react-native-video.                                                                                              |
| thumbnail               | An Image source to use as thumbnail before the video gets loaded.                                                                            |
| endThumbnail            | An Image source to use as thumbnail after the video has ended.                                                                               |
| videoWidth              | Width of the video to calculate the player size.                                                                                             |
| videoHeight             | Height of the video to calculate the player size.                                                                                            |
| duration                | Duration can not always be figured out (e.g. when using hls), this can be used as fallback.                                                  |
| showDuration            | Show duration in seek bar.                                                                                                                   |
| autoplay                | Start the video automatically.                                                                                                               |
| defaultMuted            | Start the video muted, but allow toggling.                                                                                                   |
| muted                   | Start the video muted and hide the mute toggle button.                                                                                       |
| controlsTimeout         | Timeout when to hide the controls.                                                                                                           |
| disableControlsAutoHide | Disable auto hiding the controls.                                                                                                            |
| disableFullscreen       | Disable the fullscreen button.                                                                                                               |
| loop                    | Loop the video after playback is done.                                                                                                       |
| resizeMode              | The video's resizeMode. defaults to contain and is passed to react-native-video.                                                             |
| hideControlsOnStart     | Hides the controls on start video.                                                                                                           |
| endWithThumbnail        | Returns to the thumbnail after the video ends. If an `endThumbnail` image is not specified then the image specified in `thumbnail` is shown. |
| disableSeek             | Disable video seeking.                                                                                                                       |
| pauseOnPress            | Automatically pause/play when pressing the video player anywhere.                                                                            |
| fullScreenOnLongPress   | Automatically show video on fullscreen when doing a long press.                                                                              |
| onStart                 | Callback for when the start button is pressed.                                                                                               |
| onPlayPress             | Callback for when the play button is pressed.                                                                                                |
| onHideControls          | Callback for when the controls are being hide.                                                                                               |
| onShowControls          | Callback for when the controls are being shown.                                                                                              |
| customStyles            | The player can be customized in this object, see customStyles for the options.                                                               |
| iconRenderers           | Supply custom icons for the controls.                                                                                                        |

All other props are passed to the react-native-video component.

### iconRenderers

- play
- pause
- audioOn
- audioOff
- fullscreen
- start

### customStyles

- wrapper
- video
- controls
- controlButton
- seekBar
- seekBarFullWidth
- seekBarProgress
- seekBarKnob
- seekBarBackground
- thumbnail
- playButton
- videoWrapper

## Methods

| Method | Props       | Description                               |
| ------ | ----------- | ----------------------------------------- |
| seek   | time: float | Seek the player to the given time.        |
| stop   |             | Stop the playback and reset back to 0:00. |
| pause  |             | Pause the playback.                       |
| resume |             | Resume the playback.                      |

## Future features

- [x] Make seek bar seekable.
- [x] Make player customizable.
- [ ] Add volume control
- [x] Add fullscreen button
  - [ ] Add fullscreen button for Android (See PR #38 if you need fullscreen in Android)
- [ ] Add loader
- [ ] Add video duration/play time
