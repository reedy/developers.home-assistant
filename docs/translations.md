---
title: "Contributing Translation"
---

Translations for Home Assistant are managed through [Lokalise](https://lokalise.com/), an online translation management tool.

The canonical version of message are defined in American English, referred to as "English" or `en-us`.

Our translations are split between four projects: a backend project for platform-specific translations, a frontend project for UI translations, and two for the official (iOS and Android) companion apps. Even if your language is completely translated, extra proofreading is a big help! Please feel free to review the existing translations, and vote for alternatives that might be more appropriate. Click the links below to view and join the projects! 

- [Join the frontend translation team](https://lokalise.com/public/3420425759f6d6d241f598.13594006/)
- [Join the backend translation team](https://lokalise.com/public/130246255a974bd3b5e8a1.51616605/)
- [Join the iOS translation team](https://lokalise.com/public/834452985a05254348aee2.46389241/)
- [Join the Android translation team](https://lokalise.com/public/145814835dd655bc5ab0d0.36753359/)

For more information about the translation editor and tools, please see the [Lokalise translate and collaborate documents](https://docs.lokalise.com/en/collections/2909016-translate-and-collaborate).

Translations are downloaded from Lokalise on every build, so all major, minor, beta releases and nightly builds will have the latest translations available. 

## Translation placeholders

Some translation strings will contain special placeholders that will be replaced at runtime. 

Placeholders defined in square brackets `[]` (shown in green in Lokalise) are [Lokalise key references](https://docs.lokalise.com/en/articles/1400528-key-referencing). These are primarily used to link translation strings that will be duplicated, rather then redefining the same translation over and over again. Where sensible, the translation should make use of those (the square brackets placeholder value can be easily taken over by clicking on the "Source Alt+0" button in the Lokalise edit mode). Different languages may not have the same duplicate translations as English, and are welcome to link duplicate translations that are not linked in English. 

Placeholders shown in curly brackets `{}` are [translation arguments](https://formatjs.io/docs/core-concepts/icu-syntax/) that will be replaced with a live value when Home Assistant is running. Any translation argument placeholders present in the original string must be included in the translated string and must not be translated! These placeholders may include special syntax for defining plurals or other replacement rules. These may not be needed for the source messages (in `en-us`), but will be included to ease translation into other languages. The above linked Format.JS guide explains the syntax for adding plural definitions and other rules.

## Rules

1. Only native speakers should submit translations.
2. Stick to the [Material Design Writing Guidelines](https://m2.material.io/design/communication/writing.html).
3. Don't translate or change proper nouns like `Home Assistant`, `Supervisor` or `Hue`. Some of these are documented in the project's [Glossary](https://docs.lokalise.com/en/articles/1400629-glossary) tab.
4. For a region specific translation, keys that will be the same as the base translation should be filled with [`[VOID]`](https://docs.lokalise.com/en/articles/1400511-lokalise-universal-placeholders). These will be replaced during our translation build process.
6. Translations under the `state_badge` keys will be used for the notification badge display. These translations should be short enough to fit in the badge label without overflowing. This can be tested in the Home Assistant UI either by editing the label text with your browsers Developer tools, or by using the States tab of Developer Tools in the Home Assistant UI. In the UI, enter a new entity ID (`device_tracker.test`), and enter the text you want to test in state.
7. If text will be duplicated across different translation keys, make use of the [Lokalise key reference](https://docs.lokalise.com/articles/1400528-key-referencing) feature where possible. The base translation provides examples of this underneath the `states` translations.

## Adding a new language

:::info
Region specific translations (such as `en-GB` or `fr-CA`) will only be included if translations for that region need to differ from the base language translation.
:::

If your language (or variant) is not listed, you can request it in the Home Assistant Frontend [GitHub repository](https://github.com/home-assistant/frontend/discussions/new?category=localization). Please provide both the English name and the native name for your language. For example:

```txt
English Name: German
Native Name: Deutsch
```

### Maintainer steps to add a new language

1. Language codes and tags have to follow the [BCP 47](https://tools.ietf.org/html/bcp47) standard. A list of most language tags can be found here: [IANA subtag registry](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry). Examples include `fr`, `fr-CA` and `zh-Hans`. Only include the country code if country specific overrides are being included, and the base language is already translated (such as with English and British English).
2. Add the language tag and native name in [`translationMetadata.json`](https://github.com/home-assistant/frontend/blob/dev/src/translations/translationMetadata.json). Examples include `Français` and `Français (CA)`.
4. Add the new language in [Lokalize](https://docs.lokalise.com/en/articles/1400544-language-settings).

Note: Sometimes you have to change the tag in Lokalise (Language -> Language settings -> custom ISO code).

## Language specific guidelines
Most languages have multiple possible translations of a sentence. Please take a look at any specific guidelines for your language below. These may include some examples to prevent typical mistakes.

The sections are written in their corresponding languages, as this makes explaining the grammar easier and only native speakers should be submitting translations in those languages as per the [Rules](#rules).

### German
- Du/Sie: Duze in den Übersetzungen, und verwende nicht das formale "Sie".

#### Typische Fehler
- Achte auf den richtigen Imperativ. Der Imperativ ist die Befehlsform, z. B. "Gib mir das Wasser". Falsch wäre hier: "Gebe mir das Wasser" (siehe [Bildung des Imperativs](https://www.duden.de/sprachwissen/sprachratgeber/Bildung-des-Imperativs)).

### French
- *Blueprint*: il a été décidé de ne pas traduire ce mot et de le considérer comme un nom propre. Cela évite les confusions avec les traductions de *map* et *template* et facilite la recherche de Blueprint à importer sur Internet. Il faut donc toujours utiliser `Blueprint` avec une majuscule.
