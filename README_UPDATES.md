# تعديلات منصة الحجاج للتنقل

## تم تصحيح الأكواد التالية:

### 1. استبدال Leaflet.js بـ Google Maps API
**ملف: pilgrim.html**

استبدل الكود:
```html
<!-- Leaflet Map CSS and JS -->
<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" 
      integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" 
      crossorigin=""/>
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" 
        integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" 
        crossorigin=""></script>
```

بالكود:
```html
<!-- Google Maps API with necessary libraries -->
<script src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY_HERE&libraries=places,geometry"></script>
```

> **ملاحظة مهمة**: يجب استبدال "YOUR_API_KEY_HERE" بمفتاح API الحقيقي من Google Cloud Console.

### 2. تعزيز نظام الدفع
**ملف: js/payment-integration.js**

تم إجراء التعديلات التالية:

1. **إضافة خيارات دفع جديدة**:
   - تمت إضافة Google Pay و UrPay
   - تم تحديث واجهة المستخدم لكل خيار دفع

2. **تعزيز الأمان**:
   - إضافة وظيفة `encryptPaymentData()` لتشفير البيانات الحساسة
   - إضافة وظيفة `validateCardNumber()` للتحقق من صحة أرقام البطاقات باستخدام خوارزمية Luhn

3. **تحسين تجربة المستخدم**:
   - تحديث وظيفة `showPaymentForm()` لعرض نماذج دفع أكثر تفاعلية
   - تحديث وظيفة `processPayment()` لدعم ميزات جديدة مثل تخزين طرق الدفع
   - تحديث وظيفة `showPaymentConfirmation()` لعرض معلومات أكثر تفصيلاً وخيارات للمستخدم
   - إضافة وظائف مساعدة مثل `showPaymentSupport()` و `retryPayment()` و `changePaymentMethod()`

### 3. إضافة ملف مؤقت للتحديثات
تم إنشاء ملف مؤقت يحتوي على التحديثات في:
- `pilgrim_updated.html`

يرجى نسخ محتوى هذا الملف إلى `pilgrim.html` يدويًا أو استخدام الأمر التالي:

```powershell
copy pilgrim_updated.html pilgrim.html
```

## ملخص التغييرات
- تحسين نظام الدفع ليشمل المزيد من الخيارات
- تعزيز الأمان من خلال تشفير البيانات الحساسة
- تحسين واجهة المستخدم لنماذج الدفع
- استبدال مكتبة Leaflet بـ Google Maps API للحصول على ميزات متقدمة للخرائط

## الخطوات التالية
1. استبدل مفتاح API الخاص بـ Google Maps في الملفات المحدثة
2. اختبر جميع خيارات الدفع للتأكد من عملها بشكل صحيح
3. تأكد من عمل الخرائط وميزات تحديد المواقع بشكل صحيح
