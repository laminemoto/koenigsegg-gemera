بخش اول: توصیف ماشین (جایگزین متن دستبند)

متن‌های Hero و Features را با توصیف Koenigsegg Gemera جایگزین کنید. این خودرو یک هایپرکار ۴ صندلی هیبریدی است که در سال ۲۰۲۰ معرفی شد — ترکیبی از فناوری پیشرفته و طراحی مینیمال، که دقیقاً با حال‌وهوای صفحه شما هماهنگ است.

```html
<!-- Hero -->
<div class="hero-badge">Hypercar · Hybrid · 2020</div>
<h1>Koenigsegg Gemera<br>هایپرکار نسل جدید</h1>
<p>نخستین هایپرکار ۴ صندلی جهان با پیشرانه هیبریدی ۱۷۰۰ اسب بخاری — ترکیبی از مهندسی سوئدی و فناوری آینده.</p>

<!-- Features -->
<h2 class="features-title">مشخصات کلیدی</h2>
<p class="features-sub">نگاهی به آنچه Gemera را متفاوت می‌کند.</p>

<article class="feature">
  <div class="feature-icon">⚡</div>
  <h3>پیشرانه هیبریدی</h3>
  <p>موتور ۲.۰ لیتری توربو سه‌سیلندر + سه موتور الکتریکی، مجموعاً ۱۷۰۰ اسب بخار.</p>
</article>
<article class="feature">
  <div class="feature-icon">🏎</div>
  <h3>شتاب خیره‌کننده</h3>
  <p>۰ تا ۱۰۰ کیلومتر در ۱.۹ ثانیه — سریع‌تر از بسیاری از هایپرکارهای دو صندلی.</p>
</article>
<article class="feature">
  <div class="feature-icon">🔋</div>
  <h3>برد الکتریکی</h3>
  <p>تا ۵۰ کیلومتر پیمایش تمام‌الکتریکی، مناسب حرکت شهری بی‌صدا.</p>
</article>
```

برچسب فازها را هم می‌توانید متناسب کنید: «در حال چرخش ۳۶۰°…» → «کاوش در طراحی…»، «زوم روی جزئیات…» → «نزدیک‌تر به جزئیات…»، «محو شدن…» → «آشنایی با مشخصات…».

---

بخش دوم: مکانیزم‌های انیمیشنی قابل افزودن

هدف شما آشنایی با مکانیزم‌هاست، پس این لیست را بر اساس سطح پیچیدگی و ابزار دسته‌بندی کردم. هر مکانیزم با یک توضیح کوتاه از «چه چیزی را نشان می‌دهد» و «با چه ابزاری».

دسته ۱: مکانیزم‌های اسکرول (Scroll-driven)

این‌ها با GSAP ScrollTrigger ساخته می‌شوند و قلب تجربه شما هستند.

1. Pin کردن صحنه (Scroll Pinning) — ماشین در مرکز صفحه ثابت می‌ماند و فقط انیمیشن پیش می‌رود. کاربر حس می‌کند «درون صحنه» است. ScrollTrigger.create({ pin: true }).
2. Horizontal Scroll — با اسکرول عمودی، محتوا افقی حرکت می‌کند. مناسب برای نمایش «خط زمانی» مشخصات خودرو. containerAnimation.
3. Scrub معکوس‌پذیر — کاربر با اسکرول به بالا، انیمیشن را دقیقاً برعکس می‌بیند. همان scrub: 1 که داریم، ولی می‌توان روی هر property جداگانه اعمال کرد.
4. Snap به نقاط کلیدی — اسکرول به نزدیک‌ترین «ایستگاه» می‌چسبد (مثلاً ۰°، ۹۰°، ۱۸۰°، ۲۷۰°). حس «قدم به قدم» می‌دهد. snap: [0, 0.25, 0.5, 0.75, 1].
5. Parallax چندلایه — لایه‌های پس‌زمینه با سرعت متفاوت حرکت می‌کنند (نور، ذرات، متن). عمق می‌دهد. data-speed با ScrollTrigger.
6. Reveal تدریجی متن (Split Text) — متن کلمه‌به‌کلمه یا حرف‌به‌حرف با اسکرول ظاهر می‌شود. کتابخانه SplitType + GSAP.
7. Scroll Progress Bar — نوار نازک بالای صفحه که پیشرفت اسکرول را نشان می‌دهد. ساده ولی حس کنترل می‌دهد.
8. Section Transition با Clip-path — بخش‌ها با یک ماسک دایره‌ای یا خطی از هم جدا می‌شوند. clip-path + ScrollTrigger.

دسته ۲: مکانیزم‌های دوربین و مدل سه‌بعدی

