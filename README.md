<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>لوحة تحكم احترافية - نظام إدارة المحتوى</title>
    <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@400;600;700&family=Poppins:wght@400;500;600&display=swap" rel="stylesheet">
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons+Round" rel="stylesheet">
    <style>
        /* الجزء الثاني من الكود (أنماط CSS) سيأتي هنا */
    </style>
</head>
<body>
    <div class="sidebar">
        <div class="sidebar-header">
            <span class="material-icons-round logo-icon">auto_stories</span>
            <h2 class="logo-text">إدارة المحتوى</h2>
        </div>
        <ul class="nav-links">
            <li><a href="#" onclick="showPage('dashboard', this)"><span class="material-icons-round">dashboard</span>الرئيسية</a></li>
            <li><a href="#" onclick="showPage('products', this)"><span class="material-icons-round">inventory_2</span>المنتجات</a></li>
            <li><a href="#" onclick="showPage('orders', this)"><span class="material-icons-round">shopping_cart</span>الطلبات</a></li>
            <li><a href="#" onclick="showPage('customers', this)"><span class="material-icons-round">people_alt</span>العملاء</a></li>
            <li><a href="#" onclick="showPage('reports', this)"><span class="material-icons-round">analytics</span>التقارير</a></li>
            <li><a href="#" onclick="showPage('settings', this)"><span class="material-icons-round">settings</span>الإعدادات</a></li>
            <li class="logout-link"><a href="#" onclick="showAlert('تم تسجيل الخروج بنجاح!', 'success')"><span class="material-icons-round">logout</span>تسجيل الخروج</a></li>
        </ul>
    </div>

    <div class="main-content">
        <header class="main-header">
            <h1 id="page-title">لوحة التحكم</h1>
            <div class="header-right">
                <span class="current-currency">العملة: <span id="displayed-currency">ج.س</span></span>
                <button class="profile-btn">
                    <span class="material-icons-round">account_circle</span>
                    الحساب
                </button>
            </div>
        </header>

        ```

---

### الجزء الثاني: أنماط CSS الاحترافية (Professional CSS Styling)

هذا الجزء يحتوي على جميع أنماط CSS لتصميم الواجهة بشكل احترافي، بما في ذلك التخطيط، الألوان، الخطوط، الأزرار، الجداول، والتحسينات المرئية الأخرى. يجب وضع هذا الكود داخل وسم `<style>` في الجزء الأول.

```css
        /* الخطوط الأساسية والتخطيط العام */
        body {
            font-family: 'Cairo', sans-serif; /* للغة العربية */
            direction: rtl; /* اتجاه من اليمين لليسار */
            margin: 0;
            background-color: #f0f2f5; /* خلفية رمادية فاتحة */
            color: #333;
            display: flex;
            min-height: 100vh;
            overflow-x: hidden; /* منع التمرير الأفقي غير المرغوب فيه */
        }

        /* الشريط الجانبي */
        .sidebar {
            width: 280px;
            background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%); /* تدرج لوني جذاب */
            color: #ecf0f1;
            padding: 20px 0;
            box-shadow: 4px 0 10px rgba(0, 0, 0, 0.15); /* ظل أعمق */
            display: flex;
            flex-direction: column;
            align-items: center;
            position: sticky; /* لجعل الشريط الجانبي ثابتًا عند التمرير */
            top: 0;
            height: 100vh;
            overflow-y: auto; /* للسماح بالتمرير إذا كانت الروابط كثيرة */
            transition: all 0.3s ease-in-out; /* انتقال سلس عند التغييرات */
        }

        .sidebar-header {
            display: flex;
            align-items: center;
            margin-bottom: 40px;
            padding: 0 20px;
            justify-content: center;
            width: 100%;
        }

        .sidebar-header .logo-icon {
            font-size: 38px;
            color: #2ecc71; /* لون أخضر جذاب */
            margin-left: 10px;
        }

        .sidebar-header .logo-text {
            color: #ecf0f1;
            font-size: 1.6em;
            margin: 0;
            font-weight: 700;
        }

        .nav-links {
            list-style: none;
            padding: 0;
            width: 100%;
            flex-grow: 1; /* لجعل القائمة تملأ المساحة المتاحة */
        }

        .nav-links li {
            margin-bottom: 5px;
        }

        .nav-links li a {
            display: flex;
            align-items: center;
            padding: 15px 25px;
            color: #ecf0f1;
            text-decoration: none;
            transition: all 0.3s ease; /* انتقال أزرار التنقل */
            font-size: 1.05em;
            font-weight: 500;
            border-radius: 8px; /* حواف مستديرة للروابط */
            margin: 0 15px;
        }

        .nav-links li a .material-icons-round {
            margin-left: 15px;
            font-size: 26px;
            color: #bdc3c7; /* لون أيقونة افتراضي */
            transition: color 0.3s ease;
        }

        .nav-links li a:hover {
            background-color: rgba(255, 255, 255, 0.1); /* خلفية شفافة عند التحويم */
            color: #2ecc71;
            transform: translateX(-5px); /* تأثير بسيط عند التحويم */
        }

        .nav-links li a.active {
            background-color: #2ecc71; /* لون أخضر للخلفية النشطة */
            color: #ffffff;
            box-shadow: 0 4px 10px rgba(46, 204, 113, 0.4); /* ظل للأزرار النشطة */
            transform: translateX(-5px);
        }

        .nav-links li a.active .material-icons-round {
            color: #ffffff; /* أيقونة بيضاء عند النشاط */
        }

        .logout-link {
            margin-top: auto; /* لدفع زر تسجيل الخروج للأسفل */
            padding-top: 20px;
            border-top: 1px solid rgba(255, 255, 255, 0.1);
        }
        .logout-link a {
            color: #e74c3c !important; /* لون أحمر لتسجيل الخروج */
        }
        .logout-link a:hover {
            background-color: rgba(231, 76, 60, 0.2);
        }
        .logout-link a .material-icons-round {
            color: #e74c3c !important;
        }

        /* المحتوى الرئيسي */
        .main-content {
            flex-grow: 1;
            padding: 20px 30px;
            background-color: #f0f2f5;
            transition: all 0.3s ease-in-out;
        }

        /* رأس المحتوى الرئيسي */
        .main-header {
            background-color: #ffffff;
            padding: 20px 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08); /* ظل ألطف */
            margin-bottom: 30px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .main-header #page-title {
            margin: 0;
            color: #2c3e50;
            font-size: 1.8em;
            font-weight: 700;
        }

        .header-right {
            display: flex;
            align-items: center;
            font-family: 'Poppins', sans-serif; /* خط Popins للأرقام والعملة */
        }

        .current-currency {
            font-size: 1.1em;
            font-weight: 600;
            color: #2ecc71;
            margin-left: 20px;
        }

        .profile-btn {
            background-color: #3498db; /* لون أزرق */
            color: white;
            padding: 10px 18px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1em;
            display: flex;
            align-items: center;
            transition: background-color 0.3s ease, transform 0.2s ease;
        }

        .profile-btn .material-icons-round {
            margin-left: 8px;
            font-size: 20px;
        }

        .profile-btn:hover {
            background-color: #2980b9;
            transform: translateY(-2px);
        }

        /* أقسام الصفحات (المحتوى الفعلي) */
        .page-section {
            background-color: #ffffff;
            padding: 30px;
            border-radius: 12px;
            box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
            margin-bottom: 30px;
            display: none; /* مخفية افتراضياً */
            transition: opacity 0.5s ease-in-out; /* انتقال سلس عند الظهور */
            opacity: 0;
        }

        .page-section.active {
            display: block;
            opacity: 1;
        }

        .page-section h2 {
            color: #2c3e50;
            font-size: 1.6em;
            margin-top: 0;
            margin-bottom: 25px;
            padding-bottom: 10px;
            border-bottom: 2px solid #eee;
        }
        .page-section h3 {
            color: #34495e;
            font-size: 1.3em;
            margin-top: 25px;
            margin-bottom: 15px;
        }


        /* أنماط النموذج */
        .form-group {
            margin-bottom: 20px;
        }

        .form-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: #555;
            font-size: 0.95em;
        }

        .form-group input[type="text"],
        .form-group input[type="number"],
        .form-group textarea,
        .form-group select {
            width: calc(100% - 24px); /* لتغطية العرض مع البادينج */
            padding: 12px;
            border: 1px solid #dcdfe6; /* لون حدود أنظف */
            border-radius: 8px;
            font-size: 1em;
            box-sizing: border-box;
            transition: border-color 0.3s ease, box-shadow 0.3s ease;
            font-family: 'Poppins', sans-serif; /* خط Popins للأرقام */
        }

        .form-group input:focus,
        .form-group textarea:focus,
        .form-group select:focus {
            border-color: #2ecc71;
            box-shadow: 0 0 0 3px rgba(46, 204, 113, 0.2); /* ظل تركيز ناعم */
            outline: none;
        }

        .form-group textarea {
            resize: vertical;
            min-height: 120px;
        }

        /* أنماط الأزرار العامة */
        .btn {
            background-color: #2ecc71;
            color: white;
            padding: 12px 25px;
            border: none;
            border-radius: 8px;
            cursor: pointer;
            font-size: 1.05em;
            font-weight: 600;
            transition: background-color 0.3s ease, transform 0.2s ease, box-shadow 0.3s ease;
            box-shadow: 0 4px 10px rgba(46, 204, 113, 0.3);
            display: inline-flex; /* لمركزة المحتوى إذا كان هناك أيقونة */
            align-items: center;
            justify-content: center;
            margin-left: 10px; /* مسافة بين الأزرار */
        }

        .btn:hover {
            background-color: #27ae60;
            transform: translateY(-2px);
            box-shadow: 0 6px 15px rgba(46, 204, 113, 0.4);
        }

        .btn-secondary {
            background-color: #3498db;
            box-shadow: 0 4px 10px rgba(52, 152, 219, 0.3);
        }
        .btn-secondary:hover {
            background-color: #2980b9;
            box-shadow: 0 6px 15px rgba(52, 152, 219, 0.4);
        }

        .btn-danger {
            background-color: #e74c3c;
            box-shadow: 0 4px 10px rgba(231, 76, 60, 0.3);
        }
        .btn-danger:hover {
            background-color: #c0392b;
            box-shadow: 0 6px 15px rgba(231, 76, 60, 0.4);
        }

        /* أنماط حاوية التنبيهات */
        .alert-container {
            position: fixed;
            top: 25px;
            right: 25px;
            z-index: 1050; /* أعلى من أي شيء آخر */
            max-width: 350px;
        }

        .alert {
            display: flex;
            align-items: center;
            background-color: #fff;
            padding: 15px 20px;
            border-radius: 8px;
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.15); /* ظل أعمق */
            margin-bottom: 15px;
            opacity: 0;
            animation: fadeInOut 5.5s forwards; /* انيميشن مع اختفاء بطيء */
            position: relative;
            overflow: hidden; /* لإخفاء شريط التقدم */
        }

        .alert::after { /* شريط تقدم الاختفاء */
            content: '';
            position: absolute;
            bottom: 0;
            right: 0;
            width: 100%;
            height: 4px;
            background-color: rgba(0,0,0,0.1);
            animation: progressBar 5s linear forwards;
        }

        .alert.success { border-right: 6px solid #28a745; }
        .alert.error { border-right: 6px solid #dc3545; }
        .alert.info { border-right: 6px solid #007bff; }

        .alert .material-icons-round {
            margin-right: 12px;
            font-size: 28px;
        }

        .alert.success .material-icons-round { color: #28a745; }
        .alert.error .material-icons-round { color: #dc3545; }
        .alert.info .material-icons-round { color: #007bff; }

        /* انيميشن الظهور والاختفاء */
        @keyframes fadeInOut {
            0% { opacity: 0; transform: translateY(-30px); }
            10% { opacity: 1; transform: translateY(0); }
            90% { opacity: 1; transform: translateY(0); }
            100% { opacity: 0; transform: translateY(-30px); }
        }

        /* انيميشن شريط التقدم */
        @keyframes progressBar {
            from { width: 100%; }
            to { width: 0%; }
        }

        /* أنماط الجداول الاحترافية */
        table {
            width: 100%;
            border-collapse: separate; /* لفصل الحدود قليلاً */
            border-spacing: 0;
            margin-top: 25px;
            border-radius: 8px; /* حواف مستديرة للجدول */
            overflow: hidden; /* لإخفاء المحتوى الزائد */
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
        }

        table thead {
            background-color: #f8f9fa; /* لون خلفية رأس الجدول */
        }

        table th, table td {
            border-bottom: 1px solid #ebf0f5; /* حدود سفلية ناعمة */
            padding: 15px;
            text-align: right;
            font-family: 'Poppins', sans-serif; /* خط Popins للأرقام */
        }

        table th {
            color: #555;
            font-weight: 600;
            font-size: 0.95em;
        }

        table tr:last-child td {
            border-bottom: none; /* إزالة الحدود السفلية للصف الأخير */
        }

        table tbody tr:hover {
            background-color: #fcfcfc; /* لون خفيف عند التحويم على الصف */
            cursor: pointer;
        }

        table td .btn {
            padding: 8px 15px; /* أزرار أصغر داخل الجدول */
            font-size: 0.9em;
            box-shadow: none; /* إزالة الظل من أزرار الجدول */
        }
        table td .btn:hover {
            transform: none; /* إزالة تأثير التحويم من أزرار الجدول */
        }

        /* لوحة Dashboard (البطاقات الإحصائية) */
        .dashboard-cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(280px, 1fr)); /* تخطيط شبكي متجاوب */
            gap: 25px; /* مسافة أكبر بين البطاقات */
            margin-top: 20px;
        }

        .card {
            background-color: #ffffff;
            padding: 25px;
            border-radius: 12px;
            box-shadow: 0 6px 20px rgba(0, 0, 0, 0.08);
            text-align: center;
            transition: transform 0.3s ease, box-shadow 0.3s ease;
            display: flex;
            flex-direction: column;
            align-items: center;
            justify-content: center;
        }

        .card:hover {
            transform: translateY(-5px); /* تأثير رفع خفيف */
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.12);
        }

        .card .material-icons-round {
            font-size: 48px;
            margin-bottom: 15px;
            color: #3498db; /* لون أيقونة افتراضي */
        }

        .card.products-card .material-icons-round { color: #e67e22; }
        .card.orders-card .material-icons-round { color: #3498db; }
        .card.sales-card .material-icons-round { color: #2ecc71; }

        .card h3 {
            margin: 0 0 10px 0;
            color: #555;
            font-size: 1.1em;
            font-weight: 600;
        }

        .card p {
            font-size: 2.5em;
            font-weight: 700;
            color: #2c3e50;
            margin: 0;
            font-family: 'Poppins', sans-serif;
        }
        .card.sales-card p {
            color: #2ecc71;
        }


        /* تصميم متجاوب (Responsive Design) */
        @media (max-width: 1024px) {
            .sidebar {
                width: 250px;
            }
            .main-content {
                padding: 15px 20px;
            }
            .main-header {
                padding: 15px 20px;
            }
            .main-header #page-title {
                font-size: 1.6em;
            }
            .current-currency {
                font-size: 1em;
            }
            .profile-btn {
                padding: 8px 15px;
                font-size: 0.9em;
            }
        }

        @media (max-width: 768px) {
            body {
                flex-direction: column;
            }

            .sidebar {
                width: 100%;
                height: auto;
                padding: 10px 0;
                box-shadow: 0 4px 10px rgba(0, 0, 0, 0.15);
                position: relative; /* إزالة sticky للمحمول */
                overflow-y: visible; /* إزالة التمرير العمودي */
            }

            .sidebar-header {
                margin-bottom: 20px;
            }

            .nav-links {
                flex-direction: row; /* جعل الروابط أفقية */
                flex-wrap: wrap; /* تسمح بالالتفاف */
                justify-content: center;
                gap: 5px; /* مسافة بين العناصر */
            }

            .nav-links li {
                width: auto;
                margin: 0;
            }
            .nav-links li a {
                padding: 10px 15px;
                font-size: 0.9em;
                margin: 5px;
            }
            .nav-links li a .material-icons-round {
                margin-left: 8px;
                font-size: 20px;
            }

            .logout-link {
                margin-top: 15px;
                padding-top: 15px;
            }

            .main-content {
                padding: 15px;
            }
            .main-header {
                flex-direction: column;
                align-items: flex-start;
                padding: 15px;
            }
            .main-header #page-title {
                margin-bottom: 10px;
                font-size: 1.5em;
            }
            .header-right {
                width: 100%;
                justify-content: space-between;
            }
            .current-currency {
                margin-left: 0;
            }

            .page-section {
                padding: 20px;
            }
            .page-section h2 {
                font-size: 1.4em;
                margin-bottom: 20px;
            }
            .form-group input, .form-group textarea, .form-group select {
                width: calc(100% - 20px);
            }

            .alert-container {
                top: 15px;
                right: 15px;
                max-width: calc(100% - 30px);
            }
            .dashboard-cards {
                grid-template-columns: 1fr; /* عمود واحد للموبايل */
            }
        }

        @media (max-width: 480px) {
            .nav-links {
                justify-content: space-between; /* توزيع متساوٍ للروابط */
            }
            .nav-links li a {
                padding: 8px 10px;
                font-size: 0.8em;
                margin: 3px;
            }
            .sidebar-header .logo-text {
                font-size: 1.4em;
            }
            .profile-btn {
                padding: 6px 12px;
                font-size: 0.85em;
<section id="dashboard" class="page-section active">
            <h2>نظرة عامة على لوحة التحكم</h2>
            <p>مرحباً بك في لوحة التحكم الاحترافية. هذه الشاشة توفر لك نظرة شاملة على أداء نظامك.</p>

            <div class="dashboard-cards">
                <div class="card products-card">
                    <span class="material-icons-round">inventory_2</span>
                    <h3>المنتجات الإجمالية</h3>
                    <p>150</p>
                </div>
                <div class="card orders-card">
                    <span class="material-icons-round">shopping_cart</span>
                    <h3>الطلبات الجديدة</h3>
                    <p>25</p>
                </div>
                <div class="card sales-card">
                    <span class="material-icons-round">trending_up</span>
                    <h3>إجمالي المبيعات</h3>
                    <p>50,000 ج.س</p>
                </div>
            </div>
            <h3>النشاط الأخير</h3>
            <div class="page-section" style="display: block; padding: 20px; margin-top: 20px;">
                <p>مبيعة جديدة: منتج 'هاتف ذكي' بقيمة 2000 ج.س</p>
                <p>تم تحديث حالة الطلب #003 إلى 'تم الشحن'</p>
                <p>تم إضافة عميل جديد: سلمى أحمد</p>
            </div>
        </section>

        <section id="products" class="page-section">
            <h2>إدارة المنتجات</h2>
            <form id="product-form">
                <h3>إضافة منتج جديد</h3>
                <div class="form-group">
                    <label for="product-name">اسم المنتج:</label>
                    <input type="text" id="product-name" required placeholder="اسم المنتج هنا">
                </div>
                <div class="form-group">
                    <label for="product-price">السعر (ج.س):</label>
                    <input type="number" id="product-price" step="0.01" required min="0" placeholder="0.00">
                </div>
                <div class="form-group">
                    <label for="product-description">الوصف:</label>
                    <textarea id="product-description" placeholder="وصف تفصيلي للمنتج..."></textarea>
                </div>
                <button type="submit" class="btn">
                    <span class="material-icons-round">add_circle</span> إضافة منتج
                </button>
            </form>

            <h3>قائمة المنتجات الحالية</h3>
            <table id="product-list">
                <thead>
                    <tr>
                        <th>الاسم</th>
                        <th>السعر (ج.س)</th>
                        <th>الوصف</th>
                        <th>إجراءات</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>لابتوب احترافي</td>
                        <td>25000.00 ج.س</td>
                        <td>لابتوب بمعالج i7 و 16GB RAM</td>
                        <td>
                            <button class="btn btn-secondary" onclick="editProduct(this)"><span class="material-icons-round">edit</span> تعديل</button>
                            <button class="btn btn-danger" onclick="deleteProduct(this)"><span class="material-icons-round">delete</span> حذف</button>
                        </td>
                    </tr>
                    <tr>
                        <td>شاشة 27 بوصة</td>
                        <td>7500.00 ج.س</td>
                        <td>شاشة بدقة 4K ومعدل تحديث 144Hz</td>
                        <td>
                            <button class="btn btn-secondary" onclick="editProduct(this)"><span class="material-icons-round">edit</span> تعديل</button>
                            <button class="btn btn-danger" onclick="deleteProduct(this)"><span class="material-icons-round">delete</span> حذف</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section id="orders" class="page-section">
            <h2>إدارة الطلبات</h2>
            <p>هنا يمكنك عرض وإدارة جميع الطلبات المستلمة وتتبع حالتها.</p>
            <table id="order-list">
                <thead>
                    <tr>
                        <th>رقم الطلب</th>
                        <th>العميل</th>
                        <th>التاريخ</th>
                        <th>الإجمالي (ج.س)</th>
                        <th>الحالة</th>
                        <th>إجراءات</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>#0010</td>
                        <td>أحمد علي</td>
                        <td>2025-06-30</td>
                        <td>1200.50 ج.س</td>
                        <td><span style="color: #f39c12; font-weight: 600;">قيد التنفيذ</span></td>
                        <td>
                            <button class="btn btn-secondary"><span class="material-icons-round">visibility</span> عرض</button>
                            <button class="btn btn-info" style="background-color: #555;"><span class="material-icons-round">local_shipping</span> تحديث حالة</button>
                        </td>
                    </tr>
                    <tr>
                        <td>#0009</td>
                        <td>فاطمة محمد</td>
                        <td>2025-06-28</td>
                        <td>850.00 ج.س</td>
                        <td><span style="color: #28a745; font-weight: 600;">تم التوصيل</span></td>
                        <td>
                            <button class="btn btn-secondary"><span class="material-icons-round">visibility</span> عرض</button>
                            <button class="btn btn-info" style="background-color: #555;"><span class="material-icons-round">local_shipping</span> تحديث حالة</button>
                        </td>
                    </tr>
                    <tr>
                        <td>#0008</td>
                        <td>خالد حسن</td>
                        <td>2025-06-27</td>
                        <td>3200.75 ج.س</td>
                        <td><span style="color: #dc3545; font-weight: 600;">ملغى</span></td>
                        <td>
                            <button class="btn btn-secondary"><span class="material-icons-round">visibility</span> عرض</button>
                            <button class="btn btn-info" style="background-color: #555;"><span class="material-icons-round">local_shipping</span> تحديث حالة</button>
                        </td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section id="customers" class="page-section">
            <h2>إدارة العملاء</h2>
            <p>يمكنك هنا عرض تفاصيل العملاء المسجلين في نظامك.</p>
            <table id="customer-list">
                <thead>
                    <tr>
                        <th>الاسم</th>
                        <th>البريد الإلكتروني</th>
                        <th>رقم الهاتف</th>
                        <th>تاريخ التسجيل</th>
                        <th>إجراءات</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>أحمد علي</td>
                        <td>ahmed.ali@example.com</td>
                        <td>+249912345678</td>
                        <td>2024-01-15</td>
                        <td><button class="btn btn-secondary"><span class="material-icons-round">person</span> الملف الشخصي</button></td>
                    </tr>
                    <tr>
                        <td>فاطمة محمد</td>
                        <td>fatima.mohamed@example.com</td>
                        <td>+249912345679</td>
                        <td>2024-02-20</td>
                        <td><button class="btn btn-secondary"><span class="material-icons-round">person</span> الملف الشخصي</button></td>
                    </tr>
                    <tr>
                        <td>سارة حسين</td>
                        <td>sara.hussein@example.com</td>
                        <td>+249912345680</td>
                        <td>2024-03-01</td>
                        <td><button class="btn btn-secondary"><span class="material-icons-round">person</span> الملف الشخصي</button></td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section id="reports" class="page-section">
            <h2>التقارير والتحليلات</h2>
            <p>احصل على رؤى قيمة من خلال تقارير المبيعات الشاملة والتحليلات.</p>
            <div class="dashboard-cards" style="grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));">
                <div class="card" style="background-color: #e8f5e9;">
                    <span class="material-icons-round" style="color: #4caf50;">trending_up</span>
                    <h3>أفضل منتج مبيعًا</h3>
                    <p style="color: #4caf50; font-size: 1.8em;">هاتف ذكي X</p>
                </div>
                <div class="card" style="background-color: #e3f2fd;">
                    <span class="material-icons-round" style="color: #2196f3;">groups</span>
                    <h3>أكثر عميل نشاطًا</h3>
                    <p style="color: #2196f3; font-size: 1.8em;">محمد علي</p>
                </div>
                <div class="card" style="background-color: #fff3e0;">
                    <span class="material-icons-round" style="color: #ff9800;">calendar_month</span>
                    <h3>مبيعات الشهر الحالي</h3>
                    <p style="color: #ff9800; font-size: 1.8em;">15,000 ج.س</p>
                </div>
            </div>
            <h3>رسوم بيانية تفاعلية (مثال)</h3>
            <div class="page-section" style="display: block; padding: 25px; min-height: 250px; background-color: #fcfcfc; margin-top: 25px;">
                <p style="text-align: center; color: #777;">
                    (هنا يمكن دمج مكتبات مثل Chart.js أو D3.js لعرض رسوم بيانية تفاعلية للمبيعات، المنتجات الأكثر مبيعًا، إلخ.)
                </p>
                <div style="background-color: #eee; height: 180px; display: flex; align-items: center; justify-content: center; color: #bbb; border-radius: 8px;">
                    مخطط بياني هنا
                </div>
            </div>
        </section>

        <section id="settings" class="page-section">
            <h2>الإعدادات</h2>
            <p>قم بتخصيص إعدادات نظامك والتحكم في الخيارات العامة.</p>
            <form>
                <h3>الإعدادات العامة</h3>
                <div class="form-group">
                    <label for="site-name">اسم الموقع/النظام:</label>
                    <input type="text" id="site-name" value="نظام إدارة المحتوى المتقدم" placeholder="اسم موقعك">
                </div>
                <div class="form-group">
                    <label for="currency-select">العملة الافتراضية:</label>
                    <select id="currency-select">
                        <option value="SDG" selected>الجنيه السوداني (ج.س)</option>
                        <option value="USD">الدولار الأمريكي ($)</option>
                        <option value="SAR">الريال السعودي (ر.س)</option>
                        <option value="EGP">الجنيه المصري (ج.م)</option>
                    </select>
                </div>
                <button type="button" class="btn" onclick="saveSettings()">
                    <span class="material-icons-round">save</span> حفظ الإعدادات
                </button>
            </form>

            <h3 style="margin-top: 40px;">إدارة المستخدمين (تحتاج إلى نظام خلفي)</h3>
            <p>هذا القسم يتطلب دمج نظام إدارة مستخدمين من الواجهة الخلفية.</p>
            <button type="button" class="btn btn-secondary" onclick="showAlert('هذه الميزة تتطلب إعدادات إضافية في الواجهة الخلفية.', 'info')">
                <span class="material-icons-round">group_add</span> إدارة الأدوار والصلاحيات
            </button>
        </section>

    </div>

    <div class="alert-container"></div>

    <script>
        // دالة يتم تشغيلها عند تحميل محتوى DOM بالكامل
        document.addEventListener('DOMContentLoaded', () => {
            // تفعيل صفحة لوحة التحكم عند بدء التشغيل
            const initialPage = 'dashboard';
            const initialLink = document.querySelector(`.nav-links a[onclick*="${initialPage}"]`);
            if (initialLink) {
                showPage(initialPage, initialLink);
            }
        });

        /**
         * تخفي جميع أقسام الصفحات وتظهر القسم المحدد فقط.
         * وتنشط رابط التنقل المقابل في الشريط الجانبي.
         * @param {string} pageId - مُعرّف (ID) قسم الصفحة المراد عرضه.
         * @param {HTMLElement} clickedLink - عنصر الرابط الذي تم النقر عليه لتفعيله.
         */
        function showPage(pageId, clickedLink) {
            // إخفاء جميع أقسام الصفحات
            document.querySelectorAll('.page-section').forEach(page => {
                page.classList.remove('active');
            });

            // إلغاء تفعيل جميع روابط الشريط الجانبي
            document.querySelectorAll('.nav-links li a').forEach(link => {
                link.classList.remove('active');
            });

            // إظهار الصفحة المحددة وإضافة فئة 'active' لها
            const activePage = document.getElementById(pageId);
            if (activePage) {
                activePage.classList.add('active');
                // تحديث عنوان الصفحة في الرأس الرئيسي
                document.getElementById('page-title').innerText = activePage.querySelector('h2').innerText;
            }

            // تفعيل الرابط الذي تم النقر عليه في الشريط الجانبي
            if (clickedLink) {
                clickedLink.classList.add('active');
            }
        }

        /**
         * تعرض رسالة تنبيه للمستخدم.
         * @param {string} message - الرسالة المراد عرضها.
         * @param {'success'|'error'|'info'} type - نوع التنبيه (success, error, info).
         * @param {number} duration - مدة عرض التنبيه بالمللي ثانية (افتراضي: 5000ms).
         */
        function showAlert(message, type, duration = 5000) {
            const alertContainer = document.querySelector('.alert-container');
            const alert = document.createElement('div');
            alert.classList.add('alert', type);

            // تحديد الأيقونة بناءً على نوع التنبيه
            let icon = 'info';
            if (type === 'success') {
                icon = 'check_circle';
            } else if (type === 'error') {
                icon = 'error';
            }

            alert.innerHTML = `
                <span class="material-icons-round">${icon}</span>
                <span>${message}</span>
            `;
            alertContainer.appendChild(alert);

            // إزالة التنبيه بعد المدة المحددة
            setTimeout(() => {
                alert.remove();
            }, duration);
        }

        // وظيفة إدارة المنتجات: إضافة منتج جديد
        document.getElementById('product-form').addEventListener('submit', function(event) {
            event.preventDefault(); // منع الإرسال الافتراضي للنموذج

            const productNameInput = document.getElementById('product-name');
            const productPriceInput = document.getElementById('product-price');
            const productDescriptionInput = document.getElementById('product-description');

            const productName = productNameInput.value.trim();
            const productPrice = parseFloat(productPriceInput.value);
            const productDescription = productDescriptionInput.value.trim();

            // التحقق من صحة المدخلات
            if (productName && !isNaN(productPrice) && productPrice >= 0) { // يمكن أن يكون السعر 0
                const productListBody = document.getElementById('product-list').getElementsByTagName('tbody')[0];
                const newRow = productListBody.insertRow(); // إضافة صف جديد إلى الجدول

                newRow.innerHTML = `
                    <td>${productName}</td>
                    <td>${productPrice.toFixed(2)} ج.س</td>
                    <td>${productDescription || 'لا يوجد وصف'}</td>
                    <td>
                        <button class="btn btn-secondary" onclick="editProduct(this)"><span class="material-icons-round">edit</span> تعديل</button>
                        <button class="btn btn-danger" onclick="deleteProduct(this)"><span class="material-icons-round">delete</span> حذف</button>
                    </td>
                `;

                showAlert('تم إضافة المنتج بنجاح!', 'success');
                // مسح حقول النموذج بعد الإضافة
                productNameInput.value = '';
                productPriceInput.value = '';
                productDescriptionInput.value = '';
            } else {
                showAlert('الرجاء إدخال اسم منتج صالح وسعر رقمي غير سالب.', 'error');
            }
        });

        /**
         * تملأ نموذج المنتج ببيانات الصف المحدد للتعديل.
         * @param {HTMLButtonElement} button - زر "تعديل" الذي تم النقر عليه.
         */
        function editProduct(button) {
            const row = button.parentNode.parentNode; // الحصول على الصف الأب للزر
            const cells = row.getElementsByTagName('td'); // الحصول على خلايا الصف

            const productName = cells[0].innerText;
            // إزالة رمز العملة "ج.س" من السعر لتحويله إلى رقم
            const productPrice = parseFloat(cells[1].innerText.replace(' ج.س', ''));
            const productDescription = cells[2].innerText;

            // ملء حقول النموذج بالبيانات الموجودة في الصف
            document.getElementById('product-name').value = productName;
            document.getElementById('product-price').value = productPrice;
            document.getElementById('product-description').value = productDescription === 'لا يوجد وصف' ? '' : productDescription;

            // إزالة الصف بعد التعديل. المستخدم سيعيد إضافته عبر النموذج بعد إجراء التغييرات.
            row.remove();
            showAlert('يمكنك الآن تعديل معلومات المنتج وإعادة إضافته من خلال النموذج أعلاه.', 'info', 7000); // تنبيه أطول
        }

        /**
         * تحذف صف منتج من الجدول.
         * @param {HTMLButtonElement} button - زر "حذف" الذي تم النقر عليه.
         */
        function deleteProduct(button) {
            const row = button.parentNode.parentNode; // الحصول على الصف الأب للزر
            if (confirm('هل أنت متأكد أنك تريد حذف هذا المنتج؟')) { // تأكيد الحذف
                row.remove(); // إزالة الصف
                showAlert('تم حذف المنتج بنجاح!', 'success');
            } else {
                showAlert('تم إلغاء عملية الحذف.', 'info');
            }
        }

        /**
         * وظيفة لحفظ الإعدادات (كمثال).
         */
        function saveSettings() {
            const siteName = document.getElementById('site-name').value;
            const currency = document.getElementById('currency-select').value;
            const displayedCurrencyElement = document.getElementById('displayed-currency');

            // تحديث العملة المعروضة في الرأس
            if (currency === 'SDG') {
                displayedCurrencyElement.innerText = 'ج.س';
            } else if (currency === 'USD') {
                displayedCurrencyElement.innerText = '$';
            } else if (currency === 'SAR') {
                displayedCurrencyElement.innerText = 'ر.س';
            } else if (currency === 'EGP') {
                displayedCurrencyElement.innerText = 'ج.م';
            }

            showAlert(`تم حفظ الإعدادات بنجاح! اسم الموقع: ${siteName}, العملة: ${currency}`, 'success');
            // هنا يمكنك إرسال البيانات إلى الواجهة الخلفية أو تخزينها محلياً
        }
    </script>
</body>
</html>
            }
        }
