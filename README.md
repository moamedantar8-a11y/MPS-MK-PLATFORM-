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

        /* --- الأنماط العامة للمنصة --- */
        .welcome-screen { background: var(--light-bg); padding: 20px; text-align: center; }
        .welcome-logo { font-size: 50px; color: var(--secondary-blue); margin-bottom: 5px; margin-top: 15px; }
        .accounts-list { width: 100%; margin: 10px 0; max-height: 240px; overflow-y: auto; display: flex; flex-direction: column; gap: 8px; }
        .account-card-saved { background: white; border: 1px solid #e2e8f0; padding: 10px 14px; border-radius: 14px; display: flex; justify-content: space-between; align-items: center; cursor: pointer; transition: var(--transition); }
        .account-card-saved:hover { border-color: var(--secondary-blue); transform: translateY(-2px); }
        
        .register-screen { background: linear-gradient(180deg, #1e3a8a 0%, #1e40af 100%); color: white; padding: 15px; justify-content: center; align-items: center; }
        .form-group { width: 100%; margin-bottom: 8px; text-align: right; }
        .form-group label { font-size: 11px; color: #cbd5e1; display: block; margin-bottom: 2px; }
        .form-group input, .form-group select { width: 100%; padding: 8px 10px; border-radius: 8px; border: 1px solid rgba(255,255,255,0.2); background: rgba(255,255,255,0.08); color: white; font-size: 11px; outline: none; }
        .form-group select option { background: #1e3a8a; color: white; }
        
        .btn-main { width: 100%; background: var(--secondary-blue); color: white; border: none; padding: 10px; border-radius: 12px; font-size: 12px; font-weight: 700; cursor: pointer; box-shadow: 0 4px 12px rgba(59, 130, 246,.3); margin-top: 6px; transition: var(--transition); }
        .btn-main:hover { background: #2563eb; }
        .btn-secondary { background: transparent; color: #cbd5e1; border: 1px solid rgba(255,255,255,0.2); }
        
        .top-navbar { background: white; padding: 8px 10px; display: flex; justify-content: space-between; align-items: center; box-shadow: 0 2px 4px rgba(0,0,0,0.03); position: sticky; top: 0; z-index: 10; }
        .nav-brand { display: flex; align-items: center; gap: 4px; font-size: 11px; font-weight: 900; color: var(--primary-blue); }
        .nav-links { display: flex; gap: 2px; }
        .nav-btn { background: #f1f5f9; border: none; padding: 5px 5px; border-radius: 5px; font-size: 8px; font-weight: 600; color: var(--text-muted); cursor: pointer; transition: var(--transition); }
        .nav-btn.active, .nav-btn:hover { background: var(--secondary-blue); color: white; }
        
        .dashboard-content { padding: 12px; }
        .profile-header-card { background: linear-gradient(135deg, var(--secondary-blue), var(--primary-blue)); color: white; padding: 12px; border-radius: 12px; display: flex; justify-content: space-between; align-items: center; margin-bottom: 10px; }
        .info-card-item { background: white; padding: 9px 12px; border-radius: 8px; margin-bottom: 6px; display: flex; justify-content: space-between; align-items: center; border: 1px solid #e2e8f0; font-size: 11px; }
        .info-card-item .label-side { display: flex; align-items: center; gap: 8px; color: var(--text-muted); }
        .info-card-item .value-side { font-weight: 700; color: var(--text-main); }
        .info-card-item i { color: var(--secondary-blue); }
        
        .digital-id-card { background: white; border-radius: 10px; padding: 10px; margin-bottom: 10px; border: 1px solid #e2e8f0; display: flex; align-items: center; gap: 10px; }
        .qr-box { width: 42px; height: 42px; background: #eff6ff; color: var(--secondary-blue); display: flex; align-items: center; justify-content: center; border-radius: 8px; font-size: 18px; }
        
        .dashboard-grid { display: grid; grid-template-columns: 1fr 1fr; gap: 8px; margin-bottom: 12px; }
        .dash-card { background: white; padding: 9px; border-radius: 10px; display: flex; flex-direction: column; justify-content: space-between; border: 1px solid #e2e8f0; cursor: pointer; transition: var(--transition); min-height: 80px; }
        .dash-card:hover { border-color: var(--secondary-blue); transform: translateY(-2px); }
        .dash-card-icon { width: 26px; height: 26px; background: #eff6ff; color: var(--secondary-blue); border-radius: 50%; display: flex; align-items: center; justify-content: center; font-size: 11px; margin-bottom: 4px; }
        .dash-card-title { font-size: 10px; font-weight: 700; color: var(--text-main); }
        .dash-card-value { font-size: 10px; color: var(--text-muted); font-weight: bold; margin-top: 2px; }
        
        .chat-box { background: white; border: 1px solid #e2e8f0; border-radius: 10px; padding: 10px; height: 300px; overflow-y: auto; display: flex; flex-direction: column; gap: 8px; }
        .chat-bubble { background: #f1f5f9; padding: 8px 10px; border-radius: 8px; font-size: 11px; max-width: 85%; align-self: flex-start; border-right: 3px solid var(--secondary-blue); }
        .chat-bubble.mine { background: #eff6ff; align-self: flex-end; border-right: none; border-left: 3px solid var(--accent-green); }
        .chat-sender { font-size: 9px; font-weight: bold; color: var(--primary-blue); margin-bottom: 2px; display: flex; justify-content: space-between; }
        .chat-input-area { display: flex; gap: 5px; margin-top: 8px; }
        .chat-input-area input { flex: 1; padding: 8px; border-radius: 8px; border: 1px solid #e2e8f0; font-size: 11px; outline: none; }
        .chat-input-area button { background: var(--secondary-blue); color: white; border: none; padding: 0 12px; border-radius: 8px; cursor: pointer; font-size: 12px; }
        
        /* تصميم قسم الكتب ومكتبة الـ PDF */
        .pdf-card { background: white; border: 1px solid #e2e8f0; border-radius: 10px; padding: 10px; margin-bottom: 8px; display: flex; align-items: center; justify-content: space-between; transition: var(--transition); }
        .pdf-card:hover { border-color: var(--secondary-blue); box-shadow: 0 4px 12px rgba(0,0,0,0.03); }
        .pdf-info { display: flex; align-items: center; gap: 10px; }
        .pdf-icon { width: 35px; height: 35px; background: #fee2e2; color: var(--accent-red); border-radius: 8px; display: flex; align-items: center; justify-content: center; font-size: 16px; }
        .pdf-download-btn { background: #eff6ff; color: var(--secondary-blue); border: 1px solid #bfdbfe; padding: 6px 10px; border-radius: 8px; font-size: 10px; font-weight: bold; text-decoration: none; display: flex; align-items: center; gap: 4px; transition: var(--transition); }
        .pdf-download-btn:hover { background: var(--secondary-blue); color: white; }

        .admin-pdf-upload-box { background: #eff6ff; border: 1px dashed var(--secondary-blue); padding: 10px; border-radius: 10px; margin-bottom: 12px; display: none; }
        .admin-pdf-upload-box.active { display: block; }

        .modal-overlay { position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: rgba(0,0,0,0.6); display: none; justify-content: center; align-items: center; z-index: 100; padding: 15px; }
        .modal-card { background: white; width: 100%; max-width: 320px; border-radius: 12px; padding: 15px; box-shadow: 0 20px 25px -5px rgba(0,0,0,0.2); text-align: right; max-height: 80vh; overflow-y: auto; }
        .admin-controls { background: #eff6ff; border: 1px dashed var(--secondary-blue); padding: 8px; border-radius: 8px; margin-top: 8px; display: none; }
        .admin-controls.active { display: block; }
        .app-footer { text-align: center; padding: 6px; font-size: 9px; color: var(--text-muted); background: white; border-top: 1px solid #f1f5f9; margin-top: auto; }

        /* --- أنماط شاشة الاختبار (Quiz Screen) --- */
        .quiz-container-ui { background: white; border-radius: 12px; padding: 15px; box-shadow: 0 4px 6px rgba(0,0,0,0.05); margin-top: 10px; }
        .quiz-container-ui ul { list-style: none; padding: 0; margin: 0; }
        .quiz-container-ui ul li { margin: 8px 0; }
        .quiz-container-ui label { cursor: pointer; display: block; padding: 12px; background: #f9f9f9; border: 1px solid #e0e0e0; border-radius: 8px; font-size: 12px; transition: var(--transition); }
        .quiz-container-ui label:hover { background: #eaf4ff; border-color: var(--secondary-blue); }
        .quiz-container-ui input[type="radio"] { display: none; }
        .quiz-container-ui input[type="radio"]:checked + label { background: var(--secondary-blue); color: white; border-color: var(--primary-blue); font-weight: bold; }
    </style>
</head>
<body>

    <div class="phone-frame">
        
        <!-- 1. شاشة الترحيب الرئيسية -->
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

        <!-- 3. لوحة تحكم الطالب / المعلم -->
        <div id="screen-dashboard" class="screen">
            <div class="top-navbar">
                <div class="nav-brand"><i class="fa-solid fa-landmark"></i><span>Mozakra</span></div>
                <div class="nav-links">
                    <button class="nav-btn active" onclick="switchSection('profile')">الملف</button>
                    <button class="nav-btn" onclick="switchSection('stats')">المتابعة</button>
                    <button class="nav-btn" onclick="switchSection('books')">الكتب</button>
                    <button class="nav-btn" onclick="switchSection('community')">المجتمع</button>
                    <button class="nav-btn" id="teacherBadgeBtn" style="background: #fef08a; color: #854d0e; display: none;"><i class="fa-solid fa-chalkboard"></i> أدمن</button>
                    <button class="nav-btn" onclick="showScreen('screen-welcome')" style="color: var(--accent-red);"><i class="fa-solid fa-arrow-right-from-bracket"></i></button>
                </div>
            </div>

            <div class="dashboard-content">
                <!-- أ. الملف الشخصي -->
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
                </div>

                <!-- ب. المتابعة والدرجات -->
                <div id="section-stats" style="display: none;">
                    <h4 style="font-size: 11px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;">متابعة أداء الطالب والأنشطة</h4>
                    <div class="dashboard-grid">
                        
                        <!-- زر مركز التحدي (يظهر فقط لـ 3 إعدادي) -->
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
                    
                    <!-- لوحة رفع كتاب جديد (تظهر للأدمن فقط) -->
                    <div class="admin-pdf-upload-box" id="adminPdfUploadArea">
                        <h4 style="font-size: 10px; font-weight: bold; color: var(--primary-blue); margin-bottom: 4px;"><i class="fa-solid fa-circle-plus"></i> إضافة كتاب أو ملزمة جديدة:</h4>
                        <div class="form-group" style="margin-bottom: 4px;">
                            <input type="text" id="newPdfTitle" placeholder="عنوان الملزمة أو الكتاب (مثال: ملزمة الشرح الوحدة الأولى)" style="color: #1e293b; background: white; border: 1px solid #cbd5e1;">
                        </div>
                        <div class="form-group" style="margin-bottom: 6px;">
                            <input type="text" id="newPdfLink" placeholder="رابط ملف الـ PDF (رابط مباشر أو Google Drive)" style="color: #1e293b; background: white; border: 1px solid #cbd5e1;">
                        </div>
                        <button class="btn-main" style="padding: 6px; font-size: 10px;" onclick="addNewPdfBook()">نشر الكتاب للطلاب</button>
                    </div>

                    <!-- قائمة الكتب -->
                    <div id="pdfBooksContainer"></div>
                </div>

                <!-- د. مجتمع المادة -->
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

        <!-- 4. شاشة الاختبار المدمجة (Quiz Screen) -->
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

    <!-- نافذة المودال التفصيلية -->
    <div class="modal-overlay" id="customModal" onclick="closeModal(event)">
        <div class="modal-card" onclick="event.stopPropagation()">
            <h3 id="modalTitle" style="font-size: 13px; font-weight: 900; color: var(--primary-blue); margin-bottom: 8px;">تفاصيل النشاط</h3>
            <p id="modalBodyText" style="font-size: 11px; color: var(--text-muted); margin-bottom: 12px; line-height: 1.5;"></p>
            
            <div class="admin-controls" id="adminControlsArea">
                <h4 style="font-size: 10px; font-weight: bold; color: var(--primary-blue); margin-bottom: 4px;">لوحة تحكم المعلم (تحديث البيانات):</h4>
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
            <p style="font-size: 10px; color: var(--text-muted); margin-bottom: 10px;">اختر المعلم للدخول لصلاحيات التعديل ومتابعة الطلاب</p>
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
        let savedAccounts = JSON.parse(localStorage.getItem('mozakra_pro_students_v5')) || [];
        
        // مصفوفة تخزين الكتب والـ PDF
        let pdfBooksList = JSON.parse(localStorage.getItem('mozakra_pdf_books_v1')) || [
            { title: "ملخص وحدة جغرافيا مصر (PDF)", link: "#" },
            { title: "الامتحانات التراكمية والتدريبات الشاملة", link: "#" }
        ];

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
                    alert("لا توجد حسابات مسجلة لهذا المعلم بعد، يجدر بأحد الطلاب التسجيل أولاً.");
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
            localStorage.setItem('mozakra_pro_students_v5', JSON.stringify(savedAccounts));
            loginStudent(savedAccounts.length - 1);
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

            // التحكم في إظهار مركز التحدي فقط لطلاب الصف الثالث الإعدادي
            let challengeBtn = document.getElementById('challengeCardBtn');
            if(acc.grade === "الصف الثالث الإعدادي") {
                challengeBtn.style.display = 'flex';
            } else {
                challengeBtn.style.display = 'none';
            }

            let badgeBtn = document.getElementById('teacherBadgeBtn');
            let adminPdfUploadArea = document.getElementById('adminPdfUploadArea');
            
            if(isTeacherMode) {
                badgeBtn.style.display = 'inline-block';
                badgeBtn.innerText = "أدمن: " + acc.teacher.split(' ')[1];
                adminPdfUploadArea.classList.add('active'); // إظهار لوحة رفع الكتب للأدمن
            } else {
                badgeBtn.style.display = 'none';
                adminPdfUploadArea.classList.remove('active'); // إخفاء لوحة رفع الكتب عن الطالب العادي
            }

            loadCommunityChat();
            renderPdfBooks();
            showScreen('screen-dashboard');
            switchSection('profile');
        }

        function switchSection(sectionName) {
            document.querySelectorAll('.nav-btn').forEach(btn => btn.classList.remove('active'));
            if(event && event.target) event.target.classList.add('active');
            
            document.getElementById('section-profile').style.display = (sectionName === 'profile') ? 'block' : 'none';
            document.getElementById('section-stats').style.display = (sectionName === 'stats') ? 'block' : 'none';
            document.getElementById('section-books').style.display = (sectionName === 'books') ? 'block' : 'none';
            document.getElementById('section-community').style.display = (sectionName === 'community') ? 'block' : 'none';
        }

        // --- وظائف إدارة كتب ومذكرات الـ PDF ---
        function renderPdfBooks() {
            let container = document.getElementById('pdfBooksContainer');
            if(!container) return;
            container.innerHTML = '';
            
            if(pdfBooksList.length === 0) {
                container.innerHTML = '<p style="font-size: 10px; color: var(--text-muted); text-align: center; margin-top: 15px;">لا توجد كتب أو مذكرات مضافة حالياً.</p>';
                return;
            }

            pdfBooksList.forEach((book, idx) => {
                container.innerHTML += `
                    <div class="pdf-card">
                        <div class="pdf-info">
                            <div class="pdf-icon"><i class="fa-solid fa-file-pdf"></i></div>
                            <div>
                                <h5 style="font-size: 11px; font-weight: bold; color: var(--text-main);">${book.title}</h5>
                                <span style="font-size: 9px; color: var(--text-muted);">ملف تعليمي معتمد</span>
                            </div>
                        </div>
                        <a href="${book.link}" target="_blank" class="pdf-download-btn"><i class="fa-solid fa-download"></i> تحميل PDF</a>
                    </div>
                `;
            });
        }

        function addNewPdfBook() {
            let title = document.getElementById('newPdfTitle').value.trim();
            let link = document.getElementById('newPdfLink').value.trim();

            if(!title || !link) {
                alert("يرجى إدخال عنوان الكتاب ورابط الـ PDF بشكل صحيح!");
                return;
            }

            pdfBooksList.push({ title: title, link: link });
            localStorage.setItem('mozakra_pdf_books_v1', JSON.stringify(pdfBooksList));
            
            document.getElementById('newPdfTitle').value = '';
            document.getElementById('newPdfLink').value = '';
            
            renderPdfBooks();
            alert("تم إضافة ونشر كتاب الـ PDF بنجاح لجميع طلاب المنصة!");
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
                title.innerText = "درجات الاختبارات الشهرية والأسبوعية";
                body.innerHTML = `الدرجة المسجلة: <b>${acc.score}</b><br>ملاحظات المعلم: الأداء جيد ومستمر في التقدم.`;
            } else if(type === 'homework') {
                title.innerText = "متابعة الواجب المدرسي والتمارين";
                body.innerHTML = `حالة تسليم الواجب: <b>${acc.homework}</b>`;
            }

            if(isTeacherMode) {
                adminArea.classList.add('active');
            } else {
                adminArea.classList.remove('active');
            }
            modal.style.display = 'flex';
        }

        function closeModal(e) {
            if(e.target.id === 'customModal') {
                document.getElementById('customModal').style.display = 'none';
            }
        }

        function closeModalDirect() {
            document.getElementById('customModal').style.display = 'none';
        }

        function saveAdminChanges() {
            let action = document.getElementById('adminActionSelect').value;
            let acc = savedAccounts[currentStudentIndex];
            
            if(action === 'attend') { acc.attendance = "حاضر في السنتر"; }
            else if(action === 'absent') { acc.attendance = "غائب"; }
            else if(action === 'score_full') { acc.score = "امتياز (كاملة)"; }
            else if(action === 'hw_done') { acc.homework = "تم التسليم والمراجعة"; }

            savedAccounts[currentStudentIndex] = acc;
            localStorage.setItem('mozakra_pro_students_v5', JSON.stringify(savedAccounts));
            loginStudent(currentStudentIndex);
            document.getElementById('customModal').style.display = 'none';
            alert("تم تحديث بيانات الطالب بنجاح!");
        }

        // المجتمع والدردشة التفاعلية
        let communityMessages = JSON.parse(localStorage.getItem('mozakra_chat_v5')) || [
            { sender: "مستر جلال الأتربي", text: "أهلاً بكم في مجموعة مادة الدراسات الاجتماعية للصف الثالث الإعدادي.", mine: false },
            { sender: "محمد عنتر", text: "مرحباً يا مستر، تم الانتهاء من حل أسئلة خريطة العالم.", mine: true }
        ];

        function loadCommunityChat() {
            let chatBox = document.getElementById('communityChatBox');
            if(!chatBox) return;
            chatBox.innerHTML = '';
            communityMessages.forEach(msg => {
                chatBox.innerHTML += `
                    <div class="chat-bubble ${msg.mine ? 'mine' : ''}">
                        <div class="chat-sender"><span>${msg.sender}</span></div>
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
            let acc = savedAccounts[currentStudentIndex];
            
            communityMessages.push({ sender: acc.name, text: text, mine: true });
            localStorage.setItem('mozakra_chat_v5', JSON.stringify(communityMessages));
            input.value = '';
            loadCommunityChat();
        }

        function checkEnterChat(e) {
            if(e.key === 'Enter') sendChatMessage();
        }

        // --- مصفوفة الـ 50 سؤال الخاصة بالصف الثالث الإعدادي ---
        const quizData = [
            { question: "تعد قارة أمريكا الشمالية أكبر قارات العالم الجديد من حيث المساحة.", a: "صح", b: "خطأ", correct: "a" },
            { question: "يصب نهر الأمازون في المحيط الهادي.", a: "صح", b: "خطأ", correct: "b" },
            { question: "تقع حضارة الإنكا في قارة أمريكا الجنوبية جهة...", a: "الشمال", b: "الجنوب", c: "الشرق", d: "الغرب", correct: "d" },
            { question: "أطول سلسلة جبلية في العالم هي جبال...", a: "الألب", b: "الأنديز", c: "الهمالايا", d: "روكي", correct: "b" },
            { question: "أول وال عثماني على مصر بعد خروج الحملة الفرنسية هو...", a: "محمد علي", b: "خورشيد باشا", c: "خسرو باشا", d: "إبراهيم باشا", correct: "c" },
            { question: "خط الطول الرئيسي يُعرف بخط...", a: "الاستواء", b: "جرينتش", c: "السرطان", d: "الجدي", correct: "b" },
            { question: "تقع مصر في الركن الشمالي الشرقي لقارة...", a: "إفريقيا", b: "آسيا", c: "أوروبا", d: "أستراليا", correct: "a" },
            { question: "المحيط الذي يحيط بالقطب الجنوبي هو المحيط...", a: "الهادي", b: "الأطلنطي", c: "المتجمّد الجنوبي", d: "الهندي", correct: "c" },
            { question: "الدولة العثمانية فتحت قسطنطينية على يد السلطان...", a: "سليم الأول", b: "محمد الفاتح", c: "سليمان القانوني", d: "بايزيد الأول", correct: "b" },
            { question: "معركة مرج دابق كانت عام 1516 بين العثمانيين و...", a: "المماليك", b: "الصفويين", c: "الفرنسيين", d: "الإنجليز", correct: "a" },
            { question: "أكبر بحر مغلق في العالم هو البحر...", a: "المتوسط", b: "الأحمر", c: "قزوين", d: "الأسود", correct: "c" },
            { question: "تقع شبه جزيرة إبرية في قارة...", a: "أوروبا", b: "آسيا", c: "إفريقيا", d: "أستراليا", correct: "a" },
            { question: "عدد دول العالم العربي في الإجمالي يبلغ...", a: "20 دولة", b: "22 دولة", c: "25 دولة", d: "18 دولة", correct: "b" },
            { question: "أعلى قمة جبلية في العالم هي قمة...", a: "إفرست", b: "كيليمنجارو", c: "مون بلان", d: "الكنغرو", correct: "a" },
            { question: "تتميز مصر بوجود قناة السويس التي تربط بين البحر المتوسط و...", a: "البحر الأحمر", b: "الخليج العربي", c: "بحيرة ناصر", d: "المحيط الأطلنطي", correct: "a" },
            { question: "تولى محمد علي حكم مصر بناءً على رغبة...", a: "السلطان العثماني", b: "زعماء الشعب المصري", c: "إنجلترا", d: "المماليك", correct: "b" },
            { question: "تخلص محمد علي من الزعامة الشعبية بنفي الشيخ...", a: "عمر مكرم", b: "محمد المهدي", c: "الشرقاوي", d: "السادات", correct: "a" },
            { question: "مذبحة القلعة تمت للتخلص من...", a: "العلماء", b: "المماليك", c: "الإنجليز", d: "المصريين", correct: "b" },
            { question: "المرري الذي يمر وسط مصر هو مدار...", a: "السرطان", b: "الجدي", c: "الاستواء", d: "الدائرة القطبية", correct: "a" },
            { question: "المساحة الكبرى من سطح الأرض تشغلها...", a: "اليابس", b: "الماء", c: "الجبال", d: "السهول", correct: "b" },
            { question: "عاصمة دولة اليابان هي...", a: "طوكيو", b: "بكين", c: "سيول", d: "صنعاء", correct: "a" },
            { question: "أقرب الكواكب للشمس هو كوكب...", a: "الزهرة", b: "عطارد", c: "المريخ", d: "المشتري", correct: "b" },
            { question: "الكوكب الأحمر في المجموعة الشمسية هو...", a: "المريخ", b: "زحل", c: "الأرض", d: "الزهرة", correct: "a" },
            { question: "أكبر كواكب المجموعة الشمسية حجماً هو...", a: "المشتري", b: "زحل", c: "نبتون", d: "أورانوس", correct: "a" },
            { question: "معركة الريدانية انتهت بهزيمة...", a: "العثمانيين", b: "المماليك", c: "الفرنسيين", d: "المغول", correct: "b" },
            { question: "الحملة الفرنسية على مصر كانت بقيادة...", a: "نيلسون", b: "نابليون بونابرت", c: "مينو", d: "كليبر", correct: "b" },
            { question: "تحطمت أسطول الحملة الفرنسية في معركة...", a: "أبو قير البحرية", b: "أبو قير البرية", c: "الأهرامات", d: "الملك فهد", correct: "a" },
            { question: "قُتل كليبر على يد الطالب...", a: "محمد كُرَيُّم", b: "سليمان الحلبي", c: "عمر مكرم", d: "أحمد الجزار", correct: "b" },
            { question: "تأسست مدينة القاهرة على يد...", a: "جوهر الصقلي", b: "عمر بن الخطاب", c: "أحمد بن طولون", d: "محمد بن طغج", correct: "a" },
            { question: "أطول نهر في العالم هو نهر...", a: "الأمازون", b: "النيل", c: "الميسيسيبي", d: "الدنوب", correct: "b" },
            { question: "تقع أهرامات الجيزة في جمهورية...", a: "السودان", b: "مصر", c: "العراق", d: "سوريا", correct: "b" },
            { question: "الغاز الأكثر توافداً في الغلاف الجوي للأرض هو...", a: "الأكسجين", b: "النيتروجين", c: "ثاني أكسيد الكربون", d: "الهيدروجين", correct: "b" },
            { question: "تكونت البحيرات العظمى في قارة...", a: "أفريقيا", b: "أمريكا الشمالية", c: "أستراليا", d: "أوروبا", correct: "b" },
            { question: "المضيق الذي يفصل بين قارتي إفريقيا وأوروبا هو مضيق...", a: "جبل طارق", b: "باب المندب", c: "هرمز", d: "البسفور", correct: "a" },
            { question: "مضيق باب المندب يربط بين البحر الأحمر و...", a: "المحيط الهندي", b: "خليج عدن", c: "البحر المتوسط", d: "الخليج العربي", correct: "b" },
            { question: "عاصمة مصر التاريخية الحالية هي...", a: "الإسكندرية", b: "القاهرة", c: "الجيزة", d: "أسوان", correct: "b" },
            { question: "عدد أركان الإسلام الرئيسية...", a: "4 أركان", b: "5 أركان", c: "6 أركان", d: "3 أركان", correct: "b" },
            { question: "سورة قرآنية تُسمى قلب القرآن هي سورة...", a: "البقرة", b: "الملك", c: "يس", d: "الرحمن", correct: "c" },
            { question: "غزوة أُحد كانت في العام...", a: "2 هجريا", b: "3 هجريا", c: "5 هجريا", d: "8 هجريا", correct: "b" },
            { question: "أول مؤذن في الإسلام هو الصحابي...", a: "بلال بن رباح", b: "عمر بن الخطاب", c: "أبو بكر الصديق", d: "عثمان بن عفان", correct: "a" },
            { question: "ينسب بناء السد العالي إلى مدينة...", a: "قنا", b: "أسوان", c: "الأقصر", d: "سوهاج", correct: "b" },
            { question: "الجهة المقابلة للشمال هي جهة...", a: "الشرق", b: "الجنوب", c: "الغرب", d: "الشمال الشرقي", correct: "b" },
            { question: "دولة عربية يمر بها نهر النيل وتعتبر دولة مصب هي...", a: "السودان", b: "مصر", c: "إثيوبيا", d: "أوغندا", correct: "b" },
            { question: "مقبرة توت عنخ آمون تم اكتشافها في...", a: "الأقصر", b: "الجيزة", c: "الإسكندرية", d: "أسوان", correct: "a" },
            { question: "عدد أيام السنة الكبيسة هو...", a: "365 يوم", b: "366 يوم", c: "364 يوم", d: "360 يوم", correct: "b" },
            { question: "أسرع حيوان بري في العالم هو...", a: "الأسد", b: "الفهد (الشيتا)", c: "الغزال", d: "الحصان", correct: "b" },
            { question: "العنصر الكيميائي الذي يرمز له بالرمز (O) هو...", a: "الذهب", b: "الأكسجين", c: "الهيدروجين", d: "الحديد", correct: "b" },
            { question: "العضو المسؤول عن ضخ الدم في جسم الإنسان هو...", a: "المخ", b: "القلب", c: "الكبد", d: "الرئتين", correct: "b" },
            { question: "كم عدد سور القرآن الكريم؟", a: "112 سورة", b: "114 سورة", c: "120 سورة", d: "110 سورة", correct: "b" },
            { question: "في أي قارة تقع دولة مصر العربية؟", a: "آسيا", b: "إفريقيا", c: "أوروبا", d: "أستراليا", correct: "b" }
        ];

        let currentQuiz = 0;
        let score = 0;

        function openChallengeGame() {
            let acc = savedAccounts[currentStudentIndex];
            if(acc.grade !== "الصف الثالث الإعدادي") {
                alert("مركز التحدي مخصص حالياً لطلاب الصف الثالث الإعدادي فقط!");
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

            const options = ['a', 'b', 'c', 'd'];
            options.forEach(opt => {
                if(currentQuizData[opt]) {
                    const li = document.createElement('li');
                    li.innerHTML = `
                        <input type="radio" name="quiz-answer" id="${opt}" class="quiz-answer" value="${opt}">
                        <label for="${opt}">${currentQuizData[opt]}</label>
                    `;
                    optionsEl.appendChild(li);
                }
            });
            document.getElementById('submit-quiz-btn').innerText = "السؤال التالي";
        }

        function getSelectedQuizAnswer() {
            const answerEls = document.querySelectorAll('.quiz-answer');
            let answer = undefined;
            answerEls.forEach((answerEl) => {
                if (answerEl.checked) {
                    answer = answerEl.value;
                }
            });
            return answer;
        }

        function submitQuizAnswer() {
            const answer = getSelectedQuizAnswer();
            if (answer) {
                if (answer === quizData[currentQuiz].correct) {
                    score++;
                }
                currentQuiz++;

                if (currentQuiz < quizData.length) {
                    loadQuizData();
                } else {
                    document.getElementById('quiz-header').innerHTML = `
                        <div style="text-align: center; padding: 20px 0;">
                            <i class="fa-solid fa-trophy" style="font-size: 40px; color: var(--accent-yellow); margin-bottom: 10px;"></i>
                            <h2 style="color: var(--primary-blue); font-size: 16px;">أحسنت يا بطل 3 إعدادي!</h2>
                            <h3 style="color: var(--accent-green); font-size: 18px; margin-top: 10px;">نتيجتك النهائية: ${score} من ${quizData.length}</h3>
                        </div>
                    `;
                    document.getElementById('submit-quiz-btn').innerText = "العودة للوحة المتابعة";
                    document.getElementById('submit-quiz-btn').onclick = function() {
                        showScreen('screen-dashboard');
                    };
                }
            } else {
                alert("يرجى اختيار إجابة أولاً يا بطل!");
            }
        }
    </script>
</body>
</html>
