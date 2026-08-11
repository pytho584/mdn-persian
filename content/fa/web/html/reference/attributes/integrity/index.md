---
title: "integrity HTML attribute"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/integrity"
translated_by: "n8n + AI"
---

The **`integrity`** attribute به توسعه‌دهنده مکانیزمی می‌دهد تا تأیید کند که یک script یا stylesheet لینک‌شده محتوای مشخصی دارد. مرورگر بررسی می‌کند که منبع واقعاً همان محتوا را داشته باشد و اگر نداشت، از بارگذاری آن خودداری می‌کند.

این یک دفاع در برابر [حمله زنجیره تأمین](https://developer.mozilla.org/en-US/docs/Web/Security/Attacks/Supply_chain_attacks) است؛ در این نوع حمله، مهاجم به دامنه‌ای که script یا stylesheet را سرو می‌کند دسترسی پیدا می‌کند و منبع مورد انتظار را با یک منبع مخرب جایگزین می‌کند.

## توضیحات

این ویژگی فقط روی عناصر `<script>` یا `<link>` قابل اعمال است.

این ویژگی از یک یا چند مؤلفه تشکیل شده است که هر کدام شامل موارد زیر هستند:

- شناسه‌ای برای یک تابع هش رمزنگاری (cryptographic hash function). سه تابع هش پشتیبانی می‌شوند که به ترتیب افزایش قدرت عبارتند از: SHA-256، SHA-384 و SHA-512.
- نتیجه هش کردن محتوای منبع با استفاده از تابع هش مشخص‌شده.

وقتی مرورگر منبعی را با ویژگی `integrity` دانلود می‌کند، ابتدا مجموعه هش‌هایی را انتخاب می‌کند که با قوی‌ترین تابع هش موجود تولید شده‌اند. یعنی اگر ویژگی حاوی مقادیری باشد که با SHA-256 و SHA-384 تولید شده‌اند، فقط از هش‌های تولیدشده با SHA-384 استفاده می‌کند.

سپس مرورگر هش محتوای منبع را با استفاده از تابع مشخص‌شده محاسبه می‌کند و نتیجه را با همه مقادیر مشخص‌شده مقایسه می‌کند: اگر مقدار واقعی با هر کدام از مقادیر مشخص‌شده مطابقت داشت، مرورگر منبع را بارگذاری می‌کند؛ در غیر این صورت از بارگذاری آن خودداری می‌کند.

برای جزئیات بیشتر، راهنمای [Subresource Integrity](https://developer.mozilla.org/en-US/docs/Web/Security/Defenses/Subresource_Integrity) را ببینید.

## مقادیر

مقدار این ویژگی شامل فهرستی از مؤلفه‌ها است که با فاصله از هم جدا شده‌اند و هر کدام یکی از شکل‌های زیر را دارد:

- `sha256-HASH_VALUE`
- `sha384-HASH_VALUE`
- `sha512-HASH_VALUE`

در هر حالت، بخش قبل از `-` تابع هش استفاده‌شده را مشخص می‌کند و `HASH_VALUE` کدگذاری base64 نتیجه هش کردن منبع با استفاده از تابع هش مشخص‌شده است.

## مثال‌ها

### استفاده از توابع هش مختلف

عنصر `<script>` زیر شامل یک ویژگی `integrity` با سه مقدار است: یکی با SHA-256، یکی با SHA-384 و یکی با SHA-512 محاسبه شده است.

مرورگر مقداری را انتخاب می‌کند که با قوی‌ترین الگوریتمی که پشتیبانی می‌کند محاسبه شده باشد. از آنجا که همه مرورگرهای مدرن از SHA-512 پشتیبانی می‌کنند، مرورگر مقدار `sha512-` را انتخاب می‌کند. محتوای فایل را با SHA-512 هش می‌کند، نتیجه را با مقدار `sha512-` مقایسه می‌کند و فقط در صورت مطابقت، فایل را بارگذاری می‌کند.

در این حالت، ارائه چند مقدار به وب‌سایت امکان می‌دهد با مرورگرهایی که از همه توابع هش پشتیبانی نمی‌کنند نیز کار کند.

```html
<script
  src="https://cdn.example.com/script.js"
  integrity="
  sha256-NmUxNTFiMDUzZGIwZjcwZDIyYTc5NTA4ZmQyNT
  sha384-Tk2Yjg3YmYzMWNkZTdhMTFkM2FlNDg4ZjE3MzEzNTk3ZDlh
  sha512-OGUwYThkZDc2YzFlZGI5MDEzZmZhMGFkMGQ0OTQ3MzZkNGYZTEzODk2"
  crossorigin="anonymous"></script>
```

توجه داشته باشید که در این مثال و مثال‌های بعدی، برای اختصار، مقادیر هش نمونه را کوتاه کرده‌ایم.

### استفاده از مقادیر هش مختلف

عنصر `<script>` زیر شامل یک ویژگی `integrity` با دو مقدار مختلف است که هر دو با الگوریتم SHA-512 محاسبه شده‌اند. این مقادیر متفاوت، محتوای جایگزین برای فایل لینک‌شده را نشان می‌دهند.

اگر هش SHA-512 فایل لینک‌شده با هر کدام از مقادیر داده‌شده مطابقت داشته باشد، مرورگر آن را بارگذاری می‌کند.

این کار به سرور `cdn.example.com` امکان می‌دهد با یکی از دو نسخه فایل پاسخ دهد.

```html
<script
  src="https://cdn.example.com/script.js"
  integrity="
  sha512-ZmQ5NjNiYWJjYTM3MjRhMGI4MTQzNWRmZTZkZGYyMzQyOGYYTZkYjBm
  sha512-OGUwYThkZDc2YzFlZGI5MDEzZmZhMGFkMGQ0OTQ3MzZkNGYZTEzODk2"
  crossorigin="anonymous"></script>
```

### استفاده از `integrity` در عنصر `<link>`

عنصر {{htmlelement("link")}} زیر یک stylesheet را بارگذاری می‌کند و یک ویژگی `integrity` دارد که شامل شش مقدار است. این مقادیر دو محتوای احتمالی برای فایل لینک‌شده را منعکس می‌کنند که هرکدام با سه تابع hash متفاوت محاسبه شده‌اند.

مرورگر مجموعه‌ای از مقادیر را انتخاب می‌کند که با قوی‌ترین تابع hash پشتیبانی‌شده محاسبه شده باشند. در مرورگرهای مدرن، این دو مقدار `sha512-` هستند.

سپس مرورگر hash فایل دانلودشده را با SHA-512 محاسبه می‌کند و نتیجه را با هر دو مقدار `sha512-` مقایسه می‌کند: اگر یکی از آنها مطابقت داشت، مرورگر منبع را بارگذاری می‌کند.

```html
<link
  rel="stylesheet"
  href="https://cdn.example.com/style.css"
  integrity="
  sha256-NmUxNTFiMDUzZGIwZjcwZDIyYTc5NTA4ZmQyNT
  sha256-OTcyMGZkY2Y3NGZhZjUwNWU5NGQ0ZWJhYWVhND
  sha384-Tk2Yjg3YmYzMWNkZTdhMTFkM2FlNDg4ZjE3MzEzNTk3ZDlh
  sha384-ZTdhYjQ2NTE5OTg0Yjc2ZDU2MDMxMDUxY2Y5NDMxYzI5NjA
  sha512-OGUwYThkZDc2YzFlZGI5MDEzZmZhMGFkMGQ0OTQ3MzZkNGYZTEzODk2
  sha512-IxZTcwZjE2ZjU3MzE4NWM5ODU4ZmJkYjBlYzBhYzFkYzU0OGJmM2ZkN"
  crossorigin="anonymous" />
```