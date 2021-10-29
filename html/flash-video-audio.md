# Flash, Video, and Audio

# Flash
Flash was a very popular technology distributed by Adobe in the late 1990s that many websites used to add video/audio/animations. It had many security vulnerabilities though, and Adobe decided to drop support for it rather than attempt to fix them. Much of its functionality can be replicated with HTML5 though.

If a browser doesn't support HTML5, the only option for video playback is Flash, or doing something like embedding a Youtube link.

## Video (HTML5)
HTML5 introduces the `video` tag which can be used to add videos to websites.
```html
<!DOCTYPE html>
<html>
    <body>
        <!--
            The "src" attribute is a file path to the video file that will be
            displayed on the page.

            The "preload" attribute controls when the video loads. It can have
            one of three values.
                "none"
                    Don't load until user starts playback
                "auto"
                    Load when the page loads
                "metadata"
                    Browser should just collect metadata like size, first frame,
                    track list, duration, etc.

            The "poster" attribute indicates which image file should be
            displayed as the video's thumbnail before playback starts.

            The "width" and "height" attributes control the video player's width
            and height in pixels.

            The "controls" attribute indicates that the browser should supply
            its own controls for playback.

            The "autoplay" attribute indicates that the video should start
            playing automatically.

            The "loop" attribute indicates that the video should repeat playback
            once finished.
        -->
        <video src="file/path/video.mp4"
               preload="none"
               poster="file/path/thumbnail.jpg"
               width="400"
               height="300"
               controls
               autoplay
               loop>
        </video>
    </body>
</html>
```

The `video` tag displays with its own video player on the web page. Its look can be customized with Javascript.

Keep in mind that not all browsers support all video types. Internet Explorer and Safari only support H264 video, while Android, Chrome, Firefox, and Opera all support Webm.

Instead of the `src` attribute, the `source` tag can be used within a `video` element to indicate the video file. This is useful for specifying multiple formats of the same video file to ensure a compatible video format is available for the browser.
```html
<!DOCTYPE html>
<html>
    <body>
        <video preload="none" width="400" height="300" controls>
            <!--
                The "src" attribute specifies the path to the video file.

                The "type" attribute specifies the video format and codecs to
                the browser. Without it, the browser will download a portion of
                the video to detect the format, which will take time/bandwidth.
            -->
            <!--
                Due to a bug on the iPad, always specify the mp4 format first
                (if available) or else it won't be detected.
            -->
            <source src="videos/video.mp4"
                    type='video/mp4;codecs="avc1.42E01E, mp4a.40.2"' />
            <source src="videos/video.webm"
                    type='video/webm;codecs="vp8, vorbis"' />
        </video>
    </body>
</html>
```

## Audio (HTML5)
HTML5 introduced the `audio` tag, which can be used to embed an audio player into a web page.
```html
<!DOCTYPE>
<html>
    <body>
        <!--
            The attributes here have the same behavior as in the "video"
            element.
        -->
        <audio src="audio.mp3" preload="none" controls autoplay loop />
    </body>
</html>
```

To specify multiple source audio formats, the `source` element can be used within the `audio` element instead of the `src` attribute. This is useful for making sure a compatible audio format is always available no matter the browser.
```html
<!DOCTYPE>
<html>
    <body>
        <audio preload="none" controls autoplay loop>
            <!--
                The "type" attribute is not commonly used here like it is under
                the "video" element.
            -->
            <source src="audio.ogg" />
            <source src="audio.mp3" />
        <audio>
    </body>
</html>
```

Safari 5+, Chrome 6+, and Internet Explorer 9 all support the MP3 format.

Firefox 3.6, Chrome 6, and Opera 1.5 all support the Ogg Vorbis format.
