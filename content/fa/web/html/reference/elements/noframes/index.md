---
title: "<noframes> HTML frame fallback element"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/noframes"
translated_by: "n8n + AI"
---

# `<noframes>` - عنصر جایگزین (fallback) فریم در HTML

عنصر `<noframes>` در HTML محتوایی را برای مرورگرهایی فراهم می‌کند که از عنصر `<frame>` پشتیبانی نمی‌کنند (یا پشتیبانی از آن را غیرفعال کرده‌اند). اگرچه بیشتر مرورگرهای رایج از فریم‌ها پشتیبانی می‌کنند، استثناهایی هم وجود دارد؛ از جمله برخی مرورگرهای خاص مثل بعضی مرورگرهای موبایل و همچنین مرورگرهای متنی.

داخل `<noframes>` می‌توان هر عنصر HTMLای که در بدنهٔ سند مجاز است قرار داد، به‌جز عناصر `<frameset>` و `<frame>`؛ چون استفاده از فریم وقتی پشتیبانی نمی‌شود منطقی نیست.

از `<noframes>` می‌توان برای نمایش پیامی استفاده کرد که توضیح می‌دهد مرورگر کاربر از فریم‌ها پشتیبانی نمی‌کند، اما ایده‌آل این است که از آن برای ارائهٔ نسخهٔ جایگزینی از سایت استفاده شود که از فریم استفاده نمی‌کند ولی همان کارایی یا کارایی مشابه را ارائه می‌دهد.

> **نکته:** این عنصر منسوخ (obsolete) است و نباید استفاده شود، چون عناصر `<frame>` و `<frameset>` نیز منسوخ هستند. اگر به فریم نیاز بود، باید از عنصر `<iframe>` استفاده کرد.

## ویژگی‌ها

مانند تمام عناصر HTML دیگر، این عنصر از ویژگی‌های سراسری (global attributes) پشتیبانی می‌کند. ویژگی دیگری ندارد.

## مثال

در این مثال، یک frameset با دو فریم می‌بینیم. علاوه بر آن، از `<noframes>` برای نمایش پیام توضیحی در صورتی که عامل کاربر (user agent) از فریم‌ها پشتیبانی نکند استفاده شده است.

```html
<!doctype html>
<html lang="en-US">
  <head>
    <!-- Document metadata goes here -->
  </head>
  <frameset rows="45%, 55%">
    <frame src="https://developer.mozilla.org/en/HTML/Element/frameset" />
    <frame src="https://developer.mozilla.org/en/HTML/Element/frame" />
    <noframes>
      <p>
        It seems your browser does not support frames or is configured to not
        allow them.
      </p>
    </noframes>
  </frameset>
</html>
```

## همچنین ببینید

- [`<frameset>`](/en-US/docs/Web/HTML/Element/frameset)
- [`<frame>`](/en-US/docs/Web/HTML/Element/frame)