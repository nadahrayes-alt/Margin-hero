# Margin Hero — Product Requirements Document (PRD)
**Merchant Stack | V1.0**
**التاريخ: أبريل 2026**
**الحالة: Draft للمراجعة**

---

## 0. معلومات الوثيقة

| | |
|---|---|
| **اسم المنتج** | Margin Hero |
| **الإصدار** | V1.0 (MVP) |
| **مالك المنتج** | Merchant Stack — Product Lead |
| **مالك الهندسة** | TBD |
| **مالك التصميم** | TBD |
| **تاريخ البدء** | أبريل 2026 |
| **تاريخ الإطلاق المستهدف** | يوليو 2026 (12 أسبوع) |
| **المراجعون** | Founder, Eng Lead, Design Lead, 5 Pilot Merchants |
| **آخر تحديث** | أبريل 2026 |
| **المصدر الأساسي** | [margin-hero-final-report.md](margin-hero-final-report.md) |

---

## 1. الملخص التنفيذي

**جملة المنتج:**
> Margin Hero يخبر تاجر سلة كم يربح فعلاً على كل طلب، ويحميه من الخصومات والشحن ورسوم الدفع التي تأكل هامشه بصمت.

**الموقف الاستراتيجي ضمن Merchant Stack:**
- WhatsApp Hero → الاكتساب والتواصل
- Member Plus → الاحتفاظ والولاء
- **Margin Hero → ضمان أن النشاط يتحول إلى ربح حقيقي**

**نطاق V1:** ست ميزات أساسية تُمكّن التاجر من رؤية ربحه الحقيقي خلال أقل من 10 دقائق من التثبيت.

**التسعير:** 99 / 249 / 449 ريال شهرياً (محدّث بناءً على Benchmark تنافسي — Sampo AI بـ 749 ريال يثبت قدرة السوق على الدفع).

**الشريحة الأولية:** تجار سلة في فئات العطور، الأزياء، المكملات — 50+ طلب شهرياً.

---

## 2. الخلفية وبيان المشكلة

### 2.1 بيان المشكلة (Problem Statement)

تجار سلة يحققون مبيعات ظاهرها صحي لكن باطنها قد يكون خاسراً. أربعة عوامل تأكل الهامش بصمت:

1. **الخصومات المتكررة** — التاجر يطلق كوبونات بدون قياس أثرها على الهامش
2. **تكاليف الشحن** — قد تتجاوز ما يحصّله من العميل
3. **رسوم بوابات الدفع** — 1.8% إلى 3.8% تختلف حسب البوابة، ولا يحسبها التاجر
4. **المرتجعات** — تكلفة شحن مرتدة + إعادة تخزين + خسارة بيع

**الأخطر:** التاجر لا يكتشف المشكلة إلا بعد أشهر — عبر محاسبه أو عبر نضوب التدفق النقدي.

### 2.2 لماذا الآن؟ (Why Now)

- منصة سلة وصلت لمرحلة نضج: أكثر من 68,000 تاجر نشط (مصدر: Salla 2026)
- ✅ **API ناضج ومؤكد** يدعم `cost_price` كاملاً (PUT فردي + Bulk + SKU)
- ✅ **صفر منافسين مباشرين** في Salla App Store — فئة Accounting & Finance فارغة (تحقق مباشر مايو 2026)
- ✅ **Sampo AI** يُسعّر بـ 749 ريال/شهر بدون حساب ربح — يثبت قدرة السوق على الدفع
- المنافسون العالميون (TrueProfit، BeProfit، Lifetimely) أثبتوا الطلب: 1,335+ مراجعة مدفوعة
- ارتفاع وعي التجار بمفهوم الربحية مقابل الإيرادات

### 2.3 الأهداف (Goals)

**أهداف المنتج (Product Goals):**

| الهدف | المقياس | الهدف الكمي |
|---|---|---|
| **G1** — تمكين التاجر من رؤية ربحه الفعلي بسرعة | الوقت من التثبيت إلى أول رؤية ربحية | < 10 دقائق |
| **G2** — كشف تسرّبات الهامش غير المرئية | عدد المنتجات الخاسرة المُكتشفة شهرياً | متوسط ≥ 3 لكل تاجر نشط |
| **G3** — تحويل التطبيق إلى عادة يومية | معدل فتح التطبيق الأسبوعي | ≥ 4 مرات/أسبوع |
| **G4** — إثبات وضوح ROI للتاجر | "وفّر لك التطبيق X ريال" تظهر بدقة | ≥ 90% من المستخدمين يرونها |

**أهداف الأعمال (Business Goals):**

| الهدف | المقياس | الهدف الكمي (نهاية 6 أشهر من الإطلاق) |
|---|---|---|
| **B1** — Pre-sell ناجح | تجار وافقوا على الدفع المسبق | ≥ 10 |
| **B2** — تحويل تجربة → مدفوع | Trial-to-paid | ≥ 25% |
| **B3** — احتفاظ شهر 1-3 | Churn | < 15% |
| **B4** — قاعدة عملاء عند نهاية 6 أشهر | عدد المتاجر المدفوعة | ≥ 200 |
| **B5** — MRR | Monthly Recurring Revenue | ≥ 50,000 ريال (محدّث بعد رفع التسعير) |

### 2.4 ما ليس هدفاً (Non-Goals) في V1

ما **لن** نبنيه في V1 (واضحاً ومتعمداً):

- ❌ تكامل مع منصات الإعلانات (Meta، Google، TikTok) → V2
- ❌ تقارير P&L رسمية بصيغة محاسبية → V2
- ❌ توقعات (Forecasting) → V2
- ❌ Multi-store dashboard → V2
- ❌ Cohort analysis متقدم → V2
- ❌ Customer LTV → V2
- ❌ Price Scout (التسعير التنافسي بـ AI) → V1.5 (بعد 3 أشهر من الإطلاق)
- ❌ تطبيق موبايل (iOS/Android) → V2 (V1 = Web App + إشعارات WhatsApp/Email)
- ❌ تصدير البيانات إلى Excel/CSV → V2
- ❌ تكامل مع QuickBooks / Zoho Books → V2
- ❌ دعم متعدد الفروع المنفصل → V2
- ❌ Benchmarking مع متاجر مشابهة → V2

---

## 3. الشريحة المستهدفة والشخصيات (Personas)

### 3.1 الشخصية الأساسية — "أحمد، تاجر العطور"

| السمة | التفاصيل |
|---|---|
| **العمر** | 28-42 |
| **الموقع** | الرياض / جدة / الدمام |
| **النشاط** | متجر سلة لبيع العطور |
| **حجم الأعمال** | 80-150 طلب/شهر، 25,000-60,000 ريال/شهر إيرادات |
| **عدد SKUs** | 30-80 منتج |
| **التقنية** | متوسط — يستخدم سلة، إنستجرام، WhatsApp Business، Excel |
| **المعاناة الكبرى** | "أبيع كثير لكن البنك ما يعكس النمو — وين الفلوس؟" |
| **سلوك الخصومات** | يطلق كوبون كل 2-3 أسابيع، يخفض السعر 15-30%، لا يقيس الأثر |
| **بوابات الدفع** | Mada + Visa + Tamara (الثلاثة الأكثر شيوعاً) |
| **ما يثق فيه** | الأرقام البسيطة الواضحة، التوصيات بالعربي، الواتساب |
| **ما يكرهه** | الواجهات المعقدة، الإنجليزي الكثيف، إدخال بيانات يدوي طويل |

**اقتباس يمثل صوته:**
> "أعرف إيرادتي بالضبط. أعرف عدد الطلبات. لكن صراحة — كم ربحت الشهر هذا؟ ما عندي إجابة دقيقة."

### 3.2 الشخصية الثانوية — "نورة، تاجرة الأزياء"

| السمة | التفاصيل |
|---|---|
| **النشاط** | متجر أزياء نسائية |
| **حجم الأعمال** | 200-400 طلب/شهر |
| **التحدي الإضافي** | معدل مرتجعات 12-18% |
| **سلوك مميز** | تطلق عروض موسمية ضخمة (رمضان، العيد، الجمعة البيضاء) |
| **ما يميزها** | حساسة جداً لتأثير الخصومات لأن هامشها أصلاً ضيق |

### 3.3 الشخصية الثالثة — "خالد، تاجر المكملات"

| السمة | التفاصيل |
|---|---|
| **النشاط** | متجر مكملات غذائية ورياضية |
| **حجم الأعمال** | 100-180 طلب/شهر |
| **التحدي الإضافي** | تكاليف الشحن المبرّد لبعض المنتجات |
| **سلوك مميز** | اشتراكات شهرية + بيع لمرة واحدة (يحتاج قياس ربحية لكل نوع) |

### 3.4 من لا يستهدفه التطبيق (Anti-Personas)

| الشخصية | السبب |
|---|---|
| **التاجر المبتدئ (< 30 طلب/شهر)** | لا يحتاج بعد، الخصومات لم تصبح مشكلة |
| **بائع منتج رقمي واحد** | لا تكاليف شحن، لا تكلفة إنتاج متغيرة |
| **التاجر صفر-تكلفة (Dropshipper)** | تحتاج تكامل مختلف مع موردين خارجيين |
| **متاجر Enterprise (1000+ طلب/شهر)** | يحتاج Lifetimely-level من العمق — V2+ |

### 3.5 Jobs-To-Be-Done

ثلاث وظائف يستأجرنا التاجر لإنجازها:

1. **JTBD-1:** "ساعدني أعرف بالضبط كم ربحت هذا الشهر — بدون محاسب وبدون Excel."
2. **JTBD-2:** "نبّهني قبل أن أرتكب خطأ تسعيري — ليس بعد الخسارة."
3. **JTBD-3:** "أرني المنتج الذي يستنزفني — لأقرر هل أرفع سعره، أتركه، أو أوقفه."

---

## 4. User Stories مع Acceptance Criteria

### 4.1 Onboarding

**US-01:** كتاجر، أريد أن أربط متجر سلة بـ Margin Hero بنقرة واحدة، حتى لا أضطر لإعداد API يدوي.
- **AC-01.1:** يظهر زر "ربط متجر سلة" في صفحة التسجيل
- **AC-01.2:** عند النقر، تتم إعادة التوجيه إلى Salla OAuth
- **AC-01.3:** بعد الموافقة، يعود التاجر إلى Margin Hero مع جلسة فعّالة
- **AC-01.4:** يتم سحب أول 100 طلب وأول 50 منتج خلال أقل من 60 ثانية
- **AC-01.5:** في حال فشل OAuth، تظهر رسالة بالعربية مع زر "حاول مرة أخرى"

**US-02:** كتاجر، أريد أن أُدخل تكلفة أهم 10 منتجات في خطوة موجّهة، حتى أرى الربحية فوراً.
- **AC-02.1:** بعد الربط، يعرض النظام أعلى 10 منتجات مبيعاً تلقائياً
- **AC-02.2:** لكل منتج: حقل "التكلفة" (cost_price) فارغ أو معبّأ مسبقاً إذا كان موجوداً في سلة
- **AC-02.3:** يستطيع التاجر تخطّي منتج فردي، **لكن لا يمكن تخطي الخطوة كلها** — يجب إدخال تكلفة 5 منتجات على الأقل لفتح Dashboard
- **AC-02.4:** خيار **Smart Defaults** بالفئة: لو ضغط "املأ تلقائياً"، يقترح النظام تكلفة تقديرية حسب فئة المنتج (عطور 60% من السعر، أزياء 50%، مكملات 45%) — مع علامة "تقديري"
- **AC-02.5:** عند حفظ القيم، تتم مزامنتها مع Salla Products API (`PUT /admin/v2/products/{id}`)
- **AC-02.6:** يظهر شريط تقدّم: "5 من 10 منتجات لها تكلفة — ✅ يمكنك الآن فتح Dashboard"
- **AC-02.7:** خيار **Bulk Quick Entry** — جدول Excel-like لإدخال تكاليف 20+ منتج في واجهة واحدة

**US-03:** كتاجر، أريد اختيار بوابات الدفع التي يستخدمها متجري، حتى تُحسب الرسوم تلقائياً.
- **AC-03.1:** قائمة Checkbox تحوي البوابات السعودية الشائعة
- **AC-03.2:** التاجر يحدد البوابات النشطة في متجره
- **AC-03.3:** يستطيع تخصيص النسبة لكل بوابة إذا كانت لديه نسبة تفاوضية مختلفة
- **AC-03.4:** يُحفظ الاختيار ويُطبّق على كل الطلبات السابقة والمستقبلية

### 4.2 Order Profit Card

**US-04:** كتاجر، أريد أن أرى لكل طلب: السعر، الخصم، الشحن، الرسوم، صافي الربح.
- **AC-04.1:** بطاقة طلب تحوي 7 حقول واضحة
- **AC-04.2:** صافي الربح بلون أخضر إذا موجب، أحمر إذا سالب
- **AC-04.3:** يظهر هامش الربح كنسبة مئوية بجانب القيمة الرقمية
- **AC-04.4:** يمكن النقر لرؤية تفصيل المنتجات داخل الطلب
- **AC-04.5:** التحديث يتم خلال 30 ثانية من إتمام الطلب في سلة

### 4.3 Product Margin List

**US-05:** كتاجر، أريد قائمة منتجاتي مرتبة حسب الهامش، حتى أعرف من يستنزفني.
- **AC-05.1:** قائمة جدولية مرتبة افتراضياً من الأدنى هامشاً للأعلى
- **AC-05.2:** أعمدة: اسم المنتج، الكمية المباعة الشهرية، متوسط الهامش، إجمالي الربح
- **AC-05.3:** المنتجات بهامش < 5% تظهر بشريط أحمر
- **AC-05.4:** فلاتر: حسب الفترة (اليوم/7 أيام/30 يوم)، حسب الفئة
- **AC-05.5:** خيار البحث بالاسم أو SKU

### 4.4 Discount Impact Alert

**US-06:** كتاجر، أريد أن أُنبَّه عندما يخفّض كوبون هامشي تحت حد آمن.
- **AC-06.1:** عند تطبيق كوبون، يحسب النظام الهامش بعد الخصم
- **AC-06.2:** إذا انخفض الهامش تحت 10% (افتراضي قابل للتعديل)، يظهر تنبيه
- **AC-06.3:** التنبيه يحوي: اسم الكوبون، الهامش قبل/بعد، عدد الطلبات المتأثرة
- **AC-06.4:** يستطيع التاجر تعديل عتبة التنبيه (5%، 10%، 15%، 20%)
- **AC-06.5:** التنبيه يصل عبر: داخل التطبيق + WhatsApp (اختياري)

### 4.5 Monthly Profit Summary

**US-07:** كتاجر، أريد ملخص ربح شهري واضح، حتى أعرف "كم ربحت فعلاً؟"
- **AC-07.1:** صفحة شهرية تحوي: إجمالي الإيرادات، إجمالي التكاليف (مفصّلة)، صافي الربح، الهامش
- **AC-07.2:** مقارنة مع الشهر السابق (نسبة التغيّر)
- **AC-07.3:** أعلى 5 منتجات ربحاً، أدنى 5
- **AC-07.4:** إجمالي الخصومات الممنوحة وأثرها
- **AC-07.5:** إمكانية تنقّل بين الأشهر (آخر 12 شهر)

### 4.6 Daily Profit Pulse

