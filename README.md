# ESP32-PeppersGhost
For this project, I wanted to recreate a pepper ghost using an [ESP32 mircocontroller](https://www.amazon.ca/dp/B0C9THDPXP?ref=ppx_yo2ov_dt_b_fed_asin_title&th=1) and [TFT screen](https://www.amazon.ca/dp/B07BFV69DZ?ref=ppx_yo2ov_dt_b_fed_asin_title).

A pepper's ghost is the technique of reflecting the image on a display onto a slanted piece of clear glass/acrylic to create the illusion of a ghost or "hologram."

For the purposes of this project I just found a suitable gif to display.  What I found works best is ones with black background and saturated colours, also if some 3D movement also works great.

## Code
The code to display GIFs is from [this repo](https://github.com/thelastoutpostworkshop/animated_gif_memory).

The required library for this code is:
- [TFT-eSPI](https://github.com/Bodmer/TFT_eSPI)

What is most important is to edit the `User_Setup.h` file in the TFT-eSPI library for whatever display you are using.  For mine, I made the following changes:
- the driver: uncommented `#define ST7735_DRIVER` and commented all other drivers
- colour order: uncommented `#define TFT_RGB_ORDER TFT_RGB`
- dimension: my width and height were `#define TFT_WIDTH 128` and `#define TFT_HEIGHT 160`
- the type of display (only for ST7735): `#define ST7735_GREENTAB` (for me, this was trial and error until the display colours were correct)
- since I used an ESP32 board, I defined the SPI pins for my setup:
```#define TFT_MOSI 23
#define TFT_SCLK 18
#define TFT_CS    5  // Chip select control pin
#define TFT_DC    2  // Data Command control pin
#define TFT_RST   4  // Reset pin (could connect to RST pin)
```

For the displayed image, I first found a suitable GIF on [GIPHY](https://giphy.com/), then resized and optimzed it for my display size using [Ezgif](https://ezgif.com/), finally the GIF file was converted to a hex code using a tool such as [this](https://tomeko.net/online_tools/file_to_hex.php?lang=en).  This must then be included as a header file in the project.  For this project, this can be seen in `brain.h`.

## Schematic
<img src="https://github.com/chnanc001/ESP32-PeppersGhost/blob/main/peppersGhost/Images/schematic.PNG" width="800">

## The Build
I designed an enclosure using [Fusion360](https://www.autodesk.com/ca-en/products/fusion-360/personal).  

<img src="https://github.com/chnanc001/ESP32-PeppersGhost/blob/main/peppersGhost/Images/CAD.PNG" width="300">

The diagonal piece was cut out of clear thin acrylic - it is important that the acrylic used is thin otherwise you will see multiple reflections with a thicker piece of acrylic so the illusion does not look as good.  The image below shows an early prototype with the main body laser cut out of cardboard:

<img src="https://github.com/chnanc001/ESP32-PeppersGhost/blob/main/peppersGhost/Images/Prototype.jpg" width="300">

I found it difficult to capture the illusion on camera, but it does look more convincing in person.


