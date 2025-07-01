<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>نظام إدارة المحتوى</title>
    <link href="https://fonts.googleapis.com/icon?family=Material+Icons" rel="stylesheet">
    <style>
        /* استيراد خط Cairo من Google Fonts */
        @import url('https://fonts.googleapis.com/css2?family=Cairo:wght@400;700&display=swap');

        /* الأنماط العامة للجسم */
        body {
            font-family: 'Cairo', sans-serif;
            margin: 0;
            background-color: #f4f7f6;
            color: #333;
            display: flex;
            min-height: 100vh;
        }

        /* أنماط الشريط الجانبي */
        .sidebar {
            width: 250px;
            background-color: #2c3e50; /* لون خلفية داكن */
            color: #ecf0f1; /* لون النص فاتح */
            padding-top: 20px;
            box-shadow: 2px 0 5px rgba(0, 0, 0, 0.1);
            display: flex;
            flex-direction: column;
            align-items: center;
        }

        .sidebar h2 {
            color: #ecf0f1;
            text-align: center;
            margin-bottom: 30px;
            font-size: 1.8em;
        }

        .sidebar ul {
            list-style: none;
            padding: 0;
            width: 100%;
        }

        .sidebar ul li {
            width: 100%;
        }

        .sidebar ul li a {
            display: flex;
            align-items: center;
            padding: 15px 20px;
            color: #ecf0f1;
            text-decoration: none;
            transition: background-color 0.3s, color 0.3s;
            font-size: 1.1em;
        }

        .sidebar ul li a .material-icons {
            margin-left: 10px; /* مسافة بين الأيقونة والنص */
            font-size: 24px;
        }

        .sidebar ul li a:hover,
        .sidebar ul li a.active {
            background-color: #34495e; /* لون خلفية أغمق عند التحويم/النشاط */
            color: #2ecc71; /* لون أخضر جذاب للنص عند التحويم/النشاط */
        }

        /* أنماط المحتوى الرئيسي */
        .main-content {
            flex-grow: 1; /* يجعل المحتوى يملأ المساحة المتبقية */
            padding: 20px;
            background-color: #ecf0f1; /* لون خلفية فاتح للمحتوى */
        }

        /* أنماط رأس الصفحة */
        header {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
            margin-bottom: 20px;
            display: flex;
            justify-content: space-between; /* يباعد بين العنوان والعملة */
            align-items: center;
        }

        header h1 {
            margin: 0;
            color: #2c3e50;
        }

        .currency-display {
            font-size: 1.2em;
            font-weight: bold;
            color: #2ecc71;
        }
        /* أنماط أقسام الصفحات (التبويبات) */
        .page-section {
            background-color: #ffffff;
            padding: 20px;
            border-radius: 8px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.05);
            margin-bottom: 20px;
            display: none; /* مخفية افتراضياً */
        }

        .page-section.active {
            display: block; /* تظهر عندما تكون نشطة */
        }

        /* أنماط مجموعات النماذج */
        .form-group {
            margin-bottom: 15px;
        }

        .form-group label {
            display: block;
            margin-bottom: 5px;
            font-weight: bold;
            color: #555;
        }

        .form-group input[type="text"],
        .form-group input[type="number"],
        .form-group textarea,
        .form-group select { /* إضافة select لأنماط حقول الإدخال */
            width: calc(100% - 22px); /* لتأخذ العرض الكامل مع مراعاة البادينج */
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 5px;
            font-size: 1em;
            box-sizing: border-box; /* لضمان أن البادينج لا يزيد العرض الكلي */
        }

        .form-group textarea {
            resize: vertical; /* السماح بتغيير الحجم عمودياً فقط */
            min-height: 100px;
        }

        /* أنماط الأزرار */
        .btn {
            background-color: #2ecc71; /* لون أخضر */
            color: white;
            padding: 10px 20px;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 1em;
            transition: background-color 0.3s ease;
        }

        .btn:hover {
            background-color: #27ae60; /* لون أخضر أغمق عند التحويم */
        }

        /* أنماط حاوية التنبيهات */
        .alert-container {
            position: fixed; /* لتثبيت التنبيهات على الشاشة */
            top: 20px;
            right: 20px;
            z-index: 1000; /* لضمان ظهورها فوق العناصر الأخرى */
        }

        /* أنماط التنبيهات الفردية */
        .alert {
            display: flex;
            align-items: center;
            background-color: #fff;
            padding: 10px 20px;
            border-radius: 5px;
            box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
            margin-bottom: 10px;
            opacity: 0; /* مخفية في البداية لتظهر بالانيميشن */
            animation: fadeIn 0.5s forwards; /* انيميشن الظهور */
        }

        .alert.success {
            border-right: 5px solid #28a745; /* شريط أخضر للنجاح */
        }

        .alert.error {
            border-right: 5px solid #dc3545; /* شريط أحمر للخطأ */
        }

        .alert.info { /* أنماط جديدة لتنبيهات المعلومات */
            border-right: 5px solid #007bff; /* شريط أزرق للمعلومات */
        }

        .alert .material-icons {
            margin-right: 10px;
            font-size: 24px;
        }

        .alert.success .material-icons {
            color: #28a745;
        }

        .alert.error .material-icons {
            color: #dc3545;
        }

        .alert.info .material-icons { /* لون أيقونة المعلومات */
            color: #007bff;
        }

        /* انيميشن الظهور */
        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(-20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* أنماط الجداول */
        table {
            width: 100%;
            border-collapse: collapse; /* لإزالة المسافات بين حدود الخلايا */
            margin-top: 20px;
        }

        table th, table td {
            border: 1px solid #ddd;
            padding: 10px;
            text-align: right; /* محاذاة النص لليمين */
        }

        table th {
            background-color: #f2f2f2;
            font-weight: bold;
        }

        /* تصميم متجاوب (Responsive Design) */
        @media (max-width: 768px) {
            body {
                flex-direction: column; /* جعل الشريط الجانبي والمحتوى فوق بعضهما */
            }

            .sidebar {
                width: 100%;
                height: auto;
                padding-top: 10px;
            }

            .sidebar ul {
                flex-direction: row; /* جعل عناصر القائمة أفقية */
                justify-content: space-around;
                flex-wrap: wrap; /* السماح للعناصر بالالتفاف لأسفل على الشاشات الأصغر */
            }

            .sidebar ul li {
                width: auto;
            }

            .sidebar ul li a {
                padding: 10px;
                font-size: 0.9em;
            }

            .sidebar ul li a .material-icons {
                margin-left: 5px;
            }

            .main-content {
                padding: 10px;
            }

            header {
                flex-direction: column; /* جعل العنوان والعملة فوق بعضهما */
                align-items: flex-start;
            }

            .currency-display {
                margin-top: 10px;
            }
        }
    </style>
</head>
<body>
<div class="sidebar">
        <h2>لوحة التحكم</h2>
        <ul>
            <li><a href="#" onclick="showPage('dashboard')"><span class="material-icons">dashboard</span>الرئيسية</a></li>
            <li><a href="#" onclick="showPage('products')"><span class="material-icons">inventory_2</span>المنتجات</a></li>
            <li><a href="#" onclick="showPage('orders')"><span class="material-icons">shopping_cart</span>الطلبات</a></li>
            <li><a href="#" onclick="showPage('customers')"><span class="material-icons">people</span>العملاء</a></li>
            <li><a href="#" onclick="showPage('reports')"><span class="material-icons">analytics</span>التقارير</a></li>
            <li><a href="#" onclick="showPage('settings')"><span class="material-icons">settings</span>الإعدادات</a></li>
        </ul>
    </div>

    <div class="main-content">
        <header>
            <h1>الرئيسية</h1>
            <div class="currency-display">العملة الحالية: ج.س</div>
        </header>

        <section id="dashboard" class="page-section active">
            <h2>نظرة عامة على لوحة التحكم</h2>
            <p>مرحباً بك في لوحة التحكم الخاصة بك. يمكنك هنا إدارة منتجاتك، طلباتك، وعملائك.</p>
            <div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 20px; margin-top: 20px;">
                <div class="page-section" style="display: block;">
                    <h3>المنتجات الإجمالية</h3>
                    <p style="font-size: 2em; font-weight: bold; color: #3498db;">150</p>
                </div>
                <div class="page-section" style="display: block;">
                    <h3>الطلبات الجديدة</h3>
                    <p style="font-size: 2em; font-weight: bold; color: #e67e22;">25</p>
                </div>
                <div class="page-section" style="display: block;">
                    <h3>إجمالي المبيعات</h3>
                    <p style="font-size: 2em; font-weight: bold; color: #2ecc71;">50,000 ج.س</p>
                </div>
            </div>
        </section>

        <section id="products" class="page-section">
            <h2>إدارة المنتجات</h2>
            <form id="product-form">
                <div class="form-group">
                    <label for="product-name">اسم المنتج:</label>
                    <input type="text" id="product-name" required>
                </div>
                <div class="form-group">
                    <label for="product-price">السعر (ج.س):</label>
                    <input type="number" id="product-price" step="0.01" required>
                </div>
                <div class="form-group">
                    <label for="product-description">الوصف:</label>
                    <textarea id="product-description"></textarea>
                </div>
                <button type="submit" class="btn">إضافة منتج</button>
            </form>

            <h3>قائمة المنتجات</h3>
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
                    </tbody>
            </table>
        </section>

        <section id="orders" class="page-section">
            <h2>إدارة الطلبات</h2>
            <p>هنا يمكنك عرض وإدارة الطلبات المستلمة.</p>
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
                        <td>#001</td>
                        <td>أحمد علي</td>
                        <td>2025-06-25</td>
                        <td>1200 ج.س</td>
                        <td>قيد التنفيذ</td>
                        <td><button class="btn" style="background-color: #f39c12;">تعديل</button></td>
                    </tr>
                    <tr>
                        <td>#002</td>
                        <td>فاطمة محمد</td>
                        <td>2025-06-24</td>
                        <td>850 ج.س</td>
                        <td>تم التوصيل</td>
                        <td><button class="btn" style="background-color: #28a745;">عرض</button></td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section id="customers" class="page-section">
            <h2>إدارة العملاء</h2>
            <p>هنا يمكنك عرض معلومات العملاء وإدارتها.</p>
            <table id="customer-list">
                <thead>
                    <tr>
                        <th>الاسم</th>
                        <th>البريد الإلكتروني</th>
                        <th>رقم الهاتف</th>
                        <th>تاريخ التسجيل</th>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <td>أحمد علي</td>
                        <td>ahmed.ali@example.com</td>
                        <td>+249912345678</td>
                        <td>2024-01-15</td>
                    </tr>
                    <tr>
                        <td>فاطمة محمد</td>
                        <td>fatima.mohamed@example.com</td>
                        <td>+249912345679</td>
                        <td>2024-02-20</td>
                    </tr>
                </tbody>
            </table>
        </section>

        <section id="reports" class="page-section">
            <h2>التقارير والتحليلات</h2>
            <p>عرض تقارير المبيعات، المنتجات الأكثر مبيعاً، وغيرها من التحليلات الهامة.</p>
            <div class="page-section" style="display: block;">
                <h3>تقرير المبيعات الشهرية</h3>
                <p>إجمالي المبيعات لشهر يونيو: 15,000 ج.س</p>
                <div style="background-color: #eee; height: 200px; display: flex; align-items: center; justify-content: center; color: #777; border-radius: 5px;">
                    (مخطط بياني للمبيعات هنا)
                </div>
            </div>
        </section>

        <section id="settings" class="page-section">
            <h2>الإعدادات</h2>
            <p>تغيير إعدادات النظام، العملة، وغيرها.</p>
            <form>
                <div class="form-group">
                    <label for="site-name">اسم الموقع:</label>
                    <input type="text" id="site-name" value="نظام إدارة المحتوى">
                </div>
                <div class="form-group">
                    <label for="currency-select">العملة الافتراضية:</label>
                    <select id="currency-select">
                        <option value="SDG" selected>الجنيه السوداني (ج.س)</option>
                        <option value="USD">الدولار الأمريكي ($)</option>
                        <option value="SAR">الريال السعودي (ر.س)</option>
                    </select>
                </div>
                <button type="button" class="btn" onclick="showAlert('تم حفظ الإعدادات بنجاح!', 'success')">حفظ الإعدادات</button>
            </form>
        </section>

    </div>

    <div class="alert-container"></div>

    <script>
        // عند تحميل الصفحة بالكامل، يتم تفعيل لوحة التحكم كصفحة افتراضية
        document.addEventListener('DOMContentLoaded', () => {
            const initialPage = 'dashboard';
            showPage(initialPage);
        });

        /**
         * تخفي جميع أقسام الصفحات وتظهر القسم المحدد فقط.
         * وتقوم بتفعيل رابط الشريط الجانبي المقابل.
         * @param {string} pageId - معرف قسم الصفحة (ID) الذي سيتم عرضه.
         */
        function showPage(pageId) {
            // إخفاء جميع أقسام الصفحات
            document.querySelectorAll('.page-section').forEach(page => {
                page.classList.remove('active');
            });

            // إلغاء تفعيل جميع روابط الشريط الجانبي
            document.querySelectorAll('.sidebar ul li a').forEach(link => {
                link.classList.remove('active');
            });

            // إظهار الصفحة المحددة
            const activePage = document.getElementById(pageId);
            if (activePage) {
                activePage.classList.add('active');
                // تحديث عنوان الرأس بناءً على عنوان الصفحة النشطة (h2)
                const pageTitleElement = activePage.querySelector('h2');
                if (pageTitleElement) {
                    document.querySelector('header h1').innerText = pageTitleElement.innerText;
                }
            }

            // تفعيل رابط الشريط الجانبي المقابل
            const activeLink = document.querySelector(`.sidebar ul li a[onclick*="${pageId}"]`);
            if (activeLink) {
                activeLink.classList.add('active');
            }
        }

        /**
         * تعرض رسالة تنبيه للمستخدم.
         * @param {string} message - الرسالة المراد عرضها.
         * @param {'success'|'error'|'info'} type - نوع التنبيه (success للنجاح، error للخطأ، info للمعلومات).
         */
        function showAlert(message, type) {
            const alertContainer = document.querySelector('.alert-container');
            const alert = document.createElement('div');
            alert.classList.add('alert', type);
            // تحديد الأيقونة بناءً على نوع التنبيه
            const icon = type === 'error' ? 'error' : (type === 'info' ? 'info' : 'check_circle');
            alert.innerHTML = `
                <span class="material-icons">${icon}</span>
                ${message}
            `;
            alertContainer.appendChild(alert);

            // إزالة التنبيه بعد 5 ثوانٍ
            setTimeout(() => {
                alert.remove();
            }, 5000);
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
            if (productName && !isNaN(productPrice) && productPrice > 0) {
                const productList = document.getElementById('product-list').getElementsByTagName('tbody')[0];
                const newRow = productList.insertRow(); // إضافة صف جديد إلى الجدول

                newRow.innerHTML = `
                    <td>${productName}</td>
                    <td>${productPrice.toFixed(2)} ج.س</td>
                    <td>${productDescription || 'لا يوجد وصف'}</td>
                    <td>
                        <button class="btn" style="background-color: #3498db;" onclick="editProduct(this)">تعديل</button>
                        <button class="btn" style="background-color: #e74c3c;" onclick="deleteProduct(this)">حذف</button>
                    </td>
                `;

                showAlert('تم إضافة المنتج بنجاح!', 'success');
                // مسح حقول النموذج بعد الإضافة
                productNameInput.value = '';
                productPriceInput.value = '';
                productDescriptionInput.value = '';
            } else {
                showAlert('الرجاء إدخال اسم منتج صالح وسعر أكبر من صفر.', 'error');
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
            const productPrice = parseFloat(cells[1].innerText.replace(' ج.س', '')); // إزالة رمز العملة لتحويله إلى رقم
            const productDescription = cells[2].innerText;

            // ملء حقول النموذج بالبيانات الموجودة في الصف
            document.getElementById('product-name').value = productName;
            document.getElementById('product-price').value = productPrice;
            document.getElementById('product-description').value = productDescription === 'لا يوجد وصف' ? '' : productDescription;

            // إزالة الصف بعد التعديل (المستخدم سيعيد إضافته عبر النموذج بعد إجراء التغييرات)
            row.remove();
            showAlert('يمكنك الآن تعديل معلومات المنتج وإعادة إضافته من خلال النموذج أعلاه.', 'info');
        }

        /**
         * تحذف صف منتج من الجدول.
         * @param {HTMLButtonElement} button - زر "حذف" الذي تم النقر عليه.
         */
        function deleteProduct(button) {
            const row = button.parentNode.parentNode; // الحصول على الصف الأب للزر
            row.remove(); // إزالة الصف
            showAlert('تم حذف المنتج بنجاح!', 'success');
        }
    </script>
</body>
</html>
