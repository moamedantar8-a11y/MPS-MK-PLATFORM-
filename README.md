<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mozakra Pro | منصة السنتر التعليمية</title>
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
            background: var(--light-bg);
            color: var(--text-main);
            padding: 20px;
            justify-content: flex-start;
            align-items: center;
            text-align: center;
        }

        .welcome-logo {
            font-size: 50px;
            color: var(--secondary-blue);
            margin-bottom: 5px;
            margin-top: 15px;
        }

        .accounts-list {
            width: 100%;
            margin: 10px 0;
            max-height: 310px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .account-card-saved {
            background: white;
            border: 1px solid #e2e8f0;
            padding: 10px 14px;
            border-radius: 14px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            cursor: pointer;
            transition: var(--transition);
            box-shadow: 0 2px 4px rgba(0,0,0,0.02);
        }

        .account-card-saved:hover {
            border-color: var(--secondary-blue);
            transform: translateY(-2px);
        }

        .register-screen {
            background: linear-gradient(180deg, #1e3a8a 0%, #1e40af 100%);
            color: white;
            padding: 15px;
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
            font-size: 11px;
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
            border-radius: 12px;
            font-size: 12px;
            font-weight: 700;
            cursor: pointer;
            box-shadow: 0 4px 12px rgba(59, 130, 246,.3);
            margin-top: 6px;
            transition: var(--transition);
        }

        .btn-main:hover {
            background: #2563eb;
        }

        .btn-secondary {
            background: transparent;
            color: #cbd5e1;
            border: 1px solid rgba(255,255,255,0.2);
        }

        .top-navbar {
            background: white;
            padding: 8px 10px;
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
            gap: 4px;
            font-size: 12px;
            font-weight: 900;
            color: var(--primary-blue);
        }

        .nav-links {
            display: flex;
            gap: 2px;
        }

        .nav-btn {
            background: #f1f5f9;
            border: none;
            padding: 5px 6px;
            border-radius: 5px;
            font-size: 9px;
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
            padding: 9px 12px;
            border-radius: 8px;
            margin-bottom: 6px;
            display: flex;
            justify-content: space-between;
            align-items: center;
            border: 1px solid #e2e8f0;
            font-size: 11px;
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
            width: 42px;
            height: 42px;
            background: #eff6ff;
            color: var(--secondary-blue);
            display: flex;
            align-items: center;
            justify-content: center;
            border-radius: 8px;
            font-size: 18px;
        }

        .dashboard-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 8px;
            margin-bottom: 12px;
        }

        .dash-card {
            background: white;
            padding: 9px;
            border-radius: 10px;
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            border: 1px solid #e2e8f0;
            cursor: pointer;
            transition: var(--transition);
            min-height: 80px;
        }

        .dash-card:hover {
            border-color: var(--secondary-blue);
            transform: translateY(-2px);
        }

        .dash-card-icon {
            width: 26px;
            height: 26px;
            background: #eff6ff;
            color: var(--secondary-blue);
            border-radius: 50%;
            display: flex;
            align-items: center;
            justify-content: center;
            font-size: 11px;
            margin-bottom: 4px;
        }

        .dash-card-title {
            font-size: 10px;
            font-weight: 700;
            color: var(--text-main);
        }

        .dash-card-value {
            font-size: 10px;
            color: var(--text-muted);
            font-weight: bold;
            margin-top: 2px;
        }

        .community-container {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .chat-box {
            background: white;
            border: 1px solid #e2e8f0;
            border-radius: 10px;
            padding: 10px;
            height: 330px;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .chat-bubble {
            background: #f1f5f9;
            padding: 8px 10px;
            border-radius: 8px;
            font-size: 11px;
            max-width: 85%;
            align-self: flex-start;
            border-right: 3px solid var(--secondary-blue);
        }

        .chat-bubble.mine {
            background: #eff6ff;
            align-self: flex-end;
            border-right: none;
            border-left: 3px solid var(--accent-green);
        }

        .chat-sender {
            font-size: 9px;
            font-weight: bold;
            color: var(--primary-blue);
            margin-bottom: 2px;
            display: flex;
            justify-content: space-between;
        }

        .chat-input-area {
            display: flex;
            gap: 5px;
        }

        .chat-input-area input {
            flex: 1;
            padding: 8px;
            border-radius: 8px;
            border: 1px solid #e2e8f0;
            font-size: 11px;
            outline: none;
        }

        .chat-input-area button {
            background: var(--secondary-blue);
            color: white;
            border: none;
            padding: 0 12px;
            border-radius: 8px;
            cursor: pointer;
            font-size: 12px;
        }

        .extra-section {
            background: white;
            border-radius: 10px;
            padding: 10px 12px;
            margin-bottom: 8px;
            border: 1px solid #e2e8f0;
        }

        .extra-section h5 {
            font-size: 11px;
            color: var(--primary-blue);
            margin-bottom: 6px;
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .schedule-row {
            display: flex;
            justify-content: space-between;
            font-size: 10px;
            padding: 4px 0;
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
            max-width: 320px;
            border-radius: 12px;
            padding: 15px;
            box-shadow: 0 20px 25px -5px rgba(0,0,0,0.2);
            text-align: right;
            max-height: 80vh;
            overflow-y: auto;
        }

        .admin-controls {
            background: #eff6ff;
            border: 1px dashed var(--secondary-blue);
            padding: 8px;
            border-radius: 8px;
            margin-top: 8px;
            display: none;
        }

        .admin-controls.active {
            display: block;
        }

        .app-footer {
            text-align: center;
            padding: 6px;
            font-size: 9px;
            color: var(--text-muted);
            background: white;
            border-top: 1px solid #f1f5f9;
            margin-top: auto;
        }
    </style>
</head>
<body>

    <div class="phone-frame">
        
        <!-- 1. شاشة الترحيب واختيار الحسابات -->
        <div id="screen-welcome" class="screen welcome-screen active">
            <div class="welcome-logo"><i class="fa-solid fa-graduation-cap"></i></div>
            <h2 style="font-size: 18px; font-weight: 900; margin-bottom: 2px;">Mozakra Pro</h2>
            <p style="font-size: 11px; color: var(--text-muted); margin-bottom: 12px;">اختر حسابًا لمتابعة تطبيقك</p>

            <div class="accounts-list" id="savedAccountsContainer"></div>

            <div style="width: 100%; margin-top: auto; padding-bottom: 10px;">
                <button class="btn-main" onclick="showScreen('screen-register')"><i class="fa-solid fa-user-plus"></i> تسجيل الدخول بحساب آخر</button>
                <button class="btn-main" style="background: #0f172a;" onclick="showAdminLogin()"><i class="fa-solid fa-shield-halved"></i> دخول المعلم (أدمن)</button>
            </div>
        </div>

        <!-- 2. شاشة تسجيل طالب جديد -->
        <div id="screen-register" class="screen register-screen">
            <h2 style="font-size: 16px; font-weight: 900; text-align: center; margin-bottom: 2px;">إضافة طالب جديد للسنتر</h2>
            <p style="font-size: 9px; color: #cbd5e1; text-align: center; margin-bottom: 10px;">منصة إدارة المجموعات والطلاب</p>

            <div class="form-group">
                <label>اسم المعلم / المادة</label>
                <input type="text" id="regTeacherName" placeholder="مثال: أ/ تاريخ أو أ/ لغة عربية">
            </div>

            <div class="form-group">
                <label>اسم الطالب الكامل</label>
                <input type="text" id="regStudentName" placeholder="مثال: أحمد محمد">
            </div>

            <div class="form-group">
                <label>رقم هاتف ولي الأمر</label>
                <input type="text" id="regParentPhone" placeholder="010xxxxxxxx">
            </div>

            <div class="form-group">
                <label>الصف الدراسي والمجموعة</label>
                <select id="regGrade">
                    <option value="الصف الأول الإعدادي">الصف الأول الإعدادي</option>
                    <option value="الصف الثاني الإعدادي">الصف الثاني الإعدادي</option>
                    <option value="الصف الثالث الإعدادي">الصف الثالث الإعدادي</option>
                    <option value="الصف الأول الثانوي">الصف الأول الثانوي</option>
                    <option value="الصف الثاني الثانوي">الصف الثاني الثانوي</option>
                    <option value="الصف الثالث الثانوي">الصف الثالث الثانوي</option>
                </select>
            </div>

            <button class="btn-main" onclick="registerNewStudent()">حفظ الحساب</button>
            <button class="btn-main btn-secondary" onclick="showScreen('screen-welcome')">رجوع</button>
        </div>

        <!-- 3. لوحة تحكم المنصة الداشبورد -->
        <div id="screen-dashboard" class="screen">
            
            <div class="top-navbar">
                <div class="nav-brand">
                    <i class="fa-solid fa-landmark"></i>
                    <span>Mozakra</span>
                </div>
                <div class="nav-links">
                    <button class="nav-btn active" onclick="switchSection('profile')">الملف</button>
                    <button class="nav-btn" onclick="switchSection('stats')">المتابعة</button>
                    <button class="nav-btn" onclick="switchSection('community')">المجتمع</button>
                    <button class="nav-btn" id="adminBadgeBtn" style="background: #fef08a; color: #854d0e; display: none;"><i class="fa-solid fa-shield"></i> أدمن</button>
                    <button class="nav-btn" onclick="sendWhatsAppReport()" style="background: #dcfce7; color: #166534;" title="واتساب"><i class="fa-brands fa-whatsapp"></i></button>
                    <button class="nav-btn" onclick="showScreen('screen-welcome')" style="color: var(--accent-red);"><i class="fa-solid fa-arrow-right-from-bracket"></i></button>
                </div>
            </div>

            <div class="dashboard-content">
                
                <!-- أ. قسم الملف الشخصي -->
                <div id="section-profile">
                    <div class="profile-header-card">
                        <div>
                            <h3 id="uiStudentName" style="font-size: 14px; font-weight: 900;">اسم الطالب</h3>
                            <span style="font-size: 10px; opacity: 0.9;">الكود التعريفي: <span id="uiId">0000</span></span>
                        </div>
                        <i class="fa-solid fa-user-graduate" style="font-size: 24px;"></i>
                    </div>

                    <div class="digital-id-card">
                        <div class="qr-box"><i class="fa-solid fa-qrcode"></i></div>
                        <div>
                            <h4 style="font-size: 10px; font-weight: bold; color: var(--primary-blue);">بطاقة حضور السنتر الإلكترونية</h4>
                            <p style="font-size: 9px; color: var(--text-muted);">معلم المادة: <span id="uiTeacher">المعلم</span></p>
                        </div>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-user-tie"></i><span>المعلم والمادة</span></div>
                        <div class="value-side" id="uiTeacherName">المعلم</div>
                    </div>

                    <div class="info-card-item" onclick="editFieldPrompt('phone', 'رقم ولي الأمر الجديد:')" style="cursor:pointer;" title="تعديل">
                        <div class="label-side"><i class="fa-solid fa-phone"></i><span>هاتف ولي الأمر</span></div>
                        <div class="value-side" id="uiPhone">010xxxxxxxx</div>
                    </div>

                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-book-open"></i><span>الصف الدراسي</span></div>
                        <div class="value-side" id="uiGrade">الصف الدراسي</div>
                    </div>

                    <div id="adminDeleteAccountBox" style="margin-top: 10px; display: none;">
                        <button class="btn-main" style="background: var(--accent-red); font-size: 10px; padding: 6px;" onclick="deleteCurrentStudentAccount()"><i class="fa-solid fa-trash"></i> حذف هذا الطالب من المنصة</button>
                    </div>
                </div>

                <!-- ب. قسم المتابعة -->
                <div id="section-stats" style="display: none;">
                    <h4 style="font-size: 12px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;">متابعة أداء الطالب بالسنتر</h4>
                    
                    <div class="dashboard-grid">
                        <div class="dash-card" onclick="openModal('attendance')">
                            <div class="dash-card-icon"><i class="fa-solid fa-calendar-check"></i></div>
                            <div class="dash-card-title">سجل الحضور</div>
                            <div class="dash-card-value" id="attCount" style="color: var(--accent-green);">لم يُسجل</div>
                        </div>

                        <div class="dash-card" onclick="openModal('absence')">
                            <div class="dash-card-icon" style="background: #fee2e2; color: var(--accent-red);"><i class="fa-solid fa-calendar-xmark"></i></div>
                            <div class="dash-card-title">الغياب والتأخير</div>
                            <div class="dash-card-value" id="absCount" style="color: var(--accent-red);">منتظم</div>
                        </div>

                        <div class="dash-card" onclick="openModal('exams')">
                            <div class="dash-card-icon"><i class="fa-solid fa-star-half-stroke"></i></div>
                            <div class="dash-card-title">درجات الاختبار (من 10)</div>
                            <div class="dash-card-value" id="scoreStatus">قيد الانتظار</div>
                        </div>

                        <div class="dash-card" onclick="openModal('homework')">
                            <div class="dash-card-icon" style="background: #fef3c7; color: var(--accent-yellow);"><i class="fa-solid fa-book"></i></div>
                            <div class="dash-card-title">حل الواجب</div>
                            <div class="dash-card-value" id="hwStatus">لم يُراجع</div>
                        </div>

                        <div class="dash-card" onclick="openModal('payments')">
                            <div class="dash-card-icon"><i class="fa-solid fa-wallet"></i></div>
                            <div class="dash-card-title">الرسوم الشهرية</div>
                            <div class="dash-card-value" id="payStatus">لم يتم السداد</div>
                        </div>

                        <div class="dash-card" onclick="openModal('behavior')">
                            <div class="dash-card-icon"><i class="fa-solid fa-face-smile"></i></div>
                            <div class="dash-card-title">السلوك والمشاركة</div>
                            <div class="dash-card-value" id="behStatus">ممتاز</div>
                        </div>
                    </div>

                    <div class="extra-section">
                        <h5><span><i class="fa-solid fa-circle-exclamation"></i> تنبيهات السنتر</span></h5>
                        <div class="schedule-row"><span>حالة النظام:</span> <span style="color: var(--accent-green);">متعدد المعلمين والطلاب</span></div>
                    </div>
                </div>

                <!-- ج. قسم مجتمع السنتر -->
                <div id="section-community" style="display: none;">
                    <div class="community-container">
                        <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 2px;">
                            <h4 style="font-size: 11px; font-weight: 900; color: var(--primary-blue);"><i class="fa-solid fa-comments"></i> مجتمع طلاب السنتر</h4>
                            <span style="font-size: 9px; color: var(--text-muted);">اسأل واستفسر عن الواجب</span>
                        </div>

                        <div class="chat-box" id="communityChatBox"></div>

                        <div class="chat-input-area">
                            <input type="text" id="chatInputMessage" placeholder="اكتب سؤالك أو استفسارك عن الدرس..." onkeypress="checkEnterChat(event)">
                            <button onclick="sendChatMessage()"><i class="fa-solid fa-paper-plane"></i></button>
                        </div>
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
                <h3 id="modalTitle" style="font-size: 12px; font-weight: 900; color: var(--primary-blue);">عنوان</h3>
                <i class="fa-solid fa-xmark" style="cursor: pointer; font-size: 14px; color: var(--text-muted);" onclick="closeModalDirect()"></i>
            </div>
            <div style="font-size: 10px; color: var(--text-muted); line-height: 1.4; margin-bottom: 8px;" id="modalBodyContent"></div>
            
            <div class="admin-controls" id="adminControlPanel">
                <p style="font-size: 9px; font-weight: bold; color: var(--primary-blue); margin-bottom: 4px;"><i class="fa-solid fa-lock-open"></i> لوحة تحكم المعلم:</p>
                <div id="adminActionButtons"></div>
            </div>
        </div>
    </div>

    <script>
        let isAdmin = false;
        let currentStudentIndex = 0;

        let savedAccounts = JSON.parse(localStorage.getItem('mozakra_pro_students')) || [];

        let communityMessages = JSON.parse(localStorage.getItem('mozakra_pro_chat')) || [
            { sender: "النظام", text: "أهلاً بجميع الطلاب في منصة Mozakra Pro.", time: "اليوم" }
        ];

        function renderSavedAccounts() {
            const container = document.getElementById('savedAccountsContainer');
            container.innerHTML = '';
            
            if(savedAccounts.length === 0) {
                container.innerHTML = '<p style="font-size: 11px; color: var(--text-muted); text-align: center; margin-top: 20px;">لا توجد حسابات مسجلة حالياً.<br>قم بتسجيل حساب جديد بالأسفل.</p>';
                return;
            }

            savedAccounts.forEach((acc, index) => {
                container.innerHTML += `
                    <div class="account-card-saved" onclick="loginStudent(${index})">
                        <div style="text-align: right; flex: 1;">
                            <h4 style="font-size: 11px; font-weight: bold; color: var(--text-main);">${acc.teacher}</h4>
                            <span style="font-size: 10px; color: var(--secondary-blue);">00${acc.id}</span>
                            <div style="font-size: 10px; font-weight: bold; color: var(--text-muted);">${acc.name}</div>
                        </div>
                        <div style="display: flex; align-items: center; gap: 8px;">
                            <button onclick="event.stopPropagation(); deleteAccount(${index})" style="background: #fee2e2; color: var(--accent-red); border: none; width: 28px; height: 28px; border-radius: 50%; cursor: pointer; display: flex; align-items: center; justify-content: center;" title="حذف الحساب"><i class="fa-solid fa-trash" style="font-size: 11px;"></i></button>
                            <div style="width: 34px; height: 34px; background: var(--secondary-blue); color: white; border-radius: 50%; display: flex; align-items: center; justify-content: center; font-weight: bold; font-size: 12px;">${acc.name.charAt(0)}</div>
                        </div>
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
            let pass = prompt("أدخل كود الأدمن السري للمعلم (2026):");
            if(pass === "2026") {
                if(savedAccounts.length === 0) {
                    alert("لا توجد حسابات طلاب مسجلة حالياً ليقوم الأدمن بإدارتها. يرجى تسجيل طالب أولاً.");
                    showScreen('screen-register');
                    return;
                }
                isAdmin = true;
                alert("تم تفعيل وضع المعلم (أدمن). اختر الحساب المطلوب إدارته ومراجعته من القائمة.");
                showScreen('screen-welcome');
            } else if(pass !== null) {
                alert("الكود غير صحيح!");
            }
        }

        function deleteAccount(index) {
            if(confirm("هل أنت متأكد من حذف هذا الحساب نهائياً؟")) {
                savedAccounts.splice(index, 1);
                localStorage.setItem('mozakra_pro_students', JSON.stringify(savedAccounts));
                renderSavedAccounts();
            }
        }

        function registerNewStudent() {
            let teacher = document.getElementById('regTeacherName').value.trim();
            let name = document.getElementById('regStudentName').value.trim();
            let phone = document.getElementById('regParentPhone').value.trim();
            let grade = document.getElementById('regGrade').value;

            if(!name || !teacher) {
                alert("يرجى إدخال اسم المعلم وا اسم الطالب الكامل!");
                return;
            }

            let newAcc = {
                id: Math.floor(100000 + Math.random() * 900000),
                teacher: teacher,
                name: name,
                phone: phone || "غير متوفر",
                grade: grade,
                attendance: "لم يُسجل",
                absence: "منتظم",
                payment: "لم يتم السداد",
                homework: "لم يُسلم",
                behavior: "ممتاز",
                score: "لم تُسجل"
            };

            savedAccounts.push(newAcc);
            localStorage.setItem('mozakra_pro_students', JSON.stringify(savedAccounts));
            loginStudent(savedAccounts.length - 1);
        }

        function loginStudent(index) {
            currentStudentIndex = index;
            let acc = savedAccounts[index];

            document.getElementById('uiStudentName').innerText = acc.name;
            document.getElementById('uiId').innerText = acc.id;
            document.getElementById('uiTeacher').innerText = acc.teacher;
            document.getElementById('uiTeacherName').innerText = acc.teacher;
            document.getElementById('uiPhone').innerText = acc.phone;
            document.getElementById('uiGrade').innerText = acc.grade;

            document.getElementById('attCount').innerText = acc.attendance;
            document.getElementById('absCount').innerText = acc.absence;
            document.getElementById('payStatus').innerText = acc.payment;
            document.getElementById('hwStatus').innerText = acc.homework;
            document.getElementById('behStatus').innerText = acc.behavior;
            document.getElementById('scoreStatus').innerText = acc.score;

            if(isAdmin) {
                document.getElementById('adminBadgeBtn').style.display = 'block';
                document.getElementById('adminDeleteAccountBox').style.display = 'block';
            } else {
                document.getElementById('adminBadgeBtn').style.display = 'none';
                document.getElementById('adminDeleteAccountBox').style.display = 'none';
            }

            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById('screen-dashboard').classList.add('active');
            switchSection('profile');
            renderCommunityChat();
        }

        function switchSection(sectionName) {
            document.querySelectorAll('.nav-btn').forEach(btn => {
                if(btn.id !== 'adminBadgeBtn' && !btn.getAttribute('onclick').includes('WhatsApp')) btn.classList.remove('active');
            });
            event.target.classList.add('active');

            document.getElementById('section-profile').style.display = (sectionName === 'profile') ? 'block' : 'none';
            document.getElementById('section-stats').style.display = (sectionName === 'stats') ? 'block' : 'none';
            document.getElementById('section-community').style.display = (sectionName === 'community') ? 'block' : 'none';
            
            if(sectionName === 'community') {
                renderCommunityChat();
            }
        }

        function renderCommunityChat() {
            let chatBox = document.getElementById('communityChatBox');
            chatBox.innerHTML = '';
            
            let currentStudentName = savedAccounts.length > 0 ? savedAccounts[currentStudentIndex].name : "";
            let teacherName = savedAccounts.length > 0 ? savedAccounts[currentStudentIndex].teacher : "المعلم";
            let displayName = isAdmin ? `${teacherName} (المعلم)` : currentStudentName;

            communityMessages.forEach(msg => {
                let isMine = (msg.sender === displayName || (!isAdmin && msg.sender === currentStudentName));
                chatBox.innerHTML += `
                    <div class="chat-bubble ${isMine ? 'mine' : ''}">
                        <div class="chat-sender"><span>${msg.sender}</span> <span style="font-size:7px; color:#94a3b8;">${msg.time}</span></div>
                        <div>${msg.text}</div>
                    </div>
                `;
            });
            chatBox.scrollTop = chatBox.scrollHeight;
        }

        function sendChatMessage() {
            let input = document.getElementById('chatInputMessage');
            let text = input.value.trim();
            if(!text) return;

            let currentStudentName = savedAccounts[currentStudentIndex].name;
            let teacherName = savedAccounts[currentStudentIndex].teacher;
            let senderName = isAdmin ? teacherName : currentStudentName;

            communityMessages.push({
                sender: senderName,
                text: text,
                time: "الآن"
            });

            localStorage.setItem('mozakra_pro_chat', JSON.stringify(communityMessages));
            input.value = '';
            renderCommunityChat();
        }

        function checkEnterChat(e) {
            if(e.key === 'Enter') sendChatMessage();
        }

        function editFieldPrompt(field, promptText) {
            if(!isAdmin) return;
            let student = savedAccounts[currentStudentIndex];
            let newVal = prompt(promptText, student[field]);
            if(newVal !== null && newVal.trim() !== "") {
                student[field] = newVal.trim();
                localStorage.setItem('mozakra_pro_students', JSON.stringify(savedAccounts));
                loginStudent(currentStudentIndex);
                alert("تم التحديث بنجاح!");
            }
        }

        function deleteCurrentStudentAccount() {
            if(!isAdmin) return;
            if(confirm("هل أنت متأكد من حذف هذا الطالب؟")) {
                savedAccounts.splice(currentStudentIndex, 1);
                localStorage.setItem('mozakra_pro_students', JSON.stringify(savedAccounts));
                alert("تم الحذف.");
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
                body = `الحالة: <strong>${student.attendance}</strong>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 5px; font-size: 10px;" onclick="updateData('attendance', 'حاضر في الموعد')">تسجيل حضور (حاضر)</button>`;
                }
            } else if(type === 'absence') {
                title = "متابعة الغياب";
                body = `الحالة: <strong>${student.absence}</strong>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 5px; font-size: 10px; background: var(--accent-red);" onclick="updateData('absence', 'غياب بدون عذر')">تسجيل غياب</button>`;
                }
            } else if(type === 'exams') {
                title = "درجات الاختبارات الشهرية (من 10)";
                body = `الدرجة الحالية: <strong>${student.score}</strong>`;
                if(isAdmin) {
                    adminActions = `
                        <div style="display:flex; gap:4px; margin-bottom:5px; justify-content:center;">
                            <button onclick="updateData('score', '10 / 10')" style="background:#10b981; color:white; border:none; padding:4px 8px; border-radius:4px; font-size:10px; cursor:pointer;">10</button>
                            <button onclick="updateData('score', '9 / 10')" style="background:#3b82f6; color:white; border:none; padding:4px 8px; border-radius:4px; font-size:10px; cursor:pointer;">9</button>
                            <button onclick="updateData('score', '8 / 10')" style="background:#3b82f6; color:white; border:none; padding:4px 8px; border-radius:4px; font-size:10px; cursor:pointer;">8</button>
                        </div>
                    `;
                }
            } else if(type === 'homework') {
                title = "متابعة الواجب المنزلي";
                body = `حالة الواجب: <strong>${student.homework}</strong>`;
                if(isAdmin) {
                    adminActions = `
                        <button class="btn-main" style="padding: 5px; font-size: 10px;" onclick="updateData('homework', 'تم تسليم الواجب')">تسجيل (تم التسليم)</button>
                        <button class="btn-main" style="padding: 5px; font-size: 10px; background: var(--accent-red); margin-top: 4px;" onclick="updateData('homework', 'لم يُسلم الواجب')">تسجيل (لم يُسلم)</button>
                    `;
                }
            } else if(type === 'payments') {
                title = "الاشتراك والرسوم الشهرية";
                body = `الحالة المالية: <strong style="color:var(--secondary-blue);">${student.payment}</strong>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 5px; font-size: 10px;" onclick="updateData('payment', 'تم دفع اشتراك الشهر')">إصدار إيصال سداد</button>`;
                }
            } else if(type === 'behavior') {
                title = "السلوك والمشاركة";
                body = `الملاحظة: <strong>${student.behavior}</strong>`;
                if(isAdmin) {
                    adminActions = `<button class="btn-main" style="padding: 5px; font-size: 10px;" onclick="editFieldPrompt('behavior', 'تعديل السلوك:')">تعديل ملاحظة السلوك</button>`;
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
            student[field] = val;
            if(field === 'attendance') document.getElementById('attCount').innerText = val;
            if(field === 'absence') document.getElementById('absCount').innerText = val;
            if(field === 'payment') document.getElementById('payStatus').innerText = val;
            if(field === 'homework') document.getElementById('hwStatus').innerText = val;
            if(field === 'score') document.getElementById('scoreStatus').innerText = val;

            localStorage.setItem('mozakra_pro_students', JSON.stringify(savedAccounts));
            alert("تم التحديث بنجاح!");
            closeModalDirect();
        }

        function sendWhatsAppReport() {
            let student = savedAccounts[currentStudentIndex];
            let phone = student.phone !== "غير متوفر" ? student.phone : "";
            let reportText = `📌 *منصة Mozakra Pro التعليمية*%0A` +
                             `👨‍🏫 المعلم: *${student.teacher}*%0A` +
                             `👤 الطالب: *${student.name}*%0A` +
                             `📚 الصف: ${student.grade}%0A` +
                             `------------------%0A` +
                             `✅ الحضور: ${student.attendance}%0A` +
                             `⚠️ الغياب: ${student.absence}%0A` +
                             `⭐ الدرجة: ${student.score}%0A` +
                             `📖 الواجب: ${student.homework}%0A` +
                             `💳 الاشتراك: ${student.payment}%0A` +
                             `💬 السلوك: ${student.behavior}%0A` +
                             `------------------%0A` +
                             `إدارة المنصة التعليمية`;
            
            window.open(`https://wa.me/${phone}?text=${reportText}`, '_blank');
        }

        renderSavedAccounts();
    </script>
</body>
</html> 
