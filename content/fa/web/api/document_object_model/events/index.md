```markdown
---
title: DOM events
short-title: Working with events
slug: Web/API/Document_Object_Model/Events
page-type: guide
spec-urls:
  - https://dom.spec.whatwg.org/#events
  - https://html.spec.whatwg.org/multipage/indices.html#events-2
---

{{DefaultAPISidebar("DOM")}}

[رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events) برای اطلاع‌رسانی به کد در مورد «تغییرات جالب» که ممکن است بر اجرای کد تأثیر بگذارد، فراخوانی می‌شوند. این تغییرات می‌توانند ناشی از تعاملات کاربر مانند استفاده از ماوس یا تغییر اندازه پنجره، تغییرات در وضعیت محیط زیرساخت (مانند باتری کم یا رویدادهای رسانه‌ای از سیستم‌عامل) و دلایل دیگر باشند.

هر رویداد توسط یک شیء که بر اساس رابط {{domxref("Event")}} است، نمایش داده می‌شود و ممکن است فیلدها و/یا توابع سفارشی اضافی برای ارائه اطلاعات درباره آنچه رخ داده است، داشته باشد. مستندات هر رویداد دارای یک جدول (در نزدیکی بالای صفحه) است که شامل پیوندی به رابط رویداد مرتبط و سایر اطلاعات مربوطه می‌باشد. فهرست کاملی از انواع مختلف رویدادها در [Event > Interfaces based on Event](/en-US/docs/Web/API/Event#interfaces_based_on_event) ارائه شده است.

این مبحث یک نمایه از انواع اصلی رویدادهایی که ممکن است به آنها علاقه‌مند باشید (انیمیشن، کلیپ‌بورد، workerها و غیره) به همراه کلاس‌های اصلی که آن انواع رویدادها را پیاده‌سازی می‌کنند، ارائه می‌دهد.

## فهرست رویدادها

<table class="standard-table">
  <tbody>
    <tr>
      <th>نوع رویداد</th>
      <th style="width: 50%">توضیحات</th>
      <th>مستندات</th>
    </tr>
    <tr>
      <td>انیمیشن</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/Web_Animations_API">Web Animation API</a>.
        </p>
        <p>
          برای پاسخ به تغییرات وضعیت انیمیشن (مثلاً زمانی که یک انیمیشن شروع یا پایان می‌یابد) استفاده می‌شود.
        </p>
      </td>
      <td>
        رویدادهای انیمیشن روی
        <a href="/en-US/docs/Web/API/Document#animation_events"
          ><code>Document</code></a
        >،
        <a href="/en-US/docs/Web/API/Window#animation_events"
          ><code>Window</code></a
        >،
        <a href="/en-US/docs/Web/API/HTMLElement#animation_events"
          ><code>HTMLElement</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>واکشی ناهمگام داده</td>
      <td><p>رویدادهای مربوط به واکشی داده.</p></td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/AbortSignal#events"
          ><code>AbortSignal</code></a
        >،
        <a href="/en-US/docs/Web/API/XMLHttpRequest#events"
          ><code>XMLHttpRequest</code></a
        >،
        <a href="/en-US/docs/Web/API/FileReader#events"
          ><code>FileReader</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>کلیپ‌بورد</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/Clipboard_API">Clipboard API</a>.
        </p>
        <p>برای اطلاع از زمانی که محتوا برش، کپی یا چسبانده می‌شود استفاده می‌شود.</p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Document#clipboard_events"
          ><code>Document</code></a
        >،
        <a href="/en-US/docs/Web/API/Element#clipboard_events"
          ><code>Element</code></a
        >،
        <a href="/en-US/docs/Web/API/Window#clipboard_events"
          ><code>Window</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>ترکیب</td>
      <td>
        <p>
          رویدادهای مربوط به ترکیب (composition)؛ ورود متن «به صورت غیرمستقیم» (به جای استفاده از فشار دادن عادی کلیدهای صفحه کلید).
        </p>
        <p>
          به عنوان مثال، متنی که از طریق موتور گفتار به متن وارد می‌شود، یا استفاده از ترکیب‌های کلید ویژه که فشار دادن کلیدها را برای نمایش نویسه‌های جدید در زبانی دیگر تغییر می‌دهد.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Element#composition_events"
          ><code>Element</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>گذار CSS</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/CSS/Guides/Transitions">گذارهای CSS</a>.
        </p>
        <p>
          رویدادهای اطلاع‌رسانی را زمانی که گذارهای CSS شروع، متوقف، لغو و غیره می‌شوند، فراهم می‌کند.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Document#transition_events"
          ><code>Document</code></a
        >،
        <a href="/en-US/docs/Web/API/HTMLElement#transition_events"
          ><code>HTMLElement</code></a
        >،
        <a href="/en-US/docs/Web/API/Window#transition_events"
          ><code>Window</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>پایگاه داده</td>
      <td>
        <p>
          رویدادهای مربوط به عملیات پایگاه داده: باز کردن، بستن، تراکنش‌ها، خطاها و غیره.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/IDBDatabase#events"
          ><code>IDBDatabase</code></a
        >،
        <a href="/en-US/docs/Web/API/IDBOpenDBRequest#events"
          ><code>IDBOpenDBRequest</code></a
        >،
        <a href="/en-US/docs/Web/API/IDBRequest#events"
          ><code>IDBRequest</code></a
        >،
        <a href="/en-US/docs/Web/API/IDBTransaction#events"
          ><code>IDBTransaction</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>جهش DOM</td>
      <td>
        <p>
          رویدادهای مربوط به تغییرات در سلسله‌مراتب و گره‌های مدل شیء سند (DOM).
        </p>
      </td>
      <td>
        <div class="notecard warning">
          <p>
            <strong>هشدار:</strong>
            <a href="/en-US/docs/Web/API/MutationEvent">رویدادهای جهش</a> منسوخ شده‌اند.
            به جای آنها باید از
            <a href="/en-US/docs/Web/API/MutationObserver">نظارت‌کننده‌های جهش</a>
            استفاده کرد.
          </p>
        </div>
      </td>
    </tr>
    <tr>
      <td>کشیدن و رها کردن، چرخ</td>
      <td>
        <p>
          رویدادهای مربوط به استفاده از
          <a href="/en-US/docs/Web/API/HTML_Drag_and_Drop_API"
            >HTML Drag and Drop API</a
          >
          و <a href="/en-US/docs/Web/API/WheelEvent">رویدادهای چرخ</a>.
        </p>
        <p>
          رویدادهای کشیدن و چرخ از رویدادهای ماوس مشتق شده‌اند. اگرچه هنگام استفاده از چرخ ماوس یا کشیدن/رها کردن فراخوانی می‌شوند، ممکن است با سخت‌افزارهای مناسب دیگر نیز استفاده شوند.
        </p>
      </td>
      <td>
        <p>
          رویدادهای کشیدن روی
          <a href="/en-US/docs/Web/API/Document#drag_drop_events"
            ><code>Document</code></a
          >
        </p>
        <p>
          رویدادهای چرخ روی
          <a href="/en-US/docs/Web/API/Element/wheel_event"
            ><code>Element</code></a
          >
        </p>
      </td>
    </tr>
    <tr>
      <td>فوکوس</td>
      <td><p>رویدادهای مربوط به دریافت و از دست دادن فوکوس توسط عناصر.</p></td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Element#focus_events"
          ><code>Element</code></a
        >،
        <a href="/en-US/docs/Web/API/Window#focus_events"><code>Window</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>فرم</td>
      <td>
        <p>رویدادهای مربوط به ساخته شدن، بازنشانی و ارسال فرم‌ها.</p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/HTMLFormElement#events"
          ><code>HTMLFormElement</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>تمام صفحه</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/Fullscreen_API">Fullscreen API</a>.
        </p>
        <p>
          برای اطلاع از زمان انتقال بین حالت تمام صفحه و پنجره‌ای، و همچنین خطاهای رخ داده در طول این انتقال استفاده می‌شود.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Document#fullscreen_events"
          ><code>Document</code></a
        >،
        <a href="/en-US/docs/Web/API/Element#fullscreen_events"
          ><code>Element</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>گیم‌پد</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/Gamepad_API">Gamepad API</a>.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Window#gamepad_events"
          ><code>Window</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>حرکات (ژست‌ها)</td>
      <td>
        <p>
          <a href="/en-US/docs/Web/API/Touch_events">رویدادهای لمسی</a> برای پیاده‌سازی حرکات توصیه می‌شوند.
        </p>
      </td>
      <td>
        <p>
          رویدادهای روی
          <a href="/en-US/docs/Web/API/Document#touch_events"
            ><code>Document</code></a
          >،
          <a href="/en-US/docs/Web/API/Element#touch_events"
            ><code>Element</code></a
          >.
        </p>
        <p>علاوه بر این، تعدادی رویداد حرکتی غیراستاندارد وجود دارد:</p>
        <ul>
          <li>
            رویدادهای غیراستاندارد مخصوص WebKit روی
            <a href="/en-US/docs/Web/API/Element#touch_events"
              ><code>Element</code></a
            >:
            <a href="/en-US/docs/Web/API/Element/gesturestart_event"
              ><code>gesturestart</code></a
            >،
            <a href="/en-US/docs/Web/API/Element/gesturechange_event"
              ><code>gesturechange</code></a
            >،
            <a href="/en-US/docs/Web/API/Element/gestureend_event"
              ><code>gestureend</code></a
            >.
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>تاریخچه</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/History_API">History API</a>.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Window#history_events"
          ><code>Window</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>مدیریت نمایش محتوای عنصر HTML</td>
      <td>
        <p>
          رویدادهای مربوط به تغییر وضعیت یک عنصر نمایشی یا متنی.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/HTMLDetailsElement#events"
          ><code>HTMLDetailsElement</code></a
        >،
        <a href="/en-US/docs/Web/API/HTMLDialogElement#events"
          ><code>HTMLDialogElement</code></a
        >،
        <a href="/en-US/docs/Web/API/HTMLSlotElement#events"
          ><code>HTMLSlotElement</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>ورودی‌ها</td>
      <td>
        <p>
          رویدادهای مربوط به عناصر ورودی HTML مانند
          {{HTMLElement("input")}}، {{HTMLElement("select")}} یا
          {{HTMLElement("textarea")}}.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/HTMLElement#input_events"
          ><code>HTMLElement</code></a
        >،
        <a href="/en-US/docs/Web/API/HTMLInputElement#events"
          ><code>HTMLInputElement</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>صفحه کلید</td>
      <td>
        <p>
          رویدادهای مربوط به استفاده از
          <a href="/en-US/docs/Web/API/KeyboardEvent">صفحه کلید</a>.
        </p>
        <p>برای اطلاع از زمانی که کلیدها بالا، پایین یا فقط فشرده می‌شوند استفاده می‌شود.</p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Document#keyboard_events"
          ><code>Document</code></a
        >،
        <a href="/en-US/docs/Web/API/Element#keyboard_events"
          ><code>Element</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>بارگذاری/بارگیری اسناد</td>
      <td><p>رویدادهای مربوط به بارگذاری و بارگیری اسناد.</p></td>
      <td>
        <p>
          رویدادهای روی
          <a href="/en-US/docs/Web/API/Document#load_unload_events"
            ><code>Document</code></a
          >
          و
          <a href="/en-US/docs/Web/API/Window#load_unload_events"
            ><code>Window</code></a
          >.
        </p>
      </td>
    </tr>
    <tr>
      <td>Manifestها</td>
      <td>
        <p>
          رویدادهای مربوط به نصب
          <a href="/en-US/docs/Web/Progressive_web_apps/Manifest">manifestهای برنامه‌های وب پیشرو</a>.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Window#manifest_events"
          ><code>Window</code></a
        >.
      </td>
    </tr>
    <tr id="media">
      <td>رسانه</td>
      <td>
        <p>
          رویدادهای مربوط به استفاده از رسانه (شامل
          <a href="/en-US/docs/Web/API/Media_Capture_and_Streams_API#events"
            >Media Capture and Streams API</a
          >،
          <a href="/en-US/docs/Web/API/Web_Audio_API#events">Web Audio API</a>،
          <a href="/en-US/docs/Web/API/Picture-in-Picture_API#events"
            >Picture-in-Picture API</a
          > و غیره).
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/ScriptProcessorNode#events"
          ><code>ScriptProcessorNode</code></a
        >،
        <a href="/en-US/docs/Web/API/HTMLMediaElement#events"
          ><code>HTMLMediaElement</code></a
        >،
        <a href="/en-US/docs/Web/API/AudioTrackList#events"
          ><code>AudioTrackList</code></a
        >،
        <a href="/en-US/docs/Web/API/AudioScheduledSourceNode#events"
          ><code>AudioScheduledSourceNode</code></a
        >،
        <a href="/en-US/docs/Web/API/MediaRecorder#events"
          ><code>MediaRecorder</code></a
        >،
        <a href="/en-US/docs/Web/API/MediaStream#events"
          ><code>MediaStream</code></a
        >،
        <a href="/en-US/docs/Web/API/MediaStreamTrack"
          ><code>MediaStreamTrack</code></a
        >،
        <a href="/en-US/docs/Web/API/VideoTrackList#events"
          ><code>VideoTrackList</code></a
        >،
        <a href="/en-US/docs/Web/API/HTMLTrackElement#events"
          ><code>HTMLTrackElement</code></a
        >،
        <a href="/en-US/docs/Web/API/OfflineAudioContext#events"
          ><code>OfflineAudioContext</code></a
        >،
        <a href="/en-US/docs/Web/API/TextTrack#events"><code>TextTrack</code></a
        >،
        <a href="/en-US/docs/Web/API/TextTrackList#events"
          ><code>TextTrackList</code></a
        >،
        <a href="/en-US/docs/Web/HTML/Reference/Elements/audio#events">Element/audio</a>،
        <a href="/en-US/docs/Web/HTML/Reference/Elements/video#events">Element/video</a>.
      </td>
    </tr>
    <tr>
      <td>پیام‌رسانی</td>
      <td>
        <p>
          رویدادهای مربوط به دریافت پیام توسط یک پنجره از یک زمینه مرور دیگر.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Window#messaging_events"
          ><code>Window</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>ماوس</td>
      <td>
        <p>
          رویدادهای مربوط به استفاده از
          <a href="/en-US/docs/Web/API/MouseEvent">ماوس کامپیوتر</a>.
        </p>
        <p>
          برای اطلاع از زمانی که ماوس کلیک، دوبار کلیک، رویدادهای بالا و پایین، کلیک راست، حرکت به داخل و خارج از یک عنصر، انتخاب متن و غیره می‌شود استفاده می‌شود.
        </p>
        <p>
          رویدادهای اشاره‌گر (Pointer events) یک جایگزین مستقل از سخت‌افزار برای رویدادهای ماوس ارائه می‌دهند. رویدادهای کشیدن و چرخ از رویدادهای ماوس مشتق شده‌اند.
        </p>
      </td>
      <td>
        رویدادهای ماوس روی
        <a href="/en-US/docs/Web/API/Element#mouse_events"
          ><code>Element</code></a
        >
      </td>
    </tr>
    <tr>
      <td>شبکه/اتصال</td>
      <td><p>رویدادهای مربوط به برقراری و از دست دادن اتصال شبکه.</p></td>
      <td>
        <p>
          رویدادهای روی
          <a href="/en-US/docs/Web/API/Window#connection_events"
            ><code>Window</code></a
          >.
        </p>
        <p>
          رویدادهای روی
          <a href="/en-US/docs/Web/API/NetworkInformation#event_handler"
            ><code>NetworkInformation</code></a
          >
          (<a href="/en-US/docs/Web/API/Network_Information_API"
            >Network Information API</a
          >).
        </p>
      </td>
    </tr>
    <tr>
      <td>پرداخت‌ها</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/Payment_Request_API"
            >Payment Request API</a
          >.
        </p>
      </td>
      <td>
        <p>
          رویدادهای روی
          <a href="/en-US/docs/Web/API/PaymentRequest#events"
            ><code>PaymentRequest</code></a
          >،
          <a href="/en-US/docs/Web/API/PaymentResponse#events"
            ><code>PaymentResponse</code></a
          >.
        </p>
      </td>
    </tr>
    <tr>
      <td>عملکرد</td>
      <td>
        <p>
          رویدادهای مربوط به هر مشخصه مرتبط با عملکرد که در
          <a href="/en-US/docs/Web/API/Performance_API"
            >Performance APIs</a
          > گروه‌بندی شده‌اند.
        </p>
      </td>
      <td>
        <p>
          رویدادهای روی
          <a href="/en-US/docs/Web/API/Performance#events"
            ><code>Performance</code></a
          >.
        </p>
      </td>
    </tr>
    <tr>
      <td>اشاره‌گر</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/Pointer_events">Pointer Events API</a>.
        </p>
        <p>
          اطلاع‌رسانی مستقل از سخت‌افزار از دستگاه‌های اشاره‌گر شامل ماوس، لمسی، قلم/استایلوس را فراهم می‌کند.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Document#pointer_events"
          ><code>Document</code></a
        >،
        <a href="/en-US/docs/Web/API/HTMLElement#pointer_events"
          ><code>HTMLElement</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>چاپ</td>
      <td><p>رویدادهای مربوط به چاپ.</p></td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Window#print_events"><code>Window</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>رد شدن Promise</td>
      <td>
        <p>
          رویدادهایی که به زمینه اسکریپت سراسری ارسال می‌شوند وقتی هر promise جاوااسکریپتی رد می‌شود.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Window#promise_rejection_events"
          ><code>Window</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>Socketها</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/WebSockets_API">WebSockets API</a>.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/WebSocket#events"><code>WebSocket</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>SVG</td>
      <td><p>رویدادهای مربوط به تصاویر SVG.</p></td>
      <td>
        <p>
          رویدادهای روی
          <a href="/en-US/docs/Web/API/SVGElement#events"
            ><code>SVGElement</code></a
          >،
          <a href="/en-US/docs/Web/API/SVGAnimationElement#events"
            ><code>SVGAnimationElement</code></a
          >،
          <a href="/en-US/docs/Web/API/SVGGraphicsElement#events"
            ><code>SVGGraphicsElement</code></a
          >.
        </p>
      </td>
    </tr>
    <tr>
      <td>انتخاب متن</td>
      <td>
        <p>
          رویدادهای <a href="/en-US/docs/Web/API/Selection">Selection API</a> مربوط به انتخاب متن.
        </p>
      </td>
      <td>
        <p>
          رویداد (<code>selectionchange</code>) روی
          {{domxref("HTMLTextAreaElement/selectionchange_event", "HTMLTextAreaElement")}}،
          {{domxref("HTMLInputElement/selectionchange_event", "HTMLInputElement")}}.
        </p>
      </td>
    </tr>
    <tr>
      <td>لمسی</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/Touch_events">Touch Events API</a>.
        </p>
        <p>
          رویدادهای اطلاع‌رسانی از تعامل با صفحه لمسی (یعنی با استفاده از انگشت یا قلم) را فراهم می‌کند. مربوط به
          <a href="/en-US/docs/Web/API/Force_Touch_events#events"
            >Force Touch API</a
          > نیست.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/Document#touch_events"
          ><code>Document</code></a
        >،
        <a href="/en-US/docs/Web/API/Element#touch_events"
          ><code>Element</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>واقعیت مجازی</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/WebXR_Device_API">WebXR Device API</a>.
        </p>
        <div class="notecard warning">
          <p>
            <strong>هشدار:</strong>
            <a href="/en-US/docs/Web/API/WebVR_API">WebVR API</a> (و
            <a href="/en-US/docs/Web/API/WebVR_API#window_events"
              >رویدادهای <code>Window</code> مرتبط</a
            >) منسوخ شده‌اند.
          </p>
        </div>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/XRSystem#events"><code>XRSystem</code></a
        >،
        <a href="/en-US/docs/Web/API/XRSession#events"><code>XRSession</code></a
        >،
        <a href="/en-US/docs/Web/API/XRReferenceSpace#events"
          ><code>XRReferenceSpace</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>RTC (ارتباط بلادرنگ)</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/WebRTC_API">WebRTC API</a>.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/RTCDataChannel#events"
          ><code>RTCDataChannel</code></a
        >،
        <a href="/en-US/docs/Web/API/RTCDTMFSender#events"
          ><code>RTCDTMFSender</code></a
        >،
        <a href="/en-US/docs/Web/API/RTCIceTransport#events"
          ><code>RTCIceTransport</code></a
        >،
        <a href="/en-US/docs/Web/API/RTCPeerConnection#events"
          ><code>RTCPeerConnection</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>رویدادهای ارسالی از سرور</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/Server-sent_events"
            >server sent events API</a
          >.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/EventSource#events"
          ><code>EventSource</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>گفتار</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/Web_Speech_API">Web Speech API</a>.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/SpeechSynthesisUtterance#events"
          ><code>SpeechSynthesisUtterance</code></a
        >.
      </td>
    </tr>
    <tr>
      <td>Workerها</td>
      <td>
        <p>
          رویدادهای مربوط به
          <a href="/en-US/docs/Web/API/Web_Workers_API">Web Workers API</a>،
          <a href="/en-US/docs/Web/API/Service_Worker_API">Service Worker API</a
          >،
          <a href="/en-US/docs/Web/API/Broadcast_Channel_API"
            >Broadcast Channel API</a
          >، و
          <a href="/en-US/docs/Web/API/Channel_Messaging_API"
            >Channel Messaging API</a
          >.
        </p>
        <p>
          برای پاسخ به پیام‌های جدید و خطاهای ارسال پیام استفاده می‌شود. Service workerها همچنین می‌توانند از رویدادهای دیگر، از جمله اعلان‌های فشاری، کلیک کاربر روی اعلان‌های نمایش داده شده، باطل شدن اشتراک فشاری، حذف موارد از فهرست محتوا و غیره مطلع شوند.
        </p>
      </td>
      <td>
        رویدادهای روی
        <a href="/en-US/docs/Web/API/ServiceWorkerGlobalScope#events"
          ><code>ServiceWorkerGlobalScope</code></a
        >،
        <a href="/en-US/docs/Web/API/DedicatedWorkerGlobalScope#events"
          ><code>DedicatedWorkerGlobalScope</code></a
        >،
        <a href="/en-US/docs/Web/API/SharedWorkerGlobalScope#events"
          ><code>SharedWorkerGlobalScope</code></a
        >،
        <a href="/en-US/docs/Web/API/WorkerGlobalScope#events"
          ><code>WorkerGlobalScope</code></a
        >،
        <a href="/en-US/docs/Web/API/Worker#events"
          ><code>Worker</code></a
        >،
        <a href="/en-US/docs/Web/API/BroadcastChannel#events"
          ><code>BroadcastChannel</code></a
        >،
        <a href="/en-US/docs/Web/API/MessagePort#events"
          ><code>MessagePort</code></a
        >.
      </td>
    </tr>
  </tbody>
</table>

## ایجاد و ارسال رویدادها

علاوه بر رویدادهایی که توسط رابط‌های داخلی فراخوانی می‌شوند، می‌توانید خودتان رویدادهای DOM ایجاد و ارسال کنید. این رویدادها معمولاً _رویدادهای مصنوعی_ نامیده می‌شوند، در مقابل رویدادهایی که توسط مرورگر فراخوانی می‌شوند.

### ایجاد رویدادهای سفارشی

رویدادها را می‌توان با سازنده [`Event`](/en-US/docs/Web/API/Event) به صورت زیر ایجاد کرد:

```js
const event = new Event("build");

