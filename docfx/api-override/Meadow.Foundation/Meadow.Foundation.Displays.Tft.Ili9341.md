---
uid: Meadow.Foundation.Displays.Tft.Ili9341
remarks: *content
---

| TftSpi        |             |
|---------------|-------------|
| Status        | Working     |
| Source code   | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Displays.TftSpi) |
| NuGet package | <img src="https://img.shields.io/nuget/v/Meadow.Foundation.Displays.TftSpi.svg?label=Meadow.Foundation.Displays.TftSpi" style="width: auto; height: -webkit-fill-available;" /> |

The **ILI9341** is a display controller used to drive color displays over SPI using 12, 16 or 18 bbp. These displays require a backlight. These displays are commonly found with a resolution of 320x240.

The Meadow.Foundation ILI9341 driver currently only supports 16bpp RGB565.

### Code Example

```csharp
public class MeadowApp : App<F7Micro, MeadowApp>
{
    Ili9341 display;
    GraphicsLibrary graphics;

    public MeadowApp ()
    {
        var spiBus = Device.CreateSpiBus();

        display = new Ili9341(
            device: Device, 
            spiBus: spiBus,
            chipSelectPin: null,
            dcPin: Device.Pins.D01,
            resetPin: Device.Pins.D00,
            width: 240, height: 320);

        graphics = new GraphicsLibrary(display);

        graphics.CurrentFont = new Font8x8();
        graphics.Clear();
        graphics.DrawTriangle(10, 10, 50, 50, 10, 50, Meadow.Foundation.Color.Red);
        graphics.DrawRectangle(20, 15, 40, 20, Meadow.Foundation.Color.Yellow, false);
        graphics.DrawCircle(50, 50, 40, Meadow.Foundation.Color.Blue, false);
        graphics.DrawText(5, 5, "Meadow F7 SPI");
        graphics.Show();
    }
}
```

[Sample projects available on GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Displays.TftSpi/Samples)

### Wiring Example

 To wire a ILI9341 to your Meadow board, connect the following:

| ILI9341 | Meadow Pin |
|---------|------------|
| LED-    | 3V3        |
| LED+    | GND        |
| MOSI    | MOSI       |
| SCK     | SCK        |
| RESET   | D15        |
| A0      | D14        |
| CS      | D13        |
| VCC     | 3V3        |
| GND     | GND        |

It should look like the following diagram:

<img src="../../API_Assets/Meadow.Foundation.Displays.Tft.Ili9341/Ili9341_Fritzing.png" 
    style="width: 60%; display: block; margin-left: auto; margin-right: auto;" />