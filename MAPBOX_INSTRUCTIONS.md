# تعليمات دمج خرائط Mapbox في منصة الحجاج للتنقل

## ما تم إنجازه

1. تم إضافة مكتبات Mapbox الأساسية إلى صفحتي `pilgrim.html` و `driver.html`
2. تم تحديث ملف `gps-integration.js` لاستخدام Mapbox بدلاً من Google Maps
3. تم إنشاء نماذج توضيحية لاستخدام Mapbox:
   - `mapbox-demo.html`: عرض توضيحي بسيط
   - `mapbox-demo-with-turf.html`: عرض توضيحي متقدم يستخدم مكتبة turf.js لحساب المسافات

## المتطلبات الإضافية

لتفعيل جميع خصائص Mapbox في المشروع، تحتاج إلى:

### 1. إضافة المكتبات التالية إلى صفحات HTML

```html
<!-- Mapbox CSS and JavaScript -->
<link href="https://api.mapbox.com/mapbox-gl-js/v2.14.1/mapbox-gl.css" rel="stylesheet">
<script src="https://api.mapbox.com/mapbox-gl-js/v2.14.1/mapbox-gl.js"></script>

<!-- Mapbox Geocoder Plugin for Search -->
<script src="https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-geocoder/v5.0.0/mapbox-gl-geocoder.min.js"></script>
<link rel="stylesheet" href="https://api.mapbox.com/mapbox-gl-js/plugins/mapbox-gl-geocoder/v5.0.0/mapbox-gl-geocoder.css" type="text/css">

<!-- Turf.js for Geospatial Analysis -->
<script src="https://unpkg.com/@turf/turf@6/turf.min.js"></script>
```

### 2. إعداد واجهة برمجة Mapbox Directions API (اختياري)

للحصول على توجيهات دقيقة ومسارات واقعية، يمكنك استخدام Mapbox Directions API. هذه الخدمة تتطلب إعدادات إضافية في لوحة تحكم Mapbox:

1. قم بتسجيل الدخول إلى [لوحة تحكم Mapbox](https://account.mapbox.com/)
2. قم بتمكين خدمة Directions API
3. قم بتعديل حدود الاستخدام حسب احتياجات المشروع

### 3. تحسين تجربة المستخدم للغة العربية

Mapbox يدعم اللغة العربية بشكل جيد، ولكن يمكن تحسين التجربة من خلال:

1. استخدام أنماط خرائط مخصصة للعالم العربي
2. تخصيص الترجمات والتسميات على الخريطة
3. ضبط اتجاه النصوص (RTL) في واجهات البحث والمعلومات

## كيفية استخدام خرائط Mapbox

### 1. تهيئة الخريطة

```javascript
// تعيين مفتاح API الخاص بـ Mapbox
mapboxgl.accessToken = 'pk.eyJ1IjoiaGFzc2FuMTk3NDIwMTEiLCJhIjoiY203bzY0dnpuMDc1cDJscjNkejExcW5haiJ9.fgmcHX49AnN3Kag-fMWY7g';

// إنشاء خريطة جديدة
const map = new mapboxgl.Map({
    container: 'map-container-id', // معرف العنصر HTML
    style: 'mapbox://styles/mapbox/streets-v12', // نمط الخريطة
    center: [39.826168, 21.422510], // الإحداثيات [خط الطول، خط العرض]
    zoom: 13, // مستوى التكبير
    language: 'ar' // اللغة العربية
});
```

### 2. إضافة عناصر تحكم مفيدة

```javascript
// إضافة أزرار التحكم في التكبير/التصغير والدوران
map.addControl(new mapboxgl.NavigationControl());

// إضافة زر تحديد الموقع الحالي للمستخدم
map.addControl(new mapboxgl.GeolocateControl({
    positionOptions: {
        enableHighAccuracy: true
    },
    trackUserLocation: true
}));

// إضافة أداة البحث عن المواقع
const geocoder = new MapboxGeocoder({
    accessToken: mapboxgl.accessToken,
    mapboxgl: mapboxgl,
    placeholder: 'أدخل الوجهة',
    language: 'ar',
    marker: true
});
map.addControl(geocoder);
```

### 3. إضافة علامات على الخريطة

```javascript
// إضافة علامة بسيطة
new mapboxgl.Marker()
    .setLngLat([39.826168, 21.422510])
    .addTo(map);

// إضافة علامة مع نافذة معلومات
new mapboxgl.Marker({ color: '#FF0000' })
    .setLngLat([39.826168, 21.422510])
    .setPopup(new mapboxgl.Popup().setText('المسجد الحرام'))
    .addTo(map);
```

### 4. رسم مسارات

```javascript
// إضافة مصدر للمسار
map.addSource('route', {
    'type': 'geojson',
    'data': {
        'type': 'Feature',
        'properties': {},
        'geometry': {
            'type': 'LineString',
            'coordinates': [
                [39.826168, 21.422510], // نقطة البداية
                [39.833652, 21.421218]  // نقطة النهاية
            ]
        }
    }
});

// إضافة طبقة لرسم المسار
map.addLayer({
    'id': 'route',
    'type': 'line',
    'source': 'route',
    'layout': {
        'line-join': 'round',
        'line-cap': 'round'
    },
    'paint': {
        'line-color': '#3887be',
        'line-width': 5,
        'line-opacity': 0.75
    }
});
```

### 5. حساب المسافات باستخدام turf.js

```javascript
// حساب المسافة بين نقطتين بالكيلومترات
const distance = turf.distance(
    turf.point([39.826168, 21.422510]), // نقطة البداية
    turf.point([39.833652, 21.421218]), // نقطة النهاية
    { units: 'kilometers' }
);

console.log(`المسافة: ${distance.toFixed(2)} كم`);
```

## النماذج التوضيحية

المشروع يتضمن نماذج توضيحية يمكنك دراستها:

1. **mapbox-demo.html**: نموذج بسيط يوضح كيفية عرض خريطة Mapbox وإضافة علامات
2. **mapbox-demo-with-turf.html**: نموذج متقدم يتضمن:
   - البحث عن المواقع
   - رسم المسارات
   - حساب المسافات والوقت المقدر
   - تقدير سعر الرحلة

## ملاحظات هامة

1. مفتاح API المستخدم حالياً هو:
   ```
   pk.eyJ1IjoiaGFzc2FuMTk3NDIwMTEiLCJhIjoiY203bzY0dnpuMDc1cDJscjNkejExcW5haiJ9.fgmcHX49AnN3Kag-fMWY7g
   ```

2. في البيئة الإنتاجية، يجب تقييد استخدام مفتاح API من خلال إعدادات الأمان في لوحة تحكم Mapbox لمنع الاستخدام غير المصرح به.

3. للحصول على تجربة مثالية، قم بدمج واختبار كل ميزة على حدة قبل دمجها في التطبيق الرئيسي.

4. صحح جميع المشكلات الظاهرة في وحدة التحكم (Console) للمتصفح لضمان عمل الخرائط بشكل سليم.