// گوش دادن به رویداد
elem.addEventListener("build", (e) => {
  /* … */
});

// ارسال رویداد
elem.dispatchEvent(event);
```

این مثال کد از متد [EventTarget.dispatchEvent()](/en-US/docs/Web/API/EventTarget/dispatchEvent) استفاده می‌کند.

### افزودن داده سفارشی – CustomEvent()

برای افزودن داده بیشتر به شیء رویداد، رابط [CustomEvent](/en-US/docs/Web/API/CustomEvent) وجود دارد و از ویژگی **detail** می‌توان برای ارسال داده سفارشی استفاده کرد.
به عنوان مثال، رویداد می‌تواند به صورت زیر ایجاد شود:

```js
const event = new CustomEvent("build", { detail: elem.dataset.time });
```

این کار سپس به شما امکان می‌دهد به داده اضافی در شنونده رویداد دسترسی داشته باشید:

```js
function eventHandler(e) {
  console.log(`زمان: ${e.detail}`);
}
```

### افزودن داده سفارشی – زیرکلاس‌سازی Event

رابط [`Event`](/en-US/docs/Web/API/Event) همچنین می‌تواند زیرکلاس‌سازی شود. این کار به ویژه برای استفاده مجدد، یا برای داده سفارشی پیچیده‌تر، یا حتی افزودن متد به رویداد مفید است.

```js
class BuildEvent extends Event {
  #buildTime;

