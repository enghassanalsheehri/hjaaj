# حل مشكلة 404 على GitHub Pages

## المشكلة:
تواجه خطأ 404 على GitHub Pages لأن التكوين الأساسي لم يتم إعداده بشكل صحيح.

## الحل:

### 1. تأكد من وجود ملف index.html في المجلد الرئيسي
- ملف `index.html` يجب أن يكون موجودًا في الجذر الرئيسي للمستودع.
- تأكد من اسم الملف بدقة (حساس لحالة الأحرف): `index.html` وليس `Index.html` أو `INDEX.HTML`.

### 2. انتظر التحديث
- بعد رفع الملفات، قد يستغرق GitHub Pages بضع دقائق (عادة 1-5 دقائق) لنشر موقعك.
- تحقق من علامة التبويب "Actions" في مستودعك لمعرفة ما إذا كانت عملية النشر لا تزال قيد التنفيذ.

### 3. تكوين الفرع الصحيح
1. انتقل إلى صفحة المستودع على GitHub
2. انتقل إلى علامة التبويب "Settings" (الإعدادات)
3. اضغط على "Pages" في القائمة الجانبية
4. تحت "Build and deployment" (البناء والنشر):
   - تأكد من أن المصدر هو "Deploy from a branch"
   - حدد الفرع "main" أو "master" (حسب اسم الفرع الرئيسي)
   - حدد المجلد "/ (root)"
   - اضغط على "Save" (حفظ)

### 4. تكوين اسم المجال المخصص
- إذا كنت تستخدم اسم مجال مخصص، تأكد من إعداده بشكل صحيح في إعدادات GitHub Pages.

### 5. تأكد من دمج ملف payment-integration.js
- تأكد من أن ملف `js/payment-integration.js` الذي يحتوي على وظيفة `setupPaymentFlow` موجود في المستودع.
- تحقق من أن المسار الصحيح مستخدم في صفحات HTML التي تستدعي هذا الملف.

### 6. فحص سجلات البناء في GitHub Actions
- انتقل إلى علامة التبويب "Actions" في مستودعك
- انقر على آخر عملية بناء للتحقق من الأخطاء

### 7. محاولة حل بديل:
إذا استمرت المشكلة، يمكنك تجربة نشر موقعك على خدمة Netlify:
1. انتقل إلى [Netlify Drop](https://app.netlify.com/drop)
2. اسحب وأفلت المجلد المستخرج `C:\Users\P0hsn\hajj-extracted` إلى الموقع
3. سيتم إنشاء موقع جديد على الفور مع عنوان URL عشوائي
4. يمكنك تغيير العنوان عن طريق النقر على "Site settings" ثم "Change site name"

## الخطوات التالية:
1. قم بإجراء التغييرات المطلوبة
2. انتظر تحديث GitHub Pages (قد يستغرق بضع دقائق)
3. تحقق من موقعك على العنوان: `https://[اسم-المستخدم].github.io/hajj-mobility-platform/`
