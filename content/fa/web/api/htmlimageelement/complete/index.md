---
title: "HTMLImageElement: complete property"
short-title: complete
slug: Web/API/HTMLImageElement/complete
page-type: web-api-instance-property
browser-compat: api.HTMLImageElement.complete
---

{{APIRef("HTML DOM")}}

ویژگی فقط‌خواندنی **`complete`** در رابط {{domxref("HTMLImageElement")}} یک مقدار بولی است که نشان می‌دهد آیا تصویر به طور کامل بارگذاری شده است یا خیر.

## مقدار

یک مقدار بولی که در صورت بارگذاری کامل تصویر `true` و در غیر این صورت `false` است.

تصویر زمانی کاملاً بارگذاری شده در نظر گرفته می‌شود که هر یک از موارد زیر صادق باشد:

- هیچ‌یک از ویژگی‌های [`src`](/en-US/docs/Web/HTML/Reference/Elements/img#src) یا [`srcset`](/en-US/docs/Web/HTML/Reference/Elements/img#srcset) مشخص نشده باشد.
- ویژگی `srcset` وجود نداشته باشد و ویژگی `src`، اگرچه مشخص شده، رشته خالی (`""`) باشد.
- منبع تصویر به طور کامل دریافت شده و برای رندر/ترکیب در صف قرار گرفته باشد.
- عنصر تصویر قبلاً تشخیص داده باشد که تصویر کاملاً در دسترس و آماده استفاده است.
- تصویر «خراب» باشد؛ یعنی به دلیل خطا یا غیرفعال بودن بارگذاری تصویر، بارگذاری نشده باشد.

شایان ذکر است که به دلیل احتمال دریافت ناهمزمان تصویر، مقدار `complete` ممکن است در حین اجرای اسکریپت شما تغییر کند.

## مثال‌ها

### اجرای توابع فقط روی تصاویر بارگذاری شده

برنامه‌ای از کتابخانه عکس را در نظر بگیرید که قابلیت باز کردن تصاویر در حالت جعبه نوری (lightbox) برای مشاهده بهتر و همچنین ویرایش تصویر را فراهم می‌کند. این تصاویر ممکن است بسیار بزرگ باشند، بنابراین نمی‌خواهید منتظر بارگذاری آن‌ها بمانید. از این رو کد شما از `async`/`await` برای بارگذاری تصاویر در پس‌زمینه استفاده می‌کند.

اما تصور کنید کد دیگری دارید که فقط زمانی باید اجرا شود که تصویر کاملاً بارگذاری شده باشد، مثلاً دستوری که حذف قرمزی چشم را روی تصویر در جعبه نوری انجام می‌دهد. در حالت ایده‌آل، این دستور حتی اگر تصویر به طور کامل بارگذاری نشده باشد اجرا نمی‌شود، اما برای قابلیت اطمینان بیشتر می‌خواهید مطمئن شوید که این طور است.

بنابراین تابع `fixRedEyeCommand()` که توسط دکمه‌ای که حذف قرمزی چشم را فعال می‌کند فراخوانی می‌شود، قبل از انجام کار خود، مقدار ویژگی `complete` تصویر جعبه نوری را بررسی می‌کند. این موضوع در کد زیر نشان داده شده است.

```js
const lightboxElem = document.querySelector("#lightbox");
const lightboxImgElem = lightboxElem.querySelector("img");
const lightboxControlsElem = lightboxElem.querySelector(".toolbar");

async function loadImage(url, elem) {
  return new Promise((resolve, reject) => {
    elem.onload = () => resolve(elem);
    elem.onerror = reject;
    elem.src = url;
  });
}

async function lightBox(url) {
  lightboxElem.style.display = "block";
  await loadImage("https://some-site.net/huge-image.jpg", lightboxImgElem);
  lightboxControlsElem.disabled = false;
}

// …

function fixRedEyeCommand() {
  if (lightboxElem.style.display === "block" && lightboxImgElem.complete) {
    fixRedEye(lightboxImgElem);
  } else {
    /* نمی‌توان این کار را تا زمانی که تصویر کاملاً بارگذاری نشده شروع کرد */
  }
}
```

## مشخصات

{{Specifications}}

## سازگاری با مرورگر

{{Compat}}