  constructor(buildTime) {
    super("build");
    this.#buildTime = buildTime;
  }

  get buildTime() {
    return this.#buildTime;
  }
}
```

این مثال کد یک کلاس `BuildEvent` با یک ویژگی فقط خواندنی و یک نوع رویداد ثابت تعریف می‌کند.

سپس رویداد می‌تواند به صورت زیر ایجاد شود:

```js
const event = new BuildEvent(elem.dataset.time);
```

سپس می‌توان به داده اضافی در شنونده‌های رویداد با استفاده از ویژگی‌های سفارشی دسترسی داشت:

```js
function eventHandler(e) {
  console.log(`زمان: ${e.buildTime}`);
}
```

### حباب زدن رویداد

اغلب مطلوب است که یک رویداد از یک عنصر فرزند تحریک شود و یک عنصر ancestor آن را دریافت کند. به صورت اختیاری، می‌توانید داده را با رویداد همراه کنید:

```html
<form>
  <textarea></textarea>
</form>
```

```js
const form = document.querySelector("form");
const textarea = document.querySelector("textarea");

// یک رویداد جدید ایجاد کنید، اجازه حباب زدن بدهید، و هر داده‌ای را که می‌خواهید به ویژگی "detail" ارسال کنید، ارائه دهید
const eventAwesome = new CustomEvent("awesome", {
  bubbles: true,
  detail: { text: () => textarea.value },
});

