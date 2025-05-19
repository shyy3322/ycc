# ycc
YC
<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>منصة الحصص المتقدمة</title>
  <script src="https://cdn.jsdelivr.net/npm/hls.js@latest"></script>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
  <link href="https://fonts.googleapis.com/css2?family=Tajawal:wght@400;500;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary-color: #4361ee;
      --secondary-color: #3f37c9;
      --accent-color: #4895ef;
      --danger-color: #f72585;
      --success-color: #4cc9f0;
      --light-color: #f8f9fa;
      --dark-color: #212529;
      --gray-color: #6c757d;
      --border-radius: 12px;
      --box-shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
      --transition: all 0.3s ease;
    }
    
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }
    
    body {
      font-family: 'Tajawal', sans-serif;
      background: linear-gradient(135deg, #f5f7fa 0%, #e4e8f0 100%);
      min-height: 100vh;
      padding: 20px;
      color: var(--dark-color);
      line-height: 1.6;
    }
    
    .container {
      max-width: 1200px;
      margin: 0 auto;
      padding: 20px;
    }
    
    h1, h2, h3 {
      color: var(--primary-color);
      margin-bottom: 1rem;
      font-weight: 700;
    }
    
    h1 {
      font-size: 2.5rem;
      text-align: center;
      margin: 2rem 0;
      background: linear-gradient(to right, #4361ee, #3a0ca3);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    
    .box {
      background: white;
      border-radius: var(--border-radius);
      padding: 2rem;
      margin: 1.5rem auto;
      box-shadow: var(--box-shadow);
      transition: var(--transition);
      border: 1px solid rgba(0, 0, 0, 0.05);
    }
    
    .box:hover {
      box-shadow: 0 12px 24px rgba(0, 0, 0, 0.15);
    }
    
    .hidden {
      display: none;
    }
    
    /* تصميم حقول الإدخال والأزرار */
    input, select {
      width: 100%;
      padding: 12px 15px;
      margin: 8px 0;
      border: 1px solid #ddd;
      border-radius: var(--border-radius);
      font-family: 'Tajawal', sans-serif;
      font-size: 1rem;
      transition: var(--transition);
    }
    
    input:focus, select:focus {
      outline: none;
      border-color: var(--accent-color);
      box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.2);
    }
    
    button {
      background-color: var(--primary-color);
      color: white;
      border: none;
      padding: 12px 20px;
      border-radius: var(--border-radius);
      cursor: pointer;
      font-family: 'Tajawal', sans-serif;
      font-size: 1rem;
      font-weight: 500;
      transition: var(--transition);
      margin: 5px;
      display: inline-flex;
      align-items: center;
      justify-content: center;
    }
    
    button:hover {
      background-color: var(--secondary-color);
      transform: translateY(-2px);
    }
    
    button:active {
      transform: translateY(0);
    }
    
    button i {
      margin-left: 8px;
    }
    
    .btn-danger {
      background-color: var(--danger-color);
    }
    
    .btn-danger:hover {
      background-color: #d1145a;
    }
    
    .btn-success {
      background-color: var(--success-color);
    }
    
    .btn-success:hover {
      background-color: #3aa8d8;
    }
    
    .btn-outline {
      background: transparent;
      border: 2px solid var(--primary-color);
      color: var(--primary-color);
    }
    
    .btn-outline:hover {
      background: var(--primary-color);
      color: white;
    }
    
    /* تصميم المعلمين والحصص */
    .teacher, .student-teacher {
      border: 1px solid rgba(0, 0, 0, 0.1);
      border-radius: var(--border-radius);
      padding: 1.5rem;
      margin: 1rem 0;
      background: white;
      transition: var(--transition);
    }
    
    .teacher:hover, .student-teacher:hover {
      border-color: var(--accent-color);
    }
    
    .teacher h3, .student-teacher h3 {
      color: var(--secondary-color);
      margin-bottom: 1.2rem;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
    
    .lessons-list {
      margin-top: 1rem;
    }
    
    .lesson-item {
      display: flex;
      align-items: center;
      padding: 12px 15px;
      margin: 8px 0;
      background: var(--light-color);
      border-radius: 8px;
      transition: var(--transition);
    }
    
    .lesson-item:hover {
      background: #e9ecef;
    }
    
    .lesson-item span {
      flex: 1;
      text-align: right;
    }
    
    .lesson-item button {
      padding: 8px 12px;
      font-size: 0.9rem;
    }
    
    .lesson-btn {
      width: 100%;
      margin: 5px 0;
      text-align: right;
      justify-content: flex-start;
      background: var(--light-color);
      color: var(--dark-color);
    }
    
    .lesson-btn:hover {
      background: #e2e6ea;
      color: var(--dark-color);
    }
    
    /* تصميم مشغل الفيديو */
    #playerBox {
      position: relative;
    }
    
    #playerTitle {
      display: flex;
      align-items: center;
      justify-content: center;
      gap: 10px;
      color: var(--secondary-color);
    }
    
    video {
      width: 100%;
      border-radius: var(--border-radius);
      margin-top: 1rem;
      background: black;
      aspect-ratio: 16/9;
    }
    
    /* تصميم رسائل التنبيه */
    .alert {
      padding: 15px;
      border-radius: var(--border-radius);
      margin: 15px 0;
      font-weight: 500;
    }
    
    .alert-success {
      background-color: #d1fae5;
      color: #065f46;
      border: 1px solid #a7f3d0;
    }
    
    .alert-danger {
      background-color: #fee2e2;
      color: #b91c1c;
      border: 1px solid #fecaca;
    }
    
    /* شريط الأدوات */
    .toolbar {
      display: flex;
      justify-content: space-between;
      align-items: center;
      margin-bottom: 1.5rem;
    }
    
    /* تصميم متجاوب */
    @media (max-width: 768px) {
      .container {
        padding: 10px;
      }
      
      h1 {
        font-size: 1.8rem;
      }
      
      .box {
        padding: 1.2rem;
      }
      
      button {
        padding: 10px 15px;
      }
    }
    
    /* تأثيرات إضافية */
    .fade-in {
      animation: fadeIn 0.5s ease-in-out;
    }
    
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(10px); }
      to { opacity: 1; transform: translateY(0); }
    }
    
    .pulse {
      animation: pulse 2s infinite;
    }
    
    @keyframes pulse {
      0% { box-shadow: 0 0 0 0 rgba(67, 97, 238, 0.4); }
      70% { box-shadow: 0 0 0 10px rgba(67, 97, 238, 0); }
      100% { box-shadow: 0 0 0 0 rgba(67, 97, 238, 0); }
    }
  </style>
