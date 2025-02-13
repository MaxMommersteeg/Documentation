---
uid: Meadow.Foundation.Motors.Stepper.Uln2003
remarks: *content
---

| ULN2003       |             |
|---------------|-------------|
| Status        | Working     |
| Source code   | [GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Motors.Stepper.Uln2003) |
| NuGet package | <img src="https://img.shields.io/nuget/v/Meadow.Foundation.Motors.Stepper.Uln2003.svg?label=Meadow.Foundation.Motors.Stepper.Uln2003" style="width: auto; height: -webkit-fill-available;" /> |

**ULN2003** is a high voltage, high current Darlington array containing seven open collector Darlington pairs. The ULN2003 is often packaged on board used to control stepper motors.

### Code Example

```csharp
public class MeadowApp : App<F7Micro, MeadowApp>
{
    Uln2003 stepperController;

    public MeadowApp()
    {
        stepperController = new Uln2003(
                device: Device, 
                pin1: Device.Pins.D01, 
                pin2: Device.Pins.D02, 
                pin3: Device.Pins.D03, 
                pin4: Device.Pins.D04);

        stepperController.Step(1024);

        for (int i = 0; i < 100; i++)
        {
            Console.WriteLine($"Step forward {i}");
            stepperController.Step(50);
            Thread.Sleep(10);
        }

        for (int i = 0; i < 100; i++)
        {
            Console.WriteLine($"Step backwards {i}");
            stepperController.Step(-50);
            Thread.Sleep(10);
        }
    }
}
```

[Sample projects available on GitHub](https://github.com/WildernessLabs/Meadow.Foundation/tree/master/Source/Meadow.Foundation.Peripherals/Motors.Stepper.Uln2003/Samples/) 