// عنصر فرم به رویداد سفارشی "awesome" گوش می‌دهد و سپس خروجی متد text() ارسال شده را در کنسول چاپ می‌کند
form.addEventListener("awesome", (e) => console.log(e.detail.text()));

// با تایپ کاربر، textarea داخل فرم رویداد را برای فراخوانی، با استفاده از خودش به عنوان نقطه شروع، ارسال/تحریک می‌کند
textarea.addEventListener("input", (e) => e.target.dispatchEvent(eventAwesome));
```

### ایجاد و ارسال رویدادها به صورت پویا

عناصر می‌توانند به رویدادهایی که هنوز ایجاد نشده‌اند گوش دهند:

```html
<form>
  <textarea></textarea>
</form>
```

```js
const form = document.querySelector("form");
const textarea = document.querySelector("textarea");

form.addEventListener("awesome", (e) => console.log(e.detail.text()));

textarea.addEventListener("input", function () {
  // ایجاد و ارسال/تحریک یک رویداد در لحظه
  // توجه: به صورت اختیاری، ما از "عبارت تابع" (به جای "عبارت تابع پیکانی") استفاده کرده‌ایم تا "this" نشان‌دهنده عنصر باشد
  this.dispatchEvent(
    new CustomEvent("awesome", {
      bubbles: true,
      detail: { text: () => textarea.value },
    }),
  );
});
```

## تحریک رویدادهای داخلی

این مثال شبیه‌سازی یک کلیک (یعنی تولید برنامه‌نویسی یک رویداد کلیک) روی یک چک‌باکس با استفاده از روش‌های DOM را نشان می‌دهد. [نمونه را در عمل مشاهده کنید.](https://mdn.dev/archives/media/samples/domref/dispatchEvent.html)

```js
function simulateClick() {
  const event = new MouseEvent("click", {
    view: window,
    bubbles: true,
    cancelable: true,
  });
  const cb = document.getElementById("checkbox");
  const cancelled = !cb.dispatchEvent(event);

  if (cancelled) {
    // یک هندلر preventDefault را فراخوانی کرد.
    alert("لغو شد");
  } else {
    // هیچ یک از هندلرها preventDefault را فراخوانی نکردند.
    alert("لغو نشد");
  }
}
```

## ثبت هندلرهای رویداد

دو رویکرد توصیه شده برای ثبت هندلرها وجود دارد. کد هندلر رویداد می‌تواند با اختصاص آن به ویژگی _onevent_ متناظر عنصر هدف یا با ثبت هندلر به عنوان یک شنونده برای عنصر با استفاده از متد {{domxref("EventTarget.addEventListener", "addEventListener()")}}، به گونه‌ای عمل کند که با تحریک رویداد اجرا شود. در هر دو حالت، هندلر یک شیء دریافت می‌کند که با [رابط `Event`](/en-US/docs/Web/API/Event) (یا یک [رابط مشتق شده](/en-US/docs/Web/API/Event#interfaces_based_on_event)) مطابقت دارد. تفاوت اصلی این است که می‌توان چندین هندلر رویداد را با استفاده از روش‌های شنونده رویداد اضافه (یا حذف) کرد.

> [!WARNING]
> رویکرد سوم برای تنظیم هندلرهای رویداد با استفاده از ویژگی‌های HTML onevent توصیه نمی‌شود! آنها نشانه‌گذاری را حجیم می‌کنند و آن را کم‌خواناتر و دشوارتر برای اشکال‌زدایی می‌سازند. برای اطلاعات بیشتر، به [هندلرهای رویداد درون‌خطی](/en-US/docs/Learn_web_development/Core/Scripting/Events#inline_event_handlers_—_dont_use_these) مراجعه کنید.

### استفاده از ویژگی‌های onevent

طبق قرارداد، اشیاء جاوااسکریپتی که رویدادها را فراخوانی می‌کنند، ویژگی‌های "onevent" متناظر دارند (با پیشوند "on" به نام رویداد نامگذاری می‌شوند). این ویژگی‌ها برای اجرای کد هندلر مرتبط در هنگام فراخوانی رویداد فراخوانی می‌شوند و همچنین ممکن است مستقیماً توسط کد شما فراخوانی شوند.

برای تنظیم کد هندلر رویداد، می‌توانید آن را به ویژگی onevent مناسب اختصاص دهید. فقط یک هندلر رویداد می‌تواند برای هر رویداد در یک عنصر اختصاص داده شود. در صورت نیاز، می‌توان هندلر را با اختصاص یک تابع دیگر به همان ویژگی جایگزین کرد.

مثال زیر نحوه تنظیم یک تابع `greet()` برای رویداد `click` با استفاده از ویژگی `onclick` را نشان می‌دهد.

```js
const btn = document.querySelector("button");

