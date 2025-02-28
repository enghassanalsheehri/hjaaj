# منصة الحجاج للتنقل | Hajj Mobility Platform

منصة إلكترونية لتسهيل التنقل للحجاج وربطهم بسائقي عربات المعاقين في المشاعر المقدسة.

## كيفية نشر الموقع على GitHub Pages

اتبع الخطوات التالية لنشر الموقع على GitHub Pages:

### 1. إنشاء مستودع GitHub

1. قم بالدخول إلى حسابك على [GitHub](https://github.com)
2. انقر على زر "New" لإنشاء مستودع جديد
3. أدخل اسم المستودع: `hajj-mobility-platform`
4. اضغط على "Create repository"

### 2. رفع الملفات

**الطريقة الأولى: استخدام GitHub Desktop**
1. قم بتثبيت [GitHub Desktop](https://desktop.github.com/)
2. انقر على "Clone a repository from the Internet..."
3. اختر المستودع الذي أنشأته
4. اختر المجلد المحلي (حيث تريد تخزين الملفات محلياً)
5. انسخ جميع ملفات المشروع إلى المجلد المحلي
6. أضف وصفاً للتغييرات في GitHub Desktop
7. اضغط على "Commit to main"
8. اضغط على "Push origin"

**الطريقة الثانية: الرفع المباشر على GitHub**
1. افتح المستودع على GitHub
2. انقر على "Add file" > "Upload files"
3. اسحب وأفلت جميع ملفات وملفات المشروع
4. أضف وصفاً للتغييرات
5. اضغط على "Commit changes"

### 3. تكوين GitHub Pages

1. اذهب إلى صفحة المستودع على GitHub
2. انقر على "Settings"
3. انتقل إلى قسم "Pages" (من القائمة الجانبية)
4. في قسم "Source"، اختر:
   - Branch: `main`
   - Folder: `/ (root)`
5. انقر على "Save"

### 4. انتظر النشر

- ستظهر رسالة "Your site is being published at ..."
- انتظر بضع دقائق حتى يكتمل النشر
- عند الانتهاء، ستتمكن من الوصول إلى موقعك على الرابط: `https://username.github.io/hajj-mobility-platform`

## ملاحظات مهمة

- تم إنشاء ملف `.nojekyll` للتأكد من أن GitHub Pages لا يستخدم معالج Jekyll
- تم إضافة ملف `_config.yml` لتكوين GitHub Pages بشكل صحيح
- تم إضافة ملف `404.html` للتعامل مع الصفحات غير الموجودة
- تم إضافة ملف `_redirects` للتعامل مع توجيهات الروابط
- إذا واجهت مشاكل في تحميل ملفات CSS، استخدم `index-with-inline-styles.html` كاحتياطي

## اختبار الموقع محلياً

1. انتقل إلى مجلد المشروع
2. افتح `index.html` في المتصفح
3. تأكد من أن جميع الروابط والصور تعمل بشكل صحيح

## استخدام منصات بديلة

إذا واجهت مشاكل مع GitHub Pages، يمكنك استخدام:

1. **Netlify**:
   - انتقل إلى [Netlify Drop](https://app.netlify.com/drop)
   - اسحب وأفلت مجلد المشروع
   - سيتم نشر الموقع تلقائيًا

2. **Render**:
   - أنشئ حسابًا على [Render](https://render.com)
   - أنشئ "Static Site" جديد
   - حدد مستودع GitHub أو قم برفع الملفات مباشرة
   - استخدم ملف `render.yaml` للتكوين

## دعم

إذا واجهت أي مشاكل، يرجى التواصل عبر البريد الإلكتروني support@hajjmobility.com
