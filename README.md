<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Mon site d’articles</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@500;800&family=Newsreader:ital,wght@0,400;1,400&display=swap" rel="stylesheet">
<style>
  :root {
    --jaune: #FFE14D;
    --jaune-pale: #FFF3A8;
    --rose: #FF4FA3;
    --rose-pale: #FFC2DE;
    --encre: #2A1230;
    --papier: #FFFBEA;
    --titre: "Bricolage Grotesque", "Arial Black", sans-serif;
    --texte: "Newsreader", Georgia, serif;
  }
  * { box-sizing: border-box; margin: 0; }
  html { scroll-behavior: smooth; }
  body {
    background: var(--papier);
    color: var(--encre);
    font-family: var(--texte);
    font-size: 1.15rem;
    line-height: 1.6;
  }
  a { color: inherit; }
  :focus-visible { outline: 4px solid var(--encre); outline-offset: 3px; }

  /* En-tête */
  header {
    background: var(--jaune);
    border-bottom: 4px solid var(--encre);
    padding: 1.2rem 5vw 0;
    position: relative;
    overflow: hidden;
  }
  nav { display: flex; justify-content: space-between; align-items: center; gap: 1rem; }
  .logo { font-family: var(--titre); font-weight: 800; font-size: 1.4rem; text-decoration: none; }
  nav a.contact {
    font-family: var(--titre); font-weight: 800; font-size: 1rem;
    background: var(--rose); color: var(--encre);
    border: 3px solid var(--encre); border-radius: 999px;
    padding: .4rem 1.1rem; text-decoration: none;
    box-shadow: 4px 4px 0 var(--encre);
  }
  nav a.contact:hover { transform: translate(2px, 2px); box-shadow: 2px 2px 0 var(--encre); }

  .hero { padding: clamp(2.5rem, 8vw, 6rem) 0 clamp(2rem, 5vw, 4rem); max-width: 1100px; }
  .hero h1 {
    font-family: var(--titre); font-weight: 800;
    font-size: clamp(3rem, 11vw, 8rem);
    line-height: .92; letter-spacing: -.03em;
  }
  .hero h1 span {
    background: var(--rose);
    padding: 0 .15em;
    border: 4px solid var(--encre);
    display: inline-block;
    transform: rotate(-2deg);
    box-shadow: 8px 8px 0 var(--encre);
    margin-top: .15em;
  }
  .hero p { max-width: 34rem; margin-top: 2rem; font-size: 1.3rem; font-style: italic; }

  /* Bandeau défilant */
  .bandeau {
    background: var(--encre); color: var(--jaune);
    margin: 0 -5vw; overflow: hidden; white-space: nowrap;
    font-family: var(--titre); font-weight: 800; font-size: 1.3rem;
    padding: .7rem 0; border-top: 4px solid var(--encre);
  }
  .bandeau div { display: inline-block; animation: defile 28s linear infinite; }
  .bandeau span { margin: 0 1.2rem; }
  .bandeau .r { color: var(--rose); }
  @keyframes defile { to { transform: translateX(-50%); } }
  @media (prefers-reduced-motion: reduce) { .bandeau div { animation: none; } html { scroll-behavior: auto; } }

  /* Filtres */
  main { padding: 3rem 5vw 4rem; max-width: 1250px; margin: 0 auto; }
  .filtres { display: flex; flex-wrap: wrap; gap: .8rem; margin-bottom: 2.5rem; }
  .filtres button {
    font-family: var(--titre); font-weight: 800; font-size: 1.05rem;
    background: var(--papier); color: var(--encre);
    border: 3px solid var(--encre); border-radius: 999px;
    padding: .5rem 1.3rem; cursor: pointer;
    box-shadow: 4px 4px 0 var(--encre);
  }
  .filtres button:hover { transform: translate(2px, 2px); box-shadow: 2px 2px 0 var(--encre); }
  .filtres button[aria-pressed="true"] { background: var(--rose); }

  /* Cartes */
  .grille { display: grid; grid-template-columns: repeat(auto-fill, minmax(290px, 1fr)); gap: 2rem; }
  .carte {
    border: 4px solid var(--encre); border-radius: 18px;
    padding: 1.5rem; display: flex; flex-direction: column; gap: .8rem;
    box-shadow: 8px 8px 0 var(--encre);
    text-decoration: none;
    transition: transform .15s, box-shadow .15s;
  }
  .carte:hover { transform: translate(4px, 4px); box-shadow: 4px 4px 0 var(--encre); }
  .carte.legendes { background: var(--jaune); }
  .carte.ecrivains { background: var(--rose-pale); }
  .carte.artistes { background: var(--jaune-pale); }
  .carte.meurtriers { background: var(--rose); }
  .tag {
    align-self: flex-start; font-family: var(--titre); font-weight: 800; font-size: .95rem;
    background: var(--encre); color: var(--papier);
    border-radius: 999px; padding: .15rem .9rem;
  }
  .carte h2 { font-family: var(--titre); font-weight: 800; font-size: 1.7rem; line-height: 1.05; letter-spacing: -.01em; }
  .carte p { flex: 1; }
  .carte time { font-family: var(--titre); font-weight: 500; font-size: .95rem; }
  .vide { display: none; font-style: italic; }

  footer {
    background: var(--rose); border-top: 4px solid var(--encre);
    padding: 2rem 5vw; font-family: var(--titre); font-weight: 500;
  }