function greet(event) {
  console.log("greet:", event);
}

btn.onclick = greet;
```

توجه داشته باشید که یک شیء نشان‌دهنده رویداد به عنوان اولین آرگومان به هندلر رویداد ارسال می‌شود. این شیء رویداد یا رابط {{domxref("Event")}} را پیاده‌سازی می‌کند یا از آن مشتق شده است.

### EventTarget.addEventListener

منعطف‌ترین راه برای تنظیم یک هندلر رویداد روی یک عنصر، استفاده از متد {{domxref("EventTarget.addEventListener")}} است. این رویکرد امکان اختصاص چندین شنونده به یک عنصر را فراهم می‌کند و در صورت نیاز، امکان _حذف_ شنونده‌ها را با استفاده از {{domxref("EventTarget.removeEventListener")}} فراهم می‌کند.

> [!NOTE]
> توانایی افزودن و حذف هندلرهای رویداد به شما این امکان را می‌دهد که مثلاً یک دکمه در شرایط مختلف اقدامات متفاوتی انجام دهد. علاوه بر این، در برنامه‌های پیچیده‌تر، پاکسازی هندلرهای رویداد قدیمی/استفاده نشده می‌تواند کارایی را بهبود بخشد.

مثال زیر نحوه تنظیم یک تابع `greet()` به عنوان شنونده/هندلر رویداد برای رویداد `click` را نشان می‌دهد (در صورت تمایل می‌توانید به جای یک تابع نام‌دار از یک عبارت تابع ناشناس استفاده کنید). دوباره توجه کنید که رویداد به عنوان اولین آرگومان به هندلر رویداد ارسال می‌شود.

```js
const btn = document.querySelector("button");

