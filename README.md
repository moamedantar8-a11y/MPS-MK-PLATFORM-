<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MPS Platform | بوابة الطالب</title>
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
            padding: 10px;
        }

        .app-container {
            width: 100%;
            max-width: 480px;
            background: var(--light-bg);
            height: 92vh;
            max-height: 850px;
            border-radius: 35px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.3);
            display: flex;
            flex-direction: column;
            overflow: hidden;
            position: relative;
            border: 8px solid #1e293b;
        }

        .screen {
            display: none;
            flex: 1;
            flex-direction: column;
            overflow-y: auto;
            padding: 15px;
        }

        .screen.active {
            display: flex;
        }

        /* 1. الشاشة الأولى: الترحيب والحسابات المحفوظة */
        .welcome-screen {
            justify-content: center;
            align-items: center;
            text-align: center;
            background: linear-gradient(180deg, #1e3a8a 0%, #1e40af 100%);
            color: white;
            padding: 25px;
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
            padding: 10px 15px;
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

        /* 2. شاشة إنشاء الحساب الجديد */
        .register-screen {
            background: linear-gradient(180deg, #1e3a8a 0%, #1e40af 100%);
            color: white;
            justify-content: center;
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

        .form-group input::placeholder {
            color: #94a3b8;
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
        }

        .btn-secondary {
            background: transparent;
            color: #cbd5e1;
            border: 1px solid rgba(255,255,255,0.2);
            margin-top: 8px;
        }

        /* 3. لوحة تحكم الطالب (المطابقة للصور تماماً) */
        .top-navbar {
            background: white;
            padding: 10px 12px;
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
            gap: 5px;
            font-size: 14px;
            font-weight: 900;
            color: var(--primary-blue);
        }

        .nav-links {
            display: flex;
            gap: 5px;
            overflow-x: auto;
        }

        .nav-links::-webkit-scrollbar { display: none; }

        .nav-btn {
            background: #f1f5f9;
            border: none;
            padding: 5px 8px;
            border-radius: 8px;
            font-size: 11px;
            font-weight: 600;
            color: var(--text-muted);
            cursor: pointer;
            white-space: nowrap;
        }

        .nav-btn.active, .nav-btn:hover {
            background: var(--secondary-blue);
            color: white;
        }

        /* كروت بيانات الطالب المنظمة */
        .profile-header-card {
            background: linear-gradient(135deg, var(--secondary-blue), var(--primary-blue));
            color: white;
            padding: 15px;
            border-radius: 15px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 12px;
            box-shadow: 0 4px 10px rgba(59, 130, 246, 0.2);
        }

        .info-card-item {
            background: white;
            padding: 12px 15px;
            border-radius: 12px;
            margin-bottom: 8px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            box-shadow: 0 2px 4px rgba(0,0,0,0.02);
            border: 1px solid #e2e8f0;
        }

        .info-card-item .label-side {
            display: flex;
            align-items: center;
            gap: 10px;
            color: var(--text-muted);
            font-size: 12px;
        }

        .info-card-item .value-side {
            font-weight: 700;
            color: var(--text-main);
            font-size: 13px;
        }

        .info-card-item i {
            color: var(--secondary-blue);
            font-size: 16px;
        }

        .success-alert {
            background: #d1fae5;
            color: #065f46;
            padding: 10px;
            border-radius: 10px;
            text-align: center;
            font-size: 12px;
            font-weight: bold;
            margin-bottom: 10px;
            display: flex;
            justify-content: center;
            align-items: center;
            gap: 6px;
        }

        /* شبكة الأزرار والأقسام الأخرى */
        .dashboard-grid {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .dash-card {
            background: white;
            padding: 15px;
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
        }

        .dash-card-content {
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .dash-card-icon {
            width: 40px;
            height: 40px;
            background: #eff6ff;
            color: var(--secondary-blue);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 16px;
        }

        .dash-card-title {
            font-size: 14px;
            font-weight: 700;
            color: var(--text-main);
        }

        .app-footer {
            text-align: center;
            padding: 8px;
            font-size: 11px;
            color: var(--text-muted);
            background: white;
            border-top: 1px solid #f1f5f9;
            margin-top: auto;
        }
    </style>
</head>
<body>

    <div class="app-container">
        
        <!-- 1. شاشة اختيار أو تسجيل الحسابات -->
        <div id="screen-welcome" class="screen welcome-screen active">
            <div class="welcome-logo"><i class="fa-solid fa-graduation-cap"></i></div>
            <h1 style="font-size: 22px; font-weight: 900; margin-bottom: 5px;">MPS Platform</h1>
            <p style="font-size: 12px; color: #94a3b8; margin-bottom: 15px;">بوابة متابعة الطالب والمعلم</p>

            <div style="width: 100%; text-align: right; font-size: 11px; font-weight: bold; margin-bottom: 5px;">الحسابات المسجلة:</div>
            <div class="accounts-list" id="savedAccountsContainer"></div>

            <button class="btn-main" onclick="showScreen('screen-register')">تسجيل حساب طالب جديد</button>
        </div>

        <!-- 2. صفحة إنشاء حساب طالب جديد -->
        <div id="screen-register" class="screen register-screen">
            <h2 style="font-size: 20px; font-weight: 900; text-align: center; margin-bottom: 3px;">إنشاء حساب طالب</h2>
            <p style="font-size: 11px; color: #cbd5e1; text-align: center; margin-bottom: 15px;">أدخل بياناتك للانتقال مباشرة إلى لوحة المتابعة</p>

            <div class="form-group">
                <label>اسم الطالب الكامل</label>
                <input type="text" id="regStudentName" placeholder="مثال: محمد عنتر">
            </div>

            <div class="form-group">
                <label>اسم المدرس</label>
                <input type="text" id="regTeacherName" value="جلال الاتربي" placeholder="اسم المدرس">
            </div>

            <div class="form-group">
                <label>رقم هاتف ولي الأمر</label>
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
                <input type="text" id="regGroup" value="السبت والثلاثاء الساعة 3" placeholder="موعد المجموعة">
            </div>

            <button class="btn-main" onclick="registerNewStudent()">حفظ ودخول المنصة</button>
            <button class="btn-main btn-secondary" onclick="showScreen('screen-welcome')">رجوع</button>
        </div>

        <!-- 3. لوحة تحكم الطالب الكاملة (بناءً على لقطات الشاشة المرفقة) -->
        <div id="screen-dashboard" class="screen" style="padding: 0; background: var(--light-bg);">
            
            <!-- الشريط العلوي والتنقل -->
            <div class="top-navbar">
                <div class="nav-brand">
                    <i class="fa-solid fa-layer-group"></i>
                    <span>MPS Platform</span>
                </div>
                <div class="nav-links">
                    <button class="nav-btn active" onclick="switchSection('profile')">الملف الشخصي</button>
                    <button class="nav-btn" onclick="switchSection('stats')">المتابعة</button>
                    <button class="nav-btn" onclick="showScreen('screen-welcome')" style="color: var(--accent-green);"><i class="fa-solid fa-users"></i> تبديل الحساب</button>
                </div>
            </div>

            <!-- المحتوى الداخلي -->
            <div style="padding: 12px; flex: 1; overflow-y: auto;">
                
                <!-- قسم الملف الشخصي للطالب -->
                <div id="section-profile">
                    <div class="success-alert">
                        <i class="fa-solid fa-circle-check"></i> تم تسجيل الدخول بنجاح
                    </div>

                    <div class="profile-header-card">
                        <div>
                            <h3 id="uiStudentName" style="font-size: 16px; font-weight: 900;">محمد عنتر</h3>
                            <span style="font-size: 11px; opacity: 0.9;">الرقم التعريفي: <span id="uiId">3034</span></span>
                        </div>
                        <i class="fa-solid fa-graduation-cap" style="font-size: 28px;"></i>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side">
                            <i class="fa-solid fa-user-tie"></i>
                            <span>اسم المدرس</span>
                        </div>
                        <div class="value-side" id="uiTeacher">جلال الاتربي</div>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side">
                            <i class="fa-solid fa-hashtag"></i>
                            <span>كود الطالب</span>
                        </div>
                        <div class="value-side" id="uiCode">3034</div>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side">
                            <i class="fa-solid fa-phone"></i>
                            <span>هاتف ولي الأمر</span>
                        </div>
                        <div class="value-side" id="uiPhone">غير متوفر</div>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side">
                            <i class="fa-solid fa-users-rectangle"></i>
                            <span>الصف الدراسي</span>
                        </div>
                        <div class="value-side" id="uiGrade">الصف الاول الثانوي</div>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side">
                            <i class="fa-solid fa-calendar-days"></i>
                            <span>المجموعة</span>
                        </div>
                        <div class="value-side" id="uiGroup">السبت والثلاثاء الساعة 3</div>
                    </div>
                </div>

                <!-- قسم معلومات ومتابعة الطالب (الصور الإضافية) -->
                <div id="section-stats" style="display: none;">
                    <h4 style="font-size: 14px; font-weight: 900; color: var(--primary-blue); margin-bottom: 10px; text-align: right;">معلومات الطالب والمتابعة</h4>
                    
                    <div class="dashboard-grid">
                        <div class="dash-card">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-bell"></i></div>
                                <div class="dash-card-title">الاشعارات</div>
                            </div>
                            <i class="fa-solid fa-chevron-left" style="font-size: 12px; color: var(--text-muted);"></i>
                        </div>

                        <div class="dash-card">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-calendar-check"></i></div>
                                <div class="dash-card-title">عدد مرات الحضور</div>
                            </div>
                            <span style="font-weight: bold; color: var(--accent-green);">12</span>
                        </div>

                        <div class="dash-card">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-calendar-xmark"></i></div>
                                <div class="dash-card-title">عدد مرات الغياب</div>
                            </div>
                            <span style="font-weight: bold; color: #ef4444;">1</span>
                        </div>

                        <div class="dash-card">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-wallet"></i></div>
                                <div class="dash-card-title">المدفوعات</div>
                            </div>
                            <span style="font-size: 12px; font-weight: bold; color: var(--secondary-blue);">تم السداد</span>
                        </div>

                        <div class="dash-card">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-chart-line"></i></div>
                                <div class="dash-card-title">الدرجات اليومية والشهرية</div>
                            </div>
                            <i class="fa-solid fa-chevron-left" style="font-size: 12px; color: var(--text-muted);"></i>
                        </div>

                        <div class="dash-card">
                            <div class="dash-card-content">
                                <div class="dash-card-icon"><i class="fa-solid fa-note-sticky"></i></div>
                                <div class="dash-card-title">ملاحظات المعلم</div>
                            </div>
                            <i class="fa-solid fa-chevron-left" style="font-size: 12px; color: var(--text-muted);"></i>
                        </div>
                    </div>
                </div>

            </div>

            <div class="app-footer">
                Developed by <span>MK CREATIVE Agency</span>
            </div>
        </div>

    </div>

    <script>
        let savedAccounts = JSON.parse(localStorage.getItem('mps_student_accounts')) || [
            { id: 3034, name: "محمد عنتر", teacher: "جلال الاتربي", phone: "غير متوفر", grade: "الصف الاول الثانوي", group: "السبت والثلاثاء الساعة 3" }
        ];

        function renderSavedAccounts() {
            const container = document.getElementById('savedAccountsContainer');
            container.innerHTML = '';
            
            if(savedAccounts.length === 0) {
                container.innerHTML = '<p style="font-size: 11px; color: #cbd5e1;">لا توجد حسابات مسجلة.</p>';
                return;
            }

            savedAccounts.forEach(acc => {
                container.innerHTML += `
                    <div class="account-card-saved" onclick='loginAccount(${JSON.stringify(acc)})'>
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
                group: group || "المجموعة العامة"
            };

            savedAccounts.push(newAcc);
            localStorage.setItem('mps_student_accounts', JSON.stringify(savedAccounts));
            
            loginAccount(newAcc);
        }

        function loginAccount(acc) {
            document.getElementById('uiStudentName').innerText = acc.name;
            document.getElementById('uiId').innerText = acc.id;
            document.getElementById('uiTeacher').innerText = acc.teacher;
            document.getElementById('uiCode').innerText = acc.id;
            document.getElementById('uiPhone').innerText = acc.phone;
            document.getElementById('uiGrade').innerText = acc.grade;
            document.getElementById('uiGroup').innerText = acc.group;

            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById('screen-dashboard').classList.add('active');
            switchSection('profile');
        }

        function switchSection(sectionName) {
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            event.target.classList.add('active');

            if(sectionName === 'profile') {
                document.getElementById('section-profile').style.display = 'block';
                document.getElementById('section-stats').style.display = 'none';
            } else {
                document.getElementById('section-profile').style.display = 'none';
                document.getElementById('section-stats').style.display = 'block';
            }
        }

        renderSavedAccounts();
    </script>
</body>
</html>