**US-08:** كتاجر، أريد إشعار يومي بسيط بربح الأمس.
- **AC-08.1:** إشعار يصل في الساعة 9 صباحاً (افتراضي قابل للتعديل)
- **AC-08.2:** المحتوى: عدد الطلبات، صافي الربح، الهامش، اتجاه (↑/↓)
- **AC-08.3:** قنوات الإرسال: داخل التطبيق + WhatsApp (الأساسي) + Email
- **AC-08.4:** يستطيع التاجر إيقافه أو تغيير قناته أو وقته
- **AC-08.5:** إذا كان أمس بدون طلبات، يصل إشعار: "لا طلبات أمس — إجمالي الشهر حتى الآن: X ريال"

---

## 5. Functional Requirements — تفصيل الميزات

### 5.1 ميزة 1: Smart Onboarding

#### 5.1.1 الوصف
عملية تعريف موجّهة (Guided Onboarding) تقود التاجر من اللحظة صفر إلى أول رؤية ربحية في أقل من 10 دقائق.

#### 5.1.2 الخطوات (User Flow)

```
1. التسجيل / تسجيل الدخول
        ↓
2. ربط متجر سلة عبر OAuth
        ↓
3. مزامنة أولية للبيانات (مؤشر تحميل: "نجلب طلباتك...")
        ↓
4. اختيار بوابات الدفع المستخدمة (Multi-select)
        ↓
5. إدخال تكلفة أهم 10 منتجات (يمكن التخطّي)
        ↓
6. تأكيد عتبة تنبيه الهامش الافتراضية (10%)
        ↓
7. الوصول إلى Dashboard مع رسالة ترحيب: "ربحك الفعلي خلال آخر 30 يوم: X ريال"
```

#### 5.1.3 المتطلبات الوظيفية التفصيلية

**Step 2 — ربط سلة:**
- استخدام Salla OAuth 2.0
- الـ Scopes المطلوبة: `read_products`, `write_products`, `read_orders`, `read_coupons`, `read_settings`
- تخزين Access Token وRefresh Token مشفّرين (AES-256)
- التحقق من صحة الاتصال قبل المتابعة

**Step 3 — المزامنة الأولية:**
- جلب آخر 90 يوم من الطلبات (Pagination 50 طلب لكل صفحة)
- جلب كل المنتجات النشطة
- جلب الكوبونات النشطة
- إذا تجاوز عدد الطلبات 5,000، تُجرى المزامنة في الخلفية مع رسالة "سنُنهي في < 5 دقائق"
- إظهار تقدّم حقيقي (75 من 240 طلب)

**Step 4 — بوابات الدفع:**
- قائمة افتراضية: Mada، Visa/Master، STC Pay، Tamara، Tabby، COD، Apple Pay
- لكل بوابة: نسبة افتراضية + خيار "تعديل النسبة"
- إذا كانت البوابة غير موجودة في القائمة → خيار "أضف بوابة مخصصة"

**Step 5 — إدخال التكاليف (Cost Capture Gate):**
- يُحدد النظام أعلى 10 منتجات مبيعاً (آخر 30 يوم)
- لكل منتج: صورة + اسم + سعر بيع + حقل "التكلفة (ريال)"
- إذا كان `cost_price` موجوداً مسبقاً في سلة → يُعرض للتأكيد
- 🔴 **Gate إجباري:** الحد الأدنى لفتح Dashboard هو **5 منتجات بتكلفة**. لا يستطيع التاجر تخطّي الخطوة كلها
- **3 طرق لتعبئة سريعة:**
  1. **يدوياً:** Skip لكل منتج فردي مسموح (لكن لازم يصل لـ 5)
  2. **Smart Defaults بالفئة:** زر "املأ تلقائياً بهامش متوقع" — يستخدم متوسطات الفئة (عطور 60%، أزياء 50%، مكملات 45%) مع علامة "تقديري"
  3. **Bulk Quick Entry:** جدول Excel-like في صفحة واحدة لإدخال 20+ منتج
  4. **Excel/CSV Import:** رفع ملف بـ (SKU، التكلفة)
- بعد الحفظ: يُحدّث `cost_price` في Salla عبر API (`PUT /admin/v2/products/{id}` أو الـ Bulk endpoint)
- التكاليف الـ Smart Defaults تظهر بشارة دائمة "تقديري — أكّد الرقم الحقيقي" حتى يعدّلها التاجر

**Step 6 — عتبة التنبيه:**
- اقتراح افتراضي: 10%
- خيارات: 5%, 10%, 15%, 20%, مخصصة

#### 5.1.4 حالات الفشل (Error States)

| الحالة | السلوك |
|---|---|
| فشل OAuth | رسالة: "لم يتم الربط — حاول مرة أخرى" + زر إعادة |
| انقطاع المزامنة | حفظ التقدّم، زر "إكمال" عند العودة |
| API Rate Limit | إعادة المحاولة بعد 60 ثانية مع رسالة "سلة تطلب التمهّل قليلاً..." |
| لا توجد طلبات في آخر 90 يوم | تخطّي Step 3 + رسالة "متجرك جديد — سنبدأ من اليوم" |
| لا توجد منتجات | تخطّي Step 5 |

#### 5.1.5 حالة فارغة (Empty State)
متجر جديد بدون طلبات: عرض Dashboard فارغ مع رسالة "أول طلب سيظهر هنا فور إتمامه" + إرشاد لإدخال التكاليف.

#### 5.1.6 معايير القبول (Acceptance Criteria)
- ✅ التاجر يكمل Onboarding في < 10 دقائق (متوسط)
- ✅ نسبة إكمال Onboarding > 60%
- ✅ **100% من التجار يصلون Dashboard مع تكلفة 5 منتجات على الأقل** (Cost Capture Gate)
- ✅ بعد Onboarding، يرى التاجر ربحاً حقيقياً محسوباً لـ 5+ منتجات
- ✅ يعمل على الجوال والديسكتوب
- ✅ متاح بالكامل بالعربية مع RTL

---

### 5.2 ميزة 2: Order Profit Card

#### 5.2.1 الوصف
بطاقة تفصيلية لكل طلب تعرض كل مكونات الربح بشكل شفاف.

#### 5.2.2 الحقول المعروضة

| الحقل | المصدر | الحساب |
|---|---|---|
| **رقم الطلب** | Salla Order ID | مباشر |
| **التاريخ والوقت** | Salla Order created_at | مباشر |
| **العميل** | Salla Customer | الاسم الأول فقط (للخصوصية) |
| **سعر البيع (Subtotal)** | `order.sub_total` | مجموع أسعار المنتجات قبل الخصم |
| **الخصم** | `order.discount` | قيمة الخصم + اسم الكوبون |
| **الشحن المحصّل** | `order.shipping_amount` | المبلغ من العميل |
| **الضريبة** | `order.tax_amount` | (لا تُحتسب من الربح) |
| **الإجمالي المدفوع** | `order.total` | ما دفعه العميل |
| **— حسابات Margin Hero —** | | |
| **تكلفة المنتجات (COGS)** | sum(`product.cost_price` × qty) | محسوبة |
| **رسوم بوابة الدفع** | Fee Engine | total × نسبة البوابة |
| **تكلفة الشحن الفعلية** | إدخال يدوي / متوسط | افتراضي = الشحن المحصّل |
| **صافي الربح** | معادلة أدناه | محسوب |
| **هامش الربح %** | (صافي الربح / Subtotal) × 100 | محسوب |

#### 5.2.3 معادلة صافي الربح

```
Net Profit = Subtotal
           − Discount
           − COGS
           − Payment Gateway Fee
           − Actual Shipping Cost (إن وُجد، وإلا = الشحن المحصّل)
           + Shipping Collected (إذا الفعلي > المحصّل تكون سالبة، عكسها موجبة)

Profit Margin % = (Net Profit / Subtotal) × 100
```

**مثال:**
- Subtotal: 200 ريال
- Discount: 30 ريال (كوبون SUMMER10)
- COGS: 90 ريال
- Tamara Fee: 7 ريال (3.5% × 200)
- Shipping Cost: 25 ريال (الفعلي) — Shipping Collected: 20 ريال
- **Net Profit:** 200 − 30 − 90 − 7 − 25 + 20 = **68 ريال**
- **Margin:** 68 / 200 = **34%**

#### 5.2.4 متطلبات UI

- البطاقة تستخدم ألوان دلالية:
  - 🟢 أخضر إذا margin ≥ 20%
  - 🟡 أصفر إذا margin بين 5-20%
  - 🔴 أحمر إذا margin < 5%
- شارة "خطر" للطلبات الخاسرة (Net Profit < 0)
- زر "اعرض التفاصيل" يفتح breakdown كامل
- زر "لماذا الربح منخفض؟" يعرض tooltip بأكبر مكوّن أكَل الهامش

#### 5.2.5 حالات خاصة

| الحالة | السلوك |
|---|---|
| طلب لا يحوي `cost_price` لمنتج | يُحسب الربح بدون COGS لهذا المنتج + شارة "تكلفة ناقصة — أدخلها" |
| طلب مرتجع جزئياً | تعديل الحساب حسب المرتجع، عرض "رد جزئي" |
| طلب ملغى | لا يُحسب في الربح، يظهر بحالة "ملغى" |
| طلب COD بعد الدفع | الرسوم = 0% |
| طلب يحوي عدة بوابات (نادر) | تطبيق نسبة البوابة المسجّلة في `payment_method` |

---

### 5.3 ميزة 3: Product Margin List

#### 5.3.1 الوصف
قائمة جدولية لكل المنتجات النشطة، مرتبة افتراضياً حسب الهامش الأدنى — لكشف "اللصوص الصامتين".

#### 5.3.2 الأعمدة

| العمود | الوصف | الفرز |
|---|---|---|
| **المنتج** | الصورة + الاسم + SKU | حسب الاسم |
| **الفئة** | تصنيف سلة | حسب الفئة |
| **سعر البيع** | السعر الحالي | تصاعدي/تنازلي |
| **التكلفة** | cost_price (مع تنبيه إذا فارغة) | تصاعدي/تنازلي |
| **الكمية المباعة** | آخر 30 يوم | تصاعدي/تنازلي |
| **متوسط الهامش %** | محسوب | **افتراضي: تصاعدي** |
| **إجمالي الربح** | (السعر − التكلفة) × الكمية | تصاعدي/تنازلي |
| **الحالة** | 🟢 / 🟡 / 🔴 | حسب الحالة |

#### 5.3.3 الفلاتر

- **الفترة:** اليوم / 7 أيام / 30 يوم / 90 يوم / مخصصة
- **الفئة:** متعدد الاختيار من فئات المتجر
- **الحالة:** خاسر فقط / منخفض الهامش / متوسط / عالٍ
- **يحتوي على تكلفة:** نعم / لا / الكل
- **بحث:** بالاسم أو SKU

#### 5.3.4 الإجراءات لكل منتج

عند النقر على منتج:
- صفحة تفصيلية تعرض: تاريخ الهامش (Chart خطي 30 يوم) + كل الطلبات التي حواها
- زر **"عدّل التكلفة"** — يحدّث cost_price في سلة عبر API
- زر **"عدّل السعر"** — يحدّث selling_price في سلة عبر API
- زر **"احسب السعر المثالي"** — يقترح سعر يضمن هامش ≥ X%

#### 5.3.5 حالات خاصة

| الحالة | السلوك |
|---|---|
| منتج بدون cost_price | يظهر "—" مع شارة "أدخل التكلفة" |
| منتج بدون مبيعات في الفترة | يظهر "0" مع رمز هاديء |
| منتج بـ variants | يُعرض كصف رئيسي + توسيع لرؤية كل variant |
| منتج محذوف من سلة | لا يظهر، لكن يبقى في تاريخ الطلبات |

---

### 5.4 ميزة 4: Discount Impact Alert

#### 5.4.1 الوصف
نظام تنبيهات استباقي يكشف الكوبونات التي تخفّض الهامش تحت العتبة الآمنة — قبل أن يدمر التاجر هامشه دون أن يدري.

#### 5.4.2 المنطق

**Trigger:** عند إتمام طلب يحوي كوبوناً.

**الحساب:**
1. حساب هامش الطلب بدون الخصم (Hypothetical Margin)
2. حساب هامش الطلب الفعلي (Actual Margin)
3. الفرق = Discount Impact %
4. إذا (Actual Margin < threshold) → تنبيه فوري

**Aggregation:**
- بعد 5 طلبات أو 24 ساعة (الأقرب) لنفس الكوبون → تنبيه إجمالي:
  - "الكوبون SUMMER10 طُبّق على 12 طلب — متوسط الهامش انخفض من 28% إلى 7%"

#### 5.4.3 محتوى التنبيه

```
⚠️ تنبيه هامش — كوبون SUMMER10
─────────────────────────────────
طُبّق على: 12 طلب خلال 3 أيام
الهامش قبل الكوبون: 28%
الهامش بعد الكوبون: 7%
الخسارة المتراكمة: 1,820 ريال

التوصية: أعد التفكير في هذا الكوبون
أو ضعه على منتجات هامشها أعلى من 35%

[عرض التفاصيل]   [أوقف الكوبون]
```

#### 5.4.4 قنوات الإرسال

| القناة | الافتراضي | قابل للتخصيص |
|---|---|---|
| داخل التطبيق (Banner + قائمة) | ON | لا |
| WhatsApp | ON | نعم |
| Email | OFF | نعم |
| SMS | OFF (V2) | — |

#### 5.4.5 إعدادات التاجر

- **عتبة التنبيه:** 5%, 10%, 15%, 20%, مخصصة
- **تكرار التنبيه:** فوري / يومي مجمّع / أسبوعي
- **استثناءات:** عدم التنبيه على كوبونات معيّنة (مثل كوبونات الموظفين)

#### 5.4.6 حالات خاصة

| الحالة | السلوك |
|---|---|
| كوبون على شحن مجاني فقط | يُحسب أثره على الشحن، لا يُحسب كخصم منتج |
| كوبون مزدوج (نادر) | تطبيق الأكبر فقط |
| كوبون يجعل الطلب خاسر | تنبيه فوري **حتى لو** كانت العتبة منخفضة |

---

### 5.5 ميزة 5: Monthly Profit Summary

#### 5.5.1 الوصف
صفحة شهرية مدمجة تجيب على سؤال واحد: "كم ربحت هذا الشهر؟"

#### 5.5.2 الأقسام

**القسم 1 — البطاقة الكبرى:**
```
صافي ربحك في أبريل 2026
─────────────────────
        14,820 ريال
        ↑ 18% عن مارس
        هامش 22%
```

**القسم 2 — تفصيل التكاليف:**

| البند | المبلغ | النسبة من الإيرادات |
|---|---|---|
| إجمالي المبيعات | 67,500 ريال | 100% |
| الخصومات | 4,200 ريال | 6.2% |
| تكلفة المنتجات (COGS) | 36,800 ريال | 54.5% |
| رسوم الدفع | 2,180 ريال | 3.2% |
| تكلفة الشحن | 9,500 ريال | 14.1% |
| **صافي الربح** | **14,820 ريال** | **22.0%** |

**القسم 3 — أبطال وضحايا:**
- أعلى 5 منتجات ربحاً (Net Profit Top 5)
- أدنى 5 منتجات ربحاً (تحذير، ربما خاسرة)

**القسم 4 — أكبر تسرّبات الهامش:**
- "خصومات هذا الشهر كلّفتك 4,200 ريال — منها 1,820 من كوبون SUMMER10"
- "تكلفة الشحن في 8 طلبات تجاوزت ما حصّلته"
- "3 منتجات بعتها بهامش أقل من 5%"

**القسم 5 — مقارنة شهرية:**
- Bar Chart لآخر 6 أشهر
- اتجاه (↑↓) لكل بند

#### 5.5.3 التفاعل

- النقر على أي بند → فلترة الطلبات حسبه
- النقر على شهر سابق → تنقّل تاريخي (آخر 12 شهر)
- زر "شارك التقرير" → نسخة PDF (V1.5)

