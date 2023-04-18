# I18n
[[عربي]](readme.ar.md)

Internationalization functionality for Alusus Language. This library can load translations from PO
files.

## Usage

* Add the library to the project using Alusus Package Manager:

```
import "Apm";
Apm.importFile("Alusus/I18n");
```

* Initialize the library from PO file:

```
I18n.initialize(poContent);
```

or

```
I18n.initialize(Srl.Fs.readFile("lang.po"));
```

* Replace the hardcoded strings with `I18n.string`:

```
Console.print(I18n.string("My localized string"));
```