9. Camera Path Animation — دوربین روی یک مسیر از پیش تعریف‌شده (مثلاً دور خودرو) حرکت می‌کند. CatmullRomCurve3 + GSAP.
10. Camera Dolly Zoom (Vertigo Effect) — زوم داخل همزمان با عقب رفتن دوربین — افکت سینمایی معروف هیچکاک. مناسب لحظه «مکث».
11. Orbit Auto + Manual Toggle — چرخش خودکار، ولی به محض لمس/کلیک کاربر، کنترل به دست او می‌افتد. OrbitControls.autoRotate + event listener.
12. Focus on Part (Raycasting) — کاربر روی یک بخش (چرخ، درب، سنسور) کلیک می‌کند و دوربین به آن زوم می‌کند. THREE.Raycaster + GSAP به موقعیت جدید.
13. Exploded View — قطعات خودرو از هم جدا می‌شوند و کنار هم می‌ایستند (مثل نمای انفجاری مهندسی). نیازمند مدل با اجزای نام‌گذاری‌شده.
14. Ghost/Transparent Mode — بدنه خودرو نیمه‌شفاف می‌شود تا موتور یا کابین دیده شود. تغییر material.opacity روی بدنه.
15. Wireframe → Solid Transition — خودرو از حالت سیمی به حالت جامد تبدیل می‌شود. مناسب لحظه معرفی. تغییر material.wireframe.
16. Material Morph — رنگ بدنه از مشکی به سبز برند، یا از مات به براق تغییر می‌کند. material.color.lerp یا GSAP روی material.color.
17. Environment Swap — پس‌زمینه مدل از استودیو تاریک به جاده یا پیست تغییر می‌کند. scene.environment + HDRI.
18. Wheel Spin (چرخش چرخ) — چرخ‌ها با سرعت مشخص می‌چرخند، حس حرکت ایستا می‌دهد. wheel.rotation.x += speed * dt.
19. Door Open Animation — درب‌ها با GSAP باز/بسته می‌شوند. نیازمند getObjectByName('Door_L') و مدل جدا.
20. Hood/Trunk Open — مشابه درب، برای کاپوت و صندوق عقب.
21. Suspension Bounce — خودرو با یک ضربه ملایم بالا-پایین می‌رود، حس وزن. group.position.y = sin(t) * 0.02.

دسته ۳: مکانیزم‌های تعامل کاربر (Interaction)

22. Hover Highlight — با هاور روی هر بخش، آن بخش برجسته می‌شود (emissive). Raycaster + material.emissive.
23. Click to Zoom Part — کلیک روی یک بخش، دوربین به آن نزدیک می‌شود و یک کادر توضیح باز می‌شود.
24. Drag to Rotate (Mobile) — با کشیدن انگشت روی مدل، کاربر خودش می‌چرخاند. pointerdown / pointermove روی canvas.
25. Pinch to Zoom (Mobile) — با دو انگشت، زوم on the model. touchmove با محاسبه فاصله.
26. Gyroscope Tilt (Mobile) — با کج کردن گوشی، نور یا دوربین کمی تغییر می‌کند. DeviceOrientationEvent — جذاب برای نمایش «حس فیزیکی».
27. Swipe to Change Color — با سوایپ، رنگ بدنه تغییر می‌کند. GSAP.to(material.color, ...).
28. Keyboard Navigation — با کلیدهای جهت، چرخش و زوم. برای دسترسی‌پذیری.

دسته ۴: مکانیزم‌های بصری و افکت

29. Particle System (ذرات) — ذرات نورانی اطراف خودرو شناورند، حس «فناوری». THREE.Points با shader ساده.
30. Speed Lines — خطوط نوری که در لحظه «شتاب» از کنار خودرو رد می‌شوند.
31. Light Trail — دنباله نور پشت چرخ‌ها یا LED. مناسب نمای شب.
32. Volumetric Light — پرتوهای نور از بالا (مثل نورافکن). SpotLight + volumetric shader.
33. Bloom / Glow — درخشش روی LED و صفحه‌ها. UnrealBloomPass از EffectComposer.
34. Depth of Field — بخش‌های دور تار می‌شوند، تمرکز روی خودرو. BokehPass.
35. Chromatic Aberration — لبه‌ها کمی رنگین‌کمانی، حس لنز سینمایی. FilmPass.
36. Film Grain — دانه‌های ریز روی تصویر، حس فیلم. FilmPass.
37. Motion Blur — در لحظه حرکت، تاری حرکتی. نیاز به post-processing.
38. Vignette — گوشه‌های تصویر تیره‌تر، تمرکز روی مرکز.

دسته ۵: مکانیزم‌های UI و متن