</style>
</head>
<body>

<header>
  <nav>
    <a class="logo" href="#">Mon site</a>
    <a class="contact" href="mailto:ton.adresse@mail.com">Me contacter</a>
  </nav>
  <div class="hero">
    <h1>Légendes, plumes, pinceaux et <span>crimes.</span></h1>
    <p>Des articles sur ceux qu’on raconte encore, ceux qui écrivent, ceux qui peignent, et ceux qui tuent.</p>
  </div>
  <div class="bandeau" aria-hidden="true">
    <div id="defile"></div>
  </div>
</header>

<main id="articles">
  <div class="filtres" role="group" aria-label="Filtrer par thème">
    <button aria-pressed="true" data-theme="tous">Tout</button>
    <button aria-pressed="false" data-theme="legendes">Légendes</button>
    <button aria-pressed="false" data-theme="ecrivains">Écrivains</button>
    <button aria-pressed="false" data-theme="artistes">Artistes</button>
    <button aria-pressed="false" data-theme="meurtriers">Meurtriers</button>
  </div>
  <div class="grille" id="grille"></div>
  <p class="vide" id="vide">Aucun article dans ce thème pour le moment.</p>
</main>

<footer>© <span id="annee"></span> · Tous droits réservés</footer>

<script>
  /* ====== TES ARTICLES : copie un bloc { ... } pour en ajouter un ======
     theme : legendes, ecrivains, artistes ou meurtriers
     lien  : adresse de la page de l'article (ex. "articles/mon-article.html") */
  const articles = [
    { titre: "Titre de ton article sur une légende", theme: "legendes", date: "2026-11-01",
      resume: "Deux ou trois phrases pour donner envie de lire la suite.", lien: "#" },
    { titre: "Titre de ton article sur un écrivain", theme: "ecrivains", date: "2026-10-20",
      resume: "Deux ou trois phrases pour donner envie de lire la suite.", lien: "#" },
    { titre: "Titre de ton article sur un artiste", theme: "artistes", date: "2026-10-05",
      resume: "Deux ou trois phrases pour donner envie de lire la suite.", lien: "#" },
    { titre: "Titre de ton article sur un meurtrier", theme: "meurtriers", date: "2026-09-18",
      resume: "Deux ou trois phrases pour donner envie de lire la suite.", lien: "#" }
  ];

  const noms = { legendes: "Légendes", ecrivains: "Écrivains", artistes: "Artistes", meurtriers: "Meurtriers" };
  const grille = document.getElementById("grille");
  const vide = document.getElementById("vide");

  function afficher(theme) {
    grille.innerHTML = "";
    const liste = articles
      .filter(a => theme === "tous" || a.theme === theme)
      .sort((a, b) => b.date.localeCompare(a.date));
    liste.forEach(a => {
      const el = document.createElement("a");
      el.className = "carte " + a.theme;
      el.href = a.lien;
      const d = new Date(a.date).toLocaleDateString("fr-FR", { day: "numeric", month: "long", year: "numeric" });
      el.innerHTML = '<span class="tag"></span><h2></h2><p></p><time></time>';
      el.querySelector(".tag").textContent = noms[a.theme];
      el.querySelector("h2").textContent = a.titre;
      el.querySelector("p").textContent = a.resume;
      el.querySelector("time").textContent = d;
      grille.appendChild(el);
    });
    vide.style.display = liste.length ? "none" : "block";
  }

  document.querySelectorAll(".filtres button").forEach(b => {
    b.addEventListener("click", () => {
      document.querySelectorAll(".filtres button").forEach(x => x.setAttribute("aria-pressed", "false"));
      b.setAttribute("aria-pressed", "true");
      afficher(b.dataset.theme);
    });
  });

  // Bandeau défilant
  const mots = ["Légendes", "Écrivains", "Artistes", "Meurtriers"];
  let bande = "";
  for (let i = 0; i < 16; i++) bande += '<span class="' + (i % 2 ? "r" : "") + '">' + mots[i % 4] + "</span>";
  document.getElementById("defile").innerHTML = bande + bande;

  document.getElementById("annee").textContent = new Date().getFullYear();
  afficher("tous");
</script>
</body>
</html>
