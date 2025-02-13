---
uid: Meadow.Foundation.Displays.ePaper.Il3897
remarks: *content
---

| ePaper        |             |
|---------------|-------------|
| Status        | Working     |
| Source code   | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Displays.ePaper) |
| NuGet package | <img src="https://img.shields.io/nuget/v/Meadow.Foundation.Displays.ePaper.svg?label=Meadow.Foundation.Displays.ePaper" style="width: auto; height: -webkit-fill-available;" /> |

The **IL3897** is a dual-color display controller for ePaper displays. Data is sent to the controller via SPI and supports full screen updates only.

The IL3897 is commonly paired with a 2.13" two color ePaper display.

[Sample projects available on GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Displays.ePaper/Samples)

### Wiring Example

 To control a IL3897 from Meadow, connect the following:

| IL3897  | Meadow Pin |
|---------|------------|
| BUSY    | D15        |
| RST     | D14        |
| DC      | D13        |
| CS      | D12        |
| CLK     | SCK        |
| DIN     | MOSI       |
| GND     | GND        |
| VCC     | 3V3        |

If your display does not include any of the above pins, they can be omitted. Pass `NULL` into the constructor for the missing pin(s).

<img src="../../API_Assets/Meadow.Foundation.Displays.ePaper.IL3897/ePaper_Fritzing.png" 
    style="width: 60%; display: block; margin-left: auto; margin-right: auto;" />