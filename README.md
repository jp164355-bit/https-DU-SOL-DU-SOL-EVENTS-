
<html lang="en">
<head>
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>DU SOL Event Management Portal</title>
<style>
  * { box-sizing: border-box; }
  body { margin:0; font-family: 'Segoe UI', -apple-system, BlinkMacSystemFont, Arial, sans-serif; background: linear-gradient(135deg, #f6f8fa 0%, #e9ecef 100%); line-height: 1.6; }
   /* Header Enhancements */
  header { background: linear-gradient(135deg, #143058 0%, #1a3d6e 100%); padding:25px 20px; color:#fff; text-align:center; position: relative; overflow: hidden; }
  header::before { content: ''; position: absolute; top: 0; left: 0; right: 0; bottom: 0; background: url('data:image/svg+xml,<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 100 100"><defs><pattern id="grain" width="100" height="100" patternUnits="userSpaceOnUse"><circle cx="25" cy="25" r="1" fill="rgba(255,255,255,0.05)"/><circle cx="75" cy="75" r="1.5" fill="rgba(255,255,255,0.03)"/></pattern></defs><rect width="100" height="100" fill="url(%23grain)"/></svg>'); }
  .logo { width:90px; height:90px; border-radius:50%; box-shadow:0 8px 24px rgba(45,120,209,0.3); margin-bottom:15px; animation: pulse 2s infinite; border: 3px solid rgba(253,200,1,0.3); }
  @keyframes pulse { 0%, 100% { transform: scale(1); } 50% { transform: scale(1.05); } }
  h1 { margin:0 0 12px 0; font-size:2.4em; font-weight: 700; letter-spacing: -0.5px; text-shadow: 0 2px 8px rgba(0,0,0,0.3); }
  .hero-subtitle { font-size:1.1em; opacity: 0.95; margin-bottom: 20px; }
  .hero-img { width:98vw; max-width:480px; max-height: 220px; object-fit: cover; border-radius:16px; box-shadow:0 12px 40px rgba(45,120,209,0.25); margin-top:18px; transition: transform 0.4s ease; }
  .hero-img:hover { transform: scale(1.02); }
/* Navigation & Buttons */
  nav { margin:24px 0; }
  .login-btn { background: linear-gradient(135deg, #2d78d1 0%, #1e5fa5 100%); color:#fff; font-size:1.2em; font-weight: 600; padding:14px 36px; border-radius:12px; text-decoration:none; transition:all .3s cubic-bezier(0.4,0,0.2,1); cursor:pointer; border:none; box-shadow:0 4px 16px rgba(45,120,209,0.3); position: relative; overflow: hidden; }
  .login-btn::before { content: ''; position: absolute; top: 0; left: -100%; width: 100%; height: 100%; background: linear-gradient(90deg, transparent, rgba(255,255,255,0.3), transparent); transition: left 0.5s; }
  .login-btn:hover::before { left: 100%; }
  .login-btn:hover { background: linear-gradient(135deg, #fdc801 0%, #ffb800 100%); color:#143058; transform: translateY(-2px); box-shadow:0 8px 24px rgba(253,200,1,0.4); }
/* Login Section */
  #login-section { background: rgba(255,255,255,0.95); backdrop-filter: blur(20px); max-width:380px; margin:40px auto 24px; box-shadow:0 12px 48px rgba(20,48,88,0.15); border-radius:20px; text-align:center; padding:32px 20px; border:1px solid rgba(255,255,255,0.3); }
  .login-choice { display:flex; gap:24px; justify-content:center; margin-bottom:24px; flex-wrap: wrap; }
  .role-btn { width:82px; height:82px; background: linear-gradient(135deg, #2d78d1 0%, #1e5fa5 100%); color:#fff; font-size:1.1em; font-weight: 600; border-radius:50%; border:none; cursor:pointer; transition:all .3s cubic-bezier(0.4,0,0.2,1); box-shadow:0 6px 20px rgba(45,120,209,0.3); position: relative; }
  .role-btn::after { content: attr(data-role); position: absolute; bottom: -30px; left: 50%; transform: translateX(-50%); font-size: 0.85em; opacity: 0; transition: opacity 0.3s; white-space: nowrap; }
  .role-btn:hover { background: linear-gradient(135deg, #fdc801 0%, #ffb800 100%); color:#143058; transform: scale(1.12) translateY(-4px); box-shadow:0 12px 32px rgba(253,200,1,0.4); }
  .role-btn:hover::after { opacity: 1; }
  label { display:block; margin:18px 0 8px; text-align:left; font-weight: 600; color: #2c3e50; }
  input[type=text], input[type=email], input[type=password], input[type=tel], select { width:100%; padding:12px 16px; margin-bottom:16px; border-radius:10px; border:2px solid #e1e8ed; transition:all 0.3s ease; font-size: 1em; background: rgba(255,255,255,0.8); }
  input:focus, select:focus { outline: none; border-color: #2d78d1; box-shadow: 0 0 0 3px rgba(45,120,209,0.1); transform: translateY(-1px); }
  .submit-btn { background: linear-gradient(135deg, #2d78d1 0%, #1e5fa5 100%); color:#fff; padding:14px 0; width:100%; border:none; font-size:1.15em; font-weight: 600; border-radius:12px; margin-top:12px; cursor:pointer; transition:all .3s cubic-bezier(0.4,0,0.2,1); box-shadow:0 6px 20px rgba(45,120,209,0.3); }
  .submit-btn:hover { background: linear-gradient(135deg, #fdc801 0%, #ffb800 100%); color:#143058; transform: translateY(-2px); box-shadow:0 10px 30px rgba(253,200,1,0.4); }
/* Dashboard Sections */
  #dashboard-section, #organizer-section, #registration-section, #help-center { display:none; background: rgba(255,255,255,0.97); backdrop-filter: blur(20px); border-radius:24px; box-shadow:0 16px 64px rgba(20,48,88,0.12); max-width:780px; margin:50px auto 28px; padding:32px 28px; border:1px solid rgba(255,255,255,0.4); }
  .dash-header { display:flex; gap:20px; align-items:center; margin-bottom:20px; position: relative; padding-bottom: 16px; border-bottom: 2px solid #f0f4f8; }
  .icon { width:52px; height:52px; background: linear-gradient(135deg, #fdc801 0%, #ffb800 100%); color:#143058; border-radius:50%; display:flex; align-items:center; justify-content:center; font-size:1.8em; box-shadow:0 6px 24px rgba(253,200,1,0.4); cursor:pointer; transition:all 0.3s ease; position: relative; }
  .icon:hover { transform: scale(1.1) rotate(5deg); box-shadow:0 10px 32px rgba(253,200,1,0.5); }
  .role-show { margin-left:auto; font-size:1.15em; color:#2d78d1; font-weight: 700; user-select:none; background: linear-gradient(135deg, #2d78d1, #1e5fa5); -webkit-background-clip: text; -webkit-text-fill-color: transparent; }
/* Event Cards & Lists */
  .location-list, .event-list, #eventsContainer { margin-top:24px; }
  .event-card { background: linear-gradient(135deg, #f8f9ff 0%, #f6f8fa 100%); border-radius:20px; box-shadow:0 8px 32px rgba(45,120,209,0.12); margin-bottom:28px; display:flex; align-items:flex-start; gap:24px; padding:24px; transition:all 0.4s cubic-bezier(0.4,0,0.2,1); border:1px solid rgba(45,120,209,0.1); position: relative; overflow: hidden; }
  .event-card::before { content: ''; position: absolute; top: 0; left: 0; right: 0; height: 4px; background: linear-gradient(90deg, #2d78d1, #fdc801, #2d78d1); }
  .event-card:hover { transform: translateY(-8px); box-shadow:0 20px 48px rgba(45,120,209,0.2); }
  .event-icon { width:72px; height:72px; object-fit:cover; border-radius:16px; box-shadow:0 8px 24px rgba(0,0,0,0.15); transition: transform 0.3s ease; }
  .event-card:hover .event-icon { transform: scale(1.1); }
  .event-info { flex:1; }
  .event-title { font-size:1.25em; margin:0 0 8px 0; font-weight: 700; color: #1a1a1a; line-height: 1.3; }
  .event-desc { font-size:1em; color: #5a6c7d; margin-bottom: 12px; line-height: 1.5; }
  .event-meta { display: flex; gap: 16px; font-size: 0.95em; color: #6c757d; margin-bottom: 12px; flex-wrap: wrap; }
  .map-link { color:#2d78d1; font-weight:700; text-decoration:none; padding: 4px 8px; border-radius: 6px; transition: all 0.3s ease; background: rgba(45,120,209,0.1); }
  .map-link:hover { background: rgba(45,120,209,0.2); text-decoration:none; transform: translateY(-1px); }
  .register-btn, .delete-btn { padding:10px 20px; border:none; border-radius:10px; cursor:pointer; transition:all .3s ease; font-weight: 600; font-size: 0.95em; }
  .register-btn { background: linear-gradient(135deg, #2d78d1 0%, #1e5fa5 100%); color:#fff; margin-left: auto; }
  .register-btn:hover { background: linear-gradient(135deg, #fdc801 0%, #ffb800 100%); color:#143058; transform: translateY(-2px); box-shadow:0 6px 20px rgba(253,200,1,0.3); }
  .delete-btn { background: linear-gradient(135deg, #fd5050 0%, #e63946 100%); color:#fff; margin-top:12px; }
  .delete-btn:hover { transform: translateY(-2px); box-shadow:0 6px 20px rgba(253,80,80,0.4); }
 /* Forms */
  #organizer-section h2, #registration-section h2, #help-center h2 { margin-bottom: 24px; font-size: 1.8em; color: #143058; text-align: center; position: relative; }
  #organizer-section h2::after, #registration-section h2::after, #help-center h2::after { content: ''; position: absolute; bottom: -8px; left: 50%; transform: translateX(-50%); width: 60px; height: 4px; background: linear-gradient(90deg, #2d78d1, #fdc801); border-radius: 2px; }
  form#eventForm, form#registrationForm { display:flex; flex-direction:column; gap:18px; }
  form#eventForm input[type=text], form#eventForm input[type=date], form#eventForm textarea, form#eventForm input[type=file],
  form#registrationForm input[type=text], form#registrationForm input[type=email], form#registrationForm input[type=tel], form#registrationForm select { 
    border-radius:12px; border:2px solid #e1e8ed; padding:14px 18px; font-size:1.05em; width:100%; transition:all 0.3s ease; background: rgba(255,255,255,0.9); }
  form#eventForm textarea, form#registrationForm textarea { resize:vertical; min-height: 100px; }
  form input:focus, form textarea:focus, form select:focus { outline: none; border-color: #2d78d1; box-shadow: 0 0 0 3px rgba(45,120,209,0.1); }
  form button { background: linear-gradient(135deg, #2d78d1 0%, #1e5fa5 100%); color:#fff; border:none; padding:16px; border-radius:12px; cursor:pointer; font-size:1.15em; font-weight: 600; transition:all .3s cubic-bezier(0.4,0,0.2,1); box-shadow:0 6px 20px rgba(45,120,209,0.3); }
  form button:hover { background: linear-gradient(135deg, #fdc801 0%, #ffb800 100%); color:#143058; transform: translateY(-2px); box-shadow:0 12px 32px rgba(253,200,1,0.4); }
 /* Help Center */
  .help-center-grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 24px; margin-top: 24px; }
  .help-card { background: linear-gradient(135deg, #f8f9ff 0%, #f6f8fa 100%); border-radius: 16px; padding: 24px; box-shadow: 0 8px 32px rgba(45,120,209,0.1); border: 1px solid rgba(45,120,209,0.15); transition: all 0.3s ease; cursor: pointer; }
  .help-card:hover { transform: translateY(-4px); box-shadow: 0 16px 48px rgba(45,120,209,0.2); }
  .help-icon { font-size: 2.5em; margin-bottom: 16px; display: block; }
  .help-title { font-size: 1.3em; font-weight: 700; margin-bottom: 12px; color: #143058; }
  .help-desc { color: #5a6c7d; line-height: 1.6; }
  .search-help { width: 100%; padding: 14px 18px; border-radius: 12px; border: 2px solid #e1e8ed; font-size: 1.05em; margin-bottom: 24px; }
  .search-help:focus { outline: none; border-color: #2d78d1; box-shadow: 0 0 0 3px rgba(45,120,209,0.1); }
/* Logout Button */
  .logout-fixed-btn {
    position: fixed; top: 24px; right: 24px; background: linear-gradient(135deg, #fdc801 0%, #ffb800 100%);
    color: #143058; padding: 14px 24px; border: none; border-radius: 30px; font-weight: 700; font-size: 1em;
    cursor: pointer; box-shadow: 0 8px 24px rgba(253,200,1,0.4); z-index: 10001; transition: all .3s ease;
  }
  .logout-fixed-btn:hover { background: linear-gradient(135deg, #2d78d1 0%, #1e5fa5 100%); color:#fff; transform: translateY(-2px); box-shadow:0 12px 32px rgba(45,120,209,0.5); }
/* Chatbot Enhancements */
  .chatbot-icon {
    position: fixed; right: 24px; bottom: 24px; font-size: 2.2em; background: linear-gradient(135deg, #2d78d1, #1e5fa5);
    color: #fff; border-radius: 50%; width: 60px; height: 60px; display: flex; align-items: center; justify-content: center;
    box-shadow: 0 12px 40px rgba(20,48,88,0.4); cursor: pointer; animation: bounceChat 2s infinite alternate;
    z-index: 10000; transition: all 0.3s ease;
  }
  .chatbot-icon:hover { transform: scale(1.1); box-shadow: 0 16px 48px rgba(20,48,88,0.5); }
  @keyframes bounceChat { 0% {transform: translateY(0) scale(1);} 100% {transform: translateY(-12px) scale(1.05);} }
  .chatbox {
    position: fixed; right: 24px; bottom: 100px; background: rgba(255,255,255,0.98); backdrop-filter: blur(25px);
    border-radius: 20px; box-shadow: 0 16px 64px rgba(45,120,209,0.25); padding: 24px; width: 320px; max-height: 400px;
    z-index: 10001; border:1px solid rgba(45,120,209,0.2); overflow-y: auto;
  }
  .chatbox input { width: 65%; padding: 12px 16px; margin-right: 12px; border-radius: 12px; border:2px solid #e1e8ed; outline:none; font-size: 1em; }
  .chatbox button { padding: 12px 20px; background:linear-gradient(135deg, #2d78d1, #1e5fa5); color:#fff; border:none; border-radius: 12px; cursor: pointer; font-weight: 600; transition: all 0.3s ease; }
  .chatbox button:hover { background:linear-gradient(135deg, #fdc801, #ffb800); color:#143058; transform: translateY(-1px); }
/* Responsive */
  @media (max-width:768px) {
    .login-choice { flex-direction: column; align-items: center; gap: 16px; }
    #dashboard-section, #organizer-section, #registration-section, #help-center { margin: 24px 16px; padding: 24px 20px; }
    .event-card { flex-direction: column; gap: 20px; text-align: center; }
    .dash-header { flex-direction: column; gap: 16px; text-align: center; }
    .logout-fixed-btn { top: 20px; right: 20px; padding: 12px 20px; font-size: 0.95em; }
    .chatbox { width: calc(100vw - 48px); right: 24px; bottom: 90px; }
  }
 /* Animations */
  @keyframes fadeInUp { from { opacity: 0; transform: translateY(30px); } to { opacity: 1; transform: translateY(0); } }
  .event-card, .help-card { animation: fadeInUp 0.6s ease forwards; }
</style>
</head>
<body>

 <header>
  <img src="https://github.com/user-attachments/assets/4abc5761-14fa-4dca-8d36-c7ef8118590a" class="logo" alt="DU SOL Logo" />
  <h1>Delhi University School of Open Learning</h1>
  <p class="hero-subtitle">Event Management Portal</p>
  <img src="https://github.com/user-attachments/assets/be0e5e85-36f3-4dd1-b6c8-6343f422e673" class="hero-img" alt="DU SOL Campus" />
</header>

<!-- LOGIN PAGE -->
<section id="login-section">
  <div class="login-choice">
    <button class="role-btn" data-role="Event Organizer" onclick="startLogin('Organizer')">👥 Organizer</button>
    <button class="role-btn" data-role="Student" onclick="startLogin('Student')">🎓 Student</button>
  </div>
  <form id="loginForm" style="display:none;" autocomplete="off">
    <label>Role: <input type="text" id="roleField" readonly /></label>
    <label>College ID: <input type="text" id="collegeIdField" required pattern="SOL[0-9]{8}" placeholder="SOL20251234" /></label>
    <label>Password: <input type="password" id="passwordField" required /></label>
    <button class="submit-btn" type="submit">🚀 Login Securely</button>
  </form>
</section>

<!-- STUDENT DASHBOARD -->
<section id="dashboard-section">
  <div class="dash-header">
    <div class="icon" title="Current Location" onclick="showHelpCenter()">📍</div>
    <div class="icon" title="Smart Help Center" onclick="showHelpCenter()">🆘</div>
    <span class="role-show" id="userRoleDisp"></span>
  </div>
  <h2>🎉 Upcoming Events</h2>
  <div class="location-list" id="event-list"></div>
</section>

<!-- EVENT REGISTRATION -->
<section id="registration-section">
  <h2>📝 Event Registration Form</h2>
  <form id="registrationForm" enctype="multipart/form-data">
    <label for="idCard">🆔 Upload ID Card Photo *</label>
    <input type="file" id="idCard" accept="image/*" required />
    
   <label for="studentName">👤 Full Name *</label>
    <input type="text" id="studentName" required />
    
   <label for="rollNumber">🎫 Roll Number *</label>
    <input type="text" id="rollNumber" required />
    
   <label for="phoneNumber">📱 Phone Number *</label>
    <input type="tel" id="phoneNumber" required />
    
   <label for="emailAddress">✉️ Email Address *</label>
    <input type="email" id="emailAddress" required />
    
   <label for="studentYear">📚 Student Year *</label>
    <select id="studentYear" required>
      <option value="" disabled selected>Select Academic Year</option>
      <option value="1st Year">1st Year</option>
      <option value="2nd Year">2nd Year</option>
      <option value="3rd Year">3rd Year</option>
      <option value="4th Year">4th Year</option>
    </select>
    
   <button type="submit">✅ Submit Registration</button>
  </form>
</section>

<!-- ORGANIZER DASHBOARD -->
<section id="organizer-section">
  <h2>⚙️ Organizer Dashboard</h2>
  <p style="text-align:center; color:#6c757d; margin-bottom:24px;">Create & Manage Events for DU SOL Students</p>
  
  <form id="eventForm">
    <label for="eventName">🎯 Event Name</label>
    <input type="text" id="eventName" placeholder="e.g., Annual Cultural Fest" required />
    
   <label for="eventDate">📅 Event Date</label>
    <input type="date" id="eventDate" required />
    
   <label for="eventLocation">📍 Venue Location</label>
    <input type="text" id="eventLocation" placeholder="e.g., North Campus, DU SOL Center" required />
    
   <label for="eventDesc">📄 Event Description</label>
    <textarea id="eventDesc" rows="4" placeholder="Describe your event, schedule, activities..." required></textarea>
    
   <label for="eventImage">🖼️ Event Banner Image</label>
    <input type="file" id="eventImage" accept="image/*" />
    
   <button type="submit">➕ Create New Event</button>
  </form>
  
  <h3 style="margin:28px 0 20px 0;">📋 Existing Events</h3>
  <div id="eventsContainer"></div>
</section>

<!-- HELP CENTER -->
<section id="help-center">
  <h2>🆘 Help Center</h2>
  <input type="text" class="search-help" id="helpSearch" placeholder="🔍 Search help articles... (e.g., 'login', 'register', 'create event')">
  
  <div class="help-center-grid" id="helpGrid">
    <div class="help-card" onclick="showHelpDetail('login')">
      <span class="help-icon">🔐</span>
      <div class="help-title">How to Login</div>
      <div class="help-desc">Login as Organizer or Student using your SOL College ID (SOLXXXXXXXX format).</div>
    </div>
    
   <div class="help-card" onclick="showHelpDetail('student')">
      <span class="help-icon">🎓</span>
      <div class="help-title">Student Features</div>
      <div class="help-desc">Browse events, register with ID proof, view campus maps & get notifications.</div>
    </div>
    
   <div class="help-card" onclick="showHelpDetail('organizer')">
      <span class="help-icon">👥</span>
      <div class="help-title">Organizer Tools</div>
      <div class="help-desc">Create events with images, manage listings, delete events & track registrations.</div>
    </div>
    
   <div class="help-card" onclick="showHelpDetail('register')">
      <span class="help-icon">📝</span>
      <div class="help-title">Event Registration</div>
      <div class="help-desc">Complete registration form with ID photo, personal details & academic year.</div>
    </div>
    
   <div class="help-card" onclick="showHelpDetail('campus')">
      <span class="help-icon">📍</span>
      <div class="help-title">Campus Maps</div>
      <div class="help-desc">Interactive Google Maps links for North Campus, SOL Center & other venues.</div>
    </div>
    
   <div class="help-card" onclick="showHelpDetail('contact')">
      <span class="help-icon">📞</span>
      <div class="help-title">Contact Support</div>
      <div class="help-desc">DU SOL Admin: events@sol.du.ac.in | Emergency: +91-XXXXXXXXXX</div>
    </div>
  </div>
</section>

<button class="logout-fixed-btn" id="fixedLogout">🚪 Logout</button>

<!-- Chatbot -->
<div class="chatbot-icon" title="AI Help Assistant">💬</div>

<script>
  // DOM Elements
  const loginSection = document.getElementById('login-section');
  const dashboardSection = document.getElementById('dashboard-section');
  const organizerSection = document.getElementById('organizer-section');
  const registrationSection = document.getElementById('registration-section');
  const helpCenterSection = document.getElementById('help-center');
  const loginForm = document.getElementById('loginForm');
  const userRoleDisp = document.getElementById('userRoleDisp');
  const fixedLogoutBtn = document.getElementById('fixedLogout');
  const eventsContainer = document.getElementById('eventsContainer');
  const eventList = document.getElementById('event-list');
  const registrationForm = document.getElementById('registrationForm');

  // Data Storage
  let globalEvents = [
    {name: '🎉 Annual Cultural Fest - North Campus', date: '2025-12-15', location: 'North Campus, Delhi University', desc: 'Music performances, dance competitions, food festival & celebrity guest performances.', imgData: 'assets/images/north-campus.jpg', mapLink: 'https://www.google.com/maps?q=28.693165,77.213016'},
    {name: '💼 Career Guidance Workshop - SOL Center', date: '2025-12-05', location: 'School of Open Learning, North Delhi', desc: 'Resume building, interview skills, corporate networking & placement opportunities.', imgData: 'assets/images/sol-campus.jpg', mapLink: 'https://www.google.com/maps?q=28.682366,77.206839'},
    {name: '🎓 Alumni Meet & Interactive Session', date: '2025-12-20', location: 'DU SOL Auditorium', desc: 'Connect with successful alumni, live Q&A, mentorship opportunities & networking.', imgData: null, mapLink: 'https://www.google.com/maps?q=DU+SOL+Auditorium'}
  ];

  let currentUserRole = null;
  let currentRegisterEvent = null;
  let registrations = [];
  let helpDetailsVisible = false;

  // Enhanced Login
  function startLogin(role) {
    document.getElementById('roleField').value = role;
    loginForm.style.display = 'block';
    document.getElementById('collegeIdField').focus();
  }

  loginForm.addEventListener('submit', function (e) {
    e.preventDefault();
    const role = document.getElementById('roleField').value;
    const collegeId = document.getElementById('collegeIdField').value.trim();
    
    if (!/^SOL[0-9]{8}$/.test(collegeId)) {
      alert('❌ Invalid College ID!\n\nFormat must be: SOLXXXXXXXX\nExample: SOL20251234');
      document.getElementById('collegeIdField').focus();
      return;
    }
    
    // Simulate authentication
    setTimeout(() => {
      currentUserRole = role;
      loginSection.style.display = 'none';
      fixedLogoutBtn.style.display = 'block';
      userRoleDisp.innerHTML = `Logged in as: <strong>${role}</strong>`;
      
      if (role === 'Student') {
        showStudentDashboard();
      } else {
        showOrganizerDashboard();
      }
    }, 800);
  });

  // Student Dashboard
  function showStudentDashboard() {
    registrationSection.style.display = 'none';
    organizerSection.style.display = 'none';
    helpCenterSection.style.display = 'none';
    renderStudentEvents();
    dashboardSection.style.display = 'block';
  }

  function renderStudentEvents() {
    eventList.innerHTML = '';
    if (globalEvents.length === 0) {
      eventList.innerHTML = '<div style="text-align:center; padding:40px; color:#6c757d;"><h3>📭 No Upcoming Events</h3><p>Check back soon for exciting events at DU SOL!</p></div>';
      return;
    }
    
    globalEvents.forEach((ev, idx) => {
      const div = document.createElement('div');
      div.className = 'event-card';
      div.innerHTML = `
        <img src="${ev.imgData || 'https://images.unsplash.com/photo-1517457373958-b7bdd4587206?w=300&h=300&fit=crop'}" alt="${ev.name}" class="event-icon" onerror="this.src='https://images.unsplash.com/photo-1517457373958-b7bdd4587206?w=300&h=300&fit=crop'" />
        <div class="event-info">
          <div class="event-title">${ev.name}</div>
          <div class="event-desc">${ev.desc}</div>
          <div class="event-meta">
            <span>📅 ${new Date(ev.date).toLocaleDateString('en-IN', {weekday:'short', year:'numeric', month:'short', day:'numeric'})}</span>
            <span>📍 ${ev.location}</span>
          </div>
          <div>
            <a href="${ev.mapLink}" target="_blank" class="map-link">🗺️ View Campus Map</a>
            <button class="register-btn" onclick="openRegistrationForm(${idx})">📝 Register Now</button>
          </div>
        </div>
      `;
      eventList.appendChild(div);
    });
  }

  // Registration
  function openRegistrationForm(eventIndex) {
    currentRegisterEvent = eventIndex;
    dashboardSection.style.display = 'none';
    organizerSection.style.display = 'none';
    helpCenterSection.style.display = 'none';
    registrationSection.style.display = 'block';
    document.getElementById('studentName').focus();
  }

  registrationForm.addEventListener('submit', function (e) {
    e.preventDefault();
    const idCardFile = document.getElementById('idCard').files[0];
    
    if (!idCardFile) {
      alert('❌ Please upload your ID card photo to complete registration.');
      return;
    }

    const formData = {
      event: globalEvents[currentRegisterEvent].name,
      name: document.getElementById('studentName').value.trim(),
      roll: document.getElementById('rollNumber').value.trim(),
      phone: document.getElementById('phoneNumber').value.trim(),
      email: document.getElementById('emailAddress').value.trim(),
      year: document.getElementById('studentYear').value,
      timestamp: new Date().toLocaleString('en-IN')
    };

    const reader = new FileReader();
    reader.onload = function (event) {
      formData.idCard = event.target.result;
      registrations.push(formData);
      
      // Success animation
      const btn = registrationForm.querySelector('button');
      const originalText = btn.textContent;
      btn.textContent = '✅ Registration Successful!';
      btn.style.background = 'linear-gradient(135deg, #28a745, #20c997)';
      
      setTimeout(() => {
        btn.textContent = originalText;
        btn.style.background = '';
        alert(`🎉 Registration confirmed!\n\nEvent: ${globalEvents[currentRegisterEvent].name}\nConfirmation ID: REG-${Date.now().toString().slice(-6)}`);
        showStudentDashboard();
      }, 2000);
    };
    reader.readAsDataURL(idCardFile);
  });

  // Organizer Dashboard
  function showOrganizerDashboard() {
    dashboardSection.style.display = 'none';
    registrationSection.style.display = 'none';
    helpCenterSection.style.display = 'none';
    organizerSection.style.display = 'block';
    renderOrganizerEvents();
  }

  function renderOrganizerEvents() {
    if (globalEvents.length === 0) {
      eventsContainer.innerHTML = '<div style="text-align:center; padding:40px; color:#6c757d;"><h3>📭 No Events Created</h3><p>Create your first event using the form above!</p></div>';
      return;
    }
    
    eventsContainer.innerHTML = '';
    globalEvents.forEach((ev, idx) => {
      const div = document.createElement('div');
      div.className = 'event-card';
      div.innerHTML = `
        <img src="${ev.imgData || 'https://images.unsplash.com/photo-1517457373958-b7bdd4587206?w=300&h=300&fit=crop'}" alt="${ev.name}" class="event-icon" onerror="this.src='https://images.unsplash.com/photo-1517457373958-b7bdd4587206?w=300&h=300&fit=crop'" />
        <div class="event-info">
          <div class="event-title">${ev.name}</div>
          <div class="event-desc">${ev.desc}</div>
          <div class="event-meta">
            <span>📅 ${new Date(ev.date).toLocaleDateString('en-IN', {weekday:'short', year:'numeric', month:'short', day:'numeric'})}</span>
            <span>📍 ${ev.location}</span>
            <span>📊 ${registrations.filter(r => r.event === ev.name).length} Registrations</span>
          </div>
          <button class="delete-btn" onclick="deleteEvent(${idx})">🗑️ Delete Event</button>
        </div>
      `;
      eventsContainer.appendChild(div);
    });
  }

  function deleteEvent(index) {
    if (confirm(`⚠️ Delete "${globalEvents[index].name}"?\n\nThis cannot be undone.\n${registrations.filter(r => r.event === globalEvents[index].name).length} students are registered.`)) {
      globalEvents.splice(index, 1);
      renderOrganizerEvents();
      if (currentUserRole === 'Student') renderStudentEvents();
      alert('✅ Event deleted successfully.');
    }
  }

  // Event Creation
  document.getElementById('eventForm').addEventListener('submit', function (e) {
    e.preventDefault();
    const formData = {
      name: document.getElementById('eventName').value.trim(),
      date: document.getElementById('eventDate').value,
      location: document.getElementById('eventLocation').value.trim(),
      desc: document.getElementById('eventDesc').value.trim()
    };

    const fileInput = document.getElementById('eventImage');
    const file = fileInput.files[0];

    if (file) {
      const reader = new FileReader();
      reader.onload = function (event) {
        formData.imgData = event.target.result;
        formData.mapLink = `https://www.google.com/maps?q=${encodeURIComponent(formData.location)}`;
        globalEvents.push(formData);
        renderOrganizerEvents();
        renderStudentEvents();
        this.reset();
        alert('🎉 Event created successfully!');
      };
      reader.readAsDataURL(file);
    } else {
      formData.imgData = null;
      formData.mapLink = `https://www.google.com/maps?q=${encodeURIComponent(formData.location)}`;
      globalEvents.push(formData);
      renderOrganizerEvents();
      renderStudentEvents();
      this.reset();
      alert('✅ Event created successfully! (Add image next time for better visuals)');
    }
  });

  // Help Center
  function showHelpCenter() {
    dashboardSection.style.display = 'none';
    organizerSection.style.display = 'none';
    registrationSection.style.display = 'none';
    helpCenterSection.style.display = 'block';
  }

  document.getElementById('helpSearch').addEventListener('input', function(e) {
    const query = e.target.value.toLowerCase();
    const cards = document.querySelectorAll('.help-card');
    cards.forEach(card => {
      const text = card.textContent.toLowerCase();
      card.style.display = text.includes(query) ? 'block' : 'none';
    });
  });

  function showHelpDetail(topic) {
    const messages = {
      login: "🔐 **Login Guide**\n• Click Organizer or Student button\n• Enter SOLXXXXXXXX format\n• Use your secure password\n• Click Login Securely",
      student: "🎓 **Student Dashboard**\n• View all upcoming events\n• Click REGISTER on any event\n• Upload ID + fill details\n• Get instant confirmation",
      organizer: "👥 **Organizer Tools**\n• Create events with images\n• Auto Google Maps links\n• View registration count\n• Delete events anytime",
      register: "📝 **Registration Steps**\n1. Click REGISTER on event\n2. Upload clear ID photo\n3. Fill all details accurately\n4. Submit for confirmation",
      campus: "📍 **Campus Navigation**\n• North Campus: 28.693165,77.213016\n• SOL Center: 28.682366,77.206839\n• Click MAP LINKS for directions",
      contact: "📞 **Support Contacts**\n• Email: events@sol.du.ac.in\n• Phone: +91-XXXXXXXXXX\n• Emergency: +91-XXXXXXXXXX\n• Office Hours: 9AM-6PM"
    };
    alert(messages[topic] || 'Select from help cards above!');
  }

  // Logout
  fixedLogoutBtn.onclick = () => {
    if (confirm('🚪 Logout Confirmation\n\nAll unsaved data will be lost.\nContinue?')) {
      logout();
    }
  };

  function logout() {
    currentUserRole = null;
    currentRegisterEvent = null;
    loginForm.style.display = 'none';
    loginForm.reset();
    loginSection.style.display = 'block';
    dashboardSection.style.display = 'none';
    organizerSection.style.display = 'none';
    registrationSection.style.display = 'none';
    helpCenterSection.style.display = 'none';
    fixedLogoutBtn.style.display = 'none';
    userRoleDisp.textContent = '';
  }

  // Enhanced Chatbot
  const chatbotIcon = document.querySelector('.chatbot-icon');
  let chatbox = null;

  chatbotIcon.onclick = () => {
    if (chatbox) return;

    chatbox = document.createElement('div');
    chatbox.className = 'chatbox';
    chatbox.innerHTML = `
      <div style="font-size:1.2em; font-weight:700; color:#143058; margin-bottom:12px;">🤖 DU SOL Smart Assistant</div>
      <div style="font-size:0.95em; color:#6c757d; margin-bottom:20px; line-height:1.5;">
        Hi! I'm here to help with:<br>
        • Login issues • Event registration<br>
        • Creating events • Campus navigation<br>
        • Technical support
      </div>
      <input type="text" id="chat-input" placeholder="Ask me anything... (e.g., 'how to register')" />
      <button id="send-btn">Send 🚀</button>
    `;
    document.body.appendChild(chatbox);
    chatbotIcon.style.display = 'none';

    const sendBtn = document.getElementById('send-btn');
    const input = document.getElementById('chat-input');
    
    sendBtn.onclick = input.onkeypress = (e) => {
      if (e.type === 'keypress' && e.key !== 'Enter') return;
      const val = input.value.toLowerCase().trim();
      input.value = '';
      
      const responses = {
        'login': '🔐 Click Organizer/Student → Enter SOLXXXXXXXX → Password → Login',
        'register': '📝 Student login → Click REGISTER → Upload ID → Fill form → Submit',
        'create': '👥 Organizer login → Fill event form → Add image → Create Event',
        'password': '🔒 Use your college ID password. Forgot? Contact admin@events.sol.du.ac.in',
        'map': '🗺️ Click "View Campus Map" on any event for Google Maps directions',
        'delete': '🗑️ Organizers: Click DELETE button on event card in dashboard',
        'help': '🆘 Click location icon (📍) or help icon (🆘) in dashboard for Help Center'
      };
      
      const response = Object.keys(responses).find(key => val.includes(key)) || 'ℹ️ For detailed help, use Help Center (📍 icon) or contact support!';
      setTimeout(() => alert(response), 200);
    };

    // Auto-close
    setTimeout(() => {
      chatbox.onclick = e => e.stopPropagation();
      document.body.onclick = () => {
        if (chatbox) {
          chatbox.remove();
          chatbox = null;
          chatbotIcon.style.display = 'flex';
        }
        document.body.onclick = null;
      };
    }, 100);
  };

  // Initialize
  fixedLogoutBtn.style.display = 'none';
</script>
</body>
</html>