function greet(event) {
  console.log("greet:", event);
}

btn.addEventListener("click", greet);
```

این متد همچنین می‌تواند آرگومان‌ها/گزینه‌های اضافی برای کنترل جنبه‌های نحوه ضبط و حذف رویدادها دریافت کند. اطلاعات بیشتر در صفحه مرجع {{domxref("EventTarget.addEventListener")}} یافت می‌شود.

#### استفاده از AbortSignal

یک ویژگی قابل توجه شنونده رویداد، توانایی استفاده از یک سیگنال قطع (abort signal) برای پاکسازی همزمان چندین هندلر رویداد است.

این کار با ارسال همان {{domxref("AbortSignal")}} به فراخوانی {{domxref("EventTarget/addEventListener()", "addEventListener()")}} برای همه هندلرهای رویدادی که می‌خواهید بتوانید با هم حذف کنید، انجام می‌شود. سپس می‌توانید {{domxref("AbortController/abort()", "abort()")}} را روی کنترل‌کننده‌ای که مالک `AbortSignal` است فراخوانی کنید، و تمام هندلرهای رویدادی که با آن سیگنال اضافه شده‌اند را حذف خواهد کرد. به عنوان مثال، برای افزودن یک هندلر رویداد که می‌توانیم با یک `AbortSignal` حذف کنیم:

```js
const controller = new AbortController();