---

### 5.6 ميزة 6: Daily Profit Pulse

#### 5.6.1 الوصف
إشعار يومي قصير يحوّل التطبيق من "أفتحه أحياناً" إلى عادة يومية.

#### 5.6.2 محتوى الرسالة

**نموذج WhatsApp:**
```
☀️ صباح الخير، أحمد

أمس (29 أبريل):
📦 12 طلب
💰 صافي الربح: 1,840 ريال
📈 هامش 23% ↑ (+2% عن المتوسط)

⭐ أعلى منتج: عطر A (450 ريال ربح)
⚠️ تنبيه: كوبون NEWUSER خفّض هامش 3 طلبات

[افتح التطبيق]
```

#### 5.6.3 المتطلبات

- وقت الإرسال: قابل للتخصيص (افتراضي 9:00 صباحاً)
- اللغة: عربي افتراضياً، إنجليزي اختيارياً
- إذا 0 طلبات أمس: رسالة بديلة "لا طلبات أمس — مجموع الشهر حتى الآن: X ريال"
- إذا طلب خاسر بشدة: تنبيه إضافي مدمج

#### 5.6.4 إيقاف/تخصيص
- ON/OFF
- اختيار القناة (WhatsApp / Email / كلاهما)
- اختيار الوقت
- اختيار التفاصيل (بسيط / متوسط / مفصّل)

---

## 6. Non-Functional Requirements

### 6.1 الأداء (Performance)

| المقياس | الهدف |
|---|---|
| وقت تحميل Dashboard | < 2 ثانية (Initial Load) |
| تحديث طلب جديد | < 30 ثانية من إتمام الطلب في سلة |
| استعلام Order Profit Card | < 500ms |
| استعلام Product Margin List (1000 منتج) | < 1 ثانية |
| Onboarding مزامنة 100 طلب | < 60 ثانية |
| API Response Time (P95) | < 800ms |

### 6.2 الموثوقية (Reliability)

- **Uptime SLA:** 99.5% شهرياً (تجاوز سقف 3.6 ساعة توقف/شهر = خرق)
- **Disaster Recovery:** نسخ احتياطية يومية، RPO ≤ 24 ساعة، RTO ≤ 4 ساعات
- **Idempotency:** كل Webhook handler يجب أن يتعامل مع التكرار بأمان
- **Retry Policy:** Exponential backoff للـ Salla API (3 محاولات: 1s, 5s, 15s)

### 6.3 الأمان (Security)

- **Authentication:** OAuth 2.0 مع Salla
- **Authorization:** Multi-tenancy — كل تاجر يرى بيانات متجره فقط
- **Token Storage:** AES-256 encrypted at rest
- **Token Rotation:** Refresh كل 24 ساعة
- **HTTPS:** إلزامي لكل حركة شبكية
- **Webhook Verification:** التحقق من توقيع Salla على كل Webhook
- **Input Validation:** كل المدخلات تُفحص (server-side) — منع SQL Injection / XSS
- **Rate Limiting:** 100 req/min لكل تاجر للـ API الداخلي
- **Audit Log:** تسجيل كل تعديل على cost_price أو selling_price

### 6.4 الخصوصية (Privacy)

- **PII:** تخزين الحد الأدنى — اسم العميل الأول فقط في UI
- **Data Retention:** 24 شهر افتراضياً، حذف تلقائي بعدها
- **Right to Delete:** التاجر يستطيع حذف حسابه وكل بياناته خلال 30 يوم
- **GDPR / NDMO:** التزام بأنظمة حماية البيانات السعودية

### 6.5 التوسّع (Scalability)

| الحمل | الهدف |
|---|---|
| عدد المتاجر المتزامنة | 1,000 (V1) — 10,000 (V2) |
| طلبات/شهر/متجر | حتى 10,000 |
| إجمالي طلبات يومية على المنصة | 200,000 |
| Webhooks/ثانية | 50 |

### 6.6 التوطين (Localization)

- **اللغات:** عربي (افتراضي)، إنجليزي
- **الاتجاه:** RTL كامل — لا "نصف-RTL" مكسور
- **الأرقام:** عربية شرقية أو لاتينية حسب تفضيل التاجر
- **التواريخ:** هجري وميلادي (الميلادي افتراضي)
- **العملة:** الريال السعودي افتراضياً، دعم AED/KWD/USD لاحقاً
- **النصوص:** كل النصوص في ملفات i18n منفصلة، لا hardcoded

### 6.7 إمكانية الوصول (Accessibility)

- **WCAG 2.1 Level AA**
- تباين ألوان كافٍ (≥ 4.5:1)
- دعم قارئ الشاشة العربي
- Keyboard navigation كامل
- أحجام لمس ≥ 44×44 px على الجوال

### 6.8 التوافق (Compatibility)

- **المتصفحات:** Chrome 100+, Safari 15+, Firefox 100+, Edge 100+
- **الجوال:** Safari iOS 15+, Chrome Android 100+
- **الشاشات:** 320px → 4K
- **المتاجر:** سلة فقط في V1 (Zid، Shopify لاحقاً)

---

## 7. المعمارية التقنية (Technical Architecture)

### 7.1 الـ Stack المقترح

| الطبقة | التقنية المقترحة | المبرر |
|---|---|---|
| **Frontend** | Next.js 14 + React + TypeScript | SEO، RTL ناضج، DX قوي |
| **UI Library** | Tailwind + shadcn/ui (مع تخصيص RTL) | سرعة بناء + تخصيص |
| **Backend** | Node.js (NestJS) أو Python (FastAPI) | TBD حسب الفريق |
| **Database** | PostgreSQL 15+ | علاقات مالية تحتاج ACID |
| **Cache** | Redis | جلسات + queue + rate limiting |
| **Queue** | BullMQ (Redis) أو RabbitMQ | للمزامنة الخلفية |
| **Search** | PostgreSQL Full-Text أو Meilisearch | بحث المنتجات |
| **Analytics** | PostHog أو Mixpanel | KPIs + Funnels |
| **Error Tracking** | Sentry | مراقبة الأخطاء |
| **Hosting** | AWS (Riyadh region) أو Salla Cloud | قرب جغرافي + امتثال |
| **CDN** | CloudFront / Cloudflare | أداء |
| **WhatsApp** | Salla WhatsApp API أو 360dialog | الإشعارات |
| **Email** | AWS SES أو Resend | الإشعارات |

### 7.2 المخطط على المستوى العالي

```
┌──────────────┐
│  Salla Store │
└───────┬──────┘
        │ Webhooks + REST API
        ↓
┌──────────────────────────────────────────┐
│         Margin Hero Backend              │
│  ┌──────────┐  ┌──────────┐  ┌────────┐  │
│  │ API      │  │ Workers  │  │ Cron   │  │
│  │ (REST)   │  │ (Queue)  │  │ Jobs   │  │
│  └────┬─────┘  └────┬─────┘  └───┬────┘  │
│       │             │             │       │
│       └─────────────┼─────────────┘       │
│                     ↓                     │
│        ┌────────────────────┐             │
│        │  PostgreSQL + Redis│             │
│        └────────────────────┘             │
└──────────────────────────────────────────┘
        ↑                            ↓
        │                    ┌───────────────┐
        │                    │ WhatsApp/Email│
        │                    └───────────────┘
        ↓
┌──────────────┐
│   Web App    │
│  (Next.js)   │
└──────────────┘
```

### 7.3 المكوّنات الرئيسية (Services)

| Service | المسؤولية |
|---|---|
| **Auth Service** | OAuth + جلسات + multi-tenancy |
| **Sync Service** | جلب البيانات من Salla (Webhooks + Polling) |
| **Profit Engine** | حساب الربح لكل طلب — قلب التطبيق |
| **Fee Engine** | تطبيق رسوم بوابات الدفع |
| **Alert Engine** | اكتشاف وإرسال التنبيهات |
| **Notification Service** | WhatsApp + Email |
| **Reporting Service** | التقارير الشهرية واليومية |
| **Webhook Handler** | استقبال Webhooks من سلة |

### 7.4 استراتيجية المزامنة

**Hybrid Approach:**
1. **Webhooks** (الأساس) — `order.created`, `order.updated`, `order.refunded`, `product.updated`
2. **Polling** (Fallback) — كل 15 دقيقة، التحقق من الطلبات الفائتة
3. **Initial Sync** — عند Onboarding، جلب آخر 90 يوم
4. **Reconciliation** — جوب يومي ينقّب عن أي تباين

---

## 8. نموذج البيانات (Data Model)

### 8.1 الكيانات الرئيسية

```
Merchant ──< Store ──< Product ──< ProductVariant
                  │
                  └──< Order ──< OrderLineItem
                          │
                          └──< OrderProfit
                          
PaymentGateway ──< MerchantPaymentGateway
Coupon ──< CouponUsage
Alert
```

### 8.2 جداول مفصّلة

#### `merchants`
| Field | Type | Notes |
|---|---|---|
| id | UUID PK | |
| email | VARCHAR | unique |
| phone | VARCHAR | unique, للواتساب |
| name | VARCHAR | |
| created_at | TIMESTAMP | |
| plan | ENUM | starter/growth/pro |
| status | ENUM | trial/active/cancelled |
| trial_ends_at | TIMESTAMP | |

#### `stores`
| Field | Type | Notes |
|---|---|---|
| id | UUID PK | |
| merchant_id | UUID FK | |
| salla_store_id | VARCHAR | unique |
| salla_access_token | TEXT | encrypted |
| salla_refresh_token | TEXT | encrypted |
| token_expires_at | TIMESTAMP | |
| name | VARCHAR | |
| currency | VARCHAR(3) | SAR default |
| timezone | VARCHAR | Asia/Riyadh |
| sync_status | ENUM | idle/syncing/error |
| last_synced_at | TIMESTAMP | |

#### `products`
| Field | Type | Notes |
|---|---|---|
| id | UUID PK | |
| store_id | UUID FK | |
| salla_product_id | VARCHAR | |
| name | VARCHAR | |
| sku | VARCHAR | |
| selling_price | DECIMAL(12,2) | |
| cost_price | DECIMAL(12,2) | nullable |
| category | VARCHAR | |
| status | ENUM | active/draft/archived |
| created_at | TIMESTAMP | |
| updated_at | TIMESTAMP | |

#### `orders`
| Field | Type | Notes |
|---|---|---|
| id | UUID PK | |
| store_id | UUID FK | |
| salla_order_id | VARCHAR | |
| order_number | VARCHAR | |
| customer_first_name | VARCHAR | |
| sub_total | DECIMAL(12,2) | |
| discount_amount | DECIMAL(12,2) | |
| discount_code | VARCHAR | nullable |
| shipping_collected | DECIMAL(12,2) | |
| shipping_actual | DECIMAL(12,2) | nullable, manual |
| tax_amount | DECIMAL(12,2) | |
| total | DECIMAL(12,2) | |
| payment_method | VARCHAR | |
| status | ENUM | completed/cancelled/refunded |
| created_at | TIMESTAMP | |

#### `order_line_items`
| Field | Type | Notes |
|---|---|---|
| id | UUID PK | |
| order_id | UUID FK | |
| product_id | UUID FK | |
| quantity | INT | |
| unit_price | DECIMAL(12,2) | |
| unit_cost | DECIMAL(12,2) | snapshot at time of order |

#### `order_profits` (calculated, cached)
| Field | Type | Notes |
|---|---|---|
| order_id | UUID PK | |
| cogs | DECIMAL(12,2) | sum(line.cost × qty) |
| payment_fee | DECIMAL(12,2) | |
| net_profit | DECIMAL(12,2) | |
| profit_margin | DECIMAL(5,2) | %  |
| calculated_at | TIMESTAMP | |
| version | INT | لإعادة الحساب |

#### `payment_gateways` (catalog)
| Field | Type | Notes |
|---|---|---|
| id | UUID PK | |
| code | VARCHAR | mada/visa/tamara/tabby/stcpay/cod |
| name_ar | VARCHAR | |
| default_fee_percent | DECIMAL(5,2) | |
| default_fee_fixed | DECIMAL(8,2) | |

#### `merchant_payment_gateways`
| Field | Type | Notes |
|---|---|---|
| store_id | UUID FK | |
| gateway_id | UUID FK | |
| custom_fee_percent | DECIMAL(5,2) | nullable |
| custom_fee_fixed | DECIMAL(8,2) | nullable |
| enabled | BOOLEAN | |

#### `alerts`
| Field | Type | Notes |
|---|---|---|
| id | UUID PK | |
| store_id | UUID FK | |
| type | ENUM | discount_impact/loss_order/missing_cost |
| severity | ENUM | info/warning/critical |
| title | TEXT | |
| body | JSONB | structured |
| triggered_at | TIMESTAMP | |
| read_at | TIMESTAMP | nullable |
| dismissed_at | TIMESTAMP | nullable |

---

## 9. تكامل Salla API

### 9.1 OAuth Scopes

```
read_products
write_products       (لتحديث cost_price و selling_price)
read_orders
read_coupons
read_settings
read_categories
```

### 9.2 Endpoints المستخدمة

**حالة التحقق:** ✅ **Confirmed** (تحقق مباشر من docs.salla.dev — مايو 2026)

| Endpoint | Method | الاستخدام | حالة |
|---|---|---|---|
| `/admin/v2/products` | GET | جلب المنتجات (Pagination 50/page) | ✅ Confirmed |
| `/admin/v2/products/{id}` | PUT | تحديث `cost_price` و `price` لمنتج واحد | ✅ Confirmed |
| `/admin/v2/products/sku/{sku}` | PUT | تحديث منتج عبر SKU (بديل أكثر مرونة) | ✅ Confirmed |
| `/admin/v2/products/quantities/prices` | PUT | **Bulk Update** — تحديث `price` + `cost_price` + `sale_price` لعدة منتجات دفعة واحدة | ✅ Confirmed |
| `/admin/v2/orders` | GET | جلب الطلبات (Filter بالتاريخ) | ✅ Confirmed |
| `/admin/v2/orders/{id}` | GET | تفاصيل طلب | ✅ Confirmed |
| `/admin/v2/coupons` | GET | الكوبونات النشطة | ✅ Confirmed |
| `/admin/v2/payments/methods` | GET | بوابات الدفع المفعّلة في المتجر | ✅ Confirmed |

**Scope المطلوب:** `products.read_write` (لـ PUT)، `orders.read`، `coupons.read`، `settings.read`

**التعريف الرسمي لـ `cost_price` من Salla:**
> "Product cost price, the amount a business pays to acquire or manufacture a product before any additional expenses."

### 9.3 Webhooks المستخدمة (محدّثة بناءً على Specialized Events)

> ⚠️ **تحذير مهم:** Salla هجرت (Deprecated) الـ events العامة مثل `product.updated` و `product.available`. الـ PRD يستخدم الآن **Specialized Events** فقط.

#### 9.3.1 Order Webhooks (مؤكدة من docs.salla.dev — مايو 2026)

