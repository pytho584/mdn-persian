```
---
title: DOMException
slug: Web/API/DOMException
page-type: web-api-interface
browser-compat: api.DOMException
---

{{APIRef("DOM")}}{{AvailableInWorkers}}

رابطِ **`DOMException`** یک رویداد غیرعادی (که **exception** نامیده میشود) را نمایش میدهد که در نتیجهٔ فراخوانی یک متد یا دسترسی به یک ویژگی از یک API وب رخ میدهد. این روشی است که شرایط خطا در APIهای وب توصیف میشوند.

هر استثنا یک **name** دارد؛ یک رشتهٔ کوتاه به سبک "PascalCase" که خطا یا وضعیت غیرعادی را شناسایی میکند.

`DOMException` یک {{Glossary("Serializable object")}} است، بنابراین میتوان آن را با {{DOMxRef("Window.structuredClone", "structuredClone()")}} شبیهسازی کرد یا با استفاده از {{domxref("Worker.postMessage()", "postMessage()")}} بین [Workers](/en-US/docs/Web/API/Worker) کپی کرد.

## سازنده

- {{domxref("DOMException.DOMException()", "DOMException()")}}
  - : یک شیء `DOMException` با پیام و نام مشخصشده برمیگرداند.

## ویژگیهای نمونه

- {{domxref("DOMException.code")}} {{deprecated_inline}} {{ReadOnlyInline}}
  - : یکی از ثابتهای قدیمی کد خطا را برمیگرداند، یا اگر هیچکدام مطابقت نداشته باشند، `0` را برمیگرداند.
- {{domxref("DOMException.message")}} {{ReadOnlyInline}}
  - : رشتهای را برمیگرداند که پیام یا توضیح مرتبط با [نام خطا](#error_names) دادهشده را نشان میدهد.
- {{domxref("DOMException.name")}} {{ReadOnlyInline}}
  - : رشتهای را برمیگرداند که حاوی یکی از رشتههای مرتبط با یک [نام خطا](#error_names) است.

## نامهای خطا

نامهای رایج خطا در اینجا فهرست شدهاند. برخی APIها مجموعههای نام خود را تعریف میکنند، بنابراین این لزوماً یک فهرست کامل نیست.

خطاهای تاریخی منسوخ زیر نام خطا ندارند، اما در عوض فقط یک مقدار کد ثابت قدیمی و یک نام ثابت قدیمی دارند:

- مقدار کد قدیمی: `2`، نام ثابت قدیمی: `DOMSTRING_SIZE_ERR`
- مقدار کد قدیمی: `6`، نام ثابت قدیمی: `NO_DATA_ALLOWED_ERR`
- مقدار کد قدیمی: `16`، نام ثابت قدیمی: `VALIDATION_ERR`

> [!NOTE]
> از آنجا که در گذشته خطاها با یک مقدار عددی شناسایی میشدند که با یک متغیر نامگذاریشده با همان مقدار در ارتباط بود، برخی از موارد زیر مقدار کد قدیمی و نام ثابت استفادهشده در گذشته را نشان میدهند.

- `IndexSizeError`
  - : شاخص در محدودهٔ مجاز نیست. برای مثال، این ممکن است توسط شیء {{ domxref("Range") }} پرتاب شود. (مقدار کد قدیمی: `1` و نام ثابت قدیمی: `INDEX_SIZE_ERR`)
- `HierarchyRequestError`
  - : سلسلهمراتب درخت گره صحیح نیست. (مقدار کد قدیمی: `3` و نام ثابت قدیمی: `HIERARCHY_REQUEST_ERR`)
- `WrongDocumentError`
  - : شیء در {{ domxref("Document") }} اشتباهی قرار دارد. (مقدار کد قدیمی: `4` و نام ثابت قدیمی: `WRONG_DOCUMENT_ERR`)
- `InvalidCharacterError`
  - : رشته شامل نویسههای نامعتبر است. (مقدار کد قدیمی: `5` و نام ثابت قدیمی: `INVALID_CHARACTER_ERR`)
- `NoModificationAllowedError`
  - : شیء قابل تغییر نیست. (مقدار کد قدیمی: `7` و نام ثابت قدیمی: `NO_MODIFICATION_ALLOWED_ERR`)
- `NotFoundError`
  - : شیء در اینجا یافت نمیشود. (مقدار کد قدیمی: `8` و نام ثابت قدیمی: `NOT_FOUND_ERR`)
- `NotSupportedError`
  - : عملیات پشتیبانی نمیشود. (مقدار کد قدیمی: `9` و نام ثابت قدیمی: `NOT_SUPPORTED_ERR`)
- `InUseAttributeError`
  - : ویژگی در حال استفاده است. (مقدار کد قدیمی: `10` و نام ثابت قدیمی: `INUSE_ATTRIBUTE_ERR`)
- `InvalidStateError`
  - : شیء در حالت نامعتبر است. (مقدار کد قدیمی: `11` و نام ثابت قدیمی: `INVALID_STATE_ERR`)
- `SyntaxError`
  - : رشته با الگوی مورد انتظار مطابقت ندارد. (مقدار کد قدیمی: `12` و نام ثابت قدیمی: `SYNTAX_ERR`)
- `InvalidModificationError`
  - : شیء به این صورت قابل تغییر نیست. (مقدار کد قدیمی: `13` و نام ثابت قدیمی: `INVALID_MODIFICATION_ERR`)
- `NamespaceError`
  - : عملیات توسط فضاهای نام در XML مجاز نیست. (مقدار کد قدیمی: `14` و نام ثابت قدیمی: `NAMESPACE_ERR`)
- `InvalidAccessError`
  - : شیء از عملیات یا آرگومان پشتیبانی نمیکند. (مقدار کد قدیمی: `15` و نام ثابت قدیمی: `INVALID_ACCESS_ERR`)
- `TypeMismatchError` {{deprecated_inline}}
  - : نوع شیء با نوع مورد انتظار مطابقت ندارد. (مقدار کد قدیمی: `17` و نام ثابت قدیمی: `TYPE_MISMATCH_ERR`) این مقدار منسوخ شده است؛ در حال حاضر به جای `DOMException` با این مقدار، استثنای جاوااسکریپتی {{jsxref("TypeError")}} ایجاد میشود.
- `SecurityError`
  - : عملیات ناامن است. (مقدار کد قدیمی: `18` و نام ثابت قدیمی: `SECURITY_ERR`)
- `NetworkError` {{experimental_inline}}
  - : یک خطای شبکه رخ داد. (مقدار کد قدیمی: `19` و نام ثابت قدیمی: `NETWORK_ERR`)
- `AbortError` {{experimental_inline}}
  - : عملیات لغو شد. (مقدار کد قدیمی: `20` و نام ثابت قدیمی: `ABORT_ERR`)
- `URLMismatchError` {{experimental_inline}}
  - : URL دادهشده با URL دیگری مطابقت ندارد. (مقدار کد قدیمی: `21` و نام ثابت قدیمی: `URL_MISMATCH_ERR`)
- {{domxref("QuotaExceededError")}}
  - : سهمیه بیش از حد مجاز استفاده شده است. (مقدار کد قدیمی: `22` و نام ثابت قدیمی: `QUOTA_EXCEEDED_ERR`) این یک رابط واقعی است که از `DOMException` مشتق میشود.
- `TimeoutError`
  - : زمان عملیات به پایان رسید. (مقدار کد قدیمی: `23` و نام ثابت قدیمی: `TIMEOUT_ERR`)
- `InvalidNodeTypeError` {{experimental_inline}}
  - : گره برای این عملیات نادرست است یا جدِ نامناسبی دارد. (مقدار کد قدیمی: `24` و نام ثابت قدیمی: `INVALID_NODE_TYPE_ERR`)
- `DataCloneError` {{experimental_inline}}
  - : شیء قابل شبیهسازی نیست. (مقدار کد قدیمی: `25` و نام ثابت قدیمی: `DATA_CLONE_ERR`)
- `EncodingError` {{experimental_inline}}
  - : عملیات رمزگذاری یا رمزگشایی شکست خورد (مقدار کد قدیمی و نام ثابت قدیمی ندارد).
- `NotReadableError` {{experimental_inline}}
  - : عملیات خواندن ورودی/خروجی شکست خورد (مقدار کد قدیمی و نام ثابت قدیمی ندارد).
- `UnknownError` {{experimental_inline}}
  - : عملیات به دلیل نامعلوم موقتی (مثلاً کمبود حافظه) شکست خورد (مقدار کد قدیمی و نام ثابت قدیمی ندارد).
- `ConstraintError` {{experimental_inline}}
  - : یک عملیات تغییر در یک تراکنش به دلیل برآورده نشدن یک قید شکست خورد (مقدار کد قدیمی و نام ثابت قدیمی ندارد).
- `DataError` {{experimental_inline}}
  - : دادههای ارائهشده ناکافی هستند (مقدار کد قدیمی و نام ثابت قدیمی ندارد).
- `TransactionInactiveError` {{experimental_inline}}
  - : درخواستی علیه تراکنشی که در حال حاضر فعال نیست یا به پایان رسیده است، ارسال شد (مقدار کد قدیمی و نام ثابت قدیمی ندارد).
- `ReadOnlyError` {{experimental_inline}}
  - : عملیات تغییر در یک تراکنش «فقطخواندنی» تلاش شد (مقدار کد قدیمی و نام ثابت قدیمی ندارد).
- `VersionError` {{experimental_inline}}
  - : تلاش شد یک پایگاهداده با نسخهای پایینتر از نسخهٔ موجود باز شود (مقدار کد قدیمی و نام ثابت قدیمی ندارد).
- `OperationError` {{experimental_inline}}
  - : عملیات به دلیلی خاص برای آن عملیات شکست خورد (مقدار کد قدیمی و نام ثابت قدیمی ندارد).
- `NotAllowedError`
  - : درخواست توسط عامل کاربر یا پلتفرم در زمینهٔ فعلی مجاز نیست، احتمالاً به این دلیل که کاربر اجازه را رد کرده است (مقدار کد قدیمی و نام ثابت قدیمی ندارد).

## مشخصات

{{Specifications}}

## سازگاری مرورگر

{{Compat}}

## همچنین ببینید

- [یک polyfill برای `DOMException`](https://github.com/zloirock/core-js#domexception) در [`core-js`](https://github.com/zloirock/core-js) موجود است.
- {{ domxref("DOMError") }}
```