# timeagoplus

`timeagoplus` is a WebAssembly (Wasm) package that provides a utility to calculate and display the time elapsed since a given timestamp in a human-readable format. It supports multiple languages.

## Features

- Calculates the time elapsed since a given timestamp.
- Supports detailed labels (e.g., "1 year, 2 months ago").
- Multi-language support.

## Installation

Install the package via npm:

```sh
npm install timeagoplus
```

## Usage

Below are examples of how to use the `timeagoplus` package in both a React component and a plain JavaScript file.

### React Example

First, make sure you have installed the `timeagoplus` package:

```sh
npm install timeagoplus
```

Now, here's how you can use it in a React component:

```typescript
import React, { useState, useEffect } from 'react';
import init, { TimeAgo, Language } from 'timeagoplus';

const HomePage: React.FC = () => {
  const [time, setTime] = useState('');

  useEffect(() => {
    let intervalId: NodeJS.Timeout;

    // Initialization (Runs Only Once)
    init().then(() => {
      // Create a TimeAgo instance with default language and detailed label
      const timeAgo = new TimeAgo(Language.TRK);

      // Example using timestamp
      setTime(timeAgo.format(new Date().getTime())); // "now"

      // Update Logic (Runs every second)
      intervalId = setInterval(() => {
        setTime(timeAgo.format(new Date('2024-06-27T20:00:00+03:00')));
      }, 1000); // Update every second
    });

    // Cleanup (Runs when the component unmounts)
    return () => clearInterval(intervalId);
  }, []);

  return <div>{time}</div>;
};

export default HomePage;
```

### JavaScript Example

For plain JavaScript, make sure to also install the `timeagoplus` package:

```sh
npm install timeagoplus
```

Here's how you can use it in a simple HTML file:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>TimeAgoPlus Example</title>
  </head>
  <body>
    <div id="time"></div>
    <script type="module">
      import init, { TimeAgo, Language } from 'timeagoplus';

      document.addEventListener('DOMContentLoaded', async () => {
        await init();
        const timeAgo = new TimeAgo(Language.TRK);

        // Example using timestamp
        document.getElementById('time').textContent = timeAgo.format(
          new Date().getTime()
        ); // "now"

        // Update Logic (Runs every second)
        setInterval(() => {
          document.getElementById('time').textContent = timeAgo.format(
            new Date('2024-06-27T20:00:00+03:00')
          );
        }, 1000); // Update every second
      });
    </script>
  </body>
</html>
```

Both examples initialize the `timeagoplus` package, create a `TimeAgo` instance, and set up an interval to update the displayed time every second. The React example uses React hooks, while the JavaScript example uses plain DOM manipulation.

## Supported Languages

The `Language` enum provides a wide range of languages you can use.

| Language Code | Language Name           |
| ------------- | ----------------------- |
| `ACM`         | Mesopotamian Arabic     |
| `AEC`         | Saidi Arabic            |
| `AEB`         | Tunisian Arabic         |
| `AMH`         | Amharic                 |
| `APC`         | North Levantine Arabic  |
| `APD`         | Samar-Leyte Visayan     |
| `ARQ`         | Algerian Arabic         |
| `ARS`         | Najdi Arabic            |
| `ARY`         | Moroccan Arabic         |
| `ARZ`         | Egyptian Arabic         |
| `ASM`         | Assamese                |
| `AWD`         | Awadhi                  |
| `AYN`         | Northern Altai          |
| `AZB`         | South Azerbaijani       |
| `AZE`         | Azerbaijani             |
| `BGC`         | Haryanvi                |
| `BHJ`         | Bhojpuri                |
| `BLG`         | Bulgarian               |
| `BMS`         | Javanese                |
| `BNG`         | Bengali                 |
| `CEB`         | Cebuano                 |
| `CFR`         | Crimean Tatar           |
| `CHN`         | Mandarin Chinese        |
| `CJY`         | Jinyu Chinese           |
| `CIT`         | Citak                   |
| `CCX`         | Northern Luri           |
| `CZC`         | Czech                   |
| `DCC`         | Dakhini                 |
| `DUT`         | Dutch                   |
| `ENG`         | English                 |
| `FRN`         | French                  |
| `FUV`         | Nigerian Fulfulde       |
| `GAZ`         | West Central Oromo      |
| `GER`         | German                  |
| `GJR`         | Gujarati                |
| `GRK`         | Greek, Modern (1453-)   |
| `HAK`         | Hakka Chinese           |
| `HAT`         | Haitian; Haitian Creole |
| `HIL`         | Hiligaynon              |
| `HND`         | Hindi                   |
| `HNE`         | Chhattisgarhi           |
| `HNG`         | Hungarian               |
| `HSN`         | Xiang Chinese           |
| `HUA`         | Mandarin Chinese        |
| `IGR`         | Igbo                    |
| `ILO`         | Iloko                   |
| `INZ`         | Indonesian              |
| `ITN`         | Italian                 |
| `JAN`         | Javanese                |
| `JPN`         | Japanese                |
| `KAZ`         | Kazakh                  |
| `KJV`         | Kannada                 |
| `KKN`         | Kokni                   |
| `KMR`         | Khmer                   |
| `KNN`         | Gan Chinese             |
| `KUR`         | Central Kurdish         |
| `LMO`         | Lombard                 |
| `MEX`         | Mexican Spanish         |
| `MJS`         | Malaccan Creole Malay   |
| `MKD`         | Macedonian              |
| `MKP`         | Mohawk                  |
| `MHJ`         | Mahajani                |
| `MLI`         | Malayalam               |
| `MNP`         | Manipuri                |
| `MQM`         | Macaense                |
| `MRT`         | Marathi                 |
| `NEP`         | Nepali                  |
| `NPL`         | Nepali                  |
| `ORY`         | Odia                    |
| `PBT`         | Southern Pashto         |
| `PBU`         | Northern Pashto         |
| `PES`         | Western Farsi           |
| `PNJ`         | Eastern Panjabi         |
| `PNB`         | Western Panjabi         |
| `PQL`         | Pomeranian              |
| `POR`         | Portuguese              |
| `PRS`         | Eastern Farsi           |
| `RUA`         | Kinyarwanda             |
| `RUM`         | Romanian                |
| `RUS`         | Russian                 |
| `RUW`         | Kinyarwanda             |
| `SHD`         | Kundal Shahi            |
| `SKR`         | Saraiki                 |
| `SNH`         | Sinhala                 |
| `SND`         | Sindhi                  |
| `SOM`         | Somali                  |
| `SPN`         | Spanish                 |
| `SRC`         | Serbian                 |
| `SUO`         | Finnish                 |
| `SWD`         | Swedish                 |
| `TCV`         | Caviteño                |
| `TCW`         | Telugu                  |
| `TGL`         | Tagalog                 |
| `THJ`         | Tai                     |
| `TTR`         | Tatar                   |
| `TTS`         | Tausug                  |
| `TRK`         | Turkish                 |
| `TWS`         | Twi                     |
| `UKR`         | Ukrainian               |
| `URD`         | Urdu                    |
| `UZB`         | Uzbek                   |
| `UIG`         | Uighur                  |
| `VIE`         | Vietnamese              |
| `WUU`         | Wu Chinese              |
| `YOR`         | Yoruba                  |
| `YUH`         | Chinese, Yue            |
| `ZUU`         | Zulu                    |

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Author

Fatih Yavuz

## Repository

[GitHub](https://github.com/yvzfth/timeagoplus)

---

This README includes a brief introduction, installation instructions, usage examples, a description of the `time_ago` function, supported languages, licensing information, and links to the author and repository.
