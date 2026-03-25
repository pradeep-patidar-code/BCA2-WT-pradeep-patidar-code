# Day 41 — User Authentication & Complete Web Application

🔬 **Type:** Theory + Practical
🕐 **Duration:** 2 Hours
📚 **Unit:** 7 — Web Forms & Database
🧪 **Lab Experiment:** 24

---

## Learning Objectives

By the end of this session, students will be able to:
- Understand user authentication concepts (login, registration, sessions)
- Implement a login/registration system using client-side techniques
- Understand the importance of security in web forms
- Build a complete web app with login, dashboard, and CRUD features

---

## 1. Authentication Concepts

> **Analogy:** Authentication is like showing your **University ID card** at the gate. Registration creates your ID (signup), login shows your ID (authentication), and the gate remembers you for the rest of the day (session).

### Authentication Flow

```
1. User fills login form (email + password)
2. Client sends credentials to server
3. Server checks against database
4. If valid → Create session → Redirect to dashboard
5. If invalid → Show error message
6. On logout → Destroy session
```

### Key Terms

| Term | Meaning |
|------|---------|
| Authentication | Verifying identity (who are you?) |
| Authorization | Checking permissions (what can you do?) |
| Session | Server remembers logged-in user |
| Cookie | Small data stored in browser |
| Token (JWT) | Encrypted identity proof for APIs |
| Hashing | One-way encryption for passwords |

---

## 2. Security Best Practices

### Never Do These

| Bad Practice | Why It's Bad |
|-------------|-------------|
| Store passwords in plain text | Anyone with DB access sees passwords |
| Send passwords via GET | Visible in URL and browser history |
| Trust client-side only | JavaScript can be disabled/modified |
| Show "incorrect password" | Tells attacker the username exists |

### Always Do These

| Good Practice | Reason |
|--------------|--------|
| Hash passwords (bcrypt) | Even DB breach doesn't expose passwords |
| Use HTTPS | Encrypts data in transit |
| Validate server-side | Client can be bypassed |
| Show generic errors | "Invalid credentials" — don't reveal which field is wrong |
| Use CSRF tokens | Prevents cross-site request forgery |

### Password Hashing (Concept)

```
User enters: "MyPassword123"
          ↓
Hash function (bcrypt/argon2)
          ↓
Stored: "$2b$10$r4jF8kQ..." (irreversible)

Login check: hash("MyPassword123") === stored_hash? → Allow
             hash("WrongPassword") !== stored_hash? → Deny
```

---

## 3. Sessions & Cookies

### How Sessions Work

```
1. User logs in successfully
2. Server creates session: { id: "abc123", user: "rahul@example.com" }
3. Server sends cookie: session_id=abc123
4. Browser stores cookie
5. Every request includes cookie automatically
6. Server reads cookie → finds session → knows who the user is
7. On logout → Server deletes session → Cookie expires
```

### In client-side demonstration (using localStorage):

```javascript
// "Login" - store session
localStorage.setItem('loggedInUser', JSON.stringify({
    email: 'rahul@example.com',
    name: 'Rahul Kumar',
    loginTime: new Date().toISOString()
}));

// Check if logged in
const user = JSON.parse(localStorage.getItem('loggedInUser'));
if (user) {
    // Show dashboard
} else {
    // Show login page
}

// "Logout"
localStorage.removeItem('loggedInUser');
```

---

## Practical Session

### 🧪 Lab Experiment 24: Complete Login & Dashboard System

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Student Portal — Login System</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/css/bootstrap.min.css" rel="stylesheet">
    <style>
        .page { display: none; }
        .page.active { display: block; }
        .login-container { max-width: 450px; margin: 0 auto; }
    </style>
