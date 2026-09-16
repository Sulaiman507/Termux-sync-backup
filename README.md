ضع هذا النص في ملف README.md داخل مستودع GitHub الخاص بنسختك الاحتياطية، أو في أي مكان تحتفظ فيه بملاحظاتك. يمكنك نسخه كما هو.

```markdown
# 📦 دليل استعادة النسخة الاحتياطية لـ Termux (termux-sync + GitHub)

> **ملاحظة:** هذا الدليل مكتوب لنفسي في حال حذفت Termux واحتجت لاستعادة كل شيء بما فيه ملفات `hermes agent`.

## 🧰 المتطلبات الأساسية

1. هاتف أندرويد.
2. تطبيق **Termux** مثبّت من **F-Droid** (تجنب نسخة Google Play).
3. اتصال إنترنت.
4. **رمز GitHub (Token)** واسم المستودع الذي رفعت إليه النسخة الاحتياطية.
   - إذا نسيت الرمز، أنشئ واحدًا جديدًا من:
     GitHub ← Settings ← Developer settings ← Personal access tokens ← Tokens (classic) ← Generate new token
     (اختر صلاحية `repo`).

## 🚀 خطوات الاستعادة

### 1) تثبيت الأدوات المطلوبة
```bash
pkg update && pkg install python git -y
```

2) تثبيت termux-sync

```bash
curl -fsSL https://raw.githubusercontent.com/djunekz/termux-sync/main/tsctl -o tsctl
chmod +x tsctl
./tsctl install
```

إذا فشل tsctl، جرّب التثبيت عبر pip:

```bash
pip install rich
pip install termux-sync
```

3) إعداد termux-sync مع GitHub

```bash
termux-sync setup
```

· اختر الخيار 3 (GitHub).
· أدخل رمز GitHub (Token).
· أدخل اسم المستودع بالصيغة: اسم_المستخدم/اسم_المستودع.

4) استعادة النسخة الاحتياطية

```bash
termux-sync restore
```

· ستظهر قائمة بالنسخ المتاحة، اختر النسخة التي تريدها.
· ستتحقق الأداة تلقائيًا من سلامة النسخة (SHA-256) قبل الاستخراج.
· سيتم استخراج جميع الملفات (بما فيها home وملفات hermes agent) وإعادة تثبيت الحزم.

5) بعد الاستعادة

أغلق Termux تمامًا (من الإشعار: Exit) ثم افتحه من جديد.

⚠️ ملاحظات مهمة

· إذا كان المستودع خاصًا (Private): قد يظهر خطأ HTTP 404 Not Found. الحل: حوّل المستودع مؤقتًا إلى Public، ثم أعد المحاولة، وبعد الانتهاء أعد تحويله إلى Private فورًا.
· إذا انقطعت عملية الاستعادة: أعد تشغيل الأمر termux-sync restore مرة أخرى.
· لا تخزّن النسخة الاحتياطية داخل مجلدات Termux الخاصة (مثل /data/data/com.termux)، لأنها تُحذف مع مسح بيانات التطبيق.
· للتحقق من النسخ المتاحة: يمكنك استخدام termux-sync list.
· لاستعادة نسخة معينة بالاسم: termux-sync restore --name اسم_النسخة.

🧠 تذكير سريع

· الأمر الأساسي للاستعادة: termux-sync restore
· أمر الإعداد (أول مرة فقط): termux-sync setup
· إذا نسيت الرمز: أنشئ واحدًا جديدًا بصلاحية repo.
· ملفات hermes agent موجودة في ~/.hermes وستُستعاد تلقائيًا مع مجلد home.

---

آخر تحديث: (اكتب التاريخ هنا)

```

يمكنك تعديل التاريخ أو إضافة أي تفاصيل خاصة بك. هذا النص كافٍ لتذكيرك بالخطوات كاملة إذا احت جت لاستعادة النسخة لاحقًا.