| Event | الإجراء | حالة |
|---|---|---|
| `order.created` | حساب الربح فوراً + تنبيه إذا انطبق | ✅ Confirmed |
| `order.updated` | إعادة حساب الربح عند تعديل عام | ✅ Confirmed |
| `order.status.updated` | تتبع تغييرات الحالة (تنفيذ، شحن، تسليم) — schema منفصل: `OrdersUpdateStatusWebhookResponse` | ✅ Confirmed |
| `order.cancelled` | استبعاد الطلب من إحصاءات الربح (S-CALC-11) | ✅ Confirmed |
| `order.refunded` | 🔴 **المرتجع الكامل** (S-CALC-09): إعادة حساب Net Profit = -PaymentFee - ShippingActual، نقل الطلب لقائمة المرتجعات | ✅ Confirmed (schema: `OrdersWebhookResponse`) |
| `order.shipment.return.creating` | بدء إنشاء شحنة إرجاع — تنبيه استباقي | ✅ Confirmed |
| `order.shipment.return.created` | 🔴 **المرتجع الجزئي** (S-CALC-10): إعادة حساب الربح للمنتجات المتبقية فقط | ✅ Confirmed |
| `order.shipment.return.cancelled` | إلغاء شحنة إرجاع — إعادة الحساب | ✅ Confirmed |
| `order.products.updated` | تعديل منتجات في الطلب — إعادة حساب COGS | ✅ Confirmed |
| `order.payment.updated` | تغيير طريقة الدفع — إعادة حساب رسوم البوابة | ✅ Confirmed |
| `order.coupon.updated` | تعديل/إضافة/إزالة كوبون — إعادة حساب الخصم | ✅ Confirmed |
| `order.total.price.updated` | تغيير إجمالي السعر — Fallback لاكتشاف المرتجعات الجزئية | ✅ Confirmed |
| `order.shipment.creating` | تتبع تكلفة الشحن الفعلية إن أتيحت | ✅ Confirmed |
| `order.shipment.created` | تأكيد إرسال الشحنة | ✅ Confirmed |
| `order.shipment.cancelled` | إعادة فتح الحساب | ✅ Confirmed |
| `order.shipping.address.updated` | تحديث بيانات الشحن (لتقديرات تكلفة الشحن) | ✅ Confirmed |
| `order.deleted` | حذف الطلب من الإحصاءات | ✅ Confirmed |

#### 9.3.2 Product Webhooks (Specialized — موصى بها رسمياً)

| Event | الإجراء |
|---|---|
| `product.created` | إضافة للقائمة، شارة "أدخل التكلفة" إذا `cost_price = null` |
| `product.price.updated` | إعادة حساب الهامش الحالي للمنتج (يحوي حقل `cost` وليس `cost_price`) |
| `product.status.updated` | تحديث حالة المنتج (active/draft/archived) |
| `product.image.updated` | تحديث الصورة في قائمة المنتجات |
| `product.category.updated` | تحديث التصنيف للفلترة |

#### 9.3.3 App Lifecycle Webhooks

| Event | الإجراء |
|---|---|
| `app.installed` | بدء Onboarding |
| `app.uninstalled` | تجميد الحساب، حفظ البيانات 30 يوم |

#### 9.3.4 ⚠️ تحذير تقني للفريق — اختلاف تسمية الحقل

| المكان | اسم حقل التكلفة |
|---|---|
| في `PUT /products` API (Request Body) | `cost_price` |
| في `product.created` webhook (Payload) | `cost_price` |
| في `product.price.updated` webhook (Payload) | **`cost`** (مختصر) |

**القاعدة في الكود:** كل webhook handler يجب أن يتعامل مع الاسمين، ونوحدّهم داخلياً تحت `cost_price`.

```typescript
const costPrice = payload.cost_price ?? payload.cost ?? null;
```

#### 9.3.5 ✅ آلية المرتجعات — مؤكدة بالكامل

**النتيجة بعد التحقق المباشر من docs.salla.dev و starter kits الرسمية (Laravel + Express):**

| السيناريو | الـ Event المستخدم | الـ Schema |
|----------|-------------------|-----------|
| المرتجع الكامل للطلب | `order.refunded` | `OrdersWebhookResponse` (نفس schema `order.created`) |
| المرتجع الجزئي (إرجاع بعض المنتجات) | `order.shipment.return.created` | Schema منفصل لشحنات الإرجاع |
| إلغاء طلب قبل الشحن | `order.cancelled` | — |
| تعديل سعر/منتجات الطلب | `order.total.price.updated` + `order.products.updated` | — |

**Code Pattern في الـ Handler:**

```typescript
// المرتجع الكامل
onWebhook('order.refunded', (payload) => {
  const order = payload.data;
  recalculateProfit({
    orderId: order.id,
    cogs: 0,                              // المنتجات رجعت
    paymentFee: order.amounts.payment_fee, // الرسوم لا تُسترد
    shippingActual: order.amounts.shipping_cost.amount,
    netProfit: -(paymentFee + shippingActual)
  });
  markAsRefunded(order.id);
});

// المرتجع الجزئي
onWebhook('order.shipment.return.created', (payload) => {
  const returnShipment = payload.data;
  const returnedItems = returnShipment.items;
  recalculatePartialProfit(returnShipment.order_id, returnedItems);
});
```

**ميزة Fallback مدمجة:** event `order.total.price.updated` يطلق عند أي تغير في الإجمالي — يصلح للاكتشاف الذكي لأي مرتجع جزئي قد يفوته الـ shipment event.

### 9.4 معالجة Rate Limits

- Salla API rate limit: 60 req/min (افتراضي)
- استراتيجية: Token bucket + queue
- Backoff: 1s → 5s → 15s → 60s
- إذا فشل بعد 4 محاولات → تسجيل في error log + تنبيه فريق الدعم

### 9.5 Fallback في حال غياب بيانات

| البيانات الناقصة | الحل |
|---|---|
| `cost_price` لمنتج | تجاهل في الحساب + شارة "أدخل التكلفة" |
| رسوم بوابة الدفع | Fee Engine يطبّق نسبة افتراضية |
| تكلفة الشحن الفعلية | استخدام الشحن المحصّل كتقدير |
| طلب قبل تثبيت التطبيق (تاريخ قديم) | حساب بناءً على بيانات حالية فقط |

---

## 10. Payment Gateway Fee Engine (الميزة المحورية)

### 10.1 الوصف
محرّك حساب رسوم بوابات الدفع — لا يوجد لدى أي منافس عربي.

### 10.2 قاعدة بيانات أولية للنسب

| البوابة | النسبة % | رسم ثابت | ملاحظات |
|---|---|---|---|
| Mada | 1.8% | 0 ريال | بطاقات سعودية محلية |
| Visa/Master Credit | 2.5% | 0 ريال | |
| Visa/Master Debit | 2.0% | 0 ريال | |
| STC Pay | 2.3% | 0 ريال | |
| Apple Pay | 2.5% | 0 ريال | يتبع البطاقة الأساسية |
| Tamara | 3.5% | 0 ريال | متوسط، يختلف حسب الخطة |
| Tabby | 3.8% | 0 ريال | متوسط |
| Cash on Delivery | 0% | رسم شركة الشحن | يحسب ضمن الشحن |
| Bank Transfer | 0% | 0 ريال | |
| PayPal | 3.4% | 1 ريال | للطلبات الدولية |

### 10.3 منطق التطبيق

```python
def calculate_fee(order):
    gateway = lookup_gateway(order.payment_method)
    merchant_override = get_merchant_override(order.store_id, gateway.id)
    
    if merchant_override:
        percent = merchant_override.percent
        fixed = merchant_override.fixed
    else:
        percent = gateway.default_fee_percent
        fixed = gateway.default_fee_fixed
    
    fee = (order.total * percent / 100) + fixed
    return round(fee, 2)
```

### 10.4 تحديث النسب

- مراجعة ربع سنوية للنسب الفعلية في السوق
- إشعار التجار عند تحديث جوهري (تغيّر > 0.5%)
- إمكانية تخصيص النسبة إذا كان للتاجر اتفاقية تفضيلية

### 10.5 مستقبل (V2)
- ربط مباشر مع كشف حساب البوابات (Tamara API, Tabby API) لجلب الرسوم الفعلية
- اقتراحات: "لو حوّلت العملاء من Tabby إلى Mada توفّر X ريال شهرياً"

---

## 11. UX Flows

### 11.1 Onboarding Flow

```
[Landing]
   ↓ "ابدأ التجربة المجانية"
[Sign Up] (email + phone + password)
   ↓
[Connect Salla] → OAuth Redirect → Salla → Back
   ↓
[Initial Sync] (loader: "نجلب آخر 90 يوم...")
   ↓
[Step 1: Payment Gateways] (multi-select)
   ↓
[Step 2: Top 10 Products Costs] (with Skip per product)
   ↓
[Step 3: Alert Threshold] (default 10%)
   ↓
[Welcome Dashboard]: "ربحك في آخر 30 يوم: X ريال"
```

### 11.2 Daily Use Flow

```
[Daily Pulse on WhatsApp 9 AM]
   ↓
التاجر يفتح التطبيق
   ↓
[Dashboard]
   - بطاقة "ربح اليوم"
   - بطاقة "ربح الشهر"
   - تنبيهات نشطة (إن وُجدت)
   - أخطر 3 منتجات
   ↓
ينقر على تنبيه → [Alert Detail] → اتخاذ إجراء (إيقاف كوبون / تعديل سعر)
   أو
ينقر على طلب → [Order Profit Card]
   أو
ينقر على منتج خطر → [Product Detail] → تعديل سعر/تكلفة
```

### 11.3 Weekly Review Flow (مقترح)

```
[Weekly Email/WhatsApp Sunday morning]
   ↓
[Weekly Summary Page]
   - أرباح الأسبوع
   - الكوبونات الأكثر ضرراً
   - أعلى 5 منتجات ربحاً
   - توصية أسبوعية واحدة
```

### 11.4 Wireframes References
- TBD — ستُضاف روابط Figma بعد جلسات التصميم في الأسبوع الأول

---

## 12. الإشعارات (Notifications)

### 12.1 أنواع الإشعارات

| النوع | القناة الافتراضية | التكرار | قابل للإيقاف |
|---|---|---|---|
| Daily Profit Pulse | WhatsApp | يومي 9 ص | نعم |
| Discount Impact Alert | WhatsApp + In-App | فوري عند الحدث | نعم (لكن مُحذَّر) |
| Loss Order Alert | WhatsApp + In-App | فوري عند الحدث | لا (دائماً مفعّل — أمان) |
| Missing Cost Reminder | In-App | أسبوعي | نعم |
| Weekly Summary | WhatsApp + Email | الأحد 8 ص | نعم |
| Monthly Summary | Email | أول يوم في الشهر | نعم |
| Trial Ending | Email + WhatsApp | قبل 3 أيام | لا |
| Subscription Renewal | Email | قبل 7 أيام | لا |

### 12.2 قواعد عدم الإزعاج (Anti-Spam)

- لا أكثر من 3 إشعارات WhatsApp يومياً
- التنبيهات المتشابهة تُجمّع كل 4 ساعات
- لا إشعارات بين 10 مساءً و 7 صباحاً (إلا critical)
- الـ Loss Order Alert يتجاوز هذه القواعد

---

## 13. التسعير والاشتراكات

### 13.1 الخطط

| | **Starter** | **Growth** | **Pro** |
|---|---|---|---|
| **السعر/شهر** | 99 ريال | 249 ريال | 449 ريال |
| **حد الطلبات/شهر** | 100 | 500 | غير محدود |
| **عدد المنتجات** | 100 | 500 | غير محدود |
| **Order Profit Card** | ✅ | ✅ | ✅ |
| **Product Margin List** | ✅ | ✅ | ✅ |
| **Discount Impact Alert** | ✅ | ✅ | ✅ |
| **Daily Profit Pulse** | ✅ | ✅ | ✅ |
| **Monthly Summary** | ✅ | ✅ | ✅ |
| **Profit Leakage Report** | ❌ | ✅ | ✅ |
| **WhatsApp Notifications** | محدود (Daily Pulse فقط) | كامل | كامل |
| **عدد المستخدمين** | 1 | 3 | غير محدود |
| **دعم** | Email | Email + WhatsApp | Priority + Slack |
| **تجربة مجانية** | 14 يوم | 14 يوم | 14 يوم |

### 13.1.1 مبرر التسعير (Pricing Rationale)

| العنصر | الدليل |
|--------|--------|
| **Sampo AI** (Salla App Store) | 749 ريال/شهر — تسعير AI فقط، بدون حساب ربح |
| **TrueProfit** (Shopify) | $29.95-$99.95/شهر = 112-375 ريال |
| **BeProfit** (Shopify) | $25-$100/شهر = 94-375 ريال |
| **تجار سلة المستهدفون** | 25-60 ألف ريال إيرادات/شهر → 449 ريال = 0.75-1.8% فقط |

**القاعدة:** السوق يدفع. التسعير القديم (199/349) كان متحفظاً. الجديد (249/449) يقع في وسط نطاق Shopify ودون نصف Sampo.

### 13.2 سياسة الترقية والإلغاء

- الترقية: فوراً مع تعديل الفاتورة (Prorated)
- التخفيض: في بداية الدورة التالية
- الإلغاء: في أي وقت — بدون رسوم
- الاسترداد: خلال 7 أيام من الدفع الأول إذا لم يُستخدم

### 13.3 ما يحدث عند تجاوز الحد

- 80% من الحد: تنبيه "اقتربت من حدك"
- 100%: استمرار العمل + اقتراح ترقية
- 110% لمدة 3 أيام: تجميد الميزات الإضافية حتى الترقية

---

## 14. Success Metrics & KPIs

### 14.1 KPIs الأساسية (تتبَع أسبوعياً)

| المقياس | الهدف V1 | الهدف 6 أشهر |
|---|---|---|
| **Onboarding Completion** | > 60% | > 70% |
| **Aha Moment Rate** | > 70% | > 80% |
| **Day-7 Retention** | > 40% | > 55% |
| **Day-30 Retention** | > 25% | > 40% |
| **Trial-to-Paid Conversion** | > 25% | > 35% |
| **Monthly Churn** | < 15% | < 8% |
| **NPS** | > 30 | > 50 |
| **Avg. Login Frequency** | 3-4/week | 4-5/week |
| **Daily Pulse Open Rate** | > 60% | > 75% |

### 14.2 KPIs ثانوية

- متوسط عدد المنتجات الخاسرة المُكتشفة لكل تاجر
- عدد الكوبونات التي أوقفها التاجر بسبب التنبيه
- متوسط تحسّن الهامش بعد 90 يوم من الاستخدام
- عدد الإحالات (Referrals)

### 14.3 Tracking Events

```
- onboarding_started
- onboarding_step_completed (step_number)
- onboarding_completed (duration_seconds)
- store_connected
- product_cost_added (count)
- payment_gateway_selected (gateway_code)
- order_profit_viewed (order_id)
- product_margin_clicked (product_id)
- discount_alert_received (alert_id)
- discount_alert_action_taken (alert_id, action)
- daily_pulse_received (channel)
- daily_pulse_opened
- monthly_summary_viewed
- subscription_started (plan)
- subscription_upgraded (from, to)
- subscription_cancelled (reason)
```

---

## 15. النطاق (Scope)

### 15.1 ضمن V1 (Must Have)

- ✅ Smart Onboarding
- ✅ Product Margin List
- ✅ Discount Impact Alert
- ✅ Monthly Profit Summary
- ✅ Daily Profit Pulse
- ✅ Payment Gateway Fee Engine
- ✅ WhatsApp + Email Notifications
- ✅ Web App Responsive (Desktop + Mobile)
- ✅ عربي + إنجليزي
- ✅ 3 خطط اشتراك مع تجربة مجانية
- ✅ Salla App Store Listing

### 15.2 V1.5 (بعد 3 أشهر)

- 🟡 Price Scout — التسعير التنافسي بـ AI
- 🟡 Profit Leakage Report (تقرير شهري متقدّم)
- 🟡 PDF Export للتقارير
- 🟡 Weekly Summary

### 15.3 V2 (بعد 6 أشهر)

