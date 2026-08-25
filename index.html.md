<!DOCTYPE html>  
<html lang="ko">  
<head>  
  <meta charset="UTF-8">  
  <meta name="viewport" content="width=device-width, initial-scale=1.0">  
  <title>**기전여자고등학교** **분실물** **센터**</title>  
  <style>  
    :root {  
      --primary-color: #4A90E2;  
      --bg-color: #F8F9FA;  
      --card-bg: #FFFFFF;  
      --text-color: #333333;  
      --border-color: #DDDDDD;  
      --header-bg: #FFFFFF;  
      --sub-text: #666666;  
    }  
  
    body.dark-mode {  
      --bg-color: #121212;  
      --card-bg: #1E1E1E;  
      --text-color: #E0E0E0;  
      --border-color: #333333;  
      --header-bg: #1A1A1A;  
      --sub-text: #AAAAAA;  
    }  
  
    * { box-sizing: border-box; margin: 0; padding: 0; font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; }  
    body { background-color: var(--bg-color); color: var(--text-color); transition: background-color 0.3s, color 0.3s; }  
  
    header { background-color: var(--header-bg); border-bottom: 1px solid var(--border-color); position: sticky; top: 0; z-index: 100; }  
    .nav-container { max-width: 1000px; margin: 0 auto; padding: 12px 20px; display: flex; justify-content: space-between; align-items: center; flex-wrap: wrap; gap: 10px; }  
    .logo-area h1 { font-size: 18px; color: var(--primary-color); }  
    .nav-menu { display: flex; gap: 15px; align-items: center; }  
    .nav-link { text-decoration: none; color: var(--text-color); font-size: 14px; font-weight: bold; cursor: pointer; }  
    .nav-link.active { color: var(--primary-color); }  
    .user-actions { display: flex; align-items: center; gap: 12px; }  
    .user-profile { display: flex; align-items: center; gap: 8px; font-size: 13px; }  
    .user-avatar { width: 30px; height: 30px; border-radius: 50%; object-fit: cover; }  
    .btn-auth, .btn-theme, .btn-clear-all { padding: 6px 12px; font-size: 13px; border-radius: 6px; border: 1px solid var(--border-color); background: var(--card-bg); color: var(--text-color); cursor: pointer; }  
      
    .btn-clear-all { background-color: #FFEEEB; color: #D32F2F; border-color: #FFCDD2; font-weight: bold; }  
    .btn-clear-all:hover { background-color: #FFCDD2; }  
  
    .btn-google {  
      display: flex;  
      align-items: center;  
      gap: 8px;  
      border: 1px solid #dadce0;  
      background-color: #ffffff;  
      color: #3c4043;  
      padding: 6px 12px;  
      border-radius: 4px;  
      font-size: 13px;  
      font-weight: 500;  
      cursor: pointer;  
    }  
    .btn-google:hover { background-color: #f8f9fa; }  
  
    .container { max-width: 900px; margin: 25px auto; padding: 0 20px; }  
    .page-section { display: none; }  
    .page-section.active { display: block; }  
  
    .card-box { background: var(--card-bg); padding: 20px; border-radius: 12px; box-shadow: 0 2px 6px rgba(0,0,0,0.05); border: 1px solid var(--border-color); margin-bottom: 20px; }  
    .form-group { margin-bottom: 15px; }  
    .form-group label { display: block; font-weight: bold; margin-bottom: 5px; font-size: 14px; }  
    .form-group input, .form-group textarea, .form-group select { width: 100%; padding: 10px; border: 1px solid var(--border-color); background: var(--card-bg); color: var(--text-color); border-radius: 6px; font-size: 14px; }  
    .form-hint { font-size: 12px; color: var(--sub-text); margin-top: 4px; }  
    .btn-submit { width: 100%; background-color: var(--primary-color); color: white; border: none; padding: 12px; border-radius: 6px; font-weight: bold; cursor: pointer; }  
    .btn-submit:disabled { background-color: #CCCCCC; cursor: not-allowed; }  
  
    .filter-container { display: flex; gap: 8px; margin-bottom: 20px; overflow-x: auto; }  
    .filter-btn { padding: 8px 16px; border: 1px solid var(--border-color); background: var(--card-bg); color: var(--text-color); border-radius: 20px; cursor: pointer; font-size: 13px; }  
    .filter-btn.active { background-color: var(--primary-color); color: white; border-color: var(--primary-color); }  
    .items-grid { display: grid; grid-template-columns: repeat(auto-fill, minmax(220px, 1fr)); gap: 20px; }  
    .item-card { background: var(--card-bg); border-radius: 10px; overflow: hidden; border: 1px solid var(--border-color); display: flex; flex-direction: column; }  
    .item-card.resolved-card { opacity: 0.7; }  
    .item-card img { width: 100%; height: 160px; object-fit: cover; background-color: #EEE; }  
    .item-info { padding: 12px; flex-grow: 1; display: flex; flex-direction: column; }  
    .badge-row { display: flex; justify-content: space-between; align-items: center; margin-bottom: 8px; }  
    .item-badge { padding: 3px 6px; font-size: 11px; border-radius: 4px; font-weight: bold; }  
    .badge-lost { background-color: #FFEBEE; color: #C62828; }  
    .badge-found { background-color: #E3F2FD; color: #1976D2; }  
    .badge-resolved { background-color: #E8F5E9; color: #2E7D32; }  
    .item-time { font-size: 11px; color: var(--sub-text); }  
    .item-author { font-size: 11px; color: var(--sub-text); margin-bottom: 4px; font-weight: 500; }  
    .item-title { font-size: 15px; font-weight: bold; margin-bottom: 6px; }  
    .item-meta { font-size: 12px; color: var(--sub-text); margin-bottom: 4px; }  
    .item-desc { font-size: 13px; margin-top: 6px; flex-grow: 1; margin-bottom: 10px; }  
  
    .author-controls {  
      margin-top: 10px;  
      padding-top: 10px;  
      border-top: 1px dashed var(--border-color);  
      display: flex;  
      flex-direction: column;  
      gap: 8px;  
    }  
    .status-change-box {  
      display: flex;  
      align-items: center;  
      justify-content: space-between;  
      gap: 6px;  
    }  
    .status-change-box label { font-size: 11px; color: var(--primary-color); font-weight: bold; white-space: nowrap; }  
    .status-select { font-size: 12px; padding: 4px 6px; border-radius: 4px; border: 1px solid var(--primary-color); background: var(--card-bg); color: var(--text-color); cursor: pointer; font-weight: bold; }  
    .btn-delete { background-color: #FFEBEE; color: #C62828; border: 1px solid #FFCDD2; padding: 6px 8px; border-radius: 4px; font-size: 12px; font-weight: bold; cursor: pointer; text-align: center; }  
    .btn-delete:hover { background-color: #FFCDD2; }  
  
    .auth-warning { color: #D32F2F; font-size: 13px; margin-bottom: 15px; display: none; }  
  </style>  
  
  <!-- Firebase SDK -->  
  <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-app-compat.js"></script>  
  <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-auth-compat.js"></script>  
  <script src="https://www.gstatic.com/firebasejs/9.22.0/firebase-firestore-compat.js"></script>  
</head>  
<body>  
  
  <header>  
    <div class="nav-container">  
      <div class="logo-area">  
        <h1>🏫 **기전여자고등학교** **분실물** **센터**</h1>  
      </div>  
  
      <nav class="nav-menu">  
        <span class="nav-link active" onclick="switchTab('list')">**분실물** **목록**</span>  
        <span class="nav-link" onclick="switchTab('register')">**등록하기**</span>  
      </nav>  
  
      <div class="user-actions">  
        <button class="btn-clear-all" onclick="clearAllData()">🔥 **전체** **초기화**</button>  
        <button class="btn-theme" onclick="toggleDarkMode()">🌙 **다크모드**</button>  
  
        <button id="btnLogin" class="btn-google" onclick="loginWithGoogle()">  
          <svg width="18" height="18" viewBox="0 0 18 18"><path fill="#4285F4" d="M17.64 9.2c0-.637-.057-1.251-.164-1.84H9v3.481h4.844a4.14 4.14 0 0 1-1.796 2.716v2.259h2.908c1.702-1.567 2.684-3.875 2.684-6.616z"/><path fill="#34A853" d="M9 18c2.43 0 4.467-.806 5.956-2.18l-2.908-2.259c-.806.54-1.837.86-3.048.86-2.344 0-4.328-1.584-5.036-3.711H.957v2.332A8.997 8.997 0 0 0 9 18z"/><path fill="#FBBC05" d="M3.964 10.71A5.41 5.41 0 0 1 3.682 9c0-.593.102-1.17.282-1.71V4.958H.957A8.996 8.996 0 0 0 0 9c0 1.452.348 2.827.957 4.042l3.007-2.332z"/><path fill="#EA4335" d="M9 3.58c1.321 0 2.508.454 3.44 1.345l2.582-2.58C13.463.891 11.426 0 9 0A8.997 8.997 0 0 0 .957 4.958L3.964 7.29C4.672 5.163 6.656 3.58 9 3.58z"/></svg>  
          Google **계정** **로그인**  
        </button>  
  
        <div id="userInfo" class="user-profile" style="display: none;">  
          <img id="userAvatar" class="user-avatar" src="" alt="Profile">  
          <div>  
            <div id="userName" style="font-weight: bold;"></div>  
            <div id="userEmail" style="font-size: 10px; color: var(--sub-text);"></div>  
          </div>  
          <button class="btn-auth" onclick="logout()">**로그아웃**</button>  
        </div>  
      </div>  
    </div>  
  </header>  
  
  <div class="container">  
  
    <!-- **분실물** **목록** -->  
    <section id="section-list" class="page-section active">  
      <div class="filter-container">  
        <button class="filter-btn active" onclick="setFilter('**전체**')">**전체보기**</button>  
        <button class="filter-btn" onclick="setFilter('**찾는** **중**(**분실**)')">**찾는** **중**(**분실**)</button>  
        <button class="filter-btn" onclick="setFilter('**습득** **보관** **중**')">**습득** **보관** **중**</button>  
        <button class="filter-btn" onclick="setFilter('**해결됨**')">**해결됨**</button>  
      </div>  
      <main class="items-grid" id="itemsGrid"></main>  
    </section>  
  
    <!-- **등록하기** -->  
    <section id="section-register" class="page-section">  
      <div class="card-box">  
        <h2 style="margin-bottom: 15px; font-size: 18px;">**분실물** **등록**</h2>  
        <div id="authWarning" class="auth-warning">⚠️ **글을** **등록하려면** **먼저** Google **계정으로** **로그인해야** **합니다**.</div>  
        <form id="lostForm">  
          <div class="form-group">  
            <label for="authorIdentity">**작성자** **학번** / **선생님** **성함**</label>  
            <input type="text" id="authorIdentity" placeholder="**예**: 10101 **홍길동** / 20315 **김**OO / OOO**선생님**" required>  
            <div class="form-hint">1, 2, 3**학년** **모두** **학번**(5**자리**)**과** **이름을** **작성하거나** **교사인** **경우** 'OOO**선생님**' **형식으로** **작성해** **주세요**.</div>  
          </div>  
          <div class="form-group">  
            <label for="type">**구분**</label>  
            <select id="type" required>  
              <option value="**찾는** **중**(**분실**)">**잃어버렸어요** (**찾는** **중**)</option>  
              <option value="**습득** **보관** **중**">**주웠어요** (**습득** **보관** **중**)</option>  
            </select>  
          </div>  
          <div class="form-group">  
            <label for="title">**물품명**</label>  
            <input type="text" id="title" placeholder="**예**: **검은색** **에어팟** **케이스**" required>  
          </div>  
          <div class="form-group">  
            <label for="location">**장소** **및** **날짜**</label>  
            <input type="text" id="location" placeholder="**예**: **본관** 2**층** **교무실** **앞** / 5**월** 10**일**" required>  
          </div>  
          <div class="form-group">  
            <label for="image">**사진** **첨부**</label>  
            <input type="file" id="image" accept="image/*">  
          </div>  
          <div class="form-group">  
            <label for="description">**상세** **설명**</label>  
            <textarea id="description" rows="3" placeholder="**특징이나** **상세** **설명을** **적어주세요**."></textarea>  
          </div>  
          <button type="submit" class="btn-submit" id="submitBtn">**등록하기**</button>  
        </form>  
      </div>  
    </section>  
  
  </div>  
  
  <script>  
    // 🔑 **관리자** **비밀번호가** 'kijun student'**로** **변경되었습니다**.  
    const ADMIN_PASSWORD = "kijun student";  
  
    const firebaseConfig = {  
      apiKey: "YOUR_API_KEY",  
      authDomain: "YOUR_PROJECT.firebaseapp.com",  
      projectId: "YOUR_PROJECT_ID",  
      storageBucket: "YOUR_PROJECT.appspot.com",  
      messagingSenderId: "YOUR_SENDER_ID",  
      appId: "YOUR_APP_ID"  
    };  
  
    let db = null;  
    let auth = null;  
    let isFirebaseReady = false;  
    let currentUser = null;  
    let items = [];  
    let currentFilter = '**전체**';  
  
    const THIRTY_DAYS_MS = 30 * 24 * 60 * 60 * 1000;  
  
    try {  
      if (firebaseConfig.apiKey !== "YOUR_API_KEY") {  
        firebase.initializeApp(firebaseConfig);  
        db = firebase.firestore();  
        auth = firebase.auth();  
        isFirebaseReady = true;  
      }  
    } catch (e) {  
      console.warn("Firebase **미연동** **모드로** **동작합니다**.");  
    }  
  
    window.addEventListener('DOMContentLoaded', () => {  
      if (isFirebaseReady) {  
        auth.getRedirectResult().catch(error => {  
          alert("**구글** **로그인** **인증에** **실패했습니다**: " + error.message);  
        });  
  
        auth.onAuthStateChanged(user => {  
          if (user) {  
            currentUser = {  
              email: user.email,  
              name: user.displayName,  
              avatar: user.photoURL  
            };  
          } else {  
            currentUser = null;  
          }  
          updateUserUI();  
          loadItems();  
        });  
      } else {  
        loadItems();  
      }  
    });  
  
    function timeAgo(timestamp) {  
      if (!timestamp) return '**방금** **전**';  
      const now = new Date();  
      const past = new Date(timestamp);  
      const diffInSeconds = Math.floor((now - past) / 1000);  
  
      if (diffInSeconds < 60) return '**방금** **전**';  
      const diffInMinutes = Math.floor(diffInSeconds / 60);  
      if (diffInMinutes < 60) return `${diffInMinutes}**분** **전**`;  
      const diffInHours = Math.floor(diffInMinutes / 60);  
      if (diffInHours < 24) return `${diffInHours}**시간** **전**`;  
      const diffInDays = Math.floor(diffInHours / 24);  
      if (diffInDays < 30) return `${diffInDays}**일** **전**`;  
      return `${Math.floor(diffInDays / 30)}**달** **전**`;  
    }  
  
    function loginWithGoogle() {  
      if (isFirebaseReady) {  
        const provider = new firebase.auth.GoogleAuthProvider();  
        auth.signInWithRedirect(provider);  
      } else {  
        const inputEmail = prompt("**테스트용** Google **이메일을** **입력하세요** (**예**: user@gijeon.hs.kr):");  
        if (!inputEmail || !inputEmail.includes('@')) {  
          alert('**유효한** **이메일을** **입력해** **주세요**.');  
          return;  
        }  
        currentUser = {  
          email: inputEmail,  
          name: inputEmail.split('@')[0],  
          avatar: "https://lh3.googleusercontent.com/a/default-user=s96-c"  
        };  
        updateUserUI();  
        renderItems();  
      }  
    }  
  
    function logout() {  
      if (isFirebaseReady) auth.signOut();  
      currentUser = null;  
      updateUserUI();  
      renderItems();  
    }  
  
    function updateUserUI() {  
      const btnLogin = document.getElementById('btnLogin');  
      const userInfo = document.getElementById('userInfo');  
      const authWarning = document.getElementById('authWarning');  
      const submitBtn = document.getElementById('submitBtn');  
  
      if (currentUser) {  
        btnLogin.style.display = 'none';  
        userInfo.style.display = 'flex';  
        document.getElementById('userName').innerText = currentUser.name;  
        document.getElementById('userEmail').innerText = currentUser.email;  
        document.getElementById('userAvatar').src = currentUser.avatar;  
        if (authWarning) authWarning.style.display = 'none';  
        if (submitBtn) submitBtn.disabled = false;  
      } else {  
        btnLogin.style.display = 'flex';  
        userInfo.style.display = 'none';  
        if (authWarning) authWarning.style.display = 'block';  
        if (submitBtn) submitBtn.disabled = true;  
      }  
    }  
  
    function toggleDarkMode() {  
      document.body.classList.toggle('dark-mode');  
      const isDark = document.body.classList.contains('dark-mode');  
      document.querySelector('.btn-theme').innerText = isDark ? '☀️ **라이트모드**' : '🌙 **다크모드**';  
    }  
  
    function switchTab(tabName) {  
      document.querySelectorAll('.page-section').forEach(sec => sec.classList.remove('active'));  
      document.querySelectorAll('.nav-link').forEach(link => link.classList.remove('active'));  
  
      document.getElementById(`section-${tabName}`).classList.add('active');  
      event.target.classList.add('active');  
    }  
  
    function setFilter(status) {  
      currentFilter = status;  
      document.querySelectorAll('.filter-btn').forEach(btn => {  
        btn.classList.toggle('active', btn.innerText.includes(status) || (status === '**전체**' && btn.innerText === '**전체보기**'));  
      });  
      renderItems();  
    }  
  
    function loadItems() {  
      if (isFirebaseReady) {  
        db.collection('lost_items').orderBy('createdAt', 'desc').onSnapshot(snapshot => {  
          items = snapshot.docs.map(doc => ({ id: doc.id, ...doc.data() }));  
          cleanupExpiredItems();  
          renderItems();  
        });  
      } else {  
        items = JSON.parse(localStorage.getItem('gijeon_lost_items')) || [];  
        cleanupExpiredItems();  
        renderItems();  
      }  
    }  
  
    function cleanupExpiredItems() {  
      const now = Date.now();  
        
      items.forEach(item => {  
        if (item.status === '**해결됨**' && item.resolvedAt) {  
          if (now - item.resolvedAt > THIRTY_DAYS_MS) {  
            if (isFirebaseReady) {  
              db.collection('lost_items').doc(item.id).delete();  
            } else {  
              items = items.filter(i => i.id !== item.id);  
              localStorage.setItem('gijeon_lost_items', JSON.stringify(items));  
            }  
          }  
        }  
      });  
    }  
  
    function changeItemStatus(itemId, newStatus) {  
      const updateData = { status: newStatus };  
        
      if (newStatus === '**해결됨**') {  
        updateData.resolvedAt = Date.now();  
      } else {  
        updateData.resolvedAt = null;  
      }  
  
      if (isFirebaseReady) {  
        db.collection('lost_items').doc(itemId).update(updateData)  
          .then(() => alert('**게시물** **상태가** **변경되었습니다**.'))  
          .catch(err => alert('**상태** **변경** **실패**: ' + err.message));  
      } else {  
        const item = items.find(i => i.id == itemId);  
        if (item) {  
          item.status = newStatus;  
          item.resolvedAt = updateData.resolvedAt;  
          localStorage.setItem('gijeon_lost_items', JSON.stringify(items));  
          alert('**게시물** **상태가** **변경되었습니다**.');  
          renderItems();  
        }  
      }  
    }  
  
    function deleteItem(itemId) {  
      const inputPw = prompt("**게시글을** **삭제하려면** **관리자** **비밀번호를** **입력하세요**:");  
      if (inputPw === null) return;  
  
      if (inputPw !== ADMIN_PASSWORD) {  
        alert("**비밀번호가** **올바르지** **않습니다**.");  
        return;  
      }  
  
      if (isFirebaseReady) {  
        db.collection('lost_items').doc(itemId).delete()  
          .then(() => alert('**게시물이** **삭제되었습니다**.'))  
          .catch(err => alert('**삭제** **실패**: ' + err.message));  
      } else {  
        items = items.filter(i => String(i.id) !== String(itemId));  
        localStorage.setItem('gijeon_lost_items', JSON.stringify(items));  
        alert('**게시물이** **삭제되었습니다**.');  
        renderItems();  
      }  
    }  
  
    function clearAllData() {  
      const inputPw = prompt("**전체** **데이터를** **초기화하려면** **관리자** **비밀번호를** **입력하세요**:");  
      if (inputPw === null) return;  
  
      if (inputPw !== ADMIN_PASSWORD) {  
        alert("**비밀번호가** **올바르지** **않습니다**.");  
        return;  
      }  
  
      if (isFirebaseReady) {  
        db.collection('lost_items').get().then(snapshot => {  
          snapshot.docs.forEach(doc => doc.ref.delete());  
          alert('**모든** **데이터가** **삭제되었습니다**.');  
        });  
      } else {  
        localStorage.removeItem('gijeon_lost_items');  
        items = [];  
        alert('**모든** **데이터가** **삭제되었습니다**.');  
        renderItems();  
      }  
    }  
  
    function renderItems() {  
      const grid = document.getElementById('itemsGrid');  
      grid.innerHTML = '';  
  
      const filtered = items.filter(item => currentFilter === '**전체**' || item.status === currentFilter);  
  
      if (filtered.length === 0) {  
        grid.innerHTML = '<p style="grid-column: 1/-1; text-align: center; color: var(--sub-text);">**등록된** **물품이** **없습니다**.</p>';  
        return;  
      }  
  
      filtered.forEach(item => {  
        const card = document.createElement('div');  
        const isResolved = item.status === '**해결됨**';  
        card.className = `item-card ${isResolved ? 'resolved-card' : ''}`;  
  
        let badgeClass = 'badge-lost';  
        if (item.status === '**습득** **보관** **중**') badgeClass = 'badge-found';  
        if (item.status === '**해결됨**') badgeClass = 'badge-resolved';  
  
        const authorControlsHtml = `  
          <div class="author-controls">  
            <div class="status-change-box">  
              <label for="status-${item.id}">⚙️ **상태** **변경**:</label>  
              <select class="status-select" id="status-${item.id}" onchange="changeItemStatus('${item.id}', this.value)">  
                <option value="**찾는** **중**(**분실**)" ${item.status === '**찾는** **중**(**분실**)' ? 'selected' : ''}>**찾는** **중**(**분실**)</option>  
                <option value="**습득** **보관** **중**" ${item.status === '**습득** **보관** **중**' ? 'selected' : ''}>**습득** **보관** **중**</option>  
                <option value="**해결됨**" ${item.status === '**해결됨**' ? 'selected' : ''}>**해결됨** (30**일** **후** **자동삭제**)</option>  
              </select>  
            </div>  
            <button class="btn-delete" onclick="deleteItem('${item.id}')">🗑️ **게시글** **삭제**</button>  
          </div>  
        `;  
  
        const imageHtml = item.image   
          ? `<img src="${item.image}" alt="${item.title}" onerror="this.style.display='none'">`   
          : '';  
  
        card.innerHTML = `  
          ${imageHtml}  
          <div class="item-info">  
            <div class="badge-row">  
              <span class="item-badge ${badgeClass}">${item.status}</span>  
              <span class="item-time">${timeAgo(item.createdAt)}</span>  
            </div>  
            <div class="item-author">**작성자**: ${item.authorIdentity || '**익명**'}</div>  
            <div class="item-title">${item.title}</div>  
            <div class="item-meta">📍 **위치**: ${item.location}</div>  
            <p class="item-desc">${item.description || ''}</p>  
            ${authorControlsHtml}  
          </div>  
        `;  
        grid.appendChild(card);  
      });  
    }  
  
    function validateIdentity(input) {  
      const trimmed = input.trim();  
      const studentPattern = /^[1-3]\d{4}\s*.+/;   
      const teacherPattern = /.***선생님**$/;   
  
      return studentPattern.test(trimmed) || teacherPattern.test(trimmed);  
    }  
  
    document.getElementById('lostForm').addEventListener('submit', function(e) {  
      e.preventDefault();  
  
      if (!currentUser) {  
        alert('**게시글을** **작성하려면** **반드시** Google **로그인** **상태여야** **합니다**.');  
        return;  
      }  
  
      const identityInput = document.getElementById('authorIdentity').value;  
  
      if (!identityInput || !validateIdentity(identityInput)) {  
        alert('**작성자** **학번**/**선생님** **양식이** **올바르지** **않습니다**.\n\n- **학생**: 1, 2, 3**학년** 5**자리** **학번** **포함** (**예**: 10101 **홍길동**)\n- **교사**: OOO**선생님** (**예**: **김**OO**선생님**)');  
        return;  
      }  
  
      const fileInput = document.getElementById('image');  
      const file = fileInput.files[0];  
  
      const savePost = (imageDataUrl) => {  
        const newItem = {  
          status: document.getElementById('type').value,  
          title: document.getElementById('title').value,  
          location: document.getElementById('location').value,  
          description: document.getElementById('description').value,  
          authorIdentity: identityInput.trim(),  
          authorEmail: currentUser.email,  
          image: imageDataUrl || null,  
          createdAt: Date.now(),  
          resolvedAt: null  
        };  
  
        if (isFirebaseReady) {  
          db.collection('lost_items').add(newItem)  
            .then(() => {  
              alert('**분실물이** **성공적으로** **등록되었습니다**.');  
              document.getElementById('lostForm').reset();  
              switchTab('list');  
            })  
            .catch(err => alert('**등록에** **실패했습니다**: ' + err.message));  
        } else {  
          newItem.id = Date.now();  
          items.unshift(newItem);  
          localStorage.setItem('gijeon_lost_items', JSON.stringify(items));  
          alert('**분실물이** **성공적으로** **등록되었습니다**.');  
          document.getElementById('lostForm').reset();  
          switchTab('list');  
          renderItems();  
        }  
      };  
  
      if (file) {  
        const reader = new FileReader();  
        reader.onloadend = () => savePost(reader.result);  
        reader.readAsDataURL(file);  
      } else {  
        savePost(null);  
      }  
    });  
  </script>  
</body>  
</html>  
