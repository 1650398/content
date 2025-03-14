---
title: Intl.DisplayNames.supportedLocalesOf()
slug: Web/JavaScript/Reference/Global_Objects/Intl/DisplayNames/supportedLocalesOf
tags:
  - DisplayNames
  - Internationalization
  - Intl
  - JavaScript
  - Localization
  - Method
  - Reference
browser-compat: javascript.builtins.Intl.DisplayNames.supportedLocalesOf
---

{{JSRef}}

The **`Intl.DisplayNames.supportedLocalesOf()`** method returns
an array containing those of the provided locales that are supported in display names
without having to fall back to the runtime's default locale.

## Syntax

```js
Intl.DisplayNames.supportedLocalesOf(locales)
Intl.DisplayNames.supportedLocalesOf(locales, options)
```

### Parameters

- `locales`
  - : A string with a BCP 47 language tag, or an array of such strings. For the general form and interpretation of the `locales` argument, see [Locale identification and negotiation](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#locale_identification_and_negotiation).
- `options` {{optional_inline}}

  - : An object that may have the following property:

    - `localeMatcher`
      - : The locale matching algorithm to use. Possible values are
        `"lookup"` and `"best fit"`; the default is
        `"best fit"`. For information about this option, see the
        {{jsxref("Intl", "Intl", "#Locale_negotiation", 1)}} page.

### Return value

An array of strings representing a subset of the given locale tags that are supported
in display names without having to fall back to the runtime's default locale.

## Description

Returns an array with a subset of the language tags provided in `locales`.
The language tags returned are those for which the runtime supports a locale in
display names that the locale matching algorithm used considers a match, so that it
wouldn't have to fall back to the default locale.

## Examples

### Using supportedLocalesOf()

Assuming a runtime that supports Indonesian and German but not Balinese in display
names, `supportedLocalesOf` returns the Indonesian and German language tags
unchanged, even though `pinyin` collation is neither relevant to display
names nor used with Indonesian, and a specialized German for Indonesia is unlikely to
be supported. Note the specification of the `"lookup"` algorithm here — a
`"best fit"` matcher might decide that Indonesian is an adequate match for
Balinese since most Balinese speakers also understand Indonesian, and therefore return
the Balinese language tag as well.

```js
const locales = ['ban', 'id-u-co-pinyin', 'de-ID'];
const options = { localeMatcher: 'lookup' };
console.log(Intl.DisplayNames.supportedLocalesOf(locales, options).join(', '));
// → "id-u-co-pinyin, de-ID"
```

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- {{jsxref("Intl.DisplayNames")}}
