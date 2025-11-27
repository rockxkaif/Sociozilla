<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Sociozilla — Demo Gallery</title>
  <meta name="description" content="Sociozilla demo gallery" />
  <style>
    :root{--bg:#f6f8fb;--card:#ffffff;--accent:#0b74ff;--muted:#6b7280}
    *{box-sizing:border-box}body{font-family:Inter,system-ui,Arial;background:var(--bg);margin:0;color:#0f1724}
    .wrap{max-width:960px;margin:36px auto;padding:20px}
    header{display:flex;align-items:center;justify-content:space-between}
    h1{margin:0;font-size:22px}
    p.lead{color:var(--muted)}
    .gallery{display:grid;grid-template-columns:repeat(auto-fit,minmax(240px,1fr));gap:16px;margin-top:18px}
    .card{background:var(--card);padding:12px;border-radius:10px;box-shadow:0 6px 18px rgba(12,20,40,0.06);border:1px solid rgba(2,6,23,0.04)}
    .card img{width:100%;height:auto;border-radius:8px;cursor:pointer}
    .caption{font-size:13px;color:var(--muted);margin-top:8px}

    /* Lightbox */
    .lightbox{position:fixed;inset:0;display:none;align-items:center;justify-content:center;background:rgba(2,6,23,0.6);padding:24px;z-index:50}
    .lightbox.open{display:flex}
    .lightbox img{max-width:94%;max-height:84%;border-radius:8px;box-shadow:0 12px 40px rgba(2,6,23,0.7)}
    .close{position:absolute;top:18px;right:22px;background:#fff;border-radius:999px;padding:6px 10px;border:none;cursor:pointer;font-weight:700}

    footer{margin-top:26px;color:var(--muted);font-size:13px;text-align:center}

    @media (max-width:520px){.wrap{padding:12px}}
  </style>
</head>
<body>
  <div class="wrap">
    <header>
      <div>
        <h1>Sociozilla — Demo Gallery</h1>
        <p class="lead">Preview of desktop, tablet and mobile UIs. Click any image to view larger.</p>
      </div>
      <div style="text-align:right">
        <a href="https://github.com/rockxkaif/Sociozilla" target="_blank" rel="noopener noreferrer">View repo</a>
      </div>
    </header>

    <section class="gallery">
      <div class="card">
        <img src="images/sociozilla-desktop.png" alt="Sociozilla desktop" data-full="images/sociozilla-desktop.png" />
        <div class="caption">Desktop — feed, notifications, chat</div>
      </div>

      <div class="card">
        <img src="images/sociozilla-tablet.png" alt="Sociozilla tablet" data-full="images/sociozilla-tablet.png" />
        <div class="caption">Tablet — responsive layout</div>
      </div>

      <div class="card">
        <img src="images/sociozilla-mobile.png" alt="Sociozilla mobile" data-full="images/sociozilla-mobile.png" />
        <div class="caption">Mobile — feed and posts</div>
      </div>

      <div class="card">
        <img src="images/sociozilla-login.png" alt="Sociozilla login" data-full="images/sociozilla-login.png" />
        <div class="caption">Auth — login / register</div>
      </div>

      <div class="card">
        <img src="images/sociozilla-chat.png" alt="Sociozilla chat" data-full="images/sociozilla-chat.png" />
        <div class="caption">Chat UI</div>
      </div>

      <div class="card">
        <img src="images/sociozilla-notifications.png" alt="Sociozilla notifications" data-full="images/sociozilla-notifications.png" />
        <div class="caption">Notifications panel</div>
      </div>
    </section>

    <footer>
      <div>To deploy: push this `index.html` to the repo root and enable GitHub Pages (Settings → Pages → Branch: master / root)</div>
    </footer>
  </div>

  <div id="lightbox" class="lightbox" aria-hidden="true">
    <button class="close" aria-label="Close" onclick="closeLightbox()">✕</button>
    <img id="lightboxImg" src="" alt="Expanded screenshot" />
  </div>

  <script>
    const imgs = document.querySelectorAll('.gallery img');
    const lightbox = document.getElementById('lightbox');
    const lightboxImg = document.getElementById('lightboxImg');

    imgs.forEach(img => {
      img.addEventListener('click', () => {
        const src = img.getAttribute('data-full') || img.src;
        lightboxImg.src = src;
        lightbox.classList.add('open');
        lightbox.setAttribute('aria-hidden','false');
      });
    });

    function closeLightbox(){
      lightbox.classList.remove('open');
      lightbox.setAttribute('aria-hidden','true');
      lightboxImg.src = '';
    }

    // close on Esc
    document.addEventListener('keydown', (e) => {
      if(e.key === 'Escape') closeLightbox();
    });

    // click outside to close
    lightbox.addEventListener('click', (e) => {
      if(e.target === lightbox) closeLightbox();
    });
  </script>
</body>
</html>
