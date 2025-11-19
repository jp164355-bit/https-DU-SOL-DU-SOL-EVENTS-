
<html lang="en">
<head>
<meta name="viewport" content="width=device-width, initial-scale=1" />
<title>DU SOL Event Management Portal</title>
<style>
  body { margin:0; font-family: 'Segoe UI', Arial, sans-serif; background:#f6f8fa;}
  header { background:#143058; padding:20px; color:#fff; text-align:center;}
  .logo { width:84px; border-radius:50%; box-shadow:0 4px 16px #2d78d133; margin-bottom:12px; }
  h1 { margin:0 0 10px 0; font-size:2.2em; }
  .hero-img { width:96vw; max-width:440px; border-radius:12px; box-shadow:0 0 20px #2d78d11a; margin-top:16px; }
  nav { margin:18px 0; text-align:center; }
  .login-btn { background:#2d78d1; color:#fff; font-size:1.15em; padding:11px 28px; border-radius:9px; text-decoration:none; transition:background .3s; cursor:pointer; border:none; }
  .login-btn:hover { background:#fdc801; color:#143058; }
  .login-choice { display:flex; gap:20px; justify-content:center; margin-bottom:20px; }
  .role-btn { width:74px; height:74px; background:#2d78d1; color:#fff; font-size:1.08em; border-radius:50%; border:none; cursor:pointer; transition:background .3s,transform .2s; }
  .role-btn:hover { background:#fdc801; color:#143058; transform:scale(1.09); }
  label { display:block; margin:15px 0 5px; text-align:left; }
  input[type=text], input[type=email], input[type=password], input[type=tel], select { width:95%; padding:7px; margin-bottom:12px; border-radius:6px; border:1px solid #b7c6db; box-sizing: border-box; }
  input[type=file] { margin-bottom:12px; }
  .submit-btn { background:#2d78d1; color:#fff; padding:11px 0; width:100%; border:none; font-size:1.08em; border-radius:8px; margin-top:9px; cursor:pointer; }
  .submit-btn:hover { background:#fdc801; color:#143058; }
  #dashboard-section, #organizer-section, #registration-section { display:none; background:#fff; border-radius:18px; box-shadow:0 2px 22px #14305817; max-width:700px; margin:42px auto 18px; padding:26px 20px; }
  .dash-header { display:flex; gap:18px; align-items:center; margin-bottom:12px; position: relative;}
  .icon { width:47px; height:47px; background:#fdc801; color:#143058; border-radius:50%; display:flex; align-items:center; justify-content:center; font-size:1.7em; box-shadow:0 2px 14px #2d78d133; cursor:pointer; }
  .role-show { margin-left:auto; font-size:1.09em; color:#2d78d1; user-select:none; }
  
  .location-list, .event-list, #eventsContainer { margin-top:20px; }
  .event-card { background:#f6f8fa; border-radius:14px; box-shadow:0 1px 10px #2d78d11a; margin-bottom:22px; display:flex; align-items:center; gap:22px; padding:17px; }
  .event-icon { width:60px; height:60px; object-fit:cover; border-radius:10px; }
  .event-info { flex:1; }
  .event-title { font-size:1.12em; margin:0 0 6px 0; }
  .event-desc { font-size:0.97em; }
  .map-link { color:#2d78d1; font-weight:bold; text-decoration:none; }
  .map-link:hover { text-decoration:underline; }
  .register-btn { background:#2d78d1; color:#fff; border:none; padding:8px 12px; border-radius:6px; cursor:pointer; transition: background .3s; }
  .register-btn:hover { background:#fdc801; color:#143058; }
  #organizer-section h2 { margin-bottom: 18px; }
  
  #organizer-section h3 { margin:15px 0; font-weight:700; }
  form#eventForm { display:flex; flex-direction:column; gap:14px; }
  form#eventForm input[type=text], form#eventForm input[type=date], form#eventForm textarea, form#eventForm input[type=file] {
    border-radius:8px; border:1px solid #bbb; padding:10px; font-size:1em; width:100%; box-sizing: border-box;
  }
  form#eventForm textarea { resize:none; }
  form#eventForm button { background:#2d78d1; color:#fff; border:none; padding:14px; border-radius:8px; cursor:pointer; font-size:1.1em; transition:background .3s; }
  form#eventForm button:hover { background:#fdc801; color:#143058; }
  
  #registration-section h2 { margin-bottom:18px; }
  form#registrationForm { display:flex; flex-direction:column; gap:14px; max-width:480px; margin:0 auto; }
  form#registrationForm label { font-weight:600; }
  form#registrationForm button { background:#2d78d1; color:#fff; border:none; padding:14px; border-radius:8px; cursor:pointer; font-size:1.1em; transition:background .3s; margin-top:10px;}
  form#registrationForm button:hover { background:#fdc801; color:#143058;}
  .logout-fixed-btn {
    position: fixed;
    up: 20px;
    bottom: 20px;
    background: #fdc801;
    color: #143058;
    padding: 12px 18px;
    border: none;
    border-radius: 25px;
    font-weight: 700;
    font-size: 1em;
    cursor: pointer;
    box-shadow: 0 0 12px #2d78d1aa;
    z-index: 10000;
    transition: background .3s;
  }
  .logout-fixed-btn:hover { background: #2d78d1; color:#fff; }
  @media (max-width:650px) {
    #dashboard-section, #organizer-section, #registration-section { padding:16px 10px; }
    .event-card { flex-direction: column; gap:14px; }
  }
  
  .chatbot-icon {
    position: fixed; right: 18px; bottom: 22px; font-size: 2em; background: #2d78d1;
    color: #fff; border-radius: 50%; width: 48px; height: 48px;
    display: flex; align-items: center; justify-content: center;
    box-shadow: 0 2px 12px #14305825; cursor: pointer;
    animation: bounceChat 2s infinite alternate;
    z-index: 9999;
  }
  @keyframes bounceChat { 0% {transform: translateY(0);} 100% {transform: translateY(-9px);} }
  .chatbox {
    position: fixed; right: 18px; bottom: 80px; background: #fff;
    border-radius: 17px; box-shadow: 0 2px 18px #2d78d133;
    padding: 16px; width: 260px; z-index: 10000;
  }
  .chatbox input {
    width: 160px; padding: 6px; margin-right: 8px; border-radius: 6px; border:1px solid #ccc; outline:none;
  }
  .chatbox button {
    padding: 6px 12px; background:#2d78d1; color:#fff; border:none; border-radius: 6px; cursor: pointer;
  }
  .chatbox button:hover { background:#fdc801; color:#143058; }
</style>
</head>
<body>

<header>
  <img src="assets/images/du-sol-logo.png" alt="DU SOL Logo" class="logo" />
  <h1>Delhi University School of Open Learning Event Portal</h1>
  <img src="assets/images/du-campus.jpg" alt="Delhi University Campus" class="hero-img" />
</header>

<nav>
  <button class="login-btn" onclick="document.getElementById('login-section').scrollIntoView()">Login / Register</button>
</nav>

<!-- LOGIN PAGE -->
<section id="login-section">
  <div class="login-choice">
    <button class="role-btn" onclick="startLogin('Organizer')">Organizer</button>
    <button class="role-btn" onclick="startLogin('Student')">Student</button>
  </div>
  <form id="loginForm" style="display:none;" autocomplete="off">
    <label>Role: <input type="text" id="roleField" readonly /></label>
    <label>College ID: <input type="text" id="collegeIdField" required pattern="SOL[0-9]{8}" placeholder="SOL20251234" /></label>
    <label>BAR-CODE: <input type="password" required /></label>
    <button class="submit-btn" type="submit">Login</button>
  </form>
</section>

<!-- STUDENT DASHBOARD PAGE -->
<section id="dashboard-section">
  <div class="dash-header">
    <div class="icon" title="Location">📍</div>
    <div class="icon" title="Help Chatbot">💬</div>
    <span class="role-show" id="userRoleDisp"></span>
  </div>
  <h2>Upcoming Events</h2>
  <div class="location-list" id="event-list">
    <!-- Event cards will be dynamically rendered here -->
  </div>
</section>

<!-- STUDENT EVENT REGISTRATION FORM -->
<section id="registration-section">
  <h2>Event Registration</h2>
  <form id="registrationForm" enctype="multipart/form-data">
    <label for="idCard">Upload ID Card Photo *</label>
    <input type="file" id="idCard" accept="image/*" required />
    <label for="studentName">Name *</label>
    <input type="text" id="studentName" required />
    <label for="rollNumber">Roll Number *</label>
    <input type="text" id="rollNumber" required />
    <label for="phoneNumber">Phone Number *</label>
    <input type="tel" id="phoneNumber" required />
    <label for="emailAddress">Email *</label>
    <input type="email" id="emailAddress" required />
    <label for="studentYear">Student Year *</label>
    <select id="studentYear" required>
      <option value="" disabled selected>Select year</option>
      <option value="1st Year">1st Year</option>
      <option value="2nd Year">2nd Year</option>
      <option value="3rd Year">3rd Year</option>
      <option value="4th Year">4th Year</option>
    </select>
    <button type="submit">Submit Registration</button>
  </form>
</section>

<!-- EVENT ORGANIZER DASHBOARD -->
<section id="organizer-section">
  <h2>Organizer Dashboard - Add and Manage Events</h2>
  <form id="eventForm">
    <label>Event Name</label>
    <input type="text" id="eventName" required />
        <label for="emailAddress">Email *</label>
    <input type="email" id="emailAddress" required />

    <label>Date</label>
    <input type="date" id="eventDate" required />

    <label>Location</label>
    <input type="text" id="eventLocation" placeholder="e.g. North Campus" required />

    <label>Description</label>
    <textarea id="eventDesc" rows="4" placeholder="Event details..." required></textarea>

    <label>Event Image</label>
    <input type="file" id="eventImage" accept="image/*" />

    <button type="submit">Add Event</button>
  </form>
  <h3>Existing Events</h3>
  <div id="eventsContainer"></div>
</section>

<button class="logout-fixed-btn" id="fixedLogout">Logout</button>

<footer>
  &copy; 2025 - Delhi University School of Open Learning | Event Management Portal
</footer>

<!-- Chatbot Icon + Box -->
<div class="chatbot-icon" title="Help Chatbot">💬</div>

<script>
  const loginSection = document.getElementById('login-section');
  const dashboardSection = document.getElementById('dashboard-section');
  const organizerSection = document.getElementById('organizer-section');
  const registrationSection = document.getElementById('registration-section');
  const loginForm = document.getElementById('loginForm');
  const userRoleDisp = document.getElementById('userRoleDisp');
  const fixedLogoutBtn = document.getElementById('fixedLogout');
  const eventsContainer = document.getElementById('eventsContainer');
  const eventList = document.getElementById('event-list');
  const registrationForm = document.getElementById('registrationForm');

  let globalEvents = [
        {name: 'Annual Fest - North Campus', date: '2025-11-20', location: 'North Campus, Delhi University', desc: 'Music, dance, food and competitions at iconic DU North Campus.', imgData: 'assets/images/north-campus.jpg', mapLink: 'https://www.google.com/maps?q=28.693165,77.213016'},
        {name: 'Workshop - SOL Center', date: '2025-11-30', location: 'School of Open Learning, University of Delhi', desc: 'Career guidance and networking at DU SOL.', imgData: 'assets/images/sol-campus.jpg', mapLink: 'https://www.google.com/maps?q=28.682366,77.206839'}
  ];

  let currentUserRole = null;
  let currentRegisterEvent = null;
  let registrations = [];  // Store student registrations here

  function startLogin(role) {
    document.getElementById('roleField').value = role;
    loginForm.style.display = 'block';
  }

  loginForm.addEventListener('submit', function (e) {
    e.preventDefault();
    const role = document.getElementById('roleField').value;
    const collegeId = document.getElementById('collegeIdField').value.trim();
    if (!/^SOL[0-9]{8}$/.test(collegeId)) {
      alert('Enter valid College ID! Format: SOLXXXXXXXX');
      return;
    }
    currentUserRole = role;
    loginSection.style.display = 'none';
    fixedLogoutBtn.style.display = 'block';
    userRoleDisp.textContent = 'Logged in: ' + role;

    if (role === 'Student') {
      showStudentDashboard();
    } else {
      showOrganizerDashboard();
    }
  });

  function showStudentDashboard() {
    registrationSection.style.display = 'none';
    organizerSection.style.display = 'none';
    renderStudentEvents();
    dashboardSection.style.display = 'block';
  }

  function renderStudentEvents() {
    eventList.innerHTML = '';
    if (globalEvents.length === 0) {
      eventList.innerHTML = '<p>No upcoming events at the moment.</p>';
      return;
    }
    globalEvents.forEach((ev, idx) => {
      const div = document.createElement('div');
      div.className = 'event-card';
      div.innerHTML = `
        <img src="${ev.imgData || 'assets/images/sol-campus.jpg'}" alt="${ev.name}" class="event-icon" />
        <div class="event-info">
          <div class="event-title">${ev.name}</div>
          <div class="event-desc">${ev.desc}</div>
          <div><b>Date:</b> ${ev.date}</div>
          <div><b>Location:</b> ${ev.location}</div>
          <div><a href="${ev.mapLink}" target="_blank" class="map-link">View Campus Map</a></div>
          <button class="register-btn" onclick="openRegistrationForm(${idx})">Register</button>
        </div>
      `;
      eventList.appendChild(div);
    });
  }

  function openRegistrationForm(eventIndex) {
    currentRegisterEvent = eventIndex;
    dashboardSection.style.display = 'none';
    organizerSection.style.display = 'none';
    registrationSection.style.display = 'block';
    registrationForm.reset();
  }

  registrationForm.addEventListener('submit', function (e) {
    e.preventDefault();
    const idCardFile = document.getElementById('idCard').files[0];
    const name = document.getElementById('studentName').value.trim();
    const roll = document.getElementById('rollNumber').value.trim();
    const phone = document.getElementById('phoneNumber').value.trim();
    const email = document.getElementById('emailAddress').value.trim();
    const year = document.getElementById('studentYear').value;

    if (!idCardFile) {
      alert('Please upload your ID card photo.');
      return;
    }

    const reader = new FileReader();
    reader.onload = function (event) {
      registrations.push({
        event: globalEvents[currentRegisterEvent].name,
        idCard: event.target.result,
        name, roll, phone, email, year,
      });
      alert(`Registration successful for event: ${globalEvents[currentRegisterEvent].name}`);
      showStudentDashboard();
    };
    reader.readAsDataURL(idCardFile);
  });

  function showOrganizerDashboard() {
    dashboardSection.style.display = 'none';
    registrationSection.style.display = 'none';
    organizerSection.style.display = 'block';
    renderOrganizerEvents();
  }

  function renderOrganizerEvents() {
    if (globalEvents.length === 0) {
      eventsContainer.innerHTML = '<p>No events created yet.</p>';
      return;
    }
    eventsContainer.innerHTML = '';
    globalEvents.forEach((ev, idx) => {
      const div = document.createElement('div');
      div.className = 'event-card';
      div.innerHTML = `
        <img src="${ev.imgData || 'assets/images/sol-campus.jpg'}" alt="${ev.name}" class="event-icon" />
        <div class="event-info">
          <div class="event-title">${ev.name}</div>
          <div class="event-desc">${ev.desc}</div>
          <div><b>Date:</b> ${ev.date} | <b>Location:</b> ${ev.location}</div>
          <button onclick="deleteEvent(${idx})" style="margin-top:8px; background:#fd5050; color:#fff; border:none; border-radius:5px; cursor:pointer;">Delete</button>
        </div>
      `;
      eventsContainer.appendChild(div);
    });
  }

  function deleteEvent(index) {
    if (confirm('Are you sure you want to delete this event?')) {
      globalEvents.splice(index, 1);
      renderOrganizerEvents();
      renderStudentEvents();
    }
  }

  document.getElementById('eventForm').addEventListener('submit', function (e) {
    e.preventDefault();
    const name = document.getElementById('eventName').value.trim();
    const date = document.getElementById('eventDate').value;
    const location = document.getElementById('eventLocation').value.trim();
    const desc = document.getElementById('eventDesc').value.trim();
    const fileInput = document.getElementById('eventImage');
    const file = fileInput.files[0];

    if (file) {
      const reader = new FileReader();
      reader.onload = function (event) {
        globalEvents.push({ name, date, location, desc, imgData: event.target.result, mapLink: `https://www.google.com/maps?q=${encodeURIComponent(location)}` });
        renderOrganizerEvents();
        renderStudentEvents();
      };
      reader.readAsDataURL(file);
    } else {
      globalEvents.push({ name, date, location, desc, imgData: null, mapLink: `https://www.google.com/maps?q=${encodeURIComponent(location)}` });
      renderOrganizerEvents();
      renderStudentEvents();
    }
    this.reset();
  });

  fixedLogoutBtn.style.display = 'none';
  fixedLogoutBtn.onclick = () => {
    if (confirm('Logout?')) {
      logout();
    }
  };

  function logout() {
    currentUserRole = null;
    currentRegisterEvent = null;
    registrations = [];
    userRoleDisp.textContent = '';
    loginForm.style.display = 'none';
    loginForm.reset();
    loginSection.style.display = 'block';
    dashboardSection.style.display = 'none';
    organizerSection.style.display = 'none';
    registrationSection.style.display = 'none';
    fixedLogoutBtn.style.display = 'none';
  }

  // Chatbot functionality
  const chatbotIcon = document.querySelector('.chatbot-icon');
  let chatbox = null;

  chatbotIcon.onclick = () => {
    if (chatbox) return;

    chatbox = document.createElement('div');
    chatbox.className = 'chatbox';
    chatbox.innerHTML = `
      <div><b>DU SOL HelpBot</b></div>
      <div style="font-size:.9em; margin:8px 0;">
        Login as Organizer or Student using your College ID (Format: SOLXXXXXXXX).<br>
        Organizers can create/manage events.<br>
        Students can view, register, and join events.<br><br>
        Type your question below:
      </div>
      <input type="text" id="chat-input" placeholder="Ask me anything..." />
      <button id="send-btn">Send</button>
    `;
    document.body.appendChild(chatbox);
    chatbotIcon.style.display = 'none';

    document.getElementById('send-btn').onclick = () => {
      const input = document.getElementById('chat-input');
      const val = input.value.toLowerCase();
      if (val.includes('how to login')) alert('Click on Organizer or Student, enter your College ID and password, then press Login.');
      else if (val.includes('how to create event')) alert('Login as Organizer and fill the form on the Organizer Dashboard to add events.');
      else if (val.includes('how to register')) alert('Login as Student and click Register on the event card to register with your details.');
      else alert('Please login first. For more help, contact your college admin.');
      input.value = '';
    };

    setTimeout(() => {
      chatbox.onclick = e => e.stopPropagation();
      document.body.onclick = () => {
        chatbox.remove();
        chatbox = null;
        chatbotIcon.style.display = 'flex';
        document.body.onclick = null;
      };
    }, 20000);
  };
</script>
</body>
</html>

