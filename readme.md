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

* Instantiate a `Dictionary` object and initialize it from a PO file:

```
def dict: I18n.Dictionary;
dict.initialize(poContent);
```

or

```
def dict: I18n.Dictionary;
dict.initialize(Srl.Fs.readFile("lang.po"));
```

You can also load additional strings from a separate PO file using `add`:

```
dict.add(poContent);
```

or

```
dict.add(Srl.Fs.readFile("lang.po"));
```

You can use the `clear` function to clear all the loaded strings.

* Replace the hardcoded strings with the dictionary:

```
Console.print(dict("My localized string"));
```

## Determining Language Direction

To determine the direction of a language based on its code, i.e. determine whether it's right from right to left or
left to right, we use the `isRightToLeft` function:

```
I18n.isRightToLeft(String("ar")) // returns true
I18n.isRightToLeft(String("ar_EG")) // returns true
I18n.isRightToLeft(String("en")) // returns false
```

## TextAssets class

This class enables you to load text files in multiple languages from a folder and automatically
organize them as a class containing a text property for each of these files. It then loads them
for you automatically, categorized by languages according to the available folders. This class
takes two parameters: one is the path to the text resources folder, and the other is the default
language code. It expects the text resources folder to contain a subfolder for each language with
the language code as the folder name. Inside each of these subfolders, the text files with the same
names for all languages are placed. The class will define a variable for each of these files, named
after the file but without the extension.

**Note:**
This class will load all resources for all languages during compilation rather than during
execution, allowing it to be used for translating user interfaces in web applications.

For example, if you have the following folder:

```
assets/
  en/
    file1.txt
    file2.txt
    strings.po
  ar/
    file1.txt
    file2.txt
    strings.po
```

After initializing the class, you'll have a class containing a Map with two keys: 'ar' and 'en',
and for each key an instance of the class. In this scenario, the class will contain three variables
of type String: file1, file2, and strings.

To initialize and use this class:

```
I18n.TextAssets["./text_assets", "en"].initialize();
I18n.TextAssets["./text_assets", "en"].setCurrentLanguage(currentLang);
def strings: String = I18n.TextAssets["./text_assets", "en"].current.strings;
I18n.initializeStrings(strings);
Console.print("%s\n", I18n.string("string example"));
```

You can access the current language code using the variable `currentLanguage`. It's preferable to
rely on this variable as it ensures the usage of only available languages within the current
translations. For instance, if you call the `setCurrentLanguage` function with a language code
that isn't available in the translations, the class will choose the default language instead of
selecting a language with no translation.

### TextAssets.getAvailableLanguages

This function returns a list of available languages. The `initialize` function must be called before
invoking this function. It ensures that the default language is placed at the beginning of the
returned array.

```
func getAvailableLanguages(): Array[String];
```


