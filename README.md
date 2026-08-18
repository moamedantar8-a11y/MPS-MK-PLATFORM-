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
            align-items: stretch;
        }

        .app-container {
            width: 100%;
            max-width: 100%;
            background: var(--light-bg);
            min-height: 100vh;
            display: flex;
            flex-direction: column;
            overflow-x: hidden;
            position: relative;
        }

        .screen {
            display: none;
            flex: 1;
            flex-direction: column;
            padding: 20px;
            max-width: 800px;
            margin: 0 auto;
            width: 100%;
        }

        .screen.active {
            display: flex;
        }

        /* الشاشة الأولى: الترحيب والحسابات */
        .welcome-screen {
            justify-content: center;
            align-items: center;
            text-align: center;
            background: linear-gradient(180deg, #1e3a8a 0%, #1e40af 100%);
            color: white;
            padding: 30px;
        }

        .welcome-logo {
            font-size: 70px;
            color: #60a5fa;
            margin-bottom: 15px;
        }

        .accounts-list {
            width: 100%;
            max-width: 450px;
            margin: 20px 0;
            max-height: 250px;
            overflow-y: auto;
        }

        .account-card-saved {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            padding: 12px 18px;
            border-radius: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
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
            justify-content: center;
            align-items: center;
        }

        .form-box {
            width: 100%;
            max-width: 450px;
        }

        .form-group {
            width: 100%;
            margin-bottom: 12px;
            text-align: right;
        }

        .form-group label {
            font-size: 12px;
            color: #cbd5e1;
            display: block;
            margin-bottom: 4px;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 12px;
            border-radius: 10px;
            border: 1px solid rgba(255,255,255,0.2);
            background: rgba(255,255,255,0.08);
            color: white;
            font-size: 14px;
            outline: none;
        }

        .form-group input::placeholder {
            color: #94a3b8;
        }

        .btn-main {
            width: 100%;
            background: var(--secondary-blue);
            color: white;
            border: none;
            padding: 14px;
            border-radius: 12px;
            font-size: 15px;
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
            margin-top: 10px;
        }

        /* الشريط العلوي */
        .top-navbar {
            background: white;
            padding: 12px 25px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 4px 6px -1px rgba(0,0,0,0.03);
            position: sticky;
            top: 0;
            z-index: 100;
        }

        .nav-brand {
            display: flex;
            align-items: center;
            gap: 8px;
            font-size: 16px;
            font-weight: 900;
            color: var(--primary-blue);
        }

        .nav-links {
            display: flex;
            gap: 8px;
        }

        .nav-btn {
            background: #f1f5f9;
            border: none;
            padding: 8px 14px;
            border-radius: 8px;
            font-size: 13px;
            font-weight: 600;
            color: var(--text-muted);
            cursor: pointer;
            transition: var(--transition);
        }

        .nav-btn.active, .nav-btn:hover {
            background: var(--secondary-blue);
            color: white;
        }

        /* لوحة التحكم والبيانات */
        .profile-header-card {
            background: linear-gradient(135deg, var(--secondary-blue), var(--primary-blue));
            color: white;
            padding: 20px;
            border-radius: 16px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            box-shadow: 0 4px 15px rgba(59, 130, 246, 0.2);
        }

        .info-card-item {
            background: white;
            padding: 15px 20px;
            border-radius: 12px;
            margin-bottom: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 5px rgba(0,0,0,0.02);
            border: 1px solid #e2e8f0;
        }

        .info-card-item .label-side {
            display: flex;
            align-items: center;
            gap: 12px;
            color: var(--text-muted);
            font-size: 14px;
        }

        .info-card-item .value-side {
            font-weight: 700;
            color: var(--text-main);
            font-size: 15px;
        }

        .info-card-item i {
            color: var(--secondary-blue);
            font-size: 18px;
        }

        .success-alert {
            background: #d1fae5;
            color: #065f46;
            padding: 12px;
            border-radius: 10px;
            text-align: center;
            font-size: 13px;
            font-weight: bold;
            margin-bottom: 15px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 8px;
        }

        /* شبكة أزرار المتابعة */
        .dashboard-grid {
            display: grid;
            grid-template-columns: 1fr;
            gap: 12px;
        }

        .dash-card {
            background: white;
            padding: 18px 20px;
            border-radius: 14px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            border: 1px solid #e2e8f0;
            cursor: pointer;
            transition: var(--transition);
        }

        .dash-card:hover {
            border-color: var(--secondary-blue);
            transform: translateY(-2px);
            box-shadow: 0 4px 12px rgba(0,0,0,0.05);
        }

        .dash-card-content {
            display: flex;
            align-items: center;
            gap: 15px;
        }

        .dash-card-icon {
            width: 45px;
            height: 45px;
            background: #eff6ff;
            color: var(--secondary-blue);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 18px;
        }

        .dash-card-title {
            font-size: 15px;
            font-weight: 700;
            color: var(--text-main);
        }

        /* النافذة المنبثقة للعرض التوضيحي (Modal) */
        .modal-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: rgba(0,0,0,0.5);
            display: none;
            justify-content: center;
            align-items: center;
            z-index: 1000;
            padding: 20px;
        }

        .modal-card {
            background: white;
            width: 100%;
            max-width: 450px;
            border-radius: 20px;
            padding: 25px;
            box-shadow: 0 20px 25px -5px rgba(0,0,0,0.1);
            animation: modalPop 0.3s ease;
        }

        @keyframes modalPop {
            0% { transform: scale(0.9); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .modal-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 15px;
            border-bottom: 1px solid #f1f5f9;
            padding-bottom: 10px;
        }

        .modal-body {
            font-size: 14px;
            color: var(--text-muted);
            line-height: 1.6;
            margin-bottom: 20px;
            text-align: right;
        }

        .admin-controls {
            background: #eff6ff;
            border: 1px dashed var(--secondary-blue);
            padding: 12px;
            border-radius: 10px;
            margin-top: 15px;
            display: none;
        }

        .admin-controls.active {
            display: block;
        }

        .app-footer {
            text-align: center;
            padding: 15px;
            font-size: 12px;
            color: var(--text-muted);
            background: white;
            border-top: 1px solid #f1f5f9;
            margin-top: auto;
        }

        @media (min-width: 768px) {
            .dashboard-grid {
                grid-template-columns: 1fr 1fr;
            }
        }
    </style>
</head>
<body>

    <div class="app-container">
        
        <!-- 1. الشاشة الأولى: الترحيب والحسابات -->
        <div id="screen-welcome" class="screen welcome-screen active">
            <div class="welcome-logo"><i class="fa-solid fa-graduation-cap"></i></div>
            <h1 style="font-size: 26px; font-weight: 900; margin-bottom: 5px;">MPS Platform</h1>
            <p style="font-size: 14px; color: #94a3b8; margin-bottom: 20px;">النظام الذكي المتكامل لإدارة المجموعات ومتابعة الطلاب</p>

            <div style="width: 100%; max-width: 450px; text-align: right; font-size: 13px; font-weight: bold; margin-bottom: 5px;">الحسابات المسجلة:</div>
            <div class="accounts-list" id="savedAccountsContainer"></div>

            <div style="width: 100%; max-width: 450px; display: flex; gap: 10px;">
                <button class="btn-main" onclick="showScreen('screen-register')">تسجيل حساب جديد</button>
                <button class="btn-main" style="background: #0f172a;" onclick="showAdminLogin()">دخول المعلم (الأدمن)</button>
            </div>
        </div>

        <!-- 2. شاشة تسجيل طالب جديد -->
        <div id="screen-register" class="screen register-screen">
            <div class="form-box">
                <h2 style="font-size: 24px; font-weight: 900; text-align: center; margin-bottom: 5px;">إنشاء حساب طالب جديد</h2>
                <p style="font-size: 13px; color: #cbd5e1; text-align: center; margin-bottom: 20px;">أدخل بيانات الطالب للانتقال للمنصة مباشرة</p>

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
                    <input type="text" id="regGroup" value="السبت والثلاثاء الساعة 3" placeholder="المجموعة">
                </div>

                <button class="btn-main" onclick="registerNewStudent()">حفظ ودخول المنصة</button>
                <button class="btn-main btn-secondary" onclick="showScreen('screen-welcome')">رجوع</button>
            </div>
        </div>

        <!-- 3. لوحة تحكم المنصة الكاملة -->
        <div id="screen-dashboard" class="screen" style="padding: 0; background: var(--light-bg);">
            
            <div class="top-navbar">
                <div class="nav-brand">
                    <i class="fa-solid fa-layer-group"></i>
                    <span>MPS Platform</span>
                </div>
                <div class="nav-links">
                    <button class="nav-btn active" onclick="switchSection('profile')">الملف الشخصي</button>
                    <button class="nav-btn" onclick="switchSection('stats')">المتابعة</button>
                    <button class="nav-btn" id="adminBadgeBtn" style="background: #fef08a; color: #854d0e; display: none;"><i class="fa-solid fa-shield-halved"></i> وضع الأدمن</button>
                    <button class="nav-btn" onclick="showScreen('screen-welcome')" style="color: var(--accent-green);"><i class="fa-solid fa-users"></i> تبديل الحساب</button>
                </div>
            </div>

            <div style="padding: 20px; flex: 1; max-width: 800px; margin: 0 auto; width: 100%;">
                
                <!-- قسم الملف الشخصي -->
                <div id="section-profile">
                    <div class="success-alert">
                        <i class="fa-solid fa-circle-check"></i> تم تسجيل الدخول بنجاح إلى لوحة المتابعة
                    </div>

                    <div class="profile-header-card">
                        <div>
                            <h3 id="uiStudentName" style="font-size: 20px; font-weight: 900;">محمد عنتر</h3>
                            <span style="font-size: 13px; opacity: 0.9;">الرقم التعريفي: <span id="uiId">3034</span></span>
                        </div>
                        <i class="fa-solid fa-graduation-cap" style="font-size: 35px;"></i>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-user-tie"></i><span>اسم المدرس</span></div>
                        <div class="value-side" id="uiTeacher">جلال الاتربي</div>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-hashtag"></i><span>كود الطالب</span></div>
                        <div class="value-side" id="uiCode">3034</div>
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
                        <div class="value-side" id="uiGroup">السبت والثلاثاء الساعة 3</div>
                    </div>
                </div>

                <!-- قسم المتابعة والأزرار التفاعلية -->
                <div id="section-stats" style="display: none;">
                    <h4 style="font-size: 18px; font-weight: 900; color: var(--primary-blue); margin-bottom: 15px; text-align: right;">لوحة المتابعة الشاملة</h4>
                    
                    <div class="dashboard-grid">
                        <div class="dash-card" onclick="openModal('notifications')">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-bell"></i></div>
                                <div class="dash-card-title">الاشعارات والتنبيهات</div>
                            </div>
                            <i class="fa-solid fa-chevron-left" style="color: var(--text-muted);"></i>
                        </div>

                        <div class="dash-card" onclick="openModal('attendance')">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-calendar-check"></i></div>
                                <div class="dash-card-title">عدد مرات الحضور</div>
                            </div>
                            <span id="attCount" style="font-weight: bold; color: var(--accent-green); font-size: 16px;">0</span>
                        </div>

                        <div class="dash-card" onclick="openModal('absence')">
                            <div class="dash-card-content">
                                <div class="dash-card-icon" style="background: #fee2e2; color: var(--accent-red);"><i class="fa-solid fa-calendar-xmark"></i></div>
                                <div class="dash-card-title">عدد مرات الغياب</div>
                            </div>
                            <span id="absCount" style="font-weight: bold; color: var(--accent-red); font-size: 16px;">0</span>
                        </div>

                        <div class="dash-card" onclick="openModal('payments')">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-wallet"></i></div>
                                <div class="dash-card-title">المدفوعات والاشتراكات</div>
                            </div>
                            <span id="payStatus" style="font-size: 13px; font-weight: bold; color: var(--secondary-blue);">مسدد</span>
                        </div>

                        <div class="dash-card" onclick="openModal('exams')">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-chart-line"></i></div>
                                <div class="dash-card-title">الدرجات اليومية والشهرية</div>
                            </div>
                            <i class="fa-solid fa-chevron-left" style="color: var(--text-muted);"></i>
                        </div>

                        <div class="dash-card" onclick="openModal('notes')">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-note-sticky"></i></div>
                                <div class="dash-card-title">ملاحظات المعلم</div>
                            </div>
                            <i class="fa-solid fa-chevron-left" style="color: var(--text-muted);"></i>
                        </div>
                    </div>
                </div>

            </div>

            <div class="app-footer">
                Developed by <span>MK CREATIVE Agency</span>
            </div>
        </div>

    </div>

    <!-- نافذة العرض التوضيحي المنبثقة (Modal) -->
    <div class="modal-overlay" id="customModal" onclick="closeModal(event)">
        <div class="modal-card" onclick="event.stopPropagation()">
            <div class="modal-header">
                <h3 id="modalTitle" style="font-size: 16px; font-weight: 900; color: var(--primary-blue);">عنوان القسم</h3>
                <i class="fa-solid fa-xmark" style="cursor: pointer; font-size: 18px; color: var(--text-muted);" onclick="closeModalDirect()"></i>
            </div>
            <div class="modal-body" id="modalBodyContent">
                <!-- المحتوى التوضيحي -->
            </div>
            
            <!-- أجزاء التحكم الخاصة بالأدمن فقط -->
            <div class="admin-controls" id="adminControlPanel">
                <p style="font-size: 12px; font-weight: bold; color: var(--primary-blue); margin-bottom: 8px;"><i class="fa-solid fa-lock-open"></i> لوحة تحكم المستر (أدمن فقط):</p>
                <div id="adminActionButtons"></div>
            </div>
        </div>
    </div>

    <script>
        let isAdmin = false;
        let currentStudentIndex = 0;

        let savedAccounts = JSON.parse(localStorage.getItem('mps_all_students')) || [
            { id: 3034, name: "محمد عنتر", teacher: "جلال الاتربي", phone: "غير متوفر", grade: "الصف الاول الثانوي", group: "السبت والثلاثاء الساعة 3", attendance: 0, absence: 0, payment: "تم السداد", notes: "طالب مجتهد ومشارك ممتاز في الحصة.", score: "الدرجة النهائية (10/10)" }
        ];

        function renderSavedAccounts() {
            const container = document.getElementById('savedAccountsContainer');
            container.innerHTML = '';
            
            if(savedAccounts.length === 0) {
                container.innerHTML = '<p style="font-size: 13px; color: #cbd5e1;">لا توجد حسابات مسجلة.</p>';
                return;
            }

            savedAccounts.forEach((acc, index) => {
                container.innerHTML += `
                    <div class="account-card-saved" onclick="loginStudent(${index})">
                        <div style="text-align: right;">
                            <h4 style="font-size: 15px; font-weight: bold;">${acc.name}</h4>
                            <span style="font-size: 12px; color: #94a3b8;">${acc.grade} (كود: ${acc.id})</span>
                        </div>
                        <i class="fa-solid fa-chevron-left" style="font-size: 13px; color: #60a5fa;"></i>
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
            let pass = prompt("أدخل كلمة مرور الأدمن (المستر):", "1234");
            if(pass === "1234") {
                isAdmin = true;
                alert("تم تسجيل الدخول بصلاحيات المعلم (أدمن). يمكنك تعديل حضور وغياب ودرجات الطلاب.");
                if(savedAccounts.length > 0) {
                    loginStudent(0);
                } else {
                    showScreen('screen-register');
                }
            } else if(pass !== null) {
                alert("كلمة المرور غير صحيحة!");
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
                attendance: 0,
                absence: 0,
                payment: "تم السداد",
                notes: "لم يتم تسجيل ملاحظات حتى الآن.",
                score: "لم تُحسب بعد"
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
            document.getElementById('uiCode').innerText = acc.id;
            document.getElementById('uiPhone').innerText = acc.phone;
            document.getElementById('uiGrade').innerText = acc.grade;
            document.getElementById('uiGroup').innerText = acc.group;

            document.getElementById('attCount').innerText = acc.attendance;
            document.getElementById('absCount').innerText = acc.absence;
            document.getElementById('payStatus').innerText = acc.payment;

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

        // إدارات النوافذ المنبثقة والعرض التوضيحي مع حصر التعديل بالأدمن فقط
        function openModal(type) {
            let student = savedAccounts[currentStudentIndex];
            let title = "";
            let body = "";
            let adminActions = "";

            if(type === 'notifications') {
                title = "الإشعارات والتنبيهات";
                body = `• تنبيه حصة: تم تسجيل الحضور للحصة الأخيرة بنجاح.<br>• رسالة من المدرس: برجاء مراجعة الواجب المدرسي جيداً قبل الموعد القادم.`;
            } else if(type === 'attendance') {
                title = "سجل عدد مرات الحضور";
                body = `إجمالي عدد مرات حضور الحصص النظامية للطالب حتى الآن هو: <strong>${student.attendance} مرة</strong>.<br><br><em>(هذا العداد يبدأ من الصفر ويتم تحديثه عبر مسح الباركود أو بواسطة المستر).</em>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 8px; font-size: 13px;" onclick="updateData('attendance', 1)">+ زيادة حضور</button>`;
                }
            } else if(type === 'absence') {
                title = "سجل عدد مرات الغياب";
                body = `إجمالي عدد مرات غياب الطالب عن الحصص هو: <strong>${student.absence} مرة</strong>.<br><br><em>(يبدأ من الصفر ولا يتغير إلا بتسجيل مشرف القاعة أو المستر).</em>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 8px; font-size: 13px; background: var(--accent-red);" onclick="updateData('absence', 1)">+ تسسجيل غياب جديد</button>`;
                }
            } else if(type === 'payments') {
                title = "حالة المدفوعات والاشتراكات";
                body = `حالة اشتراك الشهر الحالي: <span style="color: var(--accent-green); font-weight: bold;">${student.payment}</span>.<br>قيمة الاشتراك: 150 جنيه شهرياً.`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 8px; font-size: 13px;" onclick="updateData('payment', 'تم السداد')">تعديل إلى (تم السداد)</button>`;
                }
            } else if(type === 'exams') {
                title = "الدرجات اليومية والشهرية";
                body = `آخر تقييم شهري ويومي للطالب:<br><strong>${student.score}</strong>.<br>المستوى العام ممتاز ومستمر في التطور.`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 8px; font-size: 13px;" onclick="updateData('score', 'ممتاز (10/10)')">تحديث الدرجة إلى ممتاز</button>`;
                }
            } else if(type === 'notes') {
                title = "ملاحظات المعلم الخاصة";
                body = `ملاحظة المستر الحالية عن الطالب:<br>"${student.notes}"`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 8px; font-size: 13px;" onclick="updateData('notes', 'ملاحظة جديدة: منتظم ومجتهد')">تحديث الملاحظة</button>`;
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
                student.attendance += 1;
                document.getElementById('attCount').innerText = student.attendance;
            } else if(field === 'absence') {
                student.absence += 1;
                document.getElementById('absCount').innerText = student.absence;
            } else if(field === 'payment') {
                student.payment = val;
                document.getElementById('payStatus').innerText = val;
            } else if(field === 'score') {
                student.score = val;
            } else if(field === 'notes') {
                let newNote = prompt("أدخل الملاحظة الجديدة:", student.notes);
                if(newNote) student.notes = newNote;
            }

            localStorage.setItem('mps_all_students', JSON.stringify(savedAccounts));
            alert("تم تحديث البيانات بنجاح بواسطة الأدمن!");
            closeModalDirect();
        }

        renderSavedAccounts();
    </script>
</body>
</html> 
