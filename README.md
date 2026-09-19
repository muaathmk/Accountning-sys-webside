# الموقع التعريفي وسياسة الخصوصية (Showcase & Privacy Policy Website)

تم تصميم وبرمجة هذا الموقع التعريفي ليكون واجهة رسمية واحترافية للمشروع، ومخصص للاستخدام كـ **Developer Website** ورابط **Privacy Policy** المطلوب عند التسجيل والتوثيق في منصة **Google Play Console**.

---

## 📁 محتويات المجلد (`showcase_website/`)

| الملف | الوظيفة |
| :--- | :--- |
| `index.html` | الصفحة الرئيسية الكاملة (قسم الترحيب، نبذة عن النظام، المميزات، المنظومة، سياسة الخصوصية، التواصل عبر واتساب). |
| `privacy.html` | صفحة سياسة الخصوصية المستقلة المجهزة خصيصاً كـ رابط مباشر لـ Google Play Console. |
| `style.css` | تصميم فاخر وعصري (Vanilla CSS) يدعم الاتجاه من اليمين لليسار (RTL)، تأثيرات زجاجية وإضاءات ناعمة وتوافق تام مع الهواتف. |
| `script.js` | وظائف تفاعلية (نسخ الرقم، القائمة للجوال، التمرير السلس). |
| `assets/` | شعارات وأيقونات المشروع الرسمية. |
| `Dockerfile` & `nginx.conf` | ملفات التشغيل بالحاويات (Docker) في حال رفعه على السيرفر السحابي (Droplet). |

---

## 📱 بيانات التواصل المعتمدة
- **رقم الواتساب والهاتف:** `+967 735 468 713` (735 468 713)
- الروابط في الموقع تنقل مباشرة إلى محادثة واتساب مجهزة بنص استفسار رسمي.

---

## 🚀 خيارات الرفع والنشر (أين نرفعه لاحقاً؟)

وفقاً لهيكل السحابة الموجود في مجلدي `deploy/digitalocean` و `cloud_docs`:

### الخيار الأول: الرفع على سيرفر الـ Droplet نفسه (DigitalOcean)
المنافذ الحالية على الـ Droplet:
- `3000`: واجهة SuperAdmin
- `4000`: SuperAdmin API
- `5000`: Accounting API
- `31415/31416`: مزامنة SymmetricDS

**المنفذ 80 و 8080 متاحان!**  
يمكنك ببساطة تشغيله كحاوية في `docker-compose.yml` عبر إضافة:
```yaml
  showcase-website:
    build:
      context: ../../showcase_website
      dockerfile: Dockerfile
    container_name: showcase_site
    restart: unless-stopped
    mem_limit: 64m
    ports:
      - "80:80"
```
أو ربطه بـ Nginx على السيرفر مع شهادة SSL (Certbot) ليعمل على دومين مباشر مثل: `https://yourdomain.com`.

---

### الخيار الثاني (الأفضل والأسرع لـ Google Play Console): النشر المجاني عبر Cloudflare Pages أو GitHub Pages
* **لماذا؟** لأن متجر Google Play يشترط أن يكون رابط سياسة الخصوصية يبدأ بـ **`https://`** (مشفر بـ SSL) ومتاح دائماً وبسرعة عالية للمراجعين.
* **الخطوات:**
  1. إنشاء مستودع (Repository) على GitHub ورفع مجلد `showcase_website`.
  2. تفعيل **GitHub Pages** بنقرة واحدة من الإعدادات، أو ربطه بـ **Cloudflare Pages**.
  3. ستحصل على رابط رسمي فوري مجاناً وبشهادة HTTPS صالحة، مثل:
     - `https://yourname.github.io/`
     - ورابط سياسة الخصوصية: `https://yourname.github.io/privacy.html`
