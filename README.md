# Revista-N-03
# Creating a simple "Próximamente" webpage and saving it to /mnt/data/proximamente.html
html = """<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Próximamente</title>
  <style>
    :root{
      --bg1:#071427;
      --bg2:#11324a;
      --accent:#00d4ff;
      --glass: rgba(255,255,255,0.06);
    }
    html,body{height:100%;margin:0;font-family:Inter, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;background: radial-gradient(1000px 600px at 10% 10%, rgba(0,212,255,0.03), transparent), linear-gradient(160deg,var(--bg1),var(--bg2));color:#eaf6ff;}
    .wrap{min-height:100%;display:flex;align-items:center;justify-content:center;padding:40px;box-sizing:border-box}
    .card{width:100%;max-width:920px;padding:48px;border-radius:16px;background:linear-gradient(180deg,rgba(255,255,255,0.02),rgba(255,255,255,0.01));box-shadow:0 10px 30px rgba(2,6,23,0.6);backdrop-filter: blur(6px);border:1px solid rgba(255,255,255,0.03);display:flex;gap:32px;align-items:center}
    .left{flex:1}
    .logo{font-weight:700;letter-spacing:2px}
    h1{margin:0;font-size:54px;line-height:1;color:white}
    p.lead{margin:10px 0 20px;color:rgba(234,246,255,0.85);font-size:18px}
    .cta{display:inline-block;padding:12px 20px;border-radius:10px;background:linear-gradient(90deg,var(--accent),#6de0ff);color:#022; font-weight:600;text-decoration:none;box-shadow:0 6px 18px rgba(0,212,255,0.06)}
    .right{width:260px;text-align:center}
    .circle{width:160px;height:160px;border-radius:50%;display:inline-grid;place-items:center;background:conic-gradient(from 180deg at 50% 50%, rgba(0,212,255,0.12), rgba(255,255,255,0.02));border:1px solid rgba(255,255,255,0.04)}
    .big{font-size:28px;font-weight:700;color:var(--accent);margin:0}
    .small{font-size:13px;color:rgba(234,246,255,0.7);margin-top:6px}
    footer{margin-top:18px;color:rgba(234,246,255,0.5);font-size:13px}
    @media (max-width:720px){.card{flex-direction:column;text-align:center}.right{width:100%}h1{font-size:40px}}
  </style>
</head>
<body>
  <div class="wrap">
    <div class="card" role="main" aria-labelledby="coming-soon-title">
      <div class="left">
        <div class="logo">iMag Diplomate</div>
        <h1 id="coming-soon-title">Próximamente</h1>
        <p class="lead">Estamos preparando algo grande sobre seguridad marítima y comercio global. Vuelve pronto para ver la revista.</p>
        <a class="cta" href="#" onclick="copyLink();return false;">Copiar enlace para compartir</a>
        <footer>Hecho con ♡ — © <span id="year"></span> iMag Diplomate</footer>
      </div>
      <div class="right" aria-hidden="false">
        <div class="circle">
          <div>
            <div class="big" id="days">--</div>
            <div class="small">Días</div>
          </div>
        </div>
      </div>
    </div>
  </div>
<script>
  // Simple countdown placeholder (30 days from now)
  const target = new Date();
  target.setDate(target.getDate() + 30);
  function updateCountdown(){
    const now = new Date();
    const diff = Math.max(0, target - now);
    const days = Math.floor(diff / (1000*60*60*24));
    document.getElementById('days').textContent = days;
  }
  updateCountdown();
  setInterval(updateCountdown, 1000*60);
  document.getElementById('year').textContent = new Date().getFullYear();
  function copyLink(){
    const text = window.location.href || 'Archivo local: abra este archivo en su navegador';
    navigator.clipboard?.writeText(text).then(()=>{
      alert('Enlace copiado: ' + text);
    }).catch(()=>{
      prompt('Copie manualmente este enlace:', text);
    });
  }
</script>
</body>
</html>
"""
path = "/mnt/data/proximamente.html"
with open(path, "w", encoding="utf-8") as f:
    f.write(html)
print(f"Archivo creado en: {path}")