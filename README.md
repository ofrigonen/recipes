<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>המתכונים שלי</title>
<link href="https://fonts.googleapis.com/css2?family=Fredoka:wght@400;500;600;700&family=Nunito:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&subset=hebrew&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;500;600;700&display=swap" rel="stylesheet">
<style>
  /* ===== CSS VARIABLES ===== */
  :root {
    --cream: #F4FAF7;
    --cream-dark: #E2F0EA;
    --green: #00885E;
    --green-light: #00A872;
    --green-pale: #C8E9DC;
    --accent: #E8770A;
    --accent-light: #F4922E;
    --brown: #1A2E25;
    --brown-mid: #3D6B55;
    --brown-light: #6A9E84;
    --white: #FFFFFF;
    --shadow-soft: 0 4px 20px rgba(0,136,94,0.10);
    --shadow-card: 0 2px 12px rgba(0,80,55,0.08);
    --shadow-hover: 0 8px 32px rgba(0,136,94,0.16);
    --radius: 18px;
    --radius-sm: 10px;
    --transition: all 0.28s cubic-bezier(0.4,0,0.2,1);
  }

  /* ===== RESET & BASE ===== */
  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  body {
    font-family: 'Heebo', 'Nunito', sans-serif;
    background-color: var(--cream);
    color: var(--brown);
    min-height: 100vh;
    direction: rtl;
    /* Paper texture via radial gradients */
    background-image:
      radial-gradient(ellipse at 20% 10%, rgba(0,136,94,0.05) 0%, transparent 50%),
      radial-gradient(ellipse at 80% 90%, rgba(0,168,114,0.04) 0%, transparent 50%),
      radial-gradient(ellipse at 50% 50%, rgba(226,240,234,0.5) 0%, transparent 80%),
      url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='300' height='300'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3CfeColorMatrix type='saturate' values='0'/%3E%3C/filter%3E%3Crect width='300' height='300' filter='url(%23n)' opacity='0.03'/%3E%3C/svg%3E");
    background-size: auto, auto, auto, 300px 300px;
    overflow-x: hidden;
  }

  h1, h2, h3, h4 {
    font-family: 'Fredoka', sans-serif;
    font-weight: 600;
    line-height: 1.2;
  }

  a { color: inherit; text-decoration: none; }
  button { cursor: pointer; border: none; background: none; font-family: 'Heebo', 'Nunito', sans-serif; }
  input, textarea, select { font-family: 'Heebo', 'Nunito', sans-serif; }

  /* ===== LAYOUT ===== */
  .app-wrapper {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 20px;
  }

  /* ===== HEADER ===== */
  .app-header {
    background: linear-gradient(135deg, var(--green) 0%, #006848 100%);
    color: var(--cream);
    padding: 0 20px;
    position: sticky;
    top: 0;
    z-index: 100;
    box-shadow: 0 2px 20px rgba(0,80,55,0.2);
  }

  .header-inner {
    max-width: 1200px;
    margin: 0 auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 68px;
    gap: 16px;
  }

  .logo {
    font-family: 'Fredoka', sans-serif;
    font-size: 1.7rem;
    font-weight: 700;
    color: var(--cream);
    letter-spacing: 0.5px;
    display: flex;
    align-items: center;
    gap: 10px;
    cursor: pointer;
    white-space: nowrap;
  }

  .logo-icon { font-size: 1.5rem; }

  .header-search {
    flex: 1;
    max-width: 360px;
    position: relative;
  }

  .header-search input {
    width: 100%;
    padding: 10px 16px 10px 40px;
    border-radius: 50px;
    border: none;
    background: rgba(255,255,255,0.15);
    color: var(--cream);
    font-size: 0.95rem;
    outline: none;
    transition: var(--transition);
    backdrop-filter: blur(4px);
  }

  .header-search input::placeholder { color: rgba(250,246,240,0.6); }
  .header-search input:focus { background: rgba(255,255,255,0.25); }

  .search-icon {
    position: absolute;
    left: 14px;
    top: 50%;
    transform: translateY(-50%);
    color: rgba(250,246,240,0.7);
    pointer-events: none;
    font-size: 1rem;
  }

  .btn-add-header {
    background: var(--accent);
    color: white;
    padding: 10px 20px;
    border-radius: 50px;
    font-size: 0.95rem;
    font-weight: 700;
    font-family: 'Heebo', 'Nunito', sans-serif;
    display: flex;
    align-items: center;
    gap: 6px;
    transition: var(--transition);
    white-space: nowrap;
    box-shadow: 0 2px 10px rgba(232,119,10,0.3);
  }

  .btn-add-header:hover {
    background: var(--accent-light);
    transform: translateY(-1px);
    box-shadow: 0 4px 16px rgba(232,119,10,0.4);
  }

  /* ===== VIEWS ===== */
  .view { display: none; opacity: 0; transition: opacity 0.3s ease; }
  .view.active { display: block; opacity: 1; }
  .view.fade-in { animation: fadeIn 0.35s ease forwards; }

  @keyframes fadeIn {
    from { opacity: 0; transform: translateY(12px); }
    to { opacity: 1; transform: translateY(0); }
  }

  /* ===== HOME VIEW ===== */
  .home-top {
    padding: 32px 0 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 12px;
  }

  .home-title {
    font-size: 2rem;
    color: var(--brown);
  }

  .recipe-count {
    font-size: 0.9rem;
    color: var(--brown-light);
    background: var(--cream-dark);
    padding: 4px 12px;
    border-radius: 50px;
    font-weight: 600;
  }

  /* Filter bar */
  .filter-bar {
    display: flex;
    align-items: center;
    gap: 8px;
    flex-wrap: wrap;
    padding-bottom: 24px;
  }

  .filter-chip {
    padding: 7px 15px;
    border-radius: 50px;
    font-size: 0.87rem;
    font-weight: 600;
    font-family: 'Heebo', 'Nunito', sans-serif;
    border: 2px solid transparent;
    background: var(--cream-dark);
    color: var(--brown-mid);
    transition: var(--transition);
    cursor: pointer;
  }

  .filter-chip:hover { border-color: var(--green-light); color: var(--green); }
  .filter-chip.active { background: var(--green); color: white; border-color: var(--green); }

  .filter-chip.fav-chip {
    background: #fff8f0;
    color: var(--accent);
    border-color: #fdd9b0;
  }

  .filter-chip.fav-chip.active {
    background: var(--accent);
    color: white;
    border-color: var(--accent);
  }

  .filter-divider {
    width: 1px;
    height: 28px;
    background: var(--cream-dark);
    margin: 0 4px;
  }

  /* Recipe grid */
  .recipe-grid {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
    gap: 22px;
    padding-bottom: 60px;
  }

  .recipe-card {
    background: white;
    border-radius: var(--radius);
    overflow: hidden;
    box-shadow: var(--shadow-card);
    cursor: pointer;
    transition: var(--transition);
    border: 1.5px solid rgba(240,233,222,0.8);
    position: relative;
    animation: cardIn 0.4s ease both;
  }

  @keyframes cardIn {
    from { opacity: 0; transform: scale(0.95) translateY(10px); }
    to { opacity: 1; transform: scale(1) translateY(0); }
  }

  .recipe-card:hover {
    transform: translateY(-5px) scale(1.01);
    box-shadow: var(--shadow-hover);
    border-color: var(--green-pale);
  }

  .card-image-wrap {
    width: 100%;
    height: 175px;
    overflow: hidden;
    background: var(--cream-dark);
    position: relative;
  }

  .card-image-wrap img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    transition: transform 0.4s ease;
  }

  .recipe-card:hover .card-image-wrap img { transform: scale(1.06); }

  .card-no-image {
    width: 100%;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 3rem;
    background: linear-gradient(135deg, var(--cream-dark), #ede5d8);
  }

  .card-star {
    position: absolute;
    top: 10px;
    left: 10px;
    background: rgba(255,255,255,0.9);
    border-radius: 50%;
    width: 32px;
    height: 32px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 1rem;
    box-shadow: 0 2px 8px rgba(0,0,0,0.12);
    backdrop-filter: blur(4px);
  }

  .card-body {
    padding: 16px;
  }

  .card-name {
    font-family: 'Fredoka', sans-serif;
    font-size: 1.15rem;
    font-weight: 600;
    color: var(--brown);
    margin-bottom: 10px;
    line-height: 1.3;
  }

  .card-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 5px;
  }

  .tag-chip {
    font-size: 0.75rem;
    font-weight: 700;
    padding: 3px 9px;
    border-radius: 50px;
    background: var(--green-pale);
    color: var(--green);
  }

  .tag-chip.terracotta {
    background: #fdecd9;
    color: var(--accent);
  }

  /* Empty state */
  .empty-state {
    text-align: center;
    padding: 80px 20px;
    color: var(--brown-light);
  }

  .empty-state .empty-icon { font-size: 4rem; margin-bottom: 20px; }
  .empty-state h3 { font-family: 'Fredoka', sans-serif; font-size: 1.8rem; margin-bottom: 10px; color: var(--brown-mid); }
  .empty-state p { font-size: 1rem; margin-bottom: 24px; }

  .btn-empty {
    background: var(--green);
    color: white;
    padding: 12px 28px;
    border-radius: 50px;
    font-size: 1rem;
    font-weight: 700;
    font-family: 'Heebo', 'Nunito', sans-serif;
    display: inline-flex;
    align-items: center;
    gap: 8px;
    transition: var(--transition);
  }

  .btn-empty:hover { background: var(--green-light); transform: translateY(-2px); }

  /* ===== DETAIL VIEW ===== */
  .detail-back {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    color: var(--olive);
    font-weight: 700;
    font-size: 0.95rem;
    cursor: pointer;
    padding: 28px 0 0;
    transition: var(--transition);
  }

  .detail-back:hover { color: var(--olive-light); }

  /* Detail top: image left, info right — side by side on desktop */
  .detail-top {
    display: flex;
    flex-direction: row-reverse; /* RTL: text on right, image on left */
    gap: 28px;
    align-items: flex-start;
    margin: 24px 0 20px;
  }

  .detail-image-col {
    flex: 0 0 320px;
    width: 320px;
  }

  .detail-hero {
    width: 100%;
    height: 260px;
    border-radius: var(--radius);
    overflow: hidden;
    box-shadow: var(--shadow-soft);
  }

  .detail-hero img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .detail-hero-no-image {
    width: 100%;
    height: 260px;
    border-radius: var(--radius);
    background: linear-gradient(135deg, var(--cream-dark), #ddf0e8);
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 5rem;
    box-shadow: var(--shadow-soft);
  }

  .detail-info-col {
    flex: 1;
    min-width: 0;
    display: flex;
    flex-direction: column;
    gap: 14px;
  }

  .detail-header {
    display: flex;
    flex-direction: column;
    gap: 14px;
    margin-bottom: 0;
  }

  .detail-name {
    font-family: 'Fredoka', sans-serif;
    font-size: 2.2rem;
    color: var(--brown);
    line-height: 1.15;
  }

  .detail-actions {
    display: flex;
    flex-wrap: wrap;
    gap: 8px;
  }

  /* Mobile: stack vertically */
  @media (max-width: 700px) {
    .detail-top {
      flex-direction: column;
      gap: 16px;
    }
    .detail-image-col {
      flex: none;
      width: 100%;
    }
    .detail-hero,
    .detail-hero-no-image {
      height: 220px;
    }
    .detail-name { font-size: 1.7rem; }
  }

  .btn-action {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 9px 16px;
    border-radius: 50px;
    font-size: 0.88rem;
    font-weight: 700;
    font-family: 'Heebo', 'Nunito', sans-serif;
    transition: var(--transition);
    white-space: nowrap;
  }

  .btn-star { background: #fff8f0; color: var(--accent); border: 2px solid #fdd9b0; }
  .btn-star.starred { background: var(--accent); color: white; border-color: var(--accent); }
  .btn-star:hover { transform: scale(1.05); }

  .btn-edit { background: var(--green-pale); color: var(--green); border: 2px solid var(--green-pale); }
  .btn-edit:hover { background: var(--green); color: white; }

  .btn-delete { background: #fde8e4; color: #c0392b; border: 2px solid #fbc8c2; }
  .btn-delete:hover { background: #c0392b; color: white; }

  .btn-whatsapp { background: #e8f8ef; color: #25a244; border: 2px solid #c2ead2; }
  .btn-whatsapp:hover { background: #25a244; color: white; }

  .btn-source { background: var(--cream-dark); color: var(--brown-mid); border: 2px solid var(--cream-dark); }
  .btn-source:hover { background: var(--brown-mid); color: white; }

  .detail-tags {
    display: flex;
    flex-wrap: wrap;
    gap: 7px;
    margin-bottom: 28px;
  }

  .detail-section {
    margin-bottom: 28px;
    background: white;
    border-radius: var(--radius);
    padding: 24px;
    box-shadow: var(--shadow-card);
  }

  .detail-section h3 {
    font-family: 'Fredoka', sans-serif;
    font-size: 1.3rem;
    color: var(--green);
    margin-bottom: 14px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .ingredients-list {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .ingredients-list li {
    padding: 8px 0;
    border-bottom: 1px dashed var(--cream-dark);
    font-size: 1rem;
    display: flex;
    align-items: flex-start;
    gap: 8px;
  }

  .ingredients-list li:last-child { border-bottom: none; }
  .ingredient-dot { color: var(--green); font-size: 0.6rem; margin-top: 7px; flex-shrink: 0; }

  .ing-heading {
    list-style: none;
    padding: 10px 0 4px;
    border-bottom: 2px solid var(--green-pale);
    margin-bottom: 2px;
    color: var(--green);
    font-size: 0.95rem;
    letter-spacing: 0.3px;
  }

  .instructions-text p { margin-bottom: 6px; }
  .instructions-text ol, .instructions-text ul {
    padding-right: 22px;
    margin: 6px 0 10px;
    display: flex;
    flex-direction: column;
    gap: 6px;
  }
  .instructions-text ol { list-style: decimal; }
  .instructions-text ul { list-style: disc; }
  .instructions-text li { line-height: 1.7; }

  .instructions-text {
    font-size: 1rem;
    line-height: 1.85;
    color: var(--brown);
    white-space: pre-wrap;
  }

  .instructions-text strong { color: var(--accent); font-weight: 700; }

  /* ===== FORM VIEW ===== */
  .form-view {
    max-width: 720px;
    margin: 0 auto;
    padding: 28px 0 60px;
  }

  .form-title {
    font-family: 'Fredoka', sans-serif;
    font-size: 2rem;
    color: var(--brown);
    margin-bottom: 28px;
    display: flex;
    align-items: center;
    gap: 12px;
  }

  .form-card {
    background: white;
    border-radius: var(--radius);
    padding: 28px;
    box-shadow: var(--shadow-card);
    margin-bottom: 20px;
  }

  .form-card h3 {
    font-family: 'Fredoka', sans-serif;
    font-size: 1.2rem;
    color: var(--green);
    margin-bottom: 18px;
    display: flex;
    align-items: center;
    gap: 8px;
  }

  .form-field {
    margin-bottom: 18px;
  }

  .form-field label {
    display: block;
    font-size: 0.9rem;
    font-weight: 700;
    color: var(--brown-mid);
    margin-bottom: 7px;
  }

  .form-field input[type="text"],
  .form-field input[type="url"],
  .form-field textarea {
    width: 100%;
    padding: 11px 14px;
    border: 2px solid var(--cream-dark);
    border-radius: var(--radius-sm);
    font-size: 1rem;
    color: var(--brown);
    background: var(--cream);
    outline: none;
    transition: var(--transition);
    resize: vertical;
  }

  .form-field input:focus,
  .form-field textarea:focus {
    border-color: var(--green);
    background: white;
    box-shadow: 0 0 0 3px rgba(0,136,94,0.1);
  }

  /* Image upload */
  .image-upload-zone {
    border: 2.5px dashed var(--cream-dark);
    border-radius: var(--radius-sm);
    padding: 28px;
    text-align: center;
    cursor: pointer;
    transition: var(--transition);
    background: var(--cream);
    position: relative;
  }

  .image-upload-zone:hover { border-color: var(--green-light); background: white; }
  .image-upload-zone input[type="file"] { display: none; }
  .upload-icon { font-size: 2.5rem; margin-bottom: 8px; }
  .upload-text { color: var(--brown-light); font-size: 0.95rem; }
  .upload-text strong { color: var(--green); }

  .image-preview-box {
    margin-top: 14px;
    position: relative;
    display: inline-block;
  }

  .image-preview-box img {
    max-width: 100%;
    max-height: 220px;
    border-radius: var(--radius-sm);
    object-fit: cover;
    box-shadow: var(--shadow-card);
  }

  .btn-remove-img {
    position: absolute;
    top: -8px;
    left: -8px;
    background: var(--terracotta);
    color: white;
    border-radius: 50%;
    width: 26px;
    height: 26px;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.8rem;
    font-weight: 700;
    box-shadow: 0 2px 6px rgba(0,0,0,0.2);
    cursor: pointer;
  }

  .compress-info {
    margin-top: 10px;
    font-size: 0.88rem;
    color: var(--brown-mid);
    background: var(--green-pale);
    border-radius: 8px;
    padding: 8px 12px;
    text-align: right;
    direction: rtl;
  }

  .compress-info .arrow { color: var(--green); font-weight: 700; }
  .compress-error {
    background: #fde8e4;
    color: #c0392b;
    margin-top: 10px;
    font-size: 0.88rem;
    border-radius: 8px;
    padding: 8px 12px;
  }

  /* Instructions toolbar */
  .instructions-toolbar {
    display: flex;
    gap: 6px;
    margin-bottom: 6px;
  }

  .toolbar-btn {
    padding: 5px 12px;
    border-radius: 6px;
    background: var(--cream-dark);
    color: var(--brown-mid);
    font-size: 0.88rem;
    font-weight: 700;
    font-family: 'Heebo', 'Nunito', sans-serif;
    transition: var(--transition);
    border: 1.5px solid transparent;
  }

  .toolbar-btn:hover { background: var(--green-pale); color: var(--green); border-color: var(--green-pale); }

  .toolbar-hint {
    font-size: 0.82rem;
    color: var(--brown-light);
    margin-bottom: 8px;
    line-height: 1.5;
  }
  .toolbar-hint code {
    background: var(--cream-dark);
    padding: 1px 5px;
    border-radius: 4px;
    font-family: monospace;
    color: var(--green);
    font-size: 0.82rem;
  }

  /* Tags input */
  .tags-input-wrap {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    padding: 8px;
    border: 2px solid var(--cream-dark);
    border-radius: var(--radius-sm);
    background: var(--cream);
    min-height: 46px;
    align-items: center;
    transition: var(--transition);
    cursor: text;
  }

  .tags-input-wrap:focus-within { border-color: var(--green); background: white; box-shadow: 0 0 0 3px rgba(0,136,94,0.1); }

  .tag-pill {
    background: var(--green);
    color: white;
    border-radius: 50px;
    padding: 3px 10px;
    font-size: 0.83rem;
    font-weight: 700;
    display: flex;
    align-items: center;
    gap: 6px;
  }

  .tag-pill .remove-tag { cursor: pointer; opacity: 0.7; }
  .tag-pill .remove-tag:hover { opacity: 1; }

  .tags-input-wrap input {
    border: none;
    outline: none;
    background: transparent;
    font-size: 0.93rem;
    color: var(--brown);
    min-width: 120px;
    flex: 1;
  }

  /* Tag suggestions */
  .tag-suggestions {
    display: flex;
    flex-wrap: wrap;
    gap: 6px;
    margin-top: 8px;
  }

  .suggestion-chip {
    padding: 4px 10px;
    border-radius: 50px;
    font-size: 0.8rem;
    font-weight: 600;
    background: var(--cream-dark);
    color: var(--brown-mid);
    cursor: pointer;
    transition: var(--transition);
    border: 1.5px solid transparent;
  }

  .suggestion-chip:hover { background: var(--green-pale); color: var(--green); }

  /* Ingredients list editor */
  .ingredients-editor {
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  .ingredient-row {
    display: flex;
    gap: 8px;
    align-items: center;
  }

  .ingredient-row input {
    flex: 1;
    padding: 9px 12px;
    border: 2px solid var(--cream-dark);
    border-radius: var(--radius-sm);
    font-size: 0.95rem;
    color: var(--brown);
    background: var(--cream);
    outline: none;
    transition: var(--transition);
  }

  .ingredient-row input:focus { border-color: var(--green); background: white; }

  .btn-remove-ingredient {
    width: 32px;
    height: 32px;
    border-radius: 50%;
    background: #fde8e4;
    color: #c0392b;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 0.9rem;
    flex-shrink: 0;
    transition: var(--transition);
  }

  .btn-remove-ingredient:hover { background: #c0392b; color: white; }

  .btn-add-ingredient {
    display: inline-flex;
    align-items: center;
    gap: 6px;
    padding: 8px 16px;
    border-radius: 50px;
    background: var(--green-pale);
    color: var(--green);
    font-size: 0.9rem;
    font-weight: 700;
    font-family: 'Heebo', 'Nunito', sans-serif;
    transition: var(--transition);
    margin-top: 4px;
    width: fit-content;
  }

  .btn-add-ingredient:hover { background: var(--green); color: white; }

  /* Form submit */
  .form-submit-row {
    display: flex;
    gap: 12px;
    justify-content: flex-start;
    flex-wrap: wrap;
    margin-top: 8px;
  }

  .btn-submit {
    background: var(--green);
    color: white;
    padding: 13px 32px;
    border-radius: 50px;
    font-size: 1.05rem;
    font-weight: 700;
    font-family: 'Heebo', 'Nunito', sans-serif;
    transition: var(--transition);
    box-shadow: 0 3px 14px rgba(0,136,94,0.25);
  }

  .btn-submit:hover { background: var(--green-light); transform: translateY(-2px); box-shadow: 0 6px 20px rgba(0,136,94,0.3); }

  .btn-cancel {
    background: var(--cream-dark);
    color: var(--brown-mid);
    padding: 13px 24px;
    border-radius: 50px;
    font-size: 1rem;
    font-weight: 700;
    font-family: 'Heebo', 'Nunito', sans-serif;
    transition: var(--transition);
  }

  .btn-cancel:hover { background: #e0d5c8; }

  /* ===== TOAST ===== */
  .toast {
    position: fixed;
    bottom: 28px;
    left: 50%;
    transform: translateX(-50%) translateY(80px);
    background: var(--brown);
    color: white;
    padding: 13px 24px;
    border-radius: 50px;
    font-size: 0.95rem;
    font-weight: 600;
    z-index: 999;
    opacity: 0;
    transition: all 0.35s cubic-bezier(0.34,1.56,0.64,1);
    pointer-events: none;
    white-space: nowrap;
    box-shadow: 0 4px 20px rgba(0,0,0,0.25);
  }

  .toast.show {
    opacity: 1;
    transform: translateX(-50%) translateY(0);
  }

  .toast.success { background: var(--olive); }
  .toast.error { background: var(--terracotta); }

  /* ===== MODAL ===== */
  .modal-overlay {
    display: none;
    position: fixed;
    inset: 0;
    background: rgba(44,24,16,0.5);
    z-index: 200;
    backdrop-filter: blur(3px);
    align-items: center;
    justify-content: center;
  }

  .modal-overlay.open { display: flex; animation: fadeIn 0.2s ease; }

  .modal-box {
    background: white;
    border-radius: var(--radius);
    padding: 32px;
    max-width: 380px;
    width: 90%;
    box-shadow: 0 20px 60px rgba(44,24,16,0.3);
    text-align: center;
  }

  .modal-box h3 { font-family: 'Fredoka', sans-serif; font-size: 1.5rem; margin-bottom: 10px; }
  .modal-box p { color: var(--brown-light); margin-bottom: 24px; }

  .modal-actions { display: flex; gap: 10px; justify-content: center; }
  .btn-modal-confirm { background: #c0392b; color: white; padding: 10px 24px; border-radius: 50px; font-weight: 700; font-family: 'Heebo', 'Nunito', sans-serif; transition: var(--transition); }
  .btn-modal-confirm:hover { background: #a93226; }
  .btn-modal-cancel { background: var(--cream-dark); color: var(--brown-mid); padding: 10px 20px; border-radius: 50px; font-weight: 700; font-family: 'Heebo', 'Nunito', sans-serif; transition: var(--transition); }
  .btn-modal-cancel:hover { background: #e0d5c8; }

  /* ===== STORAGE WARNING ===== */
  .storage-warning {
    display: none;
    background: #fff3cd;
    border: 2px solid #ffc107;
    border-radius: var(--radius-sm);
    padding: 12px 16px;
    margin-bottom: 16px;
    font-size: 0.9rem;
    color: #856404;
    font-weight: 600;
  }

  /* ===== RESPONSIVE ===== */
  @media (max-width: 640px) {
    .header-inner { height: auto; padding: 12px 0; flex-wrap: wrap; gap: 10px; }
    .header-search { max-width: 100%; order: 3; width: 100%; }
    .logo { font-size: 1.4rem; }
    .btn-add-header { font-size: 0.87rem; padding: 9px 15px; }
    .recipe-grid { grid-template-columns: repeat(2, 1fr); gap: 14px; }
    .form-card { padding: 18px; }
    .form-view { padding: 16px 0 40px; }
  }

  /* detail view wrapper for padding */
  #view-detail .app-wrapper { padding-bottom: 60px; }
</style>
</head>
<body>

<!-- HEADER -->
<header class="app-header">
  <div class="header-inner">
    <div class="logo" onclick="showHome()">
      <span class="logo-icon">🍳</span>
      המתכונים שלי
    </div>
    <div class="header-search">
      <span class="search-icon">🔍</span>
      <input type="text" id="searchInput" placeholder="חיפוש מתכון..." oninput="renderHome()">
    </div>
    <button class="btn-add-header" onclick="showAddForm()">
      <span>+</span> הוספת מתכון
    </button>
  </div>
</header>

<!-- HOME VIEW -->
<div id="view-home" class="view active fade-in">
  <div class="app-wrapper">
    <div class="home-top">
      <h2 class="home-title">📖 כל המתכונים</h2>
      <span class="recipe-count" id="recipeCount">0 מתכונים</span>
    </div>
    <div class="filter-bar" id="filterBar"></div>
    <div class="recipe-grid" id="recipeGrid"></div>
  </div>
</div>

<!-- DETAIL VIEW -->
<div id="view-detail" class="view">
  <div class="app-wrapper">
    <div class="detail-back" onclick="showHome()">← חזרה לכל המתכונים</div>
    <div id="detailContent"></div>
  </div>
</div>

<!-- FORM VIEW -->
<div id="view-form" class="view">
  <div class="app-wrapper">
    <div class="form-view">
      <h2 class="form-title" id="formTitle">✨ הוספת מתכון חדש</h2>
      <div class="storage-warning" id="storageWarning">⚠️ האחסון מתקרב לגבול (4MB). לא ניתן להוסיף תמונות חדשות.</div>

      <!-- Basic Info -->
      <div class="form-card">
        <h3>📝 פרטים בסיסיים</h3>
        <div class="form-field">
          <label>שם המתכון *</label>
          <input type="text" id="f-name" placeholder="למשל: עוגת תפוחים של סבתא...">
        </div>
        <div class="form-field">
          <label>קישור למקור (אתר / URL)</label>
          <input type="url" id="f-url" placeholder="https://...">
        </div>
        <div class="form-field">
          <label>קטגוריות (הוסף ולחץ Enter)</label>
          <div class="tags-input-wrap" id="tagsWrap" onclick="document.getElementById('tagInput').focus()">
            <input type="text" id="tagInput" placeholder="הקלד קטגוריה...">
          </div>
          <div class="tag-suggestions" id="tagSuggestions"></div>
        </div>
      </div>

      <!-- Image -->
      <div class="form-card">
        <h3>📸 תמונה</h3>
        <div class="image-upload-zone" id="uploadZone" onclick="document.getElementById('imgInput').click()">
          <input type="file" id="imgInput" accept="image/*" onchange="handleImageUpload(this)">
          <div class="upload-icon">🖼️</div>
          <div class="upload-text">לחץ לבחירת תמונה<br><strong>JPG, PNG, WEBP</strong> • מקסימום 150KB אחרי כיווץ</div>
        </div>
        <div class="image-preview-box" id="imgPreviewBox" style="display:none">
          <img id="imgPreview" src="" alt="תצוגה מקדימה">
          <div class="btn-remove-img" onclick="removeImage()">✕</div>
        </div>
        <div id="compressInfo" class="compress-info" style="display:none"></div>
        <div id="compressError" class="compress-error" style="display:none"></div>
      </div>

      <!-- Ingredients -->
      <div class="form-card">
        <h3>🥕 מצרכים</h3>
        <div class="toolbar-hint">ניתן להוסיף כותרת קבוצה בשורה שמתחילה ב- <code>##</code> (למשל: <code>## לרוטב</code>)</div>
        <div class="instructions-toolbar">
          <button class="toolbar-btn" onclick="wrapIngHeading()" title="כותרת קבוצה">## כותרת</button>
          <button class="toolbar-btn" onclick="wrapIngBold()" title="הדגשה"><b>B</b> הדגשה</button>
        </div>
        <div class="form-field" style="margin:0">
          <textarea id="f-ingredients" rows="8" placeholder="2 כוסות קמח&#10;3 ביצים&#10;&#10;## לרוטב&#10;1 כוס שמנת&#10;מלח ופלפל"></textarea>
        </div>
      </div>

      <!-- Instructions -->
      <div class="form-card">
        <h3>👨‍🍳 הוראות הכנה</h3>
        <div class="instructions-toolbar">
          <button class="toolbar-btn" onclick="wrapBold()" title="הדגשה"><b>B</b> הדגשה</button>
          <button class="toolbar-btn" onclick="insertBullet()" title="תבליט">• תבליט</button>
          <button class="toolbar-btn" onclick="insertNumbered()" title="ממוספר">1. ממוספר</button>
        </div>
        <div class="form-field" style="margin:0">
          <textarea id="f-instructions" rows="10" placeholder="כתוב את הוראות ההכנה כאן...&#10;• ניתן להשתמש בתבליטים&#10;1. או ממוספר&#10;**טקסט** להדגשה"></textarea>
        </div>
      </div>

      <!-- Submit -->
      <div class="form-submit-row">
        <button class="btn-submit" onclick="saveRecipe()">💾 שמירת מתכון</button>
        <button class="btn-cancel" onclick="showHome()">ביטול</button>
      </div>
    </div>
  </div>
</div>

<!-- Toast -->
<div class="toast" id="toast"></div>

<!-- Delete Modal -->
<div class="modal-overlay" id="deleteModal">
  <div class="modal-box">
    <h3>🗑️ מחיקת מתכון</h3>
    <p>האם אתה בטוח שברצונך למחוק את המתכון הזה? פעולה זו אינה הפיכה.</p>
    <div class="modal-actions">
      <button class="btn-modal-confirm" onclick="confirmDelete()">כן, מחק</button>
      <button class="btn-modal-cancel" onclick="closeDeleteModal()">ביטול</button>
    </div>
  </div>
</div>

<script>
// ===== STATE =====
let recipes = [];
let activeFilters = new Set();
let favOnly = false;
let currentRecipeId = null;
let editingId = null;
let deleteTargetId = null;
let formTags = [];
let compressedImageData = null;

// ===== STORAGE =====
const STORAGE_KEY = 'recipes_v2';
const STORAGE_LIMIT = 4 * 1024 * 1024; // 4MB

function save() {
  try {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(recipes));
  } catch(e) {
    showToast('שגיאה בשמירה — האחסון מלא!', 'error');
  }
}

function load() {
  try {
    const raw = localStorage.getItem(STORAGE_KEY);
    recipes = raw ? JSON.parse(raw) : [];
  } catch(e) {
    recipes = [];
  }
}

function getStorageSize() {
  let total = 0;
  for (let key in localStorage) {
    if (localStorage.hasOwnProperty(key)) {
      total += (localStorage[key].length + key.length) * 2;
    }
  }
  return total;
}

function checkStorageWarning() {
  const size = getStorageSize();
  const warn = document.getElementById('storageWarning');
  if (size > STORAGE_LIMIT * 0.85) {
    warn.style.display = 'block';
    return true;
  }
  warn.style.display = 'none';
  return false;
}

// ===== UTILS =====
function uid() { return Date.now().toString(36) + Math.random().toString(36).slice(2); }

function renderBold(text) {
  // Escape HTML first
  const escaped = text
    .replace(/&/g, '&amp;')
    .replace(/</g, '&lt;')
    .replace(/>/g, '&gt;');

  const lines = escaped.split('\n');
  let html = '';
  let inOl = false, inUl = false;

  const closeOl = () => { if (inOl) { html += '</ol>'; inOl = false; } };
  const closeUl = () => { if (inUl) { html += '</ul>'; inUl = false; } };

  lines.forEach(line => {
    const boldLine = line.replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>');
    const numberedMatch = boldLine.match(/^(\d+)\.\s+(.*)/);
    const bulletMatch = boldLine.match(/^[•\-\*]\s+(.*)/);

    if (numberedMatch) {
      closeUl();
      if (!inOl) { html += '<ol>'; inOl = true; }
      html += `<li>${numberedMatch[2]}</li>`;
    } else if (bulletMatch) {
      closeOl();
      if (!inUl) { html += '<ul>'; inUl = true; }
      html += `<li>${bulletMatch[1]}</li>`;
    } else {
      closeOl(); closeUl();
      if (boldLine.trim() === '') {
        html += '<br>';
      } else {
        html += `<p>${boldLine}</p>`;
      }
    }
  });
  closeOl(); closeUl();
  return html;
}

function renderIngredients(text) {
  const lines = text.split('\n');
  let html = '';
  lines.forEach(line => {
    const trimmed = line.trim();
    if (!trimmed) return;
    if (trimmed.startsWith('##')) {
      const heading = trimmed.replace(/^##\s*/, '');
      html += `<li class="ing-heading"><strong>${heading}</strong></li>`;
    } else {
      const bold = trimmed.replace(/\*\*(.+?)\*\*/g, '<strong>$1</strong>');
      html += `<li><span class="ingredient-dot">●</span>${bold}</li>`;
    }
  });
  return html;
}

function boldToWhatsApp(text) {
  return text
    .replace(/\*\*(.+?)\*\*/g, '*$1*')
    .replace(/^## (.+)$/gm, '*$1*');  // headings become bold in WhatsApp
}

function showToast(msg, type='success') {
  const t = document.getElementById('toast');
  t.textContent = msg;
  t.className = 'toast show ' + type;
  setTimeout(() => { t.className = 'toast'; }, 2800);
}

function getAllCategories() {
  const cats = new Set();
  recipes.forEach(r => r.tags?.forEach(t => cats.add(t)));
  return [...cats];
}

// ===== VIEWS =====
function switchView(id) {
  document.querySelectorAll('.view').forEach(v => {
    v.classList.remove('active', 'fade-in');
    v.style.display = 'none';
  });
  const el = document.getElementById(id);
  el.style.display = 'block';
  requestAnimationFrame(() => {
    el.classList.add('active', 'fade-in');
  });
  window.scrollTo({ top: 0, behavior: 'smooth' });
}

// ===== HOME =====
function showHome() {
  switchView('view-home');
  renderHome();
}

function renderHome() {
  const search = document.getElementById('searchInput').value.toLowerCase().trim();
  let filtered = recipes.filter(r => {
    if (favOnly && !r.starred) return false;
    if (activeFilters.size > 0 && !r.tags?.some(t => activeFilters.has(t))) return false;
    if (search && !r.name?.toLowerCase().includes(search) && !r.tags?.join(' ').toLowerCase().includes(search)) return false;
    return true;
  });

  // Sort: starred first, then newest
  filtered.sort((a, b) => {
    if (b.starred !== a.starred) return b.starred ? 1 : -1;
    return (b.id || '').localeCompare(a.id || '');
  });

  document.getElementById('recipeCount').textContent = `${recipes.length} מתכונים`;

  // Filter bar
  const cats = getAllCategories();
  const bar = document.getElementById('filterBar');
  bar.innerHTML = '';

  // Fav toggle
  const favBtn = document.createElement('button');
  favBtn.className = 'filter-chip fav-chip' + (favOnly ? ' active' : '');
  favBtn.textContent = 'מועדפים בלבד ⭐';
  favBtn.onclick = () => { favOnly = !favOnly; renderHome(); };
  bar.appendChild(favBtn);

  if (cats.length > 0) {
    const div = document.createElement('div');
    div.className = 'filter-divider';
    bar.appendChild(div);

    cats.sort().forEach(cat => {
      const chip = document.createElement('button');
      chip.className = 'filter-chip' + (activeFilters.has(cat) ? ' active' : '');
      chip.textContent = cat;
      chip.onclick = () => {
        if (activeFilters.has(cat)) activeFilters.delete(cat);
        else activeFilters.add(cat);
        renderHome();
      };
      bar.appendChild(chip);
    });
  }

  // Grid
  const grid = document.getElementById('recipeGrid');
  grid.innerHTML = '';

  if (filtered.length === 0) {
    grid.innerHTML = `<div class="empty-state" style="grid-column:1/-1">
      <div class="empty-icon">${recipes.length === 0 ? '📖' : '🔍'}</div>
      <h3>${recipes.length === 0 ? 'עדיין אין מתכונים!' : 'לא נמצאו מתכונים'}</h3>
      <p>${recipes.length === 0 ? 'הוסף את המתכון הראשון שלך.' : 'נסה לשנות את החיפוש או הסינון.'}</p>
      ${recipes.length === 0 ? '<button class="btn-empty" onclick="showAddForm()">+ הוספת מתכון ראשון</button>' : ''}
    </div>`;
    return;
  }

  filtered.forEach((r, i) => {
    const card = document.createElement('div');
    card.className = 'recipe-card';
    card.style.animationDelay = (i * 0.05) + 's';
    card.onclick = () => showDetail(r.id);

    const tagColors = ['', 'terracotta'];
    const tagsHtml = (r.tags || []).map((t, idx) =>
      `<span class="tag-chip ${tagColors[idx % 2]}">${t}</span>`
    ).join('');

    card.innerHTML = `
      <div class="card-image-wrap">
        ${r.image
          ? `<img src="${r.image}" alt="${r.name}" loading="lazy">`
          : `<div class="card-no-image">🍽️</div>`}
        ${r.starred ? '<div class="card-star">⭐</div>' : ''}
      </div>
      <div class="card-body">
        <div class="card-name">${r.name || 'מתכון ללא שם'}</div>
        <div class="card-tags">${tagsHtml}</div>
      </div>
    `;
    grid.appendChild(card);
  });
}

// ===== DETAIL =====
function showDetail(id) {
  currentRecipeId = id;
  const r = recipes.find(x => x.id === id);
  if (!r) return;
  switchView('view-detail');

  const imageHtml = r.image
    ? `<div class="detail-hero"><img src="${r.image}" alt="${r.name}"></div>`
    : `<div class="detail-hero-no-image">🍽️</div>`;

  const tagColors = ['', 'terracotta'];
  const tagsHtml = (r.tags || []).map((t, idx) =>
    `<span class="tag-chip ${tagColors[idx % 2]}" style="font-size:0.9rem;padding:5px 14px">${t}</span>`
  ).join('');

  const ingredientsHtml = renderIngredients((r.ingredients || []).join('\n'));

  const instructionsHtml = renderBold(r.instructions || '');

  document.getElementById('detailContent').innerHTML = `
    <div class="detail-top">
      <div class="detail-image-col">${imageHtml}</div>
      <div class="detail-info-col">
        <div class="detail-header">
          <h1 class="detail-name">${r.name || 'מתכון ללא שם'}</h1>
          <div class="detail-actions">
            <button class="btn-action btn-star ${r.starred ? 'starred' : ''}" onclick="toggleStar('${id}')">
              ${r.starred ? '⭐ מועדף' : '☆ הוסף למועדפים'}
            </button>
            <button class="btn-action btn-whatsapp" onclick="copyWhatsApp('${id}')">📋 העתק לוואטסאפ</button>
            <button class="btn-action btn-edit" onclick="showEditForm('${id}')">✏️ עריכה</button>
            <button class="btn-action btn-delete" onclick="openDeleteModal('${id}')">🗑️ מחק</button>
          </div>
        </div>
        <div class="detail-tags">${tagsHtml}</div>
        ${r.sourceUrl ? `<div><a href="${r.sourceUrl}" target="_blank" rel="noopener" class="btn-action btn-source" style="display:inline-flex">🔗 עבור למקור המתכון</a></div>` : ''}
      </div>
    </div>
    ${ingredientsHtml ? `<div class="detail-section"><h3>🥕 מצרכים</h3><ul class="ingredients-list">${ingredientsHtml}</ul></div>` : ''}
    ${r.instructions ? `<div class="detail-section"><h3>👨‍🍳 הוראות הכנה</h3><div class="instructions-text">${instructionsHtml}</div></div>` : ''}
  `;
}

function toggleStar(id) {
  const r = recipes.find(x => x.id === id);
  if (!r) return;
  r.starred = !r.starred;
  save();
  showDetail(id);
  showToast(r.starred ? '⭐ נוסף למועדפים!' : 'הוסר מהמועדפים');
}

// ===== WHATSAPP =====
function copyWhatsApp(id) {
  const r = recipes.find(x => x.id === id);
  if (!r) return;

  const ingredientsList = (r.ingredients || []).filter(i => i.trim()).map(i => `• ${i}`).join('\n');
  const instructions = boldToWhatsApp(r.instructions || '');
  const categories = (r.tags || []).join(', ');

  let text = `*${r.name}*\n`;
  if (categories) text += `\n🏷️ קטגוריות: ${categories}\n`;
  text += `\n🥄 *מצרכים:*\n${ingredientsList}`;
  if (instructions) text += `\n\n📝 *הוראות הכנה:*\n${instructions}`;
  if (r.sourceUrl) text += `\n\n🔗 מקור: ${r.sourceUrl}`;

  // Try modern clipboard API first, fall back to execCommand
  if (navigator.clipboard && navigator.clipboard.writeText) {
    navigator.clipboard.writeText(text).then(() => {
      showToast('✅ הועתק! אפשר להדביק בוואטסאפ.');
    }).catch(() => fallbackCopy(text));
  } else {
    fallbackCopy(text);
  }
}

function fallbackCopy(text) {
  const ta = document.createElement('textarea');
  ta.value = text;
  ta.style.cssText = 'position:fixed;top:-9999px;right:-9999px;opacity:0';
  document.body.appendChild(ta);
  ta.focus();
  ta.select();
  try {
    document.execCommand('copy');
    showToast('✅ הועתק! אפשר להדביק בוואטסאפ.');
  } catch(e) {
    showToast('שגיאה בהעתקה — נסה להעתיק ידנית', 'error');
  }
  document.body.removeChild(ta);
}

// ===== DELETE =====
function openDeleteModal(id) {
  deleteTargetId = id;
  document.getElementById('deleteModal').classList.add('open');
}

function closeDeleteModal() {
  deleteTargetId = null;
  document.getElementById('deleteModal').classList.remove('open');
}

function confirmDelete() {
  if (!deleteTargetId) return;
  recipes = recipes.filter(r => r.id !== deleteTargetId);
  save();
  closeDeleteModal();
  showToast('🗑️ המתכון נמחק', 'error');
  showHome();
}

// ===== FORM =====
function showAddForm() {
  editingId = null;
  formTags = [];
  compressedImageData = null;
  resetForm();
  document.getElementById('formTitle').textContent = '✨ הוספת מתכון חדש';
  checkStorageWarning();
  renderTagSuggestions();
  switchView('view-form');
}

function showEditForm(id) {
  editingId = id;
  const r = recipes.find(x => x.id === id);
  if (!r) return;
  formTags = [...(r.tags || [])];
  compressedImageData = r.image || null;
  resetForm();
  document.getElementById('formTitle').textContent = '✏️ עריכת מתכון';
  document.getElementById('f-name').value = r.name || '';
  document.getElementById('f-url').value = r.sourceUrl || '';
  document.getElementById('f-instructions').value = r.instructions || '';
  document.getElementById('f-ingredients').value = (r.ingredients || []).join('\n');
  checkStorageWarning();
  renderTagPills();
  renderTagSuggestions();

  // Image preview
  if (r.image) {
    document.getElementById('imgPreviewBox').style.display = 'inline-block';
    document.getElementById('imgPreview').src = r.image;
    document.getElementById('compressInfo').style.display = 'none';
  }

  switchView('view-form');
}

function resetForm() {
  document.getElementById('f-name').value = '';
  document.getElementById('f-url').value = '';
  document.getElementById('f-instructions').value = '';
  document.getElementById('f-ingredients').value = '';
  document.getElementById('imgPreviewBox').style.display = 'none';
  document.getElementById('imgPreview').src = '';
  document.getElementById('compressInfo').style.display = 'none';
  document.getElementById('compressError').style.display = 'none';
  document.getElementById('imgInput').value = '';
  renderTagPills();
}

// ===== TAGS =====
function renderTagPills() {
  const wrap = document.getElementById('tagsWrap');
  // Remove old pills
  wrap.querySelectorAll('.tag-pill').forEach(p => p.remove());
  // Insert pills before input
  const input = document.getElementById('tagInput');
  formTags.forEach(tag => {
    const pill = document.createElement('span');
    pill.className = 'tag-pill';
    pill.innerHTML = `${tag}<span class="remove-tag" onclick="removeTag('${tag}')">✕</span>`;
    wrap.insertBefore(pill, input);
  });
}

function addTag(tag) {
  tag = tag.trim();
  if (!tag || formTags.includes(tag)) return;
  formTags.push(tag);
  renderTagPills();
  renderTagSuggestions();
  document.getElementById('tagInput').value = '';
}

function removeTag(tag) {
  formTags = formTags.filter(t => t !== tag);
  renderTagPills();
  renderTagSuggestions();
}

function renderTagSuggestions() {
  const allCats = getAllCategories().filter(c => !formTags.includes(c));
  const sug = document.getElementById('tagSuggestions');
  sug.innerHTML = '';
  if (allCats.length === 0) return;
  const label = document.createElement('span');
  label.style.cssText = 'font-size:0.8rem;color:var(--brown-light);font-weight:600;';
  label.textContent = 'קטגוריות קיימות: ';
  sug.appendChild(label);
  allCats.forEach(cat => {
    const chip = document.createElement('button');
    chip.type = 'button';
    chip.className = 'suggestion-chip';
    chip.textContent = cat;
    chip.onclick = () => addTag(cat);
    sug.appendChild(chip);
  });
}

document.addEventListener('DOMContentLoaded', () => {
  const tagInput = document.getElementById('tagInput');
  tagInput.addEventListener('keydown', e => {
    if (e.key === 'Enter' || e.key === ',') {
      e.preventDefault();
      addTag(tagInput.value);
    } else if (e.key === 'Backspace' && !tagInput.value && formTags.length > 0) {
      removeTag(formTags[formTags.length - 1]);
    }
  });
});

// ===== INGREDIENTS =====
function getIngredients() {
  return document.getElementById('f-ingredients').value
    .split('\n')
    .map(l => l.trim())
    .filter(Boolean);
}

// ===== BOLD TOOLBAR =====
function wrapInTextarea(taId, before, after) {
  const ta = document.getElementById(taId);
  const start = ta.selectionStart, end = ta.selectionEnd;
  const sel = ta.value.substring(start, end);
  ta.value = ta.value.substring(0, start) + before + sel + after + ta.value.substring(end);
  ta.focus();
  ta.setSelectionRange(start + before.length, end + before.length);
}

function insertAtLineStart(taId, prefix) {
  const ta = document.getElementById(taId);
  const start = ta.selectionStart;
  // Find the start of the current line
  const before = ta.value.lastIndexOf('\n', start - 1);
  const lineStart = before + 1;
  ta.value = ta.value.substring(0, lineStart) + prefix + ta.value.substring(lineStart);
  ta.focus();
  ta.setSelectionRange(start + prefix.length, start + prefix.length);
}

function wrapBold() { wrapInTextarea('f-instructions', '**', '**'); }
function wrapIngBold() { wrapInTextarea('f-ingredients', '**', '**'); }

function wrapIngHeading() {
  const ta = document.getElementById('f-ingredients');
  const start = ta.selectionStart;
  const before = ta.value.lastIndexOf('\n', start - 1);
  const lineStart = before + 1;
  const lineText = ta.value.substring(lineStart, ta.value.indexOf('\n', lineStart) === -1 ? ta.value.length : ta.value.indexOf('\n', lineStart));
  // Toggle: if already a heading remove it, otherwise add
  if (lineText.startsWith('## ')) {
    ta.value = ta.value.substring(0, lineStart) + lineText.substring(3) + ta.value.substring(lineStart + lineText.length);
    ta.focus();
    ta.setSelectionRange(start - 3, start - 3);
  } else {
    ta.value = ta.value.substring(0, lineStart) + '## ' + ta.value.substring(lineStart);
    ta.focus();
    ta.setSelectionRange(start + 3, start + 3);
  }
}

function insertBullet() {
  const ta = document.getElementById('f-instructions');
  const start = ta.selectionStart, end = ta.selectionEnd;
  if (start === end) {
    // No selection: insert bullet at line start
    insertAtLineStart('f-instructions', '• ');
  } else {
    // Wrap each selected line
    const sel = ta.value.substring(start, end);
    const bulleted = sel.split('\n').map(l => l.trim() ? '• ' + l : l).join('\n');
    ta.value = ta.value.substring(0, start) + bulleted + ta.value.substring(end);
    ta.focus();
  }
}

function insertNumbered() {
  const ta = document.getElementById('f-instructions');
  const start = ta.selectionStart, end = ta.selectionEnd;
  if (start === end) {
    insertAtLineStart('f-instructions', '1. ');
  } else {
    const sel = ta.value.substring(start, end);
    let counter = 1;
    const numbered = sel.split('\n').map(l => l.trim() ? `${counter++}. ${l}` : l).join('\n');
    ta.value = ta.value.substring(0, start) + numbered + ta.value.substring(end);
    ta.focus();
  }
}

// ===== IMAGE UPLOAD =====
async function handleImageUpload(input) {
  const file = input.files[0];
  if (!file) return;
  const origKB = Math.round(file.size / 1024);

  document.getElementById('compressError').style.display = 'none';
  document.getElementById('compressInfo').style.display = 'none';

  try {
    const compressed = await compressImage(file, 400, 0.7);
    const compKB = Math.round(compressed.length * 0.75 / 1024); // base64 to bytes approx

    if (compKB > 150) {
      document.getElementById('compressError').style.display = 'block';
      document.getElementById('compressError').textContent = `⚠️ התמונה גדולה מדי גם אחרי כיווץ (${compKB} KB). אנא בחר תמונה קטנה יותר.`;
      compressedImageData = null;
      document.getElementById('imgPreviewBox').style.display = 'none';
      return;
    }

    compressedImageData = compressed;
    document.getElementById('imgPreview').src = compressed;
    document.getElementById('imgPreviewBox').style.display = 'inline-block';
    document.getElementById('compressInfo').style.display = 'block';
    document.getElementById('compressInfo').innerHTML =
      `גודל מקורי: <strong>${origKB} KB</strong> <span class="arrow">←</span> אחרי כיווץ: <strong>${compKB} KB</strong>`;

  } catch(e) {
    document.getElementById('compressError').style.display = 'block';
    document.getElementById('compressError').textContent = 'שגיאה בטעינת התמונה. אנא נסה שוב.';
  }
}

function compressImage(file, maxPx, quality) {
  return new Promise((resolve, reject) => {
    const reader = new FileReader();
    reader.onload = e => {
      const img = new Image();
      img.onload = () => {
        let { width: w, height: h } = img;
        if (w > maxPx || h > maxPx) {
          if (w > h) { h = Math.round(h * maxPx / w); w = maxPx; }
          else { w = Math.round(w * maxPx / h); h = maxPx; }
        }
        const canvas = document.createElement('canvas');
        canvas.width = w; canvas.height = h;
        const ctx = canvas.getContext('2d');
        ctx.drawImage(img, 0, 0, w, h);
        resolve(canvas.toDataURL('image/jpeg', quality));
      };
      img.onerror = reject;
      img.src = e.target.result;
    };
    reader.onerror = reject;
    reader.readAsDataURL(file);
  });
}

function removeImage() {
  compressedImageData = null;
  document.getElementById('imgPreviewBox').style.display = 'none';
  document.getElementById('imgPreview').src = '';
  document.getElementById('compressInfo').style.display = 'none';
  document.getElementById('compressError').style.display = 'none';
  document.getElementById('imgInput').value = '';
}

// ===== SAVE RECIPE =====
function saveRecipe() {
  const name = document.getElementById('f-name').value.trim();
  if (!name) {
    showToast('❗ יש להזין שם למתכון', 'error');
    document.getElementById('f-name').focus();
    return;
  }

  // Storage check if adding image
  if (compressedImageData && !editingId) {
    if (checkStorageWarning()) {
      showToast('❗ האחסון מלא, לא ניתן לשמור תמונה חדשה', 'error');
      return;
    }
  }

  const recipe = {
    id: editingId || uid(),
    name,
    sourceUrl: document.getElementById('f-url').value.trim(),
    tags: [...formTags],
    image: compressedImageData,
    ingredients: getIngredients(),
    instructions: document.getElementById('f-instructions').value.trim(),
    starred: editingId ? (recipes.find(r => r.id === editingId)?.starred || false) : false,
    createdAt: editingId ? (recipes.find(r => r.id === editingId)?.createdAt || Date.now()) : Date.now(),
  };

  if (editingId) {
    const idx = recipes.findIndex(r => r.id === editingId);
    if (idx !== -1) recipes[idx] = recipe;
  } else {
    recipes.unshift(recipe);
  }

  save();
  showToast(editingId ? '✅ המתכון עודכן בהצלחה!' : '🎉 המתכון נשמר בהצלחה!');
  editingId = null;
  showDetail(recipe.id);
}

// ===== INIT =====
load();
renderHome();
</script>
</body>
</html>
