Experimental HTML Guidelines
============================

Tables
------
> * <mark>Simple tables can have two levels of headers. Each header cell should have `scope="col"` or `scope="row"`.</mark>
> * Complex tables are tables with more than two levels of headers. Each header should be given a unique id and each data cell should have a headers attribute with each related header cell’s id listed.

- [18F on tables][]

Buttons
-------
`<a href="#" role="button">Submit</a>`

vs

`<button role="button">Submit</button>`

vs

`<input type="submit" value="Submit" role="button" />`

Button and input elements are interchangeable, but anchor tags are a different matter, writes [MDN][]:

> Warning: Be careful when marking up links with the button role. Buttons are expected to be triggered using the Space key, while links are expected to be triggered through the Enter key. In other words, when links are used to behave like buttons, adding role="button" alone is not sufficient. It will also be necessary to add a key event handler that listens for the Space key in order to be consistent with native buttons.

Use input elements by defaults and use buttons for a separate purpose or behaviour.

* ["When To Use The Button Element"][csstricks-buttons]
* ["The Difference Between Anchors, Inputs and Buttons"][davidwalsh-buttons]

Video and GIF
-------------

Here is a GIF:

```html
<img alt="Example animation" src="example.gif" />
```

Here is what this would look like with videos that improve load performance vastly:

```html
<figure>
    <video loop controls>
        <source type="video/mp4"
                src="example.mp4" />
        <source type="video/webm"
                src="example.webm" />
        <source type="video/ogg"
                src="example.ogv" />
        <img alt="Example animation" src="example.gif" />
        <figcaption>Example animation.</figcaption>
    </video>
</figure>
```

Failing that, here’s an image-based alternative:

```html
<figure>
    <a href="example.gif"><img alt="Example animation" src="example.png" /></a>
    <figcaption>Example animation.</figcaption>
</figure>
```

### Converting a GIF to Video ###

#### Set-up ####

Install ffmpeg with Homebrew:

```sh
brew install ffmpeg --with-libvpx --with-theora --with-libogg --with-libvorbis
```

If you have ffmpeg, but haven’t installed the additional codecs, use `brew reinstall` instead.

#### GIF to WebM ####

```sh
ffmpeg -i example.gif -c:v libvpx -crf 12 -b:v 500K example.webm
```

Let’s break that down, shall we?

* `-i example.gif`: Input file
* `-c:v libvpx`: Decoder name
* `-crf 12`: Exponential range of quantizer scale from `0–51`
    - `0` is lossless, and `51` is, well, lossy
    - `18` is considered “visually lossless”

    As you can probably infer, you want to use as high a scale as possible with an acceptable quality.

    > You can use `-qp 0` or `-crf 0` to encode a lossless output. Use of `-qp` is recommended over `-crf` for lossless because 8-bit and 10-bit x264 use different `-crf` values for lossless.
* `-b:v 500K`: Average bit rate (kB/s)
* `example.webm`: Output file

~ [ffmpeg guide][]

So if you wanted a lossless conversion instead of a good-enough conversion, do

```sh
ffmpeg -i example.gif -c:v libvpx -qp 0 example.webm
```


#### WebM to MP4 ####

```sh
ffmpeg -i example.webm example.mp4 # -c:v libx264
# Use -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" if you get a size error
# cf. stackoverflow.com/a/20848224
```

#### WebM to OGG ####

```sh
ffmpeg -i example.webm example.ogv
```

You can also use [Miro Converter][] to convert the WebM file to MP4 and OGG.


[18F on tables]: https://playbook.cio.gov/designstandards/tables/
[mdn]: https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_button_role
[csstricks-buttons]: https://css-tricks.com/use-button-element
[davidwalsh-buttons]: http://davidwalsh.name/html5-buttons
[ffmpeg guide]: https://trac.ffmpeg.org/wiki/Encode/H.264
[Miro Converter]: http://www.mirovideoconverter.com
