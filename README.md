<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Mon site d’articles</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@500;800&family=Newsreader:ital,wght@0,400;0,600;1,400&display=swap" rel="stylesheet">
<style>
  :root {
    --jaune: #FFD93D; --jaune-pale: #FFF0A0;
    --rose: #FF5FA8; --rose-pale: #FFD6E8;
    --prune: #2B1033; --creme: #FFF8E1;
    --titre: "Bricolage Grotesque", "Arial Black", sans-serif;
    --texte: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; margin: 0; }
  html { scroll-behavior: smooth; scroll-padding-top: 5rem; }
  body { background: var(--creme); color: var(--prune); font-family: var(--texte); font-size: 1.15rem; line-height: 1.65; }
  a { color: inherit; }
  :focus-visible { outline: 4px solid var(--prune); outline-offset: 3px; }
  section { padding: clamp(3rem, 7vw, 5.5rem) 5vw; border-bottom: 4px solid var(--prune); }
  .contenu { max-width: 1200px; margin: 0 auto; }
  h2.section-titre { font-family: var(--titre); font-weight: 800; font-size: clamp(2rem, 5vw, 3.4rem); line-height: 1; letter-spacing: -.02em; margin-bottom: .6rem; }
  .sous-titre { font-style: italic; margin-bottom: 2.2rem; max-width: 36rem; }
  .btn { font-family: var(--titre); font-weight: 800; font-size: 1.05rem; color: var(--prune); background: var(--rose); border: 3px solid var(--prune); border-radius: 999px; padding: .55rem 1.4rem; cursor: pointer; text-decoration: none; display: inline-block; box-shadow: 4px 4px 0 var(--prune); transition: transform .12s, box-shadow .12s; }
  .btn:hover { transform: translate(2px, 2px); box-shadow: 2px 2px 0 var(--prune); }
  .btn.jaune { background: var(--jaune); }

  /* Menu */
  .menu { position: sticky; top: 0; z-index: 20; background: var(--jaune); border-bottom: 4px solid var(--prune); padding: .8rem 5vw; display: flex; justify-content: space-between; align-items: center; gap: 1rem; flex-wrap: wrap; }
  .logo { font-family: var(--titre); font-weight: 800; font-size: 1.5rem; text-decoration: none; }
  .menu nav { display: flex; gap: 1.2rem; align-items: center; flex-wrap: wrap; font-family: var(--titre); font-weight: 800; }
  .menu nav a:not(.btn) { text-decoration: none; }
  .menu nav a:not(.btn):hover { text-decoration: underline; text-decoration-thickness: 3px; text-decoration-color: var(--rose); }
  .adminbtn { background: var(--creme); width: 2.8rem; height: 2.8rem; padding: 0; font-size: 1.15rem; line-height: 1; text-align: center; }

  /* Hero */
  .hero { background: var(--jaune); padding-bottom: 4rem; }
  .hero h1 { font-family: var(--titre); font-weight: 800; font-size: clamp(2.8rem, 9vw, 7rem); line-height: .95; letter-spacing: -.03em; max-width: 1000px; }
  .hero h1 .mot { background: var(--rose); padding: 0 .15em; border: 4px solid var(--prune); display: inline-block; transform: rotate(-2deg); box-shadow: 8px 8px 0 var(--prune); margin-top: .15em; }
  .hero p { max-width: 34rem; margin: 2rem 0; font-size: 1.3rem; font-style: italic; }
  .hero .boutons { display: flex; gap: 1rem; flex-wrap: wrap; align-items: center; }
  .pastille { width: 105px; height: 105px; border-radius: 50%; background: var(--rose); border: 4px solid var(--prune); box-shadow: 5px 5px 0 var(--prune); display: grid; place-items: center; text-align: center; font-family: var(--titre); font-weight: 800; font-size: .8rem; line-height: 1.1; transform: rotate(10deg); margin-left: .6rem; }
  .pastille b { font-size: 2rem; display: block; }

  .bandeau { background: var(--prune); color: var(--jaune); overflow: hidden; white-space: nowrap; font-family: var(--titre); font-weight: 800; font-size: 1.4rem; padding: .8rem 0; border-bottom: 4px solid var(--prune); }
  .bandeau div { display: inline-block; animation: defile 30s linear infinite; }
  .bandeau span { margin: 0 1.3rem; } .bandeau .r { color: var(--rose); }
  @keyframes defile { to { transform: translateX(-50%); } }
  @media (prefers-reduced-motion: reduce) { .bandeau div { animation: none; } html { scroll-behavior: auto; } }

  /* Univers */
  .univers { background: var(--creme); }
  .tuiles { display: grid; grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); gap: 1.8rem; }
  .tuile { text-align: left; font: inherit; color: inherit; cursor: pointer; border: 4px solid var(--prune); border-radius: 22px; padding: 1.6rem; box-shadow: 8px 8px 0 var(--prune); transition: transform .15s, box-shadow .15s; display: flex; flex-direction: column; gap: .5rem; }
  .tuile:hover { transform: translate(4px, 4px); box-shadow: 4px 4px 0 var(--prune); }
  .tuile .emoji { font-size: 2.6rem; line-height: 1; }
  .tuile h3 { font-family: var(--titre); font-weight: 800; font-size: 1.8rem; line-height: 1; }
  .tuile small { font-family: var(--titre); font-weight: 800; font-size: .95rem; }
  .t-legendes, .carte.legendes { background: var(--jaune); }
  .t-ecrivains, .carte.ecrivains { background: var(--rose-pale); }
  .t-artistes, .carte.artistes { background: var(--jaune-pale); }
  .t-meurtriers, .carte.meurtriers { background: var(--rose); }

  /* À la une */
  .une { background: var(--rose); }
  .une-carte { background: var(--creme); border: 4px solid var(--prune); border-radius: 26px; box-shadow: 10px 10px 0 var(--prune); padding: clamp(1.6rem, 4vw, 3rem); display: grid; gap: 1rem; max-width: 900px; cursor: pointer; text-align: left; font: inherit; color: inherit; width: 100%; }
  .une-carte:hover { transform: translate(4px, 4px); box-shadow: 6px 6px 0 var(--prune); }
  .une-carte h3 { font-family: var(--titre); font-weight: 800; font-size: clamp(1.9rem, 5vw, 3.2rem); line-height: 1; letter-spacing: -.02em; }

  /* Articles */
  .outils { display: flex; flex-wrap: wrap; gap: 1rem; align-items: center; margin-bottom: 2.2rem; }
  .filtres { display: flex; flex-wrap: wrap; gap: .7rem; }
  .filtres button { font-family: var(--titre); font-weight: 800; font-size: 1rem; background: var(--creme); color: var(--prune); border: 3px solid var(--prune); border-radius: 999px; padding: .4rem 1.1rem; cursor: pointer; box-shadow: 3px 3px 0 var(--prune); }
  .filtres button[aria-pressed="true"] { background: var(--rose); }
  .recherche { flex: 1; min-width: 200px; font: inherit; font-size: 1.05rem; padding: .55rem 1.1rem; border: 3px solid var(--prune); border-radius: 999px; background: #fff; color: var(--prune); }
  .grille { display: grid; grid-template-columns: repeat(auto-fill, minmax(290px, 1fr)); gap: 2rem; }
  .carte { border: 4px solid var(--prune); border-radius: 20px; padding: 1.5rem; display: flex; flex-direction: column; gap: .7rem; box-shadow: 8px 8px 0 var(--prune); text-align: left; font: inherit; color: inherit; cursor: pointer; transition: transform .15s, box-shadow .15s; }
  .carte:hover { transform: translate(4px, 4px); box-shadow: 4px 4px 0 var(--prune); }
  .tag { align-self: flex-start; font-family: var(--titre); font-weight: 800; font-size: .9rem; background: var(--prune); color: var(--creme); border-radius: 999px; padding: .1rem .9rem; }
  .carte h3 { font-family: var(--titre); font-weight: 800; font-size: 1.65rem; line-height: 1.05; }
  .carte p { flex: 1; }
  .meta { font-family: var(--titre); font-weight: 500; font-size: .92rem; }
  .vide { display: none; font-style: italic; margin-top: 1rem; }

  /* À propos */
  .apropos { background: var(--jaune-pale); }
  .apropos-grille { display: grid; grid-template-columns: 1fr 1fr; gap: 3rem; align-items: center; }
  @media (max-width: 800px) { .apropos-grille { grid-template-columns: 1fr; } }
  .portrait { aspect-ratio: 1; background: var(--rose); border: 4px solid var(--prune); border-radius: 30px 30px 120px 30px; box-shadow: 10px 10px 0 var(--prune); display: grid; place-items: center; font-size: 6rem; max-width: 380px; }
  .apropos p + p { margin-top: 1rem; }
  .chiffres { display: flex; gap: 1.2rem; flex-wrap: wrap; margin-top: 1.6rem; }
  .chiffres div { background: var(--creme); border: 3px solid var(--prune); border-radius: 16px; padding: .6rem 1.2rem; font-family: var(--titre); font-weight: 800; text-align: center; }
  .chiffres b { display: block; font-size: 2rem; line-height: 1; }

  footer { background: var(--prune); color: var(--creme); padding: 3rem 5vw; font-family: var(--titre); }
  footer .contenu { display: flex; justify-content: space-between; gap: 1.5rem; flex-wrap: wrap; align-items: center; }
  footer a { color: var(--jaune); }
  .lien-admin { background: none; border: 0; color: var(--jaune); font: inherit; text-decoration: underline; cursor: pointer; }
  .haut { position: fixed; right: 1.2rem; bottom: 1.2rem; z-index: 30; display: none; }

  /* Fenêtres */
  dialog { border: 4px solid var(--prune); border-radius: 24px; padding: 0; width: min(780px, 94vw); max-height: 92vh; background: var(--creme); color: var(--prune); box-shadow: 10px 10px 0 var(--prune); margin: auto; }
  dialog::backdrop { background: rgba(43, 16, 51, .65); }
  .lecture-haut { padding: 1.6rem 2rem 1.2rem; border-bottom: 4px solid var(--prune); position: sticky; top: 0; z-index: 2; background: var(--creme); }
  .lecture-haut h2 { font-family: var(--titre); font-weight: 800; font-size: clamp(1.7rem, 4.5vw, 2.6rem); line-height: 1.02; margin: .6rem 3.5rem .4rem 0; }
  .fermer { position: absolute; right: 1.2rem; top: 1.2rem; width: 2.8rem; height: 2.8rem; padding: 0; font-size: 1.3rem; text-align: center; }
  .lecture-corps { padding: 1.8rem 2rem; max-width: 40rem; }
  .lecture-corps p + p { margin-top: 1.1rem; }
  .commentaires { padding: 1.8rem 2rem 2.2rem; background: #fff; border-top: 4px solid var(--prune); }
  .commentaires h3 { font-family: var(--titre); font-weight: 800; font-size: 1.7rem; margin-bottom: 1rem; }
  .aide-commentaires { background: var(--jaune-pale); border: 3px dashed var(--prune); border-radius: 14px; padding: 1rem 1.2rem; font-size: 1rem; }

  /* Espace auteure */
  .adm { padding: 1.6rem 2rem 2rem; display: grid; gap: 1rem; font-size: 1rem; }
  .adm label { display: grid; gap: .3rem; font-family: var(--titre); font-weight: 800; }
  .adm input, .adm select, .adm textarea { font: inherit; font-weight: 400; font-size: 1rem; padding: .5rem .8rem; border: 3px solid var(--prune); border-radius: 12px; background: #fff; color: var(--prune); width: 100%; }
  .rang { display: flex; gap: .8rem; flex-wrap: wrap; align-items: center; }
  .onglets .btn { font-size: .95rem; padding: .35rem 1rem; }
  .onglets .btn[aria-pressed="true"] { background: var(--jaune); }
  .ligne { display: flex; gap: .8rem; justify-content: space-between; align-items: center; border: 3px solid var(--prune); border-radius: 14px; padding: .6rem 1rem; background: #fff; flex-wrap: wrap; }
  .ligne b { font-family: var(--titre); }
  .ligne .btn { font-size: .85rem; padding: .25rem .8rem; box-shadow: 2px 2px 0 var(--prune); }
  .msg { font-family: var(--titre); font-weight: 800; }
  .erreur { color: #B00020; }
</style>
</head>
<body>

<div class="menu">
  <a class="logo" href="#haut" id="logo"></a>
  <nav>
    <a href="#univers">Univers</a>
    <a href="#articles">Articles</a>
    <a href="#apropos">À propos</a>
    <a class="btn" id="contact" href="#">Me contacter</a>
    <button class="btn adminbtn js-admin" type="button" aria-label="Espace auteure" title="Espace auteure"><span class="cad">🔒</span></button>
  </nav>
</div>

<section class="hero" id="haut">
  <div class="contenu">
    <h1><span id="h1-debut"></span> <span class="mot" id="h1-mot"></span></h1>
    <p id="intro"></p>
    <div class="boutons">
      <a class="btn" href="#articles">Lire les articles</a>
      <button class="btn jaune" id="hasard" type="button">Surprends-moi 🎲</button>
      <div class="pastille"><div><b id="nb-articles">0</b>articles<br>à lire</div></div>
    </div>
  </div>
</section>

<div class="bandeau" aria-hidden="true"><div id="defile"></div></div>

<section class="univers" id="univers">
  <div class="contenu">
    <h2 class="section-titre">Choisis ton univers</h2>
    <p class="sous-titre">Quatre thèmes, quatre ambiances. Clique sur une case pour voir seulement ces articles.</p>
    <div class="tuiles" id="tuiles"></div>
  </div>
</section>

<section class="une" id="une">
  <div class="contenu">
    <h2 class="section-titre">À la une</h2>
    <p class="sous-titre">Le dernier article publié, à ne pas manquer.</p>
    <button class="une-carte" id="une-carte" type="button"></button>
  </div>
</section>

<section id="articles">
  <div class="contenu">
    <h2 class="section-titre">Tous les articles</h2>
    <p class="sous-titre">Filtre par thème ou cherche un mot. Clique sur un article pour le lire et laisser un commentaire.</p>
    <div class="outils">
      <div class="filtres" id="filtres" role="group" aria-label="Filtrer par thème"></div>
      <input class="recherche" id="recherche" type="search" placeholder="Rechercher un article…" aria-label="Rechercher un article">
    </div>
    <div class="grille" id="grille"></div>
    <p class="vide" id="vide">Aucun article ne correspond. Essaie un autre thème ou un autre mot.</p>
  </div>
</section>

<section class="apropos" id="apropos">
  <div class="contenu apropos-grille">
    <div class="portrait" aria-hidden="true">✍️</div>
    <div>
      <h2 class="section-titre">À propos</h2>
      <div id="apropos-txt"></div>
      <div class="chiffres">
        <div><b id="c-articles">0</b>articles</div>
        <div><b>4</b>univers</div>
        <div><b>∞</b>curiosité</div>
      </div>
    </div>
  </div>
</section>

<footer>
  <div class="contenu">
    <span>© <span id="annee"></span> <span id="pied-nom"></span> · Tous droits réservés</span>
    <span>Une idée d’article ? <a id="pied-contact" href="#">Écris-moi</a></span>
    <button class="lien-admin js-admin" type="button"><span class="cad">🔒</span> Espace auteure</button>
  </div>
</footer>

<a class="btn jaune haut" id="haut-btn" href="#haut" aria-label="Retour en haut">↑</a>

<dialog id="lecture" aria-labelledby="lecture-titre">
  <div class="lecture-haut">
    <span class="tag" id="lecture-tag"></span>
    <h2 id="lecture-titre"></h2>
    <div class="meta" id="lecture-meta"></div>
    <button class="btn fermer" id="fermer" type="button" aria-label="Fermer">✕</button>
  </div>
  <div class="lecture-corps" id="lecture-corps"></div>
  <div class="commentaires">
    <h3>💬 Commentaires</h3>
    <div id="zone-commentaires"></div>
  </div>
</dialog>

<dialog id="admin" aria-labelledby="admin-titre">
  <div class="lecture-haut">
    <h2 id="admin-titre">Espace auteure</h2>
    <button class="btn fermer" id="admin-fermer" type="button" aria-label="Fermer">✕</button>
  </div>
  <div class="adm" id="adm"></div>
</dialog>

<script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-app-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-auth-compat.js"></script>
<script src="https://www.gstatic.com/firebasejs/10.12.2/firebase-firestore-compat.js"></script>
<script>
  /* ============ 1. FIREBASE (espace auteure + stockage des articles) ============
     Colle ici les 4 valeurs de ta console Firebase. */
  const FIREBASE = { apiKey: "", authDomain: "", projectId: "", appId: "" };

  /* ============ 2. COMMENTAIRES (Giscus) ============ */
  const GISCUS = { repo: "", repoId: "", category: "", categoryId: "" };

  /* ============ 3. TEXTES PAR DÉFAUT ============ */
  const REG0 = {
    nomSite: "Mon site",
    titreDebut: "Légendes, plumes, pinceaux et",
    titreMot: "crimes.",
    intro: "Bienvenue ! Ici je raconte ceux qu’on n’oublie pas : les héros de légende, les écrivains, les artistes… et les meurtriers. Installe-toi, lis, et dis-moi ce que tu en penses en commentaire.",
    email: "ton.adresse@mail.com",
    apropos: "Salut, moi c’est [ton prénom ou pseudo]. J’écris sur les histoires qui fascinent : celles qu’on se raconte depuis des siècles, celles des gens qui créent, et les plus sombres aussi.\n\nModifie ce texte depuis ton espace auteure (le cadenas dans le menu)."
  };
  const DEMO = [
    { id: "a1", theme: "legendes", date: "2026-11-01", minutes: 5, titre: "Article de démonstration", resume: "Configure Firebase puis publie tes vrais articles depuis l’espace auteure.", texte: ["Ceci est un exemple. Il disparaîtra dès que Firebase sera configuré."] }
  ];
  const univers = {
    legendes:   { nom: "Légendes",   emoji: "🐉", desc: "Héros, monstres et récits qui traversent les siècles." },
    ecrivains:  { nom: "Écrivains",  emoji: "🪶", desc: "Les vies et les plumes derrière les grands livres." },
    artistes:   { nom: "Artistes",   emoji: "🎨", desc: "Peintres, musiciens, créateurs et leurs œuvres." },
    meurtriers: { nom: "Meurtriers", emoji: "🔪", desc: "Des affaires criminelles célèbres, racontées avec soin." }
  };

  const $ = id => document.getElementById(id);
  const fmt = d => new Date(d).toLocaleDateString("fr-FR", { day: "numeric", month: "long", year: "numeric" });
  const enligne = !!FIREBASE.apiKey;
  let articles = enligne ? [] : DEMO, reg = { ...REG0 }, tri = [], theme = "tous", requete = "", user = null, db, auth;

  /* ---------- Réglages du site ---------- */
  function appliquerReg() {
    $("logo").textContent = reg.nomSite + " ✦";
    $("h1-debut").textContent = reg.titreDebut;
    $("h1-mot").textContent = reg.titreMot;
    $("intro").textContent = reg.intro;
    $("pied-nom").textContent = reg.nomSite;
    document.title = reg.nomSite;
    ["contact", "pied-contact"].forEach(i => $(i).href = "mailto:" + reg.email);
    const z = $("apropos-txt"); z.innerHTML = "";
    reg.apropos.split(/\n\s*\n/).forEach(t => { const p = document.createElement("p"); p.textContent = t; z.appendChild(p); });
  }

  /* ---------- Affichage public ---------- */
  function rendre() {
    tri = [...articles].sort((a, b) => b.date.localeCompare(a.date));
    $("nb-articles").textContent = $("c-articles").textContent = articles.length;

    $("tuiles").innerHTML = "";
    Object.entries(univers).forEach(([cle, u]) => {
      const n = articles.filter(a => a.theme === cle).length;
      const t = document.createElement("button");
      t.type = "button"; t.className = "tuile t-" + cle;
      t.innerHTML = '<span class="emoji"></span><h3></h3><p></p><small></small>';
      t.querySelector(".emoji").textContent = u.emoji;
      t.querySelector("h3").textContent = u.nom;
      t.querySelector("p").textContent = u.desc;
      t.querySelector("small").textContent = n + (n > 1 ? " articles" : " article");
      t.onclick = () => { choisir(cle); $("articles").scrollIntoView(); };
      $("tuiles").appendChild(t);
    });

    const une = tri[0], c = $("une-carte");
    $("une").style.display = une ? "" : "none";
    if (une) {
      c.innerHTML = '<span class="tag"></span><h3></h3><p></p><span class="meta"></span>';
      c.querySelector(".tag").textContent = univers[une.theme].nom;
      c.querySelector("h3").textContent = une.titre;
      c.querySelector("p").textContent = une.resume;
      c.querySelector(".meta").textContent = fmt(une.date) + " · " + une.minutes + " min de lecture";
      c.onclick = () => ouvrir(une);
    }
    afficher();
  }
  function afficher() {
    const g = $("grille"); g.innerHTML = "";
    const liste = tri.filter(a => (theme === "tous" || a.theme === theme) && (a.titre + " " + a.resume).toLowerCase().includes(requete));
    liste.forEach(a => {
      const el = document.createElement("button");
      el.type = "button"; el.className = "carte " + a.theme;
      el.innerHTML = '<span class="tag"></span><h3></h3><p></p><span class="meta"></span>';
      el.querySelector(".tag").textContent = univers[a.theme].emoji + " " + univers[a.theme].nom;
      el.querySelector("h3").textContent = a.titre;
      el.querySelector("p").textContent = a.resume;
      el.querySelector(".meta").textContent = fmt(a.date) + " · " + a.minutes + " min";
      el.onclick = () => ouvrir(a);
      g.appendChild(el);
    });
    $("vide").style.display = liste.length ? "none" : "block";
  }
  function choisir(cle) {
    theme = cle;
    document.querySelectorAll("#filtres button").forEach(b => b.setAttribute("aria-pressed", b.dataset.theme === cle));
    afficher();
  }
  [["tous", "Tout"], ...Object.entries(univers).map(([k, u]) => [k, u.nom])].forEach(([cle, nom]) => {
    const b = document.createElement("button");
    b.type = "button"; b.textContent = nom; b.dataset.theme = cle;
    b.setAttribute("aria-pressed", cle === "tous");
    b.onclick = () => choisir(cle);
    $("filtres").appendChild(b);
  });
  $("recherche").addEventListener("input", e => { requete = e.target.value.toLowerCase(); afficher(); });

  // Bandeau
  const mots = Object.values(univers).map(u => u.nom);
  let bande = "";
  for (let i = 0; i < 16; i++) bande += '<span class="' + (i % 2 ? "r" : "") + '">' + mots[i % 4] + "</span>";
  $("defile").innerHTML = bande + bande;
  $("annee").textContent = new Date().getFullYear();

  /* ---------- Lecture + commentaires ---------- */
  const dlg = $("lecture");
  function ouvrir(a) {
    $("lecture-tag").textContent = univers[a.theme].emoji + " " + univers[a.theme].nom;
    $("lecture-titre").textContent = a.titre;
    $("lecture-meta").textContent = fmt(a.date) + " · " + a.minutes + " min de lecture";
    const corps = $("lecture-corps"); corps.innerHTML = "";
    a.texte.forEach(t => { const p = document.createElement("p"); p.textContent = t; corps.appendChild(p); });
    chargerCommentaires(a);
    dlg.showModal(); dlg.scrollTop = 0;
  }
  function chargerCommentaires(a) {
    const z = $("zone-commentaires"); z.innerHTML = "";
    if (!GISCUS.repo) {
      z.innerHTML = '<div class="aide-commentaires">Les commentaires ne sont pas encore activés (ligne <b>GISCUS</b> en haut du script).</div>';
      return;
    }
    const s = document.createElement("script");
    s.src = "https://giscus.app/client.js";
    const attrs = { repo: GISCUS.repo, "repo-id": GISCUS.repoId, category: GISCUS.category, "category-id": GISCUS.categoryId,
      mapping: "specific", term: a.id, "reactions-enabled": "1", "emit-metadata": "0",
      "input-position": "top", theme: "light", lang: "fr", loading: "lazy" };
    Object.entries(attrs).forEach(([k, v]) => s.setAttribute("data-" + k, v));
    s.crossOrigin = "anonymous"; s.async = true;
    z.appendChild(s);
  }
  $("fermer").onclick = () => dlg.close();
  dlg.addEventListener("click", e => { if (e.target === dlg) dlg.close(); });
  dlg.addEventListener("close", () => { $("zone-commentaires").innerHTML = ""; });
  $("hasard").onclick = () => { if (articles.length) ouvrir(articles[Math.floor(Math.random() * articles.length)]); };
  addEventListener("scroll", () => { $("haut-btn").style.display = scrollY > 700 ? "inline-block" : "none"; });

  /* ---------- Espace auteure ---------- */
  const adm = $("adm"), ad = $("admin");
  const today = () => new Date().toISOString().slice(0, 10);
  const optTheme = Object.entries(univers).map(([k, u]) => `<option value="${k}">${u.emoji} ${u.nom}</option>`).join("");
  const msg = (t, err) => { const m = $("msg"); if (m) { m.textContent = t; m.className = "msg" + (err ? " erreur" : ""); } };

  document.querySelectorAll(".js-admin").forEach(b => b.onclick = () => { vue(); ad.showModal(); });
  $("admin-fermer").onclick = () => ad.close();
  ad.addEventListener("click", e => { if (e.target === ad) ad.close(); });

  function vue(nom, a) {
    if (!enligne) {
      adm.innerHTML = '<p>L’espace auteure n’est pas encore activé : remplis la ligne <b>FIREBASE</b> en haut du script en suivant les étapes.</p>';
      return;
    }
    if (!user) return vueLogin();
    if (nom === "edition") return vueEdition(a);
    if (nom === "reglages") return vueReglages();
    vueListe();
  }
  function barre(actif) {
    return `<div class="rang onglets">
      <button class="btn" data-v="liste" aria-pressed="${actif === "liste"}" type="button">📝 Articles</button>
      <button class="btn" data-v="reglages" aria-pressed="${actif === "reglages"}" type="button">⚙️ Réglages du site</button>
      <button class="btn jaune" data-v="out" type="button">Déconnexion</button></div>`;
  }
  function brancherBarre() {
    adm.querySelectorAll("[data-v]").forEach(b => b.onclick = () => {
      if (b.dataset.v === "out") { auth.signOut(); ad.close(); } else vue(b.dataset.v);
    });
  }

  function vueLogin() {
    adm.innerHTML = `<label>E-mail<input id="l-mail" type="email" autocomplete="username"></label>
      <label>Mot de passe<input id="l-mdp" type="password" autocomplete="current-password"></label>
      <div class="rang"><button class="btn" id="l-ok" type="button">Entrer</button></div><p id="msg" class="msg"></p>`;
    const go = () => auth.signInWithEmailAndPassword($("l-mail").value.trim(), $("l-mdp").value)
      .then(() => vue()).catch(() => msg("E-mail ou mot de passe incorrect.", true));
    $("l-ok").onclick = go;
    $("l-mdp").onkeydown = e => { if (e.key === "Enter") go(); };
  }

  function vueListe() {
    adm.innerHTML = barre("liste") + '<div class="rang"><button class="btn" id="nouveau" type="button">＋ Nouvel article</button></div><div id="liste" style="display:grid;gap:.7rem"></div><p id="msg" class="msg"></p>';
    brancherBarre();
    $("nouveau").onclick = () => vue("edition");
    const l = $("liste");
    if (!tri.length) l.textContent = "Aucun article pour l’instant.";
    tri.forEach(a => {
      const r = document.createElement("div"); r.className = "ligne";
      r.innerHTML = '<span><b></b><br><small></small></span><span class="rang"><button class="btn" type="button">Modifier</button><button class="btn jaune" type="button">Supprimer</button></span>';
      r.querySelector("b").textContent = a.titre;
      r.querySelector("small").textContent = univers[a.theme].nom + " · " + fmt(a.date);
      const [m, s] = r.querySelectorAll("button");
      m.onclick = () => vue("edition", a);
      s.onclick = () => { if (confirm("Supprimer « " + a.titre + " » ?")) db.collection("articles").doc(a.id).delete().then(() => msg("Article supprimé.")).catch(() => msg("Suppression refusée.", true)); };
      l.appendChild(r);
    });
  }

  function vueEdition(a) {
    a = a || { theme: "legendes", date: today(), minutes: 5, titre: "", resume: "", texte: [] };
    adm.innerHTML = `<h3 style="font-family:var(--titre)">${a.id ? "Modifier l’article" : "Nouvel article"}</h3>
      <label>Titre<input id="e-titre"></label>
      <label>Thème<select id="e-theme">${optTheme}</select></label>
      <label>Date<input id="e-date" type="date"></label>
      <label>Minutes de lecture<input id="e-min" type="number" min="1"></label>
      <label>Résumé (2-3 phrases)<textarea id="e-resume" rows="3"></textarea></label>
      <label>Texte (une ligne vide = nouveau paragraphe)<textarea id="e-texte" rows="12"></textarea></label>
      <div class="rang"><button class="btn" id="e-ok" type="button">Publier</button><button class="btn jaune" id="e-non" type="button">Annuler</button></div><p id="msg" class="msg"></p>`;
    $("e-titre").value = a.titre; $("e-theme").value = a.theme; $("e-date").value = a.date;
    $("e-min").value = a.minutes; $("e-resume").value = a.resume; $("e-texte").value = a.texte.join("\n\n");
    $("e-non").onclick = () => vue();
    $("e-ok").onclick = () => {
      const d = { titre: $("e-titre").value.trim(), theme: $("e-theme").value, date: $("e-date").value || today(),
        minutes: +$("e-min").value || 5, resume: $("e-resume").value.trim(),
        texte: $("e-texte").value.split(/\n\s*\n/).map(t => t.trim()).filter(Boolean) };
      if (!d.titre || !d.texte.length) return msg("Il faut au moins un titre et un texte.", true);
      const ref = a.id ? db.collection("articles").doc(a.id).set(d) : db.collection("articles").add(d);
      ref.then(() => vue()).catch(() => msg("Publication refusée (vérifie les règles Firebase).", true));
    };
  }

  function vueReglages() {
    adm.innerHTML = barre("reglages") + `
      <label>Nom du site<input id="r-nom"></label>
      <label>Grand titre (début)<input id="r-deb"></label>
      <label>Grand titre (mot en rose)<input id="r-mot"></label>
      <label>Phrase d’accueil<textarea id="r-intro" rows="4"></textarea></label>
      <label>E-mail de contact<input id="r-mail" type="email"></label>
      <label>Texte « À propos » (ligne vide = nouveau paragraphe)<textarea id="r-apropos" rows="8"></textarea></label>
      <div class="rang"><button class="btn" id="r-ok" type="button">Enregistrer</button></div><p id="msg" class="msg"></p>`;
    brancherBarre();
    $("r-nom").value = reg.nomSite; $("r-deb").value = reg.titreDebut; $("r-mot").value = reg.titreMot;
    $("r-intro").value = reg.intro; $("r-mail").value = reg.email; $("r-apropos").value = reg.apropos;
    $("r-ok").onclick = () => {
      const d = { nomSite: $("r-nom").value, titreDebut: $("r-deb").value, titreMot: $("r-mot").value,
        intro: $("r-intro").value, email: $("r-mail").value, apropos: $("r-apropos").value };
      db.doc("site/reglages").set(d).then(() => msg("Enregistré ✔")).catch(() => msg("Enregistrement refusé.", true));
    };
  }

  /* ---------- Démarrage ---------- */
  appliquerReg(); rendre();
  if (enligne) {
    firebase.initializeApp(FIREBASE);
    db = firebase.firestore(); auth = firebase.auth();
    auth.onAuthStateChanged(u => {
      user = u;
      document.querySelectorAll(".cad").forEach(e => e.textContent = u ? "✏️" : "🔒");
      if (ad.open) vue();
    });
    db.collection("articles").onSnapshot(s => {
      articles = s.docs.map(d => ({ id: d.id, ...d.data() }));
      rendre(); if (ad.open && user && !$("e-ok")) vue();
    }, () => {});
    db.doc("site/reglages").onSnapshot(s => { if (s.exists) { reg = { ...REG0, ...s.data() }; appliquerReg(); } }, () => {});
  }
</script>
</body>
</html>
