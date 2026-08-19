<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>MPS Platform Pro | النظام الإداري التعليمي الشامل</title>
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
            --accent-yellow: #f59e0b;
            --transition: all 0.3s ease;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Tajawal', sans-serif;
        }

        body {
            background: linear-gradient(135deg, #0f172a 0%, #1e3a8a 100%);
            color: var(--text-main);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 10px;
        }

        .phone-frame {
            width: 100%;
            max-width: 410px;
            height: 88vh;
            max-height: 880px;
            background: var(--light-bg);
            border-radius: 35px;
            box-shadow: 0 25px 50px -12px rgba(0, 0, 0, 0.6);
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

        .welcome-screen {
            background: linear-gradient(180deg, #1e3a8a 0%, #1e40af 100%);
            color: white;
            padding: 20px;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        .welcome-logo {
            font-size: 50px;
            color: #60a5fa;
            margin-bottom: 8px;
        }

        .accounts-list {
            width: 100%;
            margin: 12px 0;
            max-height: 140px;
            overflow-y: auto;
        }

        .account-card-saved {
            background: rgba(255, 255, 255, 0.1);
            border: 1px solid rgba(255, 255, 255, 0.2);
            padding: 8px 12px;
            border-radius: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 6px;
            cursor: pointer;
            transition: var(--transition);
        }

        .account-card-saved:hover {
            background: rgba(255, 255, 255, 0.2);
        }

        .register-screen {
            background: linear-gradient(180deg, #1e3a8a 0%, #1e40af 100%);
            color: white;
            padding: 20px;
            justify-content: center;
            align-items: center;
        }

        .form-group {
            width: 100%;
            margin-bottom: 8px;
            text-align: right;
        }

        .form-group label {
            font-size: 11px;
            color: #cbd5e1;
            display: block;
            margin-bottom: 2px;
        }

        .form-group input, .form-group select {
            width: 100%;
            padding: 8px 10px;
            border-radius: 8px;
            border: 1px solid rgba(255,255,255,0.2);
            background: rgba(255,255,255,0.08);
            color: white;
            font-size: 12px;
            outline: none;
        }

        .form-group select option {
            background: #1e3a8a;
            color: white;
        }

        .btn-main {
            width: 100%;
            background: var(--secondary-blue);
            color: white;
            border: none;
            padding: 10px;
            border-radius: 10px;
            font-size: 13px;
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
            margin-top: 6px;
        }

        .top-navbar {
            background: white;
            padding: 8px 12px;
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
            gap: 5px;
            font-size: 13px;
            font-weight: 900;
            color: var(--primary-blue);
        }

        .nav-links {
            display: flex;
            gap: 3px;
        }

        .nav-btn {
            background: #f1f5f9;
            border: none;
            padding: 5px 7px;
            border-radius: 5px;
            font-size: 10px;
            font-weight: 600;
            color: var(--text-muted);
            cursor: pointer;
            transition: var(--transition);
        }

        .nav-btn.active, .nav-btn:hover {
            background: var(--secondary-blue);
            color: white;
        }

        .dashboard-content {
            padding: 12px;
        }

        .profile-header-card {
            background: linear-gradient(135deg, var(--secondary-blue), var(--primary-blue));
            color: white;
            padding: 12px;
            border-radius: 12px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 10px;
        }

        .info-card-item {
            background: white;
            padding: 10px 12px;
            border-radius: 8px;
            margin-bottom: 6px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid #e2e8f0;
            font-size: 12px;
        }

        .info-card-item .label-side {
            display: flex;
            align-items: center;
            gap: 8px;
            color: var(--text-muted);
        }

        .info-card-item .value-side {
            font-weight: 700;
            color: var(--text-main);
        }

        .info-card-item i {
            color: var(--secondary-blue);
        }

        .digital-id-card {
            background: white;
            border-radius: 10px;
            padding: 10px;
            margin-bottom: 10px;
            border: 1px solid #e2e8f0;
            display: flex;
            align-items: center;
            gap: 10px;
        }
        .qr-box {
            width: 45px;
            height: 45px;
            background: #eff6ff;
            color: var(--secondary-blue);
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 8px;
            font-size: 20px;
        }

        .dashboard-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 8px;
            margin-bottom: 12px;
        }

        .dash-card {
            background: white;
            padding: 10px;
            border-radius: 10px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            border: 1px solid #e2e8f0;
            cursor: pointer;
            transition: var(--transition);
            min-height: 85px;
        }

        .dash-card:hover {
            border-color: var(--secondary-blue);
            transform: translateY(-2px);
        }

        .dash-card-icon {
            width: 28px;
            height: 28px;
            background: #eff6ff;
            color: var(--secondary-blue);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 12px;
            margin-bottom: 5px;
        }

        .dash-card-title {
            font-size: 11px;
            font-weight: 700;
            color: var(--text-main);
        }

        .dash-card-value {
            font-size: 10px;
            color: var(--text-muted);
            font-weight: bold;
            margin-top: 3px;
        }

        .extra-section {
            background: white;
            border-radius: 10px;
            padding: 10px 12px;
            margin-bottom: 8px;
            border: 1px solid #e2e8f0;
        }

        .extra-section h5 {
            font-size: 12px;
            color: var(--primary-blue);
            margin-bottom: 6px;
            display: flex;
            align-items: center;
            justify-content: space-between;
            gap: 5px;
        }

        .schedule-row {
            display: flex;
            justify-content: space-between;
            font-size: 11px;
            padding: 5px 0;
            border-bottom: 1px dashed #f1f5f9;
        }

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
            border-radius: 14px;
            padding: 16px;
            box-shadow: 0 20px 25px -5px rgba(0,0,0,0.2);
            text-align: right;
            max-height: 80vh;
            overflow-y: auto;
        }

        .admin-controls {
            background: #eff6ff;
            border: 1px dashed var(--secondary-blue);
            padding: 10px;
            border-radius: 8px;
            margin-top: 10px;
            display: none;
        }

        .admin-controls.active {
            display: block;
        }

        .app-footer {
            text-align: center;
            padding: 8px;
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
            <h1 style="font-size: 20px; font-weight: 900; margin-bottom: 2px;">MPS Platform Pro</h1>
            <p style="font-size: 11px; color: #94a3b8; margin-bottom: 12px;">ابتدائي، إعدادي، وثانوي - النظام الذكي</p>

            <div style="width: 100%; text-align: right; font-size: 11px; font-weight: bold; margin-bottom: 4px;">اختر حساب الطالب:</div>
            <div class="accounts-list" id="savedAccountsContainer"></div>

            <div style="width: 100%;">
                <button class="btn-main" onclick="showScreen('screen-register')">تسجيل طالب جديد بالسنتر</button>
                <button class="btn-main" style="background: #0f172a;" onclick="showAdminLogin()">دخول المعلم (أدمن 2026)</button>
            </div>
        </div>

        <!-- 2. شاشة تسجيل طالب جديد -->
        <div id="screen-register" class="screen register-screen">
            <h2 style="font-size: 18px; font-weight: 900; text-align: center; margin-bottom: 2px;">إضافة طالب للسنتر</h2>
            <p style="font-size: 10px; color: #cbd5e1; text-align: center; margin-bottom: 12px;">جميع المراحل التعليمية</p>

            <div class="form-group">
                <label>اسم الطالب الكامل</label>
                <input type="text" id="regStudentName" placeholder="مثال: محمد عنتر">
            </div>

            <div class="form-group">
                <label>اسم المعلم / المستر</label>
                <input type="text" id="regTeacherName" value="جلال الاتربي" placeholder="اسم المعلم">
            </div>

            <div class="form-group">
                <label>رقم هاتف ولي الأمر</label>
                <input type="text" id="regParentPhone" placeholder="010xxxxxxxx">
            </div>

            <div class="form-group">
                <label>الصف الدراسي</label>
                <select id="regGrade">
                    <!-- المرحلة الابتدائية -->
                    <option value="الصف الرابع الابتدائي">الصف الرابع الابتدائي</option>
                    <option value="الصف الخامس الابتدائي">الصف الخامس الابتدائي</option>
                    <option value="الصف السادس الابتدائي">الصف السادس الابتدائي</option>
                    <!-- المرحلة الإعدادية -->
                    <option value="الصف الأول الإعدادي">الصف الأول الإعدادي</option>
                    <option value="الصف الثاني الإعدادي">الصف الثاني الإعدادي</option>
                    <option value="الصف الثالث الإعدادي">الصف الثالث الإعدادي</option>
                    <!-- المرحلة الثانوية -->
                    <option value="الصف الأول الثانوي">الصف الأول الثانوي</option>
                    <option value="الصف الثاني الثانوي">الصف الثاني الثانوي</option>
                    <option value="الصف الثالث الثانوي">الصف الثالث الثانوي</option>
                </select>
            </div>

            <div class="form-group">
                <label>المجموعة وموعدها</label>
                <input type="text" id="regGroup" value="مجموعة السبت والثلاثاء" placeholder="المجموعة">
            </div>

            <button class="btn-main" onclick="registerNewStudent()">حفظ وإنشاء الحساب</button>
            <button class="btn-main btn-secondary" onclick="showScreen('screen-welcome')">رجوع</button>
        </div>

        <!-- 3. لوحة تحكم المنصة الداشبورد -->
        <div id="screen-dashboard" class="screen">
            
            <div class="top-navbar">
                <div class="nav-brand">
                    <i class="fa-solid fa-layer-group"></i>
                    <span>MPS Pro</span>
                </div>
                <div class="nav-links">
                    <button class="nav-btn active" onclick="switchSection('profile')">الملف</button>
                    <button class="nav-btn" onclick="switchSection('stats')">المتابعة</button>
                    <button class="nav-btn" id="adminBadgeBtn" style="background: #fef08a; color: #854d0e; display: none;"><i class="fa-solid fa-shield"></i> أدمن</button>
                    <button class="nav-btn" onclick="sendWhatsAppReport()" style="background: #dcfce7; color: #166534;" title="تقرير واتساب"><i class="fa-brands fa-whatsapp"></i></button>
                    <button class="nav-btn" onclick="showScreen('screen-welcome')" style="color: var(--accent-red);"><i class="fa-solid fa-arrow-right-from-bracket"></i></button>
                </div>
            </div>

            <div class="dashboard-content">
                
                <!-- قسم الملف الشخصي -->
                <div id="section-profile">
                    <div class="profile-header-card">
                        <div>
                            <h3 id="uiStudentName" style="font-size: 15px; font-weight: 900;">محمد عنتر</h3>
                            <span style="font-size: 10px; opacity: 0.9;">الكود التعريفي: <span id="uiId">3034</span></span>
                        </div>
                        <i class="fa-solid fa-graduation-cap" style="font-size: 26px;"></i>
                    </div>

                    <div class="digital-id-card">
                        <div class="qr-box"><i class="fa-solid fa-qrcode"></i></div>
                        <div>
                            <h4 style="font-size: 11px; font-weight: bold; color: var(--primary-blue);">بطاقة الحضور والمسح السريع</h4>
                            <p style="font-size: 9px; color: var(--text-muted);">تُستخدم لتسجيل الحضور بباب القاعة إلكترونياً</p>
                        </div>
                    </div>

                    <div class="info-card-item" onclick="editFieldPrompt('teacher', 'اسم المعلم الجديد:')" style="cursor:pointer;" title="انقر للتعديل (أدمن)">
                        <div class="label-side"><i class="fa-solid fa-user-tie"></i><span>المعلم</span></div>
                        <div class="value-side" id="uiTeacher">جلال الاتربي</div>
                    </div>

                    <div class="info-card-item" onclick="editFieldPrompt('phone', 'رقم ولي الأمر الجديد:')" style="cursor:pointer;" title="انقر للتعديل (أدمن)">
                        <div class="label-side"><i class="fa-solid fa-phone"></i><span>هاتف ولي الأمر</span></div>
                        <div class="value-side" id="uiPhone">غير متوفر</div>
                    </div>

                    <div class="info-card-item" onclick="editFieldPrompt('grade', 'الصف الدراسي الجديد:')" style="cursor:pointer;" title="انقر للتعديل (أدمن)">
                        <div class="label-side"><i class="fa-solid fa-users-rectangle"></i><span>الصف الدراسي</span></div>
                        <div class="value-side" id="uiGrade">الصف الأول الثانوي</div>
                    </div>

                    <div class="info-card-item" onclick="editFieldPrompt('group', 'المجموعة الجديدة:')" style="cursor:pointer;" title="انقر للتعديل (أدمن)">
                        <div class="label-side"><i class="fa-solid fa-calendar-days"></i><span>المجموعة</span></div>
                        <div class="value-side" id="uiGroup">مجموعة السبت والثلاثاء</div>
                    </div>

                    <div id="adminDeleteAccountBox" style="margin-top: 10px; display: none;">
                        <button class="btn-main" style="background: var(--accent-red); font-size: 11px; padding: 6px;" onclick="deleteCurrentStudentAccount()"><i class="fa-solid fa-trash"></i> حذف هذا الحساب نهائياً من المنصة</button>
                    </div>
                </div>

                <!-- قسم المتابعة والجداول الشاملة -->
                <div id="section-stats" style="display: none;">
                    <h4 style="font-size: 13px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;">لوحة المتابعة الشاملة للسنتر</h4>
                    
                    <div class="dashboard-grid">
                        <div class="dash-card" onclick="openModal('attendance')">
                            <div class="dash-card-icon"><i class="fa-solid fa-calendar-check"></i></div>
                            <div class="dash-card-title">سجل الحضور</div>
                            <div class="dash-card-value" id="attCount" style="color: var(--accent-green);">لم يُسجل</div>
                        </div>

                        <div class="dash-card" onclick="openModal('absence')">
                            <div class="dash-card-icon" style="background: #fee2e2; color: var(--accent-red);"><i class="fa-solid fa-calendar-xmark"></i></div>
                            <div class="dash-card-title">سجل الغياب والتأخير</div>
                            <div class="dash-card-value" id="absCount" style="color: var(--accent-red);">منتظم</div>
                        </div>

                        <div class="dash-card" onclick="openModal('exams')">
                            <div class="dash-card-icon"><i class="fa-solid fa-star-half-stroke"></i></div>
                            <div class="dash-card-title">الدرجات والتقييم (من 10)</div>
                            <div class="dash-card-value" id="scoreStatus">قيد الانتظار</div>
                        </div>

                        <div class="dash-card" onclick="openModal('homework')">
                            <div class="dash-card-icon" style="background: #fef3c7; color: var(--accent-yellow);"><i class="fa-solid fa-book"></i></div>
                            <div class="dash-card-title">متابعة الواجب</div>
                            <div class="dash-card-value" id="hwStatus">لم يُراجع</div>
                        </div>

                        <div class="dash-card" onclick="openModal('payments')">
                            <div class="dash-card-icon"><i class="fa-solid fa-wallet"></i></div>
                            <div class="dash-card-title">الاشتراك والرسوم</div>
                            <div class="dash-card-value" id="payStatus">لم يتم السداد</div>
                        </div>

                        <div class="dash-card" onclick="openModal('behavior')">
                            <div class="dash-card-icon"><i class="fa-solid fa-face-smile"></i></div>
                            <div class="dash-card-title">السلوك والمشاركة</div>
                            <div class="dash-card-value" id="behStatus">ممتاز</div>
                        </div>
                    </div>

                    <div class="extra-section">
                        <h5>
                            <span><i class="fa-solid fa-calendar-week"></i> جدول الحصص والشرح الأسبوعي</span>
                            <i class="fa-solid fa-pen-to-square" id="editScheduleBtn" style="cursor:pointer; display:none; color:var(--secondary-blue);" onclick="editScheduleData()" title="تعديل الجدول"></i>
                        </h5>
                        <div class="schedule-row"><span>الحصة القادمة:</span> <span id="uiNextClass" style="font-weight: bold; color: var(--primary-blue);">السبت - الحصة الأساسية</span></div>
                        <div class="schedule-row"><span>المحاضرة السابقة:</span> <span id="uiPrevClass" style="color: var(--text-muted);">تم شرح التأسيس</span></div>
                    </div>

                    <div class="extra-section">
                        <h5>
                            <span><i class="fa-solid fa-circle-exclamation"></i> موعد الامتحان القادم</span>
                            <i class="fa-solid fa-pen-to-square" id="editExamDayBtn" style="cursor:pointer; display:none; color:var(--secondary-blue);" onclick="changeExamDay()" title="تغيير يوم الامتحان"></i>
                        </h5>
                        <div class="schedule-row"><span>اليوم والموعد:</span> <span id="uiNextExamDay" style="color: var(--accent-red); font-weight: bold;">الخميس القادم (الساعة 2 ظهراً)</span></div>
                        <div class="schedule-row"><span>حالة النظام:</span> <span style="color: var(--accent-green);">ابتدائي، إعدادي، وثانوي مفعل</span></div>
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
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px; border-bottom: 1px solid #f1f5f9; padding-bottom: 5px;">
                <h3 id="modalTitle" style="font-size: 13px; font-weight: 900; color: var(--primary-blue);">عنوان</h3>
                <i class="fa-solid fa-xmark" style="cursor: pointer; font-size: 15px; color: var(--text-muted);" onclick="closeModalDirect()"></i>
            </div>
            <div style="font-size: 11px; color: var(--text-muted); line-height: 1.4; margin-bottom: 10px;" id="modalBodyContent"></div>
            
            <div class="admin-controls" id="adminControlPanel">
                <p style="font-size: 10px; font-weight: bold; color: var(--primary-blue); margin-bottom: 5px;"><i class="fa-solid fa-lock-open"></i> لوحة تحكم المعلم (كود 2026):</p>
                <div id="adminActionButtons"></div>
            </div>
        </div>
    </div>

    <script>
        let isAdmin = false;
        let currentStudentIndex = 0;

        let savedAccounts = JSON.parse(localStorage.getItem('mps_pro_students')) || [
            { 
                id: 3034, 
                name: "محمد عنتر", 
                teacher: "جلال الاتربي", 
                phone: "201000000000", 
                grade: "الصف الأول الثانوي", 
                group: "مجموعة السبت والثلاثاء", 
                attendance: "لم يُسجل", 
                absence: "منتظم (لا غياب)", 
                payment: "لم يتم السداد", 
                homework: "لم يتم التسليم", 
                behavior: "مشارك بإيجابية وهادئ",
                score: "لم تُسجل بعد",
                nextClass: "السبت - الحصة الأساسية",
                prevClass: "تم شرح التأسيس",
                examDay: "الخميس القادم (الساعة 2 ظهراً)"
            }
        ];

        function renderSavedAccounts() {
            const container = document.getElementById('savedAccountsContainer');
            container.innerHTML = '';
            
            if(savedAccounts.length === 0) {
                container.innerHTML = '<p style="font-size: 10px; color: #cbd5e1;">لا توجد حسابات مسجلة حالياً.</p>';
                return;
            }

            savedAccounts.forEach((acc, index) => {
                container.innerHTML += `
                    <div class="account-card-saved" onclick="loginStudent(${index})">
                        <div style="text-align: right;">
                            <h4 style="font-size: 12px; font-weight: bold;">${acc.name}</h4>
                            <span style="font-size: 9px; color: #94a3b8;">${acc.grade} (كود: ${acc.id})</span>
                        </div>
                        <i class="fa-solid fa-chevron-left" style="font-size: 10px; color: #60a5fa;"></i>
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
            let pass = prompt("أدخل كود الأدمن السري للمستر :");
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
                alert("يرجى إدخال اسم الطالب الكامل!");
                return;
            }

            let newAcc = {
                id: Math.floor(1000 + Math.random() * 9000),
                name: name,
                teacher: teacher || "جلال الاتربي",
                phone: phone || "غير متوفر",
                grade: grade,
                group: group || "مجموعة عامة",
                attendance: "لم يُسجل",
                absence: "منتظم (لا غياب)",
                payment: "لم يتم السداد",
                homework: "لم يتم التسليم",
                behavior: "ممتاز",
                score: "لم تُسجل بعد",
                nextClass: "السبت - الشرح الأساسي",
                prevClass: "تم الشرح",
                examDay: "الخميس القادم"
            };

            savedAccounts.push(newAcc);
            localStorage.setItem('mps_pro_students', JSON.stringify(savedAccounts));
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
            document.getElementById('hwStatus').innerText = acc.homework;
            document.getElementById('behStatus').innerText = acc.behavior;
            document.getElementById('scoreStatus').innerText = acc.score;

            document.getElementById('uiNextClass').innerText = acc.nextClass || "الحصة القادمة";
            document.getElementById('uiPrevClass').innerText = acc.prevClass || "المحاضرة السابقة";
            document.getElementById('uiNextExamDay').innerText = acc.examDay || "الخميس القادم";

            if(isAdmin) {
                document.getElementById('adminBadgeBtn').style.display = 'block';
                document.getElementById('adminDeleteAccountBox').style.display = 'block';
                document.getElementById('editScheduleBtn').style.display = 'inline-block';
                document.getElementById('editExamDayBtn').style.display = 'inline-block';
            } else {
                document.getElementById('adminBadgeBtn').style.display = 'none';
                document.getElementById('adminDeleteAccountBox').style.display = 'none';
                document.getElementById('editScheduleBtn').style.display = 'none';
                document.getElementById('editExamDayBtn').style.display = 'none';
            }

            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById('screen-dashboard').classList.add('active');
            switchSection('profile');
        }

        function switchSection(sectionName) {
            document.querySelectorAll('.nav-btn').forEach(btn => {
                if(btn.id !== 'adminBadgeBtn' && !btn.getAttribute('onclick').includes('WhatsApp')) btn.classList.remove('active');
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

        function editFieldPrompt(field, promptText) {
            if(!isAdmin) return;
            let student = savedAccounts[currentStudentIndex];
            let currentValue = student[field];
            let newVal = prompt(promptText, currentValue);
            if(newVal !== null && newVal.trim() !== "") {
                student[field] = newVal.trim();
                localStorage.setItem('mps_pro_students', JSON.stringify(savedAccounts));
                loginStudent(currentStudentIndex);
                alert("تم تحديث البيانات بنجاح!");
            }
        }

        function changeExamDay() {
            if(!isAdmin) return;
            let student = savedAccounts[currentStudentIndex];
            let newDay = prompt("حدد موعد الامتحان الجديد:", student.examDay);
            if(newDay) {
                student.examDay = newDay;
                document.getElementById('uiNextExamDay').innerText = newDay;
                localStorage.setItem('mps_pro_students', JSON.stringify(savedAccounts));
                alert("تم تحديث موعد الامتحان بنجاح!");
            }
        }

        function editScheduleData() {
            if(!isAdmin) return;
            let student = savedAccounts[currentStudentIndex];
            let nextC = prompt("تعديل محتوى الحصة القادمة:", student.nextClass);
            let prevC = prompt("تعديل محتوى الحصة السابقة:", student.prevClass);
            if(nextC) student.nextClass = nextC;
            if(prevC) student.prevClass = prevC;
            localStorage.setItem('mps_pro_students', JSON.stringify(savedAccounts));
            document.getElementById('uiNextClass').innerText = student.nextClass;
            document.getElementById('uiPrevClass').innerText = student.prevClass;
            alert("تم تحديث جدول الشرح بنجاح!");
        }

        function deleteCurrentStudentAccount() {
            if(!isAdmin) return;
            let confirmDel = confirm("هل أنت متأكد من رغبتك في حذف هذا الحساب نهائياً؟");
            if(confirmDel) {
                savedAccounts.splice(currentStudentIndex, 1);
                localStorage.setItem('mps_pro_students', JSON.stringify(savedAccounts));
                alert("تم مسح الحساب بنجاح.");
                showScreen('screen-welcome');
            }
        }

        function openModal(type) {
            let student = savedAccounts[currentStudentIndex];
            let title = "";
            let body = "";
            let adminActions = "";

            if(type === 'attendance') {
                title = "سجل الحضور بالسنتر";
                body = `حالة الحضور الحالية: <strong>${student.attendance}</strong>`;
                if(isAdmin) {
                    adminActions = `
                        <button class="btn-main" style="padding: 5px; font-size: 10px;" onclick="updateData('attendance', 'حاضر في الموعد')">تسجيل حضور (حاضر)</button>
                        <button class="btn-main" style="padding: 5px; font-size: 10px; background: var(--accent-red); margin-top: 4px;" onclick="updateData('attendance', 'متأخر')">تسجيل تأخير</button>
                    `;
                }
            } else if(type === 'absence') {
                title = "متابعة الغياب";
                body = `سجل الغياب: <strong>${student.absence}</strong>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 5px; font-size: 10px; background: var(--accent-red);" onclick="updateData('absence', 'غياب بدون عذر (إنذار)')">تسجيل غياب عاجل</button>`;
                }
            } else if(type === 'exams') {
                title = "الدرجات والتقييم (من 10)";
                body = `الدرجة الحالية: <strong>${student.score}</strong>.<br><span style="font-size:10px; color:var(--text-muted);">اختر من الدرجات أدناه:</span>`;
                if(isAdmin) {
                    adminActions = `
                        <div style="display:flex; gap:5px; margin-bottom:5px; flex-wrap:wrap; justify-content:center;">
                            <button onclick="updateData('score', '10 / 10 (ممتاز)')" style="background:#10b981; color:white; border:none; padding:4px 8px; border-radius:4px; font-size:10px; cursor:pointer;">10</button>
                            <button onclick="updateData('score', '9 / 10')" style="background:#3b82f6; color:white; border:none; padding:4px 8px; border-radius:4px; font-size:10px; cursor:pointer;">9</button>
                            <button onclick="updateData('score', '8 / 10')" style="background:#3b82f6; color:white; border:none; padding:4px 8px; border-radius:4px; font-size:10px; cursor:pointer;">8</button>
                            <button onclick="updateData('score', '7 / 10')" style="background:#3b82f6; color:white; border:none; padding:4px 8px; border-radius:4px; font-size:10px; cursor:pointer;">7</button>
                            <button onclick="updateData('score', 'أقل من 6')" style="background:#ef4444; color:white; border:none; padding:4px 8px; border-radius:4px; font-size:10px; cursor:pointer;">ضعيف</button>
                        </div>
                        <button class="btn-main" style="padding: 5px; font-size: 10px;" onclick="customScoreInput()">إدخال درجة مخصصة</button>
                    `;
                }
            } else if(type === 'homework') {
                title = "متابعة الواجب المنزلي";
                body = `حالة تسليم الواجب: <strong>${student.homework}</strong>`;
                if(isAdmin) {
                    adminActions = `
                        <button class="btn-main" style="padding: 5px; font-size: 10px;" onclick="updateData('homework', 'تم تسليم الواجب كاملاً')">تحديد (تم التسليم)</button>
                        <button class="btn-main" style="padding: 5px; font-size: 10px; background: var(--accent-red); margin-top: 4px;" onclick="updateData('homework', 'لم يُسلم الواجب')">تحديد (لم يُسلم)</button>
                    `;
                }
            } else if(type === 'payments') {
                title = "إيصال السداد والرسوم الشهرية";
                body = `الحالة المالية: <strong style="color:var(--secondary-blue);">${student.payment}</strong>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 5px; font-size: 10px;" onclick="updateData('payment', 'تم دفع اشتراك الشهر (معتمد)')">إصدار إيصال (تم السداد)</button>`;
                }
            } else if(type === 'behavior') {
                title = "السلوك والمشاركة الصفية";
                body = `ملاحظة السلوك: <strong>${student.behavior}</strong>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 5px; font-size: 10px;" onclick="updateBehaviorNote()">تعديل ملاحظة السلوك</button>`;
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
            } else if(field === 'homework') {
                student.homework = val;
                document.getElementById('hwStatus').innerText = val;
            } else if(field === 'score') {
                student.score = val;
                document.getElementById('scoreStatus').innerText = val;
            }

            localStorage.setItem('mps_pro_students', JSON.stringify(savedAccounts));
            alert("تم التحديث وحفظ البيانات بنجاح!");
            closeModalDirect();
        }

        function customScoreInput() {
            let customVal = prompt("أدخل الدرجة يدوياً (مثال: 9.5 / 10):");
            if(customVal) {
                updateData('score', customVal + " / 10");
            }
        }

        function updateBehaviorNote() {
            let student = savedAccounts[currentScene = currentStudentIndex];
            let note = prompt("أدخل الملاحظة السلوكية الجديدة:", student.behavior);
            if(note) {
                student.behavior = note;
                document.getElementById('behStatus').innerText = note;
                localStorage.setItem('mps_pro_students', JSON.stringify(savedAccounts));
                alert("تم تحديث السلوك بنجاح!");
                closeModalDirect();
            }
        }

        function sendWhatsAppReport() {
            let student = savedAccounts[currentStudentIndex];
            let phone = student.phone !== "غير متوفر" ? student.phone : "";
            
            let reportText = `📌 *منصة MPS Pro التعليمية - تقرير ولي الأمر*%0A` +
                             `-----------------------------------%0A` +
                             `👤 الطالب: *${student.name}*%0A` +
                             `📚 الصف: ${student.grade}%0A` +
                             `-----------------------------------%0A` +
                             `✅ الحضور: ${student.attendance}%0A` +
                             `⚠️ الغياب: ${student.absence}%0A` +
                             `⭐ الدرجة: ${student.score}%0A` +
                             `📖 الواجب: ${student.homework}%0A` +
                             `💳 الاشتراك: ${student.payment}%0A` +
                             `💬 السلوك: ${student.behavior}%0A` +
                             `📅 الامتحان: ${student.examDay}%0A` +
                             `-----------------------------------%0A` +
                             `مع تحيات إدارة السنتر / ${student.teacher}`;
            
            window.open(`https://wa.me/${phone}?text=${reportTest = reportText}`, '_blank');
        }

        renderSavedAccounts();
    </script>
</body>
</html> 
