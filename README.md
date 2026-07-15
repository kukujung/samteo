[index.html](https://github.com/user-attachments/files/30053097/index.html)
<!DOCTYPE html>
<html lang="ko">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no, viewport-fit=cover">
<title>영감의 샘터</title>
<link rel="manifest" href="manifest.json">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="🪺샘터🪺">
<meta name="theme-color" content="#FCFBF9">
<link rel="apple-touch-icon" href="icon.png">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Nanum+Myeongjo:wght@400;700;800&display=swap" rel="stylesheet">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/orioncactus/pretendard@v1.3.9/dist/web/static/pretendard.css">
<style>
  :root{
    --f-disp:"Nanum Myeongjo", serif;
    --f-body:"Pretendard", -apple-system, BlinkMacSystemFont, "Malgun Gothic", sans-serif;
    --paper:#FCFBF9; --surface:#FFFFFF; --field:#F8F5F1;
    --ink:#2B2825; --ink-soft:#938C82; --ink-mid:#6C665D;
    --line:#EDE8E1; --line-strong:#E0D9CF;
    --plum:#A85C74; --plum-ink:#8A4157; --plum-tint:#F7EAEE;
    --sage:#5E93B8; --sage-ink:#47799C; --sage-tint:#E7F1F7; /* 관리루틴 = 하늘색 */
    --hl:#FBE6AE; --hl-ink:#7A5B12;
    --shadow:0 1px 2px rgba(60,50,40,.03), 0 6px 22px rgba(80,60,45,.05);
    --shadow-lift:0 8px 20px rgba(60,50,40,.10), 0 24px 60px rgba(80,60,45,.14);
  }
  html[data-theme="dark"]{
    --paper:#1C1A17; --surface:#24211D; --field:#2A2621;
    --ink:#EDE7DE; --ink-soft:#8F877C; --ink-mid:#B7AFA3;
    --line:#332E28; --line-strong:#423C34;
    --plum:#D28BA0; --plum-ink:#E7B3C1; --plum-tint:#372830;
    --sage:#8FC0DE; --sage-ink:#AFD5EA; --sage-tint:#25313A; /* 관리루틴 = 하늘색 (다크) */
    --hl:#6C5820; --hl-ink:#F4E4B8;
    --shadow:0 1px 2px rgba(0,0,0,.22), 0 6px 22px rgba(0,0,0,.3);
    --shadow-lift:0 8px 20px rgba(0,0,0,.35), 0 24px 60px rgba(0,0,0,.5);
  }
  *{box-sizing:border-box}
  html,body{margin:0;padding:0}
  body{font-family:var(--f-body);background:var(--paper);color:var(--ink);line-height:1.55;
    -webkit-font-smoothing:antialiased;transition:background .35s,color .35s;padding-bottom:env(safe-area-inset-bottom)}
  ::selection{background:var(--plum-tint);color:var(--plum-ink)}
  button{font-family:inherit;cursor:pointer;color:inherit}
  input,textarea{font-family:inherit}
  :focus-visible{outline:2px solid var(--plum);outline-offset:2px;border-radius:6px}

  /* topbar */
  .topbar{position:sticky;top:0;z-index:40;background:color-mix(in srgb,var(--paper) 85%,transparent);
    backdrop-filter:saturate(1.3) blur(10px);border-bottom:1px solid var(--line)}
  .topbar-inner{max-width:960px;margin:0 auto;padding:18px 22px;display:grid;grid-template-columns:1fr auto 1fr;align-items:center;gap:12px}
  .tb-left{justify-self:start;display:flex;gap:8px} .tb-center{justify-self:center} .tb-right{justify-self:end;display:flex;gap:8px}
  .brand{font-family:var(--f-disp);font-weight:800;font-size:23px;letter-spacing:-.01em;background:none;border:0;padding:0;white-space:nowrap}
  .t-btn{height:38px;padding:0 14px;border-radius:11px;border:1px solid var(--line);background:var(--surface);
    font-size:13.5px;font-weight:600;display:inline-flex;align-items:center;gap:7px;transition:.18s}
  .t-btn:hover{border-color:var(--line-strong);transform:translateY(-1px)}
  .t-ico{width:38px;padding:0;justify-content:center;font-size:16px}
  .save-btn{border-color:var(--ink);background:var(--ink);color:var(--paper)}
  .save-btn:hover{filter:brightness(1.12);border-color:var(--ink)}
  .save-btn .at{font-weight:500;font-size:10.5px;opacity:.82}

  .wrap{max-width:960px;margin:0 auto;padding:0 20px}

  /* home */
  .home{min-height:calc(100vh - 170px);display:flex;flex-direction:column;justify-content:center;align-items:center;text-align:center;padding:0 0 11vh;animation:fade .3s ease} /* 중앙보다 살짝 위 */
  .home h2{font-family:var(--f-disp);font-weight:700;font-size:28px;margin:0 0 34px;letter-spacing:-.01em}
  .choices{display:grid;grid-template-columns:1fr 1fr;gap:18px;width:100%;max-width:520px}
  .choice{min-height:290px;background:var(--surface);border:1px solid var(--line);border-radius:22px;padding:26px;
    display:flex;flex-direction:column;justify-content:center;align-items:center;gap:14px;position:relative;transition:.2s}
  .choice:hover{transform:translateY(-4px);box-shadow:var(--shadow-lift)}
  .choice.routine:hover{border-color:var(--sage)} .choice.product:hover{border-color:var(--plum)}
  .choice .emo{font-size:40px;line-height:1}
  .choice .nm{font-family:var(--f-disp);font-weight:700;font-size:23px}
  .choice .arrow{position:absolute;right:22px;bottom:20px;font-size:19px;color:var(--ink-soft);transition:.2s}
  .choice:hover .arrow{transform:translateX(3px)}
  .choice.routine:hover .arrow{color:var(--sage)} .choice.product:hover .arrow{color:var(--plum)}

  /* editor */
  .editor{display:none;padding:26px 0 130px;animation:fade .25s ease}
  .editor.on{display:block}
  .type-lab{font-size:13.5px;font-weight:700;margin-bottom:18px;display:flex;align-items:center;gap:6px}
  .type-lab.product{color:var(--plum)} .type-lab.routine{color:var(--sage)}

  .block{margin-bottom:24px}
  .sec-h{display:flex;align-items:center;gap:8px;margin:0 0 10px}
  .sec-h .e{font-size:20px;line-height:1}
  .sec-h .t{font-family:var(--f-disp);font-weight:700;font-size:17px}

  .theme-input{width:100%;font-family:var(--f-disp);font-weight:700;font-size:25px;border:0;background:none;color:var(--ink);outline:none;padding:2px 0;letter-spacing:-.01em}
  .theme-input::placeholder{color:var(--ink-soft);font-weight:400}
  .concept-row{display:flex;align-items:flex-start;gap:7px;margin-top:6px}
  .concept-row .ar{color:var(--ink-soft);font-size:13px;padding-top:6px;flex-shrink:0}
  .concept-in{flex:1;border:0;background:none;color:var(--ink-mid);outline:none;font-size:13.5px;line-height:1.6;resize:none;overflow:hidden;padding:4px 0;min-height:26px;border-bottom:1px dashed var(--line)}
  .concept-in::placeholder{color:var(--ink-soft)}
  .concept-in:focus{border-bottom-color:var(--plum)}

  /* date */
  .date-row{display:flex;align-items:center;gap:8px;flex-wrap:wrap}
  .date-btn{border:1px solid var(--line);background:var(--field);border-radius:11px;padding:9px 15px;font-size:13.5px;font-weight:700;color:var(--ink-soft);transition:.18s;letter-spacing:.04em}
  .date-btn:hover{border-color:var(--line-strong);color:var(--ink)}
  .date-btn.on{background:var(--ink);border-color:var(--ink);color:var(--paper)}
  .picker{margin-top:10px;background:var(--surface);border:1px solid var(--line);border-radius:14px;box-shadow:var(--shadow);padding:14px;max-width:340px}
  .pk-head{display:flex;align-items:center;gap:8px;margin-bottom:11px}
  .pk-step{font-size:12px;font-weight:700;color:var(--ink-soft)}
  .pk-cur{margin-left:auto;font-size:13px;font-weight:800;letter-spacing:.06em;color:var(--plum)}
  .pk-grid{display:grid;gap:6px}
  .pk-grid.y{grid-template-columns:repeat(3,1fr)}
  .pk-grid.m{grid-template-columns:repeat(4,1fr)}
  .pk-grid.d{grid-template-columns:repeat(7,1fr)}
  .pk-cell{border:1px solid var(--line);background:var(--field);border-radius:9px;padding:9px 0;font-size:13px;font-weight:600;transition:.15s}
  .pk-cell:hover{border-color:var(--plum);color:var(--plum)}
  .pk-cell.sel{background:var(--plum);border-color:var(--plum);color:#fff}
  .pk-foot{display:flex;gap:7px;margin-top:11px}
  .pk-foot button{flex:1;border:1px solid var(--line);background:var(--surface);border-radius:10px;padding:9px;font-size:12.5px;font-weight:600}
  .pk-foot button:hover{background:var(--field)}
  .pk-foot .done{background:var(--plum);border-color:var(--plum);color:#fff}
  .pk-foot .done:hover{background:var(--plum);filter:brightness(1.05)}
  .pk-month{font-family:var(--f-disp);font-weight:700;font-size:15px;text-align:center;margin:2px 0 9px}
  .pk-week{margin-bottom:6px}
  .pk-week span{text-align:center;font-size:11px;font-weight:700;color:var(--ink-soft);padding:2px 0}
  .pk-week span.sun{color:var(--plum)}
  .pk-cell.blank{visibility:hidden}

  /* captures */
  .cap-zone{display:flex;gap:10px;flex-wrap:wrap}
  .cap-thumb{position:relative;width:100px;height:100px;border-radius:12px;overflow:hidden;border:1px solid var(--line);background:var(--field)}
  .cap-thumb img{width:100%;height:100%;object-fit:cover;cursor:zoom-in;display:block}
  .cap-del{position:absolute;top:5px;right:5px;width:22px;height:22px;border-radius:7px;border:0;background:rgba(20,15,12,.62);color:#fff;font-size:12px;display:flex;align-items:center;justify-content:center}
  .cap-add{width:100px;height:100px;border:1.5px dashed var(--line-strong);border-radius:12px;background:none;color:var(--ink-soft);font-size:12px;font-weight:600;display:flex;flex-direction:column;align-items:center;justify-content:center;gap:5px;transition:.18s}
  .cap-add:hover{border-color:var(--sage);color:var(--sage)}
  .cap-add .pl{font-size:20px}

  /* doodle */
  .doodle{position:relative;border:1px solid var(--line);border-radius:12px;background:var(--field);transition:.2s}
  .doodle.focused{border-color:var(--plum);box-shadow:0 0 0 3px var(--plum-tint)}
  .routine-ctx .doodle.focused{border-color:var(--sage);box-shadow:0 0 0 3px var(--sage-tint)}
  .doodle-back,.doodle-in{font-family:var(--f-body);font-size:15px;line-height:1.6;padding:13px 15px;white-space:pre-wrap;word-break:break-word;overflow-wrap:break-word;margin:0;border:0;letter-spacing:0}
  .doodle-in{position:relative;display:block;width:100%;box-sizing:border-box;background:none;color:var(--ink);resize:none;outline:none;overflow:hidden;min-height:50px}
  .doodle-back{position:absolute;inset:0;box-sizing:border-box;color:transparent;pointer-events:none;overflow:hidden}
  .doodle-back mark{background:var(--hl);color:transparent;border-radius:5px;box-decoration-break:clone;-webkit-box-decoration-break:clone}

  /* item */
  .item{background:var(--surface);border:1px solid var(--line);border-radius:14px;padding:14px;margin-bottom:12px;box-shadow:var(--shadow);transition:box-shadow .2s,border-color .2s,opacity .2s}
  .item.dragging{opacity:.55;box-shadow:var(--shadow-lift);border-color:var(--plum)}
  .routine-ctx .item.dragging{border-color:var(--sage)}
  .item-head{display:flex;align-items:center;gap:9px;margin-bottom:10px}
  .item-no{font-size:19px;line-height:1;flex-shrink:0}
  .name-in{flex:1;min-width:0;border:0;background:none;color:var(--ink);outline:none;font-size:16px;font-weight:700;padding:5px 0;border-bottom:1px solid var(--line);transition:.18s}
  .name-in:focus{border-bottom-color:var(--plum)}
  .routine-ctx .name-in:focus{border-bottom-color:var(--sage)}
  .name-in::placeholder{color:var(--ink-soft);font-weight:400}
  .item-tools{display:flex;gap:5px;flex-shrink:0}
  .tool{width:30px;height:30px;border-radius:8px;border:1px solid var(--line);background:var(--field);color:var(--ink-soft);font-size:14px;display:flex;align-items:center;justify-content:center;transition:.15s;touch-action:none}
  .tool:hover{color:var(--ink);border-color:var(--line-strong)}
  .tool.del:hover{color:#B15656;border-color:#B15656}
  .tool.grab{cursor:grab} .tool.grab:active{cursor:grabbing}

  .item-tags{display:flex;align-items:center;gap:6px;flex-wrap:wrap;margin:0 0 10px 0;padding:7px 10px;border-radius:9px;background:var(--field);border:1px dashed var(--line-strong);min-height:34px}
  .it-tag{font-size:11.5px;font-weight:600;background:var(--hl);color:var(--hl-ink);padding:3px 9px;border-radius:6px;cursor:pointer}
  .it-tag:hover{filter:brightness(.96)}
  .it-empty{font-size:11.5px;color:var(--ink-soft)}

  .links{display:flex;flex-direction:column;gap:6px;margin-bottom:10px}
  .link-chip{display:flex;align-items:center;gap:9px;border:1px solid var(--line);border-radius:10px;padding:6px;background:var(--field);text-decoration:none;color:var(--ink);transition:.18s}
  .link-chip:hover{border-color:var(--plum)}
  .link-chip .thumb{width:56px;height:34px;border-radius:6px;object-fit:cover;flex-shrink:0;background:var(--line)}
  .link-chip .ph{width:56px;height:34px;border-radius:6px;flex-shrink:0;background:var(--plum-tint);color:var(--plum);display:flex;align-items:center;justify-content:center;font-size:13px}
  .link-chip .u{flex:1;min-width:0;font-size:12.5px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;color:var(--ink-mid)}
  .link-chip .lx{border:0;background:none;color:var(--ink-soft);font-size:14px;padding:4px 6px;flex-shrink:0}
  .link-chip .lx:hover{color:#B15656}
  .link-add{align-self:flex-start;border:1px dashed var(--line-strong);background:none;color:var(--plum);font-size:12.5px;font-weight:600;padding:6px 12px;border-radius:9px;display:inline-flex;align-items:center;gap:5px}
  .link-add:hover{background:var(--field);border-color:var(--plum)}
  .link-edit{display:flex;gap:6px}
  .link-edit input{flex:1;border:1px solid var(--line);background:var(--field);border-radius:9px;padding:8px 10px;font-size:13px;outline:none}
  .link-edit input:focus{border-color:var(--plum)}
  .link-edit button{border:0;border-radius:9px;padding:0 13px;font-size:12.5px;font-weight:700;background:var(--plum);color:#fff}

  .add-item{width:100%;padding:13px;border:1.5px dashed var(--line-strong);border-radius:14px;background:none;color:var(--plum);font-weight:700;font-size:13.5px;transition:.2s;display:flex;align-items:center;justify-content:center;gap:7px}
  .routine-ctx .add-item{color:var(--sage)}
  .add-item:hover{background:var(--field);border-color:var(--plum)}
  .routine-ctx .add-item:hover{border-color:var(--sage)}

  /* drawer */
  .scrim{position:fixed;inset:0;z-index:70;background:rgba(35,28,22,.4);backdrop-filter:blur(2px);opacity:0;pointer-events:none;transition:opacity .25s}
  .scrim.on{opacity:1;pointer-events:auto}
  .drawer{position:fixed;top:0;left:0;bottom:0;z-index:75;width:min(340px,86vw);background:var(--surface);border-right:1px solid var(--line);box-shadow:var(--shadow-lift);transform:translateX(-100%);transition:transform .3s cubic-bezier(.4,0,.2,1);display:flex;flex-direction:column}
  .drawer.on{transform:none}
  .drawer-head{padding:20px 20px 14px;display:flex;align-items:center;border-bottom:1px solid var(--line)}
  .drawer-head h3{font-family:var(--f-disp);font-size:19px;margin:0}
  .drawer-head .x{margin-left:auto;background:none;border:0;font-size:19px;color:var(--ink-soft)}
  .drawer-search{display:flex;align-items:center;gap:7px;margin:14px 16px 0;padding:9px 11px;border:1px solid var(--line);background:var(--field);border-radius:11px;transition:.18s}
  .drawer-search:focus-within{border-color:var(--plum);background:var(--surface)}
  .drawer-search input{flex:1;min-width:0;border:0;background:none;color:var(--ink);outline:none;font-size:13.5px}
  .drawer-search input::placeholder{color:var(--ink-soft)}
  .drawer-search button{border:0;background:none;color:var(--ink-soft);font-size:12px;padding:2px 4px;display:none}
  .drawer-search.has button{display:block}
  .drawer-search button:hover{color:var(--ink)}
  .hit{background:var(--hl);color:var(--hl-ink);border-radius:4px;padding:0 2px}
  .entry-snip{font-size:11.5px;color:var(--ink-soft);margin-top:2px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
  .entry-main{flex:1;min-width:0;display:flex;flex-direction:column}
  .search-none{text-align:center;color:var(--ink-soft);font-size:13px;padding:40px 20px}
  .drawer-hint{font-size:11px;color:var(--ink-soft);padding:9px 18px 0}
  .drawer-new{margin:8px 16px 6px;padding:11px;border:1px dashed var(--line-strong);border-radius:11px;background:none;color:var(--ink-mid);font-weight:600;font-size:13px;display:flex;align-items:center;justify-content:center;gap:6px}
  .drawer-new:hover{border-color:var(--plum);color:var(--plum)}
  .drawer-body{flex:1;overflow-y:auto;padding:6px 12px 24px}
  .month-grp{margin-top:14px}
  .month-h{font-size:11px;letter-spacing:.06em;font-weight:700;color:var(--ink-soft);padding:6px 8px;position:sticky;top:0;background:var(--surface)}
  .entry{display:flex;align-items:center;gap:10px;padding:11px 10px;border-radius:10px;cursor:pointer;transition:.15s;user-select:none}
  .entry:hover{background:var(--field)}
  .entry .dot{width:7px;height:7px;border-radius:50%;flex-shrink:0}
  .entry .dot.product{background:var(--plum)} .entry .dot.routine{background:var(--sage)}
  .entry .nm{flex:1;min-width:0;font-size:14px;font-weight:600;overflow:hidden;text-overflow:ellipsis;white-space:nowrap}
  .entry .nm.empty{color:var(--ink-soft);font-weight:400}
  .entry .ty{font-size:13px;flex-shrink:0}
  .drawer-empty{text-align:center;color:var(--ink-soft);font-size:13px;padding:50px 20px}

  /* modal etc */
  .overlay{position:fixed;inset:0;z-index:90;background:rgba(35,28,22,.46);backdrop-filter:blur(3px);display:none;align-items:center;justify-content:center;padding:20px}
  .overlay.on{display:flex;animation:fade .2s ease}
  .modal{background:var(--surface);border-radius:20px;box-shadow:var(--shadow-lift);width:min(420px,100%);padding:26px;animation:pop .22s ease}
  .modal h3{font-family:var(--f-disp);font-size:20px;margin:0 0 6px}
  .modal p{color:var(--ink-mid);font-size:13.5px;margin:0 0 20px;line-height:1.55}
  .m-list{display:flex;flex-direction:column;gap:8px;margin-bottom:16px}
  .m-actions{display:flex;gap:10px;justify-content:flex-end}
  .btn{padding:11px 16px;border-radius:11px;font-weight:600;font-size:13.5px;border:1px solid var(--line);background:var(--surface);text-align:left;display:flex;flex-direction:column;gap:2px}
  .btn.center{align-items:center;text-align:center}
  .btn:hover{background:var(--field)}
  .btn .sub{font-size:11px;color:var(--ink-soft);font-weight:400}
  .btn.primary{background:var(--plum);border-color:var(--plum);color:#fff}
  .btn.primary:hover{background:var(--plum);filter:brightness(1.05)}
  .btn.danger{background:#B15656;border-color:#B15656;color:#fff}
  .btn.danger:hover{background:#B15656;filter:brightness(1.05)}
  .lightbox{position:fixed;inset:0;z-index:95;background:rgba(15,12,10,.86);display:none;align-items:center;justify-content:center;padding:24px;cursor:zoom-out}
  .lightbox.on{display:flex;animation:fade .2s ease}
  .lightbox img{max-width:100%;max-height:100%;border-radius:10px}
  .toast-wrap{position:fixed;left:50%;bottom:34px;transform:translateX(-50%);z-index:99;display:flex;flex-direction:column;gap:8px;align-items:center;pointer-events:none}
  .toast{background:var(--ink);color:var(--paper);padding:11px 18px;border-radius:12px;font-size:13px;font-weight:600;box-shadow:var(--shadow-lift);animation:tin .3s ease}
  .toast.out{animation:tout .3s ease forwards}

  @keyframes pop{from{opacity:0;transform:scale(.97) translateY(4px)}to{opacity:1;transform:none}}
  @keyframes fade{from{opacity:0}to{opacity:1}}
  @keyframes tin{from{opacity:0;transform:translateY(10px)}to{opacity:1;transform:none}}
  @keyframes tout{to{opacity:0;transform:translateY(10px)}}

  @media (max-width:680px){
    .wrap{padding:0 14px}
    .topbar-inner{padding:13px 16px;gap:8px}
    .brand{font-size:17px}
    .t-btn{height:36px;padding:0 10px;font-size:12px;border-radius:10px;gap:5px}
    .t-ico{width:36px;padding:0;font-size:15px}
    .tb-right{gap:7px}
    .home{min-height:calc(100svh - 150px);justify-content:center;padding:0 0 13vh}
    .home h2{font-size:22px;margin-bottom:24px}
    .tool{width:34px;height:34px;font-size:15px}
    .choices{grid-template-columns:1fr 1fr;gap:11px;max-width:100%}
    .choice{min-height:230px;padding:16px;border-radius:18px;gap:10px}
    .choice .emo{font-size:31px}
    .choice .nm{font-size:18px}
    .choice .arrow{right:14px;bottom:12px;font-size:16px}
    .theme-input{font-size:21px}
  }
  @media (max-width:380px){
    .brand{font-size:12.5px}
    .t-btn{height:32px;padding:0 8px;font-size:11px}
    .t-ico{width:32px}
    .choice{min-height:200px} .choice .nm{font-size:16px} .choice .emo{font-size:27px}
  }
  /* scripted(대본화) chip + sync */
  .lab-row{display:flex;align-items:center;justify-content:space-between;gap:10px;flex-wrap:wrap}
  .scripted-chip{border:1px solid var(--line);background:var(--surface);border-radius:999px;padding:6px 13px;
    font-size:12.5px;font-weight:600;color:var(--ink-soft);transition:.18s}
  .scripted-chip:hover{border-color:var(--line-strong)}
  .scripted-chip.on{background:var(--hl);color:var(--hl-ink);border-color:transparent}
  .entry .done{font-size:12px;margin-right:1px;flex:none}
  .item .tool.grab{touch-action:none;cursor:grab} .item.dragging{opacity:.75}
  .sync-form label{display:block;font-size:12.5px;font-weight:700;color:var(--ink-mid);margin:12px 0 5px}
  .sync-form input{width:100%;height:42px;border:1px solid var(--line-strong);border-radius:10px;background:var(--field);
    padding:0 12px;font-size:14px;color:var(--ink)}
  .sub-p{font-size:13px;color:var(--ink-soft);margin:6px 0 2px;line-height:1.55}
  /* 📅 월간 캘린더 뷰 — 화면 전체를 채우는 고정 그리드 */
  .calview{position:fixed;inset:0;z-index:80;background:var(--paper);display:flex;flex-direction:column;padding:14px 14px 0;overflow:hidden;animation:fade .25s ease}
  .calview[hidden]{display:none}
  .cal-head{flex:none;display:flex;align-items:center;gap:8px;max-width:660px;width:100%;margin:6px auto 14px}
  .cal-title{flex:1;text-align:center;font-family:var(--f-disp);font-weight:700;font-size:20px}
  .cal-nav{width:38px;height:38px;border-radius:11px;border:1px solid var(--line);background:var(--surface);font-size:17px;color:var(--ink-mid)}
  .cal-nav:hover{border-color:var(--line-strong)}
  .cal-x{width:38px;height:38px;border:0;background:none;font-size:17px;color:var(--ink-soft)}
  .cal-legend{flex:none;max-width:660px;width:100%;margin:0 auto 20px;display:flex;gap:16px;justify-content:center;align-items:center;font-size:12px;color:var(--ink-soft)}
  .cal-legend i{width:7px;height:7px;border-radius:50%;display:inline-block;margin-right:5px}
  .cal-undated{border:1px solid var(--line);background:var(--surface);border-radius:999px;padding:4px 11px;font-size:11.5px;font-weight:600;color:var(--ink-mid)}
  .cal-week{flex:none;display:grid;grid-template-columns:repeat(7,minmax(0,1fr));max-width:660px;width:100%;margin:0 auto}
  .cal-week span{text-align:center;font-size:12px;font-weight:700;color:var(--ink-soft);padding-bottom:7px}
  .cal-week span.sun{color:#C0504A}
  .cal-grid{flex:1;min-height:0;display:grid;grid-template-columns:repeat(7,minmax(0,1fr));grid-auto-rows:1fr;max-width:660px;width:100%;margin:0 auto;overflow:hidden}
  .cal-cell{border:0;border-top:1px solid var(--line);display:flex;flex-direction:column;align-items:stretch;gap:2px;padding:5px 3px 3px;overflow:hidden;text-align:left;background:none;min-width:0}
  .cal-cell.blank{pointer-events:none}
  .cal-cell.sel{background:var(--field)}
  .cal-cell .cd{font-size:12.5px;font-weight:700;line-height:1;color:var(--ink-mid);margin-bottom:3px;flex:none} /* 숫자 = 왼쪽 상단 */
  .cal-cell .cd.sun{color:#C0504A}
  .cal-cell.today .cd{background:var(--plum);color:#fff;width:21px;height:21px;border-radius:50%;display:inline-flex;align-items:center;justify-content:center;font-size:12px}
  .cal-chip{display:block;font-size:10px;font-weight:600;border-radius:5px;padding:2.5px 5px;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;line-height:1.35;flex:none} /* 형광펜 주제 */
  .cal-chip.routine{background:var(--sage-tint);color:var(--sage-ink)}
  .cal-chip.product{background:var(--plum-tint);color:var(--plum-ink)}
  .cal-more{font-size:9.5px;font-weight:600;color:var(--ink-soft);padding-left:3px}
  /* 날짜 상세 — 중앙 팝업 */
  .cal-sheet-bg{position:fixed;inset:0;z-index:85;background:rgba(35,28,22,.4);backdrop-filter:blur(2px);opacity:0;pointer-events:none;transition:opacity .22s}
  .cal-sheet-bg.on{opacity:1;pointer-events:auto}
  .cal-day{position:fixed;left:50%;top:50%;z-index:86;width:min(420px,calc(100% - 40px));max-height:80vh;overflow-y:auto;background:var(--surface);border-radius:20px;box-shadow:0 20px 60px rgba(0,0,0,.28);padding:22px 20px 22px;transform:translate(-50%,-50%) scale(.95);opacity:0;pointer-events:none;transition:transform .22s cubic-bezier(.34,1.4,.5,1),opacity .18s}
  .cal-day.on{transform:translate(-50%,-50%) scale(1);opacity:1;pointer-events:auto}
  .cal-day-h{font-weight:700;font-size:17px;color:var(--ink);margin-bottom:16px;text-align:center}
  .cal-rec{display:flex;align-items:center;gap:9px;padding:13px;border:1px solid var(--line);border-radius:11px;background:var(--surface);text-align:left;transition:.15s;margin-bottom:8px;width:100%}
  .cal-rec:hover{background:var(--field)}
  .cal-rec .nm{flex:1;min-width:0;overflow:hidden;text-overflow:ellipsis;white-space:nowrap;font-weight:600;font-size:14px}
  .cal-rec.routine{border-left:3px solid var(--sage)} .cal-rec.product{border-left:3px solid var(--plum)}
  .cal-add-row{display:flex;gap:8px;margin-top:4px}
  .cal-add{flex:1;padding:13px;border:1.5px dashed var(--line-strong);border-radius:11px;background:none;font-weight:600;font-size:13px}
  .cal-add.routine{color:var(--sage)} .cal-add.product{color:var(--plum)}
  .cal-add:hover{background:var(--field)}
  @media (prefers-reduced-motion:reduce){*{animation-duration:.01ms!important;transition-duration:.01ms!important}}
</style>
</head>
<body>

<header class="topbar">
  <div class="topbar-inner">
    <div class="tb-left">
      <button class="t-btn t-ico" id="listBtn" title="기록 목록">🔖</button>
      <button class="t-btn t-ico" id="themeBtn" title="라이트/다크">🌙</button>
    </div>
    <div class="tb-center"><button class="brand" id="brandBtn" title="처음으로">🪸영감의 샘터🪸</button></div>
    <div class="tb-right">
      <button class="t-btn t-ico" id="backupBtn" title="백업 & 클라우드 동기화">💾</button>
      <button class="t-btn t-ico save-btn" id="saveBtn" title="저장"><span id="saveDot">🟡</span></button>
    </div>
  </div>
</header>

<main class="wrap">
  <section class="home" id="homeView">
    <h2>오늘의 영감 기록 🪄</h2>
    <div class="choices">
      <button class="choice routine" data-t="routine"><span class="emo">🧖🏻‍♀️</span><span class="nm">관리루틴</span><span class="arrow">→</span></button>
      <button class="choice product" data-t="product"><span class="emo">👩🏻‍🏫</span><span class="nm">제품추천</span><span class="arrow">→</span></button>
    </div>
  </section>

  <section class="editor" id="editorView">
    <div class="lab-row">
      <div class="type-lab" id="typeLab"></div>
      <button class="scripted-chip" id="scriptedBtn" title="이 낙서로 대본을 완성했다면 눌러두세요">◻️ 대본화 이전</button>
    </div>

    <div class="block">
      <div class="sec-h"><span class="e">✏️</span><span class="t">주제</span></div>
      <input class="theme-input" id="edTheme" placeholder="제목">
      <div class="concept-row"><span class="ar">→</span><textarea class="concept-in" id="edConcept" rows="1" placeholder="컨셉 · 방향"></textarea></div>
    </div>

    <div class="block">
      <div class="sec-h"><span class="e">📅</span><span class="t">날짜</span></div>
      <div class="date-row">
        <button class="date-btn" id="dbSet">YY_MM_DD</button>
        <button class="date-btn" id="dbNone">미정</button>
      </div>
      <div id="pickerMount"></div>
    </div>

    <div class="block" id="captureBlock" style="display:none">
      <div class="sec-h"><span class="e">📸</span><span class="t">캡처본</span></div>
      <div class="cap-zone" id="capZone"></div>
    </div>

    <div class="block">
      <div class="sec-h"><span class="e">🎤</span><span class="t">오프닝</span></div>
      <div id="edOpening"></div>
    </div>

    <div class="block">
      <div class="sec-h"><span class="e" id="itemsEmo"></span><span class="t" id="itemsLab"></span></div>
      <div id="edItems"></div>
      <button class="add-item" id="addItem">＋ <span id="addLabel"></span></button>
    </div>

    <div class="block">
      <div class="sec-h"><span class="e">🎬</span><span class="t">마무리</span></div>
      <div id="edClosing"></div>
    </div>
  </section>
</main>

<div class="scrim" id="scrim"></div>
<aside class="drawer" id="drawer">
  <div class="drawer-head"><h3>🪺 기록 목록</h3><button class="x" id="drawerX">✕</button></div>
  <div class="drawer-search"><span>🔎</span><input id="searchIn" placeholder="검색 (제목 · 태그 · 내용)" autocomplete="off"><button id="searchX" title="지우기">✕</button></div>
  <div class="drawer-hint">(클릭 = 열기 · 더블클릭 = 삭제)</div>
  <button class="drawer-new" id="calBtn">📅 캘린더 보기</button>
  <button class="drawer-new" id="drawerNew">＋ 새 기록</button>
  <div class="drawer-body" id="drawerBody"></div>
</aside>

<div class="calview" id="calView" hidden>
  <div class="cal-head">
    <button class="cal-nav" id="calPrev" title="이전 달">‹</button>
    <div class="cal-title" id="calTitle"></div>
    <button class="cal-nav" id="calNext" title="다음 달">›</button>
    <button class="cal-x" id="calX" title="닫기">✕</button>
  </div>
  <div class="cal-legend" id="calLegend"></div>
  <div class="cal-week"><span class="sun">일</span><span>월</span><span>화</span><span>수</span><span>목</span><span>금</span><span>토</span></div>
  <div class="cal-grid" id="calGrid"></div>
</div>
<div class="cal-sheet-bg" id="calSheetBg"></div>
<div class="cal-day" id="calDay"></div>

<div class="overlay" id="overlay"><div class="modal" id="modal"></div></div>
<div class="lightbox" id="lightbox"><img id="lightboxImg" alt="캡처본"></div>
<div class="toast-wrap" id="toastWrap"></div>
<input type="file" id="capInput" accept="image/*" multiple style="display:none">
<input type="file" id="importFile" accept="application/json" style="display:none">

<script>
(function(){
  "use strict";
  var LS="yeonggam_samteo_v3", TAG_RE=/#[\p{L}\p{N}_]+/gu;
  var NUM=["1️⃣","2️⃣","3️⃣","4️⃣","5️⃣","6️⃣","7️⃣","8️⃣","9️⃣","🔟"];
  var TYPES={
    product:{emo:"👩🏻‍🏫",label:"제품추천",item:"제품",add:"제품 추가",secEmo:"🛍️"},
    routine:{emo:"🧖🏻‍♀️",label:"관리루틴",item:"루틴",add:"루틴 추가",secEmo:"🧴"}
  };
  var store={plans:[],settings:{theme:"light",folder:false},lastSaved:null};
  var storageOK=true, currentId=null, dirHandle=null, dirty=false;

  function load(){try{var r=localStorage.getItem(LS)||localStorage.getItem("yeonggam_samteo_v2");
      if(r){var d=JSON.parse(r);if(d&&typeof d==="object")store=Object.assign(store,d);}}catch(e){storageOK=false;}
    if(!store.settings)store.settings={theme:"light"};if(!Array.isArray(store.plans))store.plans=[];
    if(!Array.isArray(store.deleted))store.deleted=[];
    var mig=[];
    store.plans.forEach(function(p){
      if(!Array.isArray(p.captures))p.captures=[];
      /* 구버전 캡처(본문 내 base64) → 기기 저장소(IndexedDB)로 이관, 목록에는 참조만 */
      p.captures=p.captures.map(function(c){
        if(typeof c==="string"){var cid=uid();mig.push({k:"cap:"+cid,v:c});return {id:cid,up:false};}
        return c;});
      if(p.concept==null)p.concept="";
      if(p.dY===undefined){p.dY="";p.dM="";p.dD="";
        if(p.date){var s=String(p.date).split("-");p.dY=s[0]||"";p.dM=s[1]||"";p.dD=s[2]||"";}}
      p.dateSet=!!(p.dY);
      p.scripted=!!p.scripted;
      if(!p.updatedAt)p.updatedAt=p.createdAt||Date.now();
      (p.items||[]).forEach(function(it){if(it.name==null)it.name="";
        if(!Array.isArray(it.links)){it.links=it.link?[it.link]:[];delete it.link;}});});
    if(mig.length){Promise.all(mig.map(function(m){return idbSet(m.k,m.v);}))
      .then(function(){
        try{localStorage.removeItem("yeonggam_samteo_v2");}catch(e){} /* 구버전 잔여 데이터 청소 → 공간 확보 */
        if(persistLocal())toast("📦 캡처를 새 저장 방식으로 옮겼어요 — 저장 공간 걱정 끝!");
        uploadCaps();}).catch(function(){});}}
  function persistLocal(){try{store.lastSaved=Date.now();localStorage.setItem(LS,JSON.stringify(store));storageOK=true;dirty=false;updateSaveUI();writeFolder();return true;}
    catch(e){/* 공간 부족 → 구버전 잔여 데이터를 지우고 1회 재시도 */
      try{localStorage.removeItem("yeonggam_samteo_v2");
        localStorage.setItem(LS,JSON.stringify(store));storageOK=true;dirty=false;updateSaveUI();writeFolder();return true;}
      catch(e2){storageOK=false;toast("저장 공간이 가득 찼어요 — ☁️ 동기화를 연결하면 해결됩니다");return false;}}}
  function persist(){
    /* 저장 원칙: 저장을 누르면 빈 기록이라도 전부 기록으로 승격 (사용자 확정 2026-07-15) */
    store.plans.forEach(function(p){if(p.draft)delete p.draft;});
    var ok=persistLocal();if(ok){cloudPush();uploadCaps();}
    return ok;}
  function markDirty(){var p=currentId?getPlan(currentId):null;if(p)p.updatedAt=Date.now();
    cloudState="idle";dirty=true;updateSaveUI();}
  function updateSaveUI(){var d=document.getElementById("saveDot");if(!d)return;
    var t,tt;
    if(dirty){t="🔴";tt="저장되지 않은 변경이 있어요";}
    else if(!ghReady()){t="🟡";tt="이 기기에 저장됨 (클라우드 미연결 — 백업 메뉴에서 연결)";}
    else if(cloudState==="ok"){t="🟢";tt="모두 저장됨 · ☁️ 모든 기기에 반영됨";}
    else if(cloudState==="err"){t="⚠️";tt="이 기기에는 저장됨 · 클라우드 반영 실패 (온라인 시 저장을 다시 누르세요)";}
    else{t="🟡";tt="이 기기에 저장됨";}
    d.textContent=t;document.getElementById("saveBtn").title=tt;}

  /* ---- ☁️ 클라우드 동기화 (GitHub 비공개 저장소) ----
     동기화 대상: 태그·내용 등 텍스트만. captures(캡처 이미지)·links(유튜브)는 이 기기에만 보관. */
  var GH_KEY="samteo_gh_v1", gh=null, ghSha=null, cloudState="idle", pushing=false, pushQueued=false;
  try{gh=JSON.parse(localStorage.getItem(GH_KEY)||"null");}catch(e){}
  function ghReady(){return !!(gh&&gh.owner&&gh.repo&&gh.token);}
  function ghUrl(){return "https://api.github.com/repos/"+encodeURIComponent(gh.owner)+"/"+encodeURIComponent(gh.repo)+"/contents/data.json";}
  function ghHeaders(){return {"Authorization":"Bearer "+gh.token,"Accept":"application/vnd.github+json","X-GitHub-Api-Version":"2022-11-28"};}
  function b64e(s){return btoa(unescape(encodeURIComponent(s)));}
  function b64d(s){return decodeURIComponent(escape(atob(String(s).replace(/\s/g,""))));}
  function setSyncUI(s){cloudState=s;updateSaveUI();}
  function cloudPayload(){return JSON.stringify({v:4,savedAt:Date.now(),deleted:store.deleted||[],
    plans:store.plans.filter(function(p){return !p.draft;}).map(function(p){var c=Object.assign({},p);
      /* 캡처는 참조({id,up})만 동기화 — 이미지 원본은 captures/<id>.jpg 파일로 별도 저장 */
      c.captures=(p.captures||[]).filter(function(x){return x&&typeof x==="object";})
        .map(function(x){return {id:x.id,up:!!x.up};});
      c.items=(p.items||[]).map(function(it){var t=Object.assign({},it);delete t.links;return t;});return c;})},null,1);}
  function cloudPull(cb){if(!ghReady()||navigator.onLine===false){if(cb)cb(false);return;}
    fetch(ghUrl(),{headers:ghHeaders()}).then(function(r){
      if(r.status===404){ghSha=null;return "empty";}
      if(!r.ok)throw new Error("HTTP "+r.status);
      return r.json();
    }).then(function(j){
      if(j==="empty"){cloudPush();if(cb)cb(true);return;}
      ghSha=j.sha;var data={};try{data=JSON.parse(b64d(j.content));}catch(e){data={};}
      applyMerge(data);if(cb)cb(true);
    }).catch(function(){setSyncUI("err");if(cb)cb(false);});}
  function cloudPush(isRetry){if(!ghReady())return;
    if(pushing){pushQueued=true;return;}
    pushing=true;setSyncUI("busy");
    var body={message:"낙서 저장 "+new Date().toISOString().slice(0,19),content:b64e(cloudPayload())};
    if(ghSha)body.sha=ghSha;
    fetch(ghUrl(),{method:"PUT",headers:ghHeaders(),body:JSON.stringify(body)}).then(function(r){
      if(r.status===409||r.status===422){pushing=false;
        if(isRetry)throw new Error("conflict");
        return cloudPull(function(){cloudPush(true);});}
      if(!r.ok)throw new Error("HTTP "+r.status);
      return r.json().then(function(j){if(j&&j.content)ghSha=j.content.sha;
        pushing=false;setSyncUI("ok");
        if(pushQueued){pushQueued=false;cloudPush();}});
    }).catch(function(){pushing=false;setSyncUI("err");toast("☁️ 클라우드 반영 실패 — 이 기기에는 저장됐어요");});}
  function applyMerge(cloud){
    var tomb={};(store.deleted||[]).concat((cloud&&cloud.deleted)||[]).forEach(function(t){
      if(t&&t.id&&(!tomb[t.id]||tomb[t.id]<t.ts))tomb[t.id]=t.ts;});
    var loc={},cl={},ids=[];
    store.plans.forEach(function(p){loc[p.id]=p;ids.push(p.id);});
    ((cloud&&cloud.plans)||[]).forEach(function(p){if(p&&p.id){cl[p.id]=p;if(!loc[p.id])ids.push(p.id);}});
    var merged=[],changedL=false,changedC=false;
    ids.forEach(function(id){
      var L=loc[id],C=cl[id];
      var lt=L?(L.updatedAt||L.createdAt||0):-1, ct=C?(C.updatedAt||C.createdAt||0):-1;
      if(tomb[id]&&tomb[id]>=Math.max(lt,ct)){if(L)changedL=true;if(C)changedC=true;return;}
      if(!C){merged.push(L);changedC=true;return;}
      if(!L){var n=Object.assign({},C);if(!Array.isArray(n.captures))n.captures=[];
        (n.items||[]).forEach(function(it){if(!Array.isArray(it.links))it.links=[];});
        merged.push(n);changedL=true;return;}
      if(ct>lt){var w=Object.assign({},C);
        if(!Array.isArray(w.captures))w.captures=L.captures||[];
        var lit={};(L.items||[]).forEach(function(it){lit[it.id]=it;});
        w.items=(C.items||[]).map(function(it){var o=Object.assign({},it);
          if(!Array.isArray(o.links))o.links=(lit[it.id]&&Array.isArray(lit[it.id].links))?lit[it.id].links:[];
          return o;});
        merged.push(w);changedL=true;}
      else{merged.push(L);if(lt>ct)changedC=true;}});
    var tl=[];Object.keys(tomb).forEach(function(id){tl.push({id:id,ts:tomb[id]});});
    tl.sort(function(a,b){return b.ts-a.ts;});store.deleted=tl.slice(0,800);
    store.plans=merged;
    if(changedL){persistLocal();
      if(currentId&&!getPlan(currentId)){showHome();}
      else if(currentId){openEditor(currentId);}
      renderDrawer();toast("☁️ 다른 기기의 낙서를 불러왔어요");}
    if(changedC)cloudPush();
    if(!changedL&&!changedC)setSyncUI("ok");
    uploadCaps();}
  function syncModal(){modal.innerHTML='<h3>☁️ 클라우드 동기화</h3>'+
    '<p class="sub-p">GitHub 비공개 저장소에 낙서(태그·내용·캡처)가 저장되어 폰·아이패드·PC가 하나로 합쳐집니다. 기기당 최초 1회만 입력하면 됩니다. 유튜브 링크만 이 기기에 남습니다.</p>'+
    '<div class="sync-form">'+
    '<label>GitHub 아이디</label><input id="ghO" autocapitalize="none" autocomplete="off" value="'+esc(gh&&gh.owner||"")+'">'+
    '<label>데이터 저장소 이름</label><input id="ghR" autocapitalize="none" autocomplete="off" value="'+esc(gh&&gh.repo||"samteo-data")+'">'+
    '<label>토큰 (github_pat_… )</label><input id="ghT" type="password" autocomplete="off" value="'+esc(gh&&gh.token||"")+'">'+
    '</div><div class="m-actions">'+
    (ghReady()?'<button class="btn center danger" id="ghDel">해제</button>':'')+
    '<button class="btn center" id="ghC">닫기</button><button class="btn center primary" id="ghS">연결</button></div>';
    overlay.classList.add("on");
    document.getElementById("ghC").onclick=closeModal;
    var del=document.getElementById("ghDel");
    if(del)del.onclick=function(){gh=null;ghSha=null;try{localStorage.removeItem(GH_KEY);}catch(e){}
      closeModal();setSyncUI("idle");toast("동기화 해제 — 이 기기의 낙서는 그대로예요");};
    document.getElementById("ghS").onclick=function(){
      var o=document.getElementById("ghO").value.trim(),r2=document.getElementById("ghR").value.trim(),t=document.getElementById("ghT").value.trim();
      if(!o||!r2||!t){toast("세 칸을 모두 입력해주세요");return;}
      gh={owner:o,repo:r2,token:t};ghSha=null;
      try{localStorage.setItem(GH_KEY,JSON.stringify(gh));}catch(e){}
      closeModal();toast("연결 확인 중…");
      cloudPull(function(ok){updateSaveUI();uploadCaps();
        toast(ok?"☁️ 연결 완료! 이제 모든 기기가 하나예요":"연결 실패 — 아이디·저장소·토큰을 확인해주세요");});};}

  /* ---- 📸 캡처 동기화: 이미지는 저장소 captures/<id>.jpg 파일로, 기기에는 IndexedDB 캐시 ---- */
  var capMem={}, capBusy={};
  function capUrl(id){return "https://api.github.com/repos/"+encodeURIComponent(gh.owner)+"/"+encodeURIComponent(gh.repo)+"/contents/captures/"+encodeURIComponent(id)+".jpg";}
  function uploadCaps(){if(!ghReady()||navigator.onLine===false)return;
    store.plans.forEach(function(p){(p.captures||[]).forEach(function(c){
      if(!c||typeof c!=="object"||c.up||capBusy[c.id])return;
      capBusy[c.id]=1;
      idbGet("cap:"+c.id).then(function(dataURL){
        if(!dataURL){delete capBusy[c.id];return;}
        var b64=String(dataURL).split(",")[1]||"";
        fetch(capUrl(c.id),{method:"PUT",headers:ghHeaders(),
          body:JSON.stringify({message:"캡처 "+c.id,content:b64})})
        .then(function(r){delete capBusy[c.id];
          if(r.ok||r.status===422){c.up=true;persistLocal();cloudPush();}})
        .catch(function(){delete capBusy[c.id];});
      }).catch(function(){delete capBusy[c.id];});});});}
  function getCap(c,cb){var id=c&&c.id;if(!id){cb(null);return;}
    if(capMem[id]){cb(capMem[id]);return;}
    idbGet("cap:"+id).then(function(v){
      if(v){capMem[id]=v;cb(v);return;}
      if(!ghReady()||navigator.onLine===false){cb(null);return;}
      fetch(capUrl(id),{headers:{"Authorization":"Bearer "+gh.token,"Accept":"application/vnd.github.raw+json","X-GitHub-Api-Version":"2022-11-28"}})
      .then(function(r){if(!r.ok)throw 0;return r.blob();})
      .then(function(bl){var fr=new FileReader();
        fr.onload=function(){capMem[id]=fr.result;idbSet("cap:"+id,fr.result).catch(function(){});cb(fr.result);};
        fr.readAsDataURL(bl);})
      .catch(function(){cb(null);});
    }).catch(function(){cb(null);});}
  function delCapRemote(id){if(!ghReady())return;
    fetch(capUrl(id),{headers:ghHeaders()}).then(function(r){if(!r.ok)throw 0;return r.json();})
    .then(function(j){return fetch(capUrl(id),{method:"DELETE",headers:ghHeaders(),
      body:JSON.stringify({message:"캡처 삭제 "+id,sha:j.sha})});}).catch(function(){});}

  function uid(){return Date.now().toString(36)+Math.random().toString(36).slice(2,7);}
  function esc(s){return String(s==null?"":s).replace(/&/g,"&amp;").replace(/</g,"&lt;").replace(/>/g,"&gt;");}
  function getPlan(id){for(var i=0;i<store.plans.length;i++)if(store.plans[i].id===id)return store.plans[i];return null;}
  function tagsIn(txt){var seen={},out=[];var m=String(txt||"").match(TAG_RE);
    if(m)m.forEach(function(g){var k=g.toLowerCase();if(!seen[k]){seen[k]=1;out.push(g);}});return out;}
  function hi(t){return esc(t).replace(TAG_RE,function(m){return "<mark>"+m+"</mark>";})+"\n";}
  function fmtSaved(ts){if(!ts)return"저장 전";var d=new Date(ts),n=new Date(),h=("0"+d.getHours()).slice(-2),m=("0"+d.getMinutes()).slice(-2);
    return d.toDateString()===n.toDateString()?"오늘 "+h+":"+m:(d.getMonth()+1)+"월 "+d.getDate()+"일 "+h+":"+m;}
  function dateLabel(p){if(!p.dateSet||!p.dY)return "YY_MM_DD";
    var s=String(p.dY).slice(-2);if(p.dM)s+="_"+p.dM;if(p.dD)s+="_"+p.dD;return s;}
  function monthKey(p){if(p.dateSet&&p.dY&&p.dM)return p.dY+"-"+p.dM;if(p.dateSet&&p.dY)return p.dY+"-00";return "";}
  function numOf(i){return i<10?NUM[i]:"("+(i+1)+")";}

  function toast(msg){var w=document.getElementById("toastWrap"),e=document.createElement("div");e.className="toast";e.textContent=msg;w.appendChild(e);
    setTimeout(function(){e.classList.add("out");setTimeout(function(){e.remove();},320);},2100);}

  var overlay=document.getElementById("overlay"),modal=document.getElementById("modal");
  function closeModal(){overlay.classList.remove("on");}
  overlay.addEventListener("click",function(e){if(e.target===overlay)closeModal();});
  document.addEventListener("keydown",function(e){if(e.key==="Escape"){closeModal();closeDrawer();closeLightbox();closeCal();}});
  function confirmModal(o){modal.innerHTML='<h3>'+esc(o.title)+'</h3><p>'+esc(o.body)+'</p><div class="m-actions">'+
    '<button class="btn center" id="cC">취소</button><button class="btn center '+(o.danger?"danger":"primary")+'" id="cO">'+esc(o.ok||"확인")+'</button></div>';
    overlay.classList.add("on");document.getElementById("cC").onclick=closeModal;document.getElementById("cO").onclick=function(){closeModal();o.onOk&&o.onOk();};}

  function applyTheme(){var t=store.settings.theme==="dark"?"dark":"light";document.documentElement.setAttribute("data-theme",t);
    document.getElementById("themeBtn").textContent=t==="dark"?"☀️":"🌙";}
  document.getElementById("themeBtn").onclick=function(){store.settings.theme=store.settings.theme==="dark"?"light":"dark";applyTheme();markDirty();};

  function showHome(){var cur=currentId?getPlan(currentId):null;
    if(cur&&cur.draft&&planEmpty(cur))store.plans=store.plans.filter(function(x){return x.id!==cur.id;});
    document.getElementById("editorView").classList.remove("on");document.getElementById("homeView").style.display="flex";currentId=null;window.scrollTo({top:0,behavior:"smooth"});}
  document.getElementById("brandBtn").onclick=showHome;
  document.getElementById("drawerNew").onclick=function(){closeDrawer();showHome();};

  document.querySelectorAll(".choice").forEach(function(b){b.onclick=function(){createPlan(b.dataset.t);};});
  function createPlan(type){var p={id:uid(),type:type,theme:"",concept:"",dateSet:false,dY:"",dM:"",dD:"",captures:[],opening:"",closing:"",
    items:[{id:uid(),name:"",text:"",links:[]},{id:uid(),name:"",text:"",links:[]},{id:uid(),name:"",text:"",links:[]}],
    createdAt:Date.now(),updatedAt:Date.now(),scripted:false,draft:true};
    store.plans.push(p);markDirty();openEditor(p.id);}
  /* 저장 원칙: draft(초안)는 목록·클라우드에 없음. 저장을 눌러야 기록으로 승격, 빈 초안은 폐기 */
  function planEmpty(p){if((p.theme||"").trim()||(p.concept||"").trim()||(p.opening||"").trim()||(p.closing||"").trim())return false;
    if((p.captures||[]).length)return false;
    var e=true;(p.items||[]).forEach(function(it){if((it.name||"").trim()||(it.text||"").trim()||(it.links||[]).length)e=false;});
    return e;}

  /* editor */
  function openEditor(id){var p=getPlan(id);if(!p)return;currentId=id;
    document.getElementById("homeView").style.display="none";
    var ev=document.getElementById("editorView");ev.classList.add("on");ev.classList.toggle("routine-ctx",p.type==="routine");
    var tl=document.getElementById("typeLab");tl.className="type-lab "+p.type;tl.innerHTML='<span>'+TYPES[p.type].emo+'</span><span>'+TYPES[p.type].label+'</span>';
    var sb=document.getElementById("scriptedBtn");
    (function renderScripted(){sb.classList.toggle("on",!!p.scripted);sb.textContent=p.scripted?"🟡 대본화 완료":"◻️ 대본화 이전";})();
    sb.onclick=function(){p.scripted=!p.scripted;
      sb.classList.toggle("on",!!p.scripted);sb.textContent=p.scripted?"🟡 대본화 완료":"◻️ 대본화 이전";
      markDirty();toast(p.scripted?"🟡 대본화 완료로 표시했어요":"대본화 이전으로 되돌렸어요");};
    /* 유형 전환: 라벨을 누르면 제품추천 ↔ 관리루틴 이동 (내용 유지) */
    tl.style.cursor="pointer";tl.title="눌러서 "+(p.type==="product"?"관리루틴":"제품추천")+"(으)로 전환";
    tl.onclick=function(){var to=p.type==="product"?"routine":"product";
      confirmModal({title:TYPES[to].emo+" "+TYPES[to].label+"(으)로 전환할까요?",body:"작성한 내용은 그대로 유지됩니다.",ok:"전환",onOk:function(){
        p.type=to;markDirty();openEditor(p.id);toast(TYPES[to].label+"(으)로 전환했어요");}});};
    document.getElementById("edTheme").value=p.theme||"";
    var cc=document.getElementById("edConcept");cc.value=p.concept||"";autoGrow(cc);
    document.getElementById("itemsEmo").textContent=TYPES[p.type].secEmo;
    document.getElementById("itemsLab").textContent=TYPES[p.type].item;
    document.getElementById("addLabel").textContent=TYPES[p.type].add;
    document.getElementById("captureBlock").style.display=p.type==="routine"?"block":"none";
    renderDate(p);renderCaptures(p);
    var om=document.getElementById("edOpening");om.innerHTML="";om.appendChild(doodle(p.opening,"",function(v){p.opening=v;markDirty();}));
    var cm=document.getElementById("edClosing");cm.innerHTML="";cm.appendChild(doodle(p.closing,"",function(v){p.closing=v;markDirty();}));
    renderItems(p);window.scrollTo({top:0});}

  function autoGrow(ta){ta.style.height="auto";ta.style.height=ta.scrollHeight+"px";}
  document.getElementById("edTheme").addEventListener("input",function(e){var p=getPlan(currentId);if(!p)return;p.theme=e.target.value;markDirty();});
  document.getElementById("edConcept").addEventListener("input",function(e){var p=getPlan(currentId);if(!p)return;p.concept=e.target.value;autoGrow(e.target);markDirty();});

  /* ---- date: 미정 / YY_MM_DD stepper ---- */
  var pkOpen=false, pkStep="y", pkTmp={y:"",m:"",d:""};
  function renderDate(p){
    var none=document.getElementById("dbNone"), set=document.getElementById("dbSet");
    none.classList.toggle("on",!p.dateSet);
    set.classList.toggle("on",!!p.dateSet);
    set.textContent=dateLabel(p);
    if(!pkOpen)document.getElementById("pickerMount").innerHTML="";}
  document.getElementById("dbNone").onclick=function(){var p=getPlan(currentId);if(!p)return;
    p.dateSet=false;p.dY="";p.dM="";p.dD="";pkOpen=false;renderDate(p);markDirty();};
  document.getElementById("dbSet").onclick=function(){var p=getPlan(currentId);if(!p)return;
    pkOpen=!pkOpen;if(pkOpen){pkStep="y";pkTmp={y:p.dY||"",m:p.dM||"",d:p.dD||""};renderPicker(p);}else document.getElementById("pickerMount").innerHTML="";};
  function renderPicker(p){
    var mt=document.getElementById("pickerMount");
    var box=document.createElement("div");box.className="picker";
    var cur=(pkTmp.y?String(pkTmp.y).slice(-2):"YY")+"_"+(pkTmp.m||"MM")+"_"+(pkTmp.d||"DD");
    var head=document.createElement("div");head.className="pk-head";
    head.innerHTML='<span class="pk-step">'+(pkStep==="y"?"연도 선택":pkStep==="m"?"월 선택":"일 선택")+'</span><span class="pk-cur">'+cur+'</span>';
    box.appendChild(head);
    var grid=document.createElement("div");grid.className="pk-grid "+pkStep;
    if(pkStep==="y"){var base=new Date().getFullYear();
      for(var i=0;i<6;i++){(function(y){var c=cell(String(y).slice(-2),String(pkTmp.y)===String(y));
        c.onclick=function(){pkTmp.y=String(y);pkTmp.m="";pkTmp.d="";pkStep="m";renderPicker(p);};grid.appendChild(c);})(base+i-1);}}
    else if(pkStep==="m"){for(var m=1;m<=12;m++){(function(mm){var s=("0"+mm).slice(-2);var c=cell(s,pkTmp.m===s);
        c.onclick=function(){pkTmp.m=s;pkTmp.d="";pkStep="d";renderPicker(p);};grid.appendChild(c);})(m);}}
    else{var yy=parseInt(pkTmp.y,10),mo=parseInt(pkTmp.m,10);
      var days=new Date(yy,mo,0).getDate()||31, first=new Date(yy,mo-1,1).getDay();
      var mh=document.createElement("div");mh.className="pk-month";mh.textContent=yy+"년 "+mo+"월";box.appendChild(mh);
      var wk=document.createElement("div");wk.className="pk-grid d pk-week";
      ["일","월","화","수","목","금","토"].forEach(function(w,i){var s=document.createElement("span");s.textContent=w;if(i===0)s.className="sun";wk.appendChild(s);});
      box.appendChild(wk);
      for(var b=0;b<first;b++){var bl=document.createElement("span");bl.className="pk-cell blank";grid.appendChild(bl);}
      for(var d=1;d<=days;d++){(function(dd){var s=("0"+dd).slice(-2);var c=cell(String(dd),pkTmp.d===s);
        c.onclick=function(){pkTmp.d=s;commit(p,true);};grid.appendChild(c);})(d);}}
    box.appendChild(grid);
    var foot=document.createElement("div");foot.className="pk-foot";
    if(pkStep!=="y"){var back=document.createElement("button");back.textContent="← 이전";
      back.onclick=function(){pkStep=pkStep==="d"?"m":"y";renderPicker(p);};foot.appendChild(back);}
    if(pkStep==="m"&&pkTmp.m){var skip=document.createElement("button");skip.className="done";skip.textContent="월까지만 저장";
      skip.onclick=function(){pkTmp.d="";commit(p,true);};foot.appendChild(skip);
      var next=document.createElement("button");next.textContent="일 선택 →";next.onclick=function(){pkStep="d";renderPicker(p);};foot.appendChild(next);}
    if(pkStep==="d"){var save=document.createElement("button");save.className="done";save.textContent="저장";
      save.onclick=function(){commit(p,true);};foot.appendChild(save);}
    if(foot.children.length)box.appendChild(foot);
    mt.innerHTML="";mt.appendChild(box);}
  function cell(txt,sel){var b=document.createElement("button");b.className="pk-cell"+(sel?" sel":"");b.textContent=txt;return b;}
  function commit(p,close){p.dY=pkTmp.y;p.dM=pkTmp.m;p.dD=pkTmp.d;p.dateSet=!!p.dY;
    if(close){pkOpen=false;document.getElementById("pickerMount").innerHTML="";}
    renderDate(p);markDirty();}

  /* captures — 참조는 동기화, 이미지는 IndexedDB 캐시 + 클라우드 파일 */
  function renderCaptures(p){if(p.type!=="routine")return;var z=document.getElementById("capZone");z.innerHTML="";
    (p.captures||[]).forEach(function(c,i){var t=document.createElement("div");t.className="cap-thumb";
      var img=document.createElement("img");img.alt="캡처본";
      if(typeof c==="string"){img.src=c;img.onclick=function(){openLightbox(c);};}
      else getCap(c,function(u){if(u){img.src=u;img.onclick=function(){openLightbox(u);};}
        else{img.alt="☁️ 불러오는 중 — 동기화 연결·인터넷을 확인하세요";img.title=img.alt;}});
      var del=document.createElement("button");del.className="cap-del";del.textContent="✕";
      del.onclick=function(e){e.stopPropagation();
        var rm=p.captures.splice(i,1)[0];
        if(rm&&typeof rm==="object"){delete capMem[rm.id];idbDel("cap:"+rm.id).catch(function(){});if(rm.up)delCapRemote(rm.id);}
        renderCaptures(p);markDirty();};
      t.appendChild(img);t.appendChild(del);z.appendChild(t);});
    var add=document.createElement("button");add.className="cap-add";add.innerHTML='<span class="pl">＋</span>캡처 추가';
    add.onclick=function(){document.getElementById("capInput").click();};z.appendChild(add);}
  document.getElementById("capInput").addEventListener("change",function(e){var p=getPlan(currentId);if(!p)return;
    var files=Array.prototype.slice.call(e.target.files);e.target.value="";if(!p.captures)p.captures=[];
    var chain=Promise.resolve();
    files.forEach(function(f){if(f.type.indexOf("image")!==0)return;
      chain=chain.then(function(){return resizeImg(f).then(function(u){
        var cid=uid();capMem[cid]=u;p.captures.push({id:cid,up:false});
        return idbSet("cap:"+cid,u).catch(function(){});});});});
    chain.then(function(){renderCaptures(p);markDirty();});});
  /* 기록 원칙: 저장 버튼을 누르기 전에는 어떤 것도 클라우드·기기 원장에 기록되지 않는다 (캡처 업로드도 저장 시점) */
  function resizeImg(file){return new Promise(function(res){var r=new FileReader();
    r.onload=function(){var img=new Image();img.onload=function(){var w=img.width,h=img.height,mx=1080;if(w>mx){h=Math.round(h*mx/w);w=mx;}
      var c=document.createElement("canvas");c.width=w;c.height=h;c.getContext("2d").drawImage(img,0,0,w,h);
      try{res(c.toDataURL("image/jpeg",.72));}catch(e){res(r.result);}};img.onerror=function(){res(r.result);};img.src=r.result;};r.readAsDataURL(file);});}

  var lb=document.getElementById("lightbox"),lbImg=document.getElementById("lightboxImg");
  function openLightbox(s){lbImg.src=s;lb.classList.add("on");}function closeLightbox(){lb.classList.remove("on");}lb.onclick=closeLightbox;

  /* doodle */
  function doodle(val,ph,onChange){var w=document.createElement("div");w.className="doodle";
    var back=document.createElement("div");back.className="doodle-back";back.setAttribute("aria-hidden","true");
    var ta=document.createElement("textarea");ta.className="doodle-in";ta.value=val||"";ta.placeholder=ph||"";
    w.appendChild(back);w.appendChild(ta);
    function sync(){back.innerHTML=hi(ta.value);ta.style.height="auto";ta.style.height=ta.scrollHeight+"px";}
    ta.addEventListener("input",function(){sync();onChange(ta.value);});
    ta.addEventListener("focus",function(){w.classList.add("focused");});
    ta.addEventListener("blur",function(){w.classList.remove("focused");});
    requestAnimationFrame(sync);w._sync=sync;return w;}

  /* items: 명 + 태그 + 링크 + 내용 (한 카드 = 함께 이동) */
  function renderItems(p){var box=document.getElementById("edItems");box.innerHTML="";
    p.items.forEach(function(it,idx){box.appendChild(itemCard(p,it,idx,box));});}
  function itemCard(p,it,idx,box){
    var card=document.createElement("div");card.className="item";card.dataset.id=it.id;
    var head=document.createElement("div");head.className="item-head";
    var no=document.createElement("span");no.className="item-no";no.textContent=numOf(idx);head.appendChild(no);
    var nm=document.createElement("input");nm.className="name-in";nm.value=it.name||"";
    nm.placeholder=(p.type==="product"?"제품명":"루틴명");
    var tagBox=document.createElement("div");tagBox.className="item-tags";
    function renderTags(){var tags=tagsIn((it.name||"")+" "+(it.text||""));tagBox.innerHTML="";
      if(tags.length===0){var e=document.createElement("span");e.className="it-empty";e.textContent="#태그를 쓰면 여기에 모입니다";tagBox.appendChild(e);return;}
      tags.forEach(function(t){var c=document.createElement("span");c.className="it-tag";c.textContent=t;c.title="클릭해 복사";
        c.onclick=function(){copyText(t,"‘"+t+"’ 복사됨");};tagBox.appendChild(c);});}
    nm.addEventListener("input",function(){it.name=nm.value;renderTags();markDirty();});
    head.appendChild(nm);
    var tools=document.createElement("div");tools.className="item-tools";
    var grab=tbtn("⠿","끌어서 순서 이동");grab.classList.add("grab");
    var del=tbtn("✕","삭제");del.classList.add("del");del.onclick=function(){delItem(p,it.id);};
    tools.appendChild(grab);tools.appendChild(del);head.appendChild(tools);
    card.appendChild(head);
    card.appendChild(tagBox);
    if(p.type==="product")card.appendChild(linksBlock(p,it));
    card.appendChild(doodle(it.text,"",function(v){it.text=v;renderTags();markDirty();}));
    renderTags();
    enableDrag(card,grab,p,box);
    return card;}
  function tbtn(t,title){var b=document.createElement("button");b.className="tool";b.textContent=t;b.title=title;b.setAttribute("aria-label",title);return b;}
  function delItem(p,id){if(p.items.length<=1){toast("최소 1개는 남겨두세요");return;}
    confirmModal({title:"이 항목을 삭제할까요?",body:"작성한 내용이 함께 사라집니다.",ok:"삭제",danger:true,onOk:function(){
      p.items=p.items.filter(function(i){return i.id!==id;});renderItems(p);markDirty();toast("삭제했습니다");}});}
  document.getElementById("addItem").onclick=function(){var p=getPlan(currentId);if(!p)return;
    p.items.push({id:uid(),name:"",text:"",links:[]});renderItems(p);markDirty();
    var box=document.getElementById("edItems"),last=box.lastElementChild;if(last){last.scrollIntoView({behavior:"smooth",block:"center"});var n=last.querySelector(".name-in");if(n)n.focus();}};

  /* youtube links: 한 줄씩 + 로 추가, 클릭 시 연동 */
  function ytId(u){var m=String(u).match(/(?:youtu\.be\/|youtube\.com\/(?:watch\?v=|embed\/|shorts\/|v\/))([\w-]{11})/);return m?m[1]:null;}
  function linksBlock(p,it){var box=document.createElement("div");box.className="links";
    function render(){box.innerHTML="";
      (it.links||[]).forEach(function(link,i){var id=ytId(link);
        var a=document.createElement("a");a.className="link-chip";a.href=link;a.target="_blank";a.rel="noopener";
        if(id){var im=document.createElement("img");im.className="thumb";im.src="https://img.youtube.com/vi/"+id+"/mqdefault.jpg";im.alt="";a.appendChild(im);}
        else{var ph=document.createElement("span");ph.className="ph";ph.textContent="▶";a.appendChild(ph);}
        var u=document.createElement("span");u.className="u";u.textContent=link;a.appendChild(u);
        var x=document.createElement("button");x.className="lx";x.textContent="✕";x.title="링크 삭제";
        x.onclick=function(e){e.preventDefault();e.stopPropagation();it.links.splice(i,1);render();markDirty();};
        a.appendChild(x);box.appendChild(a);});
      var add=document.createElement("button");add.className="link-add";add.textContent="＋ 유튜브 링크";
      add.onclick=function(){var ed=document.createElement("div");ed.className="link-edit";
        var inp=document.createElement("input");inp.type="url";inp.placeholder="https://youtu.be/...";
        var ok=document.createElement("button");ok.textContent="추가";
        function save(){var v=inp.value.trim();if(v){if(!it.links)it.links=[];it.links.push(v);markDirty();}render();}
        ok.onclick=save;inp.addEventListener("keydown",function(e){if(e.key==="Enter")save();if(e.key==="Escape")render();});
        ed.appendChild(inp);ed.appendChild(ok);
        box.replaceChild(ed,add);inp.focus();};
      box.appendChild(add);}
    render();return box;}

  /* fluid drag: 카드 전체(명+태그+링크+내용)가 함께 이동, 놓으면 번호 자동 갱신 */
  function enableDrag(card,handle,p,box){
    handle.addEventListener("pointerdown",function(e){e.preventDefault();
      var pid=e.pointerId;
      card.classList.add("dragging");document.body.style.userSelect="none";
      try{handle.setPointerCapture(pid);}catch(x){}
      /* 이동·놓기 감지를 손잡이가 아니라 문서 전체에 걸어야 손을 빨리 움직여도 안 끊긴다 */
      function onMove(ev){if(ev.pointerId!==pid)return;if(ev.cancelable)ev.preventDefault();
        var after=getAfter(box,ev.clientY);if(after==null)box.appendChild(card);else box.insertBefore(card,after);
        var vh=window.innerHeight; /* 화면 가장자리에 닿으면 자동 스크롤 */
        if(ev.clientY<80)window.scrollBy(0,-11);else if(ev.clientY>vh-80)window.scrollBy(0,11);}
      function onUp(ev){if(ev.pointerId!==pid)return;
        document.removeEventListener("pointermove",onMove);document.removeEventListener("pointerup",onUp);document.removeEventListener("pointercancel",onUp);
        card.classList.remove("dragging");document.body.style.userSelect="";
        syncOrder(p,box);renderItems(p);markDirty();}
      document.addEventListener("pointermove",onMove,{passive:false});
      document.addEventListener("pointerup",onUp);document.addEventListener("pointercancel",onUp);});}
  function getAfter(box,y){var els=Array.prototype.slice.call(box.querySelectorAll(".item:not(.dragging)"));var best={d:-Infinity,el:null};
    els.forEach(function(el){var b=el.getBoundingClientRect();var off=y-(b.top+b.height/2);if(off<0&&off>best.d)best={d:off,el:el};});return best.el;}
  function syncOrder(p,box){var ids=Array.prototype.slice.call(box.querySelectorAll(".item")).map(function(el){return el.dataset.id;});
    p.items.sort(function(a,b){return ids.indexOf(a.id)-ids.indexOf(b.id);});}

  function copyText(txt,ok){if(navigator.clipboard&&navigator.clipboard.writeText)navigator.clipboard.writeText(txt).then(function(){toast(ok);},function(){fb(txt,ok);});else fb(txt,ok);}
  function fb(txt,ok){var t=document.createElement("textarea");t.value=txt;t.style.position="fixed";t.style.opacity="0";document.body.appendChild(t);t.select();
    try{document.execCommand("copy");toast(ok);}catch(e){toast("복사 실패");}t.remove();}

  document.getElementById("saveBtn").onclick=function(){if(persist())toast("저장 완료 · "+fmtSaved(store.lastSaved));};

  /* drawer: click = open, dblclick = delete */
  var drawer=document.getElementById("drawer"),scrim=document.getElementById("scrim");
  function openDrawer(){renderDrawer();drawer.classList.add("on");scrim.classList.add("on");}
  function closeDrawer(){drawer.classList.remove("on");scrim.classList.remove("on");}
  document.getElementById("listBtn").onclick=openDrawer;document.getElementById("drawerX").onclick=closeDrawer;scrim.onclick=closeDrawer;

  /* 📅 월간 캘린더: 화면을 채우는 고정 그리드 + 날짜 탭 시 시트가 올라옴 */
  var calY=0,calM=0,calSelD=0,CAL_MAX=5; /* 셀에 표시할 최대 칩 수 */
  function cel(t,c){var e=document.createElement(t);e.className=c;return e;}
  function openCal(){closeDrawer();var n=new Date();if(!calY){calY=n.getFullYear();calM=n.getMonth()+1;}calSelD=0;closeSheet();renderCal();document.getElementById("calView").hidden=false;}
  function closeCal(){document.getElementById("calView").hidden=true;closeSheet();}
  function calShift(k){calM+=k;if(calM<1){calM=12;calY--;}if(calM>12){calM=1;calY++;}calSelD=0;closeSheet();renderCal();}
  function renderCal(){
    document.getElementById("calTitle").textContent=calY+"년 "+calM+"월";
    var g=document.getElementById("calGrid");g.innerHTML="";
    var days=new Date(calY,calM,0).getDate(), first=new Date(calY,calM-1,1).getDay();
    var byDay={},noDay=[];
    store.plans.forEach(function(p){if(p.draft||!p.dateSet)return;
      if(parseInt(p.dY,10)!==calY||parseInt(p.dM,10)!==calM)return;
      var d=parseInt(p.dD,10);if(d)(byDay[d]=byDay[d]||[]).push(p);else noDay.push(p);});
    /* 범례 + (있으면) 일자 미정 버튼 */
    var lg=document.getElementById("calLegend");
    lg.innerHTML='<span><i style="background:var(--sage)"></i>관리루틴</span><span><i style="background:var(--plum)"></i>제품추천</span>';
    if(noDay.length){var ub=cel("button","cal-undated");ub.textContent="📌 일자 미정 "+noDay.length;ub.onclick=function(){calSelD=0;openSheet(0,noDay);};lg.appendChild(ub);}
    for(var b=0;b<first;b++)g.appendChild(cel("span","cal-cell blank"));
    var now=new Date();
    for(var d=1;d<=days;d++){(function(dd){
      var c=cel("button","cal-cell");
      if(now.getFullYear()===calY&&now.getMonth()+1===calM&&now.getDate()===dd)c.classList.add("today");
      if(calSelD===dd)c.classList.add("sel");
      var n=cel("span","cd"+(((first+dd-1)%7===0)?" sun":""));n.textContent=dd;c.appendChild(n);
      var recs=byDay[dd]||[];
      recs.slice(0,CAL_MAX).forEach(function(p){var ch=cel("span","cal-chip "+p.type);
        ch.textContent=(p.theme||"").trim()||TYPES[p.type].label;c.appendChild(ch);});
      if(recs.length>CAL_MAX){var mo2=cel("span","cal-more");mo2.textContent="+"+(recs.length-CAL_MAX);c.appendChild(mo2);}
      c.onclick=function(){calSelD=dd;renderCal();openSheet(dd,byDay[dd]||[]);};
      g.appendChild(c);})(d);}
    /* 마지막 주 빈칸 채워 가로선 완성 */
    var trail=(7-(first+days)%7)%7;for(var t=0;t<trail;t++)g.appendChild(cel("span","cal-cell blank"));}
  function openSheet(dd,list){renderSheet(dd,list);
    document.getElementById("calDay").classList.add("on");document.getElementById("calSheetBg").classList.add("on");}
  function closeSheet(){document.getElementById("calDay").classList.remove("on");document.getElementById("calSheetBg").classList.remove("on");}
  var WD=["일","월","화","수","목","금","토"];
  function renderSheet(dd,list){
    var cd=document.getElementById("calDay");cd.innerHTML="";
    var h=cel("div","cal-day-h");
    h.textContent=dd?(calM+"월 "+dd+"일 "+WD[new Date(calY,calM-1,dd).getDay()]+"요일"):"📌 일자 미정 (월만 지정된 기록)";cd.appendChild(h);
    list.forEach(function(p){var e=cel("button","cal-rec "+p.type);
      e.innerHTML='<span>'+TYPES[p.type].emo+'</span><span class="nm">'+esc((p.theme||"").trim()||"(제목 없음)")+'</span>'+(p.scripted?'<span title="대본화 완료">🟡</span>':'');
      e.onclick=function(){closeCal();openEditor(p.id);};cd.appendChild(e);});
    if(dd){var row=cel("div","cal-add-row");
      [["routine","🧖🏻‍♀️ 관리루틴"],["product","👩🏻‍🏫 제품추천"]].forEach(function(t){
        var b=cel("button","cal-add "+t[0]);b.textContent="＋ "+t[1];
        b.onclick=function(){closeCal();createPlan(t[0]);
          var p=getPlan(currentId);if(p){p.dY=String(calY);p.dM=("0"+calM).slice(-2);p.dD=("0"+dd).slice(-2);p.dateSet=true;renderDate(p);markDirty();}};
        row.appendChild(b);});
      cd.appendChild(row);}}
  document.getElementById("calBtn").onclick=openCal;
  document.getElementById("calX").onclick=closeCal;
  document.getElementById("calSheetBg").onclick=closeSheet;
  document.getElementById("calPrev").onclick=function(){calShift(-1);};
  document.getElementById("calNext").onclick=function(){calShift(1);};
  var searchQ="";
  var searchIn=document.getElementById("searchIn"), searchBox=document.querySelector(".drawer-search");
  searchIn.addEventListener("input",function(){searchQ=searchIn.value.trim();searchBox.classList.toggle("has",!!searchQ);renderDrawer();});
  document.getElementById("searchX").onclick=function(){searchIn.value="";searchQ="";searchBox.classList.remove("has");renderDrawer();searchIn.focus();};

  /* 검색: 제목·컨셉·태그·오프닝·항목명·내용·마무리 전체에서 찾음 */
  function haystack(p){var s=[p.theme||"",p.concept||"",p.opening||"",p.closing||""];
    (p.items||[]).forEach(function(it){s.push(it.name||"");s.push(it.text||"");});return s.join("  ");}
  function matches(p,q){return haystack(p).toLowerCase().indexOf(q.toLowerCase())>=0;}
  function snippet(p,q){var hay=haystack(p),i=hay.toLowerCase().indexOf(q.toLowerCase());if(i<0)return "";
    var st=Math.max(0,i-14),txt=hay.slice(st,i+q.length+34).replace(/\s+/g," ").trim();
    var rel=hay.slice(st,i+q.length+34).replace(/\s+/g," ").trim();
    var pos=rel.toLowerCase().indexOf(q.toLowerCase());
    if(pos<0)return esc(rel);
    return (st>0?"…":"")+esc(rel.slice(0,pos))+'<span class="hit">'+esc(rel.slice(pos,pos+q.length))+'</span>'+esc(rel.slice(pos+q.length))+"…";}

  function renderDrawer(){var body=document.getElementById("drawerBody");
    var vis=store.plans.filter(function(p){return !p.draft;}); /* 저장된 기록만 목록에 */
    if(vis.length===0){body.innerHTML='<div class="drawer-empty">아직 기록이 없어요.</div>';return;}
    var list=searchQ?vis.filter(function(p){return matches(p,searchQ);}):vis.slice();
    if(list.length===0){body.innerHTML='<div class="search-none">‘'+esc(searchQ)+'’와 관련된 기록이 없어요.</div>';return;}
    var groups={},order=[];list.forEach(function(p){var k=monthKey(p);if(!groups[k]){groups[k]=[];order.push(k);}groups[k].push(p);});
    order.sort(function(a,b){if(a==="")return 1;if(b==="")return -1;return a<b?-1:1;});
    body.innerHTML="";
    order.forEach(function(k){var g=document.createElement("div");g.className="month-grp";
      var label=k===""?"미정":(function(){var s=k.split("-");return s[1]==="00"?s[0]+"년":s[0]+"년 "+parseInt(s[1],10)+"월";})();
      var h=document.createElement("div");h.className="month-h";h.textContent=label;g.appendChild(h);
      groups[k].slice().sort(function(a,b){return (a.theme||"제목 없음").localeCompare(b.theme||"제목 없음","ko");}).forEach(function(p){
        var e=document.createElement("div");e.className="entry";
        var snip=searchQ?snippet(p,searchQ):"";
        e.innerHTML='<span class="dot '+p.type+'"></span><span class="entry-main"><span class="nm'+(p.theme?"":" empty")+'">'+(p.theme?esc(p.theme):"제목 없음")+'</span>'+
          (snip?'<span class="entry-snip">'+snip+'</span>':'')+'</span>'+(p.scripted?'<span class="done" title="대본화 완료">🟡</span>':'')+'<span class="ty">'+TYPES[p.type].emo+'</span>';
        var timer=null;
        e.addEventListener("click",function(){if(timer)return;timer=setTimeout(function(){timer=null;closeDrawer();openEditor(p.id);},230);});
        e.addEventListener("dblclick",function(){if(timer){clearTimeout(timer);timer=null;}
          confirmModal({title:"이 기록을 삭제할까요?",body:"‘"+(p.theme||"제목 없음")+"’ 기록이 모든 기기에서 삭제되며 되돌릴 수 없습니다.",ok:"삭제",danger:true,onOk:function(){
            store.plans=store.plans.filter(function(x){return x.id!==p.id;});
            (store.deleted=store.deleted||[]).push({id:p.id,ts:Date.now()});
            if(currentId===p.id)showHome();
            markDirty();renderDrawer();toast("기록을 삭제했습니다");}});});
        g.appendChild(e);});
      body.appendChild(g);});}

  /* backup */
  document.getElementById("backupBtn").onclick=function(){
    modal.innerHTML='<h3>백업 &amp; 데이터</h3>'+
      '<div class="m-list">'+
        '<button class="btn" id="bSync"><span>☁️ 클라우드 동기화</span><span class="sub">'+(ghReady()?("연결됨 · "+esc(gh.owner+"/"+gh.repo)):"기기 연결")+'</span></button>'+
        '<button class="btn" id="bExport"><span>📱 백업 내보내기</span><span class="sub">파일 저장</span></button>'+
        '<button class="btn" id="bImport"><span>📲 백업 불러오기</span><span class="sub">파일 업뎃</span></button>'+
      '</div><div class="m-actions"><button class="btn center" id="bClose">닫기</button></div>';
    overlay.classList.add("on");
    document.getElementById("bSync").onclick=function(){closeModal();syncModal();};
    document.getElementById("bExport").onclick=function(){closeModal();exportData();};
    document.getElementById("bImport").onclick=function(){closeModal();document.getElementById("importFile").click();};
    document.getElementById("bClose").onclick=closeModal;};
  function exportData(){var blob=new Blob([JSON.stringify(store,null,2)],{type:"application/json"});var url=URL.createObjectURL(blob);
    var a=document.createElement("a"),t=new Date(),ds=t.getFullYear()+("0"+(t.getMonth()+1)).slice(-2)+("0"+t.getDate()).slice(-2);
    a.href=url;a.download="영감의샘터_"+ds+".json";a.click();setTimeout(function(){URL.revokeObjectURL(url);},500);toast("백업 파일을 내보냈어요");}
  document.getElementById("importFile").addEventListener("change",function(e){var f=e.target.files[0];if(!f)return;var r=new FileReader();
    r.onload=function(){try{var d=JSON.parse(r.result);if(!d||!Array.isArray(d.plans))throw 0;
      confirmModal({title:"불러온 데이터로 덮어쓸까요?",body:"기록 "+d.plans.length+"건을 불러오며 현재 데이터는 대체됩니다.",ok:"불러오기",onOk:function(){
        store.plans=d.plans;load2();persist();showHome();toast("데이터를 불러왔어요");}});}
      catch(x){toast("올바른 백업 파일이 아니에요");}};r.readAsText(f);e.target.value="";});
  function load2(){if(!Array.isArray(store.deleted))store.deleted=[];
    store.plans.forEach(function(p){if(!Array.isArray(p.captures))p.captures=[];if(p.concept==null)p.concept="";
    if(p.dY===undefined){p.dY="";p.dM="";p.dD="";}p.dateSet=!!p.dY;
    p.scripted=!!p.scripted;if(!p.updatedAt)p.updatedAt=p.createdAt||Date.now();
    (p.items||[]).forEach(function(it){if(it.name==null)it.name="";if(!Array.isArray(it.links))it.links=it.link?[it.link]:[];});});}

  /* folder auto-save */
  function idb(mode,fn){return new Promise(function(res,rej){if(!window.indexedDB){rej();return;}var o=indexedDB.open("samteo",1);
    o.onupgradeneeded=function(){o.result.createObjectStore("kv");};o.onsuccess=function(){var db=o.result,t=db.transaction("kv",mode);fn(t.objectStore("kv"),res,rej);};o.onerror=function(){rej();};});}
  function idbSet(k,v){return idb("readwrite",function(s,res){s.put(v,k);res();});}
  function idbGet(k){return idb("readonly",function(s,res){var r=s.get(k);r.onsuccess=function(){res(r.result);};});}
  function idbDel(k){return idb("readwrite",function(s,res){s.delete(k);res();});}
  function connectFolder(){if(!window.showDirectoryPicker){toast("이 브라우저는 폴더 연결을 지원하지 않아요");return;}
    window.showDirectoryPicker({mode:"readwrite"}).then(function(h){dirHandle=h;idbSet("dir",h);store.settings.folder=true;persist();toast("폴더 연결 완료 · 저장하면 자동 백업됩니다");}).catch(function(){});}
  function writeFolder(){if(!dirHandle)return;
    (dirHandle.queryPermission?dirHandle.queryPermission({mode:"readwrite"}):Promise.resolve("granted")).then(function(pm){
      if(pm==="granted")return "granted";if(dirHandle.requestPermission)return dirHandle.requestPermission({mode:"readwrite"});return "denied";}).then(function(pm){
      if(pm!=="granted")return;dirHandle.getFileHandle("영감의샘터.json",{create:true}).then(function(fh){return fh.createWritable();}).then(function(w){
        return w.write(JSON.stringify(store,null,2)).then(function(){return w.close();});}).catch(function(){});}).catch(function(){});}

  load();applyTheme();updateSaveUI();
  if(store.settings.folder&&window.showDirectoryPicker){idbGet("dir").then(function(h){if(h)dirHandle=h;}).catch(function(){});}
  showHome();
  if(!storageOK)setTimeout(function(){toast("이 환경은 저장이 제한돼요. 파일을 내려받아 브라우저에서 열어주세요");},800);
  /* ☁️ 시작·복귀·온라인 전환 시 클라우드와 합치기 */
  cloudPull();
  window.addEventListener("online",function(){cloudPull();});
  document.addEventListener("visibilitychange",function(){if(!document.hidden)cloudPull();});
  /* 저장 안 한 변경이 있으면 닫기 전에 경고 (저장 버튼 원칙의 안전망) */
  window.addEventListener("beforeunload",function(e){if(dirty){e.preventDefault();e.returnValue="";}});
})();
</script>
</body>
</html>