btn.addEventListener(
  "click",
  (event) => {
    console.log("greet:", event);
  },
  { signal: controller.signal },
); // یک AbortSignal به این هندلر ارسال کنید
```

سپس این هندلر رویداد می‌تواند به این صورت حذف شود:

```js
controller.abort(); // هر/همه هندلرهای رویداد مرتبط با این کنترل‌کننده را حذف می‌کند
```

### تعامل چندین هندلر رویداد

ویژگی IDL `onevent` (مثلاً `element.onclick = ...`) و ویژگی محتوای HTML `onevent` (مثلاً `<button onclick="...">`) هر دو یک شکاف هندلر واحد را هدف قرار می‌دهند. HTML قبل از اینکه جاوااسکریپت بتواند به همان عنصر دسترسی پیدا کند، بارگذاری می‌شود، بنابراین معمولاً جاوااسکریپت آنچه را که در HTML مشخص شده است جایگزین می‌کند. هندلرهای اضافه شده با {{domxref("EventTarget.addEventListener", "addEventListener()")}} مستقل هستند. استفاده از `onevent` شنونده‌های اضافه شده با `addEventListener()` را حذف یا جایگزین نمی‌کند، و بالعکس.

هنگامی که یک رویداد ارسال می‌شود، شنونده‌ها در فازها فراخوانی می‌شوند. دو فاز وجود دارد: _ضبط (capture)_ و _حباب (bubble)_. در فاز ضبط، رویداد از بالاترین عنصر ancestor شروع می‌شود و درخت DOM را به سمت پایین حرکت می‌کند تا به هدف برسد. در فاز حباب، رویداد در جهت مخالف حرکت می‌کند. شنونده‌های رویداد به طور پیش‌فرض در فاز حباب گوش می‌دهند و می‌توانند با مشخص کردن `capture: true` با `addEventListener()` در فاز ضبط گوش دهند. در یک فاز، شنونده‌ها به ترتیب ثبت خود اجرا می‌شوند. هندلر `onevent` اولین باری که غیر null می‌شود ثبت می‌شود؛ اختصاص‌های بعدی فقط callback آن را تغییر می‌دهند، نه موقعیت آن را در ترتیب.

فراخوانی {{domxref("Event.stopPropagation()")}} از فراخوانی شنونده‌ها روی عناصر دیگر در ادامه زنجیره انتشار جلوگیری می‌کند. {{domxref("Event.stopImmediatePropagation()")}} همچنین از فراخوانی شنونده‌های باقی‌مانده روی همان عنصر جلوگیری می‌کند.

## مشخصات

{{Specifications}}

## همچنین ببینید

- [مقدمه‌ای بر رویدادها](/en-US/docs/Learn_web_development/Core/Scripting/Events)
- [حباب زدن رویداد](/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling)
```