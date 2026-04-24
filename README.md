<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dari Kaus Kaki</title>
  <link href="https://fonts.googleapis.com/css2?family=Playfair+Display:ital,wght@0,400;0,700;1,400;1,600&family=Lora:ital,wght@0,400;0,500;1,400&display=swap" rel="stylesheet">
  <style>
    :root {
      --cream: #f5f0e8;
      --warm-white: #faf8f4;
      --sand: #d4c5a9;
      --bark: #7a6248;
      --deep: #2e2118;
      --sage: #8a9e7e;
      --rust: #b85c3a;
      --gold: #c9a84c;
    }

    * { margin: 0; padding: 0; box-sizing: border-box; }

    body {
      background: var(--warm-white);
      color: var(--deep);
      font-family: 'Lora', serif;
      overflow-x: hidden;
    }

    /* ── HERO ── */
    .hero {
      position: relative;
      min-height: 100vh;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: flex-end;
      padding-bottom: 4rem;
      overflow: hidden;
    }

    .hero-photo {
      position: absolute;
      inset: 0;
      width: 100%;
      height: 100%;
      object-fit: cover;
      object-position: center top;
      filter: sepia(20%) brightness(0.65);
    }

    .hero-overlay {
      position: absolute;
      inset: 0;
      background: linear-gradient(
        to bottom,
        transparent 30%,
        rgba(30, 20, 10, 0.5) 60%,
        rgba(20, 12, 5, 0.85) 100%
      );
    }

    .hero-content {
      position: relative;
      z-index: 2;
      text-align: center;
      padding: 0 2rem;
      animation: fadeUp 1.2s ease both;
    }

    .hero-tag {
      font-family: 'Lora', serif;
      font-style: italic;
      font-size: 0.85rem;
      letter-spacing: 0.25em;
      color: var(--sand);
      margin-bottom: 1.2rem;
      text-transform: uppercase;
    }

    .hero-title {
      font-family: 'Playfair Display', serif;
      font-size: clamp(2.8rem, 8vw, 5.5rem);
      font-weight: 700;
      color: var(--cream);
      line-height: 1.08;
      margin-bottom: 1rem;
    }

    .hero-title em {
      font-style: italic;
      color: var(--gold);
    }

    .hero-sub {
      font-size: 0.95rem;
      color: var(--sand);
      letter-spacing: 0.08em;
      margin-top: 0.5rem;
    }

    .scroll-hint {
      position: relative;
      z-index: 2;
      margin-top: 2.5rem;
      display: flex;
      flex-direction: column;
      align-items: center;
      gap: 0.4rem;
      color: var(--sand);
      font-size: 0.75rem;
      letter-spacing: 0.2em;
      text-transform: uppercase;
      animation: bob 2s ease-in-out infinite;
    }

    .scroll-hint::after {
      content: '';
      display: block;
      width: 1px;
      height: 40px;
      background: linear-gradient(to bottom, var(--sand), transparent);
    }

    /* ── STORY ── */
    .story {
      max-width: 680px;
      margin: 0 auto;
      padding: 5rem 2rem 6rem;
    }

    .chapter-marker {
      display: flex;
      align-items: center;
      gap: 1rem;
      margin-bottom: 3rem;
    }

    .chapter-marker::before,
    .chapter-marker::after {
      content: '';
      flex: 1;
      height: 1px;
      background: var(--sand);
    }

    .chapter-label {
      font-size: 0.7rem;
      letter-spacing: 0.3em;
      text-transform: uppercase;
      color: var(--bark);
      white-space: nowrap;
    }

    .story p {
      font-size: 1.08rem;
      line-height: 1.92;
      color: #3d2c1e;
      margin-bottom: 1.8rem;
      text-align: justify;
    }

    .story p:first-of-type::first-letter {
      font-family: 'Playfair Display', serif;
      font-size: 4.5rem;
      font-weight: 700;
      line-height: 0.75;
      float: left;
      margin-right: 0.12em;
      margin-top: 0.1em;
      color: var(--rust);
    }

    .story .highlight {
      background: linear-gradient(120deg, transparent 0%, rgba(201,168,76,0.18) 30%, rgba(201,168,76,0.18) 70%, transparent 100%);
      padding: 0 2px;
      border-radius: 2px;
      font-style: italic;
    }

    /* ── PULL QUOTE ── */
    .pullquote {
      border-left: 3px solid var(--gold);
      margin: 3rem 0;
      padding: 1.5rem 2rem;
      background: rgba(201,168,76,0.06);
      border-radius: 0 8px 8px 0;
    }

    .pullquote p {
      font-family: 'Playfair Display', serif;
      font-style: italic;
      font-size: 1.25rem !important;
      line-height: 1.65 !important;
      color: var(--bark) !important;
      margin: 0 !important;
      text-align: left !important;
    }

    /* ── FOOTER ── */
    .closing {
      text-align: center;
      padding: 4rem 2rem 6rem;
      background: var(--deep);
    }

    .closing-ornament {
      font-size: 1.5rem;
      color: var(--gold);
      letter-spacing: 0.5rem;
      margin-bottom: 1.5rem;
    }

    .closing-text {
      font-family: 'Playfair Display', serif;
      font-style: italic;
      font-size: 1.2rem;
      color: var(--sand);
      line-height: 1.8;
      max-width: 480px;
      margin: 0 auto;
    }

    .closing-sub {
      margin-top: 1.5rem;
      font-size: 0.78rem;
      letter-spacing: 0.25em;
      color: var(--bark);
      text-transform: uppercase;
    }

    /* ── ANIMATIONS ── */
    @keyframes fadeUp {
      from { opacity: 0; transform: translateY(30px); }
      to   { opacity: 1; transform: translateY(0); }
    }

    @keyframes bob {
      0%, 100% { transform: translateY(0); }
      50%       { transform: translateY(6px); }
    }

    /* Scroll reveal */
    .reveal {
      opacity: 0;
      transform: translateY(24px);
      transition: opacity 0.9s ease, transform 0.9s ease;
    }
    .reveal.visible {
      opacity: 1;
      transform: translateY(0);
    }

    @media (max-width: 600px) {
      .story p { font-size: 1rem; line-height: 1.85; }
      .pullquote p { font-size: 1.1rem !important; }
    }
  </style>
