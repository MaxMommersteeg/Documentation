---
uid: Meadow.Foundation.ICs.IOExpanders.Ht16K33
remarks: *content
---

| HT16K33       |             |
|---------------|-------------|
| Status        | Working     |
| Source code   | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/ICs.IOExpanders.HT16K33) |
| NuGet package | <img src="https://img.shields.io/nuget/v/Meadow.Foundation.ICs.IOExpanders.Ht16K33.svg?label=Meadow.Foundation.ICs.IOExpanders.Ht16K33" style="width: auto; height: -webkit-fill-available;" /> |

The **HT16K33** is an LED driver and key scanner. It can be used to drive up to 128 leds and is often found pre-assembled with 14-segment led displays. The HT16K33 is controlled via I2C.

### Code Example

```csharp
public class MeadowApp : App<F7Micro, MeadowApp>
{
    HT16K33 ht16k33;

    public MeadowApp()
    {
        ht16k33 = new HT16K33(Device.CreateI2cBus());

        TestHT16K33();
    }

    void TestHT16K33() 
    {
        int index = 0;
        bool on = true;

        while (true)
        {
            ht16k33.ToggleLed((byte)index, on);
            ht16k33.UpdateDisplay();
            index++;

            if (index >= 128)
            {
                index = 0;
                on = !on;
            }

            Thread.Sleep(100);
        }
    }
}
```

[Sample projects available on GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/ICs.IOExpanders.HT16K33Samples) 