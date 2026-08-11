---
title: "rel=\"preconnect\" HTML attribute value"
source: "https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Attributes/rel/preconnect"
translated_by: "n8n + AI"
---

مقدار `preconnect` برای ویژگی [`rel`](/en-US/docs/Web/HTML/Reference/Elements/link#rel) در عنصر {{HTMLElement("link")}} به مرورگر اشاره می‌کند که کاربر احتمالاً به منابعی از مبدأ (origin) مقصد نیاز دارد؛ بنابراین مرورگر می‌تواند با برقراری پیش‌دستی اتصال به آن مبدأ، تجربه کاربری را بهبود بخشد. Preconnect کردن باعث می‌شود بارگذاری‌های آینده از یک مبدأ مشخص سریع‌تر انجام شود، چون بخشی یا تمام handshake (DNS+TCP برای HTTP، و DNS+TCP+TLS برای مبدأهای HTTPS) از قبل انجام می‌شود.

`<link rel="preconnect">` برای هر درخواست HTTP آینده با مبدأ متفاوت (cross-origin) — چه ناوبری باشد چه زیرمنبع (subresource) — مفید است. اما برای درخواست‌های هم‌مبدأ (same-origin) هیچ سودی ندارد، چون اتصال از قبل باز است.

اگر یک صفحه نیاز به برقراری اتصال به دامنه‌های شخص ثالث زیادی دارد، preconnect کردن همه آنها می‌تواند نتیجه عکس بدهد. بهتر است از `<link rel="preconnect">` فقط برای حیاتی‌ترین اتصالات استفاده کنید. برای بقیه، از [`<link rel="dns-prefetch">`](/en-US/docs/Web/HTML/Reference/Attributes/rel/dns-prefetch) استفاده کنید تا فقط در مرحله اول (DNS lookup) زمان صرفه‌جویی شود.

## مثال‌ها

```html
<link rel="preconnect" href="https://example.com" />
```

همچنین می‌توانید preconnect را به صورت یک هدر HTTP [`Link`](/en-US/docs/Web/HTTP/Reference/Headers/Link) پیاده‌سازی کنید:

```http
Link: <https://example.com>; rel="preconnect"
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگرها

{{Compat}}

## همچنین ببینید

- [بارگذاری حدسی (Speculative loading)](/en-US/docs/Web/Performance/Guides/Speculative_loading) — مقایسه `<link rel="preconnect">` با سایر ویژگی‌های مشابه بهبود عملکرد.