39. Magnetic Button — دکمه CTA به سمت موس کشیده می‌شود. mousemove + gsap.to.
40. Cursor Follower — یک دایره یا نقطه، موس را دنبال می‌کند. حس «شخصی‌سازی».
41. Text Mask Reveal — متن از پشت یک ماسک (مثلاً شکل خودرو) بیرون می‌آید. clip-path + GSAP.
42. Number Counter — اعداد مشخصات (۱۷۰۰ اسب، ۱.۹ ثانیه) از صفر بالا می‌روند. gsap.to({ val: 0 }, { val: 1700 }).
43. Typewriter Effect — متن حرف‌به‌حرف تایپ می‌شود. مناسب تیتر Hero.
44. Gradient Shift — گرادیان پس‌زمینه آرام تغییر می‌کند. background-position + @keyframes.
45. Logo Reveal — لوگوی Koenigsegg با یک انیمیشن SVG (stroke-dashoffset) ترسیم می‌شود.
46. Sticky Navbar با تغییر رنگ — نوار بالا هنگام اسکرول شفاف به مات تبدیل می‌شود.
47. Scroll-Linked Color Theme — رنگ accent صفحه با اسکرول از سبز به آبی تغییر می‌کند (مثلاً هماهنگ با رنگ خودرو).

دسته ۶: مکانیزم‌های پیشرفته (اگر خواستید عمیق‌تر بروید)

48. SVG Line Drawing — خطوط فنی (مثل نقشه خودرو) با اسکرول ترسیم می‌شوند. stroke-dasharray + GSAP.
49. Morph SVG — یک شکل به شکل دیگر تبدیل می‌شود. flubber یا GSAP MorphSVG (پلاگین پولی).
50. Video Texture روی مدل — یک ویدیو روی صفحه داخلی خودرو پخش می‌شود. VideoTexture.
51. Physics Bounce — خودرو روی زمین می‌افتد و با فیزیک واقعی می‌پرد. cannon-es یا rapier.
52. Audio Reactive — انیمیشن با صدای موتور هماهنگ می‌شود. Web Audio API + FFT.
53. Scroll-Synced Audio — با اسکرول، صدای موتور کم/زیاد می‌شود. ترکیب ScrollTrigger با audio.volume.
54. WebGL Shader Transition — بین دو مدل یا دو صحنه، با shader محو می‌شود (نه ساده opacity). ShaderMaterial.
55. 360° Panorama — پس‌زمینه یک تصویر ۳۶۰ درجه که با موس می‌چرخد. THREE.SphereGeometry با texture.
56. Loading با Progress واقعی — همان spinner، ولی با درصد دقیق و انیمیشن SVG.

دسته ۷: مکانیزم‌های روایت (Storytelling)

57. Chapter Navigation — کاربر بین «فصل‌های» داستان (طراحی، موتور، داخل کابین) جابه‌جا می‌شود.
58. Hotspot — نقاط نورانی روی خودرو که با کلیک، توضیح باز می‌شود.
59. Timeline Slider — یک اسلایدر که کاربر با آن بین نسخه‌های مختلف (Gemera 2020 vs 2023) جابه‌جا می‌شود.
60. Compare Mode — دو خودرو کنار هم، با اسکرول مقایسه می‌شوند.

---

پیشنهاد مسیر یادگیری (ترتیب منطقی)

اگر هدف آشنایی با مکانیزم‌هاست، این ترتیب را پیشنهاد می‌کنم:

مرحله مکانیزم‌ها چرا
۱. پایه #1 (Pin)، #7 (Progress)، #42 (Counter)، #39 (Magnetic Button) ساده، سریع نتیجه می‌دهد، اعتماد می‌سازد
۲. دوربین #9 (Camera Path)، #11 (Orbit Toggle)، #13 (Exploded View) قلب تجربه سه‌بعدی
۳. تعامل #12 (Raycasting)، #22 (Hover)، #24 (Drag Mobile) حس «زنده بودن»
۴. بصری #29 (Particles)، #33 (Bloom)، #38 (Vignette) جلوگیری از حس «خشک»
۵. روایت #6 (Split Text)، #48 (SVG Line)، #57 (Chapters) داستان‌گویی حرفه‌ای
۶. پیشرفته #51 (Physics)، #54 (Shader)، #52 (Audio) برای وقتی که وقت دارید

---

سه مکانیزمی که بیشترین «بازده» را برای این دمو دارند

اگر فقط سه مورد را بخواهید اضافه کنید:

1. #22 Hover Highlight با Raycasting — وقتی کاربر روی چرخ یا درب می‌رود، آن بخش سبز می‌درخشد. یک خط کد بیشتر نیست، ولی حس تعامل را چند برابر می‌کند.
2. #13 Exploded View — قطعات جدا می‌شوند. اگر مدل Gemera اجزای نام‌گذاری‌شده داشته باشد، این تاثیرگذارترین مکانیزم است.
3. #29 Particle System — ذرات نورانی اطراف خودرو، فضای «فناوری آینده» می‌سازد. حتی با ۵۰۰ ذره ساده، تفاوت بصری چشمگیر است.

بگویید کدام‌ها را می‌خواهید پیاده کنیم — می‌توانم کد هر کدام را به‌صورت یک ماژول جدا اضافه کنم که با کد فعلی شما ترکیب شود.
