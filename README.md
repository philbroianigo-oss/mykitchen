<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0">
<meta name="apple-mobile-web-app-capable" content="yes">
<meta name="apple-mobile-web-app-status-bar-style" content="default">
<meta name="apple-mobile-web-app-title" content="My Kitchen">
<title>My Kitchen 🍽️</title>
<style>
*{box-sizing:border-box;margin:0;padding:0;-webkit-tap-highlight-color:transparent;}
body{font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;background:#f7f5f2;color:#1a1714;min-height:100vh;}
input,select,textarea,button{font-family:inherit;}
button{cursor:pointer;touch-action:manipulation;}

/* HEADER */
.header{padding:1rem 1rem 0.7rem;background:#fff;border-bottom:1px solid #e0dbd4;}
.header h1{font-size:22px;font-weight:800;color:#c85a1a;letter-spacing:-0.02em;}
.header p{font-size:11px;color:#8a8480;margin-top:3px;text-transform:uppercase;letter-spacing:0.04em;}

/* TABS */
.tabs{display:flex;background:#fff;border-bottom:1px solid #e0dbd4;position:sticky;top:0;z-index:100;}
.tab-btn{flex:1;padding:13px 4px;border:none;background:none;color:#8a8480;font-size:12px;font-weight:400;border-bottom:2.5px solid transparent;text-transform:uppercase;letter-spacing:0.04em;transition:all 0.15s;}
.tab-btn.active{color:#c85a1a;font-weight:700;border-bottom-color:#c85a1a;}

/* PANELS */
.panel{display:none;padding:1rem;padding-bottom:5rem;}
.panel.active{display:block;}

/* CARDS */
.card{background:#fff;border-radius:14px;padding:1rem;border:1.5px solid #e0dbd4;box-shadow:0 1px 4px rgba(0,0,0,0.05);margin-bottom:12px;}

/* BADGES */
.badge{display:inline-block;padding:3px 10px;border-radius:999px;font-size:11px;font-weight:600;margin:2px 3px 2px 0;white-space:nowrap;}
.badge-family{background:#fff0e0;color:#7a3a00;border:1px solid #7a3a0033;}
.badge-airfryer{background:#e8f0fd;color:#1a4a8a;border:1px solid #1a4a8a33;}
.badge-ratatouille{background:#f3eafd;color:#5a1a8a;border:1px solid #5a1a8a33;}
.badge-gray{background:#f0ede8;color:#8a8480;border:1px solid #e0dbd4;}

/* INPUTS */
.inp{width:100%;padding:10px 12px;border-radius:8px;border:1px solid #e0dbd4;background:#fff;color:#1a1714;font-size:14px;outline:none;}
.inp:focus{border-color:#c85a1a;}
select.inp{cursor:pointer;}

/* BUTTONS */
.btn-primary{padding:13px;border-radius:10px;border:none;background:#c85a1a;color:#fff;font-size:14px;font-weight:700;width:100%;}
.btn-ghost{padding:10px 14px;border-radius:9px;border:1.5px solid #e0dbd4;background:#fff;color:#1a1714;font-size:13px;font-weight:500;}
.btn-add-recipe{width:100%;padding:14px;border-radius:12px;border:2px dashed #c85a1a;background:#fdf0ea;color:#c85a1a;font-size:14px;font-weight:700;margin-bottom:14px;display:flex;align-items:center;justify-content:center;gap:8px;}
.btn-expand{width:100%;text-align:left;background:#f7f5f2;border:1px solid #e0dbd4;border-radius:8px;padding:9px 12px;font-size:13px;color:#1a1714;display:flex;justify-content:space-between;align-items:center;margin-bottom:6px;}
.btn-expand span.hint{color:#8a8480;font-size:12px;}
.btn-cook{flex:1;padding:11px;border-radius:9px;border:none;background:#c85a1a;color:#fff;font-size:13px;font-weight:700;}
.btn-cart{flex:1;padding:11px;border-radius:9px;border:1.5px solid #e0dbd4;background:#fff;color:#1a1714;font-size:13px;font-weight:500;}
.btn-del{background:none;border:none;color:#c0b8b0;font-size:20px;padding:0 4px;line-height:1;flex-shrink:0;}

/* RECIPE CARD */
.recipe-title{font-size:15px;font-weight:700;margin-bottom:8px;padding-right:8px;flex:1;line-height:1.3;}
.recipe-note{font-size:12px;color:#8a6000;font-style:italic;background:#fef8e0;border-left:3px solid #e8c87c;padding:6px 10px;border-radius:0 6px 6px 0;margin-bottom:10px;}
.ingr-list,.steps-list{background:#f7f5f2;border-radius:8px;padding:10px 14px;border:1px solid #e0dbd4;margin-bottom:6px;}
.ingr-list div{font-size:13px;padding:3px 0;border-bottom:1px solid #e0dbd4;}
.ingr-list div:last-child{border-bottom:none;}
.steps-list{padding-left:28px;}
.steps-list li{font-size:13px;padding:4px 0;border-bottom:1px solid #e0dbd4;line-height:1.5;}
.steps-list li:last-child{border-bottom:none;}

/* SECTION TITLE */
.section-title{font-size:11px;color:#8a8480;text-transform:uppercase;letter-spacing:0.08em;font-weight:600;margin:14px 0 6px;}

/* STATS */
.stat-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:14px;}
.stat-box{border-radius:10px;padding:12px 6px;text-align:center;}
.stat-box .num{font-size:22px;font-weight:800;}
.stat-box .lbl{font-size:10px;text-transform:uppercase;letter-spacing:0.06em;font-weight:600;margin-top:2px;}
.stat-green{background:#eaf5ec;} .stat-green .num,.stat-green .lbl{color:#2d7a3a;}
.stat-amber{background:#fef8e0;} .stat-amber .num,.stat-amber .lbl{color:#8a6000;}
.stat-red{background:#fdeaea;}   .stat-red .num,.stat-red .lbl{color:#b32020;}

/* PANTRY ROWS */
.pantry-row{display:flex;align-items:center;gap:8px;padding:11px 12px;border-bottom:1px solid #f0ede8;}
.pantry-row:last-child{border-bottom:none;}
.pantry-name{flex:1;font-size:13px;font-weight:500;}
.pantry-qty{font-size:11px;color:#8a8480;}
.status-select{padding:4px 8px;border-radius:6px;border:1px solid #e0dbd4;font-size:11px;font-weight:600;background:#f7f5f2;cursor:pointer;}
.status-ok{color:#2d7a3a;} .status-low{color:#8a6000;} .status-out{color:#b32020;}

/* PROGRESS BAR */
.prog-bar{height:6px;background:#e0dbd4;border-radius:3px;margin-bottom:14px;}
.prog-fill{height:100%;border-radius:3px;background:#2d7a3a;transition:width 0.3s;}
.prog-label{display:flex;justify-content:space-between;font-size:12px;color:#8a8480;margin-bottom:6px;}

/* SHOPPING */
.shop-row{display:flex;align-items:center;gap:10px;padding:13px 12px;border-bottom:1px solid #f0ede8;transition:opacity 0.2s;}
.shop-row:last-child{border-bottom:none;}
.shop-row.done{opacity:0.4;}
.shop-row input[type=checkbox]{width:20px;height:20px;accent-color:#c85a1a;flex-shrink:0;}
.shop-name{flex:1;font-size:14px;font-weight:500;}
.shop-row.done .shop-name{text-decoration:line-through;}
.shop-qty{font-size:12px;color:#8a8480;margin-left:6px;}

/* OVERLAY */
.overlay{position:fixed;inset:0;background:#f7f5f2;z-index:500;overflow-y:auto;}
.overlay-header{display:flex;justify-content:space-between;align-items:center;padding:1rem;background:#fff;border-bottom:1px solid #e0dbd4;position:sticky;top:0;z-index:10;}
.overlay-title{font-size:16px;font-weight:700;color:#c85a1a;}
.overlay-body{padding:1.2rem;}

/* COOKING MODE */
.cook-step-box{background:#fdf0ea;border-radius:14px;padding:1.5rem;border:1.5px solid #c85a1a33;margin-bottom:1rem;}
.cook-step-num{font-size:10px;color:#c85a1a;text-transform:uppercase;letter-spacing:0.1em;font-weight:700;margin-bottom:8px;}
.cook-step-text{font-size:19px;color:#1a1714;line-height:1.7;font-weight:500;}
.cook-nav{display:flex;gap:10px;margin-bottom:1rem;}
.cook-prev{flex:1;padding:15px;border-radius:10px;border:1.5px solid #e0dbd4;background:#fff;font-size:14px;font-weight:600;}
.cook-prev:disabled{opacity:0.4;cursor:not-allowed;}
.cook-next{flex:2;padding:15px;border-radius:10px;border:none;background:#c85a1a;color:#fff;font-size:15px;font-weight:700;}
.cook-next.finish{background:#2d7a3a;}
.cook-step-list{margin-top:0.5rem;}
.cook-step-item{display:flex;gap:10px;padding:9px 0;border-bottom:1px solid #e0dbd4;align-items:flex-start;font-size:13px;}
.cook-step-item:last-child{border-bottom:none;}
.cook-step-icon{width:22px;flex-shrink:0;font-weight:700;}

/* MODE PICKER */
.mode-btn{width:100%;margin-bottom:10px;background:#fff;border:1.5px solid #e0dbd4;border-radius:14px;padding:1rem 1.2rem;text-align:left;display:flex;align-items:center;gap:14px;}
.mode-icon{font-size:26px;flex-shrink:0;}
.mode-label{font-size:14px;font-weight:700;color:#1a1714;}
.mode-sub{font-size:12px;color:#8a8480;margin-top:2px;}

/* ERROR / SUCCESS */
.msg-error{background:#fdeaea;border:1px solid #b3202044;border-radius:8px;padding:10px 14px;font-size:13px;color:#b32020;margin-bottom:14px;}
.msg-ok{background:#eaf5ec;border:1px solid #2d7a3a44;border-radius:8px;padding:10px 14px;font-size:13px;color:#2d7a3a;margin-bottom:14px;}

/* LOADING */
.loading{text-align:center;padding:4rem 0;}
.loading .emoji{font-size:40px;margin-bottom:14px;}
.loading .title{font-size:15px;color:#c85a1a;font-weight:700;}
.loading .sub{font-size:12px;color:#8a8480;margin-top:6px;}

/* FILTER PILLS */
.filter-row{display:flex;flex-wrap:wrap;gap:6px;margin-bottom:14px;align-items:center;}
.pill{padding:6px 14px;border-radius:999px;font-size:12px;border:1.5px solid #e0dbd4;background:#fff;color:#8a8480;font-weight:400;}
.pill.active{border-color:#c85a1a;background:#fdf0ea;color:#c85a1a;font-weight:700;}

/* FORM LABEL */
.form-label{font-size:10px;color:#8a8480;text-transform:uppercase;letter-spacing:0.07em;font-weight:600;margin-bottom:5px;margin-top:4px;}
.form-row{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px;}
.form-group{margin-bottom:12px;}

/* EMPTY STATE */
.empty{text-align:center;color:#8a8480;padding:3rem 0;}
.empty .emoji{font-size:32px;margin-bottom:8px;}

/* ADD FORM INLINE */
.add-form{background:#fff;border-radius:12px;padding:1rem;margin-bottom:14px;border:1px solid #e0dbd4;}
.add-form-title{font-size:10px;color:#8a8480;text-transform:uppercase;letter-spacing:0.08em;font-weight:700;margin-bottom:10px;}
.add-row{display:flex;gap:6px;margin-bottom:8px;}
</style>
</head>
<body>

<div class="header">
  <h1>🍽️ My Kitchen</h1>
  <p id="header-sub">10 recipes • Pantry • Shopping</p>
</div>

<div class="tabs">
  <button class="tab-btn active" onclick="switchTab('recipes')">Recipes (<span id="recipe-count">10</span>)</button>
  <button class="tab-btn" onclick="switchTab('pantry')">Pantry (<span id="pantry-count">40</span>)</button>
  <button class="tab-btn" onclick="switchTab('shopping')">Shopping (<span id="shop-count">13</span>)</button>
</div>

<!-- RECIPES PANEL -->
<div id="panel-recipes" class="panel active">
  <div id="source-badges" style="display:flex;flex-wrap:wrap;gap:6px;margin-bottom:12px;"></div>
  <div class="filter-row" id="filter-row"></div>
  <button class="btn-add-recipe" onclick="showAddRecipe()"><span style="font-size:20px">➕</span> Add a New Recipe</button>
  <div id="recipe-list"></div>
</div>

<!-- PANTRY PANEL -->
<div id="panel-pantry" class="panel">
  <div class="stat-grid">
    <div class="stat-box stat-green"><div class="num" id="stat-ok">0</div><div class="lbl">✓ Plenty</div></div>
    <div class="stat-box stat-amber"><div class="num" id="stat-low">0</div><div class="lbl">⚠ Low</div></div>
    <div class="stat-box stat-red"><div class="num" id="stat-out">0</div><div class="lbl">✕ Out</div></div>
  </div>
  <div class="add-form">
    <div class="add-form-title">Add item</div>
    <div class="add-row">
      <input id="p-name" class="inp" placeholder="Item name" style="flex:2">
      <input id="p-qty" class="inp" placeholder="Qty" style="flex:1">
    </div>
    <div class="add-row">
      <select id="p-loc" class="inp" style="flex:1"><option>Fridge</option><option>Freezer</option><option>Pantry</option></select>
      <select id="p-stat" class="inp" style="flex:1"><option value="ok">Plenty ✓</option><option value="low">Low ⚠️</option><option value="out">Out ✕</option></select>
      <button class="btn-primary" style="width:auto;padding:10px 16px;" onclick="addPantryItem()">Add</button>
    </div>
  </div>
  <div id="pantry-fridge"></div>
  <div id="pantry-freezer"></div>
  <div id="pantry-pantry"></div>
</div>

<!-- SHOPPING PANEL -->
<div id="panel-shopping" class="panel">
  <div id="prog-wrap" style="display:none">
    <div class="prog-label"><span id="prog-text"></span><span id="prog-pct"></span></div>
    <div class="prog-bar"><div class="prog-fill" id="prog-fill"></div></div>
  </div>
  <div style="display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px;">
    <button class="btn-ghost" onclick="addLowStock()">⚠️ Add low-stock</button>
    <button class="btn-ghost" onclick="clearChecked()">🗑 Clear checked</button>
  </div>
  <div class="add-form">
    <div class="add-form-title">Add item</div>
    <div class="add-row">
      <input id="s-name" class="inp" placeholder="Item name" style="flex:2">
      <input id="s-qty" class="inp" placeholder="Qty" style="flex:1">
    </div>
    <div class="add-row">
      <select id="s-cat" class="inp" style="flex:1">
        <option>🥩 Meat</option><option>🧀 Dairy</option><option>🥦 Produce</option>
        <option>🍎 Fruits</option><option>🥫 Pantry</option><option>🫙 Spices</option><option>🛒 Other</option>
      </select>
      <button class="btn-primary" style="width:auto;padding:10px 16px;" onclick="addShoppingItem()">Add</button>
    </div>
  </div>
  <div id="shopping-list"></div>
</div>

<!-- OVERLAYS -->
<div id="overlay-cook" class="overlay" style="display:none"></div>
<div id="overlay-add" class="overlay" style="display:none"></div>

<script>
// ── DATA ─────────────────────────────────────────────────────────────────────
const RECIPES_DEFAULT = [
  {id:1,name:"Taquitos au bœuf",cat:"Mexican",time:"20–40 min",source:"airfryer",sourceLabel:"recette-airfryer.fr",ingr:["300g bœuf haché 5% MG","1 oignon émincé","2 gousses d'ail pressées","2 c.s. sauce chipotle en adobo","1 c.c. cumin en poudre","1 c.c. paprika fumé","½ c.c. origan séché","80g Monterey Jack râpé","8 tortillas de blé 15cm","2 c.s. concentré de tomate","1 c.s. huile d'olive","Sel"],steps:["Faire revenir l'oignon émincé dans une poêle","Ajouter l'ail pressé, sauter 30 sec","Ajouter le bœuf haché et faire dorer","Incorporer sauce chipotle, concentré tomate, cumin, paprika, origan. Cuire 3 min","Retirer du feu, laisser tiédir 5 min, ajouter le fromage râpé","Réchauffer les tortillas","Déposer 2-3 c.s. de garniture sur chaque tortilla","Rouler serré, badigeonner d'huile d'olive","Cuire à l'Air Fryer 8 min à 200°C"]},
  {id:2,name:"Boulettes à la viande hachée",cat:"French",time:"40–60 min",source:"family",sourceLabel:"Grand-père & Maman",ingr:["350g viande hachée","150g fromage de chèvre frais","1 oignon haché","2 gousses d'ail","1 grande tranche de pain","Persil frais haché","Farine","Huile d'olive","Sel, poivre","2–3 œufs"],steps:["Mélanger viande, chèvre, oignon, ail, persil, pain émietté","Saler et poivrer","Former des boulettes","Tremper dans les œufs battus puis dans la farine","Faire dorer dans l'huile d'olive","Finir la cuisson au four si nécessaire"]},
  {id:3,name:"Taboulé Olé-Olé",cat:"Middle-Eastern",time:"20–40 min",source:"ratatouille",sourceLabel:"Disney Ratatouille",ingr:["250g couscous moyen","40cl eau","4 tomates","2 petits oignons frais","½ concombre","8 feuilles de persil plat","2 citrons","3 c.s. huile d'olive","Sel"],steps:["La veille : verser couscous + eau dans saladier, mélanger, mettre au frigo","Couper tomates en cubes, vider pépins","Peler oignons et concombre, couper en cubes","Couper persil en lanières","Presser les citrons","Mélanger tout dans le saladier, rectifier sel","Réfrigérer 1h avant de servir"],note:"Servir dans des verres transparents, décorer de persil entier."},
  {id:4,name:"Champignons farcis tomme & romarin",cat:"French",time:"20–40 min",source:"ratatouille",sourceLabel:"Disney Ratatouille",ingr:["12 champignons de Paris (gros)","100g tomme de chèvre sans croûte","2 c.s. crème fraîche épaisse","2 brins de romarin","Sel et poivre"],steps:["Préchauffer le four à 180°C (th.6)","Retirer les queues des champignons","Mixer le fromage, mélanger avec la crème, saler et poivrer","Remplir les champignons avec le mélange","Poser des feuilles de romarin par-dessus","Enfourner 15 min, servir chaud"],note:"Vous pouvez remplacer le romarin par des graines de cumin."},
  {id:5,name:"Poulet au fromage en robe de jambon",cat:"French",time:"20–40 min",source:"ratatouille",sourceLabel:"Disney Ratatouille",ingr:["4 escalopes de poulet","8 c.s. fromage de chèvre frais","4 tranches de jambon de pays","2 c.s. huile d'olive","Sel et poivre"],steps:["Préchauffer le four à 200°C (th.6-7)","Couper les escalopes en portefeuille","Remplir chaque poche de fromage de chèvre","Enrouler chaque escalope dans une tranche de jambon","Étaler l'huile dans le plat","Enfourner 15 min"]},
  {id:6,name:"Gnocchi tomate & mozzarella",cat:"Italian",time:"20–40 min",source:"airfryer",sourceLabel:"recette-airfryer.fr",ingr:["500g gnocchi de pommes de terre","200g sauce tomate (passata)","125g mozzarella en dés","30g parmesan râpé","1 c.s. huile d'olive","2 gousses d'ail émincées","1 c.c. origan séché","Sel et poivre noir","6 feuilles de basilic frais","10 tomates cerises"],steps:["Mélanger gnocchi, ail, origan, huile, sel et poivre","Verser la sauce tomate sur les gnocchi","Ajouter tomates cerises et mozzarella, mélanger délicatement","Préchauffer l'Air Fryer","Cuire à 190°C pendant 10 min","Saupoudrer de parmesan, poursuivre jusqu'à gratinage","Garnir de basilic frais"]},
  {id:7,name:"Gratin de chou-fleur",cat:"French",time:"40–60 min",source:"airfryer",sourceLabel:"recette-airfryer.fr",ingr:["½ chou-fleur","15g beurre","15g farine","25g fromage râpé","20cl eau","3cl crème fraîche","1 bouillon de volaille","Sel, poivre, muscade"],steps:["Couper le chou-fleur en bouquets, cuire à la vapeur","Porter eau + bouillon à ébullition","Faire fondre le beurre, ajouter farine, incorporer le bouillon chaud en remuant","Ajouter la crème, sel, poivre, muscade","Déposer le chou-fleur, napper de sauce, saupoudrer de fromage","Cuire à l'Air Fryer 8 min à 200°C"]},
  {id:8,name:"Gratin dauphinois",cat:"French",time:"> 1 hour",source:"airfryer",sourceLabel:"recette-airfryer.fr",ingr:["1 kg pommes de terre Belle de Fontenay","3 gousses d'ail","75cl crème fraîche","Sel, poivre, muscade"],steps:["Éplucher et couper les pommes de terre en tranches fines (~2mm)","Frotter le plat avec les gousses d'ail coupées","Mélanger la crème, sel, poivre, muscade","Alterner couches de pommes de terre et crème","Cuire à 160°C environ 50 min"]},
  {id:9,name:"Chicken Tenders",cat:"American",time:"20–40 min",source:"airfryer",sourceLabel:"recette-airfryer.fr",ingr:["500g filets de poulet en lanières","100g farine","2 œufs","150g chapelure fine","2 c.c. paprika fumé","1 c.c. piment de Cayenne","1 c.c. ail en poudre","1 c.c. oignon en poudre","½ c.c. thym séché","½ c.c. origan séché","½ c.c. sel","1 c.s. huile d'olive"],steps:["Mélanger chapelure + épices","Couper poulet en lanières, éponger","Paner : farine → œuf → chapelure","Préchauffer l'Air Fryer à 200°C","Cuire 10–12 min en retournant à mi-cuisson"]},
  {id:10,name:"Pork Rib Tomato Sauce",cat:"French",time:"> 1 hour",source:"family",sourceLabel:"Tante",ingr:["595g bone-in pork ribs","175g whole onion (peeled)","15g garlic cloves","540g canned peeled tomatoes","160g tomato paste","150g red wine","7g sugar","2 sprigs fresh thyme","1 bay leaf","310g water"],steps:["Brown pork ribs on all sides in a heavy pot","Add whole onion and garlic, cook 2 min","Pour in red wine, let alcohol evaporate","Add crushed tomatoes and tomato paste, mix well","Add sugar, thyme, bay leaf, water to cover","Simmer low and slow until meat is tender and sauce thick","Adjust sugar if too acidic. Remove thyme and bay leaf","Serve over pasta with Parmesan or Gruyère on the side"],note:"Sauce looks very liquid at first — thickens as it reduces. Do NOT mix cheese into the sauce."}
];

const PANTRY_DEFAULT = [
  {id:1001,name:"Chicken breast fillets",qty:"500g",loc:"Fridge",status:"ok"},{id:1002,name:"Pork ribs",qty:"600g",loc:"Fridge",status:"ok"},{id:1003,name:"Ham slices",qty:"4 pieces",loc:"Fridge",status:"ok"},{id:1004,name:"Eggs",qty:"6",loc:"Fridge",status:"ok"},{id:1005,name:"Onions",qty:"5",loc:"Pantry",status:"ok"},{id:1006,name:"Spring onions",qty:"2",loc:"Fridge",status:"ok"},{id:1007,name:"Garlic cloves",qty:"10",loc:"Pantry",status:"ok"},{id:1008,name:"Cauliflower",qty:"½ head",loc:"Fridge",status:"ok"},{id:1009,name:"Potatoes (Belle de Fontenay)",qty:"1 kg",loc:"Pantry",status:"ok"},{id:1010,name:"Cherry tomatoes",qty:"10",loc:"Fridge",status:"ok"},{id:1011,name:"Tomatoes",qty:"4",loc:"Fridge",status:"ok"},{id:1012,name:"Cucumber",qty:"½",loc:"Fridge",status:"ok"},{id:1013,name:"Paris mushrooms",qty:"12 large",loc:"Fridge",status:"ok"},{id:1014,name:"Fresh basil",qty:"6 leaves",loc:"Fridge",status:"ok"},{id:1015,name:"Flat-leaf parsley",qty:"1 bunch",loc:"Fridge",status:"ok"},{id:1016,name:"Fresh rosemary",qty:"2 sprigs",loc:"Fridge",status:"ok"},{id:1017,name:"Fresh thyme",qty:"2 sprigs",loc:"Fridge",status:"ok"},{id:1018,name:"Lemons",qty:"2",loc:"Fridge",status:"ok"},{id:1019,name:"Kiwis",qty:"",loc:"Fridge",status:"ok"},{id:1020,name:"Strawberries",qty:"",loc:"Fridge",status:"ok"},{id:1021,name:"Blueberries",qty:"",loc:"Fridge",status:"ok"},{id:1022,name:"Couscous",qty:"250g",loc:"Pantry",status:"ok"},{id:1023,name:"Flour tortillas 15cm",qty:"8",loc:"Pantry",status:"ok"},{id:1024,name:"Canned peeled tomatoes",qty:"540g",loc:"Pantry",status:"ok"},{id:1025,name:"Tomato sauce / passata",qty:"200g",loc:"Pantry",status:"ok"},{id:1026,name:"Tomato paste",qty:"320g",loc:"Pantry",status:"ok"},{id:1027,name:"Red wine",qty:"150ml",loc:"Pantry",status:"ok"},{id:1028,name:"All-purpose flour",qty:"200g",loc:"Pantry",status:"ok"},{id:1029,name:"Fine breadcrumbs",qty:"150g",loc:"Pantry",status:"ok"},{id:1030,name:"Chicken stock cube",qty:"1",loc:"Pantry",status:"ok"},{id:1031,name:"Olive oil",qty:"",loc:"Pantry",status:"ok"},{id:1032,name:"Smoked paprika",qty:"",loc:"Pantry",status:"ok"},{id:1033,name:"Dried oregano",qty:"",loc:"Pantry",status:"ok"},{id:1034,name:"Ground cumin",qty:"",loc:"Pantry",status:"ok"},{id:1035,name:"Cayenne pepper",qty:"",loc:"Pantry",status:"ok"},{id:1036,name:"Garlic powder",qty:"",loc:"Pantry",status:"ok"},{id:1037,name:"Onion powder",qty:"",loc:"Pantry",status:"ok"},{id:1038,name:"Dried thyme",qty:"",loc:"Pantry",status:"ok"},{id:1039,name:"Nutmeg",qty:"",loc:"Pantry",status:"ok"},{id:1040,name:"Salt & Pepper",qty:"",loc:"Pantry",status:"ok"}
];

const SHOPPING_DEFAULT = [
  {id:201,name:"Ground beef 5% fat",qty:"650g",cat:"🥩 Meat",done:false},{id:202,name:"Chicken escalopes",qty:"4 pieces",cat:"🥩 Meat",done:false},{id:203,name:"Heavy cream",qty:"78 cl",cat:"🧀 Dairy",done:false},{id:204,name:"Thick crème fraîche",qty:"2 tbsp",cat:"🧀 Dairy",done:false},{id:205,name:"Mozzarella",qty:"125g",cat:"🧀 Dairy",done:false},{id:206,name:"Monterey Jack / cheddar",qty:"80g",cat:"🧀 Dairy",done:false},{id:207,name:"Parmesan grated",qty:"30g",cat:"🧀 Dairy",done:false},{id:208,name:"Shredded cheese",qty:"25g",cat:"🧀 Dairy",done:false},{id:209,name:"Goat cheese tomme",qty:"100g",cat:"🧀 Dairy",done:false},{id:210,name:"Fresh goat cheese",qty:"150g + 8 tbsp",cat:"🧀 Dairy",done:false},{id:211,name:"Butter",qty:"15g",cat:"🧀 Dairy",done:false},{id:212,name:"Potato gnocchi",qty:"500g",cat:"🥫 Pantry",done:false},{id:213,name:"Chipotle sauce in adobo",qty:"2 tbsp",cat:"🥫 Pantry",done:false}
];

const SOURCE_STYLE = {
  family:     {label:"👨‍👩‍👧 Family",     cls:"badge-family"},
  airfryer:   {label:"⚡ Air Fryer",   cls:"badge-airfryer"},
  ratatouille:{label:"🐭 Ratatouille", cls:"badge-ratatouille"},
};

// ── STATE ─────────────────────────────────────────────────────────────────────
function ld(k,fb){try{const v=localStorage.getItem(k);return v?JSON.parse(v):fb;}catch{return fb;}}
function sv(k,v){try{localStorage.setItem(k,JSON.stringify(v));}catch{}}

let recipes  = ld("mk-recipes",  RECIPES_DEFAULT);
let pantry   = ld("mk-pantry",   PANTRY_DEFAULT);
let shopping = ld("mk-shopping", SHOPPING_DEFAULT);
let activeFilter = "All";
let cookStep = 0;
let cookDone = [];
let cookRecipe = null;

// ── TABS ──────────────────────────────────────────────────────────────────────
function switchTab(t){
  document.querySelectorAll(".tab-btn").forEach((b,i)=>b.classList.toggle("active",["recipes","pantry","shopping"][i]===t));
  document.querySelectorAll(".panel").forEach(p=>p.classList.remove("active"));
  document.getElementById("panel-"+t).classList.add("active");
}

// ── RECIPES ───────────────────────────────────────────────────────────────────
function renderRecipes(){
  // source badges
  const sb=document.getElementById("source-badges");
  sb.innerHTML=Object.entries(SOURCE_STYLE).map(([k,v])=>`<span class="badge ${v.cls}">${v.label}</span>`).join("");

  // filter pills
  const cats=["All",...new Set(recipes.map(r=>r.cat))];
  document.getElementById("filter-row").innerHTML=cats.map(c=>`<button class="pill${activeFilter===c?" active":""}" onclick="setFilter('${c}')">${c}</button>`).join("");

  // recipe cards
  const filtered=activeFilter==="All"?recipes:recipes.filter(r=>r.cat===activeFilter);
  document.getElementById("recipe-list").innerHTML=filtered.map(r=>{
    const src=SOURCE_STYLE[r.source]||{label:r.sourceLabel||"Other",cls:"badge-gray"};
    return `<div class="card">
      <div style="display:flex;justify-content:space-between;align-items:flex-start;margin-bottom:8px">
        <div class="recipe-title">${r.name}</div>
        <button class="btn-del" onclick="deleteRecipe(${r.id})">×</button>
      </div>
      <div style="margin-bottom:10px">
        <span class="badge ${src.cls}">${src.label}</span>
        <span class="badge badge-gray">${r.cat}</span>
        <span class="badge badge-gray">⏱ ${r.time}</span>
      </div>
      ${r.note?`<div class="recipe-note">💡 ${r.note}</div>`:""}
      <button class="btn-expand" onclick="toggleSection(this,'ingr-${r.id}')">
        <span>🧄 Ingredients (${r.ingr.length})</span><span class="hint">▼ show</span>
      </button>
      <div id="ingr-${r.id}" style="display:none" class="ingr-list">
        ${r.ingr.map(i=>`<div>• ${i}</div>`).join("")}
      </div>
      <button class="btn-expand" onclick="toggleSection(this,'steps-${r.id}')">
        <span>📋 Steps (${r.steps.length})</span><span class="hint">▼ show</span>
      </button>
      <ol id="steps-${r.id}" style="display:none" class="steps-list">
        ${r.steps.map(s=>`<li>${s}</li>`).join("")}
      </ol>
      <div style="display:flex;gap:8px;margin-top:10px">
        <button class="btn-cook" onclick="startCooking(${r.id})">👨‍🍳 Cook</button>
        <button class="btn-cart" onclick="addToCart(${r.id})">🛒 To cart</button>
      </div>
    </div>`;
  }).join("");

  document.getElementById("recipe-count").textContent=recipes.length;
  document.getElementById("header-sub").textContent=`${recipes.length} recipes • Pantry • Shopping`;
}

function toggleSection(btn,id){
  const el=document.getElementById(id);
  const hidden=el.style.display==="none";
  el.style.display=hidden?"block":"none";
  btn.querySelector(".hint").textContent=hidden?"▲ hide":"▼ show";
}

function setFilter(cat){activeFilter=cat;renderRecipes();}

function deleteRecipe(id){
  if(!confirm("Delete this recipe?"))return;
  recipes=recipes.filter(r=>r.id!==id);
  sv("mk-recipes",recipes);
  renderRecipes();
}

function addToCart(id){
  const r=recipes.find(x=>x.id===id);if(!r)return;
  let added=0;
  r.ingr.forEach(i=>{
    if(!shopping.find(s=>s.name.toLowerCase()===i.toLowerCase())){
      shopping.push({id:Date.now()+Math.random(),name:i,qty:"",cat:"🛒 Other",done:false});added++;
    }
  });
  sv("mk-shopping",shopping);renderShopping();switchTab("shopping");
  alert(added?`${added} ingredient(s) added!`:"All already in shopping list.");
}

// ── COOKING MODE ──────────────────────────────────────────────────────────────
function startCooking(id){
  cookRecipe=recipes.find(x=>x.id===id);
  if(!cookRecipe)return;
  cookStep=0;cookDone=[];
  renderCooking();
  document.getElementById("overlay-cook").style.display="block";
}

function renderCooking(){
  if(!cookRecipe)return;
  const total=cookRecipe.steps.length;
  const isLast=cookStep===total-1;
  document.getElementById("overlay-cook").innerHTML=`
    <div class="overlay-header">
      <div>
        <div style="font-size:10px;color:#8a8480;text-transform:uppercase;letter-spacing:0.08em">Cooking Mode</div>
        <div style="font-size:15px;font-weight:700;margin-top:2px">${cookRecipe.name}</div>
      </div>
      <button class="btn-ghost" onclick="closeCooking()">✕ Exit</button>
    </div>
    <div style="height:4px;background:#e0dbd4">
      <div style="height:100%;width:${(cookStep/total)*100}%;background:#c85a1a;transition:width 0.3s"></div>
    </div>
    <div style="padding:0.7rem 1rem 0.2rem;font-size:12px;color:#8a8480">Step ${cookStep+1} of ${total}</div>
    <div class="overlay-body">
      <div class="cook-step-box">
        <div class="cook-step-num">Step ${cookStep+1}</div>
        <div class="cook-step-text">${cookRecipe.steps[cookStep]}</div>
      </div>
      <div class="cook-nav">
        <button class="cook-prev" onclick="cookPrev()" ${cookStep===0?"disabled":""}>← Prev</button>
        <button class="cook-next${isLast?" finish":""}" onclick="${isLast?"closeCooking()":"cookNext()"}">${isLast?"🎉 Finished!":"Next →"}</button>
      </div>
      <div class="cook-step-list">
        ${cookRecipe.steps.map((s,i)=>`
          <div class="cook-step-item">
            <span class="cook-step-icon" style="color:${cookDone.includes(i)?"#2d7a3a":i===cookStep?"#c85a1a":"#c0b8b0"}">${cookDone.includes(i)?"✓":i===cookStep?"▶":i+1}</span>
            <span style="font-size:13px;color:${i===cookStep?"#1a1714":"#8a8480"};text-decoration:${cookDone.includes(i)?"line-through":"none"}">${s}</span>
          </div>`).join("")}
      </div>
    </div>`;
}

function cookNext(){if(!cookDone.includes(cookStep))cookDone.push(cookStep);cookStep++;renderCooking();}
function cookPrev(){if(cookStep>0)cookStep--;renderCooking();}
function closeCooking(){document.getElementById("overlay-cook").style.display="none";cookRecipe=null;}

// ── ADD RECIPE ────────────────────────────────────────────────────────────────
function showAddRecipe(){
  document.getElementById("overlay-add").style.display="block";
  renderAddPicker();
}

function closeAdd(){document.getElementById("overlay-add").style.display="none";}

function renderAddPicker(){
  document.getElementById("overlay-add").innerHTML=`
    <div class="overlay-header">
      <div class="overlay-title">➕ Add Recipe</div>
      <button class="btn-ghost" onclick="closeAdd()">✕ Cancel</button>
    </div>
    <div class="overlay-body">
      <div style="font-size:13px;color:#8a8480;margin-bottom:16px">How would you like to add the recipe?</div>
      ${[
        ["📷","Take a photo","Point camera at a recipe book, handwritten note or screen","showPhoto()"],
        ["🔗","Paste a URL","From any recipe website — AI extracts it automatically","showURL()"],
        ["💬","Describe it","Tell AI what you want, it writes the full recipe","showDescribe()"],
        ["✏️","Type manually","Fill in all details yourself","showManual(null)"],
      ].map(([icon,lbl,sub,fn])=>`
        <button class="mode-btn" onclick="${fn}">
          <span class="mode-icon">${icon}</span>
          <div><div class="mode-label">${lbl}</div><div class="mode-sub">${sub}</div></div>
        </button>`).join("")}
    </div>`;
}

function addRecipeHeader(backFn){
  return `<div class="overlay-header">
    <div class="overlay-title">➕ Add Recipe</div>
    <button class="btn-ghost" onclick="${backFn}">← Back</button>
  </div>`;
}

function showPhoto(){
  document.getElementById("overlay-add").innerHTML=`
    ${addRecipeHeader("renderAddPicker()")}
    <div class="overlay-body">
      <p style="font-size:13px;color:#8a8480;margin-bottom:16px;line-height:1.6">Take a photo of any recipe — a book page, handwritten note or screen. AI reads it automatically.</p>
      <input type="file" id="photo-input" accept="image/*" capture="environment" style="display:none" onchange="handlePhoto(this)">
      <input type="file" id="photo-lib" accept="image/*" style="display:none" onchange="handlePhoto(this)">
      <button class="btn-primary" style="margin-bottom:10px" onclick="document.getElementById('photo-input').click()">📷 Open Camera</button>
      <button class="btn-ghost" style="width:100%;padding:13px" onclick="document.getElementById('photo-lib').click()">🖼 Choose from Library</button>
    </div>`;
}

function showURL(){
  document.getElementById("overlay-add").innerHTML=`
    ${addRecipeHeader("renderAddPicker()")}
    <div class="overlay-body">
      <p style="font-size:13px;color:#8a8480;margin-bottom:14px;line-height:1.6">Paste any recipe website URL. AI extracts name, ingredients and steps automatically.</p>
      <input id="url-input" class="inp" placeholder="https://www.marmiton.org/recettes/..." style="margin-bottom:12px">
      <button class="btn-primary" onclick="handleURL()">🔍 Extract Recipe</button>
    </div>`;
}

function showDescribe(){
  document.getElementById("overlay-add").innerHTML=`
    ${addRecipeHeader("renderAddPicker()")}
    <div class="overlay-body">
      <p style="font-size:13px;color:#8a8480;margin-bottom:14px;line-height:1.6">Describe the recipe and AI generates it with full ingredients and steps.</p>
      <textarea id="desc-input" class="inp" rows="3" placeholder="e.g. A classic French onion soup with gruyère croutons" style="margin-bottom:12px;resize:vertical"></textarea>
      <button class="btn-primary" onclick="handleDescribe()">✨ Generate Recipe</button>
    </div>`;
}

function showLoading(){
  document.getElementById("overlay-add").innerHTML=`
    ${addRecipeHeader("renderAddPicker()")}
    <div class="overlay-body">
      <div class="loading"><div class="emoji">🤖</div><div class="title">AI is reading the recipe…</div><div class="sub">Just a few seconds</div></div>
    </div>`;
}

async function handlePhoto(inp){
  const file=inp.files[0];if(!file)return;
  showLoading();
  try{
    const b64=await new Promise((res,rej)=>{const r=new FileReader();r.onload=()=>res(r.result.split(",")[1]);r.onerror=rej;r.readAsDataURL(file);});
    const recipe=await callAI({imageBase64:b64});
    showManual(recipe,true);
  }catch(e){showError("Could not read the photo. Try again or use manual mode.");}
}

async function handleURL(){
  const url=document.getElementById("url-input").value.trim();
  if(!url){alert("Please enter a URL.");return;}
  showLoading();
  try{const recipe=await callAI({url});showManual(recipe,true);}
  catch(e){showError("Could not extract recipe from this URL. Try manual mode.");}
}

async function handleDescribe(){
  const desc=document.getElementById("desc-input").value.trim();
  if(!desc){alert("Please describe the recipe.");return;}
  showLoading();
  try{const recipe=await callAI({description:desc});showManual(recipe,true);}
  catch(e){showError("AI could not generate the recipe. Try again.");}
}

async function callAI({url,imageBase64,description}){
  const prompt=`Extract the recipe and return ONLY valid JSON (no markdown):
{"name":"...","cat":"French|Italian|Mexican|American|Asian|Thai|Middle-Eastern|Other","time":"< 20 min|20–40 min|40–60 min|> 1 hour","source":"other","sourceLabel":"...","ingr":["..."],"steps":["..."],"note":"...or null"}`;
  let content=[];
  if(imageBase64)content=[{type:"image",source:{type:"base64",media_type:"image/jpeg",data:imageBase64}},{type:"text",text:prompt+"\n\nExtract from this image. Keep original language."}];
  else if(url)content=[{type:"text",text:prompt+`\n\nExtract from this URL: ${url}`}];
  else content=[{type:"text",text:prompt+`\n\nCreate a complete recipe for: "${description}"`}];
  const res=await fetch("https://api.anthropic.com/v1/messages",{method:"POST",headers:{"Content-Type":"application/json","x-api-key":["sk-ant-api03-Ly1_D2d","vuqRVlANCWLYlRhH_qKD","kt4-_fXaUGZiJhT3n_GQ","rg4jlLkCQojRDIEhfdpcKYAIss4YgceAunoHXHg-7pp2cAAA"].join(""),"anthropic-version":"2023-06-01","anthropic-dangerous-direct-browser-access":"true"},body:JSON.stringify({model:"claude-sonnet-4-20250514",max_tokens:1000,tools:url?[{type:"web_search_20250305",name:"web_search"}]:undefined,messages:[{role:"user",content}]})});
  const data=await res.json();
  const text=(data.content||[]).filter(b=>b.type==="text").map(b=>b.text).join("");
  return JSON.parse(text.replace(/```json|```/g,"").trim());
}

function showError(msg){
  document.getElementById("overlay-add").innerHTML=`
    ${addRecipeHeader("renderAddPicker()")}
    <div class="overlay-body">
      <div class="msg-error">${msg}</div>
      <button class="btn-primary" onclick="renderAddPicker()">← Try again</button>
    </div>`;
}

function showManual(r,extracted){
  const v=(k,fb)=>r&&r[k]!=null?r[k]:fb;
  document.getElementById("overlay-add").innerHTML=`
    ${addRecipeHeader("renderAddPicker()")}
    <div class="overlay-body">
      ${extracted?'<div class="msg-ok">✓ Recipe extracted — review and save.</div>':""}
      <div class="form-group"><div class="form-label">Recipe name *</div><input id="f-name" class="inp" placeholder="e.g. Poulet rôti" value="${v("name","")}"></div>
      <div class="form-row">
        <div><div class="form-label">Cuisine</div><select id="f-cat" class="inp">${["French","Italian","Mexican","American","Asian","Thai","Middle-Eastern","Other"].map(c=>`<option${v("cat","")==c?" selected":""}>${c}</option>`).join("")}</select></div>
        <div><div class="form-label">Time</div><select id="f-time" class="inp">${["< 20 min","20–40 min","40–60 min","> 1 hour"].map(t=>`<option${v("time","")==t?" selected":""}>${t}</option>`).join("")}</select></div>
      </div>
      <div class="form-row">
        <div><div class="form-label">Source</div><select id="f-source" class="inp"><option value="family"${v("source","")==="family"?" selected":""}>👨‍👩‍👧 Family</option><option value="airfryer"${v("source","")==="airfryer"?" selected":""}>⚡ Air Fryer</option><option value="ratatouille"${v("source","")==="ratatouille"?" selected":""}>🐭 Ratatouille</option><option value="other"${v("source","other")==="other"?" selected":""}>📖 Other</option></select></div>
        <div><div class="form-label">Source label</div><input id="f-sourcelabel" class="inp" placeholder="e.g. Maman" value="${v("sourceLabel","")}"></div>
      </div>
      <div class="form-group"><div class="form-label">Ingredients * — one per line</div><textarea id="f-ingr" class="inp" rows="6" style="resize:vertical">${v("ingr",[]).join("\n")}</textarea></div>
      <div class="form-group"><div class="form-label">Steps * — one per line</div><textarea id="f-steps" class="inp" rows="6" style="resize:vertical">${v("steps",[]).join("\n")}</textarea></div>
      <div class="form-group"><div class="form-label">💡 Tip / note (optional)</div><input id="f-note" class="inp" placeholder="Any useful tip…" value="${v("note","")||""}"></div>
      <button class="btn-primary" onclick="saveNewRecipe()">Save Recipe</button>
    </div>`;
}

function saveNewRecipe(){
  const name=document.getElementById("f-name").value.trim();
  const ingr=document.getElementById("f-ingr").value.trim();
  const steps=document.getElementById("f-steps").value.trim();
  if(!name){alert("Please enter a recipe name.");return;}
  if(!ingr){alert("Please enter at least one ingredient.");return;}
  if(!steps){alert("Please enter at least one step.");return;}
  const recipe={
    id:Date.now(),
    name,
    cat:document.getElementById("f-cat").value,
    time:document.getElementById("f-time").value,
    source:document.getElementById("f-source").value,
    sourceLabel:document.getElementById("f-sourcelabel").value,
    ingr:ingr.split("\n").map(l=>l.trim()).filter(Boolean),
    steps:steps.split("\n").map(l=>l.trim()).filter(Boolean),
    note:document.getElementById("f-note").value.trim()||undefined,
  };
  recipes.push(recipe);
  sv("mk-recipes",recipes);
  closeAdd();
  renderRecipes();
  alert("Recipe saved! 🎉");
}

// ── PANTRY ────────────────────────────────────────────────────────────────────
function renderPantry(){
  const ok=pantry.filter(p=>p.status==="ok").length;
  const low=pantry.filter(p=>p.status==="low").length;
  const out=pantry.filter(p=>p.status==="out").length;
  document.getElementById("stat-ok").textContent=ok;
  document.getElementById("stat-low").textContent=low;
  document.getElementById("stat-out").textContent=out;
  document.getElementById("pantry-count").textContent=pantry.length;

  ["Fridge","Freezer","Pantry"].forEach(loc=>{
    const items=pantry.filter(p=>p.loc===loc);
    const el=document.getElementById("pantry-"+loc.toLowerCase());
    if(!items.length){el.innerHTML="";return;}
    const icons={Fridge:"🧊",Freezer:"❄️",Pantry:"🗄️"};
    el.innerHTML=`<div class="section-title">${icons[loc]} ${loc} — ${items.length} items</div>
      <div class="card" style="padding:6px 12px">
        ${items.map(p=>`<div class="pantry-row">
          <div style="flex:1"><div class="pantry-name">${p.name}</div>${p.qty?`<div class="pantry-qty">${p.qty}</div>`:""}</div>
          <select class="status-select status-${p.status}" onchange="setPantryStatus(${p.id},this.value)">
            <option value="ok"${p.status==="ok"?" selected":""}>Plenty ✓</option>
            <option value="low"${p.status==="low"?" selected":""}>Low ⚠️</option>
            <option value="out"${p.status==="out"?" selected":""}>Out ✕</option>
          </select>
          <button class="btn-del" onclick="deletePantry(${p.id})">×</button>
        </div>`).join("")}
      </div>`;
  });
}

function addPantryItem(){
  const name=document.getElementById("p-name").value.trim();
  if(!name)return;
  pantry.push({id:Date.now(),name,qty:document.getElementById("p-qty").value,loc:document.getElementById("p-loc").value,status:document.getElementById("p-stat").value});
  sv("mk-pantry",pantry);renderPantry();
  document.getElementById("p-name").value="";document.getElementById("p-qty").value="";
}

function setPantryStatus(id,status){
  pantry=pantry.map(p=>p.id===id?{...p,status}:p);
  sv("mk-pantry",pantry);renderPantry();
}

function deletePantry(id){pantry=pantry.filter(p=>p.id!==id);sv("mk-pantry",pantry);renderPantry();}

// ── SHOPPING ──────────────────────────────────────────────────────────────────
function renderShopping(){
  const total=shopping.length;
  const done=shopping.filter(s=>s.done).length;
  const pct=total?Math.round(done/total*100):0;
  const pw=document.getElementById("prog-wrap");
  pw.style.display=total?"block":"none";
  if(total){
    document.getElementById("prog-text").textContent=`${done}/${total} items checked`;
    document.getElementById("prog-pct").textContent=pct===100?"🎉 All done!":pct+"%";
    document.getElementById("prog-fill").style.width=pct+"%";
  }
  document.getElementById("shop-count").textContent=shopping.filter(s=>!s.done).length;

  const cats=[...new Set(shopping.map(s=>s.cat))];
  document.getElementById("shopping-list").innerHTML=cats.map(cat=>{
    const items=shopping.filter(s=>s.cat===cat);
    const catDone=items.filter(s=>s.done).length;
    return `<div class="section-title">${cat} — ${catDone}/${items.length}</div>
      <div class="card" style="padding:0 12px">
        ${items.map(s=>`<div class="shop-row${s.done?" done":""}">
          <input type="checkbox" ${s.done?"checked":""} onchange="toggleShop(${s.id})">
          <span class="shop-name">${s.name}</span>
          ${s.qty?`<span class="shop-qty">(${s.qty})</span>`:""}
          <button class="btn-del" onclick="deleteShop(${s.id})">×</button>
        </div>`).join("")}
      </div>`;
  }).join("")||`<div class="empty"><div class="emoji">🛒</div><div>Shopping list is empty.</div><div style="font-size:12px;margin-top:4px">Tap ⚠️ Add low-stock or 🛒 To cart on a recipe.</div></div>`;
}

function addShoppingItem(){
  const name=document.getElementById("s-name").value.trim();if(!name)return;
  shopping.push({id:Date.now(),name,qty:document.getElementById("s-qty").value,cat:document.getElementById("s-cat").value,done:false});
  sv("mk-shopping",shopping);renderShopping();
  document.getElementById("s-name").value="";document.getElementById("s-qty").value="";
}

function toggleShop(id){shopping=shopping.map(s=>s.id===id?{...s,done:!s.done}:s);sv("mk-shopping",shopping);renderShopping();}
function deleteShop(id){shopping=shopping.filter(s=>s.id!==id);sv("mk-shopping",shopping);renderShopping();}
function clearChecked(){shopping=shopping.filter(s=>!s.done);sv("mk-shopping",shopping);renderShopping();}

function addLowStock(){
  const low=pantry.filter(p=>p.status==="low"||p.status==="out");
  let added=0;
  low.forEach(p=>{if(!shopping.find(s=>s.name.toLowerCase()===p.name.toLowerCase())){shopping.push({id:Date.now()+Math.random(),name:p.name,qty:p.qty||"",cat:"🛒 Other",done:false});added++;}});
  sv("mk-shopping",shopping);renderShopping();
  alert(added?`${added} item(s) added!`:"No low/out items in pantry.");
}

// ── INIT ──────────────────────────────────────────────────────────────────────
renderRecipes();renderPantry();renderShopping();
</script>
</body>
</html>