</head>
<body>
  <div class="container">
    <h1><i class="fas fa-chalkboard-teacher"></i> منصة الحصص المتقدمة</h1>

    <!-- 1. تسجيل الدخول -->
    <div class="box fade-in" id="loginBox">
      <h2><i class="fas fa-sign-in-alt"></i> تسجيل الدخول</h2>
      <input type="text" id="user" placeholder="اسم المستخدم">
      <input type="password" id="pass" placeholder="كلمة المرور">
      <button onclick="doLogin()"><i class="fas fa-sign-in-alt"></i> دخول</button>
    </div>

    <!-- 2. إدارة المعلمين (أدمن) -->
    <div class="box hidden fade-in" id="adminBox">
      <div class="toolbar">
        <h2><i class="fas fa-users-cog"></i> إدارة المعلمين والحصص</h2>
        <button class="btn-danger" onclick="logout()"><i class="fas fa-sign-out-alt"></i> تسجيل خروج</button>
      </div>
      
      <div class="alert alert-success">
        <i class="fas fa-info-circle"></i> مرحباً بك في لوحة التحكم، يمكنك إضافة وإدارة المعلمين والحصص التعليمية.
      </div>
      
      <div class="box" style="background: #f8f9fa;">
        <h3><i class="fas fa-plus-circle"></i> إضافة معلم جديد</h3>
        <input type="text" id="newTeacherName" placeholder="اسم المعلم">
        <button class="btn-success" onclick="addTeacher()"><i class="fas fa-user-plus"></i> إضافة معلم</button>
      </div>
      
      <div id="teachersAdminList"></div>
    </div>

    <!-- 3. عرض قائمة المعلمين والحصص (طالب وأدمن) -->
    <div class="box hidden fade-in" id="listBox">
      <div class="toolbar">
        <h2><i class="fas fa-list-ul"></i> قائمة المعلمين والحصص</h2>
        <button class="btn-outline" onclick="logout()"><i class="fas fa-sign-out-alt"></i> تسجيل خروج</button>
      </div>
      
      <div id="teachersList"></div>
    </div>

    <!-- 4. تشغيل الفيديو -->
    <div class="box hidden fade-in" id="playerBox">
      <h2 id="playerTitle"><i class="fas fa-video"></i> اختر حصة</h2>
      <video id="video" controls></video>
    </div>
  </div>