- 🟢 تكامل مع منصات الإعلانات (Meta، Google، TikTok)
- 🟢 P&L Report رسمي
- 🟢 Customer LTV
- 🟢 Cohort Analysis
- 🟢 Forecasting
- 🟢 تطبيق موبايل (iOS + Android)
- 🟢 Multi-store Dashboard
- 🟢 Benchmarking
- 🟢 تكامل QuickBooks / Zoho Books
- 🟢 دعم Zid + Shopify

### 15.4 خارج النطاق نهائياً (في الأفق المنظور)

- ❌ نظام محاسبة كامل (نحن أداة ذكاء، لسنا ERP)
- ❌ إدارة المخزون (يفعلها بوصلة وآخرون)
- ❌ POS أو نقاط بيع
- ❌ شحن وتلبية (Fulfillment)

---

## 16. Timeline & Milestones

### 16.1 المراحل الزمنية (12 أسبوع)

| المرحلة | الأسابيع | المخرجات |
|---|---|---|
| **Phase 0: Validation** | 1-2 | Pre-sell 10 تجار + Prototype Figma + اختبار مع 5 تجار |
| **Phase 1: Foundation** | 3-4 | Auth + Salla OAuth + DB Schema + CI/CD |
| **Phase 2: Core Engine** | 5-7 | Profit Engine + Fee Engine + Sync + Webhooks |
| **Phase 3: Features** | 8-10 | الميزات الست + UI + Notifications |
| **Phase 4: Beta** | 11 | إطلاق مع 10-20 تاجر، إصلاح الأخطاء |
| **Phase 5: GA Launch** | 12 | إطلاق عام + Salla App Store + تسويق |

### 16.2 Milestones التفصيلية

**أسبوع 1:**
- [ ] إنهاء PRD (هذه الوثيقة)
- [ ] تأكيد نسب بوابات الدفع مع 5 تجار
- [ ] Prototype Figma (Onboarding + Dashboard)
- [ ] إعداد Repo + CI/CD

**أسبوع 2:**
- [ ] 10 تجار وافقوا على Pre-sell
- [ ] اختبار Prototype مع 5 تجار حقيقيين
- [ ] الموافقة على التصميم النهائي
- [ ] التحقق من Salla Webhooks

**أسبوع 3-4:**
- [ ] Auth Service + OAuth
- [ ] DB Schema + Migrations
- [ ] Salla API Client مع Rate Limiting
- [ ] Initial Sync Job

**أسبوع 5-7:**
- [ ] Profit Calculation Engine
- [ ] Payment Gateway Fee Engine
- [ ] Webhook Handlers
- [ ] Order Profit Card (UI + Backend)
- [ ] Product Margin List

**أسبوع 8-10:**
- [ ] Discount Impact Alert
- [ ] Monthly Summary
- [ ] Daily Profit Pulse + WhatsApp Integration
- [ ] Smart Onboarding
- [ ] Subscription & Billing

**أسبوع 11:**
- [ ] Beta مع 10-20 تاجر
- [ ] Bug Bash
- [ ] إصلاحات حرجة
- [ ] تجهيز Salla App Store Listing

**أسبوع 12:**
- [ ] إطلاق رسمي
- [ ] حملة تسويقية (إنستجرام + WhatsApp + يوتيوب)
- [ ] Salla App Store Approval
- [ ] متابعة KPIs أسبوعياً

### 16.3 Dependencies

| المهمة | تعتمد على |
|---|---|
| Profit Engine | Salla API Client + Fee Engine |
| Order Profit Card | Profit Engine |
| Discount Impact Alert | Profit Engine + Notification Service |
| Daily Pulse | WhatsApp Integration + Cron Jobs |
| Monthly Summary | كل ما سبق |
| Beta | كل الميزات + Subscription |

---

## 17. المخاطر وخطط التخفيف (Risks & Mitigations)

| الخطر | الاحتمال | التأثير | خطة التخفيف |
|---|---|---|---|
| **التجار لا يدخلون cost_price** | **متوسط ⬇️** | عالٍ | **Cost Capture Gate إجباري (5 منتجات)** + Smart Defaults بالفئة + Bulk Quick Entry + Excel import + شارة "تقديري" |
| ~~webhook المرتجعات~~ ✅ **محلول** | — | — | مؤكد: `order.refunded` للكامل + `order.shipment.return.created` للجزئي (تحقق مباشر من docs.salla.dev + Salla Laravel/Express Starter Kits) |
| **فقدان الثقة بالأرقام** | متوسط | عالٍ | شفافية كاملة — كل رقم يُشرح مصدره + breakdown قابل للتدقيق |
| **سلة تطلق ميزة منافسة nativey** | منخفض | متوسط | طبقة التوصيات تحميه — سلة عادة تبني الأرقام لا الذكاء |
| **منافس مباشر يدخل Salla App Store** | **منخفض ⬇️** (مؤكد: صفر منافسين في مايو 2026) | متوسط | السرعة للسوق + بناء حواجز (تكاملات WhatsApp، Smart Defaults، نموذج بيانات تكلفة خاص) |
| **بوصلة تطور ميزة ربحية** | متوسط | متوسط | تركيزنا على الربحية التشغيلية، بوصلة على المخزون والإعلانات |
| **Salla API غير مستقر / تعطّل** | منخفض | عالٍ | Polling fallback + Reconciliation jobs + تنبيه مستخدم |
| **تأخير الـ MVP** | متوسط | عالٍ | Scope صارم، أسبوعياً Sprint Review، إزالة ميزات إن لزم |
| **فشل Pre-sell** | منخفض | حرج | إعادة تموضع، اختبار مع شريحة مختلفة |
| **رسوم بوابات الدفع غير دقيقة** | متوسط | متوسط | تخصيص يدوي للتاجر + مراجعة ربع سنوية |
| **Churn مرتفع بعد التجربة** | متوسط | عالٍ | Daily Pulse يبني العادة + ROI واضح + onboarding ممتاز |
| **مشاكل WhatsApp delivery** | منخفض | متوسط | Email fallback + In-app كقناة احتياطية |
| **اختلاف تسمية `cost` vs `cost_price` في webhooks** | عالٍ (تقني) | منخفض | كل webhook handler يستخدم: `cost_price ?? cost ?? null` |
| **استخدام events مهجورة (product.updated)** | محل (مُحلّ) | — | الـ PRD يستخدم Specialized Events فقط: `product.price.updated`, `product.status.updated`, ... |

**لا يوجد خطر قاتل (Showstopper).** بعد التحقق الشامل من Salla docs (مايو 2026):
- ✅ API يدعم `cost_price` بالكامل (CRUD + Bulk + per-SKU)
- ✅ صفر منافسين مباشرين في Salla App Store
- ✅ Order webhooks تحوي كل الحقول المالية المطلوبة
- ✅ **آلية المرتجعات مؤكدة بالكامل** — `order.refunded` للكامل + `order.shipment.return.created` للجزئي
- ✅ Specialized Product Events مؤكدة (`product.price.updated`, إلخ)

**كل المخاطر التقنية الحرجة تم حلها. الطريق مفتوح للبناء.**

---

## 18. السيناريوهات الشاملة (Scenarios & Edge Cases)

> **الغرض:** تغطية كاملة لكل المسارات الممكنة — السعيد منها والاستثنائي وحالات الحافة والفشل — لتوجيه التطوير والاختبار. لكل سيناريو: المُحفّز (Trigger)، النتيجة المتوقعة، حالة الفشل والتعافي.

### 18.1 سيناريوهات Onboarding

#### S-ONB-01: تاجر جديد كلياً يربط متجره بنجاح
- **Trigger:** التاجر ينقر "ربط متجر سلة" → يوافق على OAuth
- **Pre-condition:** المتجر فعّال في سلة، فيه طلبات في آخر 90 يوم
- **النتيجة المتوقعة:** تتم المزامنة في < 60 ثانية، يصل لـ Dashboard مع رؤية ربحية أولية
- **التحقق:** جميع جداول `stores`, `products`, `orders` معبّأة

#### S-ONB-02: متجر جديد بدون أي طلبات
- **Trigger:** ربط متجر جديد عمره < أسبوع، لا توجد طلبات
- **النتيجة المتوقعة:** يتخطّى Step 3 (المزامنة)، يصل لـ Dashboard فارغ مع رسالة: "متجرك جديد — أول طلب سيظهر هنا فور إتمامه"
- **الإجراء البديل:** يطلب منه إدخال تكاليف منتجاته مباشرة استعداداً للطلبات القادمة

#### S-ONB-03: متجر بـ 5,000+ طلب (مزامنة كبيرة)
- **Trigger:** ربط متجر قديم بحجم بيانات كبير
- **النتيجة المتوقعة:** المزامنة تعمل في الخلفية مع شريط تقدّم، ويستطيع التاجر استخدام التطبيق فوراً على البيانات المُجلبة جزئياً
- **حد الأمان:** بعد 5 دقائق إن لم تكتمل، رسالة "نُكمل في الخلفية، سنُشعرك عبر WhatsApp عند الانتهاء"

#### S-ONB-04: التاجر يرفض صلاحيات OAuth
- **Trigger:** التاجر يضغط "إلغاء" في صفحة موافقة سلة
- **النتيجة المتوقعة:** يعود للتطبيق مع رسالة: "تحتاج للموافقة على الصلاحيات لاستخدام التطبيق" + زر "حاول مرة أخرى" + رابط لشرح كل صلاحية
- **الإجراء:** لا تُحفظ بيانات، الجلسة تبقى للمحاولة مرة أخرى

#### S-ONB-05: التاجر يكمل OAuth ثم يخرج قبل إدخال التكاليف
- **Trigger:** ربط ناجح، لكن يغلق التبويب في Step 5
- **النتيجة المتوقعة:** عند العودة، يتم استئناف Onboarding من حيث توقّف
- **التحقق:** المزامنة استمرت في الخلفية، البيانات جاهزة، فقط إدخال التكاليف بقي

#### S-ONB-06: التاجر يحاول تخطّي كل خطوات إدخال التكاليف
- **Trigger:** ضغط "Skip" على كل المنتجات الـ 10 (أقل من 5)
- **النتيجة المتوقعة:** **Dashboard مقفول** — رسالة: "نحتاج تكاليف 5 منتجات على الأقل لنحسب ربحك"
- **الخيارات المعروضة:**
  1. زر "املأ تلقائياً بهامش متوقع" (Smart Defaults)
  2. زر "Bulk Quick Entry" (جدول واحد)
  3. زر "استورد من Excel"
- **بعد الوصول لـ 5 منتجات:** يفتح Dashboard فوراً + Banner لتشجيع إكمال الباقي

#### S-ONB-07: التاجر يستخدم Excel Import
- **Trigger:** اختيار "استورد من Excel" في Step 5
- **النتيجة المتوقعة:** قبول CSV بصيغة محددة (SKU، التكلفة) + معاينة قبل الحفظ + رسالة بنتائج التحديث
- **حالات الفشل:** صيغة خاطئة → عرض السطر الخاطئ مع توضيح + إمكانية تعديل وإعادة المحاولة

#### S-ONB-08: التاجر لديه فروع متعددة في سلة
- **Trigger:** متجر فيه عدة فروع (Branches)
- **النتيجة المتوقعة:** V1 يعامل كل الفروع كمصدر واحد، يجمع طلباتها
- **الإجراء:** ملاحظة في Dashboard: "البيانات تشمل كل فروعك — التقسيم بالفرع متاح في V2"

#### S-ONB-09: انقطاع الإنترنت أثناء Onboarding
- **Trigger:** فقدان الاتصال خلال أي خطوة
- **النتيجة المتوقعة:** رسالة "اتصالك انقطع — حفظنا تقدّمك" + زر "أعد الاتصال"
- **التحقق:** عند العودة، تستأنف من نفس الخطوة بدون فقدان بيانات

#### S-ONB-10: التاجر بنفس الإيميل يحاول التسجيل مرتين
- **Trigger:** إيميل مسجّل سابقاً
- **النتيجة المتوقعة:** رسالة "هذا الإيميل مسجّل — هل نسيت كلمة المرور؟" + زر "تسجيل دخول"
- **حالة خاصة:** إذا الحساب القديم مرتبط بمتجر مختلف → "إيميلك مرتبط بمتجر X، تواصل معنا لتغييره"

#### S-ONB-11: محاولة ربط متجر مرتبط بحساب آخر
- **Trigger:** نفس `salla_store_id` موجود لتاجر آخر
- **النتيجة المتوقعة:** رفض الربط مع رسالة: "هذا المتجر مربوط بحساب آخر. تواصل مع الدعم"
- **الأمان:** منع تعدّد الحسابات لنفس المتجر (يحمي من الاحتيال أو التضارب)

#### S-ONB-12: التاجر يبدأ من الجوال ثم ينتقل للديسكتوب
- **Trigger:** بدء Onboarding على جوال، فتح التطبيق على ديسكتوب
- **النتيجة المتوقعة:** الجلسة تستمر، التقدّم محفوظ، يكمل من حيث توقّف
- **التحقق:** حفظ التقدّم في الـ DB لا في localStorage فقط

---

### 18.2 سيناريوهات OAuth والـ Token

#### S-AUTH-01: انتهاء صلاحية Access Token
- **Trigger:** Token خلصت مدته (افتراضي 24 ساعة)
- **النتيجة المتوقعة:** استخدام Refresh Token تلقائياً للتجديد، بدون أي تأثير للتاجر
- **الفشل:** إذا فشل التجديد → تنبيه التاجر "يرجى إعادة ربط متجرك"

#### S-AUTH-02: التاجر يلغي تفويض التطبيق من سلة
- **Trigger:** التاجر يحذف التطبيق من Salla Apps Dashboard
- **النتيجة المتوقعة:** Webhook `app.uninstalled` يصل، نُجمّد الحساب، نُرسل إيميل "نأسف لرحيلك"
- **حفظ البيانات:** الاحتفاظ ببيانات التاجر 30 يوم قبل الحذف الدائم

#### S-AUTH-03: التاجر يُعيد التثبيت بعد الإلغاء
- **Trigger:** نفس `salla_store_id` يحاول الربط مرة أخرى
- **إذا في فترة 30 يوم:** استعادة كاملة للبيانات، رسالة ترحيب بالعودة
- **إذا بعد 30 يوم:** التعامل كمستخدم جديد

#### S-AUTH-04: محاولة تسجيل دخول متعددة فاشلة (Brute Force)
- **Trigger:** 5 محاولات خاطئة لكلمة المرور
- **النتيجة المتوقعة:** قفل الحساب 15 دقيقة + إشعار للتاجر بمحاولات مشبوهة
- **بعد 10 محاولات في ساعة:** قفل دائم حتى تواصل الدعم + Captcha

#### S-AUTH-05: تسجيل دخول من جهاز/مكان غير معتاد
- **Trigger:** IP جديد + بصمة جهاز جديدة
- **النتيجة المتوقعة:** إشعار WhatsApp/Email للتاجر "تم تسجيل دخول جديد" مع زر "ليس أنا"
- **الإجراء على "ليس أنا":** قفل فوري + مطالبة بتغيير كلمة المرور

#### S-AUTH-06: تغيير صلاحيات API من سلة
- **Trigger:** سلة تُضيف Scope جديد إلزامي
- **النتيجة المتوقعة:** عند فشل API call بسبب صلاحية، طلب من التاجر إعادة الموافقة
- **التواصل:** إشعار جماعي قبل أسبوع إذا كان متوقعاً

---

### 18.3 سيناريوهات حساب الربح للطلب

