# Inky

[![Build Status](https://travis-ci.com/pimoroni/inky.svg?branch=master)](https://travis-ci.com/pimoroni/inky)
[![Coverage Status](https://coveralls.io/repos/github/pimoroni/inky/badge.svg?branch=master)](https://coveralls.io/github/pimoroni/inky?branch=master)
[![PyPi Package](https://img.shields.io/pypi/v/einky.svg)](https://pypi.python.org/pypi/einky)
[![Python Versions](https://img.shields.io/pypi/pyversions/einky.svg)](https://pypi.python.org/pypi/einky)

Python library for the [Inky pHAT](https://shop.pimoroni.com/products/inky-phat) and [Inky wHAT](https://shop.pimoroni.com/products/inky-what) e-paper displays.

## Inky pHAT

[Inky pHAT](https://shop.pimoroni.com/products/inky-phat) is a 212x104 pixel e-paper display, available in red/black/white, yellow/black/white and black/white. It's great for nametags and displaying very low frequency information such as a daily calendar or weather overview.


## Inky wHAT

[Inky wHAT](https://shop.pimoroni.com/products/inky-what) is a 400x300 pixel e-paper display available in red/black/white, yellow/black/white and black/white. It's got tons of resolution for detailed daily todo lists, multi-day weather forecasts, bus timetables and more.

# Installation

The Python pip package is named einky, install with:

```
sudo pip install einky
```

# Usage

The Inky library contains modules for both the pHAT and wHAT, load the InkyPHAT one as follows:

```python
from inky import InkyPHAT
```

You'll then need to pick your colour, one of 'red', 'yellow' or 'black' and instantiate the class:

```python
inkyphat = InkyPHAT('red')
```

If you're using the wHAT you'll need to load the InkyWHAT class from the Inky library like so:

```python
from inky import InkyWHAT
inkywhat = InkyWHAT('red')
```

Once you've initialised Inky, there are only three methods you need to be concerned with:

#### Set Image

Set a PIL image, numpy array or list to Inky's internal buffer. The image dimensions should match the dimensiosn of the pHAT or wHAT you're using.

```python
inkyphat.set_image(image)
```

You should use `PIL` to create an image. `PIL` provides an `ImageDraw` module which allow you to draw text, lines and shapes over your image. See: https://pillow.readthedocs.io/en/stable/reference/ImageDraw.html

#### Set Border

Set the border colour of you pHAT or wHAT.

```python
inkyphat.set_border(colour)
```

`colour` should be one of `inky.RED`, `inky.YELLOW`, `inky.WHITE` or `inky.BLACK` with available colours depending on your diplay type.

#### Update The Display

Once you've prepared and set your image, and chosen a border colour, you can update your e-ink display with:

```python
inkyphat.show()
```


# Migrating

If you're migrating code from the `inkyphat` library you'll find that much of the drawing and image manipulation functions have been removed from Inky. These functions were always supplied by PIL, and the recommended approach is to use PIL to create and prepare your image before setting it to Inky with `set_image()`.
