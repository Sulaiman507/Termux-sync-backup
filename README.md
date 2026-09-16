# 📦 دليل استعادة النسخة الاحتياطية لـ Termux (termux-sync - محلي)

> هذا الدليل لنسخة احتياطية محلية محفوظة في /sdcard/termux-backups

## 🧰 المتطلبات
1. تثبيت Termux من F-Droid.
2. نسخة من مجلد termux-backups (انسخه من الحاسوب أو السحابة إلى /sdcard/).

## 🚀 خطوات الاستعادة

### 1) تثبيت الأدوات
pkg update && pkg install python git -y

### 2) تثبيت termux-sync
curl -fsSL https://raw.githubusercontent.com/djunekz/termux-sync/main/tsctl -o tsctl
chmod +x tsctl
./tsctl install

> إذا فشل tsctl: pip install rich && pip install termux-sync

### 3) منح صلاحية التخزين
termux-setup-storage
(اضغط سماح)

### 4) إعداد termux-sync
termux-sync setup
- اختر الخيار [1] Local storage
- أدخل المسار: /sdcard/termux-backups

### 5) استعادة النسخة
termux-sync restore
- اختر النسخة المطلوبة من القائمة
- ستتحقق الأداة من السلامة ثم تستعيد كل شيء

### 6) بعد الاستعادة
أغلق Termux تمامًا ثم افتحه من جديد.

## ⚠️ ملاحظات مهمة
- لا تحذف مجلد termux-backups أبدًا.
- احتفظ بنسخة منه على الحاسوب أو Google Drive.
- إذا انقطعت الاستعادة، أعد تشغيل: termux-sync restore
- للتحقق من النسخ: termux-sync list
- استعادة نسخة معينة: termux-sync restore --name اسم_النسخة

## 🧠 تذكير سريع
- أمر الاستعادة: termux-sync restore
- أمر الإعداد: termux-sync setup (محلي → /sdcard/termux-backups)
- ملفات hermes agent في ~/.hermes وستُستعاد تلقائيًا.
