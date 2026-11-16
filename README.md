# Unit Conversion Factors

Exact unit conversion factors as one small JSON file, plus a few lines of JavaScript to use them. No dependencies.

The data comes from the free online [Unit Converter](https://unitconverter.network/), where every factor is shown with its formula, a worked example and a reference table.

## What is inside

`factors.json` covers length, mass, volume, area, speed, time, pressure, energy, power and data storage. Each category has a base unit, and every unit has the factor that turns it into the base unit.

| Category | Base unit | Example factor |
| --- | --- | --- |
| Length | meter | 1 inch = 0.0254 m, 1 mile = 1609.344 m |
| Mass | kilogram | 1 pound = 0.45359237 kg |
| Volume | liter | 1 US gallon = 3.785411784 L |
| Area | square meter | 1 acre = 4046.8564224 m2 |
| Speed | meter per second | 1 mph = 0.44704 m/s |
| Pressure | pascal | 1 atm = 101325 Pa |
| Energy | joule | 1 kWh = 3600000 J |

Factors are exact by definition unless the key ends in `_approx`. Volume units are US customary. Temperature is not a simple factor, so the file gives the formulas through kelvin.

## How to use

```js
const factors = require("./factors.json");

function convert(value, from, to, category) {
  const units = factors[category].units;
  return (value * units[from]) / units[to];
}

convert(10, "mile", "kilometer", "length");   // 16.09344
convert(5, "pound", "kilogram", "mass");       // 2.26796185
convert(1, "kilowatt_hour", "joule", "energy"); // 3600000
```

## Check a result

Compare any value with the live converters:

- [Miles to km](https://unitconverter.network/miles-to-km/)
- [Inches to mm](https://unitconverter.network/inches-to-mm/)
- [Lbs to kg](https://unitconverter.network/lbs-to-kg/)
- [kPa to bar](https://unitconverter.network/kpa-to-bar/)
- [All converters](https://unitconverter.network/all-converters/)

## License

The data is free to use in any project. A link back to [unitconverter.network](https://unitconverter.network/) is welcome but not required.
