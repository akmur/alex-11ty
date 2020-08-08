---
layout: single.njk
title: Using react-i18next to localise your application
author: akmur
type: post
date: 2019-07-04T08:15:44+00:00
categories:
  - Articles
---

In this post I would like to go through the configuration I use to provide localisation features to a React application. This might not be the best way, but it surely is the way that works for me, so I hope it can be useful to other people looking to add this same feature.

### Packages to install

These are the packages to be installed:

`i18next` and `react-i18next` are the actual internationalization packages.
`i18next-browser-languagedetector` is a package needed to set the default language to be the same as the current browser language.

```
npm install i18next react-i18next i18next-browser-languagedetector --save
```

### Creating translations

In order to load translations, we will create as many json files as you need (one for each language) in the `public` folder, inside the `locales` folder

```
./public
    - /locales
        - /de
            - translations.json
        - /en
            - translations.json
```

The `./public/locales/de/translations.json` might look like this:

```
{
    "basics": {
        "affirmation": "ja",
        "negation": "nein"
    }
}
```

and the `./public/locales/en/translations.json` will look like this:

```
{
    "basics": {
        "affirmation": "yes",
        "negation": "no"
    }
}
```

### Loading Translations in the App

This is the way I use these translation in `./src/index.js`:

First I fetch the translations from the locales folder, and once that is done I load the App

```
import React from 'react'
import ReactDOM from 'react-dom'

import i18n from 'i18next'
import { initReactI18next } from 'react-i18next'
import XHR from 'i18next-xhr-backend'
import LanguageDetector from 'i18next-browser-languagedetector';

import App from './App'

i18n
  .use(LanguageDetector)
  .use(XHR)
  .use(initReactI18next)
  .init({
    backend: {
      loadPath: '/locales/{{lng}}/translation.json'
    },
    load: 'all'
  })
  .then(() => {
    ReactDOM.render(
     <App />,
      document.getElementById('root')
    )
  })
```

### Using the translations in your app

Using the translations in your App will then work like this:

#### Function components:

```
// your react packages here...

import { useTranslation } from 'react-i18next'

const TeamMemberItem = props => {
  const { t } = useTranslation()

  return (
    <div>
      {t('basics.affirmation')}
      {/* will print yes */}
    </div>
  )
}
```

#### React components:

```
// your react packages here...

import { Translation } from 'react-i18next'

class MyComponent extends Component {
  render(){
    return (
    <Translation>
      {(t, { i18n }) => (
        <div>
          {t('basics.negation')}
          {/* will print no */}
        </div>
      )}
    </Translation>
    )
  }
}
```

### Outside the render function of the component

```
// your react packages here...

import i18n from 'i18next'

class MyComponent extends Component {
  const translationValue = i18n.t('basics.affirmation')

  render(){
    return (
     {/* your component */}
    )
  }
}
```

### Switching language

Finally, if you want to switch language, you can do the following in your component

```
// your react packages here...

import { useTranslation } from 'react-i18next'

const LanguageSwitch = () => {
    const { i18n } = useTranslation()

    const handleOnLanguageSwitch = () => {
        // get current language
        const currentLanguage = i18n.language || window.localStorage.i18nextLng || ''

        // set the new language variable
        newLanguage = currentLanguage === 'de' ? 'en' : 'de'

        // change the language
        i18n.changeLanguage(newLanguage)
    }

    return (
        <button onClick={handleOnLanguageSwitch}>
          Change Language
        </button>
    )
}
```

&nbsp;

If you would like to discuss this article, you can do so on Linkedin:

<blockquote class="blockquote__linkedin data-lang=" style="border-color: #1D77B5;">
  <p dir="ltr" lang="en">
    I wrote an article about localisation of React apps using react-i18next, hope you can find it interesting 🙂
  </p>
  <p>
    — Alessandro Muraro - July 4, 2019
  </p>
  <p>
    <a href="https://www.linkedin.com/feed/update/urn:li:activity:6552470270781739008/">Check it out on LinkedIn</a>
  </p>
</blockquote>

&nbsp;
