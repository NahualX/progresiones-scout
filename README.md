[progresiones-scouts.html](https://github.com/user-attachments/files/27063534/progresiones-scouts.html)
# progresiones-scout<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Progresiones Scout — Scouts de Argentina</title>
<link href="https://fonts.googleapis.com/css2?family=Nunito:wght@400;600;700;800;900&family=Oswald:wght@500;700&display=swap" rel="stylesheet">
<style>
  :root {
    --scout-blue: #1565C0;
    --scout-green: #2E7D32;
    --scout-purple: #6A1B9A;
    --scout-orange: #E65100;
    --area-salud: #0288D1;
    --area-paz: #7B1FA2;
    --area-ambiente: #388E3C;
    --area-hab: #D84315;
    --req-blue: #1565C0;
    --opt-bg: #FFF8E1;
    --opt-border: #FFB300;
    --card-bg: #FFFFFF;
    --page-bg: #F0F4F8;
    --text-dark: #1A237E;
    --text-body: #333;
    --shadow: 0 4px 20px rgba(0,0,0,0.10);
    --radius: 14px;
  }

  * { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Nunito', sans-serif;
    background: var(--page-bg);
    color: var(--text-body);
    min-height: 100vh;
  }

  /* ── HEADER ── */
  header {
    background: linear-gradient(135deg, #0D47A1 0%, #1565C0 40%, #0288D1 100%);
    color: white;
    padding: 32px 24px 28px;
    text-align: center;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 4px 24px rgba(13,71,161,0.4);
  }
  header h1 {
    font-family: 'Oswald', sans-serif;
    font-size: clamp(1.4rem, 5vw, 2.4rem);
    font-weight: 700;
    letter-spacing: 1px;
    text-transform: uppercase;
  }
  header p {
    font-size: 0.9rem;
    opacity: 0.85;
    margin-top: 4px;
  }
  .flor-de-lis {
    font-size: 2rem;
    display: block;
    margin-bottom: 6px;
    filter: drop-shadow(0 2px 4px rgba(0,0,0,0.3));
  }

  /* ── STATS BAR ── */
  .stats-bar {
    background: white;
    padding: 14px 20px;
    display: flex;
    gap: 12px;
    justify-content: center;
    flex-wrap: wrap;
    border-bottom: 3px solid #E3F2FD;
    box-shadow: 0 2px 8px rgba(0,0,0,0.06);
  }
  .stat-pill {
    background: #E3F2FD;
    border-radius: 20px;
    padding: 6px 16px;
    font-size: 0.82rem;
    font-weight: 700;
    color: var(--scout-blue);
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .stat-pill .num {
    font-size: 1.1rem;
    font-weight: 900;
    color: #0D47A1;
  }
  .stat-pill.green { background: #E8F5E9; color: #1B5E20; }
  .stat-pill.green .num { color: #1B5E20; }

  /* ── SCOUT NAME INPUT ── */
  .scout-input-bar {
    background: white;
    padding: 12px 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    border-bottom: 2px solid #EEE;
  }
  .scout-input-bar label {
    font-weight: 700;
    color: #333;
    font-size: 0.9rem;
    white-space: nowrap;
  }
  .scout-input-bar input {
    padding: 6px 14px;
    border-radius: 20px;
    border: 2px solid #90CAF9;
    font-family: 'Nunito', sans-serif;
    font-size: 0.9rem;
    font-weight: 600;
    outline: none;
    width: 200px;
    transition: border 0.2s;
  }
  .scout-input-bar input:focus { border-color: var(--scout-blue); }

  /* ── FILTER TABS ── */
  .filter-tabs {
    padding: 16px 20px 0;
    display: flex;
    gap: 8px;
    flex-wrap: wrap;
    justify-content: center;
    max-width: 900px;
    margin: 0 auto;
  }
  .tab-btn {
    padding: 8px 18px;
    border-radius: 20px;
    border: 2.5px solid transparent;
    font-family: 'Nunito', sans-serif;
    font-size: 0.83rem;
    font-weight: 800;
    cursor: pointer;
    transition: all 0.2s;
    text-transform: uppercase;
    letter-spacing: 0.5px;
  }
  .tab-btn.all { background: #1565C0; color: white; border-color: #1565C0; }
  .tab-btn.all:not(.active) { background: white; color: #1565C0; }
  .tab-btn.salud { background: #0288D1; color: white; border-color: #0288D1; }
  .tab-btn.salud:not(.active) { background: white; color: #0288D1; }
  .tab-btn.paz { background: #7B1FA2; color: white; border-color: #7B1FA2; }
  .tab-btn.paz:not(.active) { background: white; color: #7B1FA2; }
  .tab-btn.ambiente { background: #388E3C; color: white; border-color: #388E3C; }
  .tab-btn.ambiente:not(.active) { background: white; color: #388E3C; }
  .tab-btn.hab { background: #D84315; color: white; border-color: #D84315; }
  .tab-btn.hab:not(.active) { background: white; color: #D84315; }
  .tab-btn.completadas { background: #00897B; color: white; border-color: #00897B; }
  .tab-btn.completadas:not(.active) { background: white; color: #00897B; }

  /* ── AREA HEADERS ── */
  .area-header {
    display: flex;
    align-items: center;
    gap: 12px;
    padding: 18px 24px 10px;
    max-width: 900px;
    margin: 24px auto 0;
  }
  .area-icon { font-size: 1.8rem; }
  .area-title {
    font-family: 'Oswald', sans-serif;
    font-size: 1.4rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 1px;
  }
  .area-title.salud { color: var(--area-salud); }
  .area-title.paz { color: var(--area-paz); }
  .area-title.ambiente { color: var(--area-ambiente); }
  .area-title.hab { color: var(--area-hab); }
  .area-divider {
    flex: 1;
    height: 3px;
    border-radius: 2px;
    opacity: 0.3;
  }
  .area-divider.salud { background: var(--area-salud); }
  .area-divider.paz { background: var(--area-paz); }
  .area-divider.ambiente { background: var(--area-ambiente); }
  .area-divider.hab { background: var(--area-hab); }

  /* ── GRID ── */
  .grid {
    max-width: 900px;
    margin: 0 auto;
    padding: 12px 16px 32px;
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
    gap: 16px;
  }

  /* ── CARD ── */
  .card {
    background: var(--card-bg);
    border-radius: var(--radius);
    box-shadow: var(--shadow);
    overflow: hidden;
    transition: transform 0.2s, box-shadow 0.2s;
    border: 2px solid transparent;
  }
  .card:hover {
    transform: translateY(-3px);
    box-shadow: 0 8px 28px rgba(0,0,0,0.14);
  }
  .card.completed {
    border-color: #43A047;
    background: linear-gradient(135deg, #F1FFF3 0%, #FFFFFF 100%);
  }
  .card.completed .card-header {
    opacity: 0.85;
  }

  .card-header {
    padding: 12px 16px 10px;
    color: white;
    cursor: pointer;
    display: flex;
    align-items: flex-start;
    gap: 10px;
    position: relative;
  }
  .card-header.salud { background: linear-gradient(135deg, #0288D1, #0277BD); }
  .card-header.paz { background: linear-gradient(135deg, #7B1FA2, #6A1B9A); }
  .card-header.ambiente { background: linear-gradient(135deg, #388E3C, #2E7D32); }
  .card-header.hab { background: linear-gradient(135deg, #D84315, #BF360C); }

  .prog-num {
    background: rgba(255,255,255,0.25);
    border-radius: 8px;
    padding: 3px 9px;
    font-family: 'Oswald', sans-serif;
    font-size: 1rem;
    font-weight: 700;
    flex-shrink: 0;
    min-width: 36px;
    text-align: center;
  }
  .prog-title {
    font-size: 0.84rem;
    font-weight: 700;
    line-height: 1.3;
    flex: 1;
  }
  .card-chevron {
    font-size: 0.9rem;
    transition: transform 0.3s;
    flex-shrink: 0;
    margin-top: 2px;
  }
  .card.open .card-chevron { transform: rotate(180deg); }

  .card-progress {
    padding: 8px 16px;
    display: flex;
    align-items: center;
    gap: 8px;
    border-bottom: 1px solid #F0F0F0;
    background: #FAFAFA;
  }
  .progress-bar-track {
    flex: 1;
    height: 6px;
    background: #E0E0E0;
    border-radius: 3px;
    overflow: hidden;
  }
  .progress-bar-fill {
    height: 100%;
    border-radius: 3px;
    transition: width 0.4s ease;
    background: linear-gradient(90deg, #43A047, #66BB6A);
  }
  .progress-label {
    font-size: 0.72rem;
    font-weight: 800;
    color: #555;
    white-space: nowrap;
  }
  .check-all-btn {
    font-size: 0.7rem;
    padding: 2px 8px;
    border-radius: 10px;
    border: 1.5px solid #43A047;
    background: white;
    color: #43A047;
    cursor: pointer;
    font-family: 'Nunito', sans-serif;
    font-weight: 700;
    transition: all 0.15s;
    white-space: nowrap;
  }
  .check-all-btn:hover { background: #43A047; color: white; }

  .card-body {
    display: none;
    padding: 12px 16px 14px;
  }
  .card.open .card-body { display: block; }

  /* ── DESAFIOS LABEL ── */
  .desafios-label {
    font-size: 0.72rem;
    font-weight: 900;
    letter-spacing: 1px;
    text-transform: uppercase;
    margin-bottom: 8px;
    padding-bottom: 4px;
    border-bottom: 2px solid #EEE;
    display: flex;
    gap: 14px;
  }
  .desafios-label .req-tag {
    color: var(--req-blue);
    display: flex;
    align-items: center;
    gap: 4px;
  }
  .desafios-label .opt-tag {
    color: #F57F17;
    display: flex;
    align-items: center;
    gap: 4px;
  }

  /* ── DESAFIO ITEM ── */
  .desafio-item {
    display: flex;
    align-items: flex-start;
    gap: 10px;
    padding: 7px 10px;
    border-radius: 8px;
    margin-bottom: 5px;
    cursor: pointer;
    transition: background 0.15s;
  }
  .desafio-item:hover { background: #F5F5F5; }
  .desafio-item.required {
    background: #EFF6FF;
    border-left: 3px solid var(--req-blue);
  }
  .desafio-item.required:hover { background: #DBEAFE; }
  .desafio-item.optional {
    background: var(--opt-bg);
    border-left: 3px solid var(--opt-border);
  }
  .desafio-item.optional:hover { background: #FFF3CD; }
  .desafio-item.done {
    opacity: 0.65;
  }
  .desafio-item.done .desafio-text { text-decoration: line-through; }

  .desafio-check {
    width: 20px;
    height: 20px;
    border-radius: 50%;
    border: 2.5px solid #90CAF9;
    flex-shrink: 0;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: all 0.2s;
    margin-top: 1px;
    background: white;
  }
  .desafio-item.required .desafio-check { border-color: var(--req-blue); }
  .desafio-item.optional .desafio-check { border-color: var(--opt-border); }
  .desafio-item.done .desafio-check {
    background: #43A047;
    border-color: #43A047;
  }
  .desafio-item.done .desafio-check::after {
    content: '✓';
    color: white;
    font-size: 0.75rem;
    font-weight: 900;
  }

  .desafio-num {
    font-size: 0.72rem;
    font-weight: 900;
    color: #999;
    flex-shrink: 0;
    width: 16px;
    margin-top: 2px;
  }
  .desafio-item.required .desafio-num { color: var(--req-blue); }
  .desafio-item.optional .desafio-num { color: #F57F17; }

  .desafio-text {
    font-size: 0.82rem;
    line-height: 1.4;
    color: var(--text-body);
    flex: 1;
  }

  .tipo-badge {
    font-size: 0.62rem;
    font-weight: 900;
    padding: 1px 6px;
    border-radius: 6px;
    flex-shrink: 0;
    margin-top: 2px;
    letter-spacing: 0.3px;
    text-transform: uppercase;
  }
  .tipo-badge.req { background: #DBEAFE; color: var(--req-blue); }
  .tipo-badge.opt { background: #FEF3C7; color: #92400E; }

  /* ── COMPLETED STAMP ── */
  .completed-stamp {
    display: none;
    text-align: center;
    padding: 10px;
    background: linear-gradient(135deg, #E8F5E9, #C8E6C9);
    border-radius: 8px;
    margin-top: 10px;
    font-weight: 800;
    color: #2E7D32;
    font-size: 0.85rem;
  }
  .card.completed .completed-stamp { display: block; }

  /* ── EXPORT BUTTON ── */
  .actions-bar {
    max-width: 900px;
    margin: 0 auto 8px;
    padding: 0 16px;
    display: flex;
    gap: 10px;
    justify-content: flex-end;
    flex-wrap: wrap;
  }
  .btn-action {
    padding: 8px 18px;
    border-radius: 20px;
    border: none;
    font-family: 'Nunito', sans-serif;
    font-size: 0.82rem;
    font-weight: 800;
    cursor: pointer;
    transition: all 0.2s;
    display: flex;
    align-items: center;
    gap: 6px;
  }
  .btn-reset { background: #FFEBEE; color: #C62828; }
  .btn-reset:hover { background: #FFCDD2; }
  .btn-expand { background: #E3F2FD; color: #1565C0; }
  .btn-expand:hover { background: #BBDEFB; }

  /* ── HIDDEN ── */
  .area-section.hidden { display: none; }
  .card.hidden { display: none; }

  /* ── LEYENDA ── */
  .leyenda {
    max-width: 900px;
    margin: 12px auto 0;
    padding: 10px 20px;
    display: flex;
    gap: 20px;
    flex-wrap: wrap;
    font-size: 0.78rem;
    font-weight: 700;
    color: #555;
  }
  .ley-item { display: flex; align-items: center; gap: 6px; }
  .ley-dot {
    width: 14px; height: 14px;
    border-radius: 3px;
    flex-shrink: 0;
  }
  .ley-dot.req { background: #DBEAFE; border-left: 3px solid var(--req-blue); }
  .ley-dot.opt { background: var(--opt-bg); border-left: 3px solid var(--opt-border); }

  /* ── RESPONSIVE ── */
  @media (max-width: 480px) {
    .grid { grid-template-columns: 1fr; padding: 8px 10px 24px; }
    header { padding: 20px 16px 16px; }
    .stats-bar { gap: 8px; }
    .stat-pill { padding: 5px 12px; font-size: 0.76rem; }
  }
</style>
</head>
<body>

<header>
  <span class="flor-de-lis">⚜️</span>
  <h1>Progresiones Scout</h1>
  <p>Scouts de Argentina — Rama Scouts · 53 Competencias Educativas</p>
</header>

<div class="scout-input-bar">
  <label>🧭 Scout:</label>
  <input type="text" id="scoutName" placeholder="Tu nombre aquí..." oninput="saveScoutName()">
</div>

<div class="stats-bar">
  <div class="stat-pill"><span class="num" id="statTotal">0</span> desafíos completados</div>
  <div class="stat-pill green"><span class="num" id="statReq">0</span> obligatorios ✓</div>
  <div class="stat-pill"><span class="num" id="statProg">0</span> / 53 progresiones</div>
</div>

<div class="filter-tabs">
  <button class="tab-btn all active" onclick="filterArea('all', this)">🌐 Todas</button>
  <button class="tab-btn salud" onclick="filterArea('salud', this)">💙 Salud y Bienestar</button>
  <button class="tab-btn paz" onclick="filterArea('paz', this)">🤝 Paz y Desarrollo</button>
  <button class="tab-btn ambiente" onclick="filterArea('ambiente', this)">🌿 Ambiente</button>
  <button class="tab-btn hab" onclick="filterArea('hab', this)">⚙️ Habilidades para la Vida</button>
  <button class="tab-btn completadas" onclick="filterArea('completadas', this)">✅ Completadas</button>
</div>

<div class="leyenda">
  <div class="ley-item"><div class="ley-dot req"></div> Desafío Obligatorio</div>
  <div class="ley-item"><div class="ley-dot opt"></div> Desafío Opcional</div>
</div>

<div class="actions-bar">
  <button class="btn-action btn-expand" onclick="expandAll()">📂 Expandir todo</button>
  <button class="btn-action btn-reset" onclick="resetAll()">🗑️ Reiniciar progresión</button>
</div>

<div id="app"></div>

<script>
const PROGRESSIONS = [
  // ══════════════════════════════════════════════
  // ÁREA 1: SALUD Y BIENESTAR
  // ══════════════════════════════════════════════
  {
    id: 1, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Incorporo hábitos de higiene.',
    desafios: [
      { text: 'Tengo una rutina de higiene personal saludable y responsable. (Por ejemplo: higiene dental, aseo de manos).', req: true },
      { text: 'Colaboro con el orden y la limpieza de mi habitación, de mi casa y de los lugares en los que vivo.', req: true },
      { text: 'Cuido, limpio y ordeno los lugares en los que realizo actividades, acampo y realizo excursiones.', req: true },
      { text: 'Realizo construcciones en campamentos que ayudan a mejorar la comodidad y la higiene del lugar (mesas, sillas, toldos, percheros, lavabo, etc.).', req: true },
      { text: 'Organizo correctamente mi mochila para un campamento de 3 días.', req: true },
      { text: 'Uso correctamente mi indumentaria scout y la mantengo en buen estado.', req: false },
      { text: 'Cuando sea necesario lavo y mantengo mi ropa en buen estado durante los campamentos.', req: false },
      { text: 'Desarrollo una especialidad referida a la higiene o la salud.', req: false },
    ]
  },
  {
    id: 2, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Entiendo la importancia de alimentarme de forma saludable.',
    desafios: [
      { text: 'Sé que alimentos me ayudan a crecer y practico una alimentación saludable.', req: true },
      { text: 'Planifico un menú saludable para un campamento de Patrulla acorde a las actividades a desarrollar y la época del año.', req: true },
      { text: 'Preparo comidas sencillas y saludables en mi casa y para mi Patrulla en actividades de campamento.', req: true },
      { text: 'Conozco las técnicas de manipulación y conservación de alimentos y las aplico en la cocina.', req: true },
      { text: 'Realizo un tutorial, junto a mi Patrulla, sobre cómo preparar nuestra comida favorita y la comparto con los demás.', req: false },
      { text: 'Realizo algunas recetas tradicionales de cocina rústica o sin utensilios.', req: false },
      { text: 'Preparo un menú para una excursión o campamento de 3 días.', req: false },
      { text: 'Me encargo de hacer las compras de alimentos para una actividad o campamento de Patrulla.', req: false },
      { text: 'Pruebo, junto a mi Patrulla, nuevas recetas y técnicas de cocina con la ayuda de una persona experta.', req: false },
      { text: 'Desempeño el rol de cocinera o cocinero de mi Patrulla al menos por un ciclo de programa.', req: false },
      { text: 'Desarrollo la especialidad de cocina.', req: false },
    ]
  },
  {
    id: 3, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Reconozco y expreso mis emociones, entendiendo cómo me afectan a mí y a las demás personas.',
    desafios: [
      { text: 'Identifico y reflexiono sobre mis emociones en las diferentes situaciones en las que me encuentro y las comparto con los demás.', req: true },
      { text: 'Escucho a los demás con atención y empatía para comprender cómo se sienten y cómo mis palabras y acciones pueden influir en ellos.', req: true },
      { text: 'Aprendo técnicas de relajación como la respiración profunda o la meditación para manejar las emociones intensas.', req: true },
      { text: 'Expreso mis emociones de diversas maneras a través de diferentes formas (ya sean lúdicas, expresivas, artísticas, etc.).', req: false },
      { text: 'Dialogo con personas de mi confianza, sobre cómo me siento y lo que sucede a diario en mi vida.', req: false },
      { text: 'Aprendo a reconocer las señales físicas que acompañan mis emociones, como palpitaciones, sudoración o tensión muscular.', req: false },
    ]
  },
  {
    id: 4, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Soy crítica/o con las imágenes y mensajes que los medios de comunicación y las redes sociales nos presentan sobre los modelos corporales y las modas.',
    desafios: [
      { text: 'Investigo sobre lo que significa el estereotipo de belleza y discuto sobre el tema con mis compañeras y compañeros de Patrulla.', req: true },
      { text: 'Exploro en los medios de comunicación, en películas y series las imágenes de personas que aparecen usualmente y reflexiono con mi Patrulla sobre las imágenes y los mensajes que transmiten las redes y los medios de comunicación sobre los modelos corporales.', req: true },
      { text: 'En nuestras relaciones y actividades de Patrulla promuevo el respeto hacia mi propio cuerpo y el de los demás.', req: true },
      { text: 'Entiendo por qué no se debe hablar del cuerpo de las demás personas.', req: true },
    ]
  },
  {
    id: 5, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Busco información y tomo decisiones conscientes para cuidar mi salud y sentirme bien conmigo misma/o.',
    desafios: [
      { text: 'Busco información confiable sobre cuidados de la salud en la adolescencia.', req: true },
      { text: 'Incorporo hábitos de cuidado de mi salud para sentirme bien conmigo mismo/a, como, por ejemplo: realizar ejercicio de forma regular, comer saludable, realizar deportes o actividad física, disfrutar del aire libre, etc.', req: true },
      { text: 'Defino al menos 3 acciones para cuidar mi salud y sentirme bien, y las pongo en práctica al menos por 4 meses.', req: true },
      { text: 'Me informo sobre qué sustancias pueden dañar mi cuerpo y lo comparto con las demás personas en alguna actividad de la Unidad.', req: true },
    ]
  },
  {
    id: 6, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Acepto y valoro mi cuerpo y el de los demás, evitando comparaciones.',
    desafios: [
      { text: 'Realizo actividades, junto a mi Patrulla, de autocuidado que promuevan el bienestar emocional y físico.', req: true },
      { text: 'Entiendo por qué debemos evitar hacer comparaciones con el cuerpo de las demás personas.', req: true },
      { text: 'Me informo de los cambios que se están produciendo en mi cuerpo y en mis pensamientos, gustos y sentimientos en esta etapa de mi vida.', req: true },
      { text: 'Sé cuál es mi peso ideal, cómo se produce el sobrepeso y qué hacer para que mi peso sea el adecuado.', req: false },
      { text: 'Me informo sobre los problemas que causa el alcohol y el tabaco.', req: false },
    ]
  },
  {
    id: 7, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Reconozco e identifico las particularidades, diferencias y cambios de mi cuerpo a medida que voy creciendo.',
    desafios: [
      { text: 'Investigo sobre los cambios progresivos que se están produciendo en mi cuerpo buscando información confiable.', req: true },
      { text: 'Reconozco los cambios que se están produciendo en mi cuerpo.', req: true },
      { text: 'Comparto información y experiencias con amigas o amigos que también están pasando por cambios en sus cuerpos.', req: true },
      { text: 'Identifico las diferencias anatómicas y fisiológicas de mujeres y varones en las distintas etapas de la vida.', req: true },
      { text: 'Conozco las medidas de mi cuerpo y las aplico en mediciones y estimaciones (paso doble, brazos extendidos, altura, etc.).', req: false },
      { text: 'Reviso las medidas de mi cuerpo cada 5 o 6 meses para mantener actualizada mis técnicas de medición.', req: false },
    ]
  },
  {
    id: 8, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Identifico y respeto mis emociones y sentimientos vinculados a la sexualidad y sus cambios.',
    desafios: [
      { text: 'Consulto con personas adultas de confianza (familiares, educadores, médicos.) sobre temas relacionados con la sexualidad y el crecimiento biológico para aclarar dudas.', req: true },
      { text: 'Participo, junto a mi Patrulla, en charlas y talleres sobre educación sexual.', req: true },
      { text: 'Aprendo y utilizo un vocabulario apropiado para hablar sobre la sexualidad y los cambios corporales.', req: true },
      { text: 'Escucho y apoyo a mis amigas y amigos cercanos sobre sus inquietudes, preguntas y experiencias en un ambiente seguro y de confianza vinculado a la sexualidad.', req: true },
    ]
  },
  {
    id: 9, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Valoro el diálogo y el respeto mutuo en mis relaciones, expresando mi opinión de manera segura y respetuosa.',
    desafios: [
      { text: 'Expreso mis pensamientos y sentimientos de manera empática y considerada, teniendo en cuenta cómo podrían sentirse los demás.', req: true },
      { text: 'Tomo parte activa en los Consejos de Patrulla y Asambleas, escuchando atentamente las ideas de los demás y exponiendo mis ideas de forma clara, sin agresividad.', req: true },
      { text: 'Practico el diálogo respetuoso y una comunicación abierta en todos los ámbitos en los que me desenvuelvo (familia, escuela, scouts...).', req: true },
      { text: 'Participo en la evaluación de la progresión personal de mis amigas y amigos de la Patrulla y también soy evaluado en mi progresión.', req: true },
      { text: 'Construyo relaciones basadas en la confianza, manteniendo mi palabra y siendo honesto en mis relaciones.', req: false },
      { text: 'Desarrollo una especialidad relacionada con la comunicación.', req: false },
    ]
  },
  {
    id: 10, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Conozco los recursos y lugares donde puedo obtener información y apoyo para proteger mis derechos sexuales.',
    desafios: [
      { text: 'Me informo sobre mis derechos relacionados a mi salud sexual.', req: true },
      { text: 'Conozco y sé a dónde acudir para defender mis derechos relacionados al desarrollo sano de mi sexualidad.', req: true },
      { text: 'Participo, junto a mi Patrulla, en charlas educativas sobre derechos y salud sexual.', req: true },
      { text: 'Conozco mis derechos y expreso mi disconformidad cuando entiendo que mis derechos, opiniones y necesidades personales están siendo violentadas.', req: true },
      { text: 'Entiendo que no estoy obligada/o a hacer lo que me provoque temor o incomodidad.', req: false },
      { text: 'Desarrollo una especialidad vinculada al tema.', req: false },
    ]
  },
  {
    id: 11, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Descubro los beneficios que tiene la actividad física y los deportes para mi bienestar físico y emocional.',
    desafios: [
      { text: 'Indago sobre los beneficios que tiene la actividad física y los deportes para mi bienestar físico y emocional.', req: true },
      { text: 'Participo en diversas actividades de mi interés que me desafíen físicamente y que me permitan superarme y mejorar.', req: true },
      { text: 'Invento juegos y desafíos físicos junto a mi Patrulla, promoviendo la creatividad y la diversión.', req: true },
      { text: 'Practico una actividad deportiva y me esfuerzo por mejorar mi rendimiento.', req: true },
      { text: 'Busco y propongo juegos y actividades físicas para hacer con mi Patrulla.', req: true },
      { text: 'Realizo actividades de senderismo junto a mi Patrulla y Unidad Scout (aplicando técnicas de marcha, alimentación adecuada, tiempos de descanso, etc.).', req: true },
      { text: 'Participo junto a mi Patrulla de paseos en bicicleta, en bote, en Kayak.', req: false },
      { text: 'Desarrollo una especialidad vinculada al deporte y la actividad física.', req: false },
    ]
  },
  {
    id: 12, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Trabajo en equipo y disfruto de las actividades físicas y deportivas, fomentando el desarrollo social y emocional.',
    desafios: [
      { text: 'Junto a mi Patrulla, construyo un circuito de obstáculos para jugar junto a mi Unidad.', req: true },
      { text: 'Trazo y sigo señales de pista en un recorrido por lo menos de un kilómetro en el campo y de 2 kilómetros en área urbana.', req: true },
      { text: 'Realizo con mi Patrulla una actividad de navegación terrestre, utilizando mapa y brújula.', req: true },
      { text: 'Con mi Patrulla invento un juego o deporte para jugar juntos y con otras amigas y amigos.', req: true },
      { text: 'Organizo con mi Patrulla un campeonato de un deporte o juego para realizar con la Unidad Scout.', req: true },
      { text: 'Participo en juegos y actividades que requieran cooperación y coordinación con otros jóvenes.', req: false },
      { text: 'Desarrollo una especialidad vinculada al deporte y la actividad física.', req: false },
    ]
  },
  {
    id: 13, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Identifico situaciones de riesgo y adopto prácticas seguras.',
    desafios: [
      { text: 'Identifico situaciones que pueden dañar mi salud y la de mis pares en las actividades que realizo.', req: true },
      { text: 'Utilizo los elementos de seguridad adecuados para participar en actividades físicas o deportes.', req: true },
      { text: 'Sé cómo actuar en casos de insolación, deshidratación, pequeñas heridas y picaduras de insectos y hemorragias.', req: true },
      { text: 'Aplico el orden de prioridades en caso de accidentes.', req: true },
      { text: 'Conozco y aplico las técnicas de traslado de heridos.', req: true },
      { text: 'Respeto y aplico las normas de seguridad en las actividades que realizo.', req: true },
      { text: 'Conozco el Plan de Contingencia.', req: true },
      { text: 'Aprendo sobre la seguridad en línea, especialmente en las redes sociales (no compartir información personal, asegurarme de que las configuraciones personales de privacidad en las plataformas de uso frecuente sean adecuadas y comunicar cualquier problema a un adulto de confianza).', req: false },
      { text: 'Participo de simulacros de emergencias y accidentes.', req: false },
      { text: 'Desarrollo una especialidad vinculada a la seguridad.', req: false },
      { text: 'Desarrollo una especialidad vinculada a la salud y los primeros auxilios.', req: false },
      { text: 'Me desempeño como enfermero/a de Patrulla durante un ciclo de programa.', req: false },
    ]
  },
  {
    id: 14, area: 'salud', areaLabel: 'Salud y bienestar',
    title: 'Conozco y construyo redes de apoyo y ayuda mutua.',
    desafios: [
      { text: 'Identifico a las personas a quienes puedo pedir ayuda y apoyo en distintos ámbitos (familia, escuela, grupo scout, club, amigos, amigas...).', req: true },
      { text: 'Apoyo a una compañera o compañero de Patrulla en su progresión personal, en el logro de alguna especialidad o en otros temas de su interés.', req: true },
      { text: 'Conversamos en la Patrulla sobre aquellos temas que nos preocupa e interesa.', req: true },
    ]
  },

  // ══════════════════════════════════════════════
  // ÁREA 2: PAZ Y DESARROLLO
  // ══════════════════════════════════════════════
  {
    id: 15, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Colaboro en la resolución de situaciones de conflicto a través del diálogo, evitando situaciones de violencia, en los espacios donde me desenvuelvo.',
    desafios: [
      { text: 'Participo de los órganos de toma de decisiones de la Patrulla y de la Unidad, expresando mis opiniones e ideas con respeto y escuchando las opiniones y decisiones de los demás en todo momento.', req: true },
      { text: 'Colaboro en resolver problemas o conflictos entre mis compañeras y compañeros de Patrulla de manera pacífica.', req: true },
      { text: 'Identifico distintas formas de expresiones de violencia, intolerancia y exclusión en mi escuela u otros lugares que frecuento.', req: true },
      { text: 'Actúo como mediador/a en conflictos entre mis amigas, amigos, compañeros/as de escuela, alentando a escucharse y buscar soluciones pacíficas.', req: true },
      { text: 'Sé cómo actuar en situaciones de bullying y de ciberacoso.', req: true },
      { text: 'Coordino un Consejo de Patrulla en el que se discuten diferentes temas.', req: false },
      { text: 'Participo de un proyecto de unidad, enmarcado en las dimensiones de la paz que reconoce el Movimiento Scout (personal, comunidad y global).', req: false },
      { text: 'Sé diferenciar entre una broma y una situación de acoso o bullying.', req: false },
    ]
  },
  {
    id: 16, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Exploro y me identifico con la cultura de mi comunidad y de mi país proponiendo actividades y proyectos con esta temática.',
    desafios: [
      { text: 'Investigo juegos tradicionales de mi región y/o país y propongo hacerlos con mi Patrulla y Unidad Scout.', req: true },
      { text: 'Investigo relatos, narraciones, leyendas, música y danzas de mi región y mi país y las comparto en una velada de mi Patrulla o un fogón de la Unidad.', req: true },
      { text: 'Propongo actividades a mi Patrulla y a mi Unidad vinculadas a la cultura de mi comunidad.', req: true },
      { text: 'Participo junto a mi Patrulla, Unidad o en forma individual de festividades típicas de la región donde vivo, o en una en la que se celebre la cultura de mi comunidad y/o país.', req: true },
      { text: 'Participo de visitas a museos, monumentos históricos o sitios culturales para aprender sobre la historia local, provincial o nacional.', req: true },
      { text: 'Investigo y recreo junto a mi Patrulla o Unidad, algunas tradiciones culinarias, vestimenta o prácticas culturales de mi región y/o país.', req: true },
      { text: 'Entrevisto a personas mayores de la comunidad para obtener historias y recuerdos de cómo era la vida en los tiempos pasados y organizo charlas o presentaciones en las que estas personas puedan compartir sus experiencias.', req: false },
      { text: 'Realizo videos cortos que exploren diferentes aspectos de la cultura local, como la música, la danza, la comida, etc.', req: false },
      { text: 'Investigo sobre la historia del Movimiento Scout a nivel mundial y en nuestro país.', req: false },
      { text: 'Conozco el significado de los colores del pañuelo de mi grupo scout y de su nombre.', req: false },
      { text: 'Participo en proyectos que involucren la restauración, limpieza o conservación de sitios históricos y culturales de la comunidad.', req: false },
      { text: 'Desarrollo una especialidad vinculada a la cultura.', req: false },
    ]
  },
  {
    id: 17, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Valoro mi historia e identidad, la de mi País y respeto sus símbolos patrios.',
    desafios: [
      { text: 'Aprendo sobre la historia de mi propia familia y antepasados, y comprendo cómo esto se relaciona con la historia del país.', req: true },
      { text: 'Conozco la historia y el sentido de los principales símbolos patrios.', req: true },
      { text: 'Conozco y realizo correctamente los procedimientos de izado y arriado de la bandera nacional.', req: true },
      { text: 'Exploro la vida y los logros de figuras históricas nacionales que hayan influido en la historia de la región donde vivo y/o del país.', req: true },
      { text: 'Creo materiales visuales que destaquen aspectos importantes de la historia, la cultura y la identidad de la región donde vivo y/o del país.', req: true },
      { text: 'Recopilo fotos y recuerdos familiares para crear un álbum o video que muestre la historia y las experiencias de la familia.', req: false },
      { text: 'Exploro diversas canciones que hablen de los símbolos patrios para cantar en nuestros actos y conmemoraciones.', req: false },
    ]
  },
  {
    id: 18, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Valoro y respeto la importancia de los Derechos Humanos en la sociedad e identifico situaciones de vulneración de estos, buscando activamente ayuda en mi entorno.',
    desafios: [
      { text: 'Aprendo sobre los derechos del niño, niñas y adolescentes utilizando diferentes fuentes confiables.', req: true },
      { text: 'Tomo decisiones justas y equitativas en juegos y situaciones cotidianas.', req: true },
      { text: 'Identifico y denuncio cualquier forma de discriminación y/o vulneración de derechos que presencie o conozca.', req: true },
      { text: 'Conozco los números de teléfono de emergencia, líneas de ayuda y organizaciones que trabajan en la protección de los derechos de las niñas y los niños.', req: true },
      { text: 'Con mi Patrulla o Unidad realizo una descubierta sobre los Derechos Humanos en la comunidad en donde vivo, en mi escuela.', req: true },
      { text: 'Participo en proyectos, tanto fuera como dentro del Movimiento Scout, que promuevan la igualdad, la justicia y el respeto a los Derechos Humanos en la comunidad.', req: false },
      { text: 'Participo en eventos, colectas o actividades de voluntariado para apoyar a organizaciones que trabajan en defensa de los Derechos Humanos.', req: false },
      { text: 'Mantengo diálogos abiertos con personas de confianza para conocer experiencias y preocupaciones sobre situaciones de vulneración de los DD.HH.', req: false },
    ]
  },
  {
    id: 19, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Ejercito y promuevo prácticas que fomenten la participación democrática en los diferentes contextos en donde me desenvuelvo.',
    desafios: [
      { text: 'Investigo cómo funciona la democracia en mi país y cómo se toman decisiones en los diferentes niveles de gobierno.', req: true },
      { text: 'Realizo una visita al Consejo Deliberante / Municipal de mi ciudad y me interiorizo sobre su funcionamiento.', req: true },
      { text: 'Me informo sobre cómo se toman las decisiones en mi Grupo Scout y sobre mis deberes y derechos como miembro de Scouts de Argentina.', req: true },
      { text: 'Respeto las decisiones tomadas en forma democrática en mi Patrulla y Unidad Scout.', req: true },
      { text: 'Practico la escucha activa y el respeto hacia opiniones diferentes, incluso si no estoy de acuerdo.', req: true },
      { text: 'Realizo propuestas de actividades y proyectos teniendo en cuenta los intereses de mi Patrulla.', req: true },
      { text: 'Conozco y participo en espacios de participación ciudadana en mi barrio y de mi escuela, como por ejemplo el Centro de Estudiantes.', req: true },
      { text: 'Dialogo con los representantes juveniles de mi Grupo Scout para conocer los temas que se tratan en el Consejo de Grupo.', req: false },
      { text: 'Fomento la participación de todas las personas, asegurando que se escuchen las voces de diferentes grupos y que las decisiones sean justas.', req: false },
      { text: 'Propongo reuniones para discutir temas importantes y asegurarme de que todas las personas tengan la oportunidad de hablar.', req: false },
      { text: 'Participo en debates constructivos con los demás para analizar las diferentes propuestas y llegar a un entendimiento común.', req: false },
    ]
  },
  {
    id: 20, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Respeto los acuerdos de convivencia y las decisiones tomadas por los demás, expresando mis propias ideas y posturas de manera empática y respetuosa.',
    desafios: [
      { text: 'Conozco el funcionamiento de los órganos de gobierno de la Patrulla y la Unidad y participo de los ámbitos que me corresponden.', req: true },
      { text: 'Participo en la elaboración de los acuerdos de convivencia de mi Unidad Scout.', req: true },
      { text: 'Opino sobre lo que me gusta o no de los acuerdos de convivencia en distintos ámbitos en los que actúo.', req: true },
      { text: 'Conozco y respeto los acuerdos de convivencia de los distintos ámbitos en los que actúo, aunque no siempre esté de acuerdo.', req: true },
      { text: 'Participo en la elaboración de reglas en actividades de grupo, como juegos, deportes o proyectos.', req: true },
    ]
  },
  {
    id: 21, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Promuevo que se garanticen los derechos de todas las personas en los ámbitos en los que participo.',
    desafios: [
      { text: 'Conozco cuáles son mis derechos y responsabilidades.', req: true },
      { text: 'Hablo con mis educadoras y educadores cuando me doy cuenta de situaciones que vulneran los derechos de algún compañero o compañera.', req: true },
      { text: 'Investigo sobre problemas de desigualdad y discriminación de géneros en mi comunidad y propongo alguna actividad al respecto.', req: true },
      { text: 'Contribuyo al clima de respeto y tolerancia en los espacios en los que participo.', req: true },
      { text: 'Participo en iniciativas y proyectos de Unidad que buscan crear conciencia sobre los Derechos Humanos y trabajar para su protección y promoción.', req: true },
      { text: 'Propongo una actividad de Patrulla o de Unidad relacionado con la defensa de los derechos de las personas.', req: false },
    ]
  },
  {
    id: 22, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Fomento el respeto a la diversidad en todas sus formas, cuestionando estereotipos y prejuicios en mis interacciones diarias.',
    desafios: [
      { text: 'Respeto a mis compañeras, compañeros y los reconozco como iguales.', req: true },
      { text: 'Ofrezco ayuda y apoyo a compañeras y compañeros que puedan estar enfrentando desafíos debido a sus diferencias.', req: true },
      { text: 'Aprendo sobre qué son los estereotipos y cómo pueden afectar a las personas.', req: true },
      { text: 'Soy consciente de cómo las palabras pueden herir a las demás personas y evito comentarios ofensivos.', req: true },
      { text: 'Realizo acciones en favor de la inclusión en los lugares en los que me desenvuelvo, y me manifiesto en contra de comentarios o actitudes prejuiciosas y estereotipadas.', req: true },
      { text: 'Trato a todas las personas con amabilidad y respeto, independientemente de su apariencia, origen o creencias.', req: true },
      { text: 'Practico la empatía imaginándome cómo se siente la otra persona en su situación.', req: true },
      { text: 'Mantengo contacto con scouts de otros países y me intereso por saber cómo viven, cómo es su cultura, etc.', req: false },
      { text: 'Propongo charlas, talleres, proyectos y actividades que promuevan la inclusión y diversidad.', req: false },
      { text: 'Participo, junto con mi Patrulla, en charlas y talleres de sensibilización sobre temas de diversidad, inclusión y respeto.', req: false },
      { text: 'Reflexiono regularmente sobre mis creencias y actitudes hacia diferentes grupos de personas.', req: false },
      { text: 'Cuestiono cualquier suposición que puedan hacer sobre alguien basada en su apariencia o identidad.', req: false },
      { text: 'Promuevo espacios de diálogo para reflexionar sobre situaciones de discriminación y prejuicios tanto en mi Patrulla como Unidad.', req: false },
      { text: 'Desarrollo la Insignia del cono Sur.', req: false },
    ]
  },
  {
    id: 23, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Promuevo la participación e inclusión de todas las personas, sin discriminación alguna.',
    desafios: [
      { text: 'Ayudo a alguien que se incorpora a mi Patrulla a comprender y avanzar en su progresión personal.', req: true },
      { text: 'Propongo a mi Patrulla y a la Unidad Scout juegos y actividades diferentes pensando en la participación e inclusión de todas las personas.', req: true },
      { text: 'Propongo realizar actividades con Patrullas y Unidades de otros grupos scouts.', req: true },
      { text: 'Participo de actividades y eventos con Patrullas y Unidades de mi distrito o zona.', req: true },
      { text: 'Reconozco y respeto las decisiones y preferencias de las demás personas, incluso si son diferentes a las mías.', req: true },
      { text: 'Practico el respeto y la inclusión al jugar y compartir con amigas y amigos, asegurándome de que todas las personas se sientan incluidas.', req: true },
    ]
  },
  {
    id: 24, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Identifico oportunidades para ayudar a alguien de manera individual y/o colectiva, sin esperar nada a cambio.',
    desafios: [
      { text: 'Siempre que tengo oportunidad, realizo buenas acciones personales en los lugares en los que me desenvuelvo.', req: true },
      { text: 'Participo de actividades solidarias y buenas acciones colectivas con mi Patrulla y mi Unidad.', req: true },
      { text: 'Realizo una descubierta en las que identifico las principales organizaciones y servicios públicos de mi comunidad, conozco a que se dedican y las ubico en un mapa.', req: true },
      { text: 'Colaboro con las tareas en mi hogar.', req: true },
      { text: 'Propongo buenas acciones y actividades solidarias para hacer junto a mi Patrulla y colaboro en su organización.', req: true },
      { text: 'Participo en al menos un proyecto solidario junto a mi Unidad.', req: false },
      { text: 'Desarrollo una especialidad vinculada al tema.', req: false },
    ]
  },
  {
    id: 25, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Me comprometo y animo a otras personas a trabajar en conjunto para lograr un cambio positivo en el mundo.',
    desafios: [
      { text: 'Realizo una descubierta junto a mi Patrulla o Unidad Scout en la que tomamos conocimiento de algunos problemas de la comunidad. A partir de esa descubierta, identifico un problema y propongo posibles acciones a realizar con mi Patrulla o Unidad.', req: true },
      { text: 'Identifico en mi comunidad a otros grupos de personas (además del Movimiento Scout) con quienes puedo trabajar en conjunto para lograr cambios positivos.', req: true },
      { text: 'Ante algunos problemas detectados en mi escuela o comunidad propongo algunas soluciones y animo a algunos compañeros/as a trabajar en conjunto para solucionarlos.', req: true },
    ]
  },
  {
    id: 26, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Observo lo que pasa a mi alrededor y trato de entender las razones detrás de las desigualdades que veo, actuando de manera responsable en situaciones que afectan a la sociedad, contribuyendo a mejorar el bienestar de las personas.',
    desafios: [
      { text: 'Realizo descubiertas con mi Patrulla o Unidad con el propósito de conocer de cerca las realidades y necesidades de mi entorno.', req: true },
      { text: 'A partir de los resultados de la descubierta reflexiono desde una mirada crítica, junto a mi Patrulla, sobre las razones o causas del problema detectado y busco algunas respuestas posibles.', req: true },
      { text: 'Propongo una actividad o Proyecto de Unidad que aborde alguna problemática de mi Comunidad, dentro del campo prioritario solidaridad.', req: true },
      { text: 'Exploro en los Objetivos de Desarrollo Sostenible aquellos objetivos vinculados a las desigualdades y analizo qué cosas puedo hacer.', req: false },
      { text: 'Desarrollo una especialidad vinculada a la solidaridad.', req: false },
    ]
  },
  {
    id: 27, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Me pregunto sobre el origen, la grandeza, belleza y misterios de todo lo que soy, somos y nos rodea.',
    desafios: [
      { text: 'Realizo dos marchas en silencio, una de día y otra de noche, intentando captar los sonidos, los olores, colores y formas, y reflexiono sobre esto.', req: true },
      { text: 'Participo de una actividad de observación del cielo nocturno y orientación por las estrellas, me pregunto sobre el origen del universo y lo converso con mi Patrulla y/o Unidad Scout.', req: true },
      { text: 'Realizo y participo de reflexiones y de meditaciones junto a mi Patrulla o Unidad en las excursiones o campamentos.', req: true },
      { text: 'Formulo preguntas sobre el origen, la grandeza, belleza y misterios de todo lo que soy, somos y nos rodea y busco respuestas en distintos ámbitos, como, por ejemplo, en mis creencias espirituales, en la ciencia.', req: false },
      { text: 'Participo en la construcción de espacios de reflexión y de meditación en un campamento de mi Unidad Scout.', req: false },
    ]
  },
  {
    id: 28, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Dialogo con los demás sobre lo que creo y busco conocer lo que los otros creen, demostrando respeto e interés.',
    desafios: [
      { text: 'Exploro religiones u opciones espirituales diferentes a la mía.', req: true },
      { text: 'Con mi Patrulla o Unidad compartimos un día de actividades y juegos y/o una actividad solidaria con un grupo de jóvenes de alguna iglesia, mezquita, sinagoga o templo de nuestra comunidad.', req: true },
      { text: 'Con mi Patrulla o Unidad realizo descubiertas sobre las religiones y opciones espirituales presentes en mi comunidad.', req: true },
      { text: 'Confecciono un calendario en el que registro las celebraciones y festividades religiosas de las confesiones de los scouts que integran mi Patrulla o Unidad Scout.', req: true },
      { text: 'Invito a mi Patrulla a cooperar en acciones organizadas por mi comunidad religiosa en favor de las personas vulneradas.', req: true },
      { text: 'Elijo un texto de mi confesión religiosa y lo comparto con mis amigas y amigos de la Patrulla, comentando por qué lo elegí.', req: false },
      { text: 'Visito los templos o lugares sagrados de las religiones presentes en la comunidad donde vivo.', req: false },
    ]
  },
  {
    id: 29, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Adhiero a los valores expresados en la Ley y la Promesa Scout comprendiendo su importancia para mi vida.',
    desafios: [
      { text: 'Conozco y comprendo la Ley y la Promesa Scout.', req: true },
      { text: 'He prometido esforzarme por vivir la Ley y la Promesa Scout.', req: true },
      { text: 'Conozco el significado de la flor de lis como emblema del Movimiento Scout.', req: true },
      { text: 'Identifico situaciones en las que aplico la Ley y la Promesa Scout en otros ámbitos diferentes a mi Unidad (casa, escuela, la calle, etc.).', req: true },
      { text: 'Reviso los acontecimientos vividos por la Patrulla y la Unidad a la luz de la Ley Scout, participando de momentos de reflexión y evaluación en el Consejo de Patrulla y la Asamblea.', req: true },
      { text: 'Ayudo a un/a compañero/a de Patrulla a comprender el significado de la Ley y la Promesa Scout.', req: false },
      { text: 'Colaboro en la organización de actividades como el Fuego de la Ley y en celebraciones donde se realice o renueve la Promesa Scout.', req: false },
    ]
  },
  {
    id: 30, area: 'paz', areaLabel: 'Paz y Desarrollo',
    title: 'Me pregunto sobre mis creencias, prioridades, valores y cómo se manifiesta en mi actuar cotidiano.',
    desafios: [
      { text: 'Reflexiono sobre mis creencias, valores y prioridades y trato de identificarlas en mis acciones.', req: true },
      { text: 'Confecciona una lista de acciones en las que se manifiesten aquellas cosas que enseña mi confesión religiosa o espiritualidad y me comprometo a realizarlas.', req: true },
      { text: 'Selecciono el relato de un personaje real que haya demostrado ser coherente con sus creencias espirituales y valores y lo comparto con mi Patrulla y/o Unidad.', req: true },
      { text: 'Evalúo mis acciones en el Consejo de Patrulla, entendiendo que es importante actuar de acuerdo con lo que se piensa y cree.', req: true },
      { text: 'Exploro la herencia espiritual de mi familia y comunidad.', req: false },
      { text: 'Participo de celebraciones (misas, cultos, servicios religiosos, etc.) y festividades vinculadas a mi confesión religiosa o espiritualidad.', req: false },
      { text: 'Busco y selecciono un texto de confesión religiosa o creencia que sea significativo para mí y lo utilizo en mi celebración de Promesa u en otra ocasión especial.', req: false },
      { text: 'Apelo a mi religión o creencias, para expresar gratitud, una necesidad, alegría o tristeza de forma personal o comunitaria.', req: false },
      { text: 'Desarrollo una especialidad vinculada a la espiritualidad.', req: false },
    ]
  },

  // ══════════════════════════════════════════════
  // ÁREA 3: AMBIENTE
  // ══════════════════════════════════════════════
  {
    id: 31, area: 'ambiente', areaLabel: 'Ambiente',
    title: 'Reconozco mi impacto en el ambiente y en la sociedad, adoptando un estilo de vida responsable y sostenible.',
    desafios: [
      { text: 'Indago sobre hábitos responsables y sostenibles para aplicarlos en mi vida diaria. (Por ejemplo, separación de residuos, tomar duchas cortas, desenchufar cargadores de celular u otros electrodomésticos si no los usas).', req: true },
      { text: 'Me informo sobre la huella de carbono y propongo actividades para aprender a reducirla.', req: true },
      { text: 'Realizo actividades de concientización para mi Patrulla, familia, escuela y lugares que frecuento sobre los hábitos responsables y sostenibles.', req: true },
      { text: 'Realizo acciones para reutilizar y reciclar materiales de manera creativa con mi Patrulla, por ejemplo: creo juegos y juguetes con materiales reutilizables junto a mi Patrulla.', req: true },
      { text: 'Planifico un menú variado y nutritivo para mi campamento de Patrulla o Unidad que contenga frutas o verduras de estación y productos locales.', req: true },
      { text: 'Construyo, junto a mi Patrulla o Unidad, un huerto y aprendo sobre la importancia de la agricultura sostenible y el cuidado del suelo.', req: true },
      { text: 'Sé cómo tratar los residuos en campamento, por ejemplo, construyo un pozo de aguas grasas para el tratamiento correcto.', req: true },
      { text: 'Indago sobre actividades que fomenten la reducción de residuos y se las propongo a mi Patrulla y Unidad Scout.', req: false },
      { text: 'Realizo cultivos de plantas nativas.', req: false },
      { text: 'Reutilizo los desechos orgánicos como abono.', req: false },
      { text: 'Investigo de dónde provienen los alimentos que consumo.', req: false },
      { text: 'Desarrollo una especialidad o iniciativa regional o global vinculada a la sostenibilidad.', req: false },
    ]
  },
  {
    id: 32, area: 'ambiente', areaLabel: 'Ambiente',
    title: 'Utilizo los recursos naturales de forma consciente y busco alternativas que promuevan la conservación del ambiente.',
    desafios: [
      { text: 'Me informo sobre qué son los recursos naturales e indago en los efectos que generan si no se usan correctamente.', req: true },
      { text: 'Investigo sobre los agentes contaminantes presentes en mi barrio y realizo acciones para su reducción.', req: true },
      { text: 'Reflexiono sobre el impacto en la naturaleza que tienen las actividades al aire libre que realizo e intento reducirlo.', req: true },
      { text: 'Separo los residuos (orgánicos y no orgánicos), reparo y reciclo aquello que ya no utilizo.', req: true },
      { text: 'Utilizo los desechos orgánicos de mi casa para crear abono.', req: true },
    ]
  },
  {
    id: 33, area: 'ambiente', areaLabel: 'Ambiente',
    title: 'Participo de iniciativas para construir una sociedad más respetuosa con el planeta.',
    desafios: [
      { text: 'Propongo al menos una actividad y/o proyecto ambiental.', req: true },
      { text: 'Participo de jornadas o campañas de limpieza de espacios naturales (lagunas, lagos, ríos, mares, sierras, etc.) y espacios verdes (plazas, parques, etc.).', req: true },
      { text: 'Me sumo a iniciativas de otras organizaciones que trabajan por el ambiente.', req: true },
      { text: 'Investigo, junto con mi Patrulla, sobre las energías renovables y propongo actividades sobre cómo utilizarlas.', req: false },
      { text: 'Construyo y aprendo a utilizar una cocina u horno solar.', req: false },
      { text: 'Promuevo con mi Patrulla acciones que reduzcan el cambio climático dentro de mi comunidad.', req: false },
      { text: 'Participo en una de las iniciativas o desafíos ambientales que propone Scouts de Argentina o la Organización Mundial del Movimiento Scout.', req: false },
    ]
  },
  {
    id: 34, area: 'ambiente', areaLabel: 'Ambiente',
    title: 'Comprendo las causas y consecuencias del impacto ambiental y realizo acciones para preservar y proteger el ambiente.',
    desafios: [
      { text: 'Conozco las causas del cambio climático y las consecuencias en mi país y en el mundo.', req: true },
      { text: 'Realizo una descubierta ambiental con mi Patrulla o Unidad en la que exploramos los problemas ambientales de mi comunidad o región y sus causas.', req: true },
      { text: 'Con mi Patrulla o Unidad realizo un safari fotográfico en el que capto en imágenes los principales problemas ambientales de mi comunidad o región y organizo una muestra de fotos en un lugar público.', req: true },
      { text: 'Calculo mi huella de carbono y busco maneras de disminuirla.', req: false },
    ]
  },
  {
    id: 35, area: 'ambiente', areaLabel: 'Ambiente',
    title: 'Comprendo que todo lo que le hacemos a los seres vivos y al ambiente nos afecta recíprocamente.',
    desafios: [
      { text: 'Me intereso por conocer la relación de los pueblos originarios con la naturaleza (saberes ancestrales) e identifico algunas prácticas que puedan ser aplicadas en mi comunidad.', req: true },
      { text: 'Me informo sobre las especies de flora y fauna en peligro de extinción en mi región y en el país.', req: true },
      { text: 'Aprendo sobre la importancia de reducir el consumo de plásticos de un solo uso y como afecta esto a la fauna y flora de mi región.', req: true },
      { text: 'Realizo la separación de los residuos en reciclables y no reciclables.', req: true },
      { text: 'Investigo sobre cómo los agroquímicos afectan nuestra vida y promuevo el uso de productos ecológicos y amigables para el ambiente en mi hogar y en los espacios donde participo.', req: false },
      { text: 'Aprendo sobre abonos y fertilizantes naturales y los utilizo para mis plantas, huerta, macetas, etc.', req: false },
    ]
  },
  {
    id: 36, area: 'ambiente', areaLabel: 'Ambiente',
    title: 'Entiendo que la Tierra es un lugar precioso y único en el universo, y que todos tenemos la responsabilidad de protegerla y mantenerla saludable.',
    desafios: [
      { text: 'Participo en actividades de reforestación plantando árboles en áreas deforestadas o en peligro.', req: true },
      { text: 'Organizo, junto a mi Patrulla, campañas de concientización sobre la importancia de reducir, reutilizar y reciclar los materiales para minimizar los desechos.', req: true },
      { text: 'Participo en actividades de limpieza comunitaria para recoger basura y promover un entorno más limpio y saludable.', req: true },
      { text: 'Realizo una excursión en un curso de agua para analizar su calidad, posible contaminación y sus causas.', req: false },
      { text: 'Construyo y pruebo un filtro de agua.', req: false },
      { text: 'Construyo y utilizo un catalejo y un telescopio.', req: false },
      { text: 'Construyo hornos, cocinas y fogones conservacionistas.', req: false },
    ]
  },
  {
    id: 37, area: 'ambiente', areaLabel: 'Ambiente',
    title: 'Exploro oportunidades junto a mis amigas y amigos para conectarme con la naturaleza, cuidándola y protegiéndola, ya sea en mi comunidad local o en lugares más lejanos.',
    desafios: [
      { text: 'Participo de al menos dos campamentos de Patrulla.', req: true },
      { text: 'Propongo y participo en la planificación de un campamento con mi Patrulla.', req: true },
      { text: 'Puedo identificar la fauna y flora de mi barrio, provincia, ecorregión y/o lugar de campamento.', req: true },
      { text: 'Llevo un registro de mis noches y lugares de campamentos.', req: true },
      { text: 'Puedo trazar y seguir una pista de al menos un kilómetro, en un medio natural, utilizando señales de pista.', req: true },
      { text: 'Realizo levantamiento de huellas, identifico las especies y rotulo las muestras.', req: true },
      { text: 'Participo de actividades donde deba utilizar mapas y croquis, uso de signos topográficos.', req: false },
      { text: 'Conozco y practico técnicas de acecho para juegos y observación de fauna.', req: false },
      { text: 'Realizo actividades acuáticas (nado, uso de embarcaciones, etc.) respetando las medidas de seguridad.', req: false },
      { text: 'Realizo una colección de piedras y minerales, identificando y rotulando cada muestra.', req: false },
      { text: 'Construyo una estación meteorológica para la predicción del clima.', req: false },
      { text: 'Construyo un refugio para la observación de la fauna.', req: false },
    ]
  },
  {
    id: 38, area: 'ambiente', areaLabel: 'Ambiente',
    title: 'Desarrollo habilidades y técnicas que me permitan el disfrute de la vida en la naturaleza.',
    desafios: [
      { text: 'Aplico técnicas de senderismo (tipo de marcha, alimentación adecuada, tiempos de descanso en las excursiones) con mi Patrulla y/o la Unidad.', req: true },
      { text: 'Realizo caminatas de diferentes niveles de dificultad para mejorar la resistencia física, la coordinación y la confianza en el entorno natural.', req: true },
      { text: 'Participo en el diseño e instalación de las construcciones básicas de un campamento de Patrulla que nos permita disfrutar de la naturaleza: ubicación y armado de la carpa y del sector de Patrulla, preparación para situaciones de tormentas, cocina, mesa...)', req: true },
      { text: 'Utilizo adecuadamente algunas herramientas útiles en la vida al aire libre (cortaplumas, hacha de mano, sierra, etc.) respetando las medidas de seguridad y los cuidados para su uso.', req: true },
      { text: 'Conozco y utilizo distintos tipos de fuego, de acuerdo con mis necesidades (cocina, calor, iluminación) y circunstancias, respetando las reglas de seguridad.', req: true },
      { text: 'Organizo mi mochila para un campamento de Patrulla o de Unidad.', req: true },
      { text: 'Aplico la técnica "no dejar huellas" en los lugares en lo que acampo o realizo excursiones.', req: true },
      { text: 'Busco información y comparto con mi Patrulla sobre áreas naturales protegidas.', req: false },
      { text: 'Mantengo actualizada la lista de materiales y elementos personales para un campamento de Patrulla.', req: false },
      { text: 'Construyo un periscopio y un acuascopio para la observación de la naturaleza.', req: false },
      { text: 'Obtengo una especialidad vinculada al campismo y la vida al aire libre.', req: false },
    ]
  },
  {
    id: 39, area: 'ambiente', areaLabel: 'Ambiente',
    title: 'Exploro y contemplo la naturaleza como un espacio que me permite el bienestar para mí, ayudándome a conectar con lo trascendente.',
    desafios: [
      { text: 'Participo de actividades de observación astronómica para aprender sobre las estrellas, planetas y otros cuerpos celestes, y apreciar la belleza del cielo nocturno en entornos naturales alejados de la contaminación lumínica.', req: true },
      { text: 'Realizo, junto a mi Patrulla, paseos en la naturaleza de manera consciente, prestando atención a los detalles, los sonidos y los aromas del entorno, percibiendo la naturaleza.', req: true },
      { text: 'Diseño y construyo un espacio de reflexión, meditación u oración para mi Patrulla o Unidad en un campamento.', req: true },
      { text: 'Participo de momentos de reflexión, meditación u oración en la naturaleza.', req: true },
      { text: 'Busco textos religiosos o espirituales que hagan referencia a la naturaleza y la comparto en las reflexiones de mi Patrulla o Unidad.', req: true },
      { text: 'Realizo una lista de las acciones que puedo realizar para cuidar nuestra "Casa Común".', req: true },
      { text: 'Me conecto con la naturaleza a través de actividades creativas como la pintura o la creación de objetos, juguetes, adornos, guirnaldas, etc. con elementos naturales.', req: false },
      { text: 'Participo de una excursión nocturna con los ojos vendados intentando captar los sonidos, aromas y sensaciones del entorno.', req: false },
      { text: 'Realizo actividades al aire libre que me permitan conectar con mi cuerpo, tales como excursiones, caminatas, juegos de Kim, etc.', req: false },
    ]
  },

  // ══════════════════════════════════════════════
  // ÁREA 4: HABILIDADES PARA LA VIDA
  // ══════════════════════════════════════════════
  {
    id: 40, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Exploro temas de mi interés con la intención de mejorar cada día.',
    desafios: [
      { text: 'Realizo un listado de los temas sobre los que me gustaría aprender.', req: true },
      { text: 'Elijo al menos dos temas de mi lista y me propongo aprender sobre ellos.', req: true },
      { text: 'Propongo a mi Patrulla o Unidad una descubierta sobre un tema que me interese explorar.', req: true },
      { text: 'Evalúo mi progresión personal y me planteo nuevas acciones para seguir avanzando.', req: true },
      { text: 'Investigo y aplico técnicas de estudio en los temas que deseo y necesito aprender.', req: false },
      { text: 'Desarrollo una especialidad que me interesa.', req: false },
      { text: 'Desempeño un rol en mi Patrulla de acuerdo con mis intereses al menos por un ciclo de programa.', req: false },
    ]
  },
  {
    id: 41, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Experimento diferentes medios y tecnologías que me ayuden a resolver problemas de la vida cotidiana.',
    desafios: [
      { text: 'Utilizo herramientas básicas (martillo, serrucho, destornillador, pinza, tenazas, etc.) para construir o reparar elementos de mi casa, de mi Patrulla, mi Unidad o Grupo Scout.', req: true },
      { text: 'Conozco el funcionamiento de los electrodomésticos y los utilizo para resolver tareas de mi casa.', req: true },
      { text: 'Utilizo tutoriales para resolver dudas sobre el arreglo o uso de elementos de la vida cotidiana.', req: true },
      { text: 'Utilizo juegos en línea o aplicaciones educativas que involucren la resolución de problemas utilizando tecnología. (por ejemplo, GPS, brújula digital, etc.).', req: true },
      { text: 'Utilizo aplicaciones útiles para medir los pasos y las distancias, realizar pronóstico del clima, etc.', req: true },
      { text: 'Conozco el uso de las estructuras, caballetes, poleas, anclajes, tensores y las aplico en las construcciones de campamento.', req: false },
      { text: 'Me desempeño como intendente/a de patrulla al menos por un Ciclo de Programa.', req: false },
      { text: 'Desarrollo una especialidad o insignia especial relacionada con la tecnología.', req: false },
    ]
  },
  {
    id: 42, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Aplico mi conocimiento y habilidades para resolver los desafíos y oportunidades que se me presentan.',
    desafios: [
      { text: 'Soy capaz de hacer algunos arreglos en mi casa.', req: true },
      { text: 'Colaboro en el mantenimiento y arreglo del local de la Unidad y de los materiales de mi Patrulla.', req: true },
      { text: 'Puedo orientarme utilizando una brújula y un mapa, por indicios y medios naturales (sol, estrellas, vegetación, etc.).', req: true },
      { text: 'Utilizo mis especialidades para ayudar a otras personas o resolver problemas que se les presentan.', req: true },
      { text: 'Aplico técnicas de estimación de alturas y de distancia en actividades de mi Patrulla.', req: true },
      { text: 'Realizo una previsión del tiempo por indicios naturales o por instrumentos.', req: false },
      { text: 'Sé cómo realizar arreglos a nuestro local de Patrulla ante situaciones imprevistas.', req: false },
    ]
  },
  {
    id: 43, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Comparto mis pasatiempos y especialidades con amigas y amigos, buscando intereses comunes que podamos desarrollar en conjunto.',
    desafios: [
      { text: 'Participo con mi Patrulla en actividades relacionadas con temas referidos a oficios, trabajos y profesiones.', req: true },
      { text: 'Coordino con los integrantes de mi Patrulla para desarrollar actividades que nos permitan el logro de al menos una competencia.', req: true },
      { text: 'Identifico pasatiempos o intereses personales que puedan convertirse en una especialidad.', req: true },
      { text: 'Desarrollo, junto a mi Patrulla, una descubierta relacionada a un oficio o profesión que nos interese, reconociendo cuáles son las habilidades y competencias necesarias para poder desarrollarlos.', req: false },
      { text: 'Ayudo a un integrante de mi Patrulla a desarrollar una especialidad.', req: false },
    ]
  },
  {
    id: 44, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Asumo un rol de manera responsable en los proyectos y/o actividades de mi Patrulla y/o Unidad.',
    desafios: [
      { text: 'Desempeño diversos roles en mi Patrulla y lo hago con responsabilidad.', req: true },
      { text: 'Apoyo a los miembros de mi Patrulla que estén asumiendo nuevos roles o responsabilidades, compartiendo mis experiencias y conocimientos.', req: true },
      { text: 'Coordino una misión de Patrulla realizada en el contexto de un proyecto de la Unidad.', req: true },
      { text: 'Colaboro en la organización de actividades y reuniones de mi Patrulla.', req: true },
      { text: 'Busco ideas de actividades y proyectos de Unidad y las propongo a mi Consejo de Patrulla (para ser presentadas en la Asamblea).', req: true },
    ]
  },
  {
    id: 45, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Lidero actividades y proyectos, acompañando y motivando a mis pares a sumarse.',
    desafios: [
      { text: 'Asumo la responsabilidad de coordinar a mi Patrulla en una misión o actividad que deba realizar: por ejemplo, una excursión o campamento de patrulla.', req: true },
      { text: 'Propongo ideas de actividades, temas a tratar y soluciones a problemas en mi Consejo de Patrulla.', req: true },
      { text: 'Comparto habilidades específicas relacionadas con los roles en la Patrulla, ayudando a otros a mejorar sus habilidades y competencias.', req: true },
      { text: 'Asumo distintas responsabilidades en las actividades y misiones que realiza mi Patrulla y Unidad.', req: true },
      { text: 'Diseño y coordino una construcción de campamento con mi Patrulla o Unidad.', req: false },
    ]
  },
  {
    id: 46, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Exploro y experimento con diferentes técnicas y tecnologías para resolver problemas, lograr mis objetivos y descubrir soluciones creativas.',
    desafios: [
      { text: 'Experimento con técnicas de supervivencia en la naturaleza, como encender fuego sin fósforos, cocina sin utensilios, potabilización de agua, refugios improvisados, etc.', req: true },
      { text: 'Realizo, junto a mi Patrulla, actividades de orientación y/o exploración, utilizando mapas, croquis y/o brújulas.', req: true },
      { text: 'Exploro y utilizo distintas aplicaciones para resolver temas de mis excursiones, campamentos y salidas, así como de mi vida cotidiana.', req: true },
      { text: 'Realizo, junto a mi Patrulla, una exploración por la ciudad utilizando GPS para orientarme por las calles y registro en esta herramienta los lugares más importantes de mi recorrido.', req: true },
      { text: 'Propongo una solución creativa a un problema o tarea que enfrentamos con la Patrulla o la Unidad.', req: true },
      { text: 'Construyo una cocina o una ducha solar o alguna otra solución técnica creativa que mejore el bienestar en el campamento.', req: true },
      { text: 'Realizo el levantamiento de un croquis topográfico.', req: false },
      { text: 'Utilizo mapas de transporte público o aplicaciones móviles para ayudarme a navegar por la ciudad y encontrar las rutas más convenientes y eficientes.', req: false },
    ]
  },
  {
    id: 47, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Busco información en diversas fuentes, y evalúo su veracidad y relevancia antes de aplicarla de manera crítica y creativa en diferentes situaciones y contextos.',
    desafios: [
      { text: 'Realizo búsquedas de información, evaluando su veracidad, formalidad y credibilidad y lo aplico en mis investigaciones.', req: true },
      { text: 'Investigo temas de mi interés utilizando técnicas de búsqueda de la información.', req: true },
      { text: 'Indago en diversas fuentes, ideas de actividades para hacer con mi Patrulla y de proyectos para realizar con la Unidad.', req: true },
      { text: 'Busco información sobre un tema, sobre el que necesitamos información, para una actividad de Patrulla o de Unidad.', req: true },
      { text: 'Desarrollo una especialidad vinculada a la informática y/o a la comunicación.', req: false },
    ]
  },
  {
    id: 48, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Comprendo la importancia de ser responsable y ético en el uso de la tecnología y la información.',
    desafios: [
      { text: 'Me comunico de manera respetuosa y adecuada con mi Patrulla a través de diferentes medios digitales y analógicos.', req: true },
      { text: 'Participo, junto a mi Patrulla, de un taller sobre Huella e Identidad Digital.', req: true },
      { text: 'Identifico y comprendo el daño que puede realizarse desde las redes sociales y el entorno digital.', req: true },
      { text: 'Me informo sobre los riesgos existentes en las redes y cómo protegerme de ellos.', req: true },
      { text: 'Soy promotor/a de buenas prácticas en las redes.', req: false },
      { text: 'Soy consciente del tiempo que utilizo en el entorno digital y puedo limitarlo para que no me haga daño.', req: false },
      { text: 'Desarrollo una especialidad relacionada con el uso responsable de las redes sociales.', req: false },
    ]
  },
  {
    id: 49, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Administro mis recursos y mi dinero de forma responsable.',
    desafios: [
      { text: 'Administro el dinero que me brindan, registrando mis gastos en una libreta o aplicación y estableciendo metas de ahorro.', req: true },
      { text: 'Colaboro en la confección de un presupuesto para una actividad o misión de mi Patrulla.', req: true },
      { text: 'Realizo un presupuesto para una actividad personal o una compra que deseo realizar y obtengo los recursos necesarios.', req: true },
      { text: 'Organizo una actividad con mi Patrulla para recaudar los fondos que necesitamos.', req: true },
      { text: 'Me propongo asumir el rol de tesorero en mi Patrulla al menos por un ciclo de programa.', req: false },
    ]
  },
  {
    id: 50, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Organizo mi tiempo en forma adecuada diferenciando mis responsabilidades de mi tiempo libre.',
    desafios: [
      { text: 'Organizo mis diferentes tareas (estudio, tiempo libre, scouts, deportes, amigos/as, etc.) por medio de una agenda, calendario semanal u aplicación que me ayude a organizar mis tiempos.', req: true },
      { text: 'Organizo mis tareas otorgándole tiempo y prioridades a cada una.', req: true },
      { text: 'Le dedico al estudio el tiempo necesario para aprender.', req: true },
      { text: 'Organizo mi día para tener tiempo libre y de descanso, teniendo al menos 8 horas de sueño por la noche.', req: true },
      { text: 'Investigo y aplico técnicas de estudio y de concentración.', req: false },
    ]
  },
  {
    id: 51, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Enfrento y supero las dificultades que se me presentan y aprendo de la experiencia.',
    desafios: [
      { text: 'Reviso mi progresión personal, analizando aquellas cosas que hice bien y otras no tanto, y proponiéndome nuevos desafíos.', req: true },
      { text: 'Celebro mis logros y acepto cuando las cosas no me salen bien para poder mejorarlas.', req: true },
      { text: 'Afronto los desafíos de manera positiva y constructiva.', req: true },
      { text: 'En un Consejo de Patrulla evalúo mi desempeño y el de mis compañeras y compañeros en los roles de Patrulla.', req: true },
      { text: 'Pienso en al menos dos circunstancias en las que superé una situación adversa e identifico como lo hice, a quién pedí ayuda, como me sentí.', req: true },
      { text: 'Investigo y comparto la historia o testimonio de al menos tres personajes históricos que superaron dificultades y situaciones adversas.', req: true },
      { text: 'Participo en la evaluación de las actividades de patrulla y de Unidad identificando lo que hicimos bien y lo que debemos mejorar.', req: false },
      { text: 'Participo de un campamento o excursión con los elementos mínimos, durmiendo en refugios improvisados y realizando cocina rústica.', req: false },
    ]
  },
  {
    id: 52, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Desarrollo habilidades para comunicarme claramente con otros; escuchar y valorar sus ideas, trabajando juntos para lograr nuestras metas.',
    desafios: [
      { text: 'Me animo a hablar en público sobre temas de mi interés, compartiendo mis ideas y puntos de vista con respeto y claridad.', req: true },
      { text: 'Me intereso por el uso de diferentes tipos de medios de comunicación (radio, plataformas digitales, etc.).', req: true },
      { text: 'Conozco las claves para lograr una buena comunicación y las aplico en mi patrulla, familia, y los lugares que frecuento.', req: true },
      { text: 'Utilizo adecuadamente las redes sociales para compartir nuestras aventuras, exploraciones, actividades de patrulla y proyectos.', req: true },
      { text: 'Aprendo claves y las utilizo para comunicarme en el desarrollo de actividades.', req: true },
      { text: 'Puedo utilizar distintos códigos para comunicarme: morse, semáforo.', req: true },
      { text: 'Participo de un JOTA o JOTI.', req: false },
    ]
  },
  {
    id: 53, area: 'hab', areaLabel: 'Habilidades para la Vida',
    title: 'Participo de diferentes manifestaciones artísticas en las que expreso mis emociones y sentimientos.',
    desafios: [
      { text: 'Expreso mis emociones de diversas maneras a través de diferentes propuestas (escribo historias, canto, video, historietas, toco algún instrumento musical, pintura, teatro, danza, etc.).', req: true },
      { text: 'Realizo canciones y danzas, junto a mi Patrulla y Unidad.', req: true },
      { text: 'Participo de veladas y fogones, junto a mi Patrulla y mi Unidad.', req: true },
      { text: 'Propongo ideas y ayudo a preparar representaciones artísticas con mi Patrulla.', req: true },
      { text: 'Organizo con mi Patrulla una presentación (canción, sketch, danza...) para una velada o fogón de la Unidad.', req: true },
      { text: 'Expreso mis experiencias y sentimientos en el Libro de Oro de la Patrulla.', req: true },
      { text: 'Propongo a mi Patrulla una actividad artística, que permita expresar emociones y sentimientos.', req: false },
      { text: 'Compongo, junto a mi Patrulla, canciones referidas al Movimiento Scout.', req: false },
      { text: 'Me propongo realizar alguna actividad personal relacionada con el arte, por ejemplo: aprender a tocar un instrumento musical, pintar, dibujar historietas, cantar, actuar, etc.).', req: false },
      { text: 'Construyo un instrumento musical.', req: false },
      { text: 'Desarrollo una especialidad referida al arte.', req: false },
      { text: 'Desempeño el rol de Responsable de Expresión en mi Patrulla al menos por un ciclo de programa.', req: false },
    ]
  },
];

// ════════════════════════════════════════
// STATE MANAGEMENT
// ════════════════════════════════════════
const STORAGE_KEY = 'scout_progresiones_v2';
let state = {};
let currentFilter = 'all';

function loadState() {
  try {
    const saved = localStorage.getItem(STORAGE_KEY);
    if (saved) state = JSON.parse(saved);
  } catch(e) {}
  // Load scout name
  const nameKey = 'scout_name';
  const savedName = localStorage.getItem(nameKey);
  if (savedName) document.getElementById('scoutName').value = savedName;
}

function saveState() {
  try { localStorage.setItem(STORAGE_KEY, JSON.stringify(state)); } catch(e) {}
}

function saveScoutName() {
  try { localStorage.setItem('scout_name', document.getElementById('scoutName').value); } catch(e) {}
}

function getDesafioKey(progId, idx) { return `p${progId}_d${idx}`; }

function isDesafioDone(progId, idx) {
  return !!state[getDesafioKey(progId, idx)];
}

function toggleDesafio(progId, idx) {
  const key = getDesafioKey(progId, idx);
  state[key] = !state[key];
  saveState();
  renderCard(progId);
  updateStats();
}

function isProgresionComplete(prog) {
  // Complete when all required desafios are done
  return prog.desafios.filter(d => d.req).every((d, i) => {
    const realIdx = prog.desafios.indexOf(d);
    return isDesafioDone(prog.id, realIdx);
  });
}

// ════════════════════════════════════════
// RENDER
// ════════════════════════════════════════
const AREA_ICONS = {
  salud: '💙',
  paz: '🤝',
  ambiente: '🌿',
  hab: '⚙️'
};

const AREA_LABELS = {
  salud: 'Salud y Bienestar',
  paz: 'Paz y Desarrollo',
  ambiente: 'Ambiente',
  hab: 'Habilidades para la Vida'
};

function buildApp() {
  const areas = ['salud', 'paz', 'ambiente', 'hab'];
  const app = document.getElementById('app');
  app.innerHTML = '';

  areas.forEach(area => {
    const progs = PROGRESSIONS.filter(p => p.area === area);
    const section = document.createElement('div');
    section.className = 'area-section';
    section.dataset.area = area;
    section.id = `area-${area}`;

    section.innerHTML = `
      <div class="area-header">
        <span class="area-icon">${AREA_ICONS[area]}</span>
        <span class="area-title ${area}">${AREA_LABELS[area]}</span>
        <div class="area-divider ${area}"></div>
      </div>
      <div class="grid" id="grid-${area}"></div>
    `;
    app.appendChild(section);

    const grid = section.querySelector(`#grid-${area}`);
    progs.forEach(prog => {
      const card = document.createElement('div');
      card.className = 'card';
      card.id = `card-${prog.id}`;
      grid.appendChild(card);
      renderCard(prog.id);
    });
  });
}

function renderCard(progId) {
  const prog = PROGRESSIONS.find(p => p.id === progId);
  const card = document.getElementById(`card-${progId}`);
  if (!card) return;

  const isOpen = card.classList.contains('open');
  const complete = isProgresionComplete(prog);

  const totalReq = prog.desafios.filter(d => d.req).length;
  const doneReq = prog.desafios.filter((d, i) => d.req && isDesafioDone(progId, i)).length;
  const totalAll = prog.desafios.length;
  const doneAll = prog.desafios.filter((d, i) => isDesafioDone(progId, i)).length;
  const pct = totalReq > 0 ? Math.round((doneReq / totalReq) * 100) : 0;

  const desafiosHTML = prog.desafios.map((d, i) => {
    const done = isDesafioDone(progId, i);
    const cls = d.req ? 'required' : 'optional';
    const badge = d.req
      ? '<span class="tipo-badge req">Obligatorio</span>'
      : '<span class="tipo-badge opt">Opcional</span>';
    return `
      <div class="desafio-item ${cls} ${done ? 'done' : ''}" onclick="toggleDesafio(${progId}, ${i})">
        <div class="desafio-check"></div>
        <span class="desafio-num">${i+1}.</span>
        <span class="desafio-text">${d.text}</span>
        ${badge}
      </div>
    `;
  }).join('');

  const optCount = prog.desafios.filter(d => !d.req).length;

  card.className = `card${isOpen ? ' open' : ''}${complete ? ' completed' : ''}`;
  card.dataset.area = prog.area;
  card.innerHTML = `
    <div class="card-header ${prog.area}" onclick="toggleCard(${prog.id})">
      <span class="prog-num">${prog.id}</span>
      <span class="prog-title">${prog.title}</span>
      <span class="card-chevron">▼</span>
    </div>
    <div class="card-progress">
      <div class="progress-bar-track">
        <div class="progress-bar-fill" style="width:${pct}%"></div>
      </div>
      <span class="progress-label">${doneReq}/${totalReq} oblig. · ${doneAll}/${totalAll} total</span>
      <button class="check-all-btn" onclick="event.stopPropagation(); checkAllRequired(${prog.id})">✓ Marcar oblig.</button>
    </div>
    <div class="card-body">
      <div class="desafios-label">
        <span class="req-tag">🔵 ${totalReq} obligatorios</span>
        ${optCount > 0 ? `<span class="opt-tag">⭐ ${optCount} opcionales</span>` : ''}
      </div>
      ${desafiosHTML}
      <div class="completed-stamp">🏆 ¡Progresión completada! (obligatorios cumplidos)</div>
    </div>
  `;
}

function toggleCard(progId) {
  const card = document.getElementById(`card-${progId}`);
  card.classList.toggle('open');
}

function checkAllRequired(progId) {
  const prog = PROGRESSIONS.find(p => p.id === progId);
  const allDone = prog.desafios.filter((d, i) => d.req && isDesafioDone(progId, i)).length === prog.desafios.filter(d => d.req).length;
  prog.desafios.forEach((d, i) => {
    if (d.req) state[getDesafioKey(progId, i)] = !allDone;
  });
  saveState();
  renderCard(progId);
  updateStats();
}

function updateStats() {
  let totalDone = 0, reqDone = 0, progComplete = 0;
  PROGRESSIONS.forEach(prog => {
    prog.desafios.forEach((d, i) => {
      if (isDesafioDone(prog.id, i)) {
        totalDone++;
        if (d.req) reqDone++;
      }
    });
    if (isProgresionComplete(prog)) progComplete++;
  });
  document.getElementById('statTotal').textContent = totalDone;
  document.getElementById('statReq').textContent = reqDone;
  document.getElementById('statProg').textContent = progComplete;
}

function filterArea(area, btn) {
  currentFilter = area;
  document.querySelectorAll('.tab-btn').forEach(b => {
    b.classList.remove('active');
    // reset to outline style
    const cls = b.className.split(' ').find(c => ['all','salud','paz','ambiente','hab','completadas'].includes(c));
    if (cls) {
      b.style.background = 'white';
      const colors = { all:'#1565C0', salud:'#0288D1', paz:'#7B1FA2', ambiente:'#388E3C', hab:'#D84315', completadas:'#00897B' };
      b.style.color = colors[cls] || '#333';
    }
  });
  btn.classList.add('active');
  btn.style.background = '';
  btn.style.color = '';

  const areas = ['salud','paz','ambiente','hab'];
  if (area === 'all') {
    areas.forEach(a => {
      const sec = document.getElementById(`area-${a}`);
      if (sec) sec.classList.remove('hidden');
      document.querySelectorAll(`[data-area="${a}"]`).forEach(c => {
        if (c.classList.contains('card')) c.classList.remove('hidden');
      });
    });
  } else if (area === 'completadas') {
    areas.forEach(a => {
      const sec = document.getElementById(`area-${a}`);
      if (sec) sec.classList.remove('hidden');
    });
    PROGRESSIONS.forEach(prog => {
      const card = document.getElementById(`card-${prog.id}`);
      if (!card) return;
      if (isProgresionComplete(prog)) card.classList.remove('hidden');
      else card.classList.add('hidden');
    });
  } else {
    areas.forEach(a => {
      const sec = document.getElementById(`area-${a}`);
      if (!sec) return;
      if (a === area) {
        sec.classList.remove('hidden');
        document.querySelectorAll(`#grid-${a} .card`).forEach(c => c.classList.remove('hidden'));
      } else {
        sec.classList.add('hidden');
      }
    });
  }
}

function expandAll() {
  document.querySelectorAll('.card').forEach(c => c.classList.add('open'));
}

function resetAll() {
  if (!confirm('¿Seguro que querés reiniciar toda tu progresión? Se perderán todos los desafíos marcados.')) return;
  state = {};
  saveState();
  buildApp();
  updateStats();
}

// ════════════════════════════════════════
// INIT
// ════════════════════════════════════════
loadState();
buildApp();
updateStats();
</script>
</body>
</html>
