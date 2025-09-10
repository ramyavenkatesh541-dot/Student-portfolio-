<!doctype html>
<html lang="en">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>History of Animation — Student Digital Portfolio</title>
  <meta name="description" content="A clean, responsive single-file digital portfolio template about the history of animation — HTML, CSS and JavaScript (student-friendly)." />
  <style>
    /* ---------- Reset & base ---------- */
    :root{
      --bg:#0f1724; --card:#0b1220; --muted:#9aa6b2; --accent:#7dd3fc; --glass: rgba(255,255,255,0.04);
      --radius:14px; --max-w:1100px;
      color-scheme: dark;
    }
    *{box-sizing:border-box}
    html,body{height:100%}
    body{
      margin:0; font-family:Inter,ui-sans-serif,system-ui,-apple-system,"Segoe UI",Roboto,"Helvetica Neue",Arial;
      background: linear-gradient(180deg,#071224 0%, #081826 60%); color:#e6eef6; -webkit-font-smoothing:antialiased;
      line-height:1.45; padding:32px; display:flex; align-items:center; justify-content:center;
    }
    .container{width:100%; max-width:var(--max-w);}

    /* ---------- Header ---------- */
    header{display:flex; gap:16px; align-items:center; justify-content:space-between; margin-bottom:20px}
    .brand{display:flex; gap:12px; align-items:center}
    .logo{width:56px;height:56px;border-radius:12px;background:linear-gradient(135deg,var(--accent),#60a5fa);display:grid;place-items:center;font-weight:700;color:#01293a}
    h1{font-size:1.4rem;margin:0}
    .sub{color:var(--muted); font-size:.9rem}
    nav{display:flex;gap:10px}
    .btn{background:var(--glass); border:1px solid rgba(255,255,255,0.04); padding:8px 12px; border-radius:10px; cursor:pointer}

    /* ---------- Layout ---------- */
    .grid{display:grid; grid-template-columns: 1fr 360px; gap:20px}
    @media (max-width:900px){.grid{grid-template-columns:1fr} .aside{order:-1}}

    /* ---------- Card ---------- */
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01)); padding:18px; border-radius:var(--radius); box-shadow: 0 6px 30px rgba(2,6,23,0.6); border:1px solid rgba(255,255,255,0.03)}

    /* ---------- Hero / Intro ---------- */
    .hero{display:flex; gap:18px; align-items:center}
    .hero .left{flex:1}
    .avatar{width:128px;height:128px;border-radius:12px; background:linear-gradient(135deg,#111827,#0b1220); display:grid; place-items:center; font-size:2rem}
    .meta{margin-top:8px;color:var(--muted); font-size:.9rem}

    /* ---------- Timeline ---------- */
    .timeline{display:flex; flex-direction:column; gap:12px}
    .event{display:flex; gap:12px; align-items:flex-start}
    .event .dot{width:12px;height:12px;border-radius:50%; background:var(--accent); margin-top:8px}
    .event h3{margin:0 0 6px 0; font-size:1.02rem}
    .event p{margin:0;color:var(--muted)}

    /* ---------- Filters ---------- */
    .filters{display:flex; gap:8px; flex-wrap:wrap}
    .chip{padding:6px 10px; border-radius:999px; background:transparent; border:1px solid rgba(255,255,255,0.04); cursor:pointer}
    .chip.active{background:rgba(125,211,252,0.12); border-color:rgba(125,211,252,0.3)}

    /* ---------- Gallery ---------- */
    .gallery{display:grid; grid-template-columns: repeat(3,1fr); gap:8px}
    @media (max-width:700px){.gallery{grid-template-columns:repeat(2,1fr)}}
    .thumb{aspect-ratio:16/10; border-radius:8px; overflow:hidden; background:#04141f; display:grid; place-items:center; cursor:pointer}
    .thumb img{width:100%;height:100%;object-fit:cover}

    /* ---------- Aside ---------- */
    .aside .card + .card{margin-top:16px}
    .skill{display:flex;align-items:center; justify-content:space-between; gap:12px}
    .bar{height:8px;background:linear-gradient(90deg,#09202a,var(--glass)); border-radius:999px; flex:1; margin-left:8px}
    .bar > i{display:block;height:100%; border-radius:999px; background:linear-gradient(90deg,var(--accent),#60a5fa)}

    /* ---------- Modal ---------- */
    .modal{position:fixed; inset:0; display:none; align-items:center; justify-content:center; backdrop-filter:blur(6px); z-index:60}
    .modal.active{display:flex}
    .modal .panel{width:min(880px,94%); max-height:86vh; overflow:auto}

    /* ---------- Footer/print ---------- */
    footer{margin-top:18px; color:var(--muted); font-size:.85rem; text-align:center}
    @media print{ body{background:white;color:black} .card{border:none; box-shadow:none} .aside, nav, .btn{display:none} }

    /* small helpers */
    .muted{color:var(--muted)}
    .flex{display:flex;align-items:center}
    a{color:var(--accent); text-decoration:none}
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="brand">
        <div class="logo">HA</div>
        <div>
          <h1>History of Animation — Student Portfolio</h1>
          <div class="sub">Curated timeline, key figures, techniques and examples — editable template</div>
        </div>
      </div>
      <nav>
        <button class="btn" id="printBtn" title="Print or save as PDF">Print / Save PDF</button>
        <button class="btn" id="downloadJson">Export JSON</button>
      </nav>
    </header>

    <main class="grid">
      <section>
        <div class="card hero">
          <div class="left">
            <div style="display:flex;align-items:center;gap:12px;">
              <div class="avatar" aria-hidden="true">🎞️</div>
              <div>
                <strong style="font-size:1.1rem">[Student Name]</strong>
                <div class="meta">Course: Animation History | Class: 2025 | University / School</div>
              </div>
            </div>

            <p style="margin-top:12px;" class="muted">This portfolio presents a concise history of animation from early optical toys to modern CGI. Use the filters to focus on eras or techniques. Replace placeholder text and images with your own research, images, and citations before submission.</p>
          </div>
        </div>

        <div class="card" style="margin-top:16px">
          <div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:10px">
            <strong>Interactive Timeline</strong>
            <small class="muted">Click an event to view details</small>
          </div>

          <div class="filters" id="filters"></div>

          <div class="timeline" id="timeline" style="margin-top:12px"></div>
        </div>

        <div class="card" style="margin-top:16px">
          <strong style="display:block;margin-bottom:8px">Notable Techniques & Movements</strong>
          <ul class="muted">
            <li>Stop-motion / Claymation (e.g., J. Stuart Blackton, Willis O'Brien)</li>
            <li>Hand-drawn cel animation (Walt Disney, Ub Iwerks)</li>
            <li>Rotoscoping & experimental animation</li>
            <li>Computer-generated imagery (CGI) and 3D animation</li>
            <li>Motion graphics and the rise of digital tools</li>
          </ul>
        </div>

        <div class="card" style="margin-top:16px">
          <strong style="display:block;margin-bottom:8px">Gallery / Case Studies</strong>
          <div class="gallery" id="gallery">
            <!-- thumbnails populated by JS -->
          </div>
        </div>

      </section>

      <aside class="aside">
        <div class="card">
          <strong>About the Student</strong>
          <p class="muted" style="margin-top:8px">Short bio: Add your background, interests in animation, and links to your projects or GitHub. Mention role in group projects if applicable.</p>
          <div style="margin-top:12px">
            <div class="flex"><strong>Skills</strong><span style="margin-left:auto" class="muted">Level</span></div>
            <div style="margin-top:8px">
              <div class="skill"><span>Research</span><div class="bar" aria-hidden="true"><i style="width:82%"></i></div></div>
              <div class="skill" style="margin-top:8px"><span>Storyboarding</span><div class="bar" aria-hidden="true"><i style="width:68%"></i></div></div>
              <div class="skill" style="margin-top:8px"><span>Animation Tools</span><div class="bar" aria-hidden="true"><i style="width:74%"></i></div></div>
            </div>
          </div>
        </div>

        <div class="card">
          <strong>Resources</strong>
          <ul class="muted" style="margin-top:8px">
            <li><a href="#">The Illusion of Life — Frank Thomas & Ollie Johnston</a></li>
            <li><a href="#">Walt Disney Archives</a></li>
            <li><a href="#">Student's Bibliography (edit)</a></li>
          </ul>
        </div>

        <div class="card">
          <strong>Contact</strong>
          <p class="muted" style="margin-top:8px">Email: <a href="mailto:student@example.com">student@example.com</a></p>
          <p class="muted">Website / Portfolio: <a href="#">your-portfolio.example</a></p>
        </div>
      </aside>
    </main>

    <footer class="muted">Template created for student portfolios • Replace content and images with original sources and citations</footer>
  </div>

  <!-- Modal for event/gallery -->
  <div id="modal" class="modal" role="dialog" aria-modal="true" aria-hidden="true">
    <div class="panel card" style="padding:18px">
      <button class="btn" id="closeModal" style="float:right">Close</button>
      <div id="modalContent" style="margin-top:10px"></div>
    </div>
  </div>

  <script>
    // ---------- Sample data (replace with your research) ----------
    const DATA = {
      filters: ["All","Pre-cinema","Golden Age","Modern","Techniques"],
      events: [
        {id:1, era:"Pre-cinema", year:1824, title:"Optical Toys & Phenakistoscope", summary:"Early devices that created the illusion of motion using drawn frames.", details:"Phenakistoscope (1832) and zoetrope were critical pre-cinema devices that demonstrated persistence of vision.", img:null},
        {id:2, era:"Golden Age", year:1908, title:"First Animated Films", summary:"Émile Cohl and early hand-drawn animation experiments.", details:"Emile Cohl's 'Fantasmagorie' (1908) is often cited as the first true animated film.", img:null},
        {id:3, era:"Golden Age", year:1928, title:"Steamboat Willie & Sound", summary:"Synchronized sound transforms animation industry.", details:"Walt Disney's 'Steamboat Willie' (1928) popularized synchronized sound in cartoons.", img:null},
        {id:4, era:"Modern", year:1995, title:"Toy Story & CGI", summary:"First fully CGI feature film.", details:"Pixar's 'Toy Story' (1995) marked the arrival of feature-length CGI animation.", img:null},
        {id:5, era:"Techniques", year:1930, title:"Rotoscoping", summary:"Tracing live-action to create realistic motion.", details:"Invented by Max Fleischer; used widely for realistic motion effects.", img:null}
      ],
      gallery: [
        {id:1, title:"Fantasmagorie (1908)", src:null, caption:"Emile Cohl's experiments"},
        {id:2, title:"Steamboat Willie (1928)", src:null, caption:"Early synchronized sound"},
        {id:3, title:"Toy Story (1995)", src:null, caption:"Pioneering CGI feature"}
      ]
    };

    // ---------- DOM refs ----------
    const filtersEl = document.getElementById('filters');
    const timelineEl = document.getElementById('timeline');
    const galleryEl = document.getElementById('gallery');
    const modal = document.getElementById('modal');
    const modalContent = document.getElementById('modalContent');
    const closeModal = document.getElementById('closeModal');

    // ---------- Render filters ----------
    let activeFilter = 'All';
    function renderFilters(){
      filtersEl.innerHTML = '';
      DATA.filters.forEach(f=>{
        const btn = document.createElement('button');
        btn.className = 'chip' + (f===activeFilter? ' active':'');
        btn.textContent = f;
        btn.onclick = ()=>{ activeFilter = f; renderFilters(); renderTimeline(); };
        filtersEl.appendChild(btn);
      })
    }

    // ---------- Render timeline ----------
    function renderTimeline(){
      timelineEl.innerHTML='';
      const rows = DATA.events
        .filter(e => activeFilter==='All' || e.era===activeFilter)
        .sort((a,b)=>a.year - b.year);

      rows.forEach(ev=>{
        const node = document.createElement('div'); node.className='event';
        node.innerHTML = `<div class="dot" aria-hidden="true"></div><div style="flex:1"><h3>${ev.year} — ${ev.title}</h3><p class=\"muted\">${ev.summary}</p></div>`;
        node.onclick = ()=>openModal(`<h2>${ev.title} — ${ev.year}</h2><p class=\"muted\">${ev.details}</p>`);
        timelineEl.appendChild(node);
      })

      if(rows.length===0){ timelineEl.innerHTML = '<p class="muted">No events found for this filter.</p>' }
    }

    // ---------- Render gallery ----------
    function renderGallery(){
      galleryEl.innerHTML='';
      DATA.gallery.forEach(item=>{
        const div = document.createElement('div'); div.className='thumb';
        const img = document.createElement('img');
        img.alt = item.title; img.src = item.src || 'data:image/svg+xml;utf8,' + encodeURIComponent(`<svg xmlns=\"http://www.w3.org/2000/svg\" width=\"800\" height=\"500\"><rect width=\"100%\" height=\"100%\" fill=\"#061722\"/><text x=\"50%\" y=\"50%\" dominant-baseline=\"middle\" text-anchor=\"middle\" fill=\"#7dd3fc\" font-size=\"20\">${item.title}</text></svg>`);
        div.appendChild(img);
        div.onclick = ()=>openModal(`<h2>${item.title}</h2><p class=\"muted\">${item.caption}</p><div style=\"margin-top:10px;\"><img style=\"width:100%;border-radius:8px;\" src=\"${img.src}\" alt=\"${item.title}\"></div>`);
        galleryEl.appendChild(div);
      })
    }

    // ---------- Modal controls ----------
    function openModal(html){ modalContent.innerHTML = html; modal.classList.add('active'); modal.setAttribute('aria-hidden','false'); }
    function close(){ modal.classList.remove('active'); modal.setAttribute('aria-hidden','true'); }
    closeModal.onclick = close; modal.onclick = (e)=>{ if(e.target===modal) close() };

    // ---------- Export JSON ----------
    document.getElementById('downloadJson').addEventListener('click', ()=>{
      const blob = new Blob([JSON.stringify(DATA,null,2)], {type:'application/json'});
      const url = URL.createObjectURL(blob); const a = document.createElement('a'); a.href = url; a.download = 'animation-portfolio-data.json'; a.click(); URL.revokeObjectURL(url);
    });

    // ---------- Print button ----------
    document.getElementById('printBtn').addEventListener('click', ()=> window.print());

    // ---------- init ----------
    renderFilters(); renderTimeline(); renderGallery();

    // ---------- Accessibility: keyboard close ----------
    document.addEventListener('keydown', (e)=>{ if(e.key==='Escape') close(); });

    // ---------- Helpful note for students ----------
    console.log('Template ready. Replace DATA.events and DATA.gallery with your researched entries and images.');
  </script>
</body>
</html>
