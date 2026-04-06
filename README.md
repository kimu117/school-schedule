<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>📒 がんばりノート v3</title>
<link href="https://fonts.googleapis.com/css2?family=Zen+Maru+Gothic:wght@400;500;700&family=Shippori+Mincho:wght@400;600;700&family=M+PLUS+Rounded+1c:wght@400;700;900&family=Kaisei+Decol:wght@400;700&family=Yomogi&display=swap" rel="stylesheet">
<style>
*{box-sizing:border-box;margin:0;padding:0}
:root{
  --cream:#fffdf8;--ink:#2d3436;--soft:#636e72;--border:#e0d9cf;
  --sky:#e8f4fd;--leaf:#d4edda;--sun:#fff3cd;--peach:#fde8e0;--lav:#ede8fd;
  --accent:#e17055;--green:#00b894;--blue:#0984e3;--purple:#6c5ce7;--pink:#fd79a8;
  --shadow:0 4px 20px rgba(0,0,0,0.08);
}
body{font-family:'Zen Maru Gothic',sans-serif;background:var(--cream);color:var(--ink);min-height:100vh;
  background-image:radial-gradient(circle at 10% 20%,rgba(232,244,253,.5) 0,transparent 45%),radial-gradient(circle at 90% 80%,rgba(237,232,253,.4) 0,transparent 45%)}

/* HEADER */
.hdr{background:white;border-bottom:3px solid var(--border);padding:11px 18px;display:flex;align-items:center;gap:11px;position:sticky;top:0;z-index:300;box-shadow:0 2px 10px rgba(0,0,0,.06)}
.hdr-logo{font-size:1.4rem}
.hdr-title h1{font-family:'M PLUS Rounded 1c',sans-serif;font-size:1rem;font-weight:900}
.hdr-title p{font-size:.62rem;color:var(--soft);margin-top:1px}
.hdr-r{margin-left:auto;display:flex;gap:7px;align-items:center}
.ver{background:var(--sun);color:#b7791f;font-size:.62rem;font-weight:700;padding:2px 7px;border-radius:8px}

/* NAV */
.nav{display:flex;background:white;border-bottom:2px solid var(--border);overflow-x:auto;scrollbar-width:none}
.nav::-webkit-scrollbar{display:none}
.nt{flex-shrink:0;padding:10px 14px;border:none;background:none;font-family:'Zen Maru Gothic',sans-serif;font-size:.8rem;font-weight:500;color:var(--soft);cursor:pointer;border-bottom:3px solid transparent;margin-bottom:-2px;transition:all .2s;white-space:nowrap;display:flex;align-items:center;gap:4px}
.nt.active{color:var(--accent);border-bottom-color:var(--accent);font-weight:700}

/* MAIN */
.main{max-width:980px;margin:0 auto;padding:20px 14px}
.sec{display:none}.sec.active{display:block}

/* CARDS */
.card{background:white;border-radius:16px;padding:20px;box-shadow:var(--shadow);border:1px solid rgba(0,0,0,.04);margin-bottom:15px}
.clabel{font-size:.65rem;font-weight:700;letter-spacing:.1em;color:var(--soft);margin-bottom:7px;text-transform:uppercase}

/* FORMS */
label{display:block;font-size:.78rem;font-weight:500;color:var(--soft);margin-bottom:4px}
input[type=text],textarea,select{width:100%;padding:8px 12px;border:2px solid var(--border);border-radius:10px;font-family:'Zen Maru Gothic',sans-serif;font-size:.88rem;color:var(--ink);background:var(--cream);outline:none;transition:border-color .2s,box-shadow .2s;resize:vertical}
input:focus,textarea:focus,select:focus{border-color:var(--accent);box-shadow:0 0 0 3px rgba(225,112,85,.1)}
.r2{display:grid;grid-template-columns:1fr 1fr;gap:12px;margin-bottom:12px}
.r3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:12px;margin-bottom:12px}
.fg{margin-bottom:12px}
.dv{height:1px;background:var(--border);margin:14px 0}

/* BUTTONS */
.btn{padding:9px 18px;border:none;border-radius:10px;font-family:'M PLUS Rounded 1c',sans-serif;font-size:.85rem;font-weight:700;cursor:pointer;transition:all .2s;display:inline-flex;align-items:center;gap:6px}
.bp{background:var(--accent);color:white;box-shadow:0 4px 10px rgba(225,112,85,.3)}.bp:hover{transform:translateY(-2px);box-shadow:0 6px 16px rgba(225,112,85,.4)}
.bg{background:var(--green);color:white;box-shadow:0 4px 10px rgba(0,184,148,.3)}.bg:hover{transform:translateY(-2px)}
.bpu{background:var(--purple);color:white;box-shadow:0 4px 10px rgba(108,92,231,.3)}.bpu:hover{transform:translateY(-2px)}
.bb{background:var(--blue);color:white;box-shadow:0 4px 10px rgba(9,132,227,.3)}.bb:hover{transform:translateY(-2px)}
.bpk{background:var(--pink);color:white;box-shadow:0 4px 10px rgba(253,121,168,.3)}.bpk:hover{transform:translateY(-2px)}
.bs{background:white;color:var(--ink);border:2px solid var(--border)}.bs:hover{border-color:var(--soft)}
.bsm{padding:6px 12px;font-size:.76rem}
.btn:disabled{opacity:.5;cursor:not-allowed;transform:none!important}
.fr{display:flex;gap:9px;align-items:center;flex-wrap:wrap}