</head>
<body>

  <!-- HERO WITH PHOTO -->
  <section class="hero">
    <img class="hero-photo" src="/mnt/user-data/uploads/1000239692.jpg" alt="Sandal di atas pasir">
    <div class="hero-overlay"></div>
    <div class="hero-content">
      <p class="hero-tag">Sebuah perjalanan</p>
      <h1 class="hero-title">Dari <em>Kaus Kaki</em></h1>
      <p class="hero-sub">Langkah kecil menuju keistiqomahan</p>
    </div>
    <div class="scroll-hint">Baca ceritanya</div>
  </section>

  <!-- STORY BODY -->
  <article class="story">
    <div class="chapter-marker reveal">
      <span class="chapter-label">Awal mula</span>
    </div>

    <p class="reveal">Mari kita mulai dari hal yang paling sederhana: kaus kaki.</p>

    <p class="reveal">Dulu, kaus kaki itu bagiku cuma sebatas atribut sekolah aja. Aku bahkan kadang sengaja pakai yang panjangnya cuma semata kaki, atau malah di bawahnya. Sampai di pertengahan tahun 2023, aku ketemu sama santriwati pondokan punya sepupu. Penampilannya tertutup rapat: kaus kaki, sarung tangan hitam, kerudung panjang yang sampai mata kaki, hingga cadar. Reaksi pertamaku di dalam hati saat itu adalah, <span class="highlight">"Apa mereka nggak gerah, ya?"</span> Bayangkan saja, aku yang saat itu cuma memakai kerudung paris dan rok biasa saja rasanya sudah tidak betah dan ingin terus menempel di depan kipas angin.</p>

    <p class="reveal">Tapi siapa sangka, perubahan itu ternyata datang pelan-pelan.</p>

    <div class="pullquote reveal">
      <p>"Awalnya, aku mulai mencoba memakai kaus kaki. Itu pun cuma saat berangkat kajian."</p>
    </div>

    <p class="reveal">Jujur saja, rasanya tidak nyaman dan panas. Namun, karena semakin sering ikut kajian, aku akhirnya paham bahwa kaki perempuan itu adalah aurat. Sejak kesadaran itu muncul, aku memaksakan diri. Tiap kali keluar rumah dan bertemu yang bukan mahram, kaus kaki jadi hal yang wajib kupakai.</p>

    <p class="reveal">Dari kaus kaki, langkahku merambat ke gamis. Dulu, isi lemariku paling hanya punya satu atau dua potong gamis, dan itu pun jarang sekali disentuh. Sama seperti kaus kaki, awalnya aku pakai gamis cuma untuk ke tempat kajian. Rasanya? Sangat ribet. Susah bergerak, ujungnya sering nyangkut, dan pastinya gerah.</p>

    <p class="reveal">Tapi, seiring berjalannya waktu, rasa tidak nyaman itu justru berubah. Aku mulai merasa jauh lebih percaya diri saat mengenakannya. Sampai akhirnya, di akhir 2023, aku memantapkan hati. Mau keluar rumah ataupun sekadar diam di rumah, pakaian utamaku sekarang adalah gamis atau abaya.</p>

    <div class="chapter-marker reveal" style="margin-top:3rem;">
      <span class="chapter-label">Tantangan baru</span>
    </div>

    <p class="reveal">Tantangan selanjutnya ada di kerudung panjang. Lagi-lagi, permulaannya dari kajian. Awal memakai kerudung panjang, rasanya ribet sekali. Ada perasaan kurang percaya diri karena merasa jadi "jelek" dan sering dipanggil ibu-ibu. Tapi aku memilih untuk tidak baper. Alhamdulillah, dari ilmu yang kudapat di kajian, aku jadi tahu tentang Surah An-Nur ayat 31 yang memerintahkan kita untuk menjulurkan kerudung hingga menutup dada.</p>

    <p class="reveal">Aku paham betul perspektif orang-orang yang baru pertama kali melihat perempuan berkerudung panjang. Mikirnya pasti gerah, nggak nyaman, ribet, kayak ibu-ibu, nggak stylish, dan sebagainya. Kenapa aku paham? Karena aku pun dulu begitu! Tapi pada akhirnya, ini semua bukan tentang penampilan di mata manusia, setidaknya kita berusaha mengikuti Al-Qur'an dan sunnah.</p>

    <div class="chapter-marker reveal" style="margin-top:3rem;">
      <span class="chapter-label">2024 & seterusnya</span>
    </div>

    <p class="reveal">Perjalanan ini mencapai titik barunya di awal tahun 2024. Alhamdulillah, aku diberi kesempatan untuk bisa belajar bersama santri meski tidak lama dan harus disambi dengan bekerja. Di momen itulah, aku semakin memantapkan diri. Mulai dari rutin memakai kaus kaki, gamis, handsock, kerudung panjang, hingga akhirnya sampai di titik keberanian untuk memakai cadar.</p>

    <p class="reveal">Tapi jujur, langkah terakhir ini bukan tanpa dilema. Saat mulai mantap bercadar, ada satu hal berat yang lumayan mengganjal dan bikin aku maju-mundur: media sosial. Kebayang kan, betapa banyaknya foto-fotoku yang sudah telanjur kuunggah di Facebook selama bertahun-tahun? Rasanya sempat sayang, tapi aku sadar ini adalah konsekuensi dari pilihanku. Akhirnya, aku mengambil keputusan besar. Aku menghapus semua fotoku di sana dan memutuskan untuk mengubah semua sosial mediaku menjadi akun tanpa terpampang wajahku sama sekali. <span class="highlight">Rasanya seperti merelakan sebagian memori masa lalu, demi menjaga komitmen baruku.</span></p>

    <div class="pullquote reveal">
      <p>"Mungkin banyak yang melihatku sekarang dan berpikir perubahanku ini terjadi begitu saja secara instan. Padahal, sama sekali tidak."</p>
    </div>

    <p class="reveal">Semuanya berproses pelan-pelan, menundukkan ego selangkah demi selangkah. Dan dari perjalananku ini, aku yakin, kalian pun pasti bisa pelan-pelan istiqomah untuk menutup aurat.</p>
  </article>

  <!-- CLOSING -->
  <footer class="closing">
    <div class="closing-ornament">✦ ✦ ✦</div>
    <p class="closing-text">
      "Semuanya berproses pelan-pelan, menundukkan ego selangkah demi selangkah."
    </p>
    <p class="closing-sub">Semoga bermanfaat &amp; menginspirasi</p>
  </footer>

  <script>
    const reveals = document.querySelectorAll('.reveal');
    const observer = new IntersectionObserver((entries) => {
      entries.forEach((entry, i) => {
        if (entry.isIntersecting) {
          setTimeout(() => entry.target.classList.add('visible'), i * 80);
          observer.unobserve(entry.target);
        }
      });
    }, { threshold: 0.12 });
    reveals.forEach(el => observer.observe(el));
  </script>
</body>
</html>
