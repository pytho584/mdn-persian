---
title: "<script type=\"importmap\"> HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/script/type/importmap"
translated_by: "n8n + AI"
---

مقدار **`importmap`** برای ویژگی [`type`](/en-US/docs/Web/HTML/Reference/Elements/script/type) در عنصر [`<script>`](/en-US/docs/Web/HTML/Reference/Elements/script) نشان می‌دهد که محتوای عنصر حاوی یک نقشه واردات (import map) است.

نقشه واردات یک شیء JSON است که به توسعه‌دهندگان اجازه می‌دهد نحوه‌ی حل (resolve) مشخص‌کننده‌های ماژول (module specifiers) توسط مرورگر را هنگام وارد کردن [ماژول‌های JavaScript](/en-US/docs/Web/JavaScript/Guide/Modules) کنترل کنند. این نقشه یک نگاشت بین متنی که در [`import statement`](/en-US/docs/Web/JavaScript/Reference/Statements/import) یا [`import() operator`](/en-US/docs/Web/JavaScript/Reference/Operators/import) به عنوان مشخص‌کننده ماژول استفاده می‌شود و مقدار متناظر آن که هنگام حل مشخص‌کننده جایگزین می‌شود، فراهم می‌کند. شیء JSON باید با [فرمت نمایش JSON نقشه واردات](#import_map_json_representation) مطابقت داشته باشد.

نقشه واردات برای حل مشخص‌کننده‌های ماژول در importهای ایستا و پویا استفاده می‌شود، بنابراین باید قبل از هر عنصر `<script>` که ماژول‌ها را با استفاده از مشخص‌کننده‌های تعریف‌شده در نقشه وارد می‌کند، اعلام و پردازش شود. توجه داشته باشید که نقشه واردات فقط برای مشخص‌کننده‌های ماژول در `import statement` یا `import() operator` برای ماژول‌هایی که در سند بارگذاری می‌شوند اعمال می‌شود؛ این نقشه برای مسیر مشخص‌شده در ویژگی `src` یک عنصر `<script>` یا برای ماژول‌هایی که در workerها یا workletها بارگذاری می‌شوند، کاربرد ندارد.

برای اطلاعات بیشتر، بخش [وارد کردن ماژول‌ها با استفاده از import maps](/en-US/docs/Web/JavaScript/Guide/Modules#importing_modules_using_import_maps) در راهنمای ماژول‌های JavaScript را ببینید.

## Syntax

```html
<script type="importmap">
  // شیء JSON که import را تعریف می‌کند
</script>
```

ویژگی‌های `src`، `async`، `nomodule`، `defer`، `crossorigin`، `integrity` و `referrerpolicy` نباید مشخص شوند.

### Exceptions

- `TypeError`
  - : تعریف نقشه واردات یک شیء JSON نیست، کلید `importmap` تعریف شده اما مقدار آن یک شیء JSON نیست، یا کلید `scopes` تعریف شده اما مقدار آن یک شیء JSON نیست.

مرورگرها برای موارد دیگری که JSON نقشه واردات با [طرحواره نقشه واردات](#import_map_json_representation) مطابقت ندارد، هشدارهایی در کنسول تولید می‌کنند.

## Description

هنگام وارد کردن یک [ماژول JavaScript](/en-US/docs/Web/JavaScript/Guide/Modules)، هم `import statement` و هم `import() operator` یک "مشخص‌کننده ماژول" دارند که نشان می‌دهد کدام ماژول باید وارد شود. مرورگر باید بتواند این مشخص‌کننده را به یک URL مطلق حل کند تا ماژول را وارد کند.

برای مثال، دستورات زیر عناصر را از مشخص‌کننده ماژول `"https://example.com/shapes/circle.js"` (که یک URL مطلق است) و مشخص‌کننده ماژول `"./modules/shapes/square.js"` (که یک مسیر نسبی نسبت به URL پایه سند است) وارد می‌کنند.

```js
import { name as circleName } from "https://example.com/shapes/circle.js";
import { name as squareName, draw } from "./modules/shapes/square.js";
```

نقشه‌های واردات به توسعه‌دهندگان اجازه می‌دهند (تقریباً) هر متنی را که می‌خواهند در مشخص‌کننده ماژول مشخص کنند؛ نقشه یک مقدار متناظر ارائه می‌دهد که هنگام حل مشخص‌کننده ماژول جایگزین آن متن می‌شود.

### Bare modules

نقشه واردات زیر یک کلید `imports` تعریف می‌کند که یک "نقشه مشخص‌کننده ماژول" با ویژگی‌های `circle` و `square` دارد.

```html
<script type="importmap">
  {
    "imports": {
      "circle": "https://example.com/shapes/circle.js",
      "square": "./modules/shapes/square.js"
    }
  }
</script>
```

با این نقشه واردات می‌توانیم همان ماژول‌های بالا را وارد کنیم، اما با استفاده از "bare modules" در مشخص‌کننده‌های ماژول خود:

```js
import { name as circleName } from "circle";
import { name as squareName, draw } from "square";
```

### نگاشت پیشوندهای مسیر (Mapping path prefixes)

یک کلید در module specifier map می‌تواند برای بازنگاشت پیشوند مسیر در یک module specifier هم استفاده شود. توجه کنید که در این حالت، هم ویژگی و هم مسیر نگاشت‌شده باید به اسلش رو به جلو (`/`) ختم شوند.

```html
<script type="importmap">
  {
    "imports": {
      "shapes/": "./modules/shapes/",
      "other-shapes/": "https://example.com/modules/shapes/"
    }
  }
</script>
```

سپس می‌توانیم ماژول دایره را به صورت زیر import کنیم.

```js
import { name as circleName } from "shapes/circle.js";
```

### مسیرها در کلیدهای module specifier map

کلیدهای module specifier لزوماً نام‌های تک‌کلمه‌ای («bare names») نیستند. آن‌ها می‌توانند شامل جداکننده‌های مسیر باشند یا به آن‌ها ختم شوند، یا URLهای مطلق باشند، یا مسیرهای URL نسبی که با `/`، `./` یا `../` شروع می‌شوند.

```json
{
  "imports": {
    "modules/shapes/": "./modules/src/shapes/",
    "modules/square": "./modules/src/other/shapes/square.js",
    "https://example.com/modules/square.js": "./modules/src/other/shapes/square.js",
    "../modules/shapes/": "/modules/shapes/"
  }
}
```

اگر چند کلید در یک module specifier map وجود داشته باشند که بتوانند با module specifier تطبیق پیدا کنند، خاص‌ترین کلید انتخاب می‌شود (یعنی کلیدی که مسیر/مقدار طولانی‌تری دارد).

یک module specifier مانند `./foo/../js/app.js` قبل از تطبیق به `./js/app.js` تبدیل می‌شود. این یعنی کلید `./js/app.js` می‌تواند با این module specifier تطبیق یابد، حتی اگر دقیقاً یکسان نباشند.

### نقشه‌های module specifier با دامنه (Scoped)

می‌توانید از کلید `scopes` استفاده کنید تا نگاشت‌هایی را فراهم کنید که فقط وقتی به کار می‌روند که اسکریپتِ در حال import کردن ماژول، شامل یک مسیر URL خاص باشد. اگر URL اسکریپتِ در حال بارگذاری با مسیر داده‌شده مطابقت کند، نگاشت مرتبط با آن scope استفاده می‌شود. این امکان را می‌دهد که بسته به کدی که در حال import است، نسخه‌های متفاوتی از ماژول استفاده شوند.

برای مثال، در نقشهٔ زیر، فقط اگر ماژولِ در حال بارگذاری URLی داشته باشد که شامل مسیر `/modules/custom-shapes/` باشد، از نقشهٔ scoped استفاده می‌شود.

```html
<script type="importmap">
  {
    "imports": {
      "square": "./modules/shapes/square.js"
    },
    "scopes": {
      "/modules/custom-shapes/": {
        "square": "https://example.com/modules/shapes/square.js"
      }
    }
  }
</script>
```

اگر چند scope با URL مرجع (referrer) مطابقت داشته باشند، خاص‌ترین مسیر scope استفاده می‌شود (کلیدی با طولانی‌ترین نام). اگر مشخص‌کنندهٔ منطبقی وجود نداشته باشد، مرورگر به سراغ خاص‌ترین scope بعدی می‌رود و همین طور ادامه می‌دهد تا در نهایت به module specifier map در کلید `imports` برسد.

### نقشهٔ فرادادهٔ یکپارچگی (Integrity Metadata)

می‌توانید از کلید `integrity` برای نگاشت [فرادادهٔ یکپارچگی](/en-US/docs/Web/Security/Defenses/Subresource_Integrity#using_subresource_integrity) ماژول‌ها استفاده کنید. این کار به شما امکان می‌دهد یکپارچگی ماژول‌های import شده به صورت داینامیک یا استاتیک را تضمین کنید. `integrity` همچنین به شما امکان می‌دهد برای ماژول‌های سطح بالا یا پیش‌بارگذاری‌شده، یک fallback فراهم کنید، در صورتی که آن‌ها از قبل ویژگی `integrity` نداشته باشند.

کلیدهای نقشه، URLهای ماژول را نشان می‌دهند که می‌توانند مطلق یا نسبی باشند (با `/`، `./` یا `../` شروع شوند). مقدارهای نقشه، فرادادهٔ یکپارچگی را نشان می‌دهند؛ همان چیزی که در مقادیر ویژگی [`integrity`](/en-US/docs/Web/HTML/Reference/Elements/script#integrity) استفاده می‌شود.

برای مثال، نقشهٔ زیر فرادادهٔ یکپارچگی را برای ماژول `square.js` (به صورت مستقیم) و مشخص‌کنندهٔ bare آن (به صورت غیرمستقیم، از طریق کلید `imports`) تعریف می‌کند.

```html
<script type="importmap">
  {
    "imports": {
      "square": "./modules/shapes/square.js"
    },
    "integrity": {
      "./modules/shapes/square.js": "sha384-oqVuAfXRKap7fdgcCY5uykM6+R9GqQ8K/uxy9rx7HNQlGYl1kPzQho1wx4JwY8wC"
    }
  }
</script>
```

### ادغام چند import map

مرورگرهای پشتیبان می‌توانند یک یا چند import map را در هر جای سند تعریف کنند، به شرطی که پیش از بارگذاری هر ماژولی که به آن‌ها وابسته است تعریف شده باشند (برخی نسخه‌های مرورگر فقط یک تعریف import map را مجاز می‌دانند که باید پیش از بارگذاری هر ماژولی قرار گیرد).

در سطح داخلی، مرورگرها یک نمایش global import map واحد نگهداری می‌کنند. وقتی چند import map در سند گنجانده می‌شود، محتوای آن‌ها هنگام ثبت، در global import map ادغام می‌شود.

برای مثال، دو import map زیر را در نظر بگیرید:

```html
<script type="importmap">
  {
    "imports": {
      "/app/": "./original-app/"
    }
  }
</script>
```

```html
<script type="importmap">
  {
    "imports": {
      "/app/helper": "./helper/index.mjs"
    },
    "scopes": {
      "/js": {
        "/app/": "./js-app/"
      }
    }
  }
</script>
```

این دو معادل import map واحد زیر هستند:

```html
<script type="importmap">
  {
    "imports": {
      "/app/": "./original-app/",
      "/app/helper": "./helper/index.mjs"
    },
    "scopes": {
      "/js": {
        "/app/": "./js-app/"
      }
    }
  }
</script>
```

module specifierهایی که در هر map ثبت‌شده قبلاً resolve شده‌اند، کنار گذاشته می‌شوند. resolveهای بعدی این specifierها همان نتایج resolveهای قبلی خود را می‌دهند.

برای مثال، اگر module specifier «/app/helper.js» قبلاً resolve شده باشد، import map جدید زیر:

```html
<script type="importmap">
  {
    "imports": {
      "/app/helper.js": "./helper/index.mjs",
      "lodash": "/node_modules/lodash-es/lodash.js"
    }
  }
</script>
```

معادل این خواهد بود:

```html
<script type="importmap">
  {
    "imports": {
      "lodash": "/node_modules/lodash-es/lodash.js"
    }
  }
</script>
```

قانون «/app/helper.js» نادیده گرفته شد و در map گنجانده نشد.

به همین ترتیب، module specifierهایی که در یک map ثبت‌شده قبلاً در global map به URL نگاشته شده‌اند، کنار گذاشته می‌شوند؛ نگاشت قبلی آن‌ها برقرار است.

برای مثال، دو import map زیر:

```html
<script type="importmap">
  {
    "imports": {
      "/app/helper": "./helper/index.mjs",
      "lodash": "/node_modules/lodash-es/lodash.js"
    }
  }
</script>
```

```html
<script type="importmap">
  {
    "imports": {
      "/app/helper": "./main/helper/index.mjs"
    }
  }
</script>
```

معادل import map واحد زیر هستند:

```html
<script type="importmap">
  {
    "imports": {
      "/app/helper": "./helper/index.mjs",
      "lodash": "/node_modules/lodash-es/lodash.js"
    }
  }
</script>
```

قانون «/app/helper» از map دوم حذف شد.

> [!NOTE]
> در مرورگرهای غیرپشتیبان (به [داده‌های سازگاری](#browser_compatibility) مراجعه کنید)، می‌توان از [polyfill](https://github.com/guybedford/es-module-shims) برای جلوگیری از مشکلات مربوط به resolve ماژول استفاده کرد.

## بازنمایی JSON در import map

در ادامه تعریف «رسمی» از بازنمایی JSON در import map ارائه می‌شود.

import map باید یک شیء JSON معتبر باشد که بتواند هر یک از کلیدهای اختیاری `imports`، `scopes` و `integrity` را تعریف کند. مقدار هر کلید باید یک شیء باشد، که ممکن است خالی باشد.

- `imports` (اختیاری)
  - : مقدار آن یک [module specifier map](#module_specifier_map) است؛ این map نگاشتی را فراهم می‌کند بین متنی که ممکن است به‌عنوان module specifier در عبارت `import` یا عملگر `import()` استفاده شود، و متنی که هنگام resolve شدن آن specifier جایگزینش می‌شود.

    این map، نقشهٔ جایگزین (fallback) است: اگر هیچ URL مسیر `scopes` مطابقت نداشته باشد، یا اگر module specifier mapهای موجود در مسیرهای `scopes` منطبق، کلیدی مطابق با module specifier نداشته باشند، این map برای یافتن module specifierهای منطبق جستجو می‌شود.
    - `<module specifier map>`
      - : «module specifier map» یک شیء JSON معتبر است که در آن _کلیدها_ متن‌هایی هستند که ممکن است هنگام import کردن یک ماژول در module specifier وجود داشته باشند، و _مقادیر_ متناظر، URLها یا مسیرهایی هستند که وقتی module specifier به یک آدرس resolve می‌شود، جایگزین آن متن می‌شوند.

شیء JSON مربوط به **module specifier map** (نقشه‌ی مشخص‌کننده‌ی ماژول) باید شرایط زیر را داشته باشد:

- هیچ‌کدام از کلیدها نباید خالی باشند.
- همه‌ی مقادیر باید رشته باشند؛ یا یک URL مطلق معتبر، یا یک رشته‌ی URL معتبر که با `/`، `./` یا `../` شروع شود.
- اگر یک کلید با `/` خاتمه یابد، مقدار متناظر آن نیز باید با `/` خاتمه یابد.  
  کلیدی که در انتها `/` دارد می‌تواند به‌عنوان پیشوند برای نگاشت (یا تغییر نگاشت) آدرس‌های ماژول استفاده شود.
- ترتیب ویژگی‌های شیء不重要 نیست: اگر چند کلید بتوانند با مشخص‌کننده‌ی ماژول مطابقت داشته باشند، خاص‌ترین کلید استفاده می‌شود (مثلاً مشخص‌کننده‌ی `"olive/branch/"` قبل از `"olive/"` تطبیق داده می‌شود).

- `integrity` {{optional_inline}}
  - : یک شیء JSON معتبر تعریف می‌کند که در آن **کلیدها** رشته‌هایی شامل URLهای مطلق یا نسبی معتبر (شروع‌شونده با `/`، `./` یا `../`) هستند و **مقادیر** متناظر، **فراداده‌ی یکپارچگی (integrity metadata)** معتبر می‌باشند (مطابق [Subresource Integrity](/en-US/docs/Web/Security/Defenses/Subresource_Integrity#using_subresource_integrity)).

    اگر URL یک اسکریپت که ماژولی را import یا preload می‌کند با یک کلید در شیء `integrity` مطابقت داشته باشد، فراداده‌ی یکپارچگی متناظر به گزینه‌های fetch آن اسکریپت اعمال می‌شود، مگر اینکه اسکریپت از قبل دارای فراداده‌ی یکپارچگی باشد.

- `scopes` {{optional_inline}}
  - : Scopes (حوزه‌ها) **module specifier map**های مختص مسیر را تعریف می‌کنند و امکان انتخاب map بر اساس مسیر کد importکننده‌ی ماژول را فراهم می‌کنند.

    شیء `scopes` یک شیء JSON معتبر است که در آن هر ویژگی یک `<scope key>` (کلید حوزه) است که یک مسیر URL می‌باشد و مقدار متناظر آن یک `<module specifier map>` است.

    اگر URL یک اسکریپت importکننده‌ی ماژول با یک `<scope key>` مطابقت داشته باشد، ابتدا `<module specifier map>` مربوط به آن کلید برای یافتن مشخص‌کننده‌های منطبق بررسی می‌شود. اگر چند کلید scope مطابقت داشته باشند، ابتدا مقادیر مربوط به خاص‌ترین/تو‌در‌تو‌ترین مسیرهای scope برای یافتن مشخص‌کننده‌های ماژول منطبق بررسی می‌شوند. در صورت عدم تطابق هیچ‌کدام از کلیدهای module specifier map در هیچ‌یک از scoped module specifier mapهای منطبق، از `module specifier map` پیش‌فرض در `imports` استفاده می‌شود.

    توجه داشته باشید که scope نحوه‌ی حل (resolve) یک آدرس را تغییر نمی‌دهد؛ آدرس‌های نسبی همیشه نسبت به base URL import map حل می‌شوند.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [JavaScript modules > Importing modules using import maps](/en-US/docs/Web/JavaScript/Guide/Modules#importing_modules_using_import_maps)
- [The `type` attribute of HTML `<script>` elements](/en-US/docs/Web/HTML/Reference/Elements/script/type)
- [`import` statement](/en-US/docs/Web/JavaScript/Reference/Statements/import)
- [`import()` operator](/en-US/docs/Web/JavaScript/Reference/Operators/import)