/* TAGS */
.tags{display:flex;flex-wrap:wrap;gap:6px;margin-top:5px}
.tag{padding:5px 12px;border-radius:18px;font-size:.78rem;cursor:pointer;border:2px solid transparent;transition:all .15s;user-select:none;font-family:'M PLUS Rounded 1c',sans-serif;font-weight:500}
.tsk{background:var(--sky);color:#2980b9}.tlf{background:var(--leaf);color:#27ae60}
.tsn{background:var(--sun);color:#e67e22}.tpc{background:var(--peach);color:#c0392b}.tlv{background:var(--lav);color:#6c5ce7}
.tag.on{border-color:currentColor;font-weight:700}

/* CHILDREN */
.cg{display:grid;grid-template-columns:repeat(auto-fill,minmax(136px,1fr));gap:9px;margin-bottom:14px}
.cc{background:var(--cream);border:2px solid var(--border);border-radius:12px;padding:11px;text-align:center;cursor:pointer;transition:all .2s;position:relative}
.cc:hover{border-color:var(--accent);transform:translateY(-2px)}.cc.sel{border-color:var(--accent);background:rgba(225,112,85,.06)}
.cav{width:40px;height:40px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.25rem;margin:0 auto 6px}
.cn{font-size:.8rem;font-weight:700}.cg2{font-size:.68rem;color:var(--soft);margin-top:2px}
.cnt{position:absolute;top:4px;right:4px;background:var(--accent);color:white;font-size:.6rem;font-weight:700;border-radius:8px;padding:1px 5px}
.add-c{border:2px dashed var(--border);border-radius:12px;padding:11px;text-align:center;cursor:pointer;color:var(--soft);font-size:.8rem;display:flex;flex-direction:column;align-items:center;gap:4px;transition:all .2s}
.add-c:hover{border-color:var(--green);color:var(--green)}

/* KIDS GRID */
.kb{border-radius:13px;padding:9px 15px;cursor:pointer;font-family:'Zen Maru Gothic',sans-serif;font-size:.9rem;font-weight:700;display:flex;align-items:center;gap:7px;transition:all .2s;border:3px solid transparent}

/* MODE TOGGLE */
.mt{display:flex;gap:5px}
.mb{padding:7px 14px;border:2px solid var(--border);border-radius:18px;background:white;font-family:'Zen Maru Gothic',sans-serif;font-size:.78rem;font-weight:500;cursor:pointer;transition:all .2s;color:var(--soft)}
.mk{background:var(--green);border-color:var(--green);color:white;font-weight:700}
.mte{background:var(--purple);border-color:var(--purple);color:white;font-weight:700}

/* OUTPUT */
.out{background:var(--cream);border:2px solid var(--border);border-radius:12px;padding:16px;font-family:'Shippori Mincho',serif;font-size:.9rem;line-height:2;color:var(--ink);white-space:pre-wrap;min-height:80px;position:relative}
.cpb{position:absolute;top:7px;right:7px;padding:3px 9px;background:white;border:1px solid var(--border);border-radius:5px;font-size:.68rem;cursor:pointer;font-family:'Zen Maru Gothic',sans-serif;transition:all .2s}
.cpb:hover{background:var(--ink);color:white}

/* SPINNER */
.sp{width:17px;height:17px;border:3px solid rgba(255,255,255,.3);border-top-color:white;border-radius:50%;animation:spin .7s linear infinite;display:inline-block}
@keyframes spin{to{transform:rotate(360deg)}}
.dots span{width:5px;height:5px;background:var(--accent);border-radius:50%;animation:pulse 1.2s ease-in-out infinite;display:inline-block;margin:0 2px}
.dots span:nth-child(2){animation-delay:.2s}.dots span:nth-child(3){animation-delay:.4s}
@keyframes pulse{0%,80%,100%{opacity:.2;transform:scale(.8)}40%{opacity:1;transform:scale(1)}}
.gbar{display:flex;align-items:center;gap:9px;padding:9px 13px;background:rgba(225,112,85,.07);border-radius:9px;font-size:.8rem;color:var(--accent);margin-bottom:9px}

/* BADGES */
.bdg{display:inline-block;padding:2px 7px;border-radius:8px;font-size:.66rem;font-weight:700}
.bb2{background:var(--sky);color:#2980b9}.bg2{background:var(--leaf);color:#27ae60}
.bo{background:var(--sun);color:#e67e22}.bpu2{background:var(--lav);color:#6c5ce7}

/* MODAL */
.ov{display:none;position:fixed;inset:0;background:rgba(0,0,0,.4);z-index:1000;align-items:center;justify-content:center}
.ov.open{display:flex}
.modal{background:white;border-radius:20px;padding:24px;width:92%;max-width:500px;box-shadow:0 20px 60px rgba(0,0,0,.2);animation:mIn .25s ease;max-height:90vh;overflow-y:auto}
@keyframes mIn{from{transform:scale(.9);opacity:0}to{transform:scale(1);opacity:1}}
.modal h3{font-family:'Shippori Mincho',serif;font-size:1rem;margin-bottom:16px}
.mac{display:flex;gap:7px;justify-content:flex-end;margin-top:16px}
.emg{display:grid;grid-template-columns:repeat(8,1fr);gap:4px;margin:8px 0}
.eo{padding:6px;text-align:center;border-radius:6px;cursor:pointer;font-size:1.1rem;transition:background .15s;background:var(--cream)}
.eo:hover{background:var(--sky)}.eo.sel{background:var(--sun)}
.cog{display:flex;gap:7px;margin:6px 0}
.co2{width:28px;height:28px;border-radius:50%;cursor:pointer;border:3px solid transparent;transition:all .15s}
.co2.sel{border-color:var(--ink);transform:scale(1.15)}

/* REPORT STYLE LEARNING */
.example-card{border:2px solid var(--border);border-radius:12px;padding:14px;margin-bottom:10px;transition:all .2s;position:relative}
.example-card:hover{border-color:var(--accent)}
.ec-meta{font-size:.7rem;color:var(--soft);margin-bottom:6px;display:flex;gap:8px;align-items:center;flex-wrap:wrap}
.ec-text{font-family:'Shippori Mincho',serif;font-size:.88rem;line-height:1.9;color:var(--ink)}
.ec-del{position:absolute;top:8px;right:8px;background:none;border:none;color:var(--soft);cursor:pointer;font-size:.8rem;transition:color .2s}
.ec-del:hover{color:var(--accent)}
.rule-row{display:flex;align-items:flex-start;gap:10px;padding:10px 0;border-bottom:1px solid var(--border)}
.rule-row:last-child{border-bottom:none}
.rule-num{width:26px;height:26px;background:var(--lav);color:var(--purple);border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:.72rem;font-weight:700;flex-shrink:0}
.quality-badge{display:inline-flex;align-items:center;gap:3px;padding:2px 8px;border-radius:8px;font-size:.65rem;font-weight:700;cursor:pointer;transition:all .15s}
.qb-good{background:var(--leaf);color:#27ae60}.qb-ok{background:var(--sun);color:#e67e22}.qb-saved{background:#d1ecf1;color:#0c5460}

/* NEWSLETTER THEMES */
.theme-grid{display:grid;grid-template-columns:repeat(2,1fr);gap:12px;margin-bottom:16px}
@media(min-width:600px){.theme-grid{grid-template-columns:repeat(4,1fr)}}
.theme-opt{border:3px solid var(--border);border-radius:14px;padding:14px 10px;text-align:center;cursor:pointer;transition:all .2s;background:white}
.theme-opt:hover{transform:translateY(-3px);box-shadow:var(--shadow)}
.theme-opt.sel{border-color:var(--accent)}
.theme-opt .th-prev{width:100%;height:70px;border-radius:8px;margin-bottom:8px;display:flex;align-items:center;justify-content:center;font-size:1.6rem;overflow:hidden;position:relative}
.theme-opt .th-name{font-family:'M PLUS Rounded 1c',sans-serif;font-size:.78rem;font-weight:700}
.theme-opt .th-sub{font-size:.65rem;color:var(--soft);margin-top:2px}

.th-prev-pop{background:linear-gradient(135deg,#fdcb6e,#fd79a8,#a29bfe)}
.th-prev-clean{background:linear-gradient(135deg,#f8f9fa,#dee2e6);color:#495057}
.th-prev-hand{background:linear-gradient(135deg,#ffeaa7,#fab1a0)}
.th-prev-season{background:linear-gradient(135deg,#55efc4,#00b894)}

.nl-wrap{background:#ccc;padding:18px;border-radius:12px;margin-top:14px}
.nl-paper{background:white;width:100%;max-width:660px;margin:0 auto;border-radius:4px;box-shadow:0 4px 24px rgba(0,0,0,.18);overflow:hidden}

.nl-pop .nl-header-area{background:linear-gradient(135deg,#fdcb6e 0%,#fd79a8 50%,#a29bfe 100%);padding:26px 28px;position:relative;overflow:hidden}
.nl-pop .nl-header-area::before{content:'★';position:absolute;font-size:5rem;opacity:.12;top:-10px;right:-10px}
.nl-pop .nl-header-area::after{content:'♡';position:absolute;font-size:4rem;opacity:.12;bottom:-10px;left:10px}
.nl-pop .nl-ttl{font-family:'M PLUS Rounded 1c',sans-serif;font-size:1.5rem;font-weight:900;color:white;text-shadow:0 2px 8px rgba(0,0,0,.2);letter-spacing:.05em}
.nl-pop .nl-sub{font-size:.75rem;color:rgba(255,255,255,.9);margin-top:4px}
.nl-pop .nl-body-area{padding:20px 24px}
.nl-pop .nl-child-block{margin-bottom:20px;border-radius:14px;overflow:hidden;box-shadow:0 2px 10px rgba(0,0,0,.07)}
.nl-pop .nl-ch-head{padding:10px 14px;display:flex;align-items:center;gap:9px;font-weight:700;font-size:.9rem}
.nl-pop .nl-ch-head .av{width:34px;height:34px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1.05rem;background:white}
.nl-pop .nl-ch-body{padding:12px 16px;background:white}
.nl-pop .nl-ch-body .txt{font-size:.87rem;line-height:1.95;color:#333;font-family:'Shippori Mincho',serif}
.nl-pop .nl-photo-1{width:100%;object-fit:cover;max-height:180px;display:block}
.nl-pop .nl-photo-2{display:grid;grid-template-columns:1fr 1fr;gap:4px}
.nl-pop .nl-photo-2 img{width:100%;height:120px;object-fit:cover}
.nl-pop .nl-footer{background:#f8f8f8;padding:10px 20px;font-size:.7rem;color:#aaa;text-align:center}

.nl-clean .nl-header-area{background:white;padding:28px 32px;border-bottom:1px solid #dee2e6}
.nl-clean .nl-school-line{font-size:.7rem;color:#aaa;letter-spacing:.15em;text-transform:uppercase;margin-bottom:8px}
.nl-clean .nl-ttl{font-family:'Shippori Mincho',serif;font-size:1.6rem;font-weight:700;color:#2d3436;letter-spacing:.06em}
.nl-clean .nl-date-line{font-size:.72rem;color:#aaa;margin-top:6px;display:flex;align-items:center;gap:8px}
.nl-clean .nl-date-line::before{content:'';display:block;width:30px;height:1px;background:#ccc}
.nl-clean .nl-body-area{padding:24px 32px}
.nl-clean .nl-child-block{margin-bottom:28px;padding-bottom:28px;border-bottom:1px solid #f0f0f0}
.nl-clean .nl-child-block:last-child{border-bottom:none;margin-bottom:0;padding-bottom:0}
.nl-clean .nl-ch-head{display:flex;align-items:center;gap:10px;margin-bottom:12px}
.nl-clean .av{width:32px;height:32px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem}
.nl-clean .nl-ch-name{font-weight:700;font-size:.9rem}
.nl-clean .nl-ch-grade{font-size:.7rem;color:#aaa}
.nl-clean .txt{font-size:.88rem;line-height:2;color:#333;font-family:'Shippori Mincho',serif}
.nl-clean .nl-photo-1{width:100%;object-fit:cover;max-height:200px;border-radius:6px;display:block;margin:12px 0}
.nl-clean .nl-photo-2{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin:12px 0}
.nl-clean .nl-photo-2 img{width:100%;height:130px;object-fit:cover;border-radius:6px}
.nl-clean .nl-footer{padding:16px 32px;border-top:1px solid #f0f0f0;font-size:.7rem;color:#bbb;display:flex;justify-content:space-between}

.nl-hand{font-family:'Yomogi',cursive!important}
.nl-hand .nl-header-area{background:#fffef5;padding:26px 28px;border-bottom:3px dashed #f0c040}
.nl-hand .nl-ttl{font-family:'Yomogi',cursive;font-size:1.55rem;color:#2d3436;line-height:1.3}
.nl-hand .nl-sub{font-size:.75rem;color:#a0a0a0;font-family:'Yomogi',cursive;margin-top:6px}
.nl-hand .nl-body-area{padding:20px 24px;background:#fffef5}
.nl-hand .nl-child-block{margin-bottom:22px;background:white;border-radius:4px;padding:16px 18px;box-shadow:2px 3px 0 #f0c040,3px 5px 0 rgba(0,0,0,.05);border:1px solid #f0e68c}
.nl-hand .nl-ch-head{display:flex;align-items:center;gap:8px;margin-bottom:10px;padding-bottom:8px;border-bottom:2px dashed #f0c040}
.nl-hand .av{width:32px;height:32px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem}
.nl-hand .nl-ch-name{font-family:'Yomogi',cursive;font-weight:700;font-size:.92rem}
.nl-hand .txt{font-family:'Yomogi',cursive;font-size:.87rem;line-height:2.1;color:#333}
.nl-hand .nl-photo-1{width:100%;object-fit:cover;max-height:175px;border-radius:4px;display:block;margin-bottom:10px;border:3px solid white;box-shadow:2px 2px 0 #f0c040}
.nl-hand .nl-photo-2{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:10px}
.nl-hand .nl-photo-2 img{width:100%;height:110px;object-fit:cover;border-radius:4px;border:2px solid white;box-shadow:2px 2px 0 #f0c040;transform:rotate(-1deg)}
.nl-hand .nl-photo-2 img:nth-child(2){transform:rotate(1deg)}
.nl-hand .nl-footer{background:#fffef5;border-top:2px dashed #f0c040;padding:10px 20px;font-family:'Yomogi',cursive;font-size:.72rem;color:#aaa;text-align:center}

.nl-season .nl-header-area{padding:26px 28px;position:relative;overflow:hidden}
.nl-season .nl-header-area.spring{background:linear-gradient(135deg,#fce4ec,#f8bbd0,#f48fb1)}
.nl-season .nl-header-area.summer{background:linear-gradient(135deg,#e0f7fa,#b2ebf2,#4dd0e1)}
.nl-season .nl-header-area.autumn{background:linear-gradient(135deg,#fff3e0,#ffe0b2,#ffb74d)}
.nl-season .nl-header-area.winter{background:linear-gradient(135deg,#e8eaf6,#c5cae9,#9fa8da)}
.nl-season .nl-ttl{font-family:'Kaisei Decol',serif;font-size:1.5rem;font-weight:700;color:white;text-shadow:0 2px 6px rgba(0,0,0,.15)}
.nl-season .nl-sub{font-size:.75rem;color:rgba(255,255,255,.88);margin-top:5px}
.nl-season .season-deco{position:absolute;right:16px;top:50%;transform:translateY(-50%);font-size:3.5rem;opacity:.3}
.nl-season .nl-body-area{padding:20px 26px}
.nl-season .nl-child-block{margin-bottom:20px;border-radius:12px;overflow:hidden;border:1px solid rgba(0,0,0,.07)}
.nl-season .nl-ch-head{padding:10px 14px;display:flex;align-items:center;gap:8px}
.nl-season .nl-ch-head.spring-head{background:linear-gradient(90deg,#fce4ec,#fff)}
.nl-season .nl-ch-head.summer-head{background:linear-gradient(90deg,#e0f7fa,#fff)}
.nl-season .nl-ch-head.autumn-head{background:linear-gradient(90deg,#fff3e0,#fff)}
.nl-season .nl-ch-head.winter-head{background:linear-gradient(90deg,#e8eaf6,#fff)}
.nl-season .av{width:32px;height:32px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:1rem}
.nl-season .nl-ch-name{font-weight:700;font-size:.88rem}
.nl-season .nl-ch-body{padding:12px 16px;background:white}
.nl-season .txt{font-size:.87rem;line-height:2;color:#333;font-family:'Shippori Mincho',serif}
.nl-season .nl-photo-1{width:100%;object-fit:cover;max-height:175px;display:block}
.nl-season .nl-photo-2{display:grid;grid-template-columns:1fr 1fr}
.nl-season .nl-photo-2 img{width:100%;height:115px;object-fit:cover}
.nl-season .nl-footer{padding:10px 20px;background:#f8f9fa;font-size:.7rem;color:#bbb;text-align:center}

.season-btns{display:flex;gap:7px;flex-wrap:wrap;margin:8px 0}
.ssbtn{padding:6px 14px;border-radius:16px;border:2px solid var(--border);background:white;font-family:'Zen Maru Gothic',sans-serif;font-size:.75rem;cursor:pointer;transition:all .2s}
.ssbtn.sel{font-weight:700;border-color:currentColor}
.ssbtn.spring{color:#e91e63}.ssbtn.summer{color:#00bcd4}.ssbtn.autumn{color:#ff9800}.ssbtn.winter{color:#5c6bc0}

.ei{padding:11px 13px;border-left:4px solid var(--accent);background:var(--cream);border-radius:0 10px 10px 0;margin-bottom:9px}
.ei-m{font-size:.7rem;color:var(--soft);margin-bottom:4px}.ei-t{font-size:.85rem;line-height:1.7}

.pdrop{border:2px dashed var(--border);border-radius:13px;padding:24px;text-align:center;cursor:pointer;transition:all .2s;background:var(--cream)}
.pdrop:hover,.pdrop.drag{border-color:var(--accent);background:var(--peach)}
.pdrop .pic{font-size:2rem;margin-bottom:7px}.pdrop p{font-size:.8rem;color:var(--soft)}
.pgrid{display:grid;grid-template-columns:repeat(auto-fill,minmax(90px,1fr));gap:7px;margin-top:10px}
.pt{position:relative;border-radius:9px;overflow:hidden;aspect-ratio:1;background:#f0ebe4}
.pt img{width:100%;height:100%;object-fit:cover}
.pt .pd{position:absolute;top:2px;right:2px;background:rgba(0,0,0,.5);color:white;border:none;border-radius:50%;width:19px;height:19px;font-size:.65rem;cursor:pointer;display:flex;align-items:center;justify-content:center}
.pa{display:flex;align-items:center;gap:10px;padding:10px 0;border-bottom:1px solid var(--border)}
.pa:last-child{border-bottom:none}
.pas{border:2px dashed var(--border);border-radius:9px;padding:8px 12px;font-size:.78rem;color:var(--soft);cursor:pointer;transition:all .2s;display:flex;align-items:center;gap:5px}
.pas:hover{border-color:var(--accent);color:var(--accent)}
.paimg{width:54px;height:54px;border-radius:7px;object-fit:cover;border:2px solid var(--green);position:relative;display:inline-block}

.set-r{display:flex;align-items:center;justify-content:space-between;padding:11px 0;border-bottom:1px solid var(--border);gap:10px}
.set-r:last-child{border-bottom:none}
.set-l{font-size:.86rem;font-weight:500}
.set-s{font-size:.7rem;color:var(--soft);margin-top:2px}

@media print{
.hdr,.nav,.no-print,button{display:none!important}
.nl-wrap{background:none;padding:0;margin-top:0;}
.nl-paper{box-shadow:none;max-width:100%}
body{background:white;background-image:none;}
}
@media(max-width:600px){.r2,.r3{grid-template-columns:1fr}.cg{grid-template-columns:repeat(auto-fill,minmax(116px,1fr))}.theme-grid{grid-template-columns:1fr 1fr}}
</style>
</head>
<body>

<header class="hdr">
  <div class="hdr-logo">📒</div>
  <div class="hdr-title"><h1>がんばりノート</h1><p>支援学級 振り返り・通信・所見システム</p></div>
  <div class="hdr-r"><span class="ver">v3.0</span></div>
</header>

<nav class="nav">
  <button class="nt active" data-tab="children" onclick="goTab('children')">👦 子どもたち</button>
  <button class="nt" data-tab="input" onclick="goTab('input')">✏️ 振り返り</button>
  <button class="nt" data-tab="photos" onclick="goTab('photos')">📸 写真</button>
  <button class="nt" data-tab="newsletter" onclick="goTab('newsletter')">📰 学級通信</button>
  <button class="nt" data-tab="report" onclick="goTab('report')">📋 所見</button>
  <button class="nt" data-tab="style" onclick="goTab('style')">✨ 所見スタイル</button>
  <button class="nt" data-tab="settings" onclick="goTab('settings')">⚙️ 設定</button>
</nav>

<div class="main">

<!-- ===== CHILDREN ===== -->
<section id="sec-children" class="sec active">
  <div style="font-family:'Shippori Mincho',serif;font-size:1.1rem;margin-bottom:4px">👦 子どもたち</div>
  <div style="font-size:.76rem;color:var(--soft);margin-bottom:18px">クラスの子どもを登録・管理します</div>
  <div class="cg" id="chGrid"></div>
  <button class="btn bg" onclick="openAddChild()">＋ 子どもを追加</button>
</section>

<!-- ===== INPUT ===== -->
<section id="sec-input" class="sec">
  <div style="display:flex;align-items:center;gap:9px;margin-bottom:16px;flex-wrap:wrap">
    <div style="font-family:'Shippori Mincho',serif;font-size:1.1rem">✏️ 振り返りを入力</div>
    <div class="mt" style="margin-left:auto">
      <button class="mb mk" id="mbK" onclick="setMode('kids')">🧒 子どもモード</button>
      <button class="mb" id="mbT" onclick="setMode('teacher')">👩‍🏫 先生モード</button>
    </div>
  </div>

  <div id="mKids">
    <div class="card"><div class="clabel">だれのふりかえり？</div><div id="kCG" style="display:flex;flex-wrap:wrap;gap:8px"></div></div>
    <div class="card">
      <div class="r2">
        <div class="fg"><label>きょうの日付</label><input type="text" id="kDt" placeholder=""></div>
        <div class="fg"><label>なんの じかん？</label><input type="text" id="kSj" placeholder="さんすう、たいいく…"></div>
      </div>
      <div class="fg"><label>✨ きょうのがんばり</label>
        <div class="tags" id="kTg">
          <span class="tag tsk" onclick="tg(this)">さいごまでできた</span>
          <span class="tag tsk" onclick="tg(this)">しゅうちゅうできた</span>
          <span class="tag tlf" onclick="tg(this)">ともだちとなかよくできた</span>
          <span class="tag tlf" onclick="tg(this)">はっぴょうできた</span>
          <span class="tag tsn" onclick="tg(this)">あきらめずにやった</span>
          <span class="tag tsn" onclick="tg(this)">できることがふえた</span>
          <span class="tag tpc" onclick="tg(this)">おちついてできた</span>
          <span class="tag tlv" onclick="tg(this)">ルールをまもれた</span>
          <span class="tag tlv" onclick="tg(this)">せんせいといっしょにできた</span>
        </div>
      </div>
      <div class="fg"><label>💬 きょうのこと、おしえて！</label><textarea id="kTx" rows="4" placeholder="がんばったこと、うれしかったこと、なんでもOK！"></textarea></div>
      <div class="dv"></div>
      <div class="fr"><button class="btn bg" onclick="saveKids()" style="font-size:.95rem;padding:12px 24px">💾 ほぞんする！</button><button class="btn bs" onclick="clearK()">クリア</button></div>
    </div>
  </div>

  <div id="mTeacher" style="display:none">
    <div class="card">
      <div class="r3">
        <div class="fg"><label>子どもを選ぶ</label><select id="tCh" onchange="renderEPrev()"><option value="">-- 選んでください --</option></select></div>
        <div class="fg"><label>日付</label><input type="text" id="tDt" placeholder=""></div>
        <div class="fg"><label>教科・活動</label><input type="text" id="tSj" placeholder="算数、生活単元…"></div>
      </div>
      <div class="fg"><label>✨ 今日のがんばり</label>
        <div class="tags" id="tTg">
          <span class="tag tsk" onclick="tg(this)">最後まで取り組めた</span>
          <span class="tag tsk" onclick="tg(this)">集中できた</span>
          <span class="tag tlf" onclick="tg(this)">友だちと仲良くできた</span>
          <span class="tag tlf" onclick="tg(this)">自分から発言した</span>
          <span class="tag tsn" onclick="tg(this)">あきらめずにやった</span>
          <span class="tag tsn" onclick="tg(this)">できることが増えた</span>
          <span class="tag tpc" onclick="tg(this)">ゆっくり落ち着けた</span>
          <span class="tag tlv" onclick="tg(this)">自分でルールを守れた</span>
          <span class="tag tlv" onclick="tg(this)">先生と一緒にできた</span>
        </div>
      </div>
      <div class="r2">
        <div class="fg"><label>📝 子ども自身のことば</label><textarea id="tTx" rows="3" placeholder="そのまま書いてOK！"></textarea></div>
        <div class="fg"><label>👀 先生の観察メモ</label><textarea id="tNt" rows="3" placeholder="気づいたこと、変化など…"></textarea></div>
      </div>
      <div class="dv"></div>
      <div class="fr"><button class="btn bp" onclick="saveTeacher()">💾 振り返りを保存</button><button class="btn bs" onclick="clearT()">クリア</button></div>
    </div>
  </div>
  <div id="ePrev"></div>
</section>

<!-- ===== PHOTOS ===== -->
<section id="sec-photos" class="sec">
  <div style="font-family:'Shippori Mincho',serif;font-size:1.1rem;margin-bottom:4px">📸 写真管理</div>
  <div style="font-size:.76rem;color:var(--soft);margin-bottom:18px">写真をアップして子どもごとに割り当てます</div>
  <div class="card">
    <div class="pdrop" id="dropZ" onclick="document.getElementById('fIn').click()" ondragover="dOv(event)" ondragleave="dLv(event)" ondrop="dDp(event)">
      <div class="pic">🖼️</div><p>クリックまたはドラッグ＆ドロップ</p><p style="font-size:.7rem;margin-top:3px;color:#bbb">JPG・PNG対応</p>
    </div>
    <input type="file" id="fIn" accept="image/*" multiple onchange="hFiles(this.files)" style="display:none">
    <div class="pgrid" id="pGrid"></div>
  </div>
  <div class="card"><div class="clabel">子どもに写真を割り当て</div><div id="assignA"></div></div>
</section>

<!-- ===== NEWSLETTER ===== -->
<section id="sec-newsletter" class="sec">
  <div style="background:linear-gradient(135deg,var(--sky),var(--lav));border-radius:14px;padding:20px;text-align:center;margin-bottom:18px">
    <div style="font-family:'Shippori Mincho',serif;font-size:1.3rem;font-weight:700">📰 学級通信をつくる</div>
    <p style="font-size:.75rem;color:var(--soft);margin-top:4px">テーマを選んで、おしゃれな通信を生成・印刷</p>
  </div>

  <div class="card no-print">
    <div class="clabel">デザインテーマ</div>
    <div class="theme-grid">
      <div class="theme-opt sel" id="th-pop" onclick="selTheme('pop',this)">
        <div class="th-prev th-prev-pop">🎉✨🌈</div>
        <div class="th-name">ポップ</div><div class="th-sub">カラフル・にぎやか</div>
      </div>
      <div class="theme-opt" id="th-clean" onclick="selTheme('clean',this)">
        <div class="th-prev th-prev-clean" style="color:#555;font-size:1rem;font-family:'Shippori Mincho',serif">すっきり<br>読みやすい</div>
        <div class="th-name">シンプル</div><div class="th-sub">すっきり・丁寧</div>
      </div>
      <div class="theme-opt" id="th-hand" onclick="selTheme('hand',this)">
        <div class="th-prev th-prev-hand" style="font-family:'Yomogi',cursive;font-size:.85rem;color:#555">手書き風<br>あたたかい</div>
        <div class="th-name">手書き風</div><div class="th-sub">温かみのある雰囲気</div>
      </div>
      <div class="theme-opt" id="th-season" onclick="selTheme('season',this)">
        <div class="th-prev th-prev-season">🌸🍃🍂❄️</div>
        <div class="th-name">季節</div><div class="th-sub">春夏秋冬で切り替え</div>
      </div>
    </div>

    <div id="seasonPicker" style="display:none">
      <label>季節を選ぶ</label>
      <div class="season-btns">
        <button class="ssbtn spring sel" id="ss-spring" onclick="selSeason('spring',this)">🌸 春</button>
        <button class="ssbtn summer" id="ss-summer" onclick="selSeason('summer',this)">🌊 夏</button>
        <button class="ssbtn autumn" id="ss-autumn" onclick="selSeason('autumn',this)">🍂 秋</button>
        <button class="ssbtn winter" id="ss-winter" onclick="selSeason('winter',this)">❄️ 冬</button>
      </div>
    </div>
    <div class="dv"></div>

    <div class="r2">
      <div class="fg"><label>通信タイトル</label><input type="text" id="nlT" placeholder="例：みんながんばったね！"></div>
      <div class="fg"><label>発行日</label><input type="text" id="nlD" placeholder=""></div>
    </div>
    <div class="fg"><label>対象（空欄＝全員）</label><select id="nlC"><option value="">全員</option></select></div>
    <div class="fg">
      <label>文章のトーン</label>
      <div class="tags">
        <span class="tag tlf on" id="tnW" onclick="selTone('warm',this)">💛 温かく親しみやすく</span>
        <span class="tag tsk" id="tnF" onclick="selTone('formal',this)">📄 丁寧・フォーマル</span>
        <span class="tag tsn" id="tnS" onclick="selTone('story',this)">📖 エピソード風</span>
      </div>
    </div>
    <div class="fr">
      <button class="btn bp" id="nlBtn" onclick="genNL()">✨ 学級通信を生成</button>
      <button class="btn bb bsm no-print" onclick="window.print()">🖨️ 印刷・PDF保存</button>
    </div>
  </div>

  <div id="nlPrevWrap" style="display:none">
    <div class="nl-wrap"><div id="nlPaper" class="nl-paper nl-pop"></div></div>
    <div class="fr no-print" style="margin-top:10px;justify-content:center">
      <button class="btn bb bsm" onclick="window.print()">🖨️ 印刷・PDF保存</button>
    </div>
  </div>
</section>

<!-- ===== REPORT ===== -->
<section id="sec-report" class="sec">
  <div style="font-family:'Shippori Mincho',serif;font-size:1.1rem;margin-bottom:4px">📋 所見を作成</div>
  <div style="font-size:.76rem;color:var(--soft);margin-bottom:18px">蓄積したスタイルを活かして所見を生成します</div>
  <div class="card">
    <div class="r2">
      <div class="fg"><label>対象の子ども</label><select id="rpC"><option value="">-- 選んでください --</option></select></div>
      <div class="fg"><label>学期</label><select id="rpTm"><option>1学期</option><option>2学期</option><option>3学期</option></select></div>
    </div>
    <div class="r2">
      <div class="fg"><label>文字数の目安</label>
        <select id="rpL"><option value="short">短め（60〜80字）</option><option value="medium" selected>標準（100〜150字）</option><option value="long">詳しく（200字前後）</option></select>
      </div>
      <div class="fg"><label>重視する観点</label>
        <select id="rpF"><option value="all">まんべんなく</option><option value="social">社会性・友人関係</option><option value="learning">学習への取り組み</option><option value="growth">成長・変化</option><option value="strength">得意なこと・強み</option></select>
      </div>
    </div>
    <div class="fg"><label>追加で伝えたいこと（任意）</label><textarea id="rpE" rows="2" placeholder="特に伝えたいエピソードや変化など"></textarea></div>
    <div id="styleIndicator" style="margin-bottom:12px"></div>
    <button class="btn bpu" id="rpBtn" onclick="genReport()">📝 所見を生成する</button>
  </div>
  <div id="rpOut"></div>
</section>

<!-- ===== STYLE LEARNING ===== -->
<section id="sec-style" class="sec">
  <div style="font-family:'Shippori Mincho',serif;font-size:1.1rem;margin-bottom:4px">✨ 所見スタイルを学習させる</div>
  <div style="font-size:.76rem;color:var(--soft);margin-bottom:18px">過去の所見例と書き方ルールを登録して、AIに先生の文体を覚えさせます</div>

  <div class="card">
    <div class="clabel" style="margin-bottom:12px">📌 書き方ルール（AIへの指示）</div>
    <div id="rulesList"></div>
    <div class="dv"></div>
    <div class="r2" style="align-items:flex-end">
      <div class="fg" style="margin-bottom:0"><label>新しいルールを追加</label><input type="text" id="newRule" placeholder="例：語尾は「〜でした」より「〜ています」を使う"></div>
      <button class="btn bp" onclick="addRule()" style="height:40px">追加</button>
    </div>
    <div style="margin-top:12px">
      <div class="clabel">よく使うルールの例</div>
      <div class="tags" style="margin-top:6px">
        <span class="tag tsk" onclick="quickRule(this)">語尾は「〜しています」「〜できます」を使う</span>
        <span class="tag tsk" onclick="quickRule(this)">主語を省いてテンポよく書く</span>
        <span class="tag tlf" onclick="quickRule(this)">具体的なエピソードを必ず1つ入れる</span>
        <span class="tag tlf" onclick="quickRule(this)">前向きな表現で締めくくる</span>
        <span class="tag tsn" onclick="quickRule(this)">「〜が苦手」は使わず「〜を練習しています」と書く</span>
        <span class="tag tsn" onclick="quickRule(this)">保護者へのメッセージで締める</span>
        <span class="tag tlv" onclick="quickRule(this)">一文は50字以内にまとめる</span>
      </div>
    </div>
  </div>

  <div class="card">
    <div class="clabel" style="margin-bottom:12px">📂 過去の所見例を登録（AIが文体を真似ます）</div>
    <div id="exList"></div>
    <div class="dv"></div>
    <div style="font-size:.78rem;color:var(--soft);margin-bottom:10px">✏️ 新しい例を追加</div>
    <div class="r2">
      <div class="fg"><label>学年</label>
        <select id="exGr"><option>小4</option><option>小5</option><option>小6</option></select>
      </div>
      <div class="fg"><label>学期</label>
        <select id="exTm"><option>1学期</option><option>2学期</option><option>3学期</option></select>
      </div>
    </div>
    <div class="fg"><label>所見の文章</label><textarea id="exTx" rows="4" placeholder="実際に書いた（または理想の）所見の文章をそのまま貼り付けてください"></textarea></div>
    <div class="fg"><label>メモ（任意）</label><input type="text" id="exMemo" placeholder="例：落ち着きのある子向け、学習面で伸びた子など"></div>
    <button class="btn bg" onclick="addExample()">登録する</button>
  </div>

  <div class="card">
    <div class="clabel" style="margin-bottom:12px">🔄 生成済み所見をフィードバック</div>
    <p style="font-size:.82rem;color:var(--soft);line-height:1.7;margin-bottom:12px">所見タブで生成した文章を手直しして「いい例として保存」すると、次回の生成に活かされます。</p>
    <div id="feedbackList"></div>
  </div>
</section>

<!-- ===== SETTINGS ===== -->
<section id="sec-settings" class="sec">
  <div style="font-family:'Shippori Mincho',serif;font-size:1.1rem;margin-bottom:18px">⚙️ 設定</div>
  <div class="card">
    <div class="clabel">学校・クラス情報</div>
    <div class="r2"><div class="fg"><label>学校名</label><input type="text" id="sSchool" placeholder="○○小学校" oninput="saveSets()"></div><div class="fg"><label>クラス名</label><input type="text" id="sClass" placeholder="支援学級" oninput="saveSets()"></div></div>
    <div class="fg"><label>担任名</label><input type="text" id="sTeacher" placeholder="先生のお名前" oninput="saveSets()"></div>
  </div>
  <div class="card">
    <div class="clabel">データ管理</div>
    <div class="set-r"><div><div class="set-l">📥 エクスポート</div><div class="set-s">全データをJSONで保存</div></div><button class="btn bs bsm" onclick="expData()">保存</button></div>
    <div class="set-r"><div><div class="set-l">📤 インポート</div><div class="set-s">バックアップから復元</div></div><button class="btn bs bsm" onclick="document.getElementById('impIn').click()">読み込み</button><input type="file" id="impIn" accept=".json" onchange="impData(this)" style="display:none"></div>
    <div class="set-r"><div><div class="set-l" style="color:var(--accent)">🗑️ 全データ削除</div><div class="set-s">リセット（元に戻せません）</div></div><button class="btn bs bsm" style="color:var(--accent);border-color:var(--accent)" onclick="resetAll()">削除</button></div>
  </div>
</section>

</div>

<!-- MODALS -->
<div class="ov" id="addChildMod">
  <div class="modal">
    <h3>👦 子どもを追加</h3>
    <div class="fg"><label>名前</label><input type="text" id="ncN" placeholder="例：Aさん、たろうくん"></div>
    <div class="r2"><div class="fg"><label>学年</label><select id="ncG"><option>小4</option><option>小5</option><option>小6</option><option>小1</option><option>小2</option><option>小3</option><option>中1</option><option>中2</option><option>中3</option></select></div></div>
    <div class="fg"><label>絵文字</label><div class="emg" id="emG"></div></div>
    <div class="fg"><label>カラー</label><div class="cog" id="coG"></div></div>
    <div class="mac"><button class="btn bs bsm" onclick="closeM('addChildMod')">キャンセル</button><button class="btn bp bsm" onclick="saveChild()">追加</button></div>
  </div>
</div>

<div class="ov" id="photoMod">
  <div class="modal">
    <h3 id="pmTtl">写真を選ぶ</h3>
    <div id="pmGrid" style="display:grid;grid-template-columns:repeat(4,1fr);gap:7px;max-height:280px;overflow-y:auto;margin-bottom:12px"></div>
    <div class="mac"><button class="btn bs bsm" onclick="closeM('photoMod')">キャンセル</button><button class="btn bg bsm" onclick="confirmPA()">決定</button></div>
  </div>
</div>

<script>
const EMOJIS=['🌟','⭐','🌈','🌸','🌺','🍀','🌻','🦋','🐬','🐧','🐼','🦊','🐸','🌙','☀️','🎈'];
const COLS=['#e8f4fd','#d4edda','#fff3cd','#fde8e0','#ede8fd','#d1ecf1','#ffeeba','#f8d7da'];
const DEF_CH=[
  {id:'c1',name:'Aさん',grade:'小4',emoji:'🌸',color:'#fde8e0'},
  {id:'c2',name:'Bさん',grade:'小4',emoji:'🌻',color:'#fff3cd'},
  {id:'c3',name:'Cさん',grade:'小5',emoji:'🌈',color:'#e8f4fd'},
  {id:'c4',name:'Dさん',grade:'小5',emoji:'🍀',color:'#d4edda'},
  {id:'c5',name:'Eさん',grade:'小6',emoji:'⭐',color:'#fff3cd'},
  {id:'c6',name:'Fさん',grade:'小6',emoji:'🦋',color:'#ede8fd'},
  {id:'c7',name:'Gさん',grade:'小6',emoji:'🌟',color:'#d1ecf1'},
];
let S={
  children:[],entries:[],photos:[],
  styleRules:[],styleExamples:[],
  generatedReports:[],
  settings:{school:'',class:'支援学級',teacher:''},
  selEmoji:'🌟',selCol:'#e8f4fd',
  kSelC:null,nlTone:'warm',nlTheme:'pop',nlSeason:'spring',
  pmTarget:null
};

// ローカルストレージを使ってデータを保存するように修正
async function load(){
  try{
    const r=localStorage.getItem('gnv3');
    if(r){
      const d=JSON.parse(r);
      Object.assign(S,d);
    }
  }catch(e){}
  if(!S.children||!S.children.length) S.children=DEF_CH.map(c=>({...c}));
  if(!S.photos) S.photos=[];
  if(!S.styleRules) S.styleRules=[];
  if(!S.styleExamples) S.styleExamples=[];
  if(!S.generatedReports) S.generatedReports=[];
  renderAll(); applySettings();
}
async function save(){
  try{
    localStorage.setItem('gnv3',JSON.stringify(S));
  }catch(e){console.error(e);}
}

function goTab(n){
  document.querySelectorAll('.sec').forEach(s=>s.classList.remove('active'));
  document.querySelectorAll('.nt').forEach(t=>t.classList.remove('active'));
  document.getElementById('sec-'+n).classList.add('active');
  document.querySelector(`.nt[data-tab="${n}"]`)?.classList.add('active');
  if(n==='input'||n==='newsletter'||n==='report') syncSels();
  if(n==='photos'){renderPGrid();renderAssign();}
  if(n==='style'){renderRules();renderExamples();renderFeedback();}
  if(n==='report') updateStyleIndicator();
}

function renderAll(){renderCh();renderKCG();syncSels();renderEPrev();renderPGrid();renderAssign();}

function renderCh(){
  const g=document.getElementById('chGrid');g.innerHTML='';
  S.children.forEach(c=>{
    const cnt=S.entries.filter(e=>e.childId===c.id).length;
    const d=document.createElement('div');d.className='cc';
    d.innerHTML=`${cnt?`<div class="cnt">${cnt}件</div>`:''}
      <div class="cav" style="background:${c.color}">${c.emoji}</div>
      <div class="cn">${c.name}</div><div class="cg2">${c.grade}</div>`;
    d.onclick=()=>{goTab('input');syncSels();document.getElementById('tCh').value=c.id;setMode('teacher');};
    g.appendChild(d);
  });
  const a=document.createElement('div');a.className='add-c';a.innerHTML='<span style="font-size:1.3rem">＋</span><span>追加</span>';a.onclick=openAddChild;g.appendChild(a);
}

function syncSels(){
  ['tCh','nlC','rpC'].forEach(id=>{
    const el=document.getElementById(id);if(!el)return;
    const v=el.value;
    el.innerHTML=id==='tCh'?'<option value="">-- 選んでください --</option>':id==='nlC'?'<option value="">全員</option>':'<option value="">-- 選んでください --</option>';
    S.children.forEach(c=>{const o=document.createElement('option');o.value=c.id;o.textContent=`${c.emoji} ${c.name}（${c.grade}）`;el.appendChild(o);});
    if(v)el.value=v;
  });
}

let iMode='kids';
function setMode(m){
  iMode=m;
  document.getElementById('mKids').style.display=m==='kids'?'':'none';
  document.getElementById('mTeacher').style.display=m==='teacher'?'':'none';
  document.getElementById('mbK').className='mb'+(m==='kids'?' mk':'');
  document.getElementById('mbT').className='mb'+(m==='teacher'?' mte':'');
}

function renderKCG(){
  const g=document.getElementById('kCG');if(!g)return;g.innerHTML='';
  S.children.forEach(c=>{
    const b=document.createElement('button');const sel=S.kSelC===c.id;
    b.className='kb';b.style.cssText=`background:${c.color};border-color:${sel?'#2d3436':'transparent'};transform:${sel?'scale(1.07)':'scale(1)'}`;
    b.innerHTML=`<span style="font-size:1.2rem">${c.emoji}</span><span>${c.name}</span>`;
    b.onclick=()=>{S.kSelC=c.id;renderKCG();};g.appendChild(b);
  });
}

function tg(el){el.classList.toggle('on');}
function stags(id){return Array.from(document.querySelectorAll(`#${id} .tag.on`)).map(t=>t.textContent);}

function saveKids(){
  if(!S.kSelC){alert('だれのふりかえりか選んでね！');return;}
  const tx=document.getElementById('kTx').value.trim();const tg2=stags('kTg');
  if(!tx&&!tg2.length){alert('がんばったこと、教えてね！');return;}
  S.entries.push({id:Date.now()+'',childId:S.kSelC,date:document.getElementById('kDt').value||todayStr(),subject:document.getElementById('kSj').value||'授業',text:tx,teacher:'',tags:tg2,createdAt:new Date().toISOString()});
  save();clearK();renderCh();renderEPrev();flash(document.querySelector('[onclick="saveKids()"]'),'✅ ほぞんできたよ！');
}

function clearK(){document.getElementById('kTx').value='';document.getElementById('kSj').value='';document.querySelectorAll('#kTg .tag').forEach(t=>t.classList.remove('on'));}

function saveTeacher(){
  const cid=document.getElementById('tCh').value;if(!cid){alert('子どもを選んでください');return;}
  const tx=document.getElementById('tTx').value.trim();const nt=document.getElementById('tNt').value.trim();const tg2=stags('tTg');
  if(!tx&&!nt&&!tg2.length){alert('振り返りを入力してください');return;}
  S.entries.push({id:Date.now()+'',childId:cid,date:document.getElementById('tDt').value||todayStr(),subject:document.getElementById('tSj').value||'授業',text:tx,teacher:nt,tags:tg2,createdAt:new Date().toISOString()});
  save();clearT();renderCh();renderEPrev();flash(document.querySelector('[onclick="saveTeacher()"]'),'✅ 保存しました！');
}

function clearT(){['tTx','tNt','tSj'].forEach(id=>document.getElementById(id).value='');document.querySelectorAll('#tTg .tag').forEach(t=>t.classList.remove('on'));}

function renderEPrev(){
  const cid=document.getElementById('tCh')?.value;const w=document.getElementById('ePrev');if(!w)return;
  const list=(cid?S.entries.filter(e=>e.childId===cid):S.entries).slice(-5).reverse();
  if(!list.length){w.innerHTML='';return;}
  w.innerHTML=`<div class="card"><div class="clabel">最近の振り返り</div>${list.map(e=>{const c=S.children.find(x=>x.id===e.childId);return`<div class="ei"><div class="ei-m">${c?c.emoji+' '+c.name:''} ・ ${e.date} ・ ${e.subject}</div><div class="ei-t">${e.text||''}${e.tags.length?' 【'+e.tags.join('・')+'】':''}</div></div>`;}).join('')}</div>`;
}

function dOv(e){e.preventDefault();document.getElementById('dropZ').classList.add('drag');}
function dLv(){document.getElementById('dropZ').classList.remove('drag');}
function dDp(e){e.preventDefault();dLv();hFiles(e.dataTransfer.files);}
function hFiles(files){
  Array.from(files).forEach(f=>{
    if(!f.type.startsWith('image/'))return;
    const r=new FileReader();r.onload=ev=>{S.photos.push({id:Date.now()+Math.random()+'',name:f.name,dataUrl:ev.target.result,assignedTo:[]});save();renderPGrid();renderAssign();};r.readAsDataURL(f);
  });
}
function renderPGrid(){
  const g=document.getElementById('pGrid');if(!g)return;g.innerHTML='';
  S.photos.forEach(p=>{const d=document.createElement('div');d.className='pt'+(p.assignedTo.length?' '+'':'');d.innerHTML=`<img src="${p.dataUrl}"><button class="pd" onclick="delP('${p.id}')">✕</button>`;g.appendChild(d);});
}
function delP(id){S.photos=S.photos.filter(p=>p.id!==id);save();renderPGrid();renderAssign();}
function renderAssign(){
  const w=document.getElementById('assignA');if(!w)return;
  if(!S.photos.length){w.innerHTML='<div style="text-align:center;padding:24px;color:var(--soft);font-size:.82rem">写真をアップロードしてから割り当てましょう</div>';return;}
  w.innerHTML=S.children.map(c=>{
    const asgn=S.photos.filter(p=>p.assignedTo.includes(c.id));
    return`<div class="pa"><div class="cav" style="background:${c.color};width:36px;height:36px;font-size:1rem;flex-shrink:0">${c.emoji}</div>
      <div style="flex:1"><div style="font-weight:700;font-size:.85rem">${c.name} <span class="bdg bb2">${c.grade}</span></div>
      <div style="display:flex;flex-wrap:wrap;gap:6px;margin-top:7px">
        ${asgn.map(p=>`<div style="position:relative"><img src="${p.dataUrl}" class="paimg"><button onclick="unassign('${p.id}','${c.id}')" style="position:absolute;top:-4px;right:-4px;background:var(--accent);color:white;border:none;border-radius:50%;width:17px;height:17px;font-size:.6rem;cursor:pointer">✕</button></div>`).join('')}
        <div class="pas" onclick="openPA('${c.id}')"><span style="font-size:1rem">＋</span> 追加</div>
      </div></div></div>`;
  }).join('');
}
function unassign(pid,cid){const p=S.photos.find(x=>x.id===pid);if(p)p.assignedTo=p.assignedTo.filter(x=>x!==cid);save();renderAssign();renderPGrid();}
let pmTgt=null;
function openPA(cid){
  pmTgt=cid;const c=S.children.find(x=>x.id===cid);
  document.getElementById('pmTtl').textContent=`${c?c.emoji+' '+c.name:''}の写真を選ぶ`;
  const g=document.getElementById('pmGrid');g.innerHTML='';
  S.photos.forEach(p=>{
    const d=document.createElement('div');const sel=p.assignedTo.includes(cid);
    d.style.cssText=`cursor:pointer;border-radius:7px;overflow:hidden;border:3px solid ${sel?'var(--green)':'transparent'};transition:all .15s`;
    d.innerHTML=`<img src="${p.dataUrl}" style="width:100%;aspect-ratio:1;object-fit:cover">`;
    d.onclick=()=>{const pp=S.photos.find(x=>x.id===p.id);if(pp.assignedTo.includes(cid))pp.assignedTo=pp.assignedTo.filter(x=>x!==cid);else pp.assignedTo.push(cid);d.style.borderColor=pp.assignedTo.includes(cid)?'var(--green)':'transparent';};
    g.appendChild(d);
  });
  document.getElementById('photoMod').classList.add('open');
}
function confirmPA(){save();closeM('photoMod');renderAssign();renderPGrid();}

let nlTheme='pop',nlSeason='spring',nlTone='warm';
function selTheme(t,el){
  nlTheme=t;
  document.querySelectorAll('.theme-opt').forEach(x=>x.classList.remove('sel'));el.classList.add('sel');
  document.getElementById('seasonPicker').style.display=t==='season'?'block':'none';
}
function selSeason(s,el){
  nlSeason=s;
  document.querySelectorAll('.ssbtn').forEach(x=>x.classList.remove('sel'));el.classList.add('sel');
}
function selTone(t,el){
  nlTone=t;
  ['tnW','tnF','tnS'].forEach(id=>document.getElementById(id)?.classList.remove('on'));el.classList.add('on');
}

async function genNL(){
  const btn=document.getElementById('nlBtn');
  if(!S.entries.length){alert('振り返りがまだありません');return;}
  btn.disabled=true;btn.innerHTML=`<span class="sp"></span> 生成中…`;
  const title=document.getElementById('nlT').value||'がんばりの記録';
  const dateStr=document.getElementById('nlD').value||todayStr();
  const selC=document.getElementById('nlC').value;
  const targets=selC?S.children.filter(c=>c.id===selC):S.children;
  const toneDesc={warm:'温かく親しみやすい',formal:'丁寧でフォーマルな',story:'エピソードを中心にした物語風の'}[nlTone];
  const sys=`あなたは支援学級の担任の先生です。${toneDesc}文体で、保護者向け学級通信を200〜300字で書いてください。具体的で温かく、子どもの成長が伝わる文章に。子どもの名前は「〇〇さん」で伏せてください。`;
  
  const blocks=[];
  for(const c of targets){
    const ents=S.entries.filter(e=>e.childId===c.id);if(!ents.length)continue;
    const sum=ents.map(e=>`・${e.date} ${e.subject}：${e.text}${e.teacher?'（観察：'+e.teacher+'）':''}${e.tags.length?' 【'+e.tags.join('・')+'】':''}`).join('\n');
    try{
      const text=await callAI(`${c.name}（${c.grade}）の振り返り：\n${sum}\n\n学級通信の文章を書いてください。`,sys);
      blocks.push({child:c,text,photos:S.photos.filter(p=>p.assignedTo.includes(c.id))});
    }catch(ex){blocks.push({child:c,text:'（生成エラー）',photos:[]});}
  }
  renderNLPaper(title,dateStr,blocks);
  btn.disabled=false;btn.innerHTML='✨ 学級通信を生成';
}

function renderNLPaper(title,dateStr,blocks){
  const paper=document.getElementById('nlPaper');
  const sch=S.settings.school||'';const cls=S.settings.class||'支援学級';const tch=S.settings.teacher||'';
  const th=nlTheme;
  paper.className=`nl-paper nl-${th}`;
  const seasonClass=nlSeason;
  const seasonDeco={spring:'🌸',summer:'🌊',autumn:'🍂',winter:'❄️'}[nlSeason];

  let header='';
  if(th==='pop'){
    header=`<div class="nl-header-area"><div class="nl-ttl">${title}</div><div class="nl-sub">${sch} ${cls}　${dateStr}</div></div>`;
  }else if(th==='clean'){
    header=`<div class="nl-header-area"><div class="nl-school-line">${sch} · ${cls}</div><div class="nl-ttl">${title}</div><div class="nl-date-line">${dateStr}</div></div>`;
  }else if(th==='hand'){
    header=`<div class="nl-header-area"><div class="nl-ttl">${title}</div><div class="nl-sub">${sch} ${cls}　${dateStr}</div></div>`;
  }else if(th==='season'){
    header=`<div class="nl-header-area ${seasonClass}"><div class="nl-ttl">${title}</div><div class="nl-sub">${sch} ${cls}　${dateStr}</div><div class="season-deco">${seasonDeco}</div></div>`;
  }

  const bodyBlocks=blocks.map(b=>{
    const photos=b.photos;
    let photoHtml='';
    if(photos.length===1) photoHtml=`<img class="nl-photo-1" src="${photos[0].dataUrl}" alt="">`;
    else if(photos.length>=2) photoHtml=`<div class="nl-photo-2">${photos.slice(0,2).map(p=>`<img src="${p.dataUrl}" alt="">`).join('')}</div>`;

    if(th==='pop'){
      const colors=['#ffeaa7','#fab1a0','#a29bfe','#81ecec','#fd79a8','#55efc4','#fdcb6e'];
      const bg=colors[S.children.indexOf(b.child)%colors.length];
      return`<div class="nl-child-block">
        <div class="nl-ch-head" style="background:${bg}"><div class="av" style="background:white">${b.child.emoji}</div>${b.child.name} <span class="bdg bb2" style="margin-left:4px">${b.child.grade}</span>
        <button class="btn bs bsm no-print" style="margin-left:auto;font-size:.65rem" onclick="editBlock(this)">✏️</button></div>
        ${photoHtml}<div class="nl-ch-body"><div class="txt" contenteditable="false">${b.text}</div></div></div>`;
    }else if(th==='clean'){
      return`<div class="nl-child-block">
        <div class="nl-ch-head"><div class="av" style="background:${b.child.color}">${b.child.emoji}</div><div><div class="nl-ch-name">${b.child.name}</div><div class="nl-ch-grade">${b.child.grade}</div></div>
        <button class="btn bs bsm no-print" style="margin-left:auto;font-size:.65rem" onclick="editBlock(this)">✏️</button></div>
        ${photoHtml}<div class="txt" contenteditable="false">${b.text}</div></div>`;
    }else if(th==='hand'){
      return`<div class="nl-child-block">
        <div class="nl-ch-head"><div class="av" style="background:${b.child.color}">${b.child.emoji}</div><span class="nl-ch-name">${b.child.name}</span>
        <button class="btn bs bsm no-print" style="margin-left:auto;font-size:.65rem" onclick="editBlock(this)">✏️</button></div>
        ${photoHtml}<div class="txt" contenteditable="false">${b.text}</div></div>`;
    }else{
      return`<div class="nl-child-block">
        <div class="nl-ch-head ${seasonClass}-head"><div class="av" style="background:${b.child.color}">${b.child.emoji}</div><div><div class="nl-ch-name">${b.child.name}</div></div>
        <button class="btn bs bsm no-print" style="margin-left:auto;font-size:.65rem" onclick="editBlock(this)">✏️</button></div>
        ${photoHtml?`<div class="nl-ch-body">${photoHtml}<div class="txt" contenteditable="false">${b.text}</div></div>`:`<div class="nl-ch-body"><div class="txt" contenteditable="false">${b.text}</div></div>`}</div>`;
    }
  }).join('');

  let footer='';
  if(th==='pop') footer=`<div class="nl-footer">担任：${tch}</div>`;
  else if(th==='clean') footer=`<div class="nl-footer"><span>${cls}</span><span>担任：${tch}</span></div>`;
  else if(th==='hand') footer=`<div class="nl-footer">担任：${tch}</div>`;
  else footer=`<div class="nl-footer">担任：${tch}</div>`;

  paper.innerHTML=header+`<div class="nl-body-area">${bodyBlocks}</div>`+footer;
  document.getElementById('nlPrevWrap').style.display='';
}

function editBlock(btn){
  const txt=btn.closest('.nl-child-block').querySelector('.txt');
  if(txt.contentEditable==='true'){txt.contentEditable='false';txt.style.outline='';btn.textContent='✏️';}
  else{txt.contentEditable='true';txt.style.outline='2px solid var(--accent)';txt.style.borderRadius='4px';txt.style.padding='3px';txt.focus();btn.textContent='✅';}
}

function updateStyleIndicator(){
  const w=document.getElementById('styleIndicator');if(!w)return;
  const ex=S.styleExamples.length,rl=S.styleRules.length;
  if(!ex&&!rl){w.innerHTML='<div style="font-size:.78rem;color:var(--soft);padding:8px 12px;background:var(--sun);border-radius:8px">💡 「所見スタイル」タブで書き方ルールや例文を登録すると、よりあなたらしい所見が生成されます</div>';return;}
  w.innerHTML=`<div style="font-size:.78rem;color:#27ae60;padding:8px 12px;background:var(--leaf);border-radius:8px">✅ スタイル学習済：例文 ${ex}件・ルール ${rl}件 を反映して生成します</div>`;
}

async function genReport(){
  const btn=document.getElementById('rpBtn');const out=document.getElementById('rpOut');
  const cid=document.getElementById('rpC').value;if(!cid){alert('子どもを選んでください');return;}
  const c=S.children.find(x=>x.id===cid);
  const ents=S.entries.filter(e=>e.childId===cid);
  if(!ents.length){out.innerHTML=`<div class="card" style="text-align:center;padding:32px;color:var(--soft)">📝 この子の振り返りがまだありません</div>`;return;}
  
  btn.disabled=true;btn.innerHTML=`<span class="sp"></span> 生成中…`;
  out.innerHTML=`<div class="gbar"><div class="dots"><span></span><span></span><span></span></div>所見を作成しています…</div>`;
  
  const term=document.getElementById('rpTm').value;
  const len={short:'60〜80字',medium:'100〜150字',long:'200字前後'}[document.getElementById('rpL').value];
  const foc={all:'まんべんなく',social:'社会性・友人関係',learning:'学習への取り組み',growth:'成長・変化',strength:'得意なこと・強み'}[document.getElementById('rpF').value];
  const extra=document.getElementById('rpE').value;
  const sum=ents.map(e=>`・${e.date} ${e.subject}：${e.text}${e.teacher?'（観察：'+e.teacher+'）':''}${e.tags.length?' 【'+e.tags.join('・')+'】':''}`).join('\n');

  let styleSection='';
  if(S.styleRules.length){
    styleSection+=`\n【書き方ルール】\n${S.styleRules.map((r,i)=>`${i+1}. ${r}`).join('\n')}\n`;
  }
  if(S.styleExamples.length){
    const exText=S.styleExamples.slice(-5).map(e=>`---\n${e.text}`).join('\n');
    styleSection+=`\n【文体参考例（この文体・表現を真似てください）】\n${exText}\n`;
  }

  const sys=`あなたは支援学級の担任の先生です。通知表の所見欄を書きます。です・ます調で、具体的に、保護者が子どもの成長を感じられる文章を書いてください。専門用語は使わず前向きな表現で。子どもの名前は使わず「〜できるようになりました」「〜する様子が見られました」のような書き方で。${styleSection}`;
  const prompt=`${c.name}（${c.grade}）の${term}所見。文字数：${len}。観点：${foc}。${extra?'追加：'+extra+'\n':''}振り返り：\n${sum}`;

  try{
    const [t1,t2]=await Promise.all([callAI(prompt,sys),callAI(prompt+'\n\n上とは異なる表現でもう1パターン書いてください。',sys)]);
    const rid1=Date.now()+'a',rid2=Date.now()+'b';
    S.generatedReports.push({id:rid1,childId:cid,term,text:t1,savedAsExample:false});
    S.generatedReports.push({id:rid2,childId:cid,term,text:t2,savedAsExample:false});
    save();
    out.innerHTML=`<div style="border:1px solid var(--border);border-radius:12px;overflow:hidden;margin-bottom:12px">
      <div style="padding:10px 14px;display:flex;align-items:center;gap:8px;background:var(--cream);border-bottom:1px solid var(--border)">
        <span style="background:${c.color};width:30px;height:30px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:.95rem">${c.emoji}</span>
        <strong>${c.name}</strong><span class="bdg bb2">${c.grade}</span><span class="bdg bo">${term}</span>
      </div>
      <div style="padding:16px">
        <div class="clabel">パターン A</div>
        <textarea id="rout-${rid1}" style="min-height:90px;margin-bottom:6px;background:white">${t1}</textarea>
        <div class="fr" style="margin-bottom:16px">
          <button class="btn bs bsm" onclick="cpTa('rout-${rid1}')">📋 コピー</button>
          <button class="btn bg bsm" onclick="saveAsEx('${rid1}')">⭐ いい例として保存</button>
        </div>
        <div class="clabel">パターン B</div>
        <textarea id="rout-${rid2}" style="min-height:90px;margin-bottom:6px;background:white">${t2}</textarea>
        <div class="fr">
          <button class="btn bs bsm" onclick="cpTa('rout-${rid2}')">📋 コピー</button>
          <button class="btn bg bsm" onclick="saveAsEx('${rid2}')">⭐ いい例として保存</button>
        </div>
      </div>
    </div>`;

  }catch(e){out.innerHTML=`<div class="card" style="color:var(--accent)">⚠️ エラー：${e.message}</div>`;}
  btn.disabled=false;btn.innerHTML='📝 所見を生成する';
}

function saveAsEx(rid){
  const r=S.generatedReports.find(x=>x.id===rid);if(!r)return;
  const ta=document.getElementById('rout-'+rid);
  const text=ta?ta.value:r.text;
  const c=S.children.find(x=>x.id===r.childId);
  S.styleExamples.push({id:Date.now()+'',text,grade:c?.grade||'',term:r.term,memo:'生成→手直し済',createdAt:new Date().toISOString()});
  r.savedAsExample=true;
  save();
  const btn=document.querySelector(`[onclick="saveAsEx('${rid}')"]`);
  if(btn){btn.textContent='✅ 保存済';btn.disabled=true;}
  updateStyleIndicator();
}

function cpTa(id){
  const ta=document.getElementById(id);if(!ta)return;
  navigator.clipboard.writeText(ta.value).then(()=>{
    const btn=document.querySelector(`[onclick="cpTa('${id}')"]`);
    if(btn)flash(btn,'✅ コピー済');
  });
}

function renderRules(){
  const w=document.getElementById('rulesList');if(!w)return;
  if(!S.styleRules.length){w.innerHTML='<div style="font-size:.8rem;color:var(--soft);padding:8px 0">ルールが登録されていません。下から追加してください。</div>';return;}
  w.innerHTML=S.styleRules.map((r,i)=>`<div class="rule-row"><div class="rule-num">${i+1}</div><div style="flex:1;font-size:.85rem">${r}</div><button onclick="delRule(${i})" style="background:none;border:none;color:var(--soft);cursor:pointer;font-size:.8rem">✕</button></div>`).join('');
}
function addRule(){
  const v=document.getElementById('newRule').value.trim();if(!v)return;
  S.styleRules.push(v);save();renderRules();document.getElementById('newRule').value='';
}
function delRule(i){S.styleRules.splice(i,1);save();renderRules();}
function quickRule(el){document.getElementById('newRule').value=el.textContent;document.getElementById('newRule').focus();}

function renderExamples(){
  const w=document.getElementById('exList');if(!w)return;
  if(!S.styleExamples.length){w.innerHTML='<div style="font-size:.8rem;color:var(--soft);padding:8px 0;margin-bottom:12px">登録された例はまだありません。</div>';return;}
  w.innerHTML=S.styleExamples.map((ex,i)=>`<div class="example-card"> <div class="ec-meta"> <span class="bdg bb2">${ex.grade}</span><span class="bdg bo">${ex.term}</span> ${ex.memo?`<span style="color:var(--soft)">${ex.memo}</span>`:''}</div><div class="ec-text">${ex.text}</div><button class="ec-del" onclick="delEx(${i})">✕ 削除</button></div>`).join('');
}
function addExample(){
  const tx=document.getElementById('exTx').value.trim();if(!tx){alert('所見の文章を入力してください');return;}
  S.styleExamples.push({id:Date.now()+'',text:tx,grade:document.getElementById('exGr').value,term:document.getElementById('exTm').value,memo:document.getElementById('exMemo').value,createdAt:new Date().toISOString()});
  save();renderExamples();document.getElementById('exTx').value='';document.getElementById('exMemo').value='';
  flash(document.querySelector('[onclick="addExample()"]'),'✅ 登録しました！');
  updateStyleIndicator();
}
function delEx(i){S.styleExamples.splice(i,1);save();renderExamples();updateStyleIndicator();}

function renderFeedback(){
  const w=document.getElementById('feedbackList');if(!w)return;
  const recent=S.generatedReports.slice(-10).reverse();
  if(!recent.length){w.innerHTML='<div style="font-size:.8rem;color:var(--soft)">まだ所見が生成されていません。</div>';return;}
  w.innerHTML=recent.map(r=>{
    const c=S.children.find(x=>x.id===r.childId);
    return`<div class="example-card" style="opacity:${r.savedAsExample?.7:1}"> <div class="ec-meta"><span style="font-size:1rem">${c?c.emoji:''}</span><strong>${c?c.name:''}</strong><span class="bdg bb2">${c?c.grade:''}</span><span class="bdg bo">${r.term}</span>${r.savedAsExample?'<span class="bdg bg2">保存済</span>':''}</div> <div class="ec-text" style="margin-bottom:8px">${r.text.slice(0,80)}${r.text.length>80?'…':''}</div> ${!r.savedAsExample?`<button class="btn bg bsm" onclick="saveAsEx('${r.id}')">⭐ いい例として保存</button>`:''} </div>`;
  }).join('');
}

function openAddChild(){
  const eg=document.getElementById('emG');eg.innerHTML='';
  EMOJIS.forEach(e=>{const d=document.createElement('div');d.className='eo'+(e===S.selEmoji?' sel':'');d.textContent=e;d.onclick=()=>{S.selEmoji=e;eg.querySelectorAll('.eo').forEach(x=>x.classList.remove('sel'));d.classList.add('sel');};eg.appendChild(d);});
  const cg=document.getElementById('coG');cg.innerHTML='';
  COLS.forEach(c=>{const d=document.createElement('div');d.className='co2'+(c===S.selCol?' sel':'');d.style.background=c;d.onclick=()=>{S.selCol=c;cg.querySelectorAll('.co2').forEach(x=>x.classList.remove('sel'));d.classList.add('sel');};cg.appendChild(d);});
  document.getElementById('ncN').value='';
  document.getElementById('addChildMod').classList.add('open');
}
function saveChild(){
  const name=document.getElementById('ncN').value.trim();if(!name){alert('名前を入力してください');return;}
  S.children.push({id:Date.now()+'',name,grade:document.getElementById('ncG').value,emoji:S.selEmoji,color:S.selCol});
  save();renderAll();closeM('addChildMod');
}

function applySettings(){
  document.getElementById('sSchool').value=S.settings.school||'';
  document.getElementById('sClass').value=S.settings.class||'';
  document.getElementById('sTeacher').value=S.settings.teacher||'';
}
function saveSets(){S.settings.school=document.getElementById('sSchool').value;S.settings.class=document.getElementById('sClass').value;S.settings.teacher=document.getElementById('sTeacher').value;save();}
function expData(){const b=new Blob([JSON.stringify(S,null,2)],{type:'application/json'});const a=document.createElement('a');a.href=URL.createObjectURL(b);a.download=`ganbarino_${todayStr()}.json`;a.click();}
function impData(input){const f=input.files[0];if(!f)return;const r=new FileReader();r.onload=e=>{try{Object.assign(S,JSON.parse(e.target.result));save();renderAll();applySettings();alert('インポートしました！');}catch{alert('ファイルが正しくありません');}};r.readAsText(f);}
function resetAll(){if(!confirm('全データを削除しますか？'))return;S.children=DEF_CH.map(c=>({...c}));S.entries=[];S.photos=[];S.styleRules=[];S.styleExamples=[];S.generatedReports=[];save();renderAll();alert('リセットしました。');}

// 📌 ここをダミー用（テスト用）に書き換えました。GAS連携の際に本物のAI呼び出しに戻します！
async function callAI(prompt,sys){
  return new Promise(resolve => {
    setTimeout(() => {
      resolve("【ここにAIが生成した文章が入ります】\n現在は動作テストモードです。今後のGAS連携によって、ここに本物のAIから所見や学級通信の文章が届くようになります！");
    }, 1500); // 1.5秒待ってから表示する演出
  });
}

function todayStr(){const d=new Date(),w=['日','月','火','水','木','金','土'];return`${d.getMonth()+1}月${d.getDate()}日（${w[d.getDay()]}）`;}
function flash(btn,msg){if(!btn)return;const o=btn.innerHTML;btn.innerHTML=msg;setTimeout(()=>btn.innerHTML=o,2000);}
function closeM(id){document.getElementById(id).classList.remove('open');}

load();
const ph=todayStr();
['tDt','kDt'].forEach(id=>{const el=document.getElementById(id);if(el)el.placeholder=ph;});
document.getElementById('nlD').placeholder=ph;
</script>

</body>
</html>