#### S-CALC-01: طلب قياسي بكل البيانات الكاملة
- **المدخلات:** Subtotal=200, Discount=30, COGS=90, PaymentFee=7, ShippingActual=25, ShippingCollected=20
- **النتيجة:** Net Profit = 68 ريال، Margin = 34%
- **العرض:** بطاقة خضراء، تفاصيل قابلة للنقر

#### S-CALC-02: طلب بدون cost_price لمنتج
- **Trigger:** أحد منتجات الطلب بدون تكلفة
- **النتيجة المتوقعة:** الحساب يُجرى متجاهلاً COGS لذلك المنتج، شارة "تكلفة ناقصة" + زر "أدخل التكلفة الآن"
- **العلامة:** الربح يعرض كـ "تقديري" حتى تُدخل التكلفة

#### S-CALC-03: طلب بكل المنتجات بدون تكلفة
- **Trigger:** صفر منتجات لها cost_price
- **النتيجة المتوقعة:** بطاقة الربح تظهر "غير متاح بعد" + إرشاد كبير لإدخال التكاليف
- **عدم تضليل:** لا نُظهر صفر أو رقم خاطئ

#### S-CALC-04: طلب ربحه سالب (خاسر)
- **Trigger:** Net Profit < 0
- **النتيجة المتوقعة:** بطاقة حمراء + شارة "خاسر" + تنبيه فوري + أسباب: "السبب الرئيسي: تكلفة شحن أعلى من المُحصّل"
- **الإجراء التلقائي:** إضافة الطلب لقائمة "الطلبات الخاسرة" + إشعار

#### S-CALC-05: طلب بهامش ضئيل (< 5%)
- **النتيجة المتوقعة:** بطاقة صفراء + شارة "هامش ضعيف"
- **في Daily Pulse:** يُذكر "X طلب أمس بهامش أقل من 5%"

#### S-CALC-06: طلب بخصم 100% (مجاني)
- **Trigger:** قيمة الكوبون = إجمالي السلة
- **النتيجة المتوقعة:** Net Profit = -COGS - shipping - fees، يُحسب كخسارة كاملة
- **التنبيه:** "كوبون مجاني — تحقق من قاعدته"

#### S-CALC-07: طلب يحوي عدة كوبونات (Stackable)
- **Trigger:** سلة تسمح بكوبونات متعددة (نادر)
- **النتيجة المتوقعة:** جمع كل الخصومات في حقل Discount واحد + عرض تفاصيل الكوبونات في breakdown
- **حد الأمان:** إن جمع الخصومات > 50% من Subtotal → تنبيه فوري

#### S-CALC-08: طلب بكوبون شحن مجاني فقط
- **Trigger:** كوبون يخفّض الشحن إلى صفر
- **النتيجة المتوقعة:** Discount = 0 (لا يُحسب كخصم منتج)، Shipping Collected = 0، Shipping Actual يبقى
- **التأثير:** نتحمّل تكلفة الشحن كاملة → تنبيه إن كانت > 15% من الطلب

#### S-CALC-09: طلب مرتجع كلياً
- **Trigger:** Webhook `order.refunded` بكامل القيمة
- **النتيجة المتوقعة:** تحديث `order_profits.net_profit` ليصبح -fees - shipping_actual (الخسارة من الرسوم وتكلفة الشحن العائد)
- **في الإحصاءات:** يُستبعد من إحصاءات الربح الإيجابي، يُضاف لقائمة المرتجعات

#### S-CALC-10: طلب مرتجع جزئياً
- **Trigger:** Webhook `order.refunded` بقيمة أقل من الإجمالي
- **النتيجة المتوقعة:** إعادة حساب الربح بناءً على المنتجات المتبقية فقط
- **التتبع:** عرض "رد جزئي: X ريال" في بطاقة الطلب

#### S-CALC-11: طلب ملغى قبل الشحن
- **Trigger:** Webhook `order.cancelled`
- **النتيجة المتوقعة:** لا يُحتسب في الربح، يظهر في قائمة الطلبات بحالة "ملغى" مع لون رمادي

#### S-CALC-12: طلب معدّل بعد الإنشاء (تغيّر السعر/الكمية)
- **Trigger:** Webhook `order.updated`
- **النتيجة المتوقعة:** إعادة حساب كاملة، حفظ نسخة قبل وبعد للمراجعة
- **الإشعار:** إذا تغيّر الربح بنسبة > 20% → تنبيه

#### S-CALC-13: طلب قبل تثبيت التطبيق (تاريخي)
- **Trigger:** طلب تاريخه قبل تاريخ ربط المتجر
- **النتيجة المتوقعة:** يُحسب بناءً على cost_price الحالي (تقريبي) + شارة "تكاليف تاريخية تقديرية"
- **الشفافية:** "هذا الطلب من قبل تثبيت Margin Hero — التكاليف قد لا تعكس الواقع وقتها"

#### S-CALC-14: تغيير cost_price لمنتج باع سابقاً
- **Trigger:** التاجر يعدّل التكلفة من 50 إلى 60 ريال
- **النتيجة المتوقعة:** الطلبات السابقة تحتفظ بـ cost_price القديم (snapshot)، الطلبات الجديدة تستخدم الجديد
- **خيار اختياري:** زر "أعد حساب الطلبات السابقة بهذه التكلفة" (تحذير: يغيّر التاريخ)

#### S-CALC-15: طلب بمنتج له variants مختلفة الأسعار/التكاليف
- **Trigger:** منتج واحد بـ 5 ألوان مثلاً، كل لون له cost_price مختلف
- **النتيجة المتوقعة:** الحساب يستخدم cost_price للـ variant المحدد بالضبط
- **التحقق:** عرض variant في تفاصيل بطاقة الطلب

#### S-CALC-16: طلب بمنتج Bundle (حزمة)
- **Trigger:** سلة تدعم منتجات Bundle
- **النتيجة المتوقعة:** COGS = مجموع تكاليف المنتجات داخل الـ Bundle
- **الفشل:** إن لم نستطع تفكيك الـ Bundle → نستخدم cost_price للـ Bundle نفسه

#### S-CALC-17: طلب دولي بعملة مختلفة
- **Trigger:** Order currency != Store currency (نادر في V1)
- **النتيجة المتوقعة:** تحويل لعملة المتجر بسعر يوم الطلب، تنبيه "تم التحويل من USD"
- **ملاحظة V1:** قد لا ندعمه — رسالة "هذا الطلب بعملة أخرى — لا يُحسب بعد"

#### S-CALC-18: عدم دقة عشرية (Rounding)
- **Trigger:** ضرب نسبة على مبلغ → كسور
- **القاعدة:** كل المبالغ تُقرّب لخانتين عشريتين، الجمع يُجرى أولاً ثم التقريب
- **التوحيد:** نستخدم مكتبة Decimal لتجنّب float drift

#### S-CALC-19: طلب بضريبة عالية (15% VAT)
- **Trigger:** الطلب يحوي مبلغ ضريبة
- **القاعدة:** الضريبة لا تُحسب من الربح (تذهب للحكومة)، تُعرض فقط للشفافية
- **التحقق:** Total = Subtotal + Tax + Shipping - Discount

#### S-CALC-20: طلب بطريقة دفع غير معروفة
- **Trigger:** `payment_method` غير موجود في Fee Engine
- **النتيجة المتوقعة:** استخدام نسبة افتراضية 2.5% + شارة "بوابة غير معروفة" + إشعار للتاجر لإضافتها

---

### 18.4 سيناريوهات المنتجات والتكاليف

#### S-PROD-01: إضافة منتج جديد في سلة
- **Trigger:** Webhook `product.created`
- **النتيجة المتوقعة:** المنتج يظهر في القائمة بدون تكلفة، شارة "أدخل التكلفة"
- **التذكير:** بعد 7 أيام بدون تكلفة → إشعار مذكِّر

#### S-PROD-02: حذف منتج في سلة
- **Trigger:** Webhook `product.deleted`
- **النتيجة المتوقعة:** المنتج يُخفى من القائمة الحالية، لكن يبقى في تاريخ الطلبات بشارة "محذوف"
- **عدم فقدان البيانات:** الطلبات السابقة تحتفظ بـ snapshot للسعر والتكلفة

#### S-PROD-03: تغيير سعر بيع المنتج
- **Trigger:** Webhook `product.updated` مع تغيّر في السعر
- **النتيجة المتوقعة:** الطلبات السابقة لا تتأثر، الطلبات الجديدة تستخدم السعر الجديد
- **المتابعة:** عرض تاريخ تغيّرات السعر في صفحة المنتج

#### S-PROD-04: cost_price > selling_price (تكلفة أعلى من السعر)
- **Trigger:** التاجر يدخل تكلفة 100 لمنتج سعره 80
- **النتيجة المتوقعة:** قبول الإدخال (قد يكون منتج "loss leader" مقصود) + تنبيه قوي: "تبيع هذا المنتج بخسارة على كل قطعة"
- **العرض:** المنتج يظهر بشارة "loss leader" في القائمة

#### S-PROD-05: cost_price = 0
- **Trigger:** التاجر يدخل صفر
- **النتيجة المتوقعة:** قبول (قد يكون هدية ترويجية) + شارة "تكلفة صفرية مؤكدة"
- **التمييز عن "تكلفة ناقصة":** Null vs 0 — رمز مختلف

#### S-PROD-06: cost_price سالب
- **Trigger:** إدخال قيمة سالبة
- **النتيجة المتوقعة:** رفض المدخل، رسالة "التكلفة لا يمكن أن تكون سالبة"

#### S-PROD-07: منتج بكميات بـ 0 (نفد المخزون)
- **النتيجة المتوقعة:** يبقى في القائمة، لا يؤثر على الحساب — فقط المباع يُحسب

#### S-PROD-08: تحديث مجمّع لتكاليف 100+ منتج
- **Trigger:** التاجر يستورد ملف Excel كبير
- **النتيجة المتوقعة:** معالجة في الخلفية، مؤشر تقدّم، إشعار عند الانتهاء
- **حد الأمان:** سقف 5,000 منتج لكل عملية import

#### S-PROD-09: منتج بـ SKU مكرر (نادر، أخطاء بيانات)
- **Trigger:** نفس SKU لمنتجين مختلفين في سلة
- **النتيجة المتوقعة:** نعتمد على Salla Product ID لا SKU، نعرض تنبيه "SKU مكرر"

#### S-PROD-10: منتج بدون اسم أو بيانات ناقصة
- **النتيجة المتوقعة:** عرض "منتج بدون اسم" + ID + رابط لتحريره في سلة

---

### 18.5 سيناريوهات الخصومات والكوبونات

#### S-DISC-01: كوبون يخفّض الهامش تحت العتبة لأول مرة
- **Trigger:** أول طلب باستخدام كوبون SUMMER10، الهامش هبط من 28% إلى 7%
- **النتيجة المتوقعة:** تنبيه فوري للتاجر مع تفاصيل
- **القناة:** WhatsApp + In-App

#### S-DISC-02: نفس الكوبون يُستخدم 12 مرة في 24 ساعة
- **النتيجة المتوقعة:** تجميع التنبيهات بدلاً من إرسال 12 إشعاراً → إشعار مجمّع: "الكوبون SUMMER10 طُبّق على 12 طلب"
- **القاعدة:** Aggregation كل 4 ساعات أو بعد 5 طلبات (الأسبق)

#### S-DISC-03: كوبون أوقفه التاجر بعد التنبيه
- **Trigger:** التاجر يضغط "أوقف الكوبون" في التنبيه
- **النتيجة المتوقعة:** تحديث الكوبون في سلة عبر API ليصبح غير نشط، رسالة "تم الإيقاف"
- **التتبع:** حدث "discount_alert_action_taken" يُسجّل لقياس قيمة التنبيهات

#### S-DISC-04: كوبون التاجر يقصد استخدامه (Influencer)
- **Trigger:** كوبون "AHMED20" مخصص لشخصية مؤثّرة، الخسارة مقصودة (تكلفة تسويق)
- **الحل:** خيار "استثنِ هذا الكوبون من التنبيهات" في إعدادات
- **التصنيف:** التاجر يضع علامة "كوبون تسويقي" — لا يظهر في تقرير "الكوبونات الضارة"

#### S-DISC-05: كوبون موظفين بنسبة 50%
- **مماثل لـ S-DISC-04:** التاجر يضع علامة "كوبون داخلي" — يُستثنى من التنبيهات

#### S-DISC-06: كوبون "Buy 2 Get 1 Free"
- **Trigger:** خصم على كمية معيّنة
- **النتيجة المتوقعة:** الحساب يُجرى على إجمالي الخصم النهائي في الطلب (لا تفاصيل المنطق)
- **القاعدة:** نعتمد على `order.discount` كصافي

#### S-DISC-07: كوبون منتهي الصلاحية ما زال في طلب قديم
- **النتيجة المتوقعة:** يُحسب في الطلب القديم بشكل عادي، لا يؤثر على المستقبل

#### S-DISC-08: التاجر يرفع العتبة من 10% إلى 5%
- **النتيجة المتوقعة:** التنبيهات السابقة تبقى، الجديدة تستخدم العتبة الجديدة
- **التحذير:** "ستحصل على تنبيهات أقل — تأكد"

#### S-DISC-09: التاجر يُلغي كل تنبيهات الخصومات
- **النتيجة المتوقعة:** قبول مع رسالة تحذيرية بارزة: "أنت توقف ميزة الحماية الأهم — هل أنت متأكد؟"
- **استثناء أمان:** Loss Order Alert (طلب خاسر فعلياً) لا يمكن إيقافه

#### S-DISC-10: كوبون "Free Shipping" يجعل تكلفة الشحن خسارة
- **Trigger:** كوبون يضع shipping_collected = 0 لكن shipping_actual = 30
- **النتيجة المتوقعة:** التنبيه يبرز: "هذا الكوبون يكلّفك 30 ريال شحن لكل طلب"

---

### 18.6 سيناريوهات بوابات الدفع

#### S-PAY-01: التاجر يستخدم Mada فقط
- **النتيجة المتوقعة:** كل الطلبات تطبّق نسبة 1.8%

#### S-PAY-02: التاجر يستخدم 5 بوابات مختلفة
- **النتيجة المتوقعة:** كل طلب يأخذ نسبته حسب payment_method الفعلي
- **التحقق:** breakdown شهري يعرض الرسوم لكل بوابة

#### S-PAY-03: نسبة Tamara تتغيّر (تفاوض جديد)
- **Trigger:** التاجر يعدّل النسبة من 3.5% إلى 3.0%
- **النتيجة المتوقعة:** التغيير يطبّق على الطلبات الجديدة فقط
- **خيار:** "هل تريد تطبيقه على الطلبات السابقة؟" (مع تحذير)

#### S-PAY-04: بوابة دفع لم تكن في القائمة
- **Trigger:** التاجر فعّل بوابة "Hyperpay" مثلاً غير مدعومة
- **النتيجة المتوقعة:** نسبة افتراضية 2.5% + إشعار للتاجر "أضف نسبة Hyperpay الخاصة بك"
- **متابعة المنتج:** إضافتها للـ Catalog إن طلبها أكثر من 5 تجار

#### S-PAY-05: COD مع رسوم شركة الشحن
- **Trigger:** الدفع عند الاستلام، الشركة تأخذ 2% من المبلغ
- **النتيجة المتوقعة:** خيار للتاجر: "أضف رسم تحصيل COD" → نسبة + ثابت
- **القاعدة الافتراضية:** 0% للـ COD نفسه، الرسم يُضاف ضمن "تكلفة الشحن"

#### S-PAY-06: دفع بالتقسيط (Tamara) — العميل يدفع على 3 دفعات
- **النتيجة المتوقعة:** نحسب الرسم على المبلغ الكامل (سلة تحصّل من Tamara كاملاً)
- **عدم الخلط:** لا نحسب الرسم 3 مرات

