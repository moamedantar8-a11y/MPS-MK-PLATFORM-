<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Mozakra | مذاكرة - المنصة التعليمية المتكاملة</title>
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

        .welcome-screen { background: var(--light-bg); padding: 20px; text-align: center;[cite: 4]}
        .welcome-logo { font-size: 50px; color: var(--secondary-blue); margin-bottom: 5px; margin-top: 15px;[cite: 4]}
        .accounts-list { width: 100%; margin: 10px 0; max-height: 220px; overflow-y: auto; display: flex; flex-direction: column; gap: 8px;[cite: 4]}
        .account-card-saved { background: white; border: 1px solid #e2e8f0; padding: 10px 14px; border-radius: 14px; display: flex; justify-content: space-between; align-items: center; cursor: pointer; transition: var(--transition);[cite: 4]}
        .account-card-saved:hover { border-color: var(--secondary-blue); transform: translateY(-2px);[cite: 4]}
        
        .register-screen { background: linear-gradient(180deg, #1e3a8a 0%, #1e40af 100%); color: white; padding: 15px; justify-content: center; align-items: center;[cite: 4]}
        .form-group { width: 100%; margin-bottom: 8px; text-align: right;[cite: 4]}
        .form-group label { font-size: 11px; color: #cbd5e1; display: block; margin-bottom: 2px;[cite: 4]}
        .form-group input, .form-group select, .form-group textarea { width: 100%; padding: 8px 10px; border-radius: 8px; border: 1px solid rgba(255,255,255,0.2); background: rgba(255,255,255,0.08); color: white; font-size: 11px; outline: none;[cite: 4]}
        .form-group select option { background: #1e3a8a; color: white;[cite: 4]}
        
        .btn-main { width: 100%; background: var(--secondary-blue); color: white; border: none; padding: 10px; border-radius: 12px; font-size: 12px; font-weight: 700; cursor: pointer; box-shadow: 0 4px 12px rgba(59, 130, 246,.3); margin-top: 6px; transition: var(--transition);[cite: 4]}
        .btn-main:hover { background: #2563eb;[cite: 4]}
        .btn-secondary { background: transparent; color: #cbd5e1; border: 1px solid rgba(255,255,255,0.2);[cite: 4]}
        
        .top-navbar { background: white; padding: 6px 8px; display: flex; justify-content: space-between; align-items: center; box-shadow: 0 2px 4px rgba(0,0,0,0.03); position: sticky; top: 0; z-index: 10;[cite: 4]}
        .nav-brand { display: flex; align-items: center; gap: 4px; font-size: 10px; font-weight: 900; color: var(--primary-blue);[cite: 4]}
        .nav-links { display: flex; gap: 2px; flex-wrap: wrap; justify-content: flex-end;[cite: 4]}
        .nav-btn { background: #f1f5f9; border: none; padding: 4px 6px; border-radius: 5px; font-size: 8px; font-weight: 600; color: var(--text-muted); cursor: pointer; transition: var(--transition);[cite: 4]}
        .nav-btn.active, .nav-btn:hover { background: var(--secondary-blue); color: white;[cite: 4]}
        
        .dashboard-content { padding: 12px;[cite: 4]}
        .profile-header-card { background: linear-gradient(135deg, var(--secondary-blue), var(--primary-blue)); color: white; padding: 12px; border-radius: 12px; display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px;[cite: 4]}
        .info-card-item { background: white; padding: 9px 12px; border-radius: 8px; margin-bottom: 6px; display: flex; justify-content: space-between; align-items: center; border: 1px solid #e2e8f0; font-size: 11px;[cite: 4]}
        .info-card-item .label-side { display: flex; align-items: center; gap: 8px; color: var(--text-muted);[cite: 4]}
        .info-card-item .value-side { font-weight: 700; color: var(--text-main);[cite: 4]}
        .info-card-item i { color: var(--secondary-blue);[cite: 4]}
        
        .digital-id-card { background: white; border-radius: 10px; padding: 10px; margin-bottom: 10px; border: 1px solid #e2e8f0; display: flex; align-items: center; gap: 10px;[cite: 4]}
        .qr-box { width: 42px; height: 42px; background: #eff6ff; color: var(--secondary-blue); display: flex; align-items: center; justify-content: center; border-radius: 8px; font-size: 18px;[cite: 4]}
        
        .dashboard-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-bottom: 12px;[cite: 4]}
        .dash-card { background: white; padding: 10px; border-radius: 10px; display: flex; flex-direction: column; justify-content: space-between; border: 1px solid #e2e8f0; cursor: pointer; transition: var(--transition); min-height: 90px;[cite: 4]}
        .dash-card:hover { border-color: var(--secondary-blue); transform: translateY(-2px);[cite: 4]}
        .dash-card-icon { width: 28px; height: 28px; background: #eff6ff; color: var(--secondary-blue); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 11px; margin-bottom: 6px;[cite: 4]}
        .dash-card-title { font-size: 10px; font-weight: 700; color: var(--text-main);[cite: 4]}
        .dash-card-value { font-size: 10px; color: var(--text-muted); font-weight: bold; margin-top: 2px;[cite: 4]}
        
        /* تصميم صندوق الدردشة مع أزرار التعديل والحذف */
        .chat-box { background: white; border: 1px solid #e2e8f0; border-radius: 10px; padding: 10px; height: 260px; overflow-y: auto; display: flex; flex-direction: column; gap: 8px;[cite: 4]}
        .chat-bubble { background: #f1f5f9; padding: 8px 10px; border-radius: 8px; font-size: 11px; max-width: 85%; align-self: flex-start; border-right: 3px solid var(--secondary-blue); position: relative;[cite: 4]}
        .chat-bubble.mine { background: #eff6ff; align-self: flex-end; border-right: none; border-left: 3px solid var(--accent-green);[cite: 4]}
        .chat-sender { font-size: 9px; font-weight: bold; color: var(--primary-blue); margin-bottom: 2px; display: flex; justify-content: space-between; align-items: center;[cite: 4]}
        .chat-actions-btns { display: flex; gap: 6px; font-size: 9px; margin-top: 4px; border-top: 1px solid rgba(0,0,0,0.05); padding-top: 3px; }
        .chat-actions-btns button { background: none; border: none; cursor: pointer; font-size: 9px; font-weight: bold; display: flex; align-items: center; gap: 2px; }
        .btn-edit-msg { color: var(--secondary-blue); }
        .btn-del-msg { color: var(--accent-red); }

        .chat-input-area { display: flex; gap: 5px; margin-top: 8px;[cite: 4]}
        .chat-input-area input { flex: 1; padding: 8px; border-radius: 8px; border: 1px solid #e2e8f0; font-size: 11px; outline: none; background: white; color: #1e293b;[cite: 4]}
        .chat-input-area button { background: var(--secondary-blue); color: white; border: none; padding: 0 12px; border-radius: 8px; cursor: pointer; font-size: 12px;[cite: 4]}
        
        .media-card { background: white; border: 1px solid #e2e8f0; border-radius: 10px; padding: 10px; margin-bottom: 8px; display: flex; align-items: center; justify-content: space-between;[cite: 4]}
        .media-info { display: flex; align-items: center; gap: 10px;[cite: 4]}
        .media-icon { width: 35px; height: 35px; background: #fee2e2; color: var(--accent-red); border-radius: 8px; display: flex; align-items: center; justify-content: center; font-size: 16px;[cite: 4]}
        .media-icon.video { background: #dbeafe; color: var(--secondary-blue);[cite: 4]}
        .media-btn { background: #eff6ff; color: var(--secondary-blue); border: 1px solid #bfdbfe; padding: 6px 10px; border-radius: 8px; font-size: 10px; font-weight: bold; text-decoration: none; display: flex; align-items: center; gap: 4px;[cite: 4]}
        
        .empty-notice { text-align: center; font-size: 10px; color: var(--text-muted); padding: 20px; background: white; border: 1px dashed #cbd5e1; border-radius: 10px; margin-top: 8px;[cite: 4]}

        .admin-upload-box { background: #eff6ff; border: 1px dashed var(--secondary-blue); padding: 10px; border-radius: 10px; margin-bottom: 10px; display: none;[cite: 4]}
        .admin-upload-box.active { display: block;[cite: 4]}

        .post-card { background: white; border: 1px solid #e2e8f0; border-radius: 10px; padding: 10px; margin-bottom: 10px;[cite: 4]}
        .post-header { display: flex; justify-content: space-between; align-items: center; margin-bottom: 6px; font-size: 10px; font-weight: bold; color: var(--primary-blue);[cite: 4]}
        .post-body { font-size: 11px; color: var(--text-main); margin-bottom: 8px; line-height: 1.4;[cite: 4]}
        .post-actions { display: flex; gap: 10px; border-top: 1px solid #f1f5f9; padding-top: 6px; font-size: 10px; color: var(--text-muted); align-items: center;[cite: 4]}
        .post-actions button { background: none; border: none; cursor: pointer; color: var(--text-muted); font-size: 10px; display: flex; align-items: center; gap: 4px; font-weight: bold;[cite: 4]}
        .post-actions button:hover { color: var(--secondary-blue);[cite: 4]}
        .comments-section { margin-top: 6px; border-top: 1px dashed #f1f5f9; padding-top: 6px; display: flex; flex-direction: column; gap: 4px;[cite: 4]}
        .comment-item { background: #f8fafc; padding: 5px 8px; border-radius: 6px; font-size: 10px;[cite: 4]}

        .faq-item { background: white; border: 1px solid #e2e8f0; border-radius: 8px; margin-bottom: 6px; overflow: hidden;[cite: 4]}
        .faq-question { padding: 10px; font-size: 11px; font-weight: bold; color: var(--primary-blue); cursor: pointer; display: flex; justify-content: space-between; align-items: center; background: #fff;[cite: 4]}
        .faq-answer { padding: 10px; font-size: 10px; color: var(--text-muted); background: #f8fafc; border-top: 1px solid #f1f5f9; display: none; line-height: 1.4;[cite: 4]}
        .faq-item.active .faq-answer { display: block;[cite: 4]}

        .modal-overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); display: none; justify-content: center; align-items: center; z-index: 100; padding: 15px;[cite: 4]}
        .modal-card { background: white; width: 100%; max-width: 320px; border-radius: 12px; padding: 15px; box-shadow: 0 20px 25px -5px rgba(0,0,0,0.2); text-align: right; max-height: 80vh; overflow-y: auto;[cite: 4]}
        .admin-controls { background: #eff6ff; border: 1px dashed var(--secondary-blue); padding: 8px; border-radius: 8px; margin-top: 8px; display: none;[cite: 4]}
        .admin-controls.active { display: block;[cite: 4]}
        .app-footer { text-align: center; padding: 6px; font-size: 9px; color: var(--text-muted); background: white; border-top: 1px solid #f1f5f9; margin-top: auto;[cite: 4]}

        .quiz-container-ui { background: white; border-radius: 12px; padding: 15px; box-shadow: 0 4px 6px rgba(0,0,0,0.05); margin-top: 10px;[cite: 4]}
        .quiz-container-ui ul { list-style: none; padding: 0; margin: 0;[cite: 4]}
        .quiz-container-ui ul li { margin: 8px 0;[cite: 4]}
        .quiz-container-ui label { cursor: pointer; display: block; padding: 12px; background: #f9f9f9; border: 1px solid #e0e0e0; border-radius: 8px; font-size: 12px;[cite: 4]}
        .quiz-container-ui input[type="radio"] { display: none;[cite: 4]}
        .quiz-container-ui input[type="radio"]:checked + label { background: var(--secondary-blue); color: white; border-color: var(--primary-blue); font-weight: bold;[cite: 4]}
    </style>
</head>
<body>

    <div class="phone-frame">
        
        <!-- 1. شاشة الترحيب -->
        <div id="screen-welcome" class="screen welcome-screen active">
            <div class="welcome-logo"><i class="fa-solid fa-graduation-cap"></i></div>
            <h2 style="font-size: 18px; font-weight: 900; margin-bottom: 2px;">Mozakra | مذاكرة</h2>
            <p style="font-size: 11px; color: var(--text-muted); margin-bottom: 10px;">اختر حسابك المسجل للمتابعة</p>

            <div class="accounts-list" id="savedAccountsContainer"></div>

            <div style="width: 100%; margin-top: auto; padding-bottom: 10px;">
                <button class="btn-main" onclick="showScreen('screen-register')"><i class="fa-solid fa-user-plus"></i> تسجيل طالب جديد</button>
                <button class="btn-main" style="background: #0f172a;" onclick="showTeacherLoginModal()"><i class="fa-solid fa-chalkboard-user"></i> دخول المعلم (لوحة التحكم)</button>
            </div>
        </div>

        <!-- 2. شاشة تسجيل طالب جديد -->
        <div id="screen-register" class="screen register-screen">
            <h2 style="font-size: 14px; font-weight: 900; text-align: center; margin-bottom: 2px;">تسجيل طالب جديد</h2>
            <p style="font-size: 9px; color: #cbd5e1; text-align: center; margin-bottom: 8px;">اختر الصف والمعلم بدقة</p>
            <div class="form-group">
                <label>الصف الدراسي</label>
                <select id="regGrade">
                    <option value="الصف الثالث الإعدادي">الصف الثالث الإعدادي (دراسات)</option>
                    <option value="الصف الأول الثانوي">الصف الأول الثانوي</option>
                </select>
            </div>
            <div class="form-group">
                <label>اختر المعلم والمادة</label>
                <select id="regTeacherSelect" onchange="updateGroupsDropdown()">
                    <option value="مستر جلال الأتربي (دراسات اجتماعية)">مستر جلال الأتربي (دراسات اجتماعية)</option>
                    <option value="مستر سلمان زاكي (رياضيات)">مستر سلمان زاكي (رياضيات)</option>
                    <option value="مستر أحمد عبدالمطلب (لغة عربية)">مستر أحمد عبدالمطلب (لغة عربية)</option>
                    <option value="مستر نجيب رسلان (لغة إنجليزية)">مستر نجيب رسلان (لغة إنجليزية)</option>
                </select>
            </div>
            <div class="form-group">
                <label>اختر مجموعة المادة</label>
                <select id="regGroup"></select>
            </div>
            <div class="form-group">
                <label>اسم الطالب الكامل</label>
                <input type="text" id="regStudentName" placeholder="مثال: محمد عنتر">
            </div>
            <div class="form-group">
                <label>رقم هاتف ولي الأمر</label>
                <input type="text" id="regParentPhone" placeholder="010xxxxxxxx">
            </div>
            <button class="btn-main" onclick="registerNewStudent()">حفظ الحساب والانضمام</button>
            <button class="btn-main btn-secondary" onclick="showScreen('screen-welcome')">رجوع</button>
        </div>

        <!-- 3. لوحة تحكم المنصة الاحترافية -->
        <div id="screen-dashboard" class="screen">
            <div class="top-navbar">
                <div class="nav-brand"><i class="fa-solid fa-landmark"></i><span>Mozakra</span></div>
                <div class="nav-links">
                    <button class="nav-btn active" onclick="switchSection('profile')">الملف</button>
                    <button class="nav-btn" onclick="switchSection('stats')">المتابعة</button>
                    <button class="nav-btn" onclick="switchSection('books')">الكتب</button>
                    <button class="nav-btn" onclick="switchSection('videos')">الفيديوهات</button>
                    <button class="nav-btn" onclick="switchSection('ads')">الإعلانات</button>
                    <button class="nav-btn" onclick="switchSection('support')">الدعم</button>
                    <button class="nav-btn" onclick="switchSection('faq')">الأسئلة</button>
                    <button class="nav-btn" onclick="switchSection('community')">المجتمع</button>
                    <button class="nav-btn" id="teacherBadgeBtn" style="background: #fef08a; color: #854d0e; display: none;"><i class="fa-solid fa-chalkboard"></i> أدمن</button>
                    <button class="nav-btn" onclick="showScreen('screen-welcome')" style="color: var(--accent-red);"><i class="fa-solid fa-arrow-right-from-bracket"></i></button>
                </div>
            </div>

            <div class="dashboard-content">
                <!-- أ. الملف الشخصي مع زر حذف الحساب -->
                <div id="section-profile">
                    <div class="profile-header-card">
                        <div>
                            <h3 id="uiStudentName" style="font-size: 13px; font-weight: 900;">اسم الطالب</h3>
                            <span style="font-size: 9px; opacity: 0.9;">الكود: <span id="uiId">0000</span> | المجموعة: <span id="uiGroupBadge">مجموعة</span></span>
                        </div>
                        <i class="fa-solid fa-user-graduate" style="font-size: 22px;"></i>
                    </div>
                    <div class="digital-id-card">
                        <div class="qr-box"><i class="fa-solid fa-qrcode"></i></div>
                        <div>
                            <h4 style="font-size: 10px; font-weight: bold; color: var(--primary-blue);">بطاقة حضور السنتر الإلكترونية</h4>
                            <p style="font-size: 9px; color: var(--text-muted);">المعلم: <span id="uiTeacher">المعلم</span></p>
                        </div>
                    </div>
                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-user-tie"></i><span>المعلم المسؤول</span></div>
                        <div class="value-side" id="uiTeacherName">المعلم</div>
                    </div>
                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-users"></i><span>المجموعة والموعد</span></div>
                        <div class="value-side" id="uiGroup">المجموعة</div>
                    </div>
                    <div class="info-card-item">
                        <div class="label-side"><i class="fa-solid fa-book-open"></i><span>الصف الدراسي</span></div>
                        <div class="value-side" id="uiGrade">الصف الدراسي</div>
                    </div>
                    
                    <button class="btn-main" style="background: #fee2e2; color: var(--accent-red); border: 1px solid #fca5a5; margin-top: 15px;" onclick="deleteCurrentAccount()">
                        <i class="fa-solid fa-trash-can"></i> حذف هذا الحساب نهائياً
                    </button>
                </div>

                <!-- ب. المتابعة والدرجات -->
                <div id="section-stats" style="display: none;">
                    <h4 style="font-size: 11px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;">متابعة أداء الطالب والأنشطة</h4>
                    <div class="dashboard-grid">
                        <div class="dash-card" id="challengeCardBtn" style="background: #eff6ff; border-color: var(--secondary-blue);" onclick="openChallengeGame()">
                            <div class="dash-card-icon" style="background: var(--secondary-blue); color: white;"><i class="fa-solid fa-gamepad"></i></div>
                            <div class="dash-card-title" style="color: var(--primary-blue);">مركز التحدي</div>
                            <div class="dash-card-value" style="color: var(--secondary-blue);">50 سؤال (3 إعدادي)</div>
                        </div>

                        <div class="dash-card" onclick="openModal('attendance')">
                            <div class="dash-card-icon"><i class="fa-solid fa-calendar-check"></i></div>
                            <div class="dash-card-title">سجل الحضور</div>
                            <div class="dash-card-value" id="attCount" style="color: var(--accent-green);">لم يُسجل</div>
                        </div>
                        <div class="dash-card" onclick="openModal('exams')">
                            <div class="dash-card-icon"><i class="fa-solid fa-star-half-stroke"></i></div>
                            <div class="dash-card-title">درجات الاختبار</div>
                            <div class="dash-card-value" id="scoreStatus">قيد الانتظار</div>
                        </div>
                        <div class="dash-card" onclick="openModal('homework')">
                            <div class="dash-card-icon"><i class="fa-solid fa-pen-clip"></i></div>
                            <div class="dash-card-title">الواجب المدرسي</div>
                            <div class="dash-card-value" id="hwStatus">مطلوب تسليمه</div>
                        </div>
                    </div>
                </div>

                <!-- ج. مكتبة الكتب والملزمة (PDF) -->
                <div id="section-books" style="display: none;">
                    <h4 style="font-size: 11px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;"><i class="fa-solid fa-book-pdf"></i> كتب وملزمة المادة (PDF)</h4>
                    
                    <div class="admin-upload-box" id="adminPdfUploadArea">
                        <h4 style="font-size: 10px; font-weight: bold; color: var(--primary-blue); margin-bottom: 4px;">إضافة كتاب أو ملزمة جديدة:</h4>
                        <div class="form-group" style="margin-bottom: 4px;"><input type="text" id="newPdfTitle" placeholder="عنوان الملزمة" style="color: #1e293b; background: white; border: 1px solid #cbd5e1;"></div>
                        <div class="form-group" style="margin-bottom: 6px;"><input type="text" id="newPdfLink" placeholder="رابط الـ PDF" style="color: #1e293b; background: white; border: 1px solid #cbd5e1;"></div>
                        <button class="btn-main" style="padding: 6px; font-size: 10px;" onclick="addNewPdfBook()">نشر الكتاب للطلاب</button>
                    </div>

                    <div id="pdfBooksContainer"></div>
                </div>

                <!-- د. الفيديوهات التعليمية -->
                <div id="section-videos" style="display: none;">
                    <h4 style="font-size: 11px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;"><i class="fa-solid fa-video"></i> الفيديوهات والشروحات التعليمية</h4>
                    
                    <div class="admin-upload-box" id="adminVideoUploadArea">
                        <h4 style="font-size: 10px; font-weight: bold; color: var(--primary-blue); margin-bottom: 4px;">إضافة فيديو تعليمي جديد:</h4>
                        <div class="form-group" style="margin-bottom: 4px;"><input type="text" id="newVideoTitle" placeholder="عنوان الدرس" style="color: #1e293b; background: white; border: 1px solid #cbd5e1;"></div>
                        <div class="form-group" style="margin-bottom: 6px;"><input type="text" id="newVideoLink" placeholder="رابط الفيديو" style="color: #1e293b; background: white; border: 1px solid #cbd5e1;"></div>
                        <button class="btn-main" style="padding: 6px; font-size: 10px;" onclick="addNewEducationalVideo()">نشر الفيديو للطلاب</button>
                    </div>

                    <div id="videosContainer"></div>
                </div>

                <!-- هـ. قسم الإعلانات -->
                <div id="section-ads" style="display: none;">
                    <h4 style="font-size: 11px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;"><i class="fa-solid fa-bullhorn"></i> لوحة الإعلانات الرسمية</h4>
                    
                    <div class="admin-upload-box" id="adminAdsUploadArea">
                        <h4 style="font-size: 10px; font-weight: bold; color: var(--primary-blue); margin-bottom: 4px;">كتابة إعلان جديد (للأدمن فقط):</h4>
                        <div class="form-group" style="margin-bottom: 6px;"><textarea id="newAdText" rows="2" placeholder="اكتب نص الإعلان..." style="color: #1e293b; background: white; border: 1px solid #cbd5e1;"></textarea></div>
                        <button class="btn-main" style="padding: 6px; font-size: 10px;" onclick="addNewAdPost()">نشر الإعلان للجميع</button>
                    </div>

                    <div id="adsContainer"></div>
                </div>

                <!-- و. مركز الدعم والتذاكر -->
                <div id="section-support" style="display: none;">
                    <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px;">
                        <h4 style="font-size: 11px; font-weight: 900; color: var(--primary-blue);"><i class="fa-solid fa-headset"></i> مركز الدعم والتذاكر</h4>
                        <button class="btn-main" style="width: auto; padding: 4px 8px; font-size: 9px; margin: 0;" onclick="openNewTicketModal()"><i class="fa-solid fa-plus"></i> تذكرة جديدة</button>
                    </div>
                    <div id="supportTicketsContainer"></div>
                </div>

                <!-- ز. الأسئلة الشائعة -->
                <div id="section-faq" style="display: none;">
                    <h4 style="font-size: 11px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;"><i class="fa-solid fa-circle-question"></i> الأسئلة الشائعة</h4>
                    <div class="faq-item">
                        <div class="faq-question" onclick="toggleFaq(this)">كيف يمكنني الوصول إلى السنتر وحضور الحصص؟ <i class="fa-solid fa-chevron-down"></i></div>
                        <div class="faq-answer">يمكنك الحضور في الموعد المحدد لمجموعتك مع المعلم وإظهار بطاقة الحضور الإلكترونية الخاصة بك من صفحة الملف الشخصي.</div>
                    </div>
                    <div class="faq-item">
                        <div class="faq-question" onclick="toggleFaq(this)">كيف أتتبع تقدمي ودرجات الاختبارات؟ <i class="fa-solid fa-chevron-down"></i></div>
                        <div class="faq-answer">عبر الانتقال إلى قسم "المتابعة" في الأعلى، حيث تظهر لك درجاتك وحالة الحضور والواجبات بدقة.</div>
                    </div>
                    <div class="faq-item">
                        <div class="faq-question" onclick="toggleFaq(this)">كيف أحصل على المساعدة عند مواجهة مشكلة؟ <i class="fa-solid fa-chevron-down"></i></div>
                        <div class="faq-answer">يمكنك الانتقال لقسم "الدعم" وفتح تذكرة دعم جديدة وسيتم الرد عليك فوراً من قبل الإدارة.</div>
                    </div>
                </div>

                <!-- ح. مجتمع المادة (تم دعم مسح وتعديل الرسائل وصلاحيات الأدمن) -->
                <div id="section-community" style="display: none;">
                    <div class="chat-box" id="communityChatBox"></div>
                    <div class="chat-input-area">
                        <input type="text" id="chatInputMessage" placeholder="اكتب استفسارك..." onkeypress="checkEnterChat(event)">
                        <button onclick="sendChatMessage()"><i class="fa-solid fa-paper-plane"></i></button>
                    </div>
                </div>
            </div>
            
            <div class="app-footer">Developed by <span>MK CREATIVE Agency</span></div>
        </div>

        <!-- 4. شاشة الاختبار -->
        <div id="screen-quiz" class="screen" style="background: var(--light-bg); padding: 12px;">
            <div class="top-navbar" style="border-radius: 10px; margin-bottom: 10px;">
                <div class="nav-brand"><i class="fa-solid fa-gamepad"></i> تحدي 3 إعدادي (50 سؤال)</div>
                <button class="nav-btn" onclick="showScreen('screen-dashboard')" style="color: var(--accent-red); font-size: 11px;"><i class="fa-solid fa-arrow-right"></i> إنهاء الاختبار</button>
            </div>
            
            <div class="quiz-container-ui">
                <div style="display: flex; justify-content: space-between; margin-bottom: 12px; font-size: 11px; color: var(--text-muted); font-weight: bold; border-bottom: 1px solid #f1f5f9; padding-bottom: 8px;">
                    <span id="question-counter">السؤال: 1 / 50</span>
                    <span id="score-tracker">النقاط: 0</span>
                </div>
                
                <div id="quiz-header">
                    <h3 id="question-text" style="font-size: 13px; color: var(--text-main); margin-bottom: 15px; line-height: 1.6;">جاري تحميل السؤال...</h3>
                    <ul id="options-list"></ul>
                </div>
                
                <button id="submit-quiz-btn" class="btn-main" onclick="submitQuizAnswer()" style="padding: 12px; font-size: 13px; margin-top: 15px;">السؤال التالي</button>
            </div>
        </div>

    </div>

    <!-- نافذة تذكرة دعم جديدة -->
    <div class="modal-overlay" id="ticketModal" onclick="closeTicketModal(event)">
        <div class="modal-card" onclick="event.stopPropagation()">
            <h3 style="font-size: 13px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;">إنشاء تذكرة دعم جديدة</h3>
            <div class="form-group" style="margin-bottom: 6px;"><input type="text" id="ticketTitle" placeholder="عنوان المشكلة أو الاستفسار" style="color: #1e293b; background: white; border: 1px solid #cbd5e1;"></div>
            <div class="form-group" style="margin-bottom: 8px;"><textarea id="ticketDesc" rows="3" placeholder="اشرح مشكلتك بالتفصيل..." style="color: #1e293b; background: white; border: 1px solid #cbd5e1;"></textarea></div>
            <button class="btn-main" onclick="submitNewTicket()">إرسال التذكرة</button>
        </div>
    </div>

    <!-- نافذة المودال للمتابعة -->
    <div class="modal-overlay" id="customModal" onclick="closeModal(event)">
        <div class="modal-card" onclick="event.stopPropagation()">
            <h3 id="modalTitle" style="font-size: 13px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;">تفاصيل النشاط</h3>
            <p id="modalBodyText" style="font-size: 11px; color: var(--text-muted); margin-bottom: 12px; line-height: 1.5;"></p>
            
            <div class="admin-controls" id="adminControlsArea">
                <h4 style="font-size: 10px; font-weight: bold; color: var(--primary-blue); margin-bottom: 4px;">لوحة تحكم المعلم:</h4>
                <div class="form-group" style="margin-bottom: 6px;">
                    <select id="adminActionSelect" style="color: #1e293b; background: white; border: 1px solid #cbd5e1;">
                        <option value="attend">تأكيد الحضور (حاضر)</option>
                        <option value="absent">تسجيل غياب</option>
                        <option value="score_full">الدرجة النهائية (امتياز)</option>
                        <option value="hw_done">تسليم الواجب (تم التسليم)</option>
                    </select>
                </div>
                <button class="btn-main" style="padding: 6px; font-size: 10px;" onclick="saveAdminChanges()">تحديث بيانات الطالب</button>
            </div>

            <button class="btn-main btn-secondary" style="color: var(--text-main); border-color: #cbd5e1; margin-top: 8px;" onclick="closeModalDirect()">إغلاق</button>
        </div>
    </div>

    <!-- نافذة تسجيل دخول المعلم -->
    <div class="modal-overlay" id="teacherLoginModal" onclick="closeTeacherModal(event)">
        <div class="modal-card" onclick="event.stopPropagation()">
            <h3 style="font-size: 13px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;"><i class="fa-solid fa-chalkboard-user"></i> دخول المعلم / الأدمن</h3>
            <p style="font-size: 10px; color: var(--text-muted); margin-bottom: 10px;">اختر المعلم للدخول لصلاحيات التعديل ونشر الإعلانات</p>
            <div class="form-group" style="margin-bottom: 8px;">
                <select id="teacherSelectLogin" style="color: #1e293b; background: white; border: 1px solid #cbd5e1;">
                    <option value="مستر جلال الأتربي (دراسات اجتماعية)">مستر جلال الأتربي (دراسات اجتماعية)</option>
                    <option value="مستر سلمان زاكي (رياضيات)">مستر سلمان زاكي (رياضيات)</option>
                    <option value="مستر أحمد عبدالمطلب (لغة عربية)">مستر أحمد عبدالمطلب (لغة عربية)</option>
                    <option value="مستر نجيب رسلان (لغة إنجليزية)">مستر نجيب رسلان (لغة إنجليزية)</option>
                </select>
            </div>
            <button class="btn-main" onclick="teacherLoginExecute()">دخول لوحة التحكم</button>
        </div>
    </div>

    <script>
        const teacherGroupsData = {
            "مستر جلال الأتربي (دراسات اجتماعية)": ["مجموعة السبت والثلاثاء (الساعة 3 عصراً)"],
            "مستر سلمان زاكي (رياضيات)": ["مجموعة السبت والثلاثاء (الساعة 5 مساءً)"],
            "مستر أحمد عبدالمطلب (لغة عربية)": ["مجموعة السبت والثلاثاء (الساعة 5 مساءً)"],
            "مستر نجيب رسلان (لغة إنجليزية)": ["مجموعة السبت والثلاثاء (الساعة 4 عصراً)"]
        };

        let isTeacherMode = false;
        let loggedInTeacher = "";
        let currentStudentIndex = 0;
        let activeModalType = "";
        let savedAccounts = JSON.parse(localStorage.getItem('mozakra_pro_students_v7')) || [];
        
        let pdfBooksList = JSON.parse(localStorage.getItem('mozakra_pdf_books_v3')) || [];
        let videosList = JSON.parse(localStorage.getItem('mozakra_videos_v2')) || [];
        let adsList = JSON.parse(localStorage.getItem('mozakra_ads_v1')) || [];
        let ticketsList = JSON.parse(localStorage.getItem('mozakra_tickets_v1')) || [];

        function updateGroupsDropdown() {
            let teacherSelect = document.getElementById('regTeacherSelect');
            let groupSelect = document.getElementById('regGroup');
            if(!teacherSelect || !groupSelect) return;
            let selectedTeacher = teacherSelect.value;
            let groups = teacherGroupsData[selectedTeacher] || [];
            groupSelect.innerHTML = '';
            groups.forEach(g => {
                let opt = document.createElement('option');
                opt.value = g;
                opt.innerText = g;
                groupSelect.appendChild(opt);
            });
        }

        window.onload = function() {
            updateGroupsDropdown();
            renderSavedAccounts();
        };

        function renderSavedAccounts() {
            const container = document.getElementById('savedAccountsContainer');
            if(!container) return;
            container.innerHTML = '';
            if(savedAccounts.length === 0) {
                container.innerHTML = '<p style="font-size: 10px; color: var(--text-muted); text-align: center; margin-top: 15px;">لا توجد حسابات مسجلة.</p>';
                return;
            }
            savedAccounts.forEach((acc, index) => {
                container.innerHTML += `
                    <div class="account-card-saved" onclick="loginStudent(${index})">
                        <div style="text-align: right; flex: 1;">
                            <h4 style="font-size: 11px; font-weight: bold; color: var(--text-main);">${acc.name}</h4>
                            <span style="font-size: 9px; color: var(--secondary-blue);">${acc.teacher} | ${acc.grade}</span>
                        </div>
                        <i class="fa-solid fa-chevron-left" style="font-size: 10px; color: var(--text-muted);"></i>
                    </div>
                `;
            });
        }

        function showScreen(screenId) {
            document.querySelectorAll('.screen').forEach(s => s.classList.remove('active'));
            document.getElementById(screenId).classList.add('active');
            if(screenId === 'screen-welcome') {
                renderSavedAccounts();
                isTeacherMode = false;
            }
        }

        function showTeacherLoginModal() { document.getElementById('teacherLoginModal').style.display = 'flex'; }
        function closeTeacherModal(e) { document.getElementById('teacherLoginModal').style.display = 'none'; }
        
        function teacherLoginExecute() {
            loggedInTeacher = document.getElementById('teacherSelectLogin').value;
            isTeacherMode = true;
            document.getElementById('teacherLoginModal').style.display = 'none';
            
            let filteredAccIndex = savedAccounts.findIndex(acc => acc.teacher === loggedInTeacher);
            if(filteredAccIndex !== -1) {
                loginStudent(filteredAccIndex);
            } else {
                if(savedAccounts.length > 0) {
                    loginStudent(0);
                } else {
                    alert("لا توجد حسابات مسجلة لهذا المعلم بعد، يرجى تسجيل حساب أولاً.");
                    showScreen('screen-register');
                }
            }
        }

        function registerNewStudent() {
            let name = document.getElementById('regStudentName').value.trim();
            if(!name) { alert("يرجى إدخال اسم الطالب!"); return; }
            let newAcc = {
                id: Math.floor(100000 + Math.random() * 900000),
                teacher: document.getElementById('regTeacherSelect').value,
                grade: document.getElementById('regGrade').value,
                group: document.getElementById('regGroup').value,
                name: name,
                phone: document.getElementById('regParentPhone').value || "غير متوفر",
                attendance: "لم يُسجل",
                absence: "منتظم",
                payment: "لم يتم السداد",
                homework: "لم يُسلم",
                score: "لم تُسجل"
            };
            savedAccounts.push(newAcc);
            localStorage.setItem('mozakra_pro_students_v7', JSON.stringify(savedAccounts));
            loginStudent(savedAccounts.length - 1);
        }

        function deleteCurrentAccount() {
            if(confirm("هل أنت متأكد من رغبتك في حذف هذا الحساب نهائياً من المنصة؟")) {
                savedAccounts.splice(currentStudentIndex, 1);
                localStorage.setItem('mozakra_pro_students_v7', JSON.stringify(savedAccounts));
                alert("تم حذف الحساب بنجاح.");
                showScreen('screen-welcome');
            }
        }

        function loginStudent(index) {
            currentStudentIndex = index;
            let acc = savedAccounts[index];
            document.getElementById('uiStudentName').innerText = acc.name;
            document.getElementById('uiId').innerText = acc.id;
            document.getElementById('uiTeacherName').innerText = acc.teacher;
            document.getElementById('uiTeacher').innerText = acc.teacher;
            document.getElementById('uiGroup').innerText = acc.group;
            document.getElementById('uiGroupBadge').innerText = acc.group.split(' ')[0];
            document.getElementById('uiGrade').innerText = acc.grade;
            
            document.getElementById('attCount').innerText = acc.attendance;
            document.getElementById('scoreStatus').innerText = acc.score;
            document.getElementById('hwStatus').innerText = acc.homework;

            let challengeBtn = document.getElementById('challengeCardBtn');
            if(acc.grade === "الصف الثالث الإعدادي") {
                challengeBtn.style.display = 'flex';
            } else {
                challengeBtn.style.display = 'none';
            }

            let badgeBtn = document.getElementById('teacherBadgeBtn');
            let adminPdfUploadArea = document.getElementById('adminPdfUploadArea');
            let adminVideoUploadArea = document.getElementById('adminVideoUploadArea');
            let adminAdsUploadArea = document.getElementById('adminAdsUploadArea');
            
            if(isTeacherMode) {
                badgeBtn.style.display = 'inline-block';
                badgeBtn.innerText = "أدمن: " + acc.teacher.split(' ')[1];
                if(adminPdfUploadArea) adminPdfUploadArea.classList.add('active');
                if(adminVideoUploadArea) adminVideoUploadArea.classList.add('active');
                if(adminAdsUploadArea) adminAdsUploadArea.classList.add('active');
            } else {
                badgeBtn.style.display = 'none';
                if(adminPdfUploadArea) adminPdfUploadArea.classList.remove('active');
                if(adminVideoUploadArea) adminVideoUploadArea.classList.remove('active');
                if(adminAdsUploadArea) adminAdsUploadArea.classList.remove('active');
            }

            loadCommunityChat();
            renderPdfBooks();
            renderVideos();
            renderAds();
            renderSupportTickets();
            showScreen('screen-dashboard');
            switchSection('profile');
        }

        function switchSection(sectionName) {
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            if(event && event.target) event.target.classList.add('active');
            
            document.getElementById('section-profile').style.display = (sectionName === 'profile') ? 'block' : 'none';
            document.getElementById('section-stats').style.display = (sectionName === 'stats') ? 'block' : 'none';
            document.getElementById('section-books').style.display = (sectionName === 'books') ? 'block' : 'none';
            document.getElementById('section-videos').style.display = (sectionName === 'videos') ? 'block' : 'none';
            document.getElementById('section-ads').style.display = (sectionName === 'ads') ? 'block' : 'none';
            document.getElementById('section-support').style.display = (sectionName === 'support') ? 'block' : 'none';
            document.getElementById('section-faq').style.display = (sectionName === 'faq') ? 'block' : 'none';
            document.getElementById('section-community').style.display = (sectionName === 'community') ? 'block' : 'none';
        }

        function renderPdfBooks() {
            let container = document.getElementById('pdfBooksContainer');
            if(!container) return;
            container.innerHTML = '';
            
            if(pdfBooksList.length === 0) {
                container.innerHTML = '<div class="empty-notice">لا يوجد ملف / كتاب منزل في الوقت الحالي</div>';
                return;
            }

            pdfBooksList.forEach((book) => {
                container.innerHTML += `
                    <div class="media-card">
                        <div class="media-info">
                            <div class="media-icon"><i class="fa-solid fa-file-pdf"></i></div>
                            <div>
                                <h5 style="font-size: 11px; font-weight: bold; color: var(--text-main);">${book.title}</h5>
                                <span style="font-size: 9px; color: var(--text-muted);">ملف تعليمي</span>
                            </div>
                        </div>
                        <a href="${book.link}" target="_blank" class="media-btn"><i class="fa-solid fa-download"></i> تحميل PDF</a>
                    </div>
                `;
            });
        }

        function addNewPdfBook() {
            let title = document.getElementById('newPdfTitle').value.trim();
            let link = document.getElementById('newPdfLink').value.trim();
            if(!title || !link) { alert("يرجى إدخال عنوان الكتاب ورابط الـ PDF!"); return; }
            pdfBooksList.push({ title: title, link: link });
            localStorage.setItem('mozakra_pdf_books_v3', JSON.stringify(pdfBooksList));
            document.getElementById('newPdfTitle').value = '';
            document.getElementById('newPdfLink').value = '';
            renderPdfBooks();
            alert("تم نشر كتاب الـ PDF بنجاح!");
        }

        function renderVideos() {
            let container = document.getElementById('videosContainer');
            if(!container) return;
            container.innerHTML = '';
            
            if(videosList.length === 0) {
                container.innerHTML = '<div class="empty-notice">لا يوجد فيديو منزل في الوقت الحالي</div>';
                return;
            }

            videosList.forEach((vid) => {
                container.innerHTML += `
                    <div class="media-card">
                        <div class="media-info">
                            <div class="media-icon video"><i class="fa-solid fa-play"></i></div>
                            <div>
                                <h5 style="font-size: 11px; font-weight: bold; color: var(--text-main);">${vid.title}</h5>
                                <span style="font-size: 9px; color: var(--text-muted);">شرح مرئي</span>
                            </div>
                        </div>
                        <a href="${vid.link}" target="_blank" class="media-btn"><i class="fa-solid fa-tv"></i> مشاهدة</a>
                    </div>
                `;
            });
        }

        function addNewEducationalVideo() {
            let title = document.getElementById('newVideoTitle').value.trim();
            let link = document.getElementById('newVideoLink').value.trim();
            if(!title || !link) { alert("يرجى إدخال عنوان ورابط الفيديو!"); return; }
            videosList.push({ title: title, link: link });
            localStorage.setItem('mozakra_videos_v2', JSON.stringify(videosList));
            document.getElementById('newVideoTitle').value = '';
            document.getElementById('newVideoLink').value = '';
            renderVideos();
            alert("تم نشر الفيديو التعليمي بنجاح!");
        }

        function renderAds() {
            let container = document.getElementById('adsContainer');
            if(!container) return;
            container.innerHTML = '';

            if(adsList.length === 0) {
                container.innerHTML = '<div class="empty-notice">لا توجد إعلانات منشورة في الوقت الحالي</div>';
                return;
            }

            adsList.forEach((ad, index) => {
                let commentsHtml = '';
                if(ad.comments && ad.comments.length > 0) {
                    ad.comments.forEach(c => {
                        commentsHtml += `<div class="comment-item"><b>${c.sender}:</b> ${c.text}</div>`;
                    });
                }

                container.innerHTML += `
                    <div class="post-card">
                        <div class="post-header">
                            <span><i class="fa-solid fa-bullhorn"></i> إعلان رسمي</span>
                            <span style="font-size: 8px; color: var(--text-muted);">${ad.date}</span>
                        </div>
                        <div class="post-body">${ad.text}</div>
                        <div class="post-actions">
                            <button onclick="likeAd(${index})"><i class="fa-solid fa-thumbs-up" style="color: var(--secondary-blue);"></i> أعجبني (${ad.likes || 0})</button>
                        </div>
                        <div class="comments-section">
                            ${commentsHtml}
                            <div style="display: flex; gap: 4px; margin-top: 4px;">
                                <input type="text" id="adCommentInput_${index}" placeholder="اكتب رداً..." style="flex:1; padding:5px; border-radius:5px; border:1px solid #cbd5e1; font-size:10px; background:white; color:#1e293b; outline:none;">
                                <button onclick="sendAdComment(${index})" style="background:var(--secondary-blue); color:white; border:none; padding:4px 8px; border-radius:5px; font-size:10px; cursor:pointer;">رد</button>
                            </div>
                        </div>
                    </div>
                `;
            });
        }

        function addNewAdPost() {
            let text = document.getElementById('newAdText').value.trim();
            if(!text) { alert("يرجى كتابة نص الإعلان!"); return; }
            let newAd = {
                text: text,
                likes: 0,
                comments: [],
                date: new Date().toLocaleDateString('ar-EG')
            };
            adsList.push(newAd);
            localStorage.setItem('mozakra_ads_v1', JSON.stringify(adsList));
            document.getElementById('newAdText').value = '';
            renderAds();
            alert("تم نشر الإعلان بنجاح!");
        }

        function likeAd(index) {
            adsList[index].likes = (adsList[index].likes || 0) + 1;
            localStorage.setItem('mozakra_ads_v1', JSON.stringify(adsList));
            renderAds();
        }

        function sendAdComment(index) {
            let input = document.getElementById(`adCommentInput_${index}`);
            let text = input.value.trim();
            if(!text) return;
            let acc = savedAccounts[currentStudentIndex];
            if(!adsList[index].comments) adsList[index].comments = [];
            adsList[index].comments.push({ sender: acc.name, text: text });
            localStorage.setItem('mozakra_ads_v1', JSON.stringify(adsList));
            input.value = '';
            renderAds();
        }

        function renderSupportTickets() {
            let container = document.getElementById('supportTicketsContainer');
            if(!container) return;
            container.innerHTML = '';

            let acc = savedAccounts[currentStudentIndex];
            let myTickets = ticketsList.filter(t => isTeacherMode || t.studentName === acc.name);

            if(myTickets.length === 0) {
                container.innerHTML = '<div class="empty-notice">لا توجد تذاكر دعم حتى الآن</div>';
                return;
            }

            myTickets.forEach((ticket, idx) => {
                container.innerHTML += `
                    <div class="post-card" style="border-right: 3px solid var(--secondary-blue);">
                        <div class="post-header">
                            <span>${ticket.title}</span>
                            <span style="font-size: 8px; color: var(--accent-green);">${ticket.status}</span>
                        </div>
                        <div class="post-body" style="font-size: 10px;"><b>الطالب:</b> ${ticket.studentName}<br>${ticket.desc}</div>
                        <div style="font-size: 9px; color: var(--text-muted); background:#f1f5f9; padding:5px; border-radius:5px;">رد الإدارة: ${ticket.reply || "قيد المراجعة من الأدمن..."}</div>
                        ${isTeacherMode ? `
                            <div style="margin-top:5px; display:flex; gap:4px;">
                                <input type="text" id="ticketReplyInput_${idx}" placeholder="اكتب رد الأدمن..." style="flex:1; padding:4px; font-size:10px; border:1px solid #cbd5e1; border-radius:5px; background:white; color:#1e293b;">
                                <button onclick="replyTicket(${idx})" style="background:var(--secondary-blue); color:white; border:none; padding:4px 8px; border-radius:5px; font-size:10px; cursor:pointer;">إرسال الرد</button>
                            </div>
                        ` : ''}
                    </div>
                `;
            });
        }

        function openNewTicketModal() { document.getElementById('ticketModal').style.display = 'flex'; }
        function closeTicketModal(e) { if(e.target.id === 'ticketModal') document.getElementById('ticketModal').style.display = 'none'; }

        function submitNewTicket() {
            let title = document.getElementById('ticketTitle').value.trim();
            let desc = document.getElementById('ticketDesc').value.trim();
            if(!title || !desc) { alert("يرجى ملء عنوان ووصف التذكرة!"); return; }
            let acc = savedAccounts[currentStudentIndex];
            ticketsList.push({
                studentName: acc.name,
                title: title,
                desc: desc,
                status: "مفتوحة",
                reply: "لم يتم الرد بعد"
            });
            localStorage.setItem('mozakra_tickets_v1', JSON.stringify(ticketsList));
            document.getElementById('ticketTitle').value = '';
            document.getElementById('ticketDesc').value = '';
            document.getElementById('ticketModal').style.display = 'none';
            renderSupportTickets();
            alert("تم إرسال تذكرة الدعم بنجاح!");
        }

        function replyTicket(idx) {
            let input = document.getElementById(`ticketReplyInput_${idx}`);
            let text = input.value.trim();
            if(!text) return;
            ticketsList[idx].reply = text;
            ticketsList[idx].status = "تم الحل";
            localStorage.setItem('mozakra_tickets_v1', JSON.stringify(ticketsList));
            renderSupportTickets();
        }

        function toggleFaq(el) {
            let item = el.parentElement;
            item.classList.toggle('active');
        }

        function openModal(type) {
            activeModalType = type;
            let modal = document.getElementById('customModal');
            let title = document.getElementById('modalTitle');
            let body = document.getElementById('modalBodyText');
            let adminArea = document.getElementById('adminControlsArea');
            let acc = savedAccounts[currentStudentIndex];

            if(type === 'attendance') {
                title.innerText = "سجل الحضور والغياب";
                body.innerHTML = `حالة الحضور الحالية: <b>${acc.attendance}</b><br>حالة الانضباط: <b>${acc.absence}</b>`;
            } else if(type === 'exams') {
                title.innerText = "درجات الاختبارات";
                body.innerHTML = `الدرجة المسجلة: <b>${acc.score}</b>`;
            } else if(type === 'homework') {
                title.innerText = "متابعة الواجب المدرسي";
                body.innerHTML = `حالة تسليم الواجب: <b>${acc.homework}</b>`;
            }

            if(isTeacherMode) { adminArea.classList.add('active'); } 
            else { adminArea.classList.remove('active'); }
            modal.style.display = 'flex';
        }

        function closeModal(e) { if(e.target.id === 'customModal') { document.getElementById('customModal').style.display = 'none'; } }
        function closeModalDirect() { document.getElementById('customModal').style.display = 'none'; }

        function saveAdminChanges() {
            let action = document.getElementById('adminActionSelect').value;
            let acc = savedAccounts[currentStudentIndex];
            if(action === 'attend') { acc.attendance = "حاضر في السنتر"; }
            else if(action === 'absent') { acc.attendance = "غائب"; }
            else if(action === 'score_full') { acc.score = "امتياز (كاملة)"; }
            else if(action === 'hw_done') { acc.homework = "تم التسليم والمراجعة"; }

            savedAccounts[currentStudentIndex] = acc;
            localStorage.setItem('mozakra_pro_students_v7', JSON.stringify(savedAccounts));
            loginStudent(currentStudentIndex);
            document.getElementById('customModal').style.display = 'none';
            alert("تم تحديث البيانات بنجاح!");
        }

        // تطوير قسم الدردشة المجتمعية (مسح وتعديل رسائل الطلاب + صلاحيات الأدمن للحذف)
        let communityMessages = JSON.parse(localStorage.getItem('mozakra_chat_v8')) || [
            { sender: "AI Assistant Bot", senderName: "AI Assistant Bot", text: "أهلاً بك في مجتمع المنصة! يمكنك طرح استفساراتك هنا.", mine: false }
        ];

        function loadCommunityChat() {
            let chatBox = document.getElementById('communityChatBox');
            if(!chatBox) return;
            chatBox.innerHTML = '';
            let acc = savedAccounts[currentStudentIndex];

            communityMessages.forEach((msg, index) => {
                let isMine = (msg.senderName === acc.name);
                // يسمح للطالب تعديل وحذف رسالته، وللأدمن حذف أي رسالة للطلاب
                let canDelete = isMine || isTeacherMode;
                let canEdit = isMine;

                chatBox.innerHTML += `
                    <div class="chat-bubble ${isMine ? 'mine' : ''}">
                        <div class="chat-sender">
                            <span>${msg.senderName || msg.sender}</span>
                        </div>
                        <div id="msgText_${index}">${msg.text}</div>
                        <div class="chat-actions-btns">
                            ${canEdit ? `<button class="btn-edit-msg" onclick="editChatMessage(${index})"><i class="fa-solid fa-pen"></i> تعديل</button>` : ''}
                            ${canDelete ? `<button class="btn-del-msg" onclick="deleteChatMessage(${index})"><i class="fa-solid fa-trash"></i> حذف</button>` : ''}
                        </div>
                    </div>
                `;
            });
            chatBox.scrollTop = chatBox.scrollHeight;
        }

        function sendChatMessage() {
            let input = document.getElementById('chatInputMessage');
            let text = input.value.trim();
            if(!text) return;
            let acc = savedAccounts[currentStudentIndex];
            
            communityMessages.push({ 
                sender: acc.name, 
                senderName: acc.name, 
                text: text, 
                mine: true 
            });
            localStorage.setItem('mozakra_chat_v8', JSON.stringify(communityMessages));
            input.value = '';
            loadCommunityChat();
        }

        function deleteChatMessage(index) {
            if(confirm("هل أنت متأكد من رغبتك في حذف هذه الرسالة؟")) {
                communityMessages.splice(index, 1);
                localStorage.setItem('mozakra_chat_v8', JSON.stringify(communityMessages));
                loadCommunityChat();
            }
        }

        function editChatMessage(index) {
            let newText = prompt("عدل رسالتك:", communityMessages[index].text);
            if(newText !== null && newText.trim() !== "") {
                communityMessages[index].text = newText.trim();
                localStorage.setItem('mozakra_chat_v8', JSON.stringify(communityMessages));
                loadCommunityChat();
            }
        }

        function checkEnterChat(e) { if(e.key === 'Enter') sendChatMessage(); }

        const quizData = [
            { question: "تعد قارة أمريكا الشمالية أكبر قارات العالم الجديد من حيث المساحة.", a: "صح", b: "خطأ", correct: "a" },
            { question: "يصب نهر الأمازون في المحيط الهادي.", a: "صح", b: "خطأ", correct: "b" },
            { question: "تقع حضارة الإنكا في قارة أمريكا الجنوبية جهة...", a: "الشمال", b: "الجنوب", c: "الشرق", d: "الغرب", correct: "d" },
            { question: "أطول سلسلة جبلية في العالم هي جبال...", a: "الألب", b: "الأنديز", c: "الهمالايا", d: "روكي", correct: "b" },
            { question: "أول وال عثماني على مصر بعد خروج الحملة الفرنسية هو...", a: "محمد علي", b: "خورشيد باشا", c: "خسرو باشا", d: "إبراهيم باشا", correct: "c" }
        ];

        let currentQuiz = 0;
        let score = 0;

        function openChallengeGame() {
            let acc = savedAccounts[currentStudentIndex];
            if(acc.grade !== "الصف الثالث الإعدادي") {
                alert("مركز التحدي مخصص لطلاب الصف الثالث الإعدادي فقط!");
                return;
            }
            showScreen('screen-quiz');
            currentQuiz = 0;
            score = 0;
            loadQuizData();
        }

        function loadQuizData() {
            const optionsEl = document.getElementById('options-list');
            optionsEl.innerHTML = '';
            const currentQuizData = quizData[currentQuiz];
            document.getElementById('question-text').innerText = currentQuizData.question;
            document.getElementById('question-counter').innerText = `السؤال: ${currentQuiz + 1} / ${quizData.length}`;
            document.getElementById('score-tracker').innerText = `النقاط: ${score}`;

            ['a', 'b', 'c', 'd'].forEach(opt => {
                if(currentQuizData[opt]) {
                    optionsEl.innerHTML += `
                        <li>
                            <input type="radio" name="quiz-answer" id="${opt}" class="quiz-answer" value="${opt}">
                            <label for="${opt}">${currentQuizData[opt]}</label>
                        </li>
                    `;
                }
            });
        }

        function submitQuizAnswer() {
            let answer;
            document.querySelectorAll('.quiz-answer').forEach(el => { if(el.checked) answer = el.value; });
            if (answer) {
                if (answer === quizData[currentQuiz].correct) score++;
                currentQuiz++;
                if (currentQuiz < quizData.length) {
                    loadQuizData();
                } else {
                    document.getElementById('quiz-header').innerHTML = `
                        <div style="text-align: center; padding: 20px 0;">
                            <i class="fa-solid fa-trophy" style="font-size: 40px; color: var(--accent-yellow); margin-bottom: 10px;"></i>
                            <h2 style="color: var(--primary-blue); مفتاح: 16px;">أحسنت يا بطل!</h2>
                            <h3 style="color: var(--accent-green); font-size: 18px; margin-top: 10px;">نتيجتك: ${score} من ${quizData.length}</h3>
                        </div>
                    `;
                    document.getElementById('submit-quiz-btn').innerText = "العودة للوحة المتابعة";
                    document.getElementById('submit-quiz-btn').onclick = () => showScreen('screen-dashboard');
                }
            } else {
                alert("يرجى اختيار إجابة أولاً!");
            }
        }
    </script>
</body>
</html>
