# Globalization helpers

This document describe how you can use this helper in a React project.

## Configuring the project

### Translation files

In order to make the language helpers work, it need a set of configuration.

#### Create the tanslation files

Based on the file `language.jsx`. we need the following:

- Create the folder `src/i18`.
- Create a JSON file with two chars language of the desired translations. `ex: src/i18/en.json or src/i18/fr.json`.
- Update the JSON files in the `language.jsx` file to match the location. (if you copy the `globalization.helpers` in a folder `src/utils` you can skip this line.)

#### Using the helpers

In your `[index | main].js` file do the following:

- import the language `wrapper`:

```JavaScript
import { IntlProviderWrapper } from "./utils/globalization.helpers/Intl_provider_wrapper.jsx.jsx";
```

- In the `Render` method wrap all the components:

```JavaScript
ReactDOM.render(
  <IntlProviderWrapper>

    <React.StrictMode>
      <Header
        title={DEFAULT_APP_NAME_ID}
        defaultTitle={DEFAULT_APP_NAME}
        logo={Logo}
      />

      <AppContent />

      <Footer title={DEFAULT_APP_NAME_ID} defaultTitle={DEFAULT_APP_NAME} />
    </React.StrictMode>

  </IntlProviderWrapper>,
  document.getElementById("root")
);
```

#### Show the Language Switcher

You can update or change the code to match your needs. Onces finished you can use it as follow:

- Import the switcher and use it:

```JavaScript
import LanguageSwitcher from "./utils/globalization.helpers/language_switcher.jsx";

...
const navToggle = (
    <>
    <Navbar.Toggle />
    <Navbar.Collapse className="justify-content-end">
        <LanguageSwitcher/>
    </Navbar.Collapse>
    </>
);
...
```
