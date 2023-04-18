# I18n
[[English]](readme.md)

مكتبة لتمكين ترجمة النصوص المستخدمة في واجهات المستخدم. هذه المكتبة تحمل الترجمات من ملفات PO.

## الاستخدام

* أضف المكتبة إلى المشروع باستخدام مدير حزم الأسس:

<div dir=rtl>

```
اشمل "مـحا"؛
مـحا.اشمل_ملف("Alusus/I18n"، "تـرجمة.أسس")؛
```

</div>

```
import "Apm";
Apm.importFile("Alusus/I18n");
```

* هيئ المكتبة من ملف PO:

<div dir=rtl>

```
تـرجمة.هيئ(محتوى_po)؛
```

</div>

```
I18n.initialize(poContent);
```

أو

<div dir=rtl>

```
تـرجمة.هيئ(مـتم.نـم.اقرأ_ملف("en.po"))؛
```

</div>

```
I18n.initialize(Srl.Fs.readFile("lang.po"));
```

* استبدل سلاسل المحارف المضمنة بالدالة `تـرجمة.نص`:

<div dir=rtl>

```
طـرفية.اطبع(تـرجمة.نص("نصي المترجم"))؛
```

</div>

```
Console.print(I18n.string("My localized string"));
```

