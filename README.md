# Mithaq_Sunna_Syria
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>وثيقة مرتكزات الاصطفاف السني في سورية - م. حسام طرشة</title>
  
  <!-- الخطوط الرسمية للوثائق والطباعة: ريم كوفي للعناوين، الأميري للنصوص والآيات، القاهرة للقراءة الرسمية -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Amiri:ital,wght@0,400;0,700;1,400;1,700&family=Cairo:wght@400;500;600;700;800;900&family=Reem+Kufi:wght@500;600;700;800&display=swap" rel="stylesheet">
  
  <!-- محرك تصدير الـ PDF المستقل والمعالجة الفورية -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.10.1/html2pdf.bundle.min.js"></script>

  <style>
    /* =========================================================
       هوية الوثيقة الرسمية المستقلة: الأخضر السوري السيادي والذهب الشامي
       ========================================================= */
    :root {
      --syrian-green-dark: #072516;
      --syrian-green-sovereign: #0c3822;
      --syrian-green-mid: #14532d;
      --syrian-green-accent: #19703e;
      --syrian-gold: #c39a3f;
      --syrian-gold-light: #f1dfb0;
      --syrian-gold-dark: #846519;
      --syrian-red-star: #b91c1c;
      --parchment-white: #fdfcf9;
      --parchment-border: #d4c4a8;
      --text-ink: #111e17;
      --text-sub: #3d4f45;
    }

    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    body {
      background-color: #1b2420;
      font-family: 'Cairo', 'Amiri', Tahoma, sans-serif;
      color: var(--text-ink);
      line-height: 1.7;
      direction: rtl;
      -webkit-font-smoothing: antialiased;
      padding-bottom: 60px;
    }

    /* =========================================================
       شريط أدوات المستند (خارجي يظهر في المعاينة ويختفي عند الطباعة)
       ========================================================= */
    .document-app-bar {
      position: sticky;
      top: 0;
      z-index: 9999;
      background: rgba(7, 37, 22, 0.95);
      backdrop-filter: blur(12px);
      border-bottom: 2px solid var(--syrian-gold);
      padding: 10px 20px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      box-shadow: 0 4px 20px rgba(0,0,0,0.5);
    }

    .doc-meta-title {
      color: #f1dfb0;
      font-family: 'Reem Kufi', sans-serif;
      font-size: 13pt;
      font-weight: 700;
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .doc-meta-title span.stars {
      color: var(--syrian-red-star);
      font-size: 14pt;
    }

    .doc-actions {
      display: flex;
      align-items: center;
      gap: 10px;
    }

    .doc-btn {
      padding: 8px 18px;
      border-radius: 6px;
      font-family: 'Cairo', sans-serif;
      font-size: 11pt;
      font-weight: 700;
      border: 1px solid var(--syrian-gold);
      cursor: pointer;
      display: flex;
      align-items: center;
      gap: 8px;
      transition: all 0.2s ease;
    }

    .btn-pdf-print {
      background: linear-gradient(135deg, var(--syrian-gold-light), var(--syrian-gold));
      color: var(--syrian-green-dark);
    }

    .btn-pdf-print:hover {
      background: #ffffff;
      transform: translateY(-1px);
    }

    .btn-pdf-direct {
      background: var(--syrian-green-mid);
      color: #ffffff;
    }

    .btn-pdf-direct:hover {
      background: var(--syrian-green-accent);
      transform: translateY(-1px);
    }

    /* =========================================================
       هندسة صفحة الـ PDF المستقلة القياسية (A4 Dimension: 210mm x 297mm)
       ========================================================= */
    .pdf-pages-container {
      width: 210mm;
      margin: 30px auto;
      display: flex;
      flex-direction: column;
      gap: 30px;
    }

    .page-sheet {
      width: 210mm;
      height: 297mm;
      min-height: 297mm;
      max-height: 297mm;
      background: var(--parchment-white);
      position: relative;
      box-shadow: 0 15px 40px rgba(0, 0, 0, 0.45);
      padding: 16mm 16mm 14mm 16mm;
      display: flex;
      flex-direction: column;
      justify-content: space-between;
      overflow: hidden;
    }

    /* الإطار المزدوج التراثي الهندسي المحيط بصفحات الوثيقة */
    .sheet-border {
      position: absolute;
      top: 8mm;
      left: 8mm;
      right: 8mm;
      bottom: 8mm;
      border: 1.5px solid var(--syrian-green-sovereign);
      pointer-events: none;
      z-index: 10;
    }

    .sheet-border-inner {
      position: absolute;
      top: 9.5mm;
      left: 9.5mm;
      right: 9.5mm;
      bottom: 9.5mm;
      border: 0.75px solid var(--syrian-gold);
      pointer-events: none;
      z-index: 10;
    }

    /* زخارف الزوايا الأرابيسك المتجهة */
    .corner-flourish {
      position: absolute;
      width: 24px;
      height: 24px;
      z-index: 12;
      pointer-events: none;
    }
    .corner-top-right { top: 7mm; right: 7mm; }
    .corner-top-left { top: 7mm; left: 7mm; transform: scaleX(-1); }
    .corner-bottom-right { bottom: 7mm; right: 7mm; transform: scaleY(-1); }
    .corner-bottom-left { bottom: 7mm; left: 7mm; transform: scale(-1); }

    /* =========================================================
       الترويسة والتذييل الطباعي (Running Header & Footer)
       ========================================================= */
    .doc-running-header {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-bottom: 1px solid var(--parchment-border);
      padding-bottom: 5px;
      margin-bottom: 10px;
      font-size: 8.5pt;
      color: var(--syrian-green-sovereign);
      font-weight: 700;
      position: relative;
      z-index: 2;
    }

    .header-right {
      display: flex;
      align-items: center;
      gap: 6px;
    }

    .header-diamond {
      width: 5px;
      height: 5px;
      background: var(--syrian-gold);
      transform: rotate(45deg);
      display: inline-block;
    }

    .doc-running-footer {
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-top: 1px solid var(--parchment-border);
      padding-top: 5px;
      margin-top: 6px;
      font-size: 8.2pt;
      color: var(--text-sub);
      font-weight: 600;
      position: relative;
      z-index: 2;
    }

    .page-number-box {
      font-family: 'Cairo', sans-serif;
      font-weight: 800;
      color: var(--syrian-green-sovereign);
      background: var(--syrian-gold-light);
      padding: 1px 8px;
      border-radius: 4px;
    }

    /* محتوى الصفحة الفعلي داخل الهوامش */
    .sheet-body {
      flex-grow: 1;
      display: flex;
      flex-direction: column;
      position: relative;
      z-index: 2;
      overflow: hidden;
    }

    /* =========================================================
       أنماط النصوص والأشرطة الرسمية للميثاق
       ========================================================= */
    h1, h2, h3, h4 {
      font-family: 'Reem Kufi', 'Amiri', serif;
      color: var(--syrian-green-sovereign);
    }

    p {
      text-align: justify;
      font-size: 9.8pt;
      line-height: 1.65;
      color: var(--text-ink);
      margin-bottom: 7px;
    }

    .section-ribbon {
      background: linear-gradient(135deg, var(--syrian-green-dark) 0%, var(--syrian-green-sovereign) 100%);
      color: #ffffff;
      padding: 7px 14px;
      border-radius: 4px;
      border-right: 5px solid var(--syrian-gold);
      margin: 8px 0;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    .section-ribbon h2 {
      font-size: 12.8pt;
      color: #ffffff;
      font-weight: 700;
      margin: 0;
    }

    .ribbon-tag {
      background: var(--syrian-gold);
      color: var(--syrian-green-dark);
      font-size: 8.5pt;
      font-weight: 800;
      padding: 1px 10px;
      border-radius: 20px;
      font-family: 'Cairo', sans-serif;
    }

    h3.subhead {
      font-size: 11pt;
      color: var(--syrian-green-mid);
      margin: 7px 0 5px 0;
      padding-bottom: 3px;
      border-bottom: 1px dashed var(--syrian-gold);
      font-weight: 700;
    }

    /* =========================================================
       مربعات الآيات الكريمة والأحاديث الشريفة
       ========================================================= */
    .quran-box {
      background: #faf8f2;
      border: 1px solid var(--syrian-gold);
      border-radius: 5px;
      padding: 7px 12px;
      margin: 6px 0;
      text-align: center;
    }

    .quran-text {
      font-family: 'Amiri', serif;
      font-size: 10.5pt;
      line-height: 1.85;
      color: #082918;
      font-weight: 700;
    }

    /* =========================================================
       القوائم النقطية للبنود
       ========================================================= */
    .charter-list {
      list-style: none;
      padding: 0;
      margin: 4px 0;
    }

    .charter-list li {
      position: relative;
      padding-right: 18px;
      margin-bottom: 6px;
      font-size: 9.35pt;
      line-height: 1.62;
      text-align: justify;
      color: #17241d;
    }

    .charter-list li::before {
      content: "◆";
      position: absolute;
      right: 0;
      top: 1px;
      color: var(--syrian-gold);
      font-size: 8.5pt;
    }

    /* شبكة بطاقات الدواعي */
    .dawaee-grid {
      display: grid;
      grid-template-columns: 1fr 1fr;
      gap: 7px;
      margin: 7px 0;
    }

    .dawaee-item {
      background: #ffffff;
      border: 1px solid #d9e4de;
      border-top: 2.5px solid var(--syrian-green-sovereign);
      padding: 7px 10px;
      border-radius: 4px;
      font-size: 9.1pt;
      line-height: 1.55;
    }

    .dawaee-item strong {
      color: var(--syrian-green-sovereign);
      display: block;
      margin-bottom: 2px;
      font-size: 9.4pt;
    }

    /* =========================================================
       صفحة الغلاف السيادية (Cover Sheet)
       ========================================================= */
    .page-sheet.cover-sheet {
      background: radial-gradient(circle at center, #0f462a 0%, var(--syrian-green-sovereign) 60%, var(--syrian-green-dark) 100%);
      color: #ffffff;
      padding: 24mm 20mm;
      text-align: center;
      justify-content: center;
      align-items: center;
    }

    .page-sheet.cover-sheet .sheet-border {
      border-color: var(--syrian-gold);
      border-width: 2px;
    }

    .page-sheet.cover-sheet .sheet-border-inner {
      border-color: rgba(241, 223, 176, 0.4);
    }

    .cover-stars {
      display: flex;
      justify-content: center;
      gap: 16px;
      font-size: 26pt;
      color: var(--syrian-red-star);
      margin-bottom: 25px;
      filter: drop-shadow(0 0 10px rgba(185, 28, 28, 0.6));
    }

    .cover-emblem-svg {
      width: 140px;
      height: 140px;
      margin-bottom: 25px;
      filter: drop-shadow(0 8px 24px rgba(0,0,0,0.5));
    }

    .cover-kicker {
      border: 1px solid var(--syrian-gold);
      background: rgba(195, 154, 63, 0.15);
      color: var(--syrian-gold-light);
      padding: 4px 22px;
      border-radius: 30px;
      font-size: 11pt;
      font-weight: 700;
      letter-spacing: 0.5px;
      display: inline-block;
      margin-bottom: 20px;
    }

    .cover-main-title {
      font-family: 'Reem Kufi', serif;
      font-size: 32pt;
      font-weight: 800;
      line-height: 1.35;
      color: #ffffff;
      text-shadow: 0 4px 18px rgba(0,0,0,0.6);
      margin-bottom: 12px;
    }

    .cover-main-title span {
      display: block;
      background: linear-gradient(135deg, #ffffff 20%, var(--syrian-gold-light) 65%, var(--syrian-gold) 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      font-size: 36pt;
      margin-top: 4px;
    }

    .cover-subtitle {
      font-family: 'Amiri', serif;
      font-size: 19pt;
      color: #d8ecdf;
      margin: 10px 0 25px 0;
    }

    .cover-author-block {
      border: 1px solid rgba(195, 154, 63, 0.4);
      background: rgba(255, 255, 255, 0.05);
      border-radius: 10px;
      padding: 12px 35px;
      display: inline-block;
      margin-bottom: 30px;
    }

    .cover-author-label {
      font-size: 10.5pt;
      color: var(--syrian-gold-light);
      margin-bottom: 3px;
    }

    .cover-author-name {
      font-family: 'Reem Kufi', sans-serif;
      font-size: 21pt;
      font-weight: 700;
      color: #ffffff;
    }

    .cover-bottom-seal {
      width: 75%;
      border-top: 1px solid rgba(195, 154, 63, 0.35);
      padding-top: 15px;
      display: flex;
      justify-content: space-around;
      color: #b0d4c0;
      font-size: 10.5pt;
    }

    /* =========================================================
       إعدادات الطباعة الدقيقة (Direct PDF & Print Engine)
       ========================================================= */
    @page {
      size: A4 portrait;
      margin: 0;
    }

    @media print {
      body {
        background: transparent !important;
        padding: 0 !important;
        margin: 0 !important;
      }

      .document-app-bar {
        display: none !important;
      }

      .pdf-pages-container {
        width: 100% !important;
        margin: 0 !important;
        gap: 0 !important;
      }

      .page-sheet {
        margin: 0 !important;
        box-shadow: none !important;
        page-break-after: always !important;
        page-break-inside: avoid !important;
        break-after: page !important;
        -webkit-print-color-adjust: exact !important;
        print-color-adjust: exact !important;
      }
    }
  </style>
</head>
<body>

  <div class="document-app-bar">
    <div class="doc-meta-title">
      <span class="stars">★ ★ ★</span>
      وثيقة ميثاق الاصطفاف السني في سورية — نسخة الطباعة والـ PDF المستقلة
    </div>
    <div class="doc-actions">
      <!-- زر الحفظ بصيغة PDF الطباعية عالية الدقة -->
      <button class="doc-btn btn-pdf-print" onclick="window.print()" title="حفظ المستند بصيغة PDF عالية الدقة عبر المتصفح">
        <svg width="17" height="17" viewBox="0 0 24 24" fill="currentColor">
          <path d="M19 8H5c-1.66 0-3 1.34-3 3v6h4v4h12v-4h4v-6c0-1.66-1.34-3-3-3zm-3 11H8v-5h8v5zm3-7c-.55 0-1-.45-1-1s.45-1 1-1 1 .45 1 1-.45 1-1 1zm-1-9H6v4h12V3z"/>
        </svg>
        طباعة / حفظ كـ PDF فيكتوري
      </button>

      <!-- زر التصدير والتنزيل المباشر كملف PDF إلى الجهاز -->
      <button class="doc-btn btn-pdf-direct" onclick="exportStandalonePDF()" title="تنزيل ملف الـ PDF مباشرة إلى جهازك">
        <svg width="17" height="17" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2">
          <path d="M21 15v4a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-4"></path>
          <polyline points="7 10 12 15 17 10"></polyline>
          <line x1="12" y1="15" x2="12" y2="3"></line>
        </svg>
        تحميل الـ PDF مباشرة
      </button>
    </div>
  </div>

  <!-- الحاوية المجمعة لصفحات المستند المستقل -->
  <div class="pdf-pages-container" id="pdf-root">

    <!-- =========================================================
         الصفحة 1: الغلاف السيادي المستقل للوثيقة
         ========================================================= -->
    <div class="page-sheet cover-sheet">
      <div class="sheet-border"></div>
      <div class="sheet-border-inner"></div>

      <div class="cover-stars">
        <span>★</span>
        <span>★</span>
        <span>★</span>
      </div>

      <!-- شعار النجمة الثمانية الشامية المتجهة -->
      <svg class="cover-emblem-svg" viewBox="0 0 100 100" fill="none">
        <circle cx="50" cy="50" r="48" stroke="#c39a3f" stroke-width="1.2" stroke-dasharray="2 3"/>
        <circle cx="50" cy="50" r="43" stroke="#f1dfb0" stroke-width="0.8"/>
        <polygon points="50,10 62,38 90,50 62,62 50,90 38,62 10,50 38,38" fill="rgba(195,154,63,0.2)" stroke="#c39a3f" stroke-width="1.5"/>
        <polygon points="50,18 58,42 82,50 58,58 50,82 42,58 18,50 42,42" fill="rgba(241,223,176,0.3)" stroke="#f1dfb0" stroke-width="1"/>
        <circle cx="50" cy="50" r="10" fill="#c39a3f"/>
        <circle cx="50" cy="50" r="5" fill="#072516"/>
      </svg>

      <div class="cover-kicker">وثيقة ميثاق وطني واستراتيجي</div>

      <h1 class="cover-main-title">
        وثيقة مرتكزات
        <span>الاصطفاف السنّي في سورية</span>
      </h1>

      <div class="cover-subtitle">
        «لماذا الاصطفاف السني في سورية ومرتكزاته»
      </div>

      <div class="cover-author-block">
        <div class="cover-author-label">كتبه:</div>
        <div class="cover-author-name">م. حسام طرشة</div>
      </div>

      <div class="cover-bottom-seal">
        <div>سورية الحرة الموحدة</div>
        <div>•</div>
        <div>رؤية جامعة للمستقبل</div>
        <div>•</div>
        <div>1447 - 1448 هـ / 2026 م</div>
      </div>
    </div>

    <!-- =========================================================
         الصفحة 2: المقدمة ودواعي تفعيل الاعتصام
         ========================================================= -->
    <div class="page-sheet">
      <div class="sheet-border"></div>
      <div class="sheet-border-inner"></div>

      <!-- زوايا الصفحة الأرابيسك -->
      <svg class="corner-flourish corner-top-right" viewBox="0 0 50 50"><path d="M0,0 L50,0 L50,50 L42,42 L42,8 L8,8 Z" fill="#c39a3f"/></svg>
      <svg class="corner-flourish corner-top-left" viewBox="0 0 50 50"><path d="M0,0 L50,0 L50,50 L42,42 L42,8 L8,8 Z" fill="#c39a3f"/></svg>
      <svg class="corner-flourish corner-bottom-right" viewBox="0 0 50 50"><path d="M0,0 L50,0 L50,50 L42,42 L42,8 L8,8 Z" fill="#c39a3f"/></svg>
      <svg class="corner-flourish corner-bottom-left" viewBox="0 0 50 50"><path d="M0,0 L50,0 L50,50 L42,42 L42,8 L8,8 Z" fill="#c39a3f"/></svg>

      <div class="doc-running-header">
        <div class="header-right">
          <span class="header-diamond"></span>
          وثيقة مرتكزات الاصطفاف السني في سورية
        </div>
        <div>م. حسام طرشة</div>
      </div>

      <div class="sheet-body">
        <div style="text-align: center; margin-bottom: 8px;">
          <h2 style="font-size: 15pt; color: var(--syrian-green-sovereign); margin-bottom: 2px;">لماذا الاصطفاف السني في سورية</h2>
          <div style="font-size: 12pt; color: var(--syrian-gold-dark); font-weight: 700;">مرتكزاته</div>
          <div style="font-size: 10pt; color: var(--text-sub);">كتبه: م. حسام طرشة</div>
          <div style="font-size: 11pt; color: var(--syrian-green-mid); font-weight: 700; margin-top: 4px;">وثيقة مرتكزات الاصطفاف السني في سورية</div>
        </div>

        <div class="section-ribbon">
          <h2>مقدمة</h2>
          <span class="ribbon-tag">التأصيل والمرجعية</span>
        </div>

        <p>
          إن للاعتصام ووحدة الصف مرتكزات تتوزع على عدة مرابط يجتمع فيها أهل السنة جميعا اجتماعَ الجسد الواحد إذا اشتكى منه عضو تداعى له سائر الجسد بالحمى والسهر، فهو بمثابة التئام وتماسك للصفوف، والمسلمون أهل السنة: هم أهل الإسلام من الجماعات والفرق الذين يجمعهم القرآن الكريم والسنة النبوية المطهرة من مصادرها المعروفة "الصحاح والسنن والمسانيد والمصنفات والمعاجم". وكل من خالفهم في هذا فليس منهم، ولا مكان في هذا الاعتصام لمن كان وجوده عامل تمزيق لوحدة الصف والاعتصام بالحق.
        </p>

        <p>
          إن اصطفاف أهل السنة اليوم أصل قبل أن يكون ضرورة، وهو دعوة ربّانية وهدي نبوي من قبيل ترتيب البيت الداخلي، قال تعالى: "واعتصموا بحبل الله جميعا ولا تفرقوا" وقال صلى الله عليه وسلم: "المؤمن للمؤمن كالبنيان يشد بعضه بعضا"، إلا أن أهل السنة في سورية اليوم في أمس الحاجة إلى تفعيل هذا الواجب الإلهي في ظل ما يعانيه السوريون كآفّة.
        </p>

        <div class="quran-box">
          <div class="quran-text">﴿وَاعْتَصِمُوا بِحَبْلِ اللَّهِ جَمِيعًا وَلَا تَفَرَّقُوا﴾</div>
        </div>

        <h3 class="subhead">تتلخص دواعي تفعيل هذا الاعتصام ووحدة الصف بالآتي:</h3>

        <div class="dawaee-grid">
          <div class="dawaee-item">
            <strong>✦ حفظ الضرورات الخمس:</strong>
            الدفاع عن سورية وعن أهلها بحفظ الضرورات الخمس (الدين ـ النفس ـ النسل ـ المال ـ العقل).
          </div>
          <div class="dawaee-item">
            <strong>✦ تحرير البلاد والأرض:</strong>
            العمل على تحرير البلاد وأهلها، وإعادة حقوقهم واستقلال قرارهم، واستقرار أمنهم وأرضهم وسلامهم.
          </div>
          <div class="dawaee-item">
            <strong>✦ المجتمع الرشيد:</strong>
            بناء المجتمع الرشيد والنهضة بشعبنا وبلدنا إلى التمكين.
          </div>
          <div class="dawaee-item">
            <strong>✦ إقامة الحكم الرشيد:</strong>
            إقامة الحكم الرشيد بمرجعية إسلامية تقيم الحق بين الناس وتحكم بينهم بالعدل والقسط، وتأمر بالعدل والإحسان وإيتاء ذي القربى وتنهى عن الفحشاء والمنكر والبغي.
          </div>
        </div>

        <div style="background: #edf7f0; border-right: 4px solid var(--syrian-green-sovereign); padding: 8px 14px; border-radius: 4px; margin-top: 8px; font-weight: 700; font-size: 10pt; color: var(--syrian-green-dark); text-align: center;">
          تتبلور معالم هذا الاعتصام من خلال مرتكزات موزعة على خمسة مرابط
        </div>
      </div>

      <div class="doc-running-footer">
        <div>وثيقة مرتكزات الاصطفاف السني في سورية</div>
        <div class="page-number-box">صفحة ٢ من ٧</div>
        <div>م. حسام طرشة</div>
      </div>
    </div>

    <!-- =========================================================
         الصفحة 3: المربط الأول: مرتكزات إدارة الاختلاف العقدي
         ========================================================= -->
    <div class="page-sheet">
      <div class="sheet-border"></div>
      <div class="sheet-border-inner"></div>

      <div class="doc-running-header">
        <div class="header-right">
          <span class="header-diamond"></span>
          المربط الأول: مرتكزات إدارة الاختلاف العقدي
        </div>
        <div>وثيقة مرتكزات الاصطفاف</div>
      </div>

      <div class="sheet-body">
        <div class="section-ribbon">
          <h2>المربط الأول: مرتكزات إدارة الاختلاف العقدي</h2>
          <span class="ribbon-tag">المربط ١</span>
        </div>

        <p>
          التوحد والعمل على مشروع نهضة سورية هو طليعة مشروع نهضة جميع الشعوب العربية والإسلامية، ولا يلزم منه قلب المسلمات العقدية في دواخل كل شخص وأدبيات كل مدرسة عقدية من مدارس أهل الإسلام باستثناء فرق الخوارج والروافض وفروعها الباطنية. نعالج من خلال ذلك اختناقاتنا الفكرية التي يستشري بسببها التنازع والفشل في أمتنا أفراداً وجماعات.
        </p>

        <h3 class="subhead">مرتكزات إدارة الاختلاف العقدي:</h3>

        <ul class="charter-list">
          <li>
            لا بد لكل فرد أو جماعة من أهل السنة أن تجيب عن السؤال الآتي: هل الأفراد والجماعات من فرق أهل السنة "مسلمون أم كفار"؟ فمن كان جوابه بتكفير من خالفه من أهل القبلة، فلا مقام له في هذا الاعتصام والوحدة المنشودة.
          </li>
          <li>
            لا بد من التسليم أن كل جماعة ترى في معتقدها أنه الحق الذي عقدت وربطت عليه قلوب أفرادها، فمن حاد منهم عن شيء من تلك المعتقدات انحرف أو ضل ـ في منظورهم ـ بقدر هذه الحيدة، غير أن الجميع مسلمون. وهذا سيكون عين رأي أحد الأطراف فيمن يخالف عقيدته من غير جماعته، كما أنه هو عين رأي مخالفه فيه.
          </li>
          <li>
            المعاصي شبهات وشهوات، وكلا النوعين من المعاصي قد يقصد الشخص ارتكابها وهو يعلم أنها معصية أو تراه متأولا في فعلها ظانا صوابها.
          </li>
          <li>
            جميع المسلمين لهم الولاء بحده الأساسي فيما بينهم، وهذا الولاء وإن كان يقل ويزيد بحسب الالتزام والانضباط بالإسلام؛ إلا أنه مهما هبط ولاء المسلم في عين مخالفه في المعتقد إلا أنه يبقى للمسلم حق الولاء الأساسي، الذي لا يذهب إلا بكفر المرء وخروجه من الإسلام.
          </li>
          <li>
            حقوق المسلم: حرمة دمه وماله وعرضه -النصح والنصرة له ظالما أو مظلوما -الولاء للمسلم -الاجتماع على البر والتقوى والخير -الجهاد معه والصلاة خلفه. وما يحل من دم المسلم يشترط فيه: أولاً: أن يكون فيما جاء الشرع به (لا يحل دم امرئ مسلم إلا بإحدى ثلاث ...) الحديث ونحوه.ثانياً: أن يكون من مهام الإمام أو من يقوم مقام الإمام ممن له ولاية، ولا يحق لأي جماعة أو فرد مهما عظم وكبر أن يقوم به من تلقاء نفسه.
          </li>
          <li>
            الافتراق مع الأخ المسلم واعتزاله إنما يكون في محل بدعته أو انحرافه لا يتعدّى ذلك إلى غيرها من مسائل، ولا يتعداه إلى غيره حيث ثبت حق الإسلام له.
          </li>
          <li>
            أن الاختلاف والانقسام في أمة الإسلام أمر قضت سنة االله سبحانه أن يكون واقعا، ولن تسلم كل فرقة في دواخلها ونفسيتها من التحفظ والاعتراض على عقائد غيرها، لأن هذا الخلاف سنة كونية حتمية اقتضتها حكمة الخالق سبحانه.
          </li>
        </ul>

        <div style="background: #ffffff; border: 1px solid var(--syrian-gold); border-radius: 5px; padding: 7px 12px; margin-top: 4px;">
          <p style="font-weight: 700; color: var(--syrian-green-sovereign); margin-bottom: 3px; font-size: 9.2pt;">
            إن طريق الحق والنجاة لو تأملتم ليس مقتصرا على المعتقد فحسب بل له معايير ثلاثة:
          </p>
          <div style="font-size: 8.8pt; line-height: 1.55; color: #15291e;">
            <strong>الاعتقاد</strong> "الإيمان واليقين الكامل بالله وبكل ما أخبر به".<br>
            <strong>السلوك</strong> "هو الأخلاق والتزكية والإحسان".<br>
            <strong>المنهج</strong> "الطريق الذي يسلكه المؤمن في الدعوة والجهاد ...إلخ".<br>
            ولكل ركن منها تثقيل ونسبة معتبرة ، فمن التفت إلى المعتقد وأهمل وقصر في الركنين الآخرين ابتعد عن طريق الحق والنجاة بقدر إهماله للمعيارين الآخرين ، بل ربما أدى اختلال التوازن بين هذه الأركان إلى اختلال منظومته العقدية عند تداخلها بالسلوك والمنهج المنحرف ، وكذلك من ركز على السلوك دون غيره أو المنهج دون غيره والله تعالى أعلم.النتيجة: ما سبق من مرتكزات كاف حتى يستقر في النفس أن بقاء كل مدرسة مو مدارس أهل السنّة على ما تعتقده في نفسها من حيث العقيدة المنجية  ؛ لا يتعارض مع تراصّ وتماسك وتعاضد وولاء الجسد المسلم لبعضه بعضا.
          </div>
        </div>
      </div>

      <div class="doc-running-footer">
        <div>المربط الأول: إدارة الاختلاف العقدي</div>
        <div class="page-number-box">صفحة ٣ من ٧</div>
        <div>م. حسام طرشة</div>
      </div>
    </div>

    <!-- =========================================================
         الصفحة 4: المربط الثاني: العقد الاجتماعي في سورية (١)
         ========================================================= -->
    <div class="page-sheet">
      <div class="sheet-border"></div>
      <div class="sheet-border-inner"></div>

      <div class="doc-running-header">
        <div class="header-right">
          <span class="header-diamond"></span>
          المربط الثاني: مرتكزات العقد الاجتماعي في سورية
        </div>
        <div>علاقتنا مع بقية أطياف البلد</div>
      </div>

      <div class="sheet-body">
        <div class="section-ribbon">
          <h2>المربط الثاني: مرتكزات العقد الاجتماعي في سورية "علاقتنا مع بقية أطياف البلد"</h2>
          <span class="ribbon-tag">المربط ٢</span>
        </div>

        <p>
          لا شك أن الوثيقة التي كتبها الرسول صلى الله عليه وسلم في المدينة عند قدومه، وتوافق عليها أهل المدينة من المسلمين وغيرهم كبني قينقاع وبني النضير وبني قريظة من اليهود، كانت بمثابة العقد الاجتماعي الذي وضعه صلى الله عليه وسلم بين أهل المدينة.
        </p>

        <p>
          فور هجرة النبي -صَلَّى اللَّهُ عَلَيْهِ وَسَلَّمَ -إلى المدينة المنورة كتب ركائز تاريخيةً، وقد أطنب فيه المؤرخون والمستشرقون على مدار التاريخ الإسلامي، واعتبره الكثيرون مفخرة من مفاخر الحضارة الإسلامية، ومَعلَمًا من معالم مجدها السياسي والإنساني.إن هذا الوثيقة تهدف بالأساس إلى:
        </p>

        <div style="background: #ffffff; border-right: 4px solid var(--syrian-gold); padding: 7px 12px; border-radius: 4px; margin: 4px 0 6px 0; font-size: 9.1pt; line-height: 1.6;">
          • تنظيم العلاقة بين جميع طوائف وجماعات المدينة، وعلى رأسها المهاجرين والأنصار والفصائل اليهودية وغيرهم.<br>
          • يتصدى بمقتضاه المسلمون واليهود وجميع الفصائل لأي عدوان خارجي على المدينة.<br>
          وبإبرام هذه الوثيقة ـ وإقرار جميع الفصائل بما فيه ـ صارت المدينة دولة وفاقية قائدها الرسول ـ صَلَّى اللَّهُ عَلَيْهِ وَسَلَّمَ ـ، وصارت المرجعية العليا للشريعة الإسلامية، وصارت جميع الحقوق الإنسانية مكفولة، كحق حرية الاعتقاد وممارسة الشعائر، والمساواة والعدل، ويكون فيها جميع المواطنين في المدينة سواسية أمام القضاء وفي الحقوق المشتركة في داخل الدولة.
        </div>

        <h3 class="subhead">مرتكزات العقد الاجتماعي في سورية</h3>

        <ul class="charter-list">
          <li>
            <strong>الأمة الإسلامية فوق القبلية</strong> "عقد اجتماعي داخلي بين قبائل ومجاميع المسلمين بعضهم بعضا". وبهذا المرتكز يكون المسلمون على اختلاف قبائلهم وأنسابهم جماعة واحدة، فالانتماء للإسلام فوق الانتماء للقبيلة أو العائلة، وبهذا نقل رسول الله العرب من مستوى القبيلة إلى مستوى الأمة. وينطبق ذلك على كل قبيلة أو دين سماوي له عقده الاجتماعي الداخلي الخاص به.
          </li>
          <li>
            <strong>التكافل الاجتماعي</strong> بين فصائل الشعب وطوائفه.
          </li>
          <li>
            <strong>ردع الخائنين للعهود والمواثيق:</strong> فقد جاء فيما نقل عن وثيقة المدينة: "وإن المؤمنين المتقين (أيديهم) على (كل) من بغى منهم أو ابتغى دسيعة ظلم أو إثما أو عدوانا أو فسادا بين المؤمنين، وإن أيديهم عليه جميعا، ولو كان ولد أحدهم". وهذا نص في جواز حمل السلاح على أي فصيل من فصائل المدينة إذا اعتدى على المسلمين. وبموجب هذا النص حُكم بالإعدام على مجرمي قريظة -بعد معركة الأحزاب (في ذي القعدة 5 هـ/إبريل 627 م) -، لما تحالفوا مع جيوش الأحزاب الغازية للمدينة، وبغوا وخانوا بقية الفصائل، على الرغم من أنهم أبناء وطن واحد!
          </li>
          <li>
            <strong>احترام أمان المسلم:</strong> فلأي مسلم الحق في منح الأمان لأي إنسان، ومن ثم يجب على جميع أفراد الدولة أن تحترم هذا الأمان، وأن تجير من أجار المسلمُ، ولو كان المجير أحقرهم. ولا يشمل ذلك المُحدث وقد نهى صلى الله عليه وسلم عن إيواء المحدثين.
          </li>
          <li>
            <strong>حماية أهل الذمة وكل من كان تحت ولايةولي الأمر :</strong> "مالم تجرم أو تخون أو تعتدي"، وهو أصل أصيل في رعاية أهل الذمة، والمعاهدين، أو الأقليات غير الإسلامية التي تخضع لسيادة الدولة وسلطان المسلمين. فلهم –إذا خضعوا للدولة– حق النصرة على من رامهم أو اعتدى عليهم بغير حق سواء من المسلمين أو من غير المسلمين، من داخل الدولة أو من خارجها.
          </li>
        </ul>
      </div>

      <div class="doc-running-footer">
        <div>المربط الثاني: العقد الاجتماعي في سورية</div>
        <div class="page-number-box">صفحة ٤ من ٧</div>
        <div>م. حسام طرشة</div>
      </div>
    </div>

    <!-- =========================================================
         الصفحة 5: تتمة العقد الاجتماعي + المربط الثالث: السياسة الشرعية
         ========================================================= -->
    <div class="page-sheet">
      <div class="sheet-border"></div>
      <div class="sheet-border-inner"></div>

      <div class="doc-running-header">
        <div class="header-right">
          <span class="header-diamond"></span>
          تتمة العقد الاجتماعي + المربط الثالث: السياسة الشرعية
        </div>
        <div>مرتكزات سياسة الناس ورعايتهم</div>
      </div>

      <div class="sheet-body">
        <ul class="charter-list" style="margin-top: 0;">
          <li>
            <strong>الأمن الاجتماعي وضمان حق أرواح ودماء المواطنين وديّاتهم:</strong> وفي ذلك إبطال لعادة الثأر الجاهلية، وبين النص أن على المسلمين أن يكونوا جميعًا ضد المعتدي الظالم حتى يحكم عليه بحكم الشريعة. "ولا شك أن تطبيق هذا الحكم ينتج عنه استتباب الأمن في المجتمع الإسلامي منذ أن طبق المسلمون هذا الحكم".
          </li>
          <li>
            <strong>المرجعية في الحكم إلى الشريعة الإسلامية:</strong> وجاء في هذا الأصل: "وإنكم مهما اختلفتم فيه من شيء فإن مرده إلى الله –عز وجل-وإلى محمد ..." وفيه أيضا: "وإنه ما كان بين أهل هذه الصحيفة من حدث أو اشتجار يخاف فساده فإن مردَّه إلى الله، وإلى محمد رسول الله، وإن الله على أتقى ما في هذه الصحيفة وأبره".
          </li>
          <li>
            <strong>حرية الاعتقاد وممارسة الشعائر مكفولة لكل فصائل الشعب:</strong> وفي ذلك ما جاء في الوثيقة: "يهود بني عوف أمة مع المؤمنين، لليهود دينهم، وللمسلمين دينهم، ومواليهم وأنفسهم إلا من ظلم نفسه وأَثِم فإنه لا يوتغ إلا نفسه وأهل بيته" اهـ.
          </li>
          <li>
            <strong>الدعم المالي للدفاع عن البلاد مسؤولية الجميع:</strong> جاء في وثيقة المدينة هذا الأصل: "وإن اليهود ينفقون مع المؤمنين ما داموا محاربين". فعلى كل فصائل الشعب أن يدعموا الجيش ماليًا بالعدة والعتاد والرجال من أجل الدفاع عن الدولة، فكما أن الدولة وطن لكل الفصائل، كان على هذه الفصائل أن تشترك جميعها في تحمل مسؤولياتهم في الحرب.
          </li>
          <li><strong>الاستقرار المالي</strong> لكل أطياف وفصائل الشعب وطوائفه.</li>
          <li><strong>وجوب الدفاع المشترك</strong> ضد أي عدوان على البلد من جميع فصائل الشعب وطوائفه.</li>
          <li>
            <strong>النصح والبر بين جميع أهل البلاد من المواطنين من كافة فصائل وطوائف الشعب.</strong>وجاء في هذا الأصل: "وإن بينهم النصح والنصيحة والبر دون الإثم". فالأصل في العلاقة بين جميع طوائف الدولة –مهما اختلفت معتقداتهم– هو النصح المتبادل، والنصيحة التي تنفع البلاد والعباد، والبر والخير والصلة بين هذه الطوائف.
          </li>
          <li>
            <strong>حرية كل طائفة وفصيل من الشعب في عقد الأحلاف</strong> التي لا تضر بالدولة ولا مصالحها الأمنية ولا بسيادتها الداخلية والخارجية "ويكون من خلال الحكومة".
          </li>
          <li><strong>وجوب نصرة المظلوم.</strong></li>
          <li>
            <strong>حق الأمن لكل مواطن:</strong> فقد جاء في وثيقة المدينة: "إنه من خرج آمن ومن قعد آمن بالمدينة، إلا من ظلم وأثم، وإن الله جار لمن بر واتقى، ومحمد رسوله".
          </li>
        </ul>

        <div class="section-ribbon" style="margin-top: 5px;">
          <h2>المربط الثالث: مرتكزات سياسة الناس ورعاية مصالحهم "السياسة الشرعية"</h2>
          <span class="ribbon-tag">المربط ٣</span>
        </div>

        <p style="margin-bottom: 4px;">
          السياسة الشرعية بشكل عام هي تدبيرلأمور الناس لجلب المصالح ودرء المفاسد بما يوافق الشرع. ولهذه السياسة الشرعية لها أسس ومرتكزات.
        </p>

        <h3 class="subhead" style="margin-top: 3px;">مرتكزات سياسة الناس ورعاية مصالحهم "السياسة الشرعية"</h3>

        <ul class="charter-list" style="margin-bottom: 0;">
          <li>الاقتداء بسيرة النبي صلى الله عليه وسلم وسيرة صحابته ومن تبعهم في الأخلاق السياسية والكليات الأصولية والسياسية التي يستنبطها أهل العلم والتخصص.</li>
          <li>التنظيم من قواعد السياسة الشرعية، ولا يكون إلا بوجود القائم على شؤون الناس والمتولي رعايتهم وثغور البلاد ومقدراتها.</li>
          <li>أن السلطة عقد تمنحه الأمة بعقد تراضٍ للإمام أو الرئيس، وتملك حق محاسبته ويجب عليها الإشراف على ذلك.</li>
          <li>يجب على الحاكم النظر في شؤون الأمة وصلاح أمرها داخليا وخارجيا لتحقيق مصالح الرعيّة.</li>
          <li>نبذ الفرقة والخلاف، وسلامة القلوب والإخاء والتعاون الصادق بين أهل البلد، فأهل سورية بجميع مكوناتها أمة لهم حقوق وعليهم واجبات.</li>
          <li>أن جميع البرامج السياسية التي يتم تقديمها تعبّر عن وجهة نظر أصحابها، ولا يجوز نسبتها إلى الله وزعم أنها الحق من عنده، بل يجري أصحابها على طريقة اجتهدوا في أنها ترضي الله سبحانه وتعالى، فهي خاضعة للتطبيق والمراجعة والتقييم والتصحيح.</li>
          <li>من أهم قواعد سياسة الناس، النصيحة المتبادلة بين الحاكم والمحكوم وبين مؤسسات الدولة، وقد كان للحسبة في الإسلام الشأن العظيم في صلاح الراعي والرعيّة. ومن ذلك ما جاء في الحديث "الدين النصيحة، قلنا: لمن؟ قال: لله ولكتابه ولرسوله ولأئمة المسلمين وعامتهم".</li>
          <li>يرتكز القرار السياسي على أربعة عوامل رئيسة (الحاكم ـ المحكومون ـ العلاقات الإقليمية ـ العلاقات الدولية).</li>
          <li>الإسلام هو الميزان والمرجعية التي توزن بها جميع أفعال أفراد ومجموعات البلد حكاماً ومحكومين. ومصدر ذلك القرآن وصحيح السنة النبوية المطهّرة، وأصول وكليات الشريعة الإسلامية الغرّاء.</li>
          <li>الحفاظ على استقلالية البلاد وحريّة أهلها وقرارها وصون كرامتها وعزّتها والسير بها نحو أهدافها لتمكين أهلها، هو خطها السياسي الذي توزن به جميع الممارسات السياسية في المجتمع والدولة.</li>
          <li>من أهم معالم السياسة وركائز أنظمتها داخليا وخارجيا، العدل والبر، قال تعالى: (لا ينهاكم الله عن الذين لم يقاتلوكم في الدين ولم يخرجوكم من دياركم أنت تبرّوهم وتقسطوا إليهم إن الله يحب المقسطين).</li>
          <li>العمل السياسي ورعاية شؤون البلاد والعباد قائم على قاعدة درء المفاسد وجلب المصالح.</li>
          <li>الغايات ثابتة والوسائل مرنة بما يمكّننا من تحقيق الغايات والأهداف، ولا فرق بين الغاية والوسيلة من حيثُ ضبطها وإحكامها بقواعد الشرع وتعاليم الإسلام.</li>
        </ul>
      </div>

      <div class="doc-running-footer">
        <div>المربط الثالث: السياسة الشرعية ورعاية المصالح</div>
        <div class="page-number-box">صفحة ٥ من ٧</div>
        <div>م. حسام طرشة</div>
      </div>
    </div>

    <!-- =========================================================
         الصفحة 6: المربط الرابع: مرتكزات تبليغ دعوة الإسلام
         ========================================================= -->
    <div class="page-sheet">
      <div class="sheet-border"></div>
      <div class="sheet-border-inner"></div>

      <div class="doc-running-header">
        <div class="header-right">
          <span class="header-diamond"></span>
          المربط الرابـــع: مرتكزات تبليغ دعوة الإسلام
        </div>
        <div>الآيات المحكمات وركائز الدعوة</div>
      </div>

      <div class="sheet-body">
        <div class="section-ribbon">
          <h2>المربط الرابـــع: مرتكزات تبليغ دعوة الإسلام</h2>
          <span class="ribbon-tag">المربط ٤</span>
        </div>

        <p style="margin-bottom: 4px;">
          جاء في كتاب الله سبحانه وتعالى آيات محكمات فيها مرتكزات تبليغ دعوة الإسلام ، تجدها في ثلاث آيات من سورة الأنعام ، وفي ستة عشر آية من سورة الإسراء.أما سورة الأنعام فقوله تعالى:
        </p>

        <div class="quran-box" style="padding: 5px 10px; margin: 4px 0;">
          <div class="quran-text" style="font-size: 8.9pt; line-height: 1.75;">
            "قُلْ تَعَالَوْا أَتْلُ مَا حَرَّمَ رَبُّكُمْ عَلَيْكُمْ أَلاَّ تُشْرِكُوا بِهِ شَيْئًا وَبِالْوَالِدَيْنِ إِحْسَانًا وَلا تَقْتُلُوا أَوْلادَكُمْ مِنْ إِمْلاقٍ نَحْنُ نَرْزُقُكُمْ وَإِيَّاهُمْ وَلا تَقْرَبُوا الْفَوَاحِشَ مَا ظَهَرَ مِنْهَا وَمَا بَطَنَ وَلا تَقْتُلُوا النَّفْسَ الَّتِي حَرَّمَ اللَّهُ إِلاَّ بِالْحَقِّ ذَلِكُمْ وَصَّاكُمْ بِهِ لَعَلَّكُمْ تَعْقِلُونَ وَلا تَقْرَبُوا مَالَ الْيَتِيمِ إِلاَّ بِالَّتِي هِيَ أَحْسَنُ حَتَّى يَبْلُغَ أَشُدَّهُ وَأَوْفُوا الْكَيْلَ وَالْمِيزَانَ بِالْقِسْطِ لا نُكَلِّفُ نَفْسًا إِلاَّ وُسْعَهَا وَإِذَا قُلْتُمْ فَاعْدِلُوا وَلَوْ كَانَ ذَا قُرْبَى وَبِعَهْدِ اللَّهِ أَوْفُوا ذَلِكُمْ وَصَّاكُمْ بِهِ لَعَلَّكُمْ تَذَكَّرُونَ وَأَنَّ هَذَا صِرَاطِي مُسْتَقِيمًا فَاتَّبِعُوهُ وَلا تَتَّبِعُوا السُّبُلَ فَتَفَرَّقَ بِكُمْ عَنْ سَبِيلِهِ ذَلِكُمْ وَصَّاكُمْ بِهِ لَعَلَّكُمْ تَتَّقُونَ".
          </div>
        </div>

        <p style="margin-bottom: 3px;">وأما سورة الإسراء فقوله تعالى:</p>

        <div class="quran-box" style="padding: 5px 10px; margin: 4px 0;">
          <div class="quran-text" style="font-size: 8.6pt; line-height: 1.7;">
            "وَقَضَىٰ رَبُّكَ أَلَّا تَعْبُدُوا إِلَّا إِيَّاهُ وَبِالْوَالِدَيْنِ إِحْسَانًا ۚ إِمَّا يَبْلُغَنَّ عِندَكَ الْكِبَرَ أَحَدُهُمَا أَوْ كِلَاهُمَا فَلَا تَقُل لَّهُمَا أُفٍّ وَلَا تَنْهَرْهُمَا وَقُل لَّهُمَا قَوْلًا كَرِيمًا (23) وَاخْفِضْ لَهُمَا جَنَاحَ الذُّلِّ مِنَ الرَّحْمَةِ وَقُل رَّبِّ ارْحَمْهُمَا كَمَا رَبَّيَانِي صَغِيرًا (24) رَّبُّكُمْ أَعْلَمُ بِمَا فِي نُفُوسِكُمْ ۚ إِن تَكُونُوا صَالِحِينَ فَإِنَّهُ كَانَ لِلْأَوَّابِينَ غَفُورًا (25) وَآتِ ذَا الْقُرْبَىٰ حَقَّهُ وَالْمِسْكِينَ وَابْنَ السَّبِيلِ وَلَا تُبَذِّرْ تَبْذِيرًا (26) إِنَّ الْمُبَذِّرِينَ كَانُوا إِخْوَانَ الشَّيَاطِينِ ۖ وَكَانَ الشَّيْطَانُ لِرَبِّهِ كَفُورًا (27) وَإِمَّا تُعْرِضَنَّ عَنْهُمُ ابْتِغَاءَ رَحْمَةٍ مِّن رَّبِّكَ تَرْجُوهَا فَقُل لَّهُمْ قَوْلًا مَّيْسُورًا (28) وَلَا تَجْعَلْ يَدَكَ مَغْلُولَةً إِلَىٰ عُنُقِكَ وَلَا تَبْسُطْهَا كُلَّ الْبَسْطِ فَتَقْعُدَ مَلُومًا مَّحْسُورًا (29) إِنَّ رَبَّكَ يَبْسُطُ الرِّزْقَ لِمَن يَشَاءُ وَيَقْدِرُ ۚ إِنَّهُ كَانَ بِعِبَادِهِ خَبِيرًا بَصِيرًا (30) وَلَا تَقْتُلُوا أَوْلَادَكُمْ خَشْيَةَ إِمْلَاقٍ ۖ نَّحْنُ نَرْزُقُهُمْ وَإِيَّاكُمْ ۚ إِنَّ قَتْلَهُمْ كَانَ خِطْئًا كَبِيرًا (31) وَلَا تَقْرَبُوا الزِّنَا ۖ إِنَّهُ كَانَ فَاحِشَةً وَسَاءَ سَبِيلًا (32) وَلَا تَقْتُلُوا النَّفْسَ الَّتِي حَرَّمَ اللَّهُ إِلَّا بِالْحَقِّ ۗ وَمَن قُتِلَ مَظْلُومًا فَقَدْ جَعَلْنَا لِوَلِيِّهِ سُلْطَانًا فَلَا يُسْرِف فِّي الْقَتْلِ ۖ إِنَّهُ كَانَ مَنصُورًا (33) وَلَا تَقْرَبُوا مَالَ الْيَتِيمِ إِلَّا بِالَّتِي هِيَ أَحْسَنُ حَتَّىٰ يَبْلُغَ أَشُدَّهُ ۚ وَأَوْفُوا بِالْعَهْدِ ۖ إِنَّ الْعَهْدَ كَانَ مَسْئُولًا (34) وَأَوْفُوا الْكَيْلَ إِذَا كِلْتُمْ وَزِنُوا بِالْقِسْطَاسِ الْمُسْتَقِيمِ ۚ ذَٰلِكَ خَيْرٌ وَأَحْسَنُ تَأْوِيلًا (35) وَلَا تَقْفُ مَا لَيْسَ لَكَ بِهِ عِلْمٌ ۚ إِنَّ السَّمْعَ وَالْبَصَرَ وَالْفُؤَادَ كُلُّ أُولَٰئِكَ كَانَ عَنْهُ مَسْئُولًا (36) وَلَا تَمْشِ فِي الْأَرْضِ مَرَحًا ۖ إِنَّكَ لَن تَخْرِقَ الْأَرْضَ وَلَن تَبْلُغَ الْجِبَالَ طُولًا (37) كُلُّ ذَٰلِكَ كَانَ سَيِّئُهُ عِندَ رَبِّكَ مَكْرُوهًا (38)".
          </div>
        </div>

        <h3 class="subhead" style="margin-top: 4px;">مرتكزات تبليغ دعوة الإسلام</h3>

        <ul class="charter-list" style="margin-bottom: 0;">
          <li>
            <strong>المنهج:</strong> وهو حقيقة الشيء ولا يطرأ عليه التغيير ولا التبديل فهو في الإسلام عبارة عن القرآن والسنة وما اتفق عليه الصحابة ومن تبعهم ، وهو الترياق والمحرك الحقيقي لحركة الشعوب المسلمة ، به يستقيم أمرها وبه تفتح ميادين الدعوة إلى الإسلام وبه يكون خلاصها أمام ربها.
          </li>
          <li>
            <strong>الأسلوب:</strong> وهو التخلق الذي تشتريه نفس المسلم حتى يصير ممارسة تلقائية مراعية حسن الأداء والرقي والتجويد في كل شيء فكم من منهج سليم صحيح أفسده أسلوب غير منضبط.
          </li>
          <li>
            <strong>الوسيلة:</strong> وهي المرتكز المهم الذي تقوم عليه حركة التجديد والتحديث لأن الوسائل شتى وأمرها غير محكوم بأحكام ثابتة ولذا عندما يتحدث كثير من المهتمين بالعمل الدعوي بالتجديد إنما يقصدون التجديد في الوسائل
          </li>
          <li>
            <strong>الدعوة</strong> يدعو بها جميع المسلمين على اختلاف أطيافهم وآرائهم ولا يُدخلون المدعوّين للإسلام في تفاصيل ودقائق وفروع الخلافات الفقهية والعقدية بين أهل القبلة من الفرق والجماعات من أهل السنة.
          </li>
          <li>
            <strong>ضبط المرجعية</strong> في هذه الدعوة وهذا من تنظيم العمل ، وبذلك يجتمع المسلمون جميعا على منهجية وسلوك ووسائل تضبط الدعوة إلى الإسلام.
          </li>
        </ul>
      </div>

      <div class="doc-running-footer">
        <div>المربط الرابع: تبليغ دعوة الإسلام</div>
        <div class="page-number-box">صفحة ٦ من ٧</div>
        <div>م. حسام طرشة</div>
      </div>
    </div>

    <!-- =========================================================
         الصفحة 7: المربط الخامس وخاتمة الوثيقة والاعتماد
         ========================================================= -->
    <div class="page-sheet">
      <div class="sheet-border"></div>
      <div class="sheet-border-inner"></div>

      <div class="doc-running-header">
        <div class="header-right">
          <span class="header-diamond"></span>
          المربط الخامس: مرتكزات السياسة الخارجية لسورية
        </div>
        <div>خاتمة الوثيقة والاعتماد</div>
      </div>

      <div class="sheet-body">
        <div class="section-ribbon">
          <h2>المربط الخامس: مرتكزات السياسة الخارجية لسورية والعلاقة مع الآخر إقليميا ودولياً</h2>
          <span class="ribbon-tag">المربط ٥</span>
        </div>

        <p style="margin-bottom: 4px;">
          لا بد للمتصدرين لشؤون البلاد أن يكونوا على معرفة في إدارة البلاد بما يخص علاقتها بالمحيط الإقليمي والدولي، وهو أشبه بمسيرة السفينة بقيادة ربّانها في وسط موج وحوله من السفن الأخرى المختلفة منها القريب ومنها البعيد منها العدو ومنها الصديق منها المنافس ومنها المهيمن، وواجب على أهل سورية جميعا أن يكونوا متوافقين من خلال مرتكزات تتعلق بالسياسة الخارجية والعلاقة مع الإقليم والعالم.
        </p>

        <h3 class="subhead" style="margin-top: 2px;">مرتكزات السياسة الخارجية والعلاقات الإقليمية والدولية</h3>

        <ul class="charter-list">
          <li>بناء العلاقة على أساس احترام سيادتنا على أرضنا ولا يكون أي من العلاقات على حساب السيادة (استقلال القرار ـ والسيادة على الأرض)</li>
          <li>الأصل في العلاقة مع الآخرين (فإن جنحوا للسلم فاجنح لها وتوكل على الله).</li>
          <li>تنظيم علاقات التبادل التجاري والثقافي وفق هوية أهل سورية الإسلامية  بكليّاتها الأخلاقية المرتكزة على الفطرة الإنسانية والعدل التامّ، فلا تناقض مع مبادئ وقيم الإسلام الثابتة البيّنة.</li>
          <li>بناء الاتفاقات الخاصة برعاية مصالح وحقوق الجاليات السورية في أي بلد من البلاد الإقليمية والدولية على أساس سليم بما يحفظ قوق وخصوصية جالياتنا في بلاد الاغتراب وبما لا يتعارض مع سيادة تلك الدول في أرضها، وكذلك رعاية مصالح جاليات البلدان الأخرى في سورية بما لا يتعارض مع سيادة شعبها على أرضه.</li>
          <li>لا يتخذ قرار السلم والحرب مع أي بلد من البلدان إلا بقرار على مستوى أهل الرأي والكلمة والقيادة والسيادة في أقوامهم ومدنهم ومناطقهم وعشائرهم وقبائلهم، من خلال استشارة رئاسة البلاد وحكومتها بما يتفق مع المصالح العليا للبلاد وبما يحفظ أمنها وسيادتها ويصون هويتها وقيمها.</li>
          <li>التعاون مفتوح في كل فضيلة وما يُحقق العدل ورفع الظلم وإغاثة الملهوف ومساندة الضعفاء والمتضررين، وأنه حق لكل إنسان في أي أمة كانت.</li>
          <li>لا بد من إرسال السفراء والمندوبين إلى البلاد التي لا يتعارض فتح العلاقات معها مع مصالح سورية ومبادئ وقيم وهوية أهلها بغالبيته المسلمة، واستقبال سفراء ومندوبي تلك الدول، لضرورة التواصل والتنسيق في كل ما من شأنه تحقيق مصالح الأطراف جميعا وبما يتوافق مع سيادتهم ومبادئهم وهويتهم.</li>
          <li>أمن البلاد مقدم على أي علاقة، كما أنه لا بأس بالتعاون الإقليمي لتحقيق الأمن المشترك بين البلدان الإقليمية، شريطة ألا يتعارض مع منطلقات ومبادئ ومحددات السياسة الخارجية للبلاد وقيمها.</li>
          <li>الوفاء بالعهود والمواثيق، ركيزة أساسية في العلاقات الخارجية لا بد من احترامها.</li>
        </ul>

        <!-- خاتمة الوثيقة والتحذير من الفرق المنحرفة -->
        <div style="background: #fff5f5; border: 1.5px solid #eab8b8; border-right: 5px solid var(--syrian-red-star); border-radius: 5px; padding: 7px 12px; margin: 6px 0;">
          <p style="font-size: 9.2pt; color: #36070a; margin-bottom: 4px; line-height: 1.6;">
            إن تحقيق معالم الاجتماع وتوحيد الصف وتمكين دولة الإسلام ونهضة شعبنا المسلم ، فلا نفترق في ذلك مع مسلم ممن ثبت له حق الإسلام ، إلا فرقتين ، لأن بدعتهما في الحاكمية والسياسة الشرعية والإمامة تجعلهما خطرا الى أمن وسلامة الدولة والمجتمع ، وهما:
          </p>
          <div style="font-size: 9pt; color: #4a0d11; line-height: 1.6; padding-right: 12px;">
            - <strong>الرافضة</strong> الذين جعلوا الإمامة والحاكمية في سلالة نسبوا لها وخلعوا عليها الشرعية الإلهية ما أنزل الله بها من سلطان.<br>
            - <strong>الخوارج</strong> الذين غلوا في الحاكمية حتى صاروا كلاب نار تقتل وتكفر وتستبيح بيضة المسلمين جماعات وشعوبا بحجة الحكم والإمامة وتنصيب الخليفة.
          </div>
        </div>

        <!-- خانة التوقيع والاعتماد والختم الرسمي للميثاق -->
        <div style="display: flex; justify-content: space-around; text-align: center; border-top: 1px dashed var(--syrian-gold); padding-top: 10px; margin-top: 8px;">
          <div style="width: 45%;">
            <div style="font-size: 9.5pt; font-weight: 700; color: var(--syrian-green-sovereign); margin-bottom: 25px;">كتبه وحرره:</div>
            <div style="border-bottom: 1px solid #14532d; width: 60%; margin: 0 auto 4px auto;"></div>
            <div style="font-family: 'Reem Kufi', sans-serif; font-size: 11pt; font-weight: 800;">م. حسام طرشة</div>
            <div style="font-size: 8.5pt; color: var(--text-sub);">سورية - 2026 م</div>
          </div>
          <div style="width: 45%;">
            <div style="font-size: 9.5pt; font-weight: 700; color: var(--syrian-green-sovereign); margin-bottom: 25px;">الاعتماد والاصطفاف الوطني:</div>
            <div style="border-bottom: 1px solid #14532d; width: 60%; margin: 0 auto 4px auto;"></div>
            <div style="font-family: 'Reem Kufi', sans-serif; font-size: 11pt; font-weight: 800;">أهل السنّة والفعاليات الوطنية في سورية</div>
            <div style="font-size: 8.5pt; color: var(--text-sub);">«واعتصموا بحبل الله جميعاً ولا تفرقوا»</div>
          </div>
        </div>
      </div>

      <div class="doc-running-footer">
        <div>المربط الخامس: السياسة الخارجية والخاتمة</div>
        <div class="page-number-box">صفحة ٧ من ٧ (خاتمة الميثاق)</div>
        <div>م. حسام طرشة</div>
      </div>
    </div>

  </div>
  <!-- بداية قسم زر التوقيع الأخضر بالخروج من الحاوية المغلقة -->
<div style="
    text-align: center !important; 
    margin: 80px auto 40px auto !important; 
    padding: 20px !important; 
    font-family: 'Cairo', 'Segoe UI', Tahoma, sans-serif !important;
    clear: both !important;
    display: block !important;
    position: relative !important;
    z-index: 99999 !important; /* لضمان ظهور الزر فوق أي عناصر أخرى */
">
    <!-- تأكد من وضع رابط استمارتك المباشر مكان العبارة أدناه -->
    <a href="https://forms.gle/SvDn2ESmcov7SX829" target="_blank" style="
        display: inline-block !important;
        padding: 16px 40px !important;
        font-size: 18px !important;
        font-weight: bold !important;
        color: #ffffff !important;
        background-color: #1b4d3e !important; /* الأخضر الغامق الملكي */
        border-radius: 30px !important;
        text-decoration: none !important;
        box-shadow: 0 4px 15px rgba(20, 70, 55, 0.3) !important;
        transition: all 0.3s ease !important;
    " onmouseover="this.style.backgroundColor='#12362b'; this.style.transform='translateY(-3px)';" onmouseout="this.style.backgroundColor='#1b4d3e'; this.style.transform='translateY(0)';">
        اضغط للانضمام لقائمة الموقعين
    </a>
</div>
<!-- نهاية قسم زر التوقيع -->
</body>
</html>
