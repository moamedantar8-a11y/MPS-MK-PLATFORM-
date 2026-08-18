<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MPS Platform | منصة إدارة الطلاب</title>
    <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700;900&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        :root {
            --primary-blue: #1e40af;
            --secondary-blue: #3b82f6;
            --light-bg: #f8fafc;
            --card-bg: #ffffff;
            --text-main: #1e293b;
            --text-muted: #64748b;
            --accent-green: #10b981;
            --accent-red: #ef4444;
            --transition: all 0.3s ease;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Tajawal', sans-serif;
        }

        body {
            background: linear-gradient(135deg, #1e3a8a 0%, #3b82f6 100%);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 15px;
        }

        /* إطار التلفون الأساسي */
        .phone-frame {
            width: 100%;
            max-width: 410px;
            height: 85vh;
            max-height: 820px;
            background: var(--light-bg);
            border-radius: 35px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.5);
            display: flex;
            flex-direction: column;
            overflow: hidden;
            position: relative;
            border: 8px solid #0f172a;
        }

        .screen {
            display: none;
            flex: 1;
            flex-direction: column;
            overflow-y: auto;
            background: var(--light-bg);
        }

        .screen.active {
            display: flex;
        }

        /* الشاشة الأولى: الترحيب والحسابات */
        .welcome-screen {
            background: linear-gradient(180deg, #1e3a8a 0%, #1e40af 100%);
            color: white;
            padding: 25px;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        .welcome-logo {
            font-size: 60px;
            color: #60a5fa;
            margin-bottom: 10px;
        }

        .accounts-list {
            width: 100%;
            margin: 15px 0;
            max-height: 180px;
            overflow-y: auto;
        }

        .account-card-saved {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            padding: 10px 14px;
            border-radius: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 8px;
            cursor: pointer;
            transition: var(--transition);
        }

        .account-card-saved:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        /* شاشة تسجيل حساب جديد */
        .register-screen {
            background: linear-gradient(180deg, #1e3a8a 0%, #1e40af 100%);
            color: white;
            padding: 25px;
            justify-content: center;
            align-items: center;
        }

        .form-group {
            width: 100%;
            margin-bottom: 10px;
            text-align: right;
        }

        .form-group label {
            font-size: 11px;
            color: #cbd5e1;
            display: block;
            margin-bottom: 3px;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 10px;
            border-radius: 10px;
            border: 1px solid rgba(255,255,255,0.2);
            background: rgba(255,255,255,0.08);
            color: white;
            font-size: 13px;
            outline: none;
        }

        .btn-main {
            width: 100%;
            background: var(--secondary-blue);
            color: white;
            border: none;
            padding: 12px;
            border-radius: 12px;
            font-size: 14px;
            font-weight: 700;
            cursor: pointer;
            box-shadow: 0 4px 12px rgba(59, 130, 246,.4);
            margin-top: 5px;
            transition: var(--transition);
        }

        .btn-main:hover {
            background: #2563eb;
        }

        .btn-secondary {
            background: transparent;
            color: #cbd5e1;
            border: 1px solid rgba(255,255,255,0.2);
            margin-top: 8px;
        }

        /* الشريط العلوي داخل التلفون */
        .top-navbar {
            background: white;
            padding: 10px 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 4px rgba(0,0,0,0.03);
            position: sticky;
            top: 0;
            z-index: 10;
        }

        .nav-brand {
            display: flex;
            align-items: center;
            gap: 6px;
            font-size: 14px;
            font-weight: 900;
            color: var(--primary-blue);
        }

        .nav-links {
            display: flex;
            gap: 4px;
        }

        .nav-btn {
            background: #f1f5f9;
            border: none;
            padding: 6px 10px;
            border-radius: 6px;
            font-size: 11px;
            font-weight: 600;
            color: var(--text-muted);
            cursor: pointer;
            transition: var(--transition);
        }

        .nav-btn.active, .nav-btn:hover {
            background: var(--secondary-blue);
            color: white;
        }

        /* محتوى الداشبورد */
        .dashboard-content {
            padding: 15px;
        }

        .profile-header-card {
            background: linear-gradient(135deg, var(--secondary-blue), var(--primary-blue));
            color: white;
            padding: 15px;
            border-radius: 14px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
        }

        .info-card-item {
            background: white;
            padding: 12px 15px;
            border-radius: 10px;
            margin-bottom: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid #e2e8f0;
            font-size: 13px;
        }

        .info-card-item .label-side {
            display: flex;
            align-items: center;
            gap: 10px;
            color: var(--text-muted);
        }

        .info-card-item .value-side {
            font-weight: 700;
            color: var(--text-main);
        }

        .info-card-item i {
            color: var(--secondary-blue);
        }

        /* شبكة أزرار المتابعة */
        .dashboard-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 10px;
            margin-bottom: 15px;
        }

        .dash-card {
            background: white;
            padding: 12px;
            border-radius: 12px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            border: 1px solid #e2e8f0;
            cursor: pointer;
            transition: var(--transition);
            min-height: 90px;
        }

        .dash-card:hover {
            border-color: var(--secondary-blue);
            transform: translateY(-2px);
        }

        .dash-card-icon {
            width: 32px;
            height: 32px;
            background: #eff6ff;
            color: var(--secondary-blue);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 14px;
            margin-bottom: 6px;
        }

        .dash-card-title {
            font-size: 12px;
            font-weight: 700;
            color: var(--text-main);
        }

        .dash-card-value {
            font-size: 11px;
            color: var(--text-muted);
            font-weight: bold;
            margin-top: 4px;
        }

        /* الإضافات الجديدة لملء الفراغات */
        .extra-section {
            background: white;
            border-radius: 12px;
            padding: 12px 15px;
            margin-bottom: 10px;
            border: 1px solid #e2e8f0;
        }

        .extra-section h5 {
            font-size: 13px;
            color: var(--primary-blue);
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .schedule-row {
            display: flex;
            justify-content: space-between;
            font-size: 11px;
            padding: 5px 0;
            border-bottom: 1px dashed #f1f5f9;
        }

        /* النافذة المنبثقة */
        .modal-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.6);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 100;
            padding: 15px;
        }

        .modal-card {
            background: white;
            width: 100%;
            max-width: 330px;
            border-radius: 16px;
            padding: 20px;
            box-shadow: 0 20px 25px -5px rgba(0,0,0,0.2);
            text-align: right;
        }

        .admin-controls {
            background: #eff6ff;
            border: 1px dashed var(--secondary-blue);
            padding: 10px;
            border-radius: 8px;
            margin-top: 12px;
            display: none;
        }

        .admin-controls.active {
            display: block;
        }

        .app-footer {
            text-align: center;
            padding: 10px;
            font-size: 10px;
            color: var(--text-muted);
            background: white;
            border-top: 1px solid #f1f5f9;
            margin-top: auto;
        }
    </style>
</head>
<body>

    <div class="phone-frame">
        
        <!-- 1. شاشة الترحيب -->
        <div id="screen-welcome" class="screen welcome-screen active">
            <div class="welcome-logo"><i class="fa-solid fa-graduation-cap"></i></div>
            <h1 style="font-size: 22px; font-weight: 900; margin-bottom: 3px;">MPS Platform</h1>
            <p style="font-size: 12px; color: #94a3b8; margin-bottom: 15px;">بوابة متابعة الطالب والمعلم</p>

            <div style="width: 100%; text-align: right; font-size: 12px; font-weight: bold; margin-bottom: 4px;">الحسابات المسجلة:</div>
            <div class="accounts-list" id="savedAccountsContainer"></div>

            <div style="width: 100%;">
                <button class="btn-main" onclick="showScreen('screen-register')">تسجيل حساب طالب جديد</button>
                <button class="btn-main" style="background: #0f172a;" onclick="showAdminLogin()">دخول المعلم (ادمن)</button>
            </div>
        </div>

        <!-- 2. شاشة تسجيل طالب -->
        <div id="screen-register" class="screen register-screen">
            <h2 style="font-size: 20px; font-weight: 900; text-align: center; margin-bottom: 3px;">حساب طالب جديد</h2>
            <p style="font-size: 11px; color: #cbd5e1; text-align: center; margin-bottom: 15px;">أدخل بياناتك للانضمام للمنصة</p>

            <div class="form-group">
                <label>اسم الطالب الكامل</label>
                <input type="text" id="regStudentName" placeholder="مثال: محمد عنتر">
            </div>

            <div class="form-group">
                <label>اسم المدرس</label>
                <input type="text" id="regTeacherName" value="جلال الاتربي" placeholder="اسم المدرس">
            </div>

            <div class="form-group">
                <label>رقم ولي الأمر</label>
                <input type="text" id="regParentPhone" placeholder="010xxxxxxxx">
            </div>

            <div class="form-group">
                <label>الصف الدراسي</label>
                <select id="regGrade">
                    <option value="الصف الاول الثانوي">الصف الاول الثانوي</option>
                    <option value="الصف الثاني الثانوي">الصف الثاني الثانوي</option>
                    <option value="الصف الثالث الثانوي">الصف الثالث الثانوي</option>
                </select>
            </div>

            <div class="form-group">
                <label>المجموعة</label>
                <input type="text" id="regGroup" value="المجموعة العامة" placeholder="المجموعة">
            </div>

            <button class="btn-main" onclick="registerNewStudent()">حفظ ودخول</button>
            <button class="btn-main btn-secondary" onclick="showScreen('screen-welcome')">رجوع</button>
        </div>

        <!-- 3. لوحة تحكم المنصة -->
        <div id="screen-dashboard" class="screen">
            
            <div class="top-navbar">
                <div class="nav-brand">
                    <i class="fa-solid fa-layer-group"></i>
                    <span>MPS</span>
                </div>
                <div class="nav-links">
                    <button class="nav-btn active" onclick="switchSection('profile')">الملف</button>
                    <button class="nav-btn" onclick="switchSection('stats')">المتابعة</button>
                    <button class="nav-btn" id="adminBadgeBtn" style="background: #fef08a; color: #854d0e; display: none;"><i class="fa-solid fa-shield"></i> أدمن</button>
                    <button class="nav-btn" onclick="showScreen('screen-welcome')" style="color: var(--accent-green);"><i class="fa-solid fa-users"></i> الخروج</button>
                </div>
            </div>

            <div class="dashboard-content">
                
                <!-- قسم الملف الشخصي -->
                <div id="section-profile">
                    <div class="profile-header-card">
                        <div>
                            <h3 id="uiStudentName" style="font-size: 16px; font-weight: 900;">محمد عنتر</h3>
                            <span style="font-size: 11px; opacity: 0.9;">الكود التعريفي: <span id="uiId">3034</span></span>
                        </div>
                        <i class="fa-solid fa-graduation-cap" style="font-size: 28px;"></i>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-user-tie"></i><span>المدرس</span></div>
                        <div class="value-side" id="uiTeacher">جلال الاتربي</div>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-phone"></i><span>هاتف ولي الأمر</span></div>
                        <div class="value-side" id="uiPhone">غير متوفر</div>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-users-rectangle"></i><span>الصف الدراسي</span></div>
                        <div class="value-side" id="uiGrade">الصف الاول الثانوي</div>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-calendar-days"></i><span>المجموعة</span></div>
                        <div class="value-side" id="uiGroup">المجموعة العامة</div>
                    </div>
                </div>

                <!-- قسم المتابعة والأزرار التفاعلية + إضافات لملء الفراغات -->
                <div id="section-stats" style="display: none;">
                    <h4 style="font-size: 14px; font-weight: 900; color: var(--primary-blue); margin-bottom: 10px;">لوحة المتابعة الشاملة</h4>
                    
                    <div class="dashboard-grid">
                        <div class="dash-card" onclick="openModal('notifications')">
                            <div class="dash-card-icon"><i class="fa-solid fa-bell"></i></div>
                            <div class="dash-card-title">الإشعارات</div>
                            <div class="dash-card-value">لا توجد تنبيهات</div>
                        </div>

                        <div class="dash-card" onclick="openModal('attendance')">
                            <div class="dash-card-icon"><i class="fa-solid fa-calendar-check"></i></div>
                            <div class="dash-card-title">مرات الحضور</div>
                            <div class="dash-card-value" id="attCount" style="color: var(--accent-green);">لم يُسجل</div>
                        </div>

                        <div class="dash-card" onclick="openModal('absence')">
                            <div class="dash-card-icon" style="background: #fee2e2; color: var(--accent-red);"><i class="fa-solid fa-calendar-xmark"></i></div>
                            <div class="dash-card-title">مرات الغياب</div>
                            <div class="dash-card-value" id="absCount" style="color: var(--accent-red);">لم يُسجل</div>
                        </div>

                        <div class="dash-card" onclick="openModal('payments')">
                            <div class="dash-card-icon"><i class="fa-solid fa-wallet"></i></div>
                            <div class="dash-card-title">المدفوعات</div>
                            <div class="dash-card-value" id="payStatus">لم يتم الدفع</div>
                        </div>

                        <div class="dash-card" onclick="openModal('exams')">
                            <div class="dash-card-icon"><i class="fa-solid fa-chart-line"></i></div>
                            <div class="dash-card-title">الدرجات والتقييم</div>
                            <div class="dash-card-value" id="scoreStatus">قيد الانتظار</div>
                        </div>

                        <div class="dash-card" onclick="openModal('notes')">
                            <div class="dash-card-icon"><i class="fa-solid fa-note-sticky"></i></div>
                            <div class="dash-card-title">ملاحظات المستر</div>
                            <div class="dash-card-value">لا توجد ملاحظات</div>
                        </div>
                    </div>

                    <!-- إضافات جديدة لملء الفراغات السفلية -->
                    <div class="extra-section">
                        <h5><i class="fa-solid fa-calendar-week"></i> جدول مواعيد الحصص</h5>
                        <div class="schedule-row"><span>السبت والثلاثاء</span> <span>3:00 عصراً</span></div>
                        <div class="schedule-row"><span>الخميس (اختباري)</span> <span>5:00 مساءً</span></div>
                    </div>

                    <div class="extra-section">
                        <h5><i class="fa-solid fa-circle-info"></i> حالة النظام والتحديثات</h5>
                        <div class="schedule-row"><span>إصدار المنصة</span> <span>v2.5 (مؤمن بالكامل)</span></div>
                        <div class="schedule-row"><span>حالة الحساب</span> <span style="color: var(--accent-green);">نشط وآمن</span></div>
                    </div>
                </div>

            </div>

            <div class="app-footer">
                Developed by <span>MK CREATIVE Agency</span>
            </div>
        </div>

    </div>

    <!-- نافذة العرض المنبثقة -->
    <div class="modal-overlay" id="customModal" onclick="closeModal(event)">
        <div class="modal-card" onclick="event.stopPropagation()">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; border-bottom: 1px solid #f1f5f9; padding-bottom: 6px;">
                <h3 id="modalTitle" style="font-size: 14px; font-weight: 900; color: var(--primary-blue);">عنوان</h3>
                <i class="fa-solid fa-xmark" style="cursor: pointer; font-size: 16px; color: var(--text-muted);" onclick="closeModalDirect()"></i>
            </div>
            <div style="font-size: 12px; color: var(--text-muted); line-height: 1.5; margin-bottom: 12px;" id="modalBodyContent"></div>
            
            <div class="admin-controls" id="adminControlPanel">
                <p style="font-size: 11px; font-weight: bold; color: var(--primary-blue); margin-bottom: 6px;"><i class="fa-solid fa-lock-open"></i> لوحة تحكم المستر (كود 2026):</p>
                <div id="adminActionButtons"></div>
            </div>
        </div>
    </div>

    <script>
        let isAdmin = false;
        let currentStudentIndex = 0;

        let savedAccounts = JSON.parse(localStorage.getItem('mps_all_students')) || [
            { id: 3034, name: "محمد عنتر", teacher: "جلال الاتربي", phone: "غير متوفر", grade: "الصف الاول الثانوي", group: "المجموعة العامة", attendance: "لم يُسجل", absence: "لم يُسجل", payment: "لم يتم الدفع", notes: "لم تُسجل ملاحظات بعد", score: "لم تُسجل بعد" }
        ];

        function renderSavedAccounts() {
            const container = document.getElementById('savedAccountsContainer');
            container.innerHTML = '';
            
            if(savedAccounts.length === 0) {
                container.innerHTML = '<p style="font-size: 11px; color: #cbd5e1;">لا توجد حسابات مسجلة.</p>';
                return;
            }

            savedAccounts.forEach((acc, index) => {
                container.innerHTML += `
                    <div class="account-card-saved" onclick="loginStudent(${index})">
                        <div style="text-align: right;">
                            <h4 style="font-size: 13px; font-weight: bold;">${acc.name}</h4>
                            <span style="font-size: 10px; color: #94a3b8;">${acc.grade} (كود: ${acc.id})</span>
                        </div>
                        <i class="fa-solid fa-chevron-left" style="font-size: 11px; color: #60a5fa;"></i>
                    </div>
                `;
            });
        }

        function showScreen(screenId) {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById(screenId).classList.add('active');
            if(screenId === 'screen-welcome') {
                renderSavedAccounts();
                isAdmin = false;
                document.getElementById('adminBadgeBtn').style.display = 'none';
            }
        }

        function showAdminLogin() {
            let pass = prompt("أدخل كود الأدمن السري (المستر):");
            if(pass === "2026") {
                isAdmin = true;
                alert("تم تفعيل صلاحيات الأدمن (المستر) بنجاح!");
                if(savedAccounts.length > 0) {
                    loginStudent(0);
                } else {
                    showScreen('screen-register');
                }
            } else if(pass !== null) {
                alert("الكود غير صحيح!");
            }
        }

        function registerNewStudent() {
            let name = document.getElementById('regStudentName').value.trim();
            let teacher = document.getElementById('regTeacherName').value.trim();
            let phone = document.getElementById('regParentPhone').value.trim();
            let grade = document.getElementById('regGrade').value;
            let group = document.getElementById('regGroup').value.trim();

            if(!name) {
                alert("يرجى إدخال اسم الطالب!");
                return;
            }

            let newAcc = {
                id: Math.floor(1000 + Math.random() * 9000),
                name: name,
                teacher: teacher || "جلال الاتربي",
                phone: phone || "غير متوفر",
                grade: grade,
                group: group || "المجموعة العامة",
                attendance: "لم يُسجل",
                absence: "لم يُسجل",
                payment: "لم يتم الدفع",
                notes: "لم تُسجل ملاحظات بعد",
                score: "لم تُسجل بعد"
            };

            savedAccounts.push(newAcc);
            localStorage.setItem('mps_all_students', JSON.stringify(savedAccounts));
            loginStudent(savedAccounts.length - 1);
        }

        function loginStudent(index) {
            currentStudentIndex = index;
            let acc = savedAccounts[index];

            document.getElementById('uiStudentName').innerText = acc.name;
            document.getElementById('uiId').innerText = acc.id;
            document.getElementById('uiTeacher').innerText = acc.teacher;
            document.getElementById('uiPhone').innerText = acc.phone;
            document.getElementById('uiGrade').innerText = acc.grade;
            document.getElementById('uiGroup').innerText = acc.group;

            document.getElementById('attCount').innerText = acc.attendance;
            document.getElementById('absCount').innerText = acc.absence;
            document.getElementById('payStatus').innerText = acc.payment;
            document.getElementById('scoreStatus').innerText = acc.score;

            if(isAdmin) {
                document.getElementById('adminBadgeBtn').style.display = 'block';
            }

            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById('screen-dashboard').classList.add('active');
            switchSection('profile');
        }

        function switchSection(sectionName) {
            document.querySelectorAll('.nav-btn').forEach(btn => {
                if(btn.id !== 'adminBadgeBtn') btn.classList.remove('active');
            });
            event.target.classList.add('active');

            if(sectionName === 'profile') {
                document.getElementById('section-profile').style.display = 'block';
                document.getElementById('section-stats').style.display = 'none';
            } else {
                document.getElementById('section-profile').style.display = 'none';
                document.getElementById('section-stats').style.display = 'block';
            }
        }

        function openModal(type) {
            let student = savedAccounts[currentStudentIndex];
            let title = "";
            let body = "";
            let adminActions = "";

            if(type === 'notifications') {
                title = "الإشعارات والتنبيهات";
                body = `• لا توجد إشعارات جديدة حالياً.<br>• تابع هذه النافذة باستمرار لمعرفة تعليمات المستر.`;
            } else if(type === 'attendance') {
                title = "سجل الحضور";
                body = `حالة الحضور المسجلة: <strong>${student.attendance}</strong>.<br><em>(لا يمكن تعديلها إلا من خلال لوحة تحكم المستر بالكود السري).</em>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 6px; font-size: 11px;" onclick="updateData('attendance', 'حاضر (تم التسجيل)')">تسجيل حضور (حاضر)</button>`;
                }
            } else if(type === 'absence') {
                title = "سجل الغياب";
                body = `حالة الغياب المسجلة: <strong>${student.absence}</strong>.<br><em>(خاص بالمستر فقط).</em>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 6px; font-size: 11px; background: var(--accent-red);" onclick="updateData('absence', 'غائب بدون عذر')">تسجيل غياب</button>`;
                }
            } else if(type === 'payments') {
                title = "المدفوعات والاشتراكات";
                body = `حالة الاشتراك الحالي: <span style="color: var(--secondary-blue); font-weight: bold;">${student.payment}</span>.`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 6px; font-size: 11px;" onclick="updateData('payment', 'تم السداد (مدفوع)')">تعديل إلى (تم السداد)</button>`;
                }
            } else if(type === 'exams') {
                title = "الدرجات والتقييم الشهري واليومي";
                body = `التقييم الحالي: <strong>${student.score}</strong>.<br><em>(المستر وحده هو من يضع الدرجة الحقيقية).</em>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 6px; font-size: 11px;" onclick="updateData('score', 'ممتاز (10/10)')">تعيين الدرجة (10/10)</button>`;
                }
            } else if(type === 'notes') {
                title = "ملاحظات المعلم";
                body = `ملاحظة المستر: "${student.notes}"`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 6px; font-size: 11px;" onclick="updateData('notes', 'طالب منتظم ومجتهد جداً')">تعديل الملاحظة</button>`;
                }
            }

            document.getElementById('modalTitle').innerText = title;
            document.getElementById('modalBodyContent').innerHTML = body;
            
            let adminPanel = document.getElementById('adminControlPanel');
            let actionBtnContainer = document.getElementById('adminActionButtons');
            
            if(isAdmin && adminActions !== "") {
                actionBtnContainer.innerHTML = adminActions;
                adminPanel.classList.add('active');
            } else {
                actionBtnContainer.innerHTML = "";
                adminPanel.classList.remove('active');
            }

            document.getElementById('customModal').style.display = 'flex';
        }

        function closeModal(e) {
            document.getElementById('customModal').style.display = 'none';
        }

        function closeModalDirect() {
            document.getElementById('customModal').style.display = 'none';
        }

        function updateData(field, val) {
            let student = savedAccounts[currentStudentIndex];
            if(field === 'attendance') {
                student.attendance = val;
                document.getElementById('attCount').innerText = val;
            } else if(field === 'absence') {
                student.absence = val;
                document.getElementById('absCount').innerText = val;
            } else if(field === 'payment') {
                student.payment = val;
                document.getElementById('payStatus').innerText = val;
            } else if(field === 'score') {
                student.score = val;
                document.getElementById('scoreStatus').innerText = val;
            } else if(field === 'notes') {
                let customNote = prompt("أدخل الملاحظة الجديدة من المستر:", student.notes);
                if(customNote) student.notes = customNote;
            }

            localStorage.setItem('mps_all_students', JSON.stringify(savedAccounts));
            alert("تم التحديث بنجاح بواسطة المستر!");
            closeModalDirect();
        }

        renderSavedAccounts();
    </script>
</body>
</html>
