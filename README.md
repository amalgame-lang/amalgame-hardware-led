# amalgame-hardware-led

Portable **LED drivers** for Amalgame, written against [`amalgame-hal`](https://github.com/amalgame-lang/amalgame-hal) — the same code runs on a Raspberry Pi (via [`amalgame-hardware-gpio`](https://github.com/amalgame-lang/amalgame-hardware-gpio)) and on future MCU backends.

```sh
amc package add hardware-led
```

```amalgame
import Amalgame.Hardware          // GpioOut, Pwm (Pi backend)
import Amalgame.Hardware.Led

let led = new Led(new GpioOut(17))
led.On(); led.Toggle(); led.Off()

let rgb = new RgbLed(new Pwm(0,0), new Pwm(0,1), new Pwm(1,0))
rgb.On(); rgb.SetColor(80, 0, 30)   // each 0..100 %
```

| Class | API |
|---|---|
| `Led(out: DigitalOut)` | `On()` / `Off()` / `Toggle()` / `Set(on)` |
| `RgbLed(r,g,b: PwmOut)` | `On()` / `Off()` / `SetColor(r,g,b)` (0..100%) |

Requires amc ≥ 0.8.72. Apache-2.0.