#### S-PAY-07: Apple Pay على بطاقة Mada
- **النتيجة المتوقعة:** نطبّق نسبة Mada (1.8%) لا Apple Pay
- **القاعدة:** لو سلة أعطت `payment_method = applepay_mada` → نطابق Mada
- **الفولباك:** إذا غير واضح → نسبة Apple Pay الافتراضية 2.5%

#### S-PAY-08: محاولة دفع فاشلة ثم نجاح
- **النتيجة المتوقعة:** فقط الطلب الناجح يصل، لا نحسب رسم على المحاولة الفاشلة

---

### 18.7 سيناريوهات الشحن والمرتجعات

#### S-SHIP-01: تاجر لم يُدخل تكلفة شحن فعلية
- **النتيجة المتوقعة:** نستخدم Shipping Collected كتقدير + شارة "تقديري"
- **الإرشاد:** "أدخل تكلفة الشحن الفعلية لدقة أعلى"

#### S-SHIP-02: تاجر يستخدم متوسط شحن ثابت (مثلاً 25 ريال)
- **الإعدادات:** خيار "استخدم متوسط شحن" → 25 ريال لكل طلب
- **النتيجة المتوقعة:** كل الطلبات تخصم 25 ريال شحن

#### S-SHIP-03: تكامل مع شركة شحن (V2)
- **مستقبلاً:** سحب التكلفة الفعلية من Aramex/SMSA API
- **في V1:** إدخال يدوي أو متوسط

#### S-SHIP-04: شحن مجاني (التاجر يتحمّل بالكامل)
- **Trigger:** Shipping Collected = 0 (سياسة المتجر)
- **النتيجة المتوقعة:** نخصم Shipping Actual كاملاً من الربح، تنبيه إن > 15% من إجمالي الطلب

#### S-RET-01: مرتجع كامل بعد 24 ساعة من البيع
- **Trigger:** Webhook `order.refunded`
- **النتيجة المتوقعة:** Net Profit = -PaymentFee - ShippingActual_outgoing - ShippingActual_return
- **التتبع:** الطلب يدخل قائمة "المرتجعات" وتقرير شهري

#### S-RET-02: مرتجع جزئي (منتج واحد من 3)
- **النتيجة المتوقعة:** إعادة حساب ربح المنتجين المتبقيين فقط
- **القاعدة:** الشحن لا يُسترجع غالباً → يبقى مخصوماً

#### S-RET-03: استبدال (لا مرتجع نقدي)
- **Trigger:** العميل بدّل منتجاً بآخر
- **النتيجة المتوقعة:** يُعامل كطلب جديد مع تكاليف شحن إضافية
- **التتبع:** إذا تكرّر الاستبدال لنفس العميل > 3 مرات → علامة "عميل مكلف"

#### S-RET-04: معدل مرتجعات مرتفع لمنتج
- **Trigger:** منتج معدل مرتجعاته > 20% (V1.5)
- **النتيجة المتوقعة:** تنبيه شهري: "هذا المنتج 30% منه يُرتجع — راجع الجودة أو الوصف"

---

### 18.8 سيناريوهات المزامنة والـ Webhooks

#### S-SYNC-01: Webhook يصل بنجاح
- **النتيجة المتوقعة:** معالجة في < 5 ثواني، تحديث DB، تحديث Dashboard real-time إن مفتوح
- **التحقق:** Audit log لكل webhook

#### S-SYNC-02: Webhook مكرّر (نفس الـ event مرتين)
- **Trigger:** سلة ترسله مرتين (شائع، يحدث طبيعياً)
- **النتيجة المتوقعة:** معالجة مرة واحدة فقط (Idempotency Key على event_id)
- **القاعدة:** كل event يُسجّل في `processed_webhooks` أولاً

#### S-SYNC-03: Webhook يصل خارج الترتيب (out of order)
- **Trigger:** `order.updated` يصل قبل `order.created` (نادر)
- **النتيجة المتوقعة:** إذا الطلب غير موجود في DB → تجاهل مؤقت + استعلام مباشر من Salla API لجلبه
- **الفولباك:** Reconciliation Job اليومي يلتقط الفائت

#### S-SYNC-04: Webhook يفشل في المعالجة
- **Trigger:** خطأ DB أو API timeout
- **النتيجة المتوقعة:** إعادة المحاولة 3 مرات بـ exponential backoff (1s, 5s, 15s)
- **بعد 3 محاولات:** إرسال لـ Dead Letter Queue + تنبيه فريق الدعم

#### S-SYNC-05: انقطاع طويل عن Salla (ساعات)
- **Trigger:** Salla API down لساعتين
- **النتيجة المتوقعة:** Webhooks تتراكم في Salla side، Polling Job يلتقطها عند العودة
- **الإشعار:** "خدمة Salla تعاني — البيانات قد تتأخر دقائق"

#### S-SYNC-06: Reconciliation Job يكتشف 5 طلبات فائتة
- **Trigger:** الجوب اليومي يقارن طلبات Salla مع DB
- **النتيجة المتوقعة:** سحب الطلبات الفائتة، إعادة الحساب، تسجيل سبب الفقد
- **التحسين:** استخدام السبب لتحسين Webhook handling

#### S-SYNC-07: Salla تُرسل بيانات غير صحيحة (نادر)
- **Trigger:** order.total = null مثلاً
- **النتيجة المتوقعة:** رفض المعالجة، تسجيل في error log، استعلام مباشر للـ Order للتأكد
- **الإبلاغ:** فريق Salla Partner

#### S-SYNC-08: Rate Limit من Salla API
- **Trigger:** تجاوزنا 60 req/min
- **النتيجة المتوقعة:** Token Bucket queues الطلبات، تأخير معقول < 30 ثانية
- **عند الأزمة:** اقتراح ترقية الـ rate limit مع Salla Partner

#### S-SYNC-09: التاجر يضيف 100 منتج دفعة واحدة
- **Trigger:** Bulk import في سلة → 100 webhook
- **النتيجة المتوقعة:** معالجة بالطابور بدون انفجار
- **الأداء:** كل المنتجات تظهر خلال 10 دقائق كحد أقصى

#### S-SYNC-10: التاجر يحذف 50 منتج
- **النتيجة المتوقعة:** نُخفيها من القائمة الحالية، نحتفظ بـ history لتقارير ماضية

---

### 18.9 سيناريوهات الإشعارات

#### S-NOT-01: WhatsApp وصل بنجاح
- **التحقق:** delivery_status = "delivered" في WhatsApp API
- **التتبع:** نسجّل وقت التسليم لتحليل القنوات

#### S-NOT-02: WhatsApp فشل (رقم خاطئ)
- **النتيجة المتوقعة:** Fallback تلقائي لـ Email + إشعار In-App بارز "حدّث رقمك"

#### S-NOT-03: التاجر حظر رقم WhatsApp Business
- **الكشف:** فشل متكرر للـ delivery
- **النتيجة المتوقعة:** بعد 3 إخفاقات متتالية → إيقاف WhatsApp تلقائياً + Email "نلاحظ مشكلة"

#### S-NOT-04: تنبيهات متعددة في وقت واحد
- **Trigger:** 5 طلبات بنفس الكوبون خلال دقيقة
- **النتيجة المتوقعة:** Aggregation — إشعار واحد بدل 5
- **القاعدة:** لا أكثر من 3 إشعارات WhatsApp في اليوم

#### S-NOT-05: إشعار في وقت الهدوء (10م-7ص)
- **النتيجة المتوقعة:** الإشعارات العادية تنتظر للصباح، الـ Critical (Loss Order) تُرسل فوراً

#### S-NOT-06: التاجر غيّر رقم الجوال
- **الإجراء:** بعد التحديث، رسالة تأكيد على الرقم القديم (إن أمكن) + الجديد
- **الأمان:** OTP على الرقم الجديد قبل التأكيد

#### S-NOT-07: Daily Pulse في يوم بدون طلبات
- **النتيجة المتوقعة:** رسالة بديلة: "لا طلبات أمس — مجموع الشهر حتى الآن: X ريال"
- **الخيار:** إيقاف Pulse في الأيام بدون طلبات (تفضيل التاجر)

#### S-NOT-08: التاجر مسافر (timezone مختلف)
- **النتيجة المتوقعة:** Daily Pulse يبقى على timezone المتجر (Asia/Riyadh)، لا يتغيّر بسفر التاجر
- **خيار:** تعديل التوقيت يدوياً

#### S-NOT-09: Email في Spam
- **الكشف:** نسبة الفتح المنخفضة لتاجر معيّن
- **الإجراء:** نطلب منه إضافة domain إلى whitelist + استخدام WhatsApp بديلاً

#### S-NOT-10: WhatsApp Provider يفشل (downtime)
- **Trigger:** 360dialog أو Salla WhatsApp API down
- **النتيجة المتوقعة:** Fallback لـ Email تلقائياً + In-App
- **التذكير:** عند عودة الخدمة، إشعار إضافي

---

### 18.10 سيناريوهات الاشتراكات والفوترة

#### S-SUB-01: التاجر يبدأ التجربة المجانية
- **النتيجة المتوقعة:** 14 يوم وصول كامل، عداد عكسي بارز، إشعار في يوم 11 و13

#### S-SUB-02: تجربة انتهت بدون اشتراك
- **النتيجة المتوقعة:** يوم 15 → الحساب يُجمّد (Read-only)، البيانات محفوظة
- **الرسالة:** "اشترك لاستعادة الوصول الكامل"

#### S-SUB-03: تجربة انتهت بنجاح (اشترك)
- **النتيجة المتوقعة:** انتقال سلس، أول فاتورة في يوم 15
- **الإشعار:** "مرحباً بك كعضو دائم"

#### S-SUB-04: ترقية من Starter إلى Growth
- **النتيجة المتوقعة:** الميزات تُفعّل فوراً، فاتورة Prorated
- **التواصل:** "استمتع بـ WhatsApp الكامل من الآن"

#### S-SUB-05: تخفيض من Pro إلى Starter
- **النتيجة المتوقعة:** التخفيض يطبّق في الدورة التالية، ليس فوراً
- **التحذير:** "ستفقد X ميزات في 1 يونيو"

#### S-SUB-06: فشل الدفع التلقائي للتجديد
- **Trigger:** بطاقة منتهية أو رصيد غير كافٍ
- **النتيجة المتوقعة:** 3 محاولات (يوم 1, 3, 7)، إشعار قبل كل محاولة
- **بعد 7 أيام فشل:** تجميد الحساب + رسالة "حدّث طريقة الدفع"

#### S-SUB-07: التاجر طلب استرداد
- **القاعدة:** خلال 7 أيام من أول دفعة، استرداد كامل بدون أسئلة
- **بعد 7 أيام:** مراجعة يدوية، استرداد جزئي ممكن

#### S-SUB-08: الإلغاء في منتصف الشهر
- **النتيجة المتوقعة:** الوصول يستمر حتى نهاية الدورة المدفوعة، لا تجديد بعدها
- **خيار:** "ألغِ فوراً" مع تنازل عن المتبقي

#### S-SUB-09: تجاوز حد الطلبات (Starter — 100 طلب)
- **عند 80%:** "اقتربت من حدك (80 من 100)"
- **عند 100%:** "بلغت حدك — رقّ لـ Growth للاستمرار" + اقتراح Prorated
- **عند 110% لـ 3 أيام:** تجميد الميزات الإضافية، الأساسيات تستمر

#### S-SUB-10: التاجر يكرّر الاشتراك بعد إلغاء
- **النتيجة المتوقعة:** لا تجربة جديدة (مرة واحدة فقط)، يعود مباشرة لخطة مدفوعة
- **استثناء:** بعد 6 أشهر من الإلغاء، يُسمح بتجربة جديدة (تشجيع للعودة)

#### S-SUB-11: محاولة استخدام كود خصم منتهي
- **النتيجة المتوقعة:** رسالة "هذا الكود انتهى — جرّب: WELCOME50" (إن وجد بديل)