<script>
  // بيانات الدخول
  const ADMIN_USER = "admin", ADMIN_PASS = "1234";
  const STUDENT_USER = "student", STUDENT_PASS = "0000";
  const STORAGE_KEY = "teachersData";

  // قراءة/حفظ بيانات المعلمين
  function loadData() {
    return JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");
  }
  function saveData(d) {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(d));
  }

  // إدارة الجلسة
  let role = null;

  function doLogin() {
    const u = document.getElementById('user').value.trim();
    const p = document.getElementById('pass').value.trim();
    
    if (u === ADMIN_USER && p === ADMIN_PASS) {
      role = 'admin';
      showAlert('success', 'تم تسجيل الدخول بنجاح كمسؤول');
    } else if (u === STUDENT_USER && p === STUDENT_PASS) {
      role = 'student';
      showAlert('success', 'تم تسجيل الدخول بنجاح كطالب');
    } else { 
      showAlert('danger', 'بيانات الدخول غير صحيحة');
      return; 
    }

    document.getElementById('loginBox').classList.add('hidden');
    document.getElementById('listBox').classList.remove('hidden');
    document.getElementById('playerBox').classList.remove('hidden');
    if (role === 'admin') document.getElementById('adminBox').classList.remove('hidden');

    renderAdmin();
    renderList();
  }

  function showAlert(type, message) {
    const alert = document.createElement('div');
    alert.className = `alert alert-${type} fade-in`;
    alert.innerHTML = `<i class="fas fa-${type === 'success' ? 'check-circle' : 'exclamation-circle'}"></i> ${message}`;
    
    // إضافة التنبيه مؤقتاً
    document.body.appendChild(alert);
    setTimeout(() => {
      alert.classList.add('hidden');
      setTimeout(() => alert.remove(), 500);
    }, 3000);
  }

  function logout() {
    role = null;
    document.getElementById('loginBox').classList.remove('hidden');
    document.getElementById('adminBox').classList.add('hidden');
    document.getElementById('listBox').classList.add('hidden');
    document.getElementById('playerBox').classList.add('hidden');
    resetPlayer();
    showAlert('success', 'تم تسجيل الخروج بنجاح');
  }

  // Admin: إضافة/حذف معلمين
  function addTeacher() {
    const name = document.getElementById('newTeacherName').value.trim();
    if (!name) { 
      showAlert('danger', 'يجب إدخال اسم المعلم');
      document.getElementById('newTeacherName').focus();
      return; 
    }
    
    const d = loadData();
    d.push({ name, lessons: [] });
    saveData(d);
    document.getElementById('newTeacherName').value = '';
    renderAdmin();
    renderList();
    showAlert('success', `تم إضافة المعلم ${name} بنجاح`);
  }
  
  function delTeacher(idx) {
    const teachers = loadData();
    if (!confirm(`هل أنت متأكد من حذف المعلم "${teachers[idx].name}"؟`)) return;
    
    const d = loadData(); 
    d.splice(idx,1); 
    saveData(d);
    renderAdmin(); 
    renderList();
    showAlert('success', 'تم حذف المعلم بنجاح');
  }

  // Admin: إضافة/حذف حصص داخل كل معلم
  function addLesson(tidx) {
    const titleEl = document.getElementById(`lessonTitle${tidx}`);
    const linkEl  = document.getElementById(`lessonLink${tidx}`);
    const title = titleEl.value.trim(), link = linkEl.value.trim();
    
    if (!title || !link) { 
      showAlert('danger', 'يجب إدخال اسم الحصة والرابط');
      return; 
    }
    
    const d = loadData();
    d[tidx].lessons.push({ title, link });
    saveData(d);
    titleEl.value = '';
    linkEl.value = '';
    renderLessonsList(tidx);
    renderList();
    showAlert('success', `تم إضافة الحصة "${title}" بنجاح`);
  }
  
  function delLesson(tidx, lidx) {
    const lessons = loadData()[tidx].lessons;
    if (!confirm(`هل أنت متأكد من حذف الحصة "${lessons[lidx].title}"؟`)) return;
    
    const d = loadData(); 
    d[tidx].lessons.splice(lidx,1); 
    saveData(d);
    renderLessonsList(tidx); 
    renderList();
    showAlert('success', 'تم حذف الحصة بنجاح');
  }

  // عرض واجهة الأدمن
  function renderAdmin() {
    if (role !== 'admin') return;
    const container = document.getElementById('teachersAdminList');
    const data = loadData();
    container.innerHTML = '';
    
    if (data.length === 0) {
      container.innerHTML = `
        <div class="alert alert-danger">
          <i class="fas fa-info-circle"></i> لا يوجد معلمين مضافين بعد. قم بإضافة معلم جديد لبدء الإدارة.
        </div>
      `;
      return;
    }
    
    data.forEach((t, ti) => {
      const div = document.createElement('div'); 
      div.className = 'teacher fade-in';
      div.innerHTML = `
        <h3>
          <span><i class="fas fa-user-tie"></i> ${t.name}</span>
          <button class="btn-danger" onclick="delTeacher(${ti})"><i class="fas fa-trash-alt"></i> حذف المعلم</button>
        </h3>
        <div class="box" style="background: #f8f9fa; margin-top: 1rem;">
          <h4><i class="fas fa-plus-circle"></i> إضافة حصة جديدة</h4>
          <input type="text" id="lessonTitle${ti}" placeholder="اسم الحصة">
          <input type="text" id="lessonLink${ti}" placeholder="رابط m3u8">
          <button class="btn-success" onclick="addLesson(${ti})"><i class="fas fa-plus"></i> إضافة حصة</button>
        </div>
        <div id="lessonsList${ti}" class="lessons-list"></div>
      `;
      container.appendChild(div);
      renderLessonsList(ti);
    });
  }
  
  function renderLessonsList(tidx) {
    const listEl = document.getElementById(`lessonsList${tidx}`);
    const lessons = loadData()[tidx].lessons;
    listEl.innerHTML = '';
    
    if (lessons.length === 0) {
      listEl.innerHTML = `
        <div class="alert alert-danger">
          <i class="fas fa-info-circle"></i> لا توجد حصص لهذا المعلم بعد.
        </div>
      `;
      return;
    }
    
    lessons.forEach((l, li) => {
      const item = document.createElement('div'); 
      item.className = 'lesson-item fade-in';
      item.innerHTML = `
        <span><i class="fas fa-play-circle"></i> ${li+1}. ${l.title}</span>
        <button class="btn-danger" onclick="delLesson(${tidx},${li})"><i class="fas fa-trash-alt"></i></button>
        <button onclick="play(${tidx},${li})"><i class="fas fa-play"></i> تشغيل</button>
      `;
      listEl.appendChild(item);
    });
  }

  // عرض قائمة للطالب
  function renderList() {
    const container = document.getElementById('teachersList');
    const data = loadData();
    container.innerHTML = '';
    
    if (!data.length) { 
      container.innerHTML = `
        <div class="alert alert-danger">
          <i class="fas fa-info-circle"></i> لا توجد معلمين مضافين بعد.
        </div>
      `; 
      return; 
    }
    
    data.forEach((t, ti) => {
      const div = document.createElement('div'); 
      div.className = 'student-teacher fade-in';
      div.innerHTML = `<h3><i class="fas fa-user-tie"></i> ${t.name}</h3>`;
      
      if (t.lessons.length === 0) {
        div.innerHTML += `
          <div class="alert alert-danger">
            <i class="fas fa-info-circle"></i> لا توجد حصص متاحة لهذا المعلم.
          </div>
        `;
      } else {
        t.lessons.forEach((l, li) => {
          const btn = document.createElement('button');
          btn.className = 'lesson-btn'; 
          btn.innerHTML = `<i class="fas fa-play-circle"></i> ${l.title}`;
          btn.onclick = () => play(ti, li);
          div.appendChild(btn);
        });
      }
      
      container.appendChild(div);
    });
  }

  // تشغيل فيديو
  function play(tidx, lidx) {
    const lesson = loadData()[tidx].lessons[lidx];
    document.getElementById('playerTitle').innerHTML = `<i class="fas fa-play"></i> ${lesson.title}`;
    const video = document.getElementById('video');
    
    // إظهار تأثير تحميل
    video.innerHTML = '<div style="color:white;display:flex;justify-content:center;align-items:center;height:100%;"><i class="fas fa-spinner fa-spin fa-3x"></i></div>';
    
    if (Hls.isSupported()) {
      const hls = new Hls(); 
      hls.loadSource(lesson.link); 
      hls.attachMedia(video);
      hls.on(Hls.Events.MANIFEST_PARSED, () => video.play());
    } else {
      video.src = lesson.link; 
      video.play();
    }
  }

  // إعادة تعيين المشغل
  function resetPlayer() {
    document.getElementById('playerTitle').innerHTML = '<i class="fas fa-video"></i> اختر حصة';
    document.getElementById('video').src = '';
    document.getElementById('video').innerHTML = '';
  }

  document.addEventListener('DOMContentLoaded', () => {
    resetPlayer();
    
    // إضافة تأثير عند التركيز على حقول الإدخال
    const inputs = document.querySelectorAll('input');
    inputs.forEach(input => {
      input.addEventListener('focus', function() {
        this.parentNode.classList.add('pulse');
      });
      input.addEventListener('blur', function() {
        this.parentNode.classList.remove('pulse');
      });
    });
  });
</script>
</body>
</html>