</head>
<body class="bg-light">

    <!-- ==================== LOGIN PAGE ==================== -->
    <div class="page active" id="loginPage">
        <div class="container py-5">
            <div class="login-container">
                <div class="text-center mb-4">
                    <h2>🎓 Mandsaur University</h2>
                    <p class="text-muted">Student Portal — Login</p>
                </div>
                <div class="card shadow">
                    <div class="card-body p-4">
                        <ul class="nav nav-tabs mb-3" id="authTabs">
                            <li class="nav-item">
                                <button class="nav-link active" data-bs-toggle="tab" data-bs-target="#loginTab">Login</button>
                            </li>
                            <li class="nav-item">
                                <button class="nav-link" data-bs-toggle="tab" data-bs-target="#registerTab">Register</button>
                            </li>
                        </ul>
                        <div class="tab-content">
                            
                            <!-- Login Tab -->
                            <div class="tab-pane fade show active" id="loginTab">
                                <form id="loginForm">
                                    <div class="form-floating mb-3">
                                        <input type="email" class="form-control" id="loginEmail" placeholder="Email" required>
                                        <label for="loginEmail">Email</label>
                                    </div>
                                    <div class="form-floating mb-3">
                                        <input type="password" class="form-control" id="loginPwd" placeholder="Password" required>
                                        <label for="loginPwd">Password</label>
                                    </div>
                                    <div class="form-check mb-3">
                                        <input class="form-check-input" type="checkbox" id="remember">
                                        <label class="form-check-label" for="remember">Remember me</label>
                                    </div>
                                    <div class="alert alert-danger d-none" id="loginError"></div>
                                    <button type="submit" class="btn btn-primary w-100 btn-lg">Login</button>
                                </form>
                            </div>

                            <!-- Register Tab -->
                            <div class="tab-pane fade" id="registerTab">
                                <form id="registerForm">
                                    <div class="form-floating mb-3">
                                        <input type="text" class="form-control" id="regName" placeholder="Name" required>
                                        <label for="regName">Full Name</label>
                                    </div>
                                    <div class="form-floating mb-3">
                                        <input type="text" class="form-control" id="regRoll" placeholder="Roll" required>
                                        <label for="regRoll">Roll Number</label>
                                    </div>
                                    <div class="form-floating mb-3">
                                        <input type="email" class="form-control" id="regEmail" placeholder="Email" required>
                                        <label for="regEmail">Email</label>
                                    </div>
                                    <div class="form-floating mb-3">
                                        <input type="password" class="form-control" id="regPwd" placeholder="Password" 
                                               required minlength="6">
                                        <label for="regPwd">Password (min 6 chars)</label>
                                    </div>
                                    <div class="form-floating mb-3">
                                        <select class="form-select" id="regCourse" required>
                                            <option value="" disabled selected></option>
                                            <option>BCA</option>
                                            <option>BBA</option>
                                            <option>B.Tech</option>
                                        </select>
                                        <label for="regCourse">Course</label>
                                    </div>
                                    <div class="alert alert-danger d-none" id="regError"></div>
                                    <div class="alert alert-success d-none" id="regSuccess"></div>
                                    <button type="submit" class="btn btn-success w-100 btn-lg">Register</button>
                                </form>
                            </div>
                        </div>
                    </div>
                </div>
                <p class="text-center text-muted mt-3">
                    <small>Demo: Register a new account, then login</small>
                </p>
            </div>
        </div>
    </div>

    <!-- ==================== DASHBOARD PAGE ==================== -->
    <div class="page" id="dashboardPage">
        
        <!-- Dashboard Navbar -->
        <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
            <div class="container">
                <a class="navbar-brand" href="#">🎓 Student Portal</a>
                <div class="d-flex align-items-center">
                    <span class="text-white me-3">Welcome, <strong id="userName"></strong></span>
                    <button class="btn btn-outline-light btn-sm" id="logoutBtn">Logout</button>
                </div>
            </div>
        </nav>

        <div class="container my-4">
            
            <!-- Welcome Card -->
            <div class="card bg-primary text-white mb-4 shadow">
                <div class="card-body py-4">
                    <div class="row align-items-center">
                        <div class="col-md-8">
                            <h3>Welcome to Student Portal</h3>
                            <p class="mb-0">Manage your profile, view course details, and track progress.</p>
                        </div>
                        <div class="col-md-4 text-md-end">
                            <p class="mb-0">🔑 Logged in: <span id="loginTime"></span></p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Stats Row -->
            <div class="row g-4 mb-4">
                <div class="col-md-3">
                    <div class="card shadow-sm text-center">
                        <div class="card-body">
                            <div class="display-6 text-primary">📚</div>
                            <h4 id="dashCourse">BCA</h4>
                            <p class="text-muted mb-0">Course</p>
                        </div>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="card shadow-sm text-center">
                        <div class="card-body">
                            <div class="display-6 text-success">📋</div>
                            <h4>Semester II</h4>
                            <p class="text-muted mb-0">Current Semester</p>
                        </div>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="card shadow-sm text-center">
                        <div class="card-body">
                            <div class="display-6 text-warning">📝</div>
                            <h4>5</h4>
                            <p class="text-muted mb-0">Subjects</p>
                        </div>
                    </div>
                </div>
                <div class="col-md-3">
                    <div class="card shadow-sm text-center">
                        <div class="card-body">
                            <div class="display-6 text-info">🧪</div>
                            <h4>30</h4>
                            <p class="text-muted mb-0">Lab Experiments</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Profile Card -->
            <div class="row g-4">
                <div class="col-md-6">
                    <div class="card shadow">
                        <div class="card-header bg-dark text-white">
                            <h5 class="mb-0">Your Profile</h5>
                        </div>
                        <div class="card-body">
                            <table class="table table-borderless mb-0">
                                <tr><td class="fw-bold" style="width:40%">Name</td><td id="profileName"></td></tr>
                                <tr><td class="fw-bold">Roll No</td><td id="profileRoll"></td></tr>
                                <tr><td class="fw-bold">Email</td><td id="profileEmail"></td></tr>
                                <tr><td class="fw-bold">Course</td><td id="profileCourse"></td></tr>
                                <tr><td class="fw-bold">Registered</td><td id="profileDate"></td></tr>
                            </table>
                        </div>
                    </div>
                </div>
                <div class="col-md-6">
                    <div class="card shadow">
                        <div class="card-header bg-dark text-white">
                            <h5 class="mb-0">Course Progress</h5>
                        </div>
                        <div class="card-body">
                            <div class="mb-3">
                                <div class="d-flex justify-content-between">
                                    <span>Internet Technology</span><span class="text-success">100%</span>
                                </div>
                                <div class="progress" style="height: 8px;">
                                    <div class="progress-bar bg-success" style="width: 100%"></div>
                                </div>
                            </div>
                            <div class="mb-3">
                                <div class="d-flex justify-content-between">
                                    <span>HTML & HTML5</span><span class="text-success">100%</span>
                                </div>
                                <div class="progress" style="height: 8px;">
                                    <div class="progress-bar bg-success" style="width: 100%"></div>
                                </div>
                            </div>
                            <div class="mb-3">
                                <div class="d-flex justify-content-between">
                                    <span>CSS</span><span class="text-success">100%</span>
                                </div>
                                <div class="progress" style="height: 8px;">
                                    <div class="progress-bar bg-success" style="width: 100%"></div>
                                </div>
                            </div>
                            <div class="mb-3">
                                <div class="d-flex justify-content-between">
                                    <span>JavaScript</span><span class="text-success">100%</span>
                                </div>
                                <div class="progress" style="height: 8px;">
                                    <div class="progress-bar bg-success" style="width: 100%"></div>
                                </div>
                            </div>
                            <div class="mb-3">
                                <div class="d-flex justify-content-between">
                                    <span>Bootstrap</span><span class="text-primary">85%</span>
                                </div>
                                <div class="progress" style="height: 8px;">
                                    <div class="progress-bar bg-primary" style="width: 85%"></div>
                                </div>
                            </div>
                            <div class="mb-3">
                                <div class="d-flex justify-content-between">
                                    <span>Web Forms & Database</span><span class="text-warning">50%</span>
                                </div>
                                <div class="progress" style="height: 8px;">
                                    <div class="progress-bar bg-warning" style="width: 50%"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.2/dist/js/bootstrap.bundle.min.js"></script>
    <script>
    (function() {
        'use strict';

        // User storage (simulating database)
        function getUsers() {
            return JSON.parse(localStorage.getItem('portal_users') || '[]');
        }
        function saveUsers(users) {
            localStorage.setItem('portal_users', JSON.stringify(users));
        }
        function getSession() {
            return JSON.parse(localStorage.getItem('portal_session') || 'null');
        }
        function setSession(user) {
            localStorage.setItem('portal_session', JSON.stringify({
                email: user.email,
                name: user.name,
                roll: user.roll,
                course: user.course,
                loginTime: new Date().toISOString(),
                regDate: user.regDate
            }));
        }
        function clearSession() {
            localStorage.removeItem('portal_session');
        }

        // Page navigation
        function showPage(pageId) {
            document.querySelectorAll('.page').forEach(function(p) { p.classList.remove('active'); });
            document.getElementById(pageId).classList.add('active');
        }

        // Check if already logged in
        var session = getSession();
        if (session) {
            showDashboard(session);
        }

        // REGISTER
        document.getElementById('registerForm').addEventListener('submit', function(e) {
            e.preventDefault();
            var users = getUsers();
            var email = document.getElementById('regEmail').value.trim();
            var password = document.getElementById('regPwd').value;
            var name = document.getElementById('regName').value.trim();
            var roll = document.getElementById('regRoll').value.trim();
            var course = document.getElementById('regCourse').value;

            // Check if email already exists
            var exists = users.some(function(u) { return u.email === email; });
            if (exists) {
                showAlert('regError', 'An account with this email already exists');
                return;
            }

            // Store user (Note: In real app, password would be hashed server-side)
            users.push({
                email: email,
                password: password, // Client-side demo only — never store plain passwords in production
                name: name,
                roll: roll,
                course: course,
                regDate: new Date().toLocaleDateString()
            });
            saveUsers(users);

            hideAlert('regError');
            showAlert('regSuccess', 'Registration successful! You can now login.');
            this.reset();
        });

        // LOGIN
        document.getElementById('loginForm').addEventListener('submit', function(e) {
            e.preventDefault();
            var email = document.getElementById('loginEmail').value.trim();
            var password = document.getElementById('loginPwd').value;
            var users = getUsers();

            var user = users.find(function(u) { return u.email === email && u.password === password; });
            if (user) {
                setSession(user);
                hideAlert('loginError');
                showDashboard(getSession());
            } else {
                showAlert('loginError', 'Invalid email or password');
            }
        });

        // LOGOUT
        document.getElementById('logoutBtn').addEventListener('click', function() {
            clearSession();
            showPage('loginPage');
            document.getElementById('loginForm').reset();
            document.getElementById('registerForm').reset();
        });

        // Show dashboard
        function showDashboard(session) {
            document.getElementById('userName').textContent = session.name;
            document.getElementById('loginTime').textContent = new Date(session.loginTime).toLocaleString();
            document.getElementById('dashCourse').textContent = session.course;
            document.getElementById('profileName').textContent = session.name;
            document.getElementById('profileRoll').textContent = session.roll;
            document.getElementById('profileEmail').textContent = session.email;
            document.getElementById('profileCourse').textContent = session.course;
            document.getElementById('profileDate').textContent = session.regDate || 'N/A';
            showPage('dashboardPage');
        }

        // Alert helpers
        function showAlert(id, msg) {
            var el = document.getElementById(id);
            el.textContent = msg;
            el.classList.remove('d-none');
        }
        function hideAlert(id) {
            document.getElementById(id).classList.add('d-none');
        }
    })();
    </script>

</body>
</html>
```

---

## Summary

| Concept | Details |
|---------|---------|
| Authentication | Login = verify identity (email + password) |
| Registration | Create new user account |
| Sessions | Server remembers logged-in user |
| Security | Hash passwords, use HTTPS, validate server-side |
| localStorage | Client-side storage for demo (not production auth) |
| CRUD | Create (register), Read (dashboard), Update (profile), Delete (logout) |

---

## Unit 7 Complete!

You've covered all Web Forms & Database topics:
- **Day 38:** Form elements, attributes, GET vs POST, admission form
- **Day 39:** JavaScript validation, regex, real-time feedback, password strength
- **Day 40:** SQL basics (CRUD), database design, CRUD app with localStorage
- **Day 41:** Authentication, sessions, security, login/dashboard system

---

*Day 41 of 55 | Unit 7 — Web Forms & Database | Web Technology (25BCA060)*
