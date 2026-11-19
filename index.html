
<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Karaoké & Louange</title>
<style>
:root {
  --gold:#b58a3b;
  --cream:#f8f5ee;
  --ink:#302b26;
  --muted:#766f65;
}
* { box-sizing:border-box; }
body {
  margin:0;
  font-family:Arial,sans-serif;
  background:var(--cream);
  color:var(--ink);
}
header {
  background:white;
  padding:28px 18px;
  text-align:center;
  border-bottom:1px solid #eadfca;
}
h1 { margin:0; color:var(--gold); font-size:28px; }
header p { color:var(--muted); margin:9px 0 0; }
main { max-width:950px; margin:auto; padding:20px; }
.panel {
  background:white;
  padding:18px;
  border:1px solid #eadfca;
  border-radius:15px;
  margin-bottom:18px;
}
h2 { font-size:19px; margin-top:0; }
input,select,button {
  width:100%;
  padding:12px;
  margin:6px 0;
  border:1px solid #ded5c6;
  border-radius:9px;
  font-size:15px;
}
button {
  background:var(--gold);
  color:white;
  border:0;
  font-weight:bold;
  cursor:pointer;
}
button.secondary {
  background:#f1eadc;
  color:#5c4828;
}
.filters {
  display:grid;
  grid-template-columns:repeat(auto-fit,minmax(150px,1fr));
  gap:8px;
}
.song {
  padding:15px 0;
  border-bottom:1px solid #eee5d8;
}
.song:last-child { border-bottom:0; }
.song h3 { margin:0 0 6px; }
.meta { color:var(--muted); font-size:13px; }
.actions {
  display:flex;
  gap:8px;
  flex-wrap:wrap;
  margin-top:10px;
}
.actions button { width:auto; }
iframe {
  width:100%;
  aspect-ratio:16/9;
  border:0;
  border-radius:12px;
  margin-top:12px;
}
.empty { color:var(--muted); text-align:center; padding:20px; }
footer { text-align:center; color:var(--muted); padding:25px; font-size:13px; }
</style>
</head>
<body>

<header>
  <h1>♫ Karaoké & Louange</h1>
  <p>Chantons ensemble pour célébrer Dieu</p>
</header>

<main>
  <section class="panel">
    <h2>🔎 Trouver un chant</h2>
    <input id="search" placeholder="Rechercher un titre ou un artiste...">
    <div class="filters">
      <select id="language">
        <option value="">Toutes les langues</option>
        <option>Français</option>
        <option>Anglais</option>
        <option>Lingala</option>
        <option>Créole</option>
        <option>Swahili</option>
        <option>Espagnol</option>
      </select>
      <select id="category">
        <option value="">Toutes les catégories</option>
        <option>Louange</option>
        <option>Adoration</option>
        <option>Gospel</option>
        <option>Jeunesse</option>
        <option>Gospel africain</option>
      </select>
      <select id="view">
        <option value="all">Tous les chants</option>
        <option value="favorites">Mes favoris</option>
        <option value="queue">Ma file d'attente</option>
      </select>
    </div>
  </section>

  <section class="panel">
    <h2>🎵 Ajouter un chant</h2>
    <form id="songForm">
      <input id="title" placeholder="Titre du chant" required>
      <input id="artist" placeholder="Artiste ou groupe">
      <select id="newLanguage" required>
        <option value="">Choisir la langue</option>
        <option>Français</option>
        <option>Anglais</option>
        <option>Lingala</option>
        <option>Créole</option>
        <option>Swahili</option>
        <option>Espagnol</option>
      </select>
      <select id="newCategory" required>
        <option value="">Choisir la catégorie</option>
        <option>Louange</option>
        <option>Adoration</option>
        <option>Gospel</option>
        <option>Jeunesse</option>
        <option>Gospel africain</option>
      </select>
      <input id="youtube" type="url" placeholder="Lien YouTube de la vidéo karaoké" required>
      <button type="submit">Ajouter à la bibliothèque</button>
    </form>
  </section>

  <section class="panel">
    <h2>📚 Bibliothèque de chants</h2>
    <div id="songs"></div>
  </section>

  <section class="panel" id="playerPanel" hidden>
    <h2 id="playingTitle">Lecture</h2>
    <div id="player"></div>
    <button class="secondary" onclick="closePlayer()">Fermer le lecteur</button>
  </section>
</main>

<footer>
  Karaoké & Louange — Chantons ensemble dans la joie.
</footer>

