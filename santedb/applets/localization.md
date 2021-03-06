# Localization

The core SanteDB applets are designed to easily be localized and branded to suit your particular deployment of SanteDB. 

### Localizing Your Applets

When writing your applets, there are a variety of ways to make localization and branding of your applet easier. First, in all HTML assets you can use the i18n service in Angular to localize your asset. 

```markup
<strong>{{ 'my.ui.local.string' | i18n}}</strong>
```

You should then register **my.ui.local.string** in the applet's manifest file.

```markup
<strings lang="en">
    <string key="my.ui.local.string">My Local String</string>
    
```

{% hint style="info" %}
It is recommended you use the manifest file and i18n service as SanteDB will pre-translate the file before sending it to the browser and will cache the result. This reduces the amount of processing power required for repeat viewing of the page.
{% endhint %}

If you want to fetch a string from JavaScript in the current locale, you can use the localization service

```javascript
if(!valid) {
    alert(SanteDB.locale.getString("my.ui.local.error"));
    
```

### Switch Locales

By default, SanteDB will switch the current locale of the user interface to that preferred by the user when they authenticate. You can also manually set the locale by calling

```javascript
SanteDB.locale.setLocale('en');
```

When you call this, a cookie is set in the browser which controls the rendering on the server side. However, this is the lowest order of preference for the server. In short, the server will render assets using the following preference:

1. The user's preference \(stored at : **UserEntity.languageCommunication**\) is used, if the user has no preference then,
2. The lang cookie provided by the browser, if there is no setting then
3. The value of Accept-Language HTTP header sent by the browser, if not sent then
4. The configured server preference \(set in the SanteDB.config.xml file\)

### Registering New Locales

Locales are registered using the applet manifest.xml, within the manifest, you can specify one or more assets \(css, javascript, etc.\) to be loaded for the particular locale. For example, to define a localization for Esperanto:

```markup
<AppletManifest xmlns="http://santedb.org/applet">
    <info id="org.santedb.sample">
        ...
    </info>
    
    ...
    
  <locales>
    <locale code="eo">
      <asset>/org.santedb.sample/i18n/angular-locale_eo.js</asset>
      <asset>/org.santedb.sample/i18n/santedb-eo.js</asset>
    </locale>
  </locales>
```

This instructs the SanteDB application framework to register a new locale "EO" and load the two supplied assets whenever the user interface is switched to locale eo. 

{% hint style="info" %}
The locale JavaScript files can be your own settings for SanteDB specific objects or they can be included libraries from common javascript plugins. 
{% endhint %}