#### S-SUB-12: ضرائب على الفاتورة (15% VAT)
- **القاعدة:** السعر المعلن 99 ريال = 99 + VAT للفاتورة، أو 99 شامل (قرار في Open Question #5)

---

### 18.11 سيناريوهات الأمان والوصول

#### S-SEC-01: تاجر يحاول الوصول لبيانات تاجر آخر
- **Trigger:** تعديل URL ليحوي order_id لمتجر آخر
- **النتيجة المتوقعة:** 403 Forbidden + تسجيل المحاولة + تنبيه فريق الأمان

#### S-SEC-02: SQL Injection في حقل البحث
- **النتيجة المتوقعة:** الفصل بين queries والـ parameters (Prepared Statements)، لا تنفيذ
- **الاختبار:** OWASP top 10 ضمن QA suite

#### S-SEC-03: XSS في اسم المنتج (input من Salla)
- **النتيجة المتوقعة:** كل المخرجات escape بـ HTML encoding
- **الاختبار:** input بـ `<script>alert(1)</script>` → يظهر كنص

#### S-SEC-04: Token مسرَّب
- **الكشف:** استخدام token من IP غير معتاد
- **الإجراء:** إبطال فوري، إخطار التاجر، طلب إعادة ربط

#### S-SEC-05: محاولة DDoS
- **النتيجة المتوقعة:** Cloudflare/AWS Shield يلتقط، Rate Limiting طبقات
- **التحقق:** SLA يبقى ≥ 99.5%

#### S-SEC-06: طلب حذف بيانات (GDPR/PDPL)
- **النتيجة المتوقعة:** خلال 30 يوم، حذف كامل لكل البيانات الشخصية
- **الاحتفاظ:** فقط الأرقام المجمّعة المجهّلة للإحصاءات

#### S-SEC-07: طلب تصدير بيانات
- **النتيجة المتوقعة:** ZIP يحوي JSON بكل بيانات الحساب، يصل بريداً خلال 24 ساعة

#### S-SEC-08: نسيان كلمة المرور
- **النتيجة المتوقعة:** Email + WhatsApp بـ link صالح ساعة واحدة
- **الأمان:** لا نقول "هذا الإيميل غير مسجّل" (نقول دائماً "إن وُجد، سنرسل")

#### S-SEC-09: 2FA (V1.5)
- **مقترح:** OTP عبر WhatsApp عند تسجيل الدخول من جهاز جديد
- **في V1:** اختياري

#### S-SEC-10: تعديل cost_price بكميات كبيرة (مشبوه)
- **Trigger:** تعديل > 50 منتج في ساعة
- **النتيجة المتوقعة:** تأكيد إضافي + Audit log + تنبيه

---

### 18.12 سيناريوهات جودة البيانات والقيم الحدّية

#### S-DATA-01: قيم مالية كبيرة جداً
- **Trigger:** طلب بمبلغ 999,999,999 ريال (نادر، أخطاء)
- **النتيجة المتوقعة:** قبول لكن مع شارة "قيمة غير اعتيادية"
- **حد التصميم:** DECIMAL(12,2) يدعم 9,999,999,999.99

#### S-DATA-02: قيم مالية صغيرة جداً
- **Trigger:** طلب بـ 0.01 ريال (نادر، اختبار)
- **النتيجة المتوقعة:** قبول، الحساب يعمل

#### S-DATA-03: تاريخ في المستقبل
- **Trigger:** order.created_at = 2030
- **النتيجة المتوقعة:** قبول لكن تنبيه + استعلام Salla للتأكد

#### S-DATA-04: تاريخ قديم جداً
- **Trigger:** طلب من 2015 (نادر، ترحيل بيانات)
- **النتيجة المتوقعة:** قبول، يدخل في تاريخ "أكثر من 12 شهر"

#### S-DATA-05: نص بأحرف خاصة (إيموجي، رموز)
- **النتيجة المتوقعة:** UTF-8 يدعم كل شيء، التخزين والعرض يعملان

#### S-DATA-06: أسماء طويلة جداً
- **Trigger:** اسم منتج 500 حرف
- **النتيجة المتوقعة:** التخزين كامل، العرض مع truncate + tooltip

#### S-DATA-07: حقول NULL في Salla
- **النتيجة المتوقعة:** لكل حقل قاعدة fallback، لا 500 errors

#### S-DATA-08: تكرار في DB
- **النتيجة المتوقعة:** Unique constraints على salla_*_id لمنع التكرار

#### S-DATA-09: تدمج timezone
- **القاعدة:** كل التواريخ في DB بـ UTC، التحويل في الـ Frontend حسب timezone المتجر

#### S-DATA-10: عملة مختلفة لطلب واحد (نادر)
- **النتيجة المتوقعة:** التحويل بسعر يوم الطلب من API ثالث، أو تجاهل + شارة

---

### 18.13 سيناريوهات الأداء والحجم

#### S-PERF-01: متجر بـ 10,000 منتج
- **النتيجة المتوقعة:** Product Margin List مع pagination + virtual scrolling
- **الأداء:** أول 50 منتج < 1 ثانية

#### S-PERF-02: متجر بـ 50,000 طلب في السنة
- **النتيجة المتوقعة:** الإحصاءات الشهرية pre-computed (cron job)
- **التحديث:** Real-time للشهر الحالي، historical من cache

#### S-PERF-03: 100 تاجر يدخلون في نفس الثانية
- **النتيجة المتوقعة:** Auto-scaling على AWS، لا degradation
- **الاختبار:** Load test قبل GA

#### S-PERF-04: Black Friday — حجم 10× المعتاد
- **النتيجة المتوقعة:** البنية التحتية تتحمّل، تنبيه فريق DevOps قبل الموسم
- **الاحتياط:** Pre-warm الكاش، increase rate limits

#### S-PERF-05: استعلام Dashboard بطيء
- **الكشف:** P95 > 2 ثانية
- **الإجراء:** Index optimization، cache layer، query review

#### S-PERF-06: صورة منتج كبيرة جداً
- **الإجراء:** Resize تلقائي عبر CDN، lazy loading

---

### 18.14 سيناريوهات الأعمال (لحظات القرار للتاجر)

#### S-BIZ-01: التاجر يكتشف منتج يخسّره
- **اللحظة:** يفتح Product Margin List، يرى منتجاً بهامش -8%
- **الإجراءات المتاحة في التطبيق:**
  - "احسب السعر المثالي" → اقتراح زيادة 20%
  - "أوقف هذا المنتج"
  - "تجاهل" (مع شارة "أنت تعرف")
- **متابعة الأثر:** التطبيق يقيس قراره ويعرضه: "بعد الزيادة، الهامش أصبح 12%"

#### S-BIZ-02: التاجر يطلق كوبون موسمي ضخم
- **التحضير:** قبل الإطلاق، يستطيع "Simulate Coupon" — يرى الأثر المتوقع على الهامش
- **بعد الإطلاق:** Real-time monitoring + تنبيه إن تجاوز الحد

#### S-BIZ-03: التاجر يستلم تقرير شهري ويفاجأ
- **اللحظة:** "ربحت 14,820 ريال — توقعت أكثر"
- **الإجراء:** التقرير يفصّل: "خصوماتك أكلت 4,200" + توصية محددة

#### S-BIZ-04: التاجر يقارن شهرين
- **النتيجة المتوقعة:** Bar chart يبرز التغيّرات + تفسير AI: "السبب الرئيسي للانخفاض: تكلفة الشحن"

#### S-BIZ-05: التاجر يطلب رأياً قبل قرار تسعيري
- **مستقبلاً (V1.5):** Price Scout — تحليل تنافسي
- **في V1:** يستطيع رؤية تاريخ هامش المنتج لاتخاذ قرار

#### S-BIZ-06: التاجر يتجادل مع رقم
- **اللحظة:** "هذا الرقم غلط، تكلفتي مو 50"
- **الإجراء:** breakdown شفاف لكل رقم + رابط "أبلغ عن خطأ"
- **الشفافية:** كل حساب قابل للتدقيق سطر سطر

#### S-BIZ-07: التاجر يطلب ميزة جديدة
- **القناة:** زر "اقترح ميزة" في الإعدادات
- **الإجراء:** يصل لفريق المنتج، تجميع الطلبات، روادمب public

#### S-BIZ-08: التاجر ينصح صديقه
- **مستقبلاً:** نظام إحالات — كود خصم له ولصديقه

---

### 18.15 سيناريوهات حالات الإلغاء والعودة

#### S-LIFE-01: التاجر يحذف التطبيق من Salla
- **الإجراء:** Webhook `app.uninstalled`، تجميد الحساب، حفظ 30 يوم
- **الإيميل:** "نأسف — هل تخبرنا لماذا؟" + استبيان قصير

#### S-LIFE-02: التاجر يُغلق متجره في سلة
- **الإجراء:** عند فشل API بشكل دائم، نفترض الإغلاق، نحفظ البيانات 60 يوم

#### S-LIFE-03: التاجر يعود بعد 4 أشهر
- **النتيجة:** بياناته محذوفة (تجاوز 30 يوم)، يبدأ كحساب جديد
- **الترحيب:** خصم 25% للعائدين الشهر الأول

#### S-LIFE-04: تغيير ملكية المتجر
- **اللحظة:** التاجر باع متجره، المالك الجديد يحاول الربط
- **الإجراء:** نظام تحويل ملكية يدوي عبر الدعم + تحقق هوية

---

### 18.16 سيناريوهات اللغة والتوطين

#### S-I18N-01: التاجر يتنقّل بين عربي/إنجليزي
- **النتيجة المتوقعة:** كل النصوص تتغيّر، الاتجاه RTL/LTR صحيح، الأرقام تبقى لاتينية

#### S-I18N-02: منتج اسمه فيه عربي وإنجليزي مختلط
- **النتيجة المتوقعة:** عرض صحيح بدون كسر RTL

#### S-I18N-03: الإشعار بالعربية ومحتوى الكوبون بالإنجليزية
- **النتيجة المتوقعة:** كل ثابت في القالب يستخدم اللغة المختارة، أسماء الكوبونات تبقى كما هي (لا تُترجم)

#### S-I18N-04: تواريخ هجرية vs ميلادية
- **الافتراضي:** ميلادي
- **الخيار:** تبديل في الإعدادات (V1.5)

---

### 18.17 سيناريوهات حافة (Misc Edge Cases)

#### S-EDGE-01: التاجر يعدّل cost_price ثم يتراجع خلال دقيقة
- **النتيجة:** Audit log يحفظ التغيّرات، Re-calculation idempotent

#### S-EDGE-02: نقطة التحويل من تجربة لمدفوع وقت تجدّد دورة
- **القاعدة:** إن تطابق آخر يوم تجربة مع 1 من الشهر → دورة الدفع تبدأ في 2

#### S-EDGE-03: التاجر يلصق رابط من جهاز آخر
- **النتيجة:** الجلسة معتمدة على الجهاز، يطلب تسجيل دخول

#### S-EDGE-04: محاولة تسجيل بإيميل مؤقت (Disposable)
- **القاعدة:** مكتبة كشف disposable emails، رفض مع رسالة واضحة

#### S-EDGE-05: نشاط في حسابين متزامن (مالك واحد)
- **النتيجة:** السماح، WebSocket لتزامن الـ UI

#### S-EDGE-06: زائر يحاول الوصول لـ URL مدفوع بدون تسجيل
- **النتيجة:** Redirect لـ login + رسالة "سجّل لرؤية ربحك"

#### S-EDGE-07: متصفح قديم (IE 11)
- **النتيجة:** صفحة "متصفحك غير مدعوم" + اقتراح Chrome

#### S-EDGE-08: انقطاع الكهرباء/الإنترنت أثناء كتابة cost_price
- **النتيجة:** Auto-save كل 30 ثانية، استعادة عند العودة

#### S-EDGE-09: التاجر يستخدم Ad Blocker
- **النتيجة:** التطبيق يعمل، Analytics قد لا تُسجّل (مقبول)

#### S-EDGE-10: تاجر يستخدم VPN
- **النتيجة:** قبول، لكن إن كان من دولة محظورة (نادر) → رسالة قانونية

#### S-EDGE-11: ضغط متعدد على زر (Double Submit)
- **النتيجة:** Idempotency Key على الـ POST، لا تكرار

#### S-EDGE-12: Browser back button بعد إجراء حرج
- **النتيجة:** التحقق من الحالة في الـ Backend، ليس Frontend فقط

#### S-EDGE-13: محاولة تحديث صفحة أثناء حفظ
- **النتيجة:** تحذير المتصفح "عمل غير محفوظ"

#### S-EDGE-14: الجهاز نفد الـ disk space (تقارير ضخمة)
- **النتيجة:** Stream للـ download بدلاً من تحميل كامل في الذاكرة

#### S-EDGE-15: التاجر يستخدم العملية في Incognito
- **النتيجة:** الجلسة لا تستمر، لكن التطبيق يعمل

---

### 18.18 مصفوفة الأولوية لتغطية الاختبار

| السيناريو | أولوية | تغطية اختبار V1 |
|---|---|---|
| Happy Path Scenarios (S-ONB-01, S-CALC-01, ...) | حرجة | اختبار آلي |
| Loss Order, Discount Threshold | حرجة | اختبار آلي + يدوي |
| Refund/Cancel Scenarios | عالية | اختبار آلي |
| OAuth Failure | عالية | اختبار آلي |
| Webhook Idempotency | حرجة | اختبار آلي |
| Edge Cases (S-EDGE-*) | متوسطة | اختبار يدوي |
| Performance (10K products) | عالية | Load Test |
| Security (XSS, SQLi) | حرجة | OWASP Scan |
| Localization (RTL/LTR) | عالية | اختبار يدوي |
| Multi-currency | منخفضة | V2 |

---

### 18.19 خلاصة السيناريوهات

تم توثيق **170+ سيناريو** عبر 18 محوراً. تغطية شاملة لـ:
- 🟢 Happy paths
- 🟡 Edge cases وحالات الحافة
- 🔴 Error states والتعافي منها
- 🔵 Recovery scenarios
- ⚪ Boundary conditions

كل سيناريو سيتحوّل إلى **Test Case** في QA suite قبل الإطلاق.

---

## 19. Open Questions (قرارات معلّقة)

أسئلة تحتاج حسماً قبل أو أثناء التطوير:

1. **🟡 الـ Tech Stack:** Node.js (NestJS) أم Python (FastAPI)؟ — قرار في الأسبوع الأول حسب توفر الفريق
2. **🟡 الـ Hosting:** AWS Riyadh أم Salla Cloud؟ — يعتمد على شراكة سلة
3. **🟡 الـ WhatsApp Provider:** Salla WhatsApp API أم 360dialog مباشرة؟ — اختبار التكلفة أولاً
4. **🟡 سياسة المرتجعات في حساب الربح:** هل نخصمها من ربح الشهر أم نعرض الصافي؟ — استشارة محاسب
5. **🟡 معاملة الضرائب:** هل تُعرض في breakdown أم تُتجاهل؟ — التوصية: تُعرض لكنها لا تُحسب من الربح
6. **🟡 العملات الأخرى:** هل ندعم AED/KWD في V1 أم V2؟ — اقتراح: V2
7. **🟡 خطة Free Tier:** هل نوفّرها؟ — اقتراح: لا، فقط Trial 14 يوم لتجنّب gaming
8. **🟡 التسعير السنوي:** هل نقدم خصم 20% للسنوي؟ — اقتراح: نعم في V1.5
9. **🟡 سياسة Affiliates:** هل نعطي عمولة للمحاسبين/الاستشاريين الذين يحيلون التجار؟ — اقتراح: 20% الشهر الأول
10. **🟡 الموقف من Excel Import:** هل في V1 أم V2؟ — اقتراح: نعم في V1 لتسهيل Onboarding

---

## 20. Stakeholders & Communication

### 20.1 الأطراف المعنية

| الطرف | المسؤولية | تواتر التواصل |
|---|---|---|
| **Founder / CEO** | الرؤية والقرارات الاستراتيجية | يومياً |
| **Product Lead** | تنفيذ الـ PRD ومتابعة KPIs | يومياً |
| **Eng Lead** | المعمارية والجودة التقنية | يومياً |
| **Designer** | UX و UI | يومياً |
| **Pilot Merchants (5)** | اختبار وتغذية راجعة | أسبوعياً |
| **Salla Partner Manager** | علاقة الشراكة + App Store | كل أسبوعين |
| **Marketing** | إعداد الإطلاق | من الأسبوع 8 |
| **Support** | تجهيز نظام دعم | من الأسبوع 9 |

### 20.2 الاجتماعات الدورية

- **Daily Standup** — 15 دقيقة، الفريق التقني
- **Weekly Sprint Review** — ساعة، كل الفريق
- **Bi-weekly Merchant Feedback** — ساعة، مع 1-2 من الـ Pilot
- **Monthly Steering** — ساعتان، Stakeholders

---

## 21. Appendix

### 21.1 معجم المصطلحات

| المصطلح | التعريف |
|---|---|
| **Net Profit** | صافي الربح بعد خصم كل التكاليف |
| **Profit Margin** | (Net Profit / Revenue) × 100 |
| **COGS** | Cost of Goods Sold — تكلفة المنتجات المباعة |
| **AOV** | Average Order Value — متوسط قيمة الطلب |
| **MRR** | Monthly Recurring Revenue |
| **Churn** | معدل التسرّب الشهري |
| **LTV** | Lifetime Value — قيمة العميل مدى الحياة |
| **CAC** | Customer Acquisition Cost — تكلفة اكتساب العميل |
| **Aha Moment** | اللحظة التي يدرك فيها التاجر قيمة المنتج لأول مرة |

### 21.2 معادلات الحساب الكاملة

**معادلة الربح للطلب الواحد:**
```
NetProfit = SubTotal
          − Discount
          − COGS
          − PaymentFee
          − ShippingActual
          + ShippingCollected
          (− RefundedAmount إن وُجد)
```

**معادلة الربح الشهري:**
```
MonthlyProfit = Σ NetProfit(orders in month)
              − Σ AdSpend (V2)
              − Σ FixedCosts (V2)
```

**معادلة هامش المنتج:**
```
ProductMargin = (SellingPrice − CostPrice) / SellingPrice × 100
```

### 21.3 المراجع

- التقرير النهائي: [margin-hero-final-report.md](margin-hero-final-report.md)
- Salla API Docs: https://docs.salla.dev
- منافسون مرجعيون:
  - TrueProfit: https://apps.shopify.com/trueprofit
  - BeProfit: https://apps.shopify.com/beprofit-profit-calc
  - Lifetimely: https://apps.shopify.com/lifetimely

### 21.4 سجل المراجعات

| الإصدار | التاريخ | التغيير | المؤلف |
|---|---|---|---|
| 0.1 Draft | أبريل 2026 | الإصدار الأول | Product Lead |

---

## 22. Sign-off

| الدور | الاسم | التوقيع | التاريخ |
|---|---|---|---|
| Founder / CEO | | | |
| Product Lead | | | |
| Engineering Lead | | | |
| Design Lead | | | |

---

*Margin Hero PRD V1.0 — Merchant Stack | أبريل 2026*
