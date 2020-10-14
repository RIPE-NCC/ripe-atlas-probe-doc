  

## <div dir="rtl">  تنصيب المصدر لنسخ اللنكس  CentOS 7 and 8 -  </div>

<div dir="rtl"><ul>

يدعم إصدار     (amd64)  CentOS x86_6, لاحظ أن نصوص التثبيت وبدء التشغيل تفترض استخدام . systemd

1/ لإنشاء حزمة البرامج وتثبيتها ، يرجى اتباع   تعليمات CentOS المحددة المنصوص عليها في الملف التالي: 
    [INSTALL.rst] (https://github.com/RIPE-NCC/ripe-atlas-software-probe/blob/master/INSTALL.rst)
    
2/ يؤدي تثبيت برنامج التحقيق إلى إنشاء زوج مفاتيح SSH جديد,  لاستخدامه   قم بتوصيل المسبار بالبنية التحتية الخاصة ب RIPE Atlas 
  تحتاج إلى تسجيل   جزء المفتاح العام , من أجل تسجيل التحقق:  (/ application / swprobe /)  
يمكن العثور على هذا في المسار :

`/var / atlas-probe / etc / probe_key.pub`.


</ul></div>

