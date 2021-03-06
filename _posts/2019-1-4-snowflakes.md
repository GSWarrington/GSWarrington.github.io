---
layout: post
title: "First macro snowflake pictures"
category: macrophotography
tags: [snowflakes]
use_math: true
---

Here are the first two photographs of snowflakes I've taken that have
any claim to being "macro".

[<img src="{{ site.baseurl }}/images/output6085-v2.jpg" width="800">]({{ site.baseurl }}/images/output6085-v2.jpg)

[<img src="{{ site.baseurl }}/images/output6207-27.jpg" width="800">]({{ site.baseurl }}/images/output6207-27.jpg)

Below are some notes for myself to help me remember what I figured out
and learned.

# Imaging setup

I used a handheld Nikon D200 with a 50mm f/1.8 lens and three
extension tubes totalling 65mm. The extension tubes don't have any
electrical connectors so the lens was wide open since it doesn't have
an aperature ring. There was also no metering --- i.e., manual
exposures. The flakes were collected on a knit hat and shot almost
immediately. Multiple exposures were combined for each image, see
below. Lighting was natural and ISO was 800. Since this is a pretty
old camera, 800 means "rather noisy."

# Processing

The individual exposures were usable on their own, but I was curious
about using focus stacking to extend the depth of field so tried that.
I used commands like the following to first attempt to align multiple
shots. 

```align_image_stack -v -a Out *.JPG```

For each of the snowflakes below I had taken several dozen images. My
experience was that align_image_stack was unable to align too many
images together, presumably because I moved too much between
shots. Going through manually I picked off a few that looked well
aligned and restricted the focus-stacking step to them:

```enfuse --exposure-weight=0 --saturation-weight=0 --contrast-weight=1 --hard-mask --verbose --output=output6207-27.tif Out00{27..28}.tif```

After a cursory glance, I believe the focus stacking is doing the
following: For each position in the picture, it looks at how
dissimilar the corresponding pixel is from its neighbors for each of
the available frames. It then picks the pixel from the image with the
greatest dissimilarity under the assmption that this will correspond
to the sharpest focus.

I then adjusted the light curves in the gimp. This helped get rid of
some weird halo effects that were visible in some of the original
images. I don't know if this is due to forcing the lens to focus more
closely than it'd like or if there is some other cause.

# Optics and magnification

By taking a picture of a ruler, I have determined that the setup
consisting of a 50mm lens + 65mm of extension tubes results in a
resolution of about 160 pixels/mm at minimum focus. So the snowflakes
in the above images are about 5-6mm in diameter. I now want to go
through the relevant formulas to understand better what is going on.

The minimum focus distance of the lens, given [here](https://www.nikonusa.com/en/nikon-products/product/camera-lenses/af-s-nikkor-50mm-f%252f1.8g.html),
is 450 mm. Note that this is the distance from the sensor
plane rather than from the front of the lens. We know that
$\frac{1}{f_1} + \frac{1}{f_2} = \frac{1}{f}$ where $f_1$ is the
distance from the lens to the object; $f_2$ is the distance from the
lens to the focal plane; and $f$ is the focal length of the lens. We
are approximating the complicated camera lens by a thin lens and
ignoring details such as nodal points. If the object is at infinity,
then $f_2=50$ mm --- this is the "closest" the lens needs to be to the
focal plane. On the other hand, at the minimum focus distance of 450
mm, one can compute that $f_2=57$ mm while $f_1 = 390$ mm. For this
computationn, we solve the two equations $\frac{1}{f_1} +
\frac{1}{f_2} = \frac{1}{50}$ and $450 = f_1 + f_2$. I guess this
means there is effectively 7 mm of travel available for focusing, which
sounds reasonable, but I haven't tried to measure it on the lens.

The extension tubes I have are labeled 7 mm, 14 mm and 28
mm. When stacked, this yields 49 mm. However, there is an additional
16 mm of adapter that must be used, giving a total extension of 65
mm. When all the tubes are used, the maximum value of $f_2$ becomes
65 mm + 57 mm = 122 mm. Plugging back in to our formula yields a
minimum value of $f_1=85$ mm, yielding a minimum focus distance of
122 + 85 = 207 mm. From the [wikipedia page for
magnification](https://en.wikipedia.org/wiki/Magnification), we see
that the reproduction ratio is the distance to the sensor plane
divided by the distance to the object. In our case, that yields a
reproduction ratio of $122/85$ = 1.44x. This means that, if you
imagine the actual image of the object overlaid onto the image sensor,
it has been enlarged to 144% of its original size.

We can check the reproduction ratios by taking pictures of objects of
known size at minimum focus distances. I didn't do it carefully for
the bare lens, but did indeed find that I could fit a little over 6"
of a ruler in the frame. This is roughly consistent with the reported
0.15x reproduction ratio and sensor width on the D200 of 23.6 mm. With
all of the extension tubes on, I could fit in 5/8", or about 16
mm. This suggests a reproduction ratio of $23.6/16=1.48$x. This is
not far off from our computed value above of 1.44x and agrees with the
results of this
[calculator](http://extreme-macro.co.uk/extension-tubes/#calculator).

None of the values I've measured have been particularly precise, so
I'm not surprised there's a moderate discrepancy. When I first made
the computation I forgot to include the extra 16 mm from the
extension-tube adapter and got a wildly different computed value from
what I was seeing. When measuring, one helpful value for the camera
body is the flange focal distance which, for the Nikon D200, is 46.50
mm.

# Other formulas

Apparently one can also compute the increase in magnification by
simply adding the length of the extension divided by the focal length
of the lens. In our case, the increase is $65/50=1.3$ yielding a final
reproduction ratio of 0.15 + 1.3 = 1.45x. I haven't really absorbed
this formula, but seems plausible.

# Close-up Lens Filters

You can buy "filters" to place on the front of the lens to add
additional magnification. These are expressed in diopters $D$ with the
focal length being $1000/D$ mm. According to [this
page](https://en.wikipedia.org/wiki/Close-up_lens), when focused at
the minimal focusing distance $X$, the magnification increases by a
factor of $DX+1$ when a lens of diopter $D$ is added. For my bare $50$
mm lens, the minimum focus distance is 0.45 meters, so a $+4$ diopter
lens would increase the magnification by a factor of 2.8. Since the
original magnification is 0.15x, we end up at 0.42x, which is not as
good as the extension tubes. Apparently close-up filters are more
effective on longer focal lengths.

# Both close-up filters and extension tubes

I haven't been able to understand mathematically exactly what happens
when you combine extension tubes and close-up filters. I'm sure it's
not complicated, I just don't happen to know enough about
optics.

Empirically, the filters don't seem to help all that much. At minimum
focus, about 21/32 of an inch fills the frame, just a hair more than
5/8". With a +4 diopter, 18/32 fills the frame. With all three lens, a
+7 diopter, 17/32 fills the frame. These provide about 16% and 24%
more magnification than the 50 mm lens and extension tubes alone. Using
1.45x for those, the combination yields either 1.69x or 1.79x. So
certainly better, but not outrageously better. It would be interesting
to see if the overall effect is worth it given the fact that you're
adding a fair amount of glass, especially when adding all three close
up lens for the +7 diopter case. 

You'd get a larger increase in magnification by simply switching to a
more recent, 24MP camera and cropping. But since the 50 mm lens is not
being used as directed since the focal plane is being shifted back,
the image quality might not be good enough for the added resolution to
help.

