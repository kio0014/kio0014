<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Everyday Records</title>

  <!-- Quill CSS -->
  <link
    href="https://cdn.quilljs.com/1.3.6/quill.snow.css"
    rel="stylesheet"
  />

  <!-- App styles -->
  <link rel="stylesheet" href="style.css" />

  <style>
    /* --- layout enhancement --- */
    .layout {
      display: flex;
      gap: 20px;
      align-items: flex-start;
    }

    .main {
      flex: 1;
    }

    .side-panel {
      width: 400px;
      max-width: 100%;
      position: sticky;
      top: 20px;
    }

    .side-panel iframe {
      width: 100%;
      height: 240px;
      border-radius: 8px;
      border: 2px solid #222;
      background: #000;
    }

    @media (max-width: 900px) {
      .layout {
        flex-direction: column;
      }
      .side-panel {
        width: 100%;
      }
    }
  </style>
</head>

<body>
  <div class="wrap">
    <div class="layout">

      <!-- MAIN CONTENT -->
      <div class="main">
        <h1>Timeline</h1>
        <span class="admin-bar" onclick="openAdminLogin()">```</span>
        <ol id="posts" class="posts"></ol>
      </div>

      <!-- RIGHT MINI INTERACTIVE SCREEN -->
      <aside class="side-panel">
        <iframe
          src="https://matias.me/nsfw/"
          loading="lazy"
          referrerpolicy="no-referrer"
        ></iframe>
      </aside>

    </div>
  </div>

  <!-- ADMIN OVERLAY -->
  <div class="overlay" id="overlay">
    <div class="card" id="stepPassword">
      <h2>Admin Login</h2>
      <div class="row">
        <label>Password</label>
        <input type="password" id="pass" />
      </div>
      <div class="actions">
        <button class="btn outline" onclick="closeModal()">Cancel</button>
        <button class="btn" onclick="verifyPassword()">Login</button>
      </div>
    </div>

    <div class="card hidden" id="stepForm">
      <h2 id="formTitle" onclick="toggleEditMode()">New / Edit Post</h2>
      <div
        id="editor"
        style="height:200px; background:#fff; border-radius:6px;"
      ></div>
      <div class="note" id="postMeta"></div>
      <div class="actions">
        <button class="btn outline" onclick="closeModal()">Close</button>
        <button class="btn" onclick="savePost()">Save</button>
      </div>
    </div>
  </div>

  <!-- IMAGE POPUP -->
  <div
    class="img-popup"
    id="imgPopup"
    onclick="this.style.display='none'"
  >
    <img id="popupImg" src="" />
  </div>

  <!-- Quill JS -->
  <script src="https://cdn.quilljs.com/1.3.6/quill.js"></script>

  <!-- Supabase JS -->
  <script src="https://unpkg.com/@supabase/supabase-js"></script>

  <!-- App logic -->
  <script src="app.js"></script>
</body>
</html>