<script>
const STORAGE_KEY = "karaokeLouangeSongs";
let songs = JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");
let favorites = JSON.parse(localStorage.getItem("karaokeFavorites") || "[]");
let queue = JSON.parse(localStorage.getItem("karaokeQueue") || "[]");

const $ = id => document.getElementById(id);

function save() {
  localStorage.setItem(STORAGE_KEY, JSON.stringify(songs));
  localStorage.setItem("karaokeFavorites", JSON.stringify(favorites));
  localStorage.setItem("karaokeQueue", JSON.stringify(queue));
}

function videoId(url) {
  try {
    const u = new URL(url);
    if (u.hostname.includes("youtu.be")) return u.pathname.slice(1);
    if (u.hostname.includes("youtube.com")) {
      if (u.pathname === "/watch") return u.searchParams.get("v");
      if (u.pathname.startsWith("/embed/")) return u.pathname.split("/")[2];
      if (u.pathname.startsWith("/shorts/")) return u.pathname.split("/")[2];
    }
  } catch(e) {}
  return null;
}

function render() {
  const term = $("search").value.toLowerCase();
  const lang = $("language").value;
  const cat = $("category").value;
  const mode = $("view").value;

  const filtered = songs.filter(s => {
    const matches = (s.title + " " + s.artist).toLowerCase().includes(term);
    return matches &&
      (!lang || s.language === lang) &&
      (!cat || s.category === cat) &&
      (mode === "all" ||
       (mode === "favorites" && favorites.includes(s.id)) ||
       (mode === "queue" && queue.includes(s.id)));
  });

  $("songs").innerHTML = "";

  if (!filtered.length) {
    $("songs").innerHTML = '<p class="empty">Aucun chant trouvé pour le moment. Tu peux ajouter le premier chant ci-dessus !</p>';
    return;
  }

  filtered.forEach(s => {
    const item = document.createElement("article");
    item.className = "song";

    const heading = document.createElement("h3");
    heading.textContent = s.title;
    const meta = document.createElement("div");
    meta.className = "meta";
    meta.textContent = [s.artist, s.language, s.category].filter(Boolean).join(" • ");

    const actions = document.createElement("div");
    actions.className = "actions";

    const play = document.createElement("button");
    play.textContent = "▶ Chanter";
    play.onclick = () => playSong(s.id);

    const fav = document.createElement("button");
    fav.className = "secondary";
    fav.textContent = favorites.includes(s.id) ? "♥ Favori" : "♡ Favori";
    fav.onclick = () => {
      favorites = favorites.includes(s.id)
        ? favorites.filter(id => id !== s.id)
        : [...favorites, s.id];
      save(); render();
    };

    const add = document.createElement("button");
    add.className = "secondary";
    add.textContent = queue.includes(s.id) ? "✓ Dans la file" : "+ File d'attente";
    add.onclick = () => {
      if (!queue.includes(s.id)) queue.push(s.id);
      save(); render();
    };

    actions.append(play, fav, add);
    item.append(heading, meta, actions);
    $("songs").append(item);
  });
}

function playSong(id) {
  const song = songs.find(s => s.id === id);
  if (!song) return;
  const idVideo = videoId(song.youtube);
  if (!idVideo) {
    alert("Ce lien YouTube ne semble pas valide.");
    return;
  }
  $("playingTitle").textContent = "♫ " + song.title;
  $("player").innerHTML = "";
  const frame = document.createElement("iframe");
  frame.src = "https://www.youtube-nocookie.com/embed/" + encodeURIComponent(idVideo);
  frame.title = "Lecteur karaoké";
  frame.allow = "accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share";
  frame.allowFullscreen = true;
  $("player").append(frame);
  $("playerPanel").hidden = false;
  $("playerPanel").scrollIntoView({behavior:"smooth"});
}

function closePlayer() {
  $("player").innerHTML = "";
  $("playerPanel").hidden = true;
}

$("songForm").addEventListener("submit", event => {
  event.preventDefault();
  const title = $("title").value.trim();
  const youtube = $("youtube").value.trim();
  if (!videoId(youtube)) {
    alert("Merci de saisir un lien YouTube valide.");
    return;
  }
  songs.push({
    id: Date.now().toString(),
    title,
    artist: $("artist").value.trim(),
    language: $("newLanguage").value,
    category: $("newCategory").value,
    youtube
  });
  save();
  event.target.reset();
  render();
  alert("Le chant a été ajouté à cette bibliothèque !");
});

["search","language","category","view"].forEach(id => {
  $(id).addEventListener("input", render);
  $(id).addEventListener("change", render);
});

render();
</script>
</body>
</html>

