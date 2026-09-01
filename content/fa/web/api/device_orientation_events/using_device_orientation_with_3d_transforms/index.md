---
title: Using device orientation with 3D transforms
slug: Web/API/Device_orientation_events/Using_device_orientation_with_3D_transforms
page-type: guide
---

{{DefaultAPISidebar("Device Orientation Events")}}

این مقاله نکاتی را در مورد چگونگی استفاده از اطلاعات جهت‌گیری دستگاه در کنار تبدیل‌های سه‌بعدی CSS ارائه می‌دهد.

## استفاده از جهت‌گیری برای چرخش یک عنصر

ساده‌ترین راه برای تبدیل [داده‌های جهت‌گیری](/en-US/docs/Web/API/Window/deviceorientation_event) به یک [تبدیل سه‌بعدی](/en-US/docs/Web/CSS/Reference/Properties/transform) اساساً استفاده از مقادیر `alpha`، `gamma` و `beta` به عنوان مقادیر `rotateZ`، `rotateX` و `rotateY` است.

با این حال، مهم است که به خاطر داشته باشید [سیستم مختصات جهت‌گیری دستگاه](/en-US/docs/Web/API/Device_orientation_events/Orientation_and_motion_data_explained) با [سیستم مختصات CSS](/en-US/docs/Web/API/CSSOM_view_API/Coordinate_systems) متفاوت است. به طور مشخص، اولی یک سیستم [راست‌دست (right-handed)](https://en.wikipedia.org/wiki/Right-hand_rule) است و محور Y آن به سمت بالا مثبت است، در حالی که دومی یک سیستم مختصات چپ‌دست (left-handed) است که محور Y آن به سمت پایین مثبت است. علاوه بر این، چرخش‌های زاویه‌ای جهت‌گیری دستگاه باید همیشه به ترتیب Z - X' - Y'' انجام شوند که با ترتیب برخی از [تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms) مطابقت ندارد. در ادامه برخی از پیامدهای عملی این تفاوت‌ها آورده شده است:

- ترتیب چرخش‌های زاویه‌ای مهم است، بنابراین مطمئن شوید که چرخش‌های آلفا، بتا و گاما به این ترتیب اعمال می‌شوند.
- تبدیل CSS {{cssxref("transform-function/rotate3d", "rotate3d()")}} و توابع [`DOMMatrixReadOnly.rotate()`](/en-US/docs/Web/API/DOMMatrixReadOnly/rotate) و [`DOMMatrix.rotateSelf()`](/en-US/docs/Web/API/DOMMatrix/rotateSelf) چرخش‌های زاویه‌ای را به ترتیب Z - Y' - X'' اعمال می‌کنند، بنابراین امکان اعمال چرخش‌های آلفا، بتا و گاما به ترتیب صحیح با یک فراخوانی واحد از هیچ‌کدام وجود ندارد. در عوض، باید هر محور را به صورت جداگانه و به ترتیب صحیح بچرخانید.
- به دلیل تفاوت‌های سیستم مختصات که در بالا ذکر شد، هنگام نگاه به سمت مبدأ، چرخش‌ها در CSS در جهت عقربه‌های ساعت و در مشخصات جهت‌گیری دستگاه در خلاف جهت عقربه‌های ساعت اعمال می‌شوند. این بدان معناست که آلفا و بتا باید معکوس شوند (چرخش‌های حول Z و X)، زیرا در دو سیستم مختصات به جهات مختلفی اشاره می‌کنند. با این حال، گاما (چرخش حول Y) باید به همان صورت باقی بماند.

  در اینجا یک قطعه کد برای جمع‌بندی آورده شده است:

  ```js
  const elem = document.getElementById("view3d");

  window.addEventListener("deviceorientation", (e) => {
    elem.style.transform = `rotateZ(${-e.alpha}deg) rotateX(${-e.beta}deg) rotateY(${
      e.gamma
    }deg)`;
  });
  ```

## تبدیل از زوایای `rotate3d()` به زوایای `deviceorientation`

اگر روزی نیاز به تبدیل یک زاویه-محور rotate3d به زوایای [اولر (Euler angles)](https://en.wikipedia.org/wiki/Euler_angles) جهت‌گیری دستگاه (که توسط `deviceorientation` استفاده می‌شود) داشتید، می‌توانید از الگوریتم زیر استفاده کنید:

```js
// convert a rotate3d axis-angle to deviceorientation angles
function orient(aa) {
  const x = aa.x,
    y = aa.y,
    z = aa.z,
    a = aa.a,
    c = Math.cos(aa.a),
    s = Math.sin(aa.a),
    t = 1 - c,
    // axis-angle to rotation matrix
    rm00 = c + x * x * t,
    rm10 = z * s + y * x * t,
    rm20 = -y * s + z * x * t,
    rm01 = -z * s + x * y * t,
    rm11 = c + y * y * t,
    rm21 = x * s + z * y * t,
    rm02 = y * s + x * z * t,
    rm12 = -x * s + y * z * t,
    rm22 = c + z * z * t,
    TO_DEG = 180 / Math.PI,
    ea = [],
    n = Math.hypot(rm22, rm20);

  // rotation matrix to Euler angles
  ea[1] = Math.atan2(-rm21, n);

  if (n > 0.001) {
    ea[0] = Math.atan2(rm01, rm11);
    ea[2] = Math.atan2(rm20, rm22);
  } else {
    ea[0] = 0;
    ea[2] = (rm21 > 0 ? 1 : -1) * Math.atan2(-rm10, rm00);
  }

  return {
    alpha: -ea[0] * TO_DEG - 180,
    beta: -ea[1] * TO_DEG,
    gamma: ea[2] * TO_DEG,
  };
}
```

## همچنین ببینید

- [استفاده از تبدیل‌های CSS](/en-US/docs/Web/CSS/Guides/Transforms/Using)
- [تشخیص جهت‌گیری دستگاه](/en-US/docs/Web/API/Device_orientation_events/Detecting_device_orientation)