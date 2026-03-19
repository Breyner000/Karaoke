<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>🎤 KARAOKE</title>
<link href="https://fonts.googleapis.com/css2?family=Abril+Fatface&family=Space+Mono:wght@400;700&family=Oswald:wght@300;400;700&family=Playfair+Display:ital,wght@0,700;1,400&family=Rajdhani:wght@400;600;700&family=Permanent+Marker&family=Quicksand:wght@400;600;700&display=swap" rel="stylesheet">
<style>
/* ═══════════════════════════════════════════
   RESET & BASE
═══════════════════════════════════════════ */
*{box-sizing:border-box;margin:0;padding:0}
html,body{min-height:100vh;overflow-x:hidden;transition:background .6s,color .6s}

/* ═══════════════════════════════════════════
   THEME VARIABLES
═══════════════════════════════════════════ */

/* THEME 1: NEON 90s */
body.t-neon{
  --bg:#07000a;--panel:#100018;--input:#1c0028;
  --accent:#ff00cc;--accent2:#00ffee;--accent3:#ffdd00;
  --text:#fff;--text2:#ffffff88;--text3:#ffffff33;
  --border:#ff00cc30;--border2:#ff00cc66;
  --lyr-active:#fff;--lyr-past:#ffffff22;--lyr-near:#ffffff55;
  --font-title:'Abril Fatface',cursive;--font-body:'Space Mono',monospace;--font-ui:'Oswald',sans-serif;
  background:var(--bg);color:var(--text);font-family:var(--font-body);
}
body.t-neon .header h1{background:linear-gradient(160deg,#fff 0%,#ffdd00 35%,#ff6600 65%,#ff00cc 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;filter:drop-shadow(0 0 18px #ff00cc66)}
body.t-neon .neon-bar{height:1.5px;background:linear-gradient(90deg,transparent,#ff00cc,#00ffee,#ffdd00,transparent);animation:npulse 2.5s ease-in-out infinite}
body.t-neon::after{content:'';position:fixed;inset:0;background:repeating-linear-gradient(0deg,transparent,transparent 3px,rgba(0,0,0,.12) 3px,rgba(0,0,0,.12) 4px);pointer-events:none;z-index:9999}
body.t-neon .vinyl{background:radial-gradient(circle at 50%,#0d0010 0%,#0d0010 11%,#1a1a1a 11.5%,#222 14%,#1a1a1a 14.5%,#0d0010 18%,transparent 18%),repeating-conic-gradient(#0d0010 0deg 1.5deg,#1e0030 1.5deg 3deg)}
body.t-neon .lyric-line.is-active{text-shadow:0 0 40px rgba(255,255,255,.2)}

/* THEME 2: VAPORWAVE */
body.t-vapor{
  --bg:#1a0533;--panel:#240a42;--input:#2e0f52;
  --accent:#ff71ce;--accent2:#01cdfe;--accent3:#fffb96;
  --text:#ffe4ff;--text2:#ff71ce99;--text3:#ff71ce33;
  --border:#ff71ce25;--border2:#ff71ce55;
  --lyr-active:#fffb96;--lyr-past:#ff71ce22;--lyr-near:#ff71ce77;
  --font-title:'Playfair Display',serif;--font-body:'Quicksand',sans-serif;--font-ui:'Quicksand',sans-serif;
  background:var(--bg);color:var(--text);font-family:var(--font-body);
}
body.t-vapor .header h1{background:linear-gradient(135deg,#ff71ce,#b967ff,#01cdfe,#fffb96);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
body.t-vapor .neon-bar{height:1px;background:linear-gradient(90deg,transparent,#ff71ce,#b967ff,#01cdfe,transparent);opacity:.7}
body.t-vapor .vinyl{background:radial-gradient(circle at 50%,#200040 0%,#200040 12%,#3a006f 12.5%,#4a0090 16%,#3a006f 16.5%,#200040 20%,transparent 20%),repeating-conic-gradient(#200040 0deg 2deg,#350060 2deg 4deg)}
body.t-vapor .lyric-line.is-active{text-shadow:0 0 30px #fffb9666,0 0 60px #ff71ce33}

/* THEME 3: DARK LUXURY */
body.t-luxury{
  --bg:#0a0a08;--panel:#111110;--input:#181816;
  --accent:#c9a84c;--accent2:#e8d5a3;--accent3:#fff8e7;
  --text:#f5f0e8;--text2:#c9a84c99;--text3:#c9a84c33;
  --border:#c9a84c20;--border2:#c9a84c50;
  --lyr-active:#fff8e7;--lyr-past:#c9a84c22;--lyr-near:#c9a84c66;
  --font-title:'Playfair Display',serif;--font-body:'Raleway',sans-serif;--font-ui:'Oswald',sans-serif;
  background:var(--bg);color:var(--text);font-family:'Oswald',sans-serif;
}
body.t-luxury .header h1{background:linear-gradient(180deg,#fff8e7 0%,#c9a84c 50%,#8b6914 100%);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;font-family:'Playfair Display',serif;letter-spacing:6px}
body.t-luxury .neon-bar{height:1px;background:linear-gradient(90deg,transparent,#c9a84c,#fff8e7,#c9a84c,transparent)}
body.t-luxury .vinyl{background:radial-gradient(circle at 50%,#0a0a08 0%,#0a0a08 11%,#1a1a18 11.5%,#252520 14%,#1a1a18 14.5%,#0a0a08 18%,transparent 18%),repeating-conic-gradient(#0a0a08 0deg 1.5deg,#1c1c18 1.5deg 3deg)}
body.t-luxury .lyric-line.is-active{text-shadow:0 0 30px #c9a84c44;letter-spacing:2px}

/* THEME 4: CYBERPUNK */
body.t-cyber{
  --bg:#000;--panel:#080010;--input:#0c0018;
  --accent:#00ff41;--accent2:#ff003c;--accent3:#ffff00;
  --text:#00ff41;--text2:#00ff4188;--text3:#00ff4122;
  --border:#00ff4120;--border2:#00ff4155;
  --lyr-active:#ffff00;--lyr-past:#00ff4122;--lyr-near:#00ff4166;
  --font-title:'Rajdhani',sans-serif;--font-body:'Rajdhani',sans-serif;--font-ui:'Rajdhani',sans-serif;
  background:var(--bg);color:var(--text);font-family:'Rajdhani',sans-serif;
}
body.t-cyber .header h1{color:#00ff41;font-family:'Rajdhani',sans-serif;font-weight:700;letter-spacing:8px;text-shadow:0 0 20px #00ff41,0 0 40px #00ff4155;-webkit-text-fill-color:#00ff41}
body.t-cyber .neon-bar{height:1px;background:linear-gradient(90deg,transparent,#00ff41,#ff003c,#00ff41,transparent);animation:npulse 1s ease-in-out infinite}
body.t-cyber::after{content:'';position:fixed;inset:0;background:repeating-linear-gradient(0deg,transparent,transparent 2px,rgba(0,255,65,.03) 2px,rgba(0,255,65,.03) 3px);pointer-events:none;z-index:9999}
body.t-cyber .vinyl{background:radial-gradient(circle at 50%,#000 0%,#000 11%,#001400 11.5%,#002800 14%,#001400 14.5%,#000 18%,transparent 18%),repeating-conic-gradient(#000 0deg 1.5deg,#001a00 1.5deg 3deg)}
body.t-cyber .lyric-line.is-active{text-shadow:0 0 20px #ffff00,0 0 40px #ffff0066;color:#ffff00}
body.t-cyber .app{border-color:#00ff4133}
body.t-cyber .left-col{border-right-color:#00ff4133}
body.t-cyber .inp{border-color:#00ff4133;color:#00ff41}

/* THEME 5: PASTEL POP */
body.t-pastel{
  --bg:#fff5fc;--panel:#fff0fb;--input:#ffe8f8;
  --accent:#ff6eb4;--accent2:#6ec6ff;--accent3:#ffd166;
  --text:#3d1a2e;--text2:#ff6eb499;--text3:#ff6eb433;
  --border:#ff6eb420;--border2:#ff6eb455;
  --lyr-active:#3d1a2e;--lyr-past:#ff6eb422;--lyr-near:#ff6eb477;
  --font-title:'Permanent Marker',cursive;--font-body:'Quicksand',sans-serif;--font-ui:'Quicksand',sans-serif;
  background:var(--bg);color:var(--text);font-family:'Quicksand',sans-serif;
}
body.t-pastel .header h1{background:linear-gradient(135deg,#ff6eb4,#c77dff,#6ec6ff,#ffd166);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;font-family:'Permanent Marker',cursive;letter-spacing:2px}
body.t-pastel .neon-bar{height:2px;background:linear-gradient(90deg,transparent,#ff6eb4,#c77dff,#6ec6ff,transparent)}
body.t-pastel .vinyl{background:radial-gradient(circle at 50%,#f8e0f5 0%,#f8e0f5 11%,#e8c8ee 11.5%,#d4a8e4 14%,#e8c8ee 14.5%,#f8e0f5 18%,transparent 18%),repeating-conic-gradient(#f8e0f5 0deg 2deg,#e8c8f0 2deg 4deg)}
body.t-pastel .lyric-line.is-active{color:#3d1a2e;text-shadow:2px 2px 0 #ff6eb433}
body.t-pastel .app{background:#fff0fb;border-color:#ff6eb430}
body.t-pastel .right-col{background:#fff8fe}
body.t-pastel .lyric-line{color:#ff6eb422}
body.t-pastel .lyric-line.is-past{color:#ff6eb433}
body.t-pastel .lyric-line.is-near{color:#ff6eb488}

/* THEME 6: MIDNIGHT JAZZ */
body.t-jazz{
  --bg:#0c0e1a;--panel:#111422;--input:#181c2e;
  --accent:#e8a020;--accent2:#4ecdc4;--accent3:#fff;
  --text:#f0ead0;--text2:#e8a02099;--text3:#e8a02033;
  --border:#e8a02020;--border2:#e8a02050;
  --lyr-active:#fff;--lyr-past:#e8a02022;--lyr-near:#e8a02066;
  --font-title:'Playfair Display',serif;--font-body:'Space Mono',monospace;--font-ui:'Oswald',sans-serif;
  background:var(--bg);color:var(--text);font-family:'Space Mono',monospace;
}
body.t-jazz .header h1{font-family:'Playfair Display',serif;font-style:italic;background:linear-gradient(135deg,#f0ead0,#e8a020,#4ecdc4);-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text;letter-spacing:2px}
body.t-jazz .neon-bar{height:1px;background:linear-gradient(90deg,transparent,#e8a020,#fff,#4ecdc4,transparent)}
body.t-jazz .vinyl{background:radial-gradient(circle at 50%,#0c0e1a 0%,#0c0e1a 11%,#1c1e2a 11.5%,#262834 14%,#1c1e2a 14.5%,#0c0e1a 18%,transparent 18%),repeating-conic-gradient(#0c0e1a 0deg 1.5deg,#1a1c28 1.5deg 3deg)}
body.t-jazz .lyric-line.is-active{text-shadow:0 0 30px rgba(232,160,32,.3)}

/* ═══════════════════════════════════════════
   ANIMATIONS
═══════════════════════════════════════════ */
@keyframes spin{from{transform:rotate(0deg)}to{transform:rotate(360deg)}}
@keyframes npulse{0%,100%{opacity:1}50%{opacity:.3}}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.15}}
@keyframes db{0%,100%{transform:translateY(0);opacity:.25}50%{transform:translateY(-7px);opacity:1}}
@keyframes slideIn{from{opacity:0;transform:translateY(-8px)}to{opacity:1;transform:translateY(0)}}

/* ═══════════════════════════════════════════
   THEME SWITCHER
═══════════════════════════════════════════ */
.theme-bar{display:flex;align-items:center;justify-content:center;gap:8px;padding:8px 16px;flex-wrap:wrap}
.theme-btn{border:1.5px solid var(--border2);background:transparent;border-radius:20px;padding:5px 14px;font-size:10px;letter-spacing:2px;cursor:pointer;transition:all .25s;font-family:var(--font-ui,'Oswald',sans-serif);text-transform:uppercase;color:var(--text2);white-space:nowrap}
.theme-btn:hover,.theme-btn.active{background:var(--accent);color:var(--bg);border-color:var(--accent);box-shadow:0 0 12px color-mix(in srgb,var(--accent) 40%,transparent)}
.theme-btn span{margin-right:5px}

/* ═══════════════════════════════════════════
   HEADER
═══════════════════════════════════════════ */
.header{text-align:center;padding:18px 16px 8px}
.header h1{font-family:var(--font-title,'Abril Fatface',cursive);font-size:clamp(28px,6vw,54px);letter-spacing:3px;line-height:1.1}
.header-sub{font-family:var(--font-ui,'Oswald',sans-serif);font-size:10px;letter-spacing:6px;color:var(--accent2);margin-top:4px;text-transform:uppercase;opacity:.7}
.neon-bar{margin:10px 0 0}

/* ═══════════════════════════════════════════
   APP LAYOUT
═══════════════════════════════════════════ */
.app{display:grid;grid-template-columns:350px 1fr;height:calc(100vh - 140px);max-width:1200px;margin:0 auto;border:1px solid var(--border);border-radius:6px;overflow:hidden;transition:border-color .6s}
@media(max-width:760px){.app{grid-template-columns:1fr;height:auto;min-height:100vh}}

/* ═══════════════════════════════════════════
   LEFT COLUMN
═══════════════════════════════════════════ */
.left-col{background:var(--panel);border-right:1px solid var(--border);display:flex;flex-direction:column;overflow-y:auto;overflow-x:hidden;transition:background .6s,border-color .6s;scrollbar-width:thin;scrollbar-color:color-mix(in srgb,var(--accent) 20%,transparent) transparent}
.left-col::-webkit-scrollbar{width:2px}
.left-col::-webkit-scrollbar-thumb{background:var(--border2);border-radius:2px}

/* DISCO SECTION */
.disco-section{padding:22px 18px 14px;display:flex;flex-direction:column;align-items:center;border-bottom:1px solid var(--border);flex-shrink:0;transition:border-color .6s}
.vinyl-wrap{position:relative;width:160px;height:160px;margin-bottom:14px}
.vinyl{width:160px;height:160px;border-radius:50%;position:relative;animation:spin 4s linear infinite;animation-play-state:paused;border:1px solid var(--border2);transition:border-color .6s,box-shadow .6s;box-shadow:0 0 24px color-mix(in srgb,var(--accent) 15%,transparent),0 0 60px #00000077}
.vinyl.playing{animation-play-state:running}
.vinyl::after{content:'';position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:8px;height:8px;border-radius:50%;background:var(--accent);box-shadow:0 0 8px var(--accent);z-index:4}
.vinyl-center{position:absolute;top:50%;left:50%;transform:translate(-50%,-50%);width:50px;height:50px;border-radius:50%;background:var(--panel);border:2px solid var(--border2);display:flex;align-items:center;justify-content:center;font-size:18px;z-index:3;transition:all .6s}
.vinyl-shine{position:absolute;top:8%;left:18%;width:28%;height:36%;border-radius:50%;background:linear-gradient(135deg,rgba(255,255,255,.09) 0%,transparent 60%);pointer-events:none;z-index:5}

/* NEEDLE */
.needle-wrap{position:absolute;top:-6px;right:-10px;width:52px;height:72px;transform-origin:5px 5px;transform:rotate(-22deg);transition:transform .9s cubic-bezier(.34,1.4,.64,1);z-index:10;pointer-events:none}
.needle-wrap.playing{transform:rotate(-36deg)}
.n-pivot{position:absolute;top:0;left:0;width:11px;height:11px;border-radius:50%;background:radial-gradient(circle,#ccc,#666);border:1px solid #999}
.n-arm{position:absolute;top:5px;left:3.5px;width:2px;height:60px;background:linear-gradient(180deg,#aaa,#555);border-radius:1px;transform-origin:top;transform:rotate(4deg)}
.n-head{position:absolute;bottom:2px;left:.5px;width:8px;height:5px;background:#888;border-radius:1px}

.song-now{text-align:center;max-width:260px;padding:0 6px}
.song-now-name{font-family:var(--font-title,'Abril Fatface',cursive);font-size:clamp(13px,2vw,17px);color:var(--accent3);letter-spacing:.5px;margin-bottom:3px;line-height:1.3;transition:color .6s}
.song-now-artist{font-family:var(--font-ui,'Oswald',sans-serif);font-size:10px;color:var(--accent2);letter-spacing:4px;text-transform:uppercase;transition:color .6s}
.song-now-idle{font-family:var(--font-ui,'Oswald',sans-serif);font-size:10px;color:var(--text3);letter-spacing:2px;text-transform:uppercase;animation:npulse 3s ease-in-out infinite}

/* PROGRESS */
.prog-wrap{padding:8px 18px 0;flex-shrink:0}
.prog-bg{height:2px;background:var(--border);border-radius:2px;cursor:pointer;position:relative}
.prog-fill{height:100%;background:linear-gradient(90deg,var(--accent),var(--accent2));border-radius:2px;width:0%;transition:width .4s linear;box-shadow:0 0 5px var(--accent2)}
.prog-times{display:flex;justify-content:space-between;font-size:8px;color:var(--text3);margin-top:3px;font-family:var(--font-body,'Space Mono',monospace)}

/* CONTROLS */
.controls{display:flex;align-items:center;justify-content:center;gap:9px;padding:10px 18px;border-bottom:1px solid var(--border);flex-shrink:0;transition:border-color .6s}
.cbtn{background:none;border:1.5px solid var(--border2);color:var(--accent);width:36px;height:36px;border-radius:50%;cursor:pointer;font-size:13px;transition:all .2s;display:flex;align-items:center;justify-content:center}
.cbtn:hover{background:color-mix(in srgb,var(--accent) 15%,transparent);box-shadow:0 0 12px color-mix(in srgb,var(--accent) 40%,transparent);transform:scale(1.08)}
.cbtn.big{width:48px;height:48px;font-size:18px;border-color:var(--accent2);color:var(--accent2)}
.cbtn.big:hover{background:color-mix(in srgb,var(--accent2) 15%,transparent);box-shadow:0 0 16px color-mix(in srgb,var(--accent2) 40%,transparent)}
.vol-row{display:flex;align-items:center;gap:5px;margin-left:4px}
.vol-row span{font-size:8px;color:var(--text2);letter-spacing:2px;font-family:var(--font-ui,'Oswald',sans-serif);text-transform:uppercase}
input[type=range].vol{-webkit-appearance:none;width:60px;height:2px;background:var(--border);border-radius:2px;outline:none}
input[type=range].vol::-webkit-slider-thumb{-webkit-appearance:none;width:10px;height:10px;border-radius:50%;background:var(--accent);cursor:pointer}

/* ADD SECTION */
.add-section{padding:14px 16px;border-bottom:1px solid var(--border);flex-shrink:0;transition:border-color .6s}
.sec-label{font-family:var(--font-ui,'Oswald',sans-serif);font-size:9px;letter-spacing:4px;color:var(--accent);text-transform:uppercase;margin-bottom:11px;display:flex;align-items:center;gap:7px}
.sec-label::after{content:'';flex:1;height:1px;background:var(--border)}
.inp-row{margin-bottom:8px}
.inp-lbl{font-size:8px;color:var(--text2);letter-spacing:2px;display:block;margin-bottom:4px;font-family:var(--font-ui,'Oswald',sans-serif);text-transform:uppercase;opacity:.6}
.inp{width:100%;background:var(--input);border:1px solid var(--border2);color:var(--accent3);font-family:var(--font-body,'Space Mono',monospace);font-size:11px;padding:7px 9px;border-radius:3px;outline:none;transition:border-color .2s,box-shadow .2s,background .6s}
.inp:focus{border-color:var(--accent);box-shadow:0 0 8px color-mix(in srgb,var(--accent) 20%,transparent)}
.inp::placeholder{color:var(--text3)}
.btn-srch{width:100%;padding:8px;background:none;border:1.5px solid var(--accent);color:var(--accent3);font-family:var(--font-ui,'Oswald',sans-serif);font-size:11px;letter-spacing:3px;cursor:pointer;border-radius:3px;transition:all .2s;text-transform:uppercase;margin-top:2px}
.btn-srch:hover{background:color-mix(in srgb,var(--accent) 15%,transparent);box-shadow:0 0 12px color-mix(in srgb,var(--accent) 30%,transparent)}
.btn-srch:disabled{opacity:.35;cursor:not-allowed}

/* RESULTS */
.results-box{margin-top:8px;display:none;max-height:160px;overflow-y:auto;scrollbar-width:thin;scrollbar-color:var(--border2) transparent;animation:slideIn .2s ease}
.results-box::-webkit-scrollbar{width:2px}
.results-box::-webkit-scrollbar-thumb{background:var(--border2);border-radius:2px}
.r-item{display:flex;align-items:center;gap:7px;padding:6px 7px;border:1px solid transparent;border-radius:3px;cursor:pointer;transition:all .2s;margin-bottom:3px}
.r-item:hover{border-color:var(--border2);background:var(--input)}
.r-thumb{width:40px;height:27px;object-fit:cover;border-radius:2px;flex-shrink:0;background:var(--border)}
.r-info{flex:1;min-width:0}
.r-title{font-size:10px;color:var(--accent3);white-space:nowrap;overflow:hidden;text-overflow:ellipsis;font-family:var(--font-ui,'Oswald',sans-serif)}
.r-ch{font-size:8px;color:var(--text3)}
.r-add{font-size:18px;color:var(--accent2);background:none;border:none;cursor:pointer;transition:transform .2s;flex-shrink:0;line-height:1}
.r-add:hover{transform:scale(1.3);color:var(--accent3)}

/* QUEUE */
.queue-section{padding:12px 16px 16px;flex:1}
.queue-list{max-height:160px;overflow-y:auto;scrollbar-width:thin;scrollbar-color:var(--border) transparent}
.queue-list::-webkit-scrollbar{width:2px}
.queue-list::-webkit-scrollbar-thumb{background:var(--border);border-radius:2px}
.q-empty{text-align:center;color:var(--text3);font-size:9px;font-family:var(--font-ui,'Oswald',sans-serif);letter-spacing:2px;padding:16px 0;text-transform:uppercase}
.q-item{display:flex;align-items:center;gap:7px;padding:6px 8px;border:1px solid transparent;border-radius:3px;margin-bottom:3px;transition:all .2s;cursor:pointer}
.q-item:hover:not(.q-active){border-color:var(--border);background:var(--input)}
.q-active{border-color:var(--accent);background:color-mix(in srgb,var(--accent) 8%,var(--panel))}
.q-num{font-size:8px;color:var(--text3);min-width:14px;font-family:var(--font-ui,'Oswald',sans-serif)}
.q-active .q-num{color:var(--accent);animation:blink 1s step-end infinite}
.q-info{flex:1;min-width:0}
.q-name{font-size:10px;color:var(--text2);font-family:var(--font-ui,'Oswald',sans-serif);white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.q-active .q-name{color:var(--accent3)}
.q-art{font-size:8px;color:var(--text3);white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.q-del{font-size:10px;color:var(--text3);background:none;border:none;cursor:pointer;transition:color .2s;flex-shrink:0}
.q-del:hover{color:var(--accent)}

/* ═══════════════════════════════════════════
   RIGHT COLUMN — LYRICS
═══════════════════════════════════════════ */
.right-col{background:color-mix(in srgb,var(--bg) 95%,var(--panel) 5%);display:flex;flex-direction:column;position:relative;overflow:hidden;transition:background .6s}
.right-col::before{content:'';position:absolute;top:0;left:0;right:0;height:120px;background:linear-gradient(180deg,color-mix(in srgb,var(--bg) 95%,transparent) 30%,transparent 100%);z-index:5;pointer-events:none;transition:background .6s}
.right-col::after{content:'';position:absolute;bottom:0;left:0;right:0;height:120px;background:linear-gradient(0deg,color-mix(in srgb,var(--bg) 95%,transparent) 30%,transparent 100%);z-index:5;pointer-events:none;transition:background .6s}

.lyrics-header{position:absolute;top:0;left:0;right:0;padding:22px 34px 0;z-index:6}
.lh-song{font-family:var(--font-title,'Abril Fatface',cursive);font-size:clamp(15px,2.5vw,22px);color:var(--accent3);letter-spacing:.5px;margin-bottom:2px;transition:color .6s}
.lh-artist{font-family:var(--font-ui,'Oswald',sans-serif);font-size:10px;color:var(--text2);letter-spacing:4px;text-transform:uppercase;transition:color .6s}

.lyrics-scroll{flex:1;overflow-y:auto;padding:0 34px;scroll-behavior:smooth;scrollbar-width:none;position:relative;z-index:2}
.lyrics-scroll::-webkit-scrollbar{display:none}

.lyrics-idle{display:flex;flex-direction:column;align-items:center;justify-content:center;height:100%;gap:14px;padding:40px;min-height:300px}
.idle-disc{width:70px;height:70px;border-radius:50%;background:var(--border);border:2px solid var(--border2);display:flex;align-items:center;justify-content:center;font-size:26px;animation:spin 8s linear infinite paused;transition:background .6s,border-color .6s}
.idle-disc.playing{animation-play-state:running}
.idle-txt{font-family:var(--font-ui,'Oswald',sans-serif);font-size:11px;color:var(--text3);letter-spacing:3px;text-transform:uppercase;text-align:center;animation:npulse 3s ease-in-out infinite;line-height:1.9}

/* LYRIC LINES */
.lyric-line{
  font-family:var(--font-ui,'Oswald',sans-serif);
  font-weight:700;
  font-size:clamp(15px,3vw,28px);
  line-height:1.55;
  color:var(--lyr-past);
  transition:color .5s ease,font-size .4s ease;
  cursor:pointer;
  padding:2px 0;
  user-select:none;
}
.lyric-line:hover{opacity:.8}
.lyric-line.is-past{color:var(--lyr-past)}
.lyric-line.is-near{color:var(--lyr-near);font-size:clamp(16px,3.2vw,30px)}
.lyric-line.is-active{color:var(--lyr-active);font-size:clamp(20px,4vw,38px)}
.lyric-line.is-next{color:var(--lyr-near);opacity:.6}

.lyr-loading{display:flex;flex-direction:column;align-items:center;justify-content:center;height:100%;gap:10px;min-height:200px}
.lyr-loading-txt{font-family:var(--font-ui,'Oswald',sans-serif);font-size:11px;color:var(--text3);letter-spacing:3px;text-transform:uppercase;text-align:center;line-height:1.9}
.dots span{display:inline-block;width:5px;height:5px;border-radius:50%;background:var(--accent2);margin:0 3px;animation:db 1s ease-in-out infinite}
.dots span:nth-child(2){animation-delay:.2s}
.dots span:nth-child(3){animation-delay:.4s}

/* TOAST */
.toast{position:fixed;bottom:18px;left:50%;transform:translateX(-50%);background:var(--panel);border:1px solid var(--border2);color:var(--accent2);font-family:var(--font-ui,'Oswald',sans-serif);font-size:10px;letter-spacing:3px;text-transform:uppercase;padding:7px 18px;border-radius:20px;z-index:10000;opacity:0;transition:opacity .35s;pointer-events:none;white-space:nowrap;box-shadow:0 4px 20px #00000055}
.toast.show{opacity:1}

/* YT CONTAINER — visible pero oculto bajo el layout */
#yt-container{position:fixed;bottom:0;left:0;width:320px;height:180px;z-index:-1;opacity:.01;pointer-events:none}
#yt-container iframe{width:100%;height:100%;border:none}
</style>
</head>
<body class="t-neon">

<!-- YouTube iframe container — necesita ser visible (aunque sea .01 opacidad) para que YT permita audio -->
<div id="yt-container"><div id="yt-player"></div></div>

<!-- HEADER -->
<div class="header">
  <h1 id="appTitle">KARAOKE</h1>
  <p class="header-sub" id="appSub">Noche de Karaoke ✦ Elige tu estilo</p>
  <div class="neon-bar"></div>
</div>

<!-- THEME SWITCHER -->
<div class="theme-bar">
  <button class="theme-btn active" data-theme="t-neon">  <span>💜</span>Neon 90s</button>
  <button class="theme-btn" data-theme="t-vapor"><span>🌸</span>Vaporwave</button>
  <button class="theme-btn" data-theme="t-luxury"><span>✨</span>Dark Luxury</button>
  <button class="theme-btn" data-theme="t-cyber"><span>💚</span>Cyberpunk</button>
  <button class="theme-btn" data-theme="t-pastel"><span>🍭</span>Pastel Pop</button>
  <button class="theme-btn" data-theme="t-jazz"><span>🎷</span>Midnight Jazz</button>
</div>

<!-- APP -->
<div class="app">

  <!-- LEFT -->
  <div class="left-col">
    <div class="disco-section">
      <div class="vinyl-wrap">
        <div class="vinyl" id="vinyl">
          <div class="vinyl-shine"></div>
          <div class="vinyl-center" id="vinylArt">🎵</div>
        </div>
        <div class="needle-wrap" id="needle">
          <div class="n-pivot"></div>
          <div class="n-arm"></div>
          <div class="n-head"></div>
        </div>
      </div>
      <div class="song-now" id="songNow">
        <div class="song-now-idle">Sin canción · Agrega una</div>
      </div>
    </div>

    <div class="prog-wrap" id="progWrap" style="display:none">
      <div class="prog-bg" id="progBg"><div class="prog-fill" id="progFill"></div></div>
      <div class="prog-times"><span id="tEl">0:00</span><span id="tTo">0:00</span></div>
    </div>

    <div class="controls">
      <button class="cbtn" id="btnPrev">⏮</button>
      <button class="cbtn big" id="btnPlay">▶</button>
      <button class="cbtn" id="btnNext">⏭</button>
      <div class="vol-row">
        <span>Vol</span>
        <input type="range" class="vol" id="volSlider" min="0" max="100" value="80">
      </div>
    </div>

    <div class="add-section">
      <div class="sec-label">Agregar canción</div>
      <div class="inp-row">
        <label class="inp-lbl">Título</label>
        <input class="inp" id="inpSong" placeholder="Ej: Shape of You" autocomplete="off">
      </div>
      <div class="inp-row">
        <label class="inp-lbl">Artista</label>
        <input class="inp" id="inpArtist" placeholder="Ej: Ed Sheeran" autocomplete="off">
      </div>
      <button class="btn-srch" id="btnSearch">🔍 Buscar en YouTube</button>
      <div class="results-box" id="resultsBox"></div>
    </div>

    <div class="queue-section">
      <div class="sec-label">Fila</div>
      <div class="queue-list" id="queueList">
        <div class="q-empty" id="qEmpty">La fila está vacía</div>
      </div>
    </div>
  </div>

  <!-- RIGHT — LYRICS -->
  <div class="right-col">
    <div class="lyrics-header" id="lyricsHeader" style="display:none">
      <div class="lh-song" id="lhSong"></div>
      <div class="lh-artist" id="lhArtist"></div>
    </div>
    <div class="lyrics-scroll" id="lyricsScroll">
      <div class="lyrics-idle" id="lyricsIdle">
        <div class="idle-disc" id="idleDisc">🎵</div>
        <div class="idle-txt">Agrega una canción<br>para ver la letra aquí</div>
      </div>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script src="https://www.youtube.com/iframe_api"></script>
<script>
/* ══════════════════════════════════════
   THEME SWITCHER
══════════════════════════════════════ */
const themes = {
  't-neon':   {title:'KARAOKE ROCOLA', sub:'Noche de Karaoke ✦ Neon 90s'},
  't-vapor':  {title:'KARAOKE ♡', sub:'A E S T H E T I C ✦ Vaporwave'},
  't-luxury': {title:'KARAOKE', sub:'Black Tie Edition ✦ Luxury'},
  't-cyber':  {title:'K4R4OKE.EXE', sub:'SYSTEM ONLINE ✦ CYBERPUNK'},
  't-pastel': {title:'Karaoke!', sub:'Buena Vibra ✦ Pastel Pop 🌈'},
  't-jazz':   {title:'Karaoke Lounge', sub:'Late Night Jazz ✦ Midnight Sessions'},
};

document.querySelectorAll('.theme-btn').forEach(btn=>{
  btn.addEventListener('click',()=>{
    document.querySelectorAll('.theme-btn').forEach(b=>b.classList.remove('active'));
    btn.classList.add('active');
    const t=btn.dataset.theme;
    document.body.className=t;
    document.getElementById('appTitle').textContent=themes[t].title;
    document.getElementById('appSub').textContent=themes[t].sub;
  });
});

/* ══════════════════════════════════════
   STATE
══════════════════════════════════════ */
let queue=[], curIdx=-1;
let ytPlayer=null, ytReady=false, isPlaying=false;
let lyrics=[], lastActiveIdx=-1;
let syncInt=null, progInt=null;

/* ══════════════════════════════════════
   YOUTUBE PLAYER — con dimensiones reales para que YT permita audio
══════════════════════════════════════ */
window.onYouTubeIframeAPIReady=()=>{
  ytReady=true;
  ytPlayer=new YT.Player('yt-player',{
    height:'180',
    width:'320',
    playerVars:{
      autoplay:1,
      controls:0,
      disablekb:1,
      fs:0,
      rel:0,
      modestbranding:1,
      enablejsapi:1,
      playsinline:1,
      mute:0,
    },
    events:{
      onReady:(e)=>{
        e.target.setVolume(+document.getElementById('volSlider').value);
        toast('✦ Rocola lista para cantar');
      },
      onStateChange:onYTState,
      onError:(e)=>{
        const c={2:'Video no válido',5:'Error HTML5',100:'No encontrado',101:'No permitido',150:'No permitido'};
        toast('⚠ '+(c[e.data]||'Prueba otra canción'));
        setTimeout(playNext,2000);
      }
    }
  });
};

function onYTState(e){
  const S=YT.PlayerState;
  if(e.data===S.PLAYING){
    isPlaying=true;
    document.getElementById('btnPlay').textContent='⏸';
    setSpinning(true); startProg(); startSync();
  } else if(e.data===S.PAUSED){
    isPlaying=false;
    document.getElementById('btnPlay').textContent='▶';
    setSpinning(false); stopProg(); stopSync();
  } else if(e.data===S.ENDED){
    isPlaying=false;
    document.getElementById('btnPlay').textContent='▶';
    setSpinning(false); stopProg(); stopSync();
    setTimeout(playNext,1000);
  }
}

/* ══════════════════════════════════════
   YOUTUBE SEARCH — múltiples APIs públicas
══════════════════════════════════════ */
const PIPED_API=[
  'https://pipedapi.kavin.rocks',
  'https://pipedapi.adminforge.de',
  'https://piped-api.privacy.com.de',
  'https://api.piped.yt',
];
const INVIDIOUS_API=[
  'https://invidious.privacydev.net',
  'https://inv.riverside.rocks',
  'https://invidious.lunar.icu',
  'https://iv.melmac.space',
  'https://invidious.nerdvpn.de',
];

async function searchYT(q){
  const enc=encodeURIComponent(q+' audio');

  // 1. Piped API
  for(const base of PIPED_API){
    try{
      const r=await fetch(`${base}/search?q=${enc}&filter=videos`,{signal:AbortSignal.timeout(5000)});
      if(!r.ok)continue;
      const d=await r.json();
      if(d.items&&d.items.length){
        const items=d.items.filter(i=>i.url||i.videoId).slice(0,6);
        if(items.length) return items.map(i=>({
          videoId:(i.url||'').replace('/watch?v=','')||i.videoId||'',
          title:i.title||'',
          channel:i.uploaderName||i.channel||'',
          thumb:i.thumbnail||`https://i.ytimg.com/vi/${(i.url||'').replace('/watch?v=','')}/mqdefault.jpg`,
          duration:i.duration||0
        })).filter(i=>i.videoId);
      }
    }catch(e){}
  }

  // 2. Invidious API
  for(const base of INVIDIOUS_API){
    try{
      const r=await fetch(`${base}/api/v1/search?q=${enc}&type=video&fields=videoId,title,author,lengthSeconds,videoThumbnails`,{signal:AbortSignal.timeout(5000)});
      if(!r.ok)continue;
      const d=await r.json();
      if(Array.isArray(d)&&d.length){
        return d.slice(0,6).map(v=>({
          videoId:v.videoId||'',
          title:v.title||'',
          channel:v.author||'',
          thumb:(v.videoThumbnails&&v.videoThumbnails[3])?v.videoThumbnails[3].url:`https://i.ytimg.com/vi/${v.videoId}/mqdefault.jpg`,
          duration:v.lengthSeconds||0
        })).filter(i=>i.videoId);
      }
    }catch(e){}
  }

  return null;
}

/* ══════════════════════════════════════
   SEARCH UI
══════════════════════════════════════ */
document.getElementById('btnSearch').addEventListener('click',doSearch);
['inpSong','inpArtist'].forEach(id=>document.getElementById(id).addEventListener('keydown',e=>{if(e.key==='Enter')doSearch()}));

async function doSearch(){
  const song=document.getElementById('inpSong').value.trim();
  const artist=document.getElementById('inpArtist').value.trim();
  if(!song&&!artist){toast('Escribe el título o artista');return;}
  const q=[song,artist].filter(Boolean).join(' ');
  const btn=document.getElementById('btnSearch');
  btn.textContent='⏳ Buscando...'; btn.disabled=true;
  toast('Buscando en YouTube...');

  const results=await searchYT(q);
  btn.textContent='🔍 Buscar en YouTube'; btn.disabled=false;
  const box=document.getElementById('resultsBox');
  box.innerHTML='';

  if(!results||!results.length){
    box.style.display='none';
    toast('Sin resultados · Intenta con otro término');
    return;
  }

  box.style.display='block';
  toast(`${results.length} resultados ↓ Elige uno`);

  results.forEach(r=>{
    if(!r.videoId)return;
    const el=document.createElement('div');
    el.className='r-item';
    el.innerHTML=`
      <img class="r-thumb" src="${r.thumb}" onerror="this.style.opacity='.2'" alt="">
      <div class="r-info">
        <div class="r-title">${esc(r.title)}</div>
        <div class="r-ch">${esc(r.channel)}${r.duration?' · '+fmt(r.duration):''}</div>
      </div>
      <button class="r-add" title="Agregar">＋</button>`;
    el.querySelector('.r-add').addEventListener('click',()=>{
      const title=document.getElementById('inpSong').value.trim()||r.title;
      const art=document.getElementById('inpArtist').value.trim()||r.channel;
      enqueue({videoId:r.videoId,title,artist:art,thumb:r.thumb});
      box.style.display='none';
      document.getElementById('inpSong').value='';
      document.getElementById('inpArtist').value='';
    });
    box.appendChild(el);
  });
}

/* ══════════════════════════════════════
   QUEUE
══════════════════════════════════════ */
function enqueue(song){
  queue.push(song);
  renderQueue();
  toast(`"${song.title}" agregada ✦`);
  if(curIdx===-1)playAt(0);
}

function renderQueue(){
  const list=document.getElementById('queueList');
  const empty=document.getElementById('qEmpty');
  if(!queue.length){empty.style.display='block';list.innerHTML='';list.appendChild(empty);return;}
  empty.style.display='none';list.innerHTML='';
  queue.forEach((s,i)=>{
    const el=document.createElement('div');
    el.className='q-item'+(i===curIdx?' q-active':'');
    el.innerHTML=`<span class="q-num">${i===curIdx?'▶':(i+1)}</span>
      <div class="q-info"><div class="q-name">${esc(s.title)}</div><div class="q-art">${esc(s.artist)}</div></div>
      <button class="q-del">✕</button>`;
    el.querySelector('.q-del').addEventListener('click',e=>{e.stopPropagation();removeQ(i)});
    if(i!==curIdx)el.addEventListener('click',()=>playAt(i));
    list.appendChild(el);
  });
}

function removeQ(i){
  if(i===curIdx){stopAll();queue.splice(i,1);if(!queue.length){curIdx=-1;resetUI();}else{curIdx=Math.min(i,queue.length-1);playAt(curIdx);}}
  else{queue.splice(i,1);if(i<curIdx)curIdx--;}
  renderQueue();
}

/* ══════════════════════════════════════
   PLAYBACK
══════════════════════════════════════ */
function playAt(idx){
  if(idx<0||idx>=queue.length)return;
  stopAll(); curIdx=idx;
  const s=queue[idx];
  renderQueue();
  updateNowPlaying(s);
  showLoading(s);
  if(ytReady&&ytPlayer){
    ytPlayer.setVolume(+document.getElementById('volSlider').value);
    ytPlayer.loadVideoById({videoId:s.videoId,startSeconds:0});
    // Pequeño delay para que YT termine de cargar antes de playVideo
    setTimeout(()=>{try{ytPlayer.playVideo();}catch(e){}},600);
  }
  fetchLyrics(s);
}

function playNext(){if(curIdx<queue.length-1)playAt(curIdx+1);else{stopAll();curIdx=-1;resetUI();renderQueue();toast('Fin de la fila ✦');}}
function playPrev(){if(ytPlayer&&ytPlayer.getCurrentTime&&ytPlayer.getCurrentTime()>4){ytPlayer.seekTo(0);return;}if(curIdx>0)playAt(curIdx-1);}

function stopAll(){
  try{if(ytPlayer&&ytPlayer.stopVideo)ytPlayer.stopVideo();}catch(e){}
  isPlaying=false;stopProg();stopSync();
  lyrics=[];lastActiveIdx=-1;
  document.getElementById('btnPlay').textContent='▶';
  setSpinning(false);
}

document.getElementById('btnPlay').addEventListener('click',()=>{
  if(!ytPlayer||curIdx===-1)return;
  try{isPlaying?ytPlayer.pauseVideo():ytPlayer.playVideo();}catch(e){}
});
document.getElementById('btnNext').addEventListener('click',playNext);
document.getElementById('btnPrev').addEventListener('click',playPrev);
document.getElementById('volSlider').addEventListener('input',e=>{try{if(ytPlayer)ytPlayer.setVolume(+e.target.value);}catch(e){}});
document.getElementById('progBg').addEventListener('click',e=>{
  if(!ytPlayer||curIdx===-1)return;
  try{const rect=e.currentTarget.getBoundingClientRect();ytPlayer.seekTo(((e.clientX-rect.left)/rect.width)*(ytPlayer.getDuration()||0));}catch(e){}
});

/* ══════════════════════════════════════
   PROGRESS
══════════════════════════════════════ */
function startProg(){
  stopProg();
  document.getElementById('progWrap').style.display='block';
  progInt=setInterval(()=>{
    try{
      if(!ytPlayer||!isPlaying)return;
      const c=ytPlayer.getCurrentTime()||0,d=ytPlayer.getDuration()||1;
      document.getElementById('progFill').style.width=((c/d)*100).toFixed(2)+'%';
      document.getElementById('tEl').textContent=fmt(c);
      document.getElementById('tTo').textContent=fmt(d);
    }catch(e){}
  },400);
}
function stopProg(){clearInterval(progInt);}

/* ══════════════════════════════════════
   LYRICS SYNC
══════════════════════════════════════ */
function startSync(){
  stopSync();
  syncInt=setInterval(()=>{
    try{if(!ytPlayer||!isPlaying||!lyrics.length)return;syncAt(ytPlayer.getCurrentTime()||0);}catch(e){}
  },200);
}
function stopSync(){clearInterval(syncInt);}

function syncAt(cur){
  let ai=-1;
  for(let i=lyrics.length-1;i>=0;i--){if(cur>=lyrics[i].startSec){ai=i;break;}}
  if(ai===lastActiveIdx)return;
  lastActiveIdx=ai;
  lyrics.forEach((l,i)=>{
    if(!l.el)return;
    l.el.className='lyric-line';
    if(i===ai)l.el.classList.add('is-active');
    else if(i<ai)l.el.classList.add('is-past');
    else if(i===ai+1)l.el.classList.add('is-near');
    else if(i===ai+2)l.el.classList.add('is-next');
  });
  if(ai>=0&&lyrics[ai]&&lyrics[ai].el){
    const el=lyrics[ai].el;
    const sc=document.getElementById('lyricsScroll');
    sc.scrollTo({top:el.offsetTop-sc.clientHeight/2+el.offsetHeight/2,behavior:'smooth'});
  }
}

/* ══════════════════════════════════════
   CLAUDE API — LYRICS
══════════════════════════════════════ */
async function fetchLyrics(song){
  try{
    const res=await fetch('https://api.anthropic.com/v1/messages',{
      method:'POST',
      headers:{'Content-Type':'application/json'},
      body:JSON.stringify({
        model:'claude-sonnet-4-20250514',
        max_tokens:3000,
        system:'Eres un experto en letras de canciones. Responde SOLO con JSON válido, sin markdown, sin bloques de código, sin texto adicional antes o después.',
        messages:[{role:'user',content:`Dame la letra COMPLETA de la canción "${song.title}" de ${song.artist}.

Responde ÚNICAMENTE con este JSON (sin \`\`\`, sin texto extra):
{"lyrics":[{"line":"texto de la línea","startSec":12},{"line":"siguiente línea","startSec":16}]}

Reglas:
- Incluye TODA la canción completa: intro, versos, coros, puentes, repeticiones, outro
- startSec = tiempo real en segundos donde empieza esa línea en la canción original
- El primer verso suele empezar entre 8-30 segundos
- Entre líneas: 3-6 segundos según el ritmo real
- Mínimo 25 líneas
- Sin [Verso] [Coro] en el texto de line
- Si hay partes instrumentales largas, salta esos segundos
- JSON completo y válido`}]
      })
    });
    const data=await res.json();
    const raw=data.content.map(c=>c.text||'').join('').trim();
    let parsed;
    try{parsed=JSON.parse(raw);}
    catch(e){const m=raw.match(/\{[\s\S]*\}/);if(m)parsed=JSON.parse(m[0]);else throw new Error('json');}
    if(parsed.lyrics&&parsed.lyrics.length>3){
      lyrics=parsed.lyrics.map((l,i,a)=>({text:l.line,startSec:+l.startSec,endSec:a[i+1]?+a[i+1].startSec:(+l.startSec+6),el:null}));
      renderLyrics(song);
      toast(`✦ Letra lista · ${lyrics.length} líneas`);
    }else throw new Error('empty');
  }catch(err){
    console.error(err);
    lyrics=[];
    showNoLyrics();
    toast('Letra no disponible');
  }
}

/* ══════════════════════════════════════
   UI HELPERS
══════════════════════════════════════ */
function updateNowPlaying(s){
  document.getElementById('songNow').innerHTML=`
    <div class="song-now-name">${esc(s.title)}</div>
    <div class="song-now-artist">${esc(s.artist)}</div>`;
}
function setSpinning(on){
  document.getElementById('vinyl').classList.toggle('playing',on);
  document.getElementById('needle').classList.toggle('playing',on);
  document.getElementById('idleDisc').classList.toggle('playing',on);
}
function showLoading(s){
  document.getElementById('lyricsIdle').style.display='none';
  document.getElementById('lyricsHeader').style.display='block';
  document.getElementById('lhSong').textContent=s.title;
  document.getElementById('lhArtist').textContent=s.artist;
  document.getElementById('lyricsScroll').innerHTML=`
    <div class="lyr-loading">
      <div class="lyr-loading-txt">Buscando letra con IA</div>
      <div class="dots"><span></span><span></span><span></span></div>
    </div>`;
}
function renderLyrics(s){
  const sc=document.getElementById('lyricsScroll');
  sc.innerHTML='';
  const sp=document.createElement('div');sp.style.height='43vh';sc.appendChild(sp);
  lyrics.forEach((l,i)=>{
    const el=document.createElement('div');
    el.className='lyric-line'+(i===0?' is-next':'');
    el.textContent=l.text;
    el.addEventListener('click',()=>{try{if(ytPlayer)ytPlayer.seekTo(l.startSec);}catch(e){}});
    l.el=el;sc.appendChild(el);
  });
  const sp2=document.createElement('div');sp2.style.height='43vh';sc.appendChild(sp2);
}
function showNoLyrics(){
  document.getElementById('lyricsScroll').innerHTML=`
    <div class="lyr-loading"><div class="lyr-loading-txt">Letra no disponible<br>♪ ♪ ♪</div></div>`;
}
function resetUI(){
  stopAll();
  document.getElementById('progWrap').style.display='none';
  document.getElementById('songNow').innerHTML='<div class="song-now-idle">Sin canción · Agrega una</div>';
  document.getElementById('lyricsHeader').style.display='none';
  const sc=document.getElementById('lyricsScroll');
  sc.innerHTML='';
  const idle=document.getElementById('lyricsIdle');
  idle.style.display='flex';
  sc.appendChild(idle);
}

let toastT;
function toast(msg){
  const t=document.getElementById('toast');
  t.textContent=msg;t.classList.add('show');
  clearTimeout(toastT);toastT=setTimeout(()=>t.classList.remove('show'),3000);
}
function fmt(s){if(isNaN(s)||s===0)return'0:00';const m=Math.floor(s/60),ss=Math.floor(s%60);return`${m}:${ss.toString().padStart(2,'0')}`;}
function esc(s){return(s||'').replace(/&/g,'&amp;').replace(/</g,'&lt;').replace(/>/g,'&gt;');}
</script>
</body>
</html>
