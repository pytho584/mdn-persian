---
title: "FontFaceSet"
---

{{APIRef("CSS Font Loading API")}}{{AvailableInWorkers}}

رابط **`FontFaceSet`** از [CSS Font Loading API](/en-US/docs/Web/API/CSS_Font_Loading_API) بارگذاری فونت‌فیس‌ها و پرس‌وجوی وضعیت دانلود آنها را مدیریت می‌کند.

یک نمونه از `FontFaceSet` یک [شیء شبیه به `Set`](/en-US/docs/Web/JavaScript/Reference/Global_Objects/Set#set-like_browser_apis) است که می‌تواند یک مجموعه مرتب از اشیاء {{domxref("FontFace")}} را نگه دارد.

این ویژگی به صورت {{domxref("Document.fonts")}} یا `self.fonts` در [web workers](/en-US/docs/Web/API/Web_Workers_API) در دسترس است.

{{InheritanceDiagram}}

## خصوصیات نمونه

- {{domxref("FontFaceSet.status")}} {{ReadOnlyInline}}
  - : وضعیت بارگذاری فونت‌فیس را نشان می‌دهد. یکی از مقادیر `'loading'` یا `'loaded'` خواهد بود.
- {{domxref("FontFaceSet.ready")}} {{ReadOnlyInline}}
  - : یک {{jsxref("Promise")}} که پس از اتمام عملیات بارگذاری فونت و چیدمان (layout) resolve می‌شود.
- {{domxref("FontFaceSet.size")}} {{ReadOnlyInline}}
  - : تعداد مقادیر موجود در `FontFaceSet` را بازمی‌گرداند.

### رویدادها

- {{domxref("FontFaceSet.loading_event", "loading")}}
  - : هنگامی که یک مجموعه فونت‌فیس شروع به بارگذاری می‌کند، فعال می‌شود.
- {{domxref("FontFaceSet.loadingdone_event", "loadingdone")}}
  - : هنگامی که بارگذاری یک مجموعه فونت‌فیس به پایان می‌رسد، فعال می‌شود.
- {{domxref("FontFaceSet.loadingerror_event", "loadingerror")}}
  - : هنگامی که در حین بارگذاری یک مجموعه فونت‌فیس خطایی رخ می‌دهد، فعال می‌شود.

## روش‌های نمونه

- {{domxref("FontFaceSet.add","FontFaceSet.add()")}}
  - : یک فونت به مجموعه فونت اضافه می‌کند.
- {{domxref("FontFaceSet.check","FontFaceSet.check()")}}
  - : یک مقدار بولی که نشان می‌دهد آیا یک فونت بارگذاری شده است، اما در صورت عدم بارگذاری، شروع به بارگذاری نمی‌کند.
- {{domxref("FontFaceSet.clear", "FontFaceSet.clear()")}}
  - : تمام فونت‌های دستی اضافه شده را از مجموعه فونت حذف می‌کند. فونت‌های [متصل به CSS](https://drafts.csswg.org/css-font-loading-3/#css-connected) تحت تأثیر قرار نمی‌گیرند.
- {{domxref("FontFaceSet.delete","FontFaceSet.delete()")}}
  - : یک فونت دستی اضافه شده را از مجموعه فونت حذف می‌کند. فونت‌های [متصل به CSS](https://drafts.csswg.org/css-font-loading-3/#css-connected) تحت تأثیر قرار نمی‌گیرند.
- {{domxref("FontFaceSet.entries","FontFaceSet.entries()")}}
  - : یک iterator جدید با مقادیر هر عنصر در `FontFaceSet` به ترتیب درج بازمی‌گرداند.
- {{domxref("FontFaceSet.forEach","FontFaceSet.forEach()")}}
  - : یک تابع ارائه شده را برای هر مقدار در شیء `FontFaceSet` اجرا می‌کند.
- {{domxref("FontFaceSet.has","FontFaceSet.has()")}}
  - : یک {{jsxref("Boolean")}} بازمی‌گرداند که تأیید می‌کند آیا عنصری با مقدار داده شده وجود دارد یا خیر.
- {{domxref("FontFaceSet.keys","FontFaceSet.keys()")}}
  - : یک نام مستعار برای {{domxref("FontFaceSet.values()")}}.
- {{domxref("FontFaceSet.load","FontFaceSet.load()")}}
  - : یک {{jsxref("Promise")}} بازمی‌گرداند که به یک لیست از فونت‌فیس‌ها برای یک فونت درخواستی resolve می‌شود.
- {{domxref("FontFaceSet.values","FontFaceSet.values()")}}
  - : یک شیء iterator جدید بازمی‌گرداند که مقادیر هر عنصر در شیء `FontFaceSet` را به ترتیب درج تولید می‌کند.

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}