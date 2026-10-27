<!doctype html>
<html lang="en"><head><meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<title>EduFlow – Learning App</title>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@500;700&family=Literata:wght@400;600&display=swap" rel="stylesheet">
<style>
:root{--bg:#f2f6f7;--sf:#fff;--ink:#10222b;--mu:#5b6e77;--ln:#d6e1e5;--pr:#0f766e;--pt:#fff;--ac:#e8a33d;--ok:#2f8f4e;--bad:#c2410c;color-scheme:light;box-sizing:border-box;padding-top:env(safe-area-inset-top,0px);padding-bottom:env(safe-area-inset-bottom,0px)}
@media (prefers-color-scheme:dark){:root:not([data-theme="light"]){--bg:#0c181d;--sf:#14262d;--ink:#e6f0f2;--mu:#93a9b1;--ln:#26404a;--pr:#34c3b3;--pt:#06201d;--ac:#f0b85a;--ok:#5ac07c;--bad:#f08a5d;color-scheme:dark}}
:root[data-theme="dark"]{--bg:#0c181d;--sf:#14262d;--ink:#e6f0f2;--mu:#93a9b1;--ln:#26404a;--pr:#34c3b3;--pt:#06201d;--ac:#f0b85a;--ok:#5ac07c;--bad:#f08a5d;color-scheme:dark}
*{box-sizing:border-box}html,body{margin:0}
body{background:var(--bg);color:var(--ink);font:16px/1.6 'Literata',Georgia,serif}
h1,h2,h3,.b{font-family:'Bricolage Grotesque',system-ui,sans-serif;line-height:1.2;margin:0 0 .5em}
button,input,select,textarea{font:inherit;color:inherit}
.w{max-width:1040px;margin:0 auto;padding:16px}
nav{display:flex;flex-wrap:wrap;gap:6px;align-items:center;padding:10px 16px;background:var(--sf);border-bottom:1px solid var(--ln);position:sticky;top:env(safe-area-inset-top,0px);z-index:5}
nav .logo{font:700 22px 'Bricolage Grotesque',system-ui,sans-serif;margin-right:auto;color:var(--pr)}
.btn{border:1px solid var(--ln);background:var(--sf);padding:8px 14px;border-radius:8px;cursor:pointer}
.btn:hover{border-color:var(--pr)}.btn:focus-visible,input:focus-visible,select:focus-visible,textarea:focus-visible{outline:3px solid var(--ac);outline-offset:1px}
.btn.on{background:var(--pr);color:var(--pt);border-color:var(--pr)}
.btn.p{background:var(--pr);color:var(--pt);border-color:var(--pr)}
.grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:16px}
.card{background:var(--sf);border:1px solid var(--ln);border-radius:12px;padding:16px}
.tag{display:inline-block;font-size:13px;color:var(--mu);margin-right:10px}
.bar{height:8px;background:var(--ln);border-radius:4px;overflow:hidden;margin:8px 0}.bar i{display:block;height:100%;background:var(--pr)}
.row{display:flex;gap:10px;flex-wrap:wrap;align-items:center}
.row.sp{justify-content:space-between}
input,select,textarea{background:var(--sf);border:1px solid var(--ln);border-radius:8px;padding:9px 12px;width:100%}
.f{display:flex;gap:10px;flex-wrap:wrap;margin:12px 0}.f>*{flex:1 1 180px}
.lay{display:grid;grid-template-columns:260px 1fr;gap:16px}
@media(max-width:760px){.lay{grid-template-columns:1fr}}
.les{display:block;width:100%;text-align:left;margin-bottom:6px}
.les.done::before{content:"✓ ";color:var(--ok)}
.opt{display:block;padding:8px 12px;border:1px solid var(--ln);border-radius:8px;margin:6px 0;cursor:pointer}
.opt.ok{border-color:var(--ok)}.opt.no{border-color:var(--bad)}
.stat{font:700 30px 'Bricolage Grotesque',system-ui,sans-serif;color:var(--pr)}
.badge{display:inline-block;padding:6px 12px;border:1px dashed var(--ln);border-radius:20px;margin:4px;color:var(--mu)}.badge.got{border:1px solid var(--ac);color:var(--ink);background:color-mix(in srgb,var(--ac) 20%,transparent)}
.cert{border:6px double var(--ac);padding:40px 20px;text-align:center;background:var(--sf);border-radius:6px}
.mu{color:var(--mu)}.bm{background:none;border:0;cursor:pointer;font-size:20px;color:var(--ac)}
#toast{position:fixed;bottom:calc(20px + env(safe-area-inset-bottom,0px));left:50%;transform:translateX(-50%);background:var(--ink);color:var(--bg);padding:10px 18px;border-radius:8px;display:none;z-index:9}
@media print{nav,.noprint{display:none!important}}
</style></head>
<body><div id="app"></div><div id="toast" role="status"></div>
<script>
const C=[
{id:"web",t:"Web Basics: HTML & CSS",cat:"Development",lv:"Beginner",min:90,by:"Anika Rao",d:"Build and style your first web pages from scratch.",
L:[["How the web works","A browser requests a page from a server, then reads the HTML to build what you see. HTML gives structure, CSS gives style, and JavaScript adds behavior."],["Structuring with HTML","Use headings, paragraphs, lists and links to describe your content. Semantic tags such as header, main and footer help both people and search engines."],["Styling with CSS","CSS selects elements and sets properties like color and spacing. Flexbox and grid are the modern tools for laying out a page."]],
Q:[["Which language gives a web page its structure?",["CSS","HTML","SQL"],1],["Which CSS feature lays out items in rows or columns?",["Flexbox","Alt text","Cookies"],0]]},
{id:"js",t:"JavaScript Essentials",cat:"Development",lv:"Intermediate",min:120,by:"Dev Malhotra",d:"Variables, functions and the DOM, taught with small projects.",
L:[["Values and variables","Use let and const to store values. Numbers, strings, booleans, arrays and objects are the building blocks of every program."],["Functions and scope","A function packages reusable logic. Variables declared inside a function stay inside it, which keeps programs predictable."],["Working with the DOM","The DOM is the live tree of your page. Select an element, listen for a click, then change its text or style in response."]],
Q:[["Which keyword declares a value that cannot be reassigned?",["var","const","new"],1],["What does the DOM represent?",["The page as a tree of elements","A database","A CSS file"],0]]},
{id:"data",t:"Data Skills with Spreadsheets",cat:"Data",lv:"Beginner",min:75,by:"Meera Iyer",d:"Clean, summarize and chart data without writing code.",
L:[["Tidy data","Keep one record per row and one variable per column. Tidy tables are easy to sort, filter and summarize."],["Formulas that matter","SUM, AVERAGE, COUNTIF and lookup formulas answer most everyday questions about a table."],["Charts that communicate","Pick a bar chart to compare categories and a line chart to show change over time. Label axes and remove clutter."]],
Q:[["A line chart is best for showing…",["Change over time","Parts of a whole","Names"],0],["In tidy data each row holds…",["One record","One column name","A whole report"],0]]},
{id:"sci",t:"Study Smarter: Learning Science",cat:"Skills",lv:"Beginner",min:60,by:"Dr. Lena Fischer",d:"Evidence-based habits for remembering more in less time.",
L:[["Retrieval practice","Testing yourself beats rereading. Closing the book and recalling what you can strengthens memory."],["Spaced repetition","Review material at growing intervals, such as 1, 3, 7 and 21 days, to move it into long-term memory."],["Focus and rest","Work in focused blocks of 25 to 50 minutes, then rest. Sleep is when much of the learning is consolidated."]],
Q:[["Which habit boosts memory most?",["Rereading notes","Self-testing","Highlighting"],1],["Spaced repetition means reviewing…",["At growing intervals","All at once","Only before exams"],0]]},
{id:"py",t:"Python for Problem Solving",cat:"Development",lv:"Intermediate",min:150,by:"Sam Okafor",d:"Think in code: loops, lists and functions applied to real puzzles.",
L:[["Loops and conditions","Use if to choose a path and for or while to repeat work. Most puzzles reduce to a loop with a condition."],["Lists and dictionaries","Lists hold ordered items and dictionaries map keys to values. Choosing the right one makes code shorter and faster."],["Writing helper functions","Break a big problem into small named functions. Each one should do a single job and be easy to test."]],
Q:[["Which structure maps keys to values?",["List","Dictionary","Loop"],1],["Good functions should…",["Do one job","Do everything","Avoid names"],0]]},
{id:"com",t:"Clear Communication at Work",cat:"Skills",lv:"Beginner",min:55,by:"Priya Nair",d:"Write and speak so people act on what you say.",
L:[["Lead with the point","State your conclusion or request first, then give the reasons. Busy readers decide in the first two lines."],["Plain writing","Prefer short sentences and common words. Cut filler and replace vague terms with specific facts."],["Giving feedback","Describe what you observed, explain its effect and suggest a next step. Keep it about the work, not the person."]],
Q:[["Where should the main point go?",["At the start","Hidden in the middle","At the very end"],0],["Good feedback is…",["Specific and about the work","Vague","Personal"],0]]}
];
const $=s=>document.querySelector(s);
const esc=s=>String(s).replace(/[&<>"]/g,c=>({"&":"&amp;","<":"&lt;",">":"&gt;",'"':"&quot;"}[c]));
function ld(){try{return JSON.parse(localStorage.getItem("eduflow")||"{}")}catch(e){return {}}}
function sv(){try{localStorage.setItem("eduflow",JSON.stringify(D))}catch(e){}}
let D=ld();D.users=D.users||{};
let V={v:"home",id:null,i:0,q:"",cat:"All",lv:"All",qa:{},res:null,mode:"up"};
const me=()=>D.users[D.cur];
const course=id=>C.find(c=>c.id===id);
const hash=s=>{let x=5381;for(const c of s)x=((x<<5)+x+c.charCodeAt(0))|0;return String(x)};
const day=t=>new Date(t).toISOString().slice(0,10);
function toast(m){const t=$("#toast");t.textContent=m;t.style.display="block";clearTimeout(toast.t);toast.t=setTimeout(()=>t.style.display="none",2200)}
function go(v,id,i){V.v=v;if(id!==undefined)V.id=id;V.i=i||0;V.qa={};V.res=null;render();scrollTo(0,0)}
function theme(){const r=document.documentElement;const dark=r.dataset.theme?r.dataset.theme==="dark":matchMedia("(prefers-color-scheme:dark)").matches;r.dataset.theme=dark?"light":"dark";if(me()){me().theme=r.dataset.theme;sv()}}
function gain(n){const u=me(),t=day(Date.now());u.xp+=n;if(u.last!==t){u.streak=u.last===day(Date.now()-864e5)?u.streak+1:1;u.last=t}sv()}
function prog(id){const e=me().en[id];return e?Math.round(e.done.length/course(id).L.length*100):0}
function passed(id){const e=me().en[id];return !!e&&prog(id)===100&&e.quiz!==null&&e.quiz>=60}
function badges(){const u=me(),k=Object.keys(u.en);return[["First lesson",k.some(i=>u.en[i].done.length)],["3-day streak",u.streak>=3],["Course finisher",C.some(c=>passed(c.id))],["Perfect score",k.some(i=>u.en[i].quiz===100)],["Note taker",k.some(i=>Object.values(u.en[i].notes).some(n=>n))]]}
/* auth */
function signup(){const n=$("#n").value.trim(),e=$("#e").value.trim().toLowerCase(),p=$("#p").value;
 if(!n||!/^\S+@\S+\.\S+$/.test(e)||p.length<6)return toast("Enter your name, a valid email and a password of 6+ characters.");
 if(D.users[e])return toast("That email already has an account. Log in instead.");
 D.users[e]={name:n,pw:hash(p),xp:0,streak:0,last:"",bm:[],en:{}};D.cur=e;sv();go("home")}
function login(){const e=$("#e").value.trim().toLowerCase(),u=D.users[e];
 if(!u||u.pw!==hash($("#p").value))return toast("Email or password is incorrect.");
 D.cur=e;sv();if(u.theme)document.documentElement.dataset.theme=u.theme;go("home")}
function logout(){D.cur=null;sv();render()}
function authView(){const up=V.mode==="up";return`<div class="w" style="max-width:420px"><h1 style="font-size:40px;color:var(--pr)">EduFlow</h1><p class="mu">Short courses, quizzes and certificates. Your progress stays on this device.</p><div class="card">
<div class="row"><button class="btn ${up?"on":""}" onclick="V.mode='up';render()">Create account</button><button class="btn ${up?"":"on"}" onclick="V.mode='in';render()">Log in</button></div><div class="f" style="flex-direction:column">
${up?`<label>Name<input id="n" autocomplete="name"></label>`:""}<label>Email<input id="e" type="email" autocomplete="email"></label><label>Password<input id="p" type="password" autocomplete="${up?"new-password":"current-password"}"></label>
<button class="btn p" onclick="${up?"signup()":"login()"}">${up?"Create account":"Log in"}</button></div></div></div>`}
/* views */
function nav(){const t=(v,l)=>`<button class="btn ${V.v===v?"on":""}" onclick="go('${v}')">${l}</button>`;
 return`<nav><span class="logo">EduFlow</span>${t("home","Explore")}${t("mine","My learning")}${t("saved","Saved")}${t("dash","Dashboard")}<button class="btn" onclick="theme()" aria-label="Toggle dark mode">◐</button><button class="btn" onclick="logout()">Log out</button></nav>`}
function list(){const q=V.q.toLowerCase();return C.filter(c=>(V.cat==="All"||c.cat===V.cat)&&(V.lv==="All"||c.lv===V.lv)&&(c.t+c.d+c.by).toLowerCase().includes(q))}
function cards(a){if(!a.length)return`<p class="mu">No courses match. Clear the search or change a filter.</p>`;const u=me();
 return a.map(c=>`<div class="card"><div class="row sp"><span class="tag">${c.cat} · ${c.lv}</span><button class="bm" aria-label="Save course" onclick="bm('${c.id}')">${u.bm.includes(c.id)?"★":"☆"}</button></div>
<h3>${c.t}</h3><p class="mu">${c.d}</p><span class="tag">${c.L.length} lessons</span><span class="tag">${c.min} min</span><span class="tag">${c.by}</span>
${u.en[c.id]?`<div class="bar"><i style="width:${prog(c.id)}%"></i></div>`:""}<button class="btn p" onclick="go('course','${c.id}')">${u.en[c.id]?"Continue":"View course"}</button></div>`).join("")}
function filt(){$("#grid").innerHTML=cards(list())}
function home(){const o=(a,k)=>["All",...a].map(x=>`<option ${V[k]===x?"selected":""}>${x}</option>`).join("");
 return`<div class="w"><h1>Learn something new, ${esc(me().name.split(" ")[0])}</h1><div class="f"><input placeholder="Search courses or instructors" value="${esc(V.q)}" oninput="V.q=this.value;filt()" aria-label="Search">
<select onchange="V.cat=this.value;filt()" aria-label="Category">${o([...new Set(C.map(c=>c.cat))],"cat")}</select><select onchange="V.lv=this.value;filt()" aria-label="Level">${o(["Beginner","Intermediate"],"lv")}</select></div><div class="grid" id="grid">${cards(list())}</div></div>`}
function bm(id){const b=me().bm,i=b.indexOf(id);i<0?b.push(id):b.splice(i,1);sv();V.v==="home"?filt():render()}
function enroll(id){me().en[id]={done:[],notes:{},quiz:null,rate:0};gain(5);toast("Enrolled. Start with lesson 1.");go("learn",id,0)}
function coursePage(){const c=course(V.id),e=me().en[c.id];
 return`<div class="w"><button class="btn" onclick="go('home')">Back</button><h1 style="margin-top:14px">${c.t}</h1><p>${c.d}</p><p class="mu">${c.cat} · ${c.lv} · ${c.min} min · taught by ${c.by}</p>
<div class="row">${e?`<button class="btn p" onclick="go('learn','${c.id}',${Math.min(e.done.length,c.L.length)})">Continue learning</button>`:`<button class="btn p" onclick="enroll('${c.id}')">Enroll for free</button>`}<button class="btn" onclick="bm('${c.id}')">${me().bm.includes(c.id)?"★ Saved":"☆ Save for later"}</button></div>
${e?`<div class="bar"><i style="width:${prog(c.id)}%"></i></div><p class="mu">${prog(c.id)}% complete${e.quiz!==null?` · Quiz best: ${e.quiz}%`:""}</p>`:""}
<h2 style="margin-top:24px">Lessons</h2>${c.L.map((l,i)=>`<div class="card" style="margin-bottom:8px">${i+1}. ${l[0]}${e&&e.done.includes(i)?` <span style="color:var(--ok)">✓</span>`:""}</div>`).join("")}<div class="card">Final quiz · ${c.Q.length} questions · pass at 60%</div>
${e?`<h3 style="margin-top:24px">Rate this course</h3><div>${[1,2,3,4,5].map(n=>`<button class="bm" aria-label="${n} stars" onclick="rate('${c.id}',${n})">${n<=e.rate?"★":"☆"}</button>`).join("")}</div>`:""}</div>`}
function rate(id,n){me().en[id].rate=n;sv();render()}
function learn(){const c=course(V.id),e=me().en[c.id],i=V.i,q=i>=c.L.length;
 const side=`<aside>${c.L.map((l,k)=>`<button class="btn les ${e.done.includes(k)?"done":""} ${k===i?"on":""}" onclick="go('learn','${c.id}',${k})">${l[0]}</button>`).join("")}<button class="btn les ${q?"on":""}" onclick="go('learn','${c.id}',${c.L.length})">Final quiz</button><div class="bar"><i style="width:${prog(c.id)}%"></i></div></aside>`;
 let main;
 if(!q){const l=c.L[i];main=`<main class="card"><p class="mu">Lesson ${i+1} of ${c.L.length}</p><h2>${l[0]}</h2><p>${l[1]}</p>
<label class="mu">Your notes<textarea rows="4" oninput="note('${c.id}',${i},this.value)">${esc(e.notes[i]||"")}</textarea></label>
<div class="row sp" style="margin-top:12px"><button class="btn" ${i?"":"disabled"} onclick="go('learn','${c.id}',${i-1})">Previous</button>
<button class="btn p" onclick="done('${c.id}',${i})">${e.done.includes(i)?"Next":"Mark complete and continue"}</button></div></main>`}
 else{const r=V.res;main=`<main class="card"><h2>Final quiz</h2>${prog(c.id)<100?`<p class="mu">Complete all lessons first for the best result. You can still try now.</p>`:""}
${c.Q.map((x,k)=>`<div style="margin:14px 0"><b>${k+1}. ${x[0]}</b>${x[1].map((o,j)=>`<label class="opt ${r?(j===x[2]?"ok":V.qa[k]===j?"no":""):""}"><input type="radio" name="q${k}" style="width:auto" ${V.qa[k]===j?"checked":""} ${r?"disabled":""} onchange="V.qa[${k}]=${j}"> ${o}</label>`).join("")}</div>`).join("")}
${r?`<p class="b" style="font-size:20px">Score: ${r.s}% — ${r.s>=60?"Passed":"Not passed yet. Review the lessons and try again."}</p><div class="row">${passed(c.id)?`<button class="btn p" onclick="go('cert','${c.id}')">View certificate</button>`:""}<button class="btn" onclick="go('learn','${c.id}',${c.L.length})">Retake quiz</button></div>`:`<button class="btn p" onclick="submitQ('${c.id}')">Submit answers</button>`}</main>`}
 return`<div class="w"><button class="btn" onclick="go('course','${c.id}')">Back to course</button><h2 style="margin:14px 0">${c.t}</h2><div class="lay">${side}${main}</div></div>`}
function note(id,i,v){me().en[id].notes[i]=v;sv()}
function done(id,i){const e=me().en[id],c=course(id);if(!e.done.includes(i)){e.done.push(i);gain(10);toast("+10 XP")}sv();go("learn",id,Math.min(i+1,c.L.length))}
function submitQ(id){const c=course(id),e=me().en[id];if(Object.keys(V.qa).length<c.Q.length)return toast("Answer every question first.");
 const n=c.Q.filter((x,k)=>V.qa[k]===x[2]).length,s=Math.round(n/c.Q.length*100);e.quiz=Math.max(e.quiz||0,s);gain(Math.round(s/10));V.res={s};sv();render();if(passed(id))toast("Course complete. Certificate unlocked.")}
function mine(){const a=C.filter(c=>me().en[c.id]);return`<div class="w"><h1>My learning</h1>${a.length?`<div class="grid">${cards(a)}</div>`:`<p class="mu">You have not enrolled in a course yet. Browse Explore and pick one.</p><button class="btn p" onclick="go('home')">Find a course</button>`}</div>`}
function saved(){const a=C.filter(c=>me().bm.includes(c.id));return`<div class="w"><h1>Saved</h1>${a.length?`<div class="grid">${cards(a)}</div>`:`<p class="mu">Tap the star on any course to save it here.</p>`}</div>`}
function dash(){const u=me(),k=Object.keys(u.en),ls=k.reduce((s,i)=>s+u.en[i].done.length,0),dn=C.filter(c=>passed(c.id));
 const st=(n,l)=>`<div class="card"><div class="stat">${n}</div><span class="mu">${l}</span></div>`;
 return`<div class="w"><h1>Dashboard</h1><div class="grid">${st(u.xp,"XP earned")}${st("Level "+(Math.floor(u.xp/50)+1),"Next level at "+(Math.floor(u.xp/50)+1)*50+" XP")}${st(u.streak+" days","Current streak")}${st(ls,"Lessons completed")}${st(k.length,"Courses enrolled")}${st(dn.length,"Certificates earned")}</div>
<h2 style="margin-top:24px">Badges</h2>${badges().map(b=>`<span class="badge ${b[1]?"got":""}">${b[1]?"★ ":""}${b[0]}</span>`).join("")}
<h2 style="margin-top:24px">Progress by course</h2>${k.length?k.map(i=>`<div class="card" style="margin-bottom:8px"><div class="row sp"><span>${course(i).t}</span><span class="mu">${prog(i)}%${passed(i)?` · <a href="#" onclick="go('cert','${i}');return false">Certificate</a>`:""}</span></div><div class="bar"><i style="width:${prog(i)}%"></i></div></div>`).join(""):`<p class="mu">Enroll in a course to track progress here.</p>`}
<h2 style="margin-top:24px">Account</h2><p class="mu">${esc(u.name)} · ${esc(D.cur)}</p><button class="btn" onclick="reset()">Reset my progress</button></div>`}
function reset(){if(!confirm("Delete all your progress, notes and saved courses?"))return;const u=me();u.xp=0;u.streak=0;u.last="";u.bm=[];u.en={};sv();render()}
function cert(){const c=course(V.id);if(!passed(c.id))return`<div class="w"><p>Pass the final quiz to unlock this certificate.</p></div>`;
 return`<div class="w"><div class="row noprint" style="margin-bottom:12px"><button class="btn" onclick="go('dash')">Back</button><button class="btn p" onclick="print()">Print or save as PDF</button></div><div class="cert"><p class="mu">Certificate of completion</p><h1>${esc(me().name)}</h1><p>has successfully completed</p><h2>${c.t}</h2><p>Quiz score ${me().en[c.id].quiz}% · ${new Date().toLocaleDateString()}</p><p class="mu">EduFlow</p></div></div>`}
function render(){if(!me()){$("#app").innerHTML=authView();return}
 const m={home,course:coursePage,learn,mine,saved,dash,cert};$("#app").innerHTML=nav()+m[V.v]()}
if(me()&&me().theme)document.documentElement.dataset.theme=me().theme;
render();
</script></body></html>
