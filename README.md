<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>The Space Between Goodbye — Roy & Aleena</title>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,300;0,400;0,600;1,300;1,400&family=Cinzel:wght@400;600&family=EB+Garamond:ital,wght@0,400;1,400&display=swap" rel="stylesheet">
<style>
  :root {
    --cream: #f5efe6;
    --parchment: #ede0cc;
    --ink: #1a1410;
    --sepia: #7a5c3a;
    --rust: #8b3a2a;
    --gold: #c9a84c;
    --shadow-ink: rgba(26,20,16,0.18);
  }

  *, *::before, *::after { box-sizing: border-box; margin: 0; padding: 0; }

  html { scroll-behavior: smooth; }

  body {
    background-color: #1a1410;
    font-family: 'EB Garamond', Georgia, serif;
    color: var(--ink);
    min-height: 100vh;
  }

  /* ── COVER ── */
  .cover {
    position: relative;
    height: 100vh;
    min-height: 600px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    background: #1a1410;
  }

  .cover-bg {
    position: absolute; inset: 0;
    background: url('https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=1600&q=80') center/cover no-repeat;
    opacity: 0.18;
    filter: sepia(0.6);
  }

  .cover-overlay {
    position: absolute; inset: 0;
    background: radial-gradient(ellipse at center, transparent 30%, #1a1410 90%);
  }

  .cover-content {
    position: relative;
    text-align: center;
    padding: 2rem;
    animation: fadeInUp 1.8s ease both;
  }

  .cover-eyebrow {
    font-family: 'Cinzel', serif;
    font-size: 0.75rem;
    letter-spacing: 0.35em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 2rem;
    opacity: 0.85;
  }

  .cover-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(3rem, 8vw, 6.5rem);
    font-weight: 300;
    font-style: italic;
    color: var(--cream);
    line-height: 1.05;
    text-shadow: 0 4px 40px rgba(0,0,0,0.6);
    margin-bottom: 1.5rem;
  }

  .cover-subtitle {
    font-family: 'Cinzel', serif;
    font-size: 1rem;
    letter-spacing: 0.2em;
    color: var(--gold);
    margin-bottom: 3rem;
  }

  .cover-names {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.5rem;
    font-style: italic;
    color: var(--parchment);
    opacity: 0.75;
  }

  .scroll-hint {
    position: absolute;
    bottom: 2.5rem;
    left: 50%;
    transform: translateX(-50%);
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0.5rem;
    color: var(--gold);
    opacity: 0.55;
    animation: pulse 2.5s ease-in-out infinite;
  }
  .scroll-hint span { font-family: 'Cinzel', serif; font-size: 0.65rem; letter-spacing: 0.25em; }
  .scroll-hint::after {
    content: '';
    display: block;
    width: 1px;
    height: 40px;
    background: var(--gold);
    margin-top: 0.3rem;
  }

  /* ── PAGE LAYOUT ── */
  .story-wrapper {
    background: var(--cream);
    position: relative;
  }

  .page-texture {
    position: fixed; inset: 0; pointer-events: none; z-index: 0;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='400' height='400'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.75' numOctaves='4' stitchTiles='stitch'/%3E%3CfeColorMatrix type='saturate' values='0'/%3E%3C/filter%3E%3Crect width='400' height='400' filter='url(%23n)' opacity='0.04'/%3E%3C/svg%3E");
    opacity: 0.5;
  }

  /* ── PART SECTION ── */
  .part {
    max-width: 820px;
    margin: 0 auto;
    padding: 5rem 2.5rem;
    position: relative;
    z-index: 1;
    border-bottom: 1px solid rgba(122,92,58,0.2);
    animation: fadeInUp 0.9s ease both;
  }
  .part:last-child { border-bottom: none; }

  .part-label {
    font-family: 'Cinzel', serif;
    font-size: 0.65rem;
    letter-spacing: 0.4em;
    color: var(--gold);
    text-transform: uppercase;
    margin-bottom: 0.6rem;
    display: block;
  }

  .part-title {
    font-family: 'Cormorant Garamond', serif;
    font-size: clamp(1.8rem, 4vw, 2.8rem);
    font-weight: 600;
    color: var(--rust);
    line-height: 1.15;
    margin-bottom: 2.5rem;
    position: relative;
    padding-bottom: 1.2rem;
  }
  .part-title::after {
    content: '';
    position: absolute;
    bottom: 0; left: 0;
    width: 60px; height: 2px;
    background: linear-gradient(90deg, var(--gold), transparent);
  }

  .part-body {
    font-size: 1.18rem;
    line-height: 1.9;
    color: #2a1f15;
    font-weight: 400;
  }
  .part-body p { margin-bottom: 1.4em; }
  .part-body em { font-style: italic; color: var(--sepia); }

  /* ── PHOTO BLOCKS ── */
  .photo-grid {
    display: grid;
    gap: 1rem;
    margin: 2.5rem 0;
  }
  .photo-grid.two   { grid-template-columns: 1fr 1fr; }
  .photo-grid.three { grid-template-columns: 2fr 1fr; grid-template-rows: 1fr 1fr; }
  .photo-grid.single { grid-template-columns: 1fr; }

  .photo-frame {
    position: relative;
    overflow: hidden;
    border-radius: 2px;
    box-shadow: 0 6px 30px var(--shadow-ink);
  }
  .photo-frame.tall { grid-row: 1 / 3; }

  .photo-frame img {
    width: 100%; height: 100%;
    object-fit: cover;
    display: block;
    filter: sepia(0.15) contrast(1.05);
    transition: transform 0.6s ease, filter 0.6s ease;
  }
  .photo-frame:hover img {
    transform: scale(1.04);
    filter: sepia(0) contrast(1.1);
  }

  .photo-frame .caption {
    position: absolute;
    bottom: 0; left: 0; right: 0;
    background: linear-gradient(transparent, rgba(26,20,16,0.75));
    color: var(--parchment);
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: 0.82rem;
    padding: 1.5rem 1rem 0.7rem;
    letter-spacing: 0.03em;
    opacity: 0;
    transition: opacity 0.4s ease;
  }
  .photo-frame:hover .caption { opacity: 1; }

  /* Heights */
  .photo-grid.two   .photo-frame { height: 280px; }
  .photo-grid.three .photo-frame.tall { height: 320px; }
  .photo-grid.three .photo-frame:not(.tall) { height: 150px; }
  .photo-grid.single .photo-frame { height: 380px; }

  /* ── PULL QUOTE ── */
  .pull-quote {
    margin: 2.5rem 0;
    padding: 1.5rem 2rem 1.5rem 2.5rem;
    border-left: 3px solid var(--gold);
    background: rgba(201,168,76,0.07);
  }
  .pull-quote p {
    font-family: 'Cormorant Garamond', serif;
    font-size: 1.4rem;
    font-style: italic;
    font-weight: 300;
    color: var(--sepia);
    line-height: 1.6;
    margin: 0;
  }

  /* ── ORNAMENT ── */
  .ornament {
    text-align: center;
    color: var(--gold);
    font-size: 1.4rem;
    letter-spacing: 0.5em;
    margin: 2.5rem 0;
    opacity: 0.6;
  }

  /* ── EPILOGUE ── */
  .epilogue {
    background: #1a1410;
    color: var(--cream);
    padding: 6rem 2.5rem;
    text-align: center;
    position: relative;
    overflow: hidden;
  }
  .epilogue::before {
    content: '';
    position: absolute; inset: 0;
    background: url('https://images.unsplash.com/photo-1476900164809-ff19b8ae5968?w=1200&q=60') center/cover no-repeat;
    opacity: 0.08;
    filter: sepia(0.5);
  }
  .epilogue-inner {
    position: relative;
    max-width: 600px;
    margin: 0 auto;
  }
  .epilogue .part-label { color: var(--gold); margin-bottom: 1rem; }
  .epilogue .part-title { color: var(--parchment); }
  .epilogue .part-title::after { background: linear-gradient(90deg, var(--gold), transparent); left: 50%; transform: translateX(-50%); }
  .epilogue .part-body { color: #c8b89a; }
  .epilogue .pull-quote { border-left-color: var(--gold); background: rgba(255,255,255,0.04); }
  .epilogue .pull-quote p { color: var(--gold); }

  /* ── THE END ── */
  .the-end {
    background: #1a1410;
    text-align: center;
    padding: 4rem 2rem 5rem;
  }
  .the-end p {
    font-family: 'Cormorant Garamond', serif;
    font-style: italic;
    font-size: 1.1rem;
    color: var(--gold);
    letter-spacing: 0.15em;
    opacity: 0.7;
  }

  /* ── ANIMATIONS ── */
  @keyframes fadeInUp {
    from { opacity: 0; transform: translateY(24px); }
    to   { opacity: 1; transform: translateY(0); }
  }
  @keyframes pulse {
    0%, 100% { opacity: 0.4; }
    50%       { opacity: 0.9; }
  }

  /* ── RESPONSIVE ── */
  @media (max-width: 600px) {
    .photo-grid.two   { grid-template-columns: 1fr; }
    .photo-grid.three { grid-template-columns: 1fr; grid-template-rows: auto; }
    .photo-grid.three .photo-frame.tall { grid-row: auto; height: 220px; }
    .photo-grid.three .photo-frame:not(.tall) { height: 180px; }
    .photo-grid.two   .photo-frame { height: 200px; }
    .photo-grid.single .photo-frame { height: 240px; }
    .part { padding: 3rem 1.2rem; }
  }
</style>
</head>
<body>

<!-- ══════════════════════════════════════ COVER -->
<section class="cover">
  <div class="cover-bg"></div>
  <div class="cover-overlay"></div>
  <div class="cover-content">
    <p class="cover-eyebrow">A Love Story</p>
    <h1 class="cover-title">The Space Between<br>Goodbye</h1>
    <p class="cover-subtitle">— Roy &amp; Aleena —</p>
    <p class="cover-names">A story of love, distance, and the grace of letting go</p>
  </div>
  <div class="scroll-hint"><span>Begin</span></div>
</section>

<!-- ══════════════════════════════════════ STORY PAGES -->
<div class="story-wrapper">

  <!-- PART ONE -->
  <section class="part">
    <span class="part-label">Part One</span>
    <h2 class="part-title">The Beginning of Everything</h2>

    <div class="photo-grid two">
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1481627834876-b7833e8f5570?w=800&q=80" alt="Library terrace, autumn">
        <div class="caption">October — the library terrace</div>
      </div>
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=800&q=80" alt="Autumn leaves falling">
        <div class="caption">Leaves doing their slow, reluctant falling</div>
      </div>
    </div>

    <div class="part-body">
      <p>The first time Roy saw Aleena, she was standing at the edge of the library terrace, holding a cup of tea that had long gone cold, reading a paperback whose spine had been broken and re-broken a dozen times. It was October. The leaves in the courtyard below were doing their slow, reluctant falling, and the evening light was the color of amber.</p>
      <p>He didn't speak to her that day. He only watched, the way you watch something you instinctively know is not meant to last — a sunset, a candle flame, a bird resting on a wire before it decides to leave.</p>
      <p>But the next day, she was there again. And the day after that.</p>
      <p>It was she who spoke first.</p>
      <p>"You've been staring at me for three days," she said, without looking up from her book.</p>
      <p>Roy felt heat rush to his face. "I wasn't—"</p>
      <p>"It's fine." She finally looked up, and her eyes were dark and calm, like still water over deep ground. "I just thought you might want to say something, if you had something to say."</p>
      <p>He sat down across from her and said, "I'm Roy."</p>
      <p>She smiled — not a wide smile, but a careful one, the kind you give to something fragile. "Aleena."</p>
      <p>And that was how it started. Simply. Quietly. The way the most devastating things always do.</p>
    </div>
  </section>

  <!-- PART TWO -->
  <section class="part">
    <span class="part-label">Part Two</span>
    <h2 class="part-title">The Months That Felt Like Wings</h2>

    <div class="photo-grid three">
      <div class="photo-frame tall">
        <img src="https://images.unsplash.com/photo-1516589178581-6cd7833ae3b2?w=800&q=80" alt="Couple in love autumn">
        <div class="caption">Eight months — the most extraordinary ordinary love</div>
      </div>
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1544716278-ca5e3f4abd8c?w=600&q=80" alt="Love letters and tea">
        <div class="caption">Letters, even in the same city</div>
      </div>
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1524995997946-a1c2e315a42f?w=600&q=80" alt="Old bookshop narrow street">
        <div class="caption">Sunday wanderings through old bookshops</div>
      </div>
    </div>

    <div class="part-body">
      <p>They fell into each other the way rivers fall into the sea — naturally, completely, as if there had never been any other direction to go.</p>
      <p>Roy learned that Aleena laughed with her whole body, tilting backward, covering her mouth with both hands as if laughter were something to be contained. He learned that she cried at documentary films but never at fiction, because, she said, <em>real suffering deserves real tears.</em> He learned that she kept a small notebook in every bag she owned, filling them with sentences that struck her, half-finished thoughts, words she found beautiful for no reason she could explain.</p>
      <p>Aleena learned that Roy was afraid of silence — not because it was empty, but because it was full of things he didn't know how to say. She learned that he made tea too strong and coffee too weak, and that he remembered the birthday of every person he had ever loved.</p>
    </div>

    <div class="pull-quote">
      <p>"They wrote letters to each other even though they lived in the same city, because some things, Aleena said, deserve the weight of paper."</p>
    </div>

    <div class="part-body">
      <p>They spent Sundays wandering through old bookshops and narrow streets. They argued about small things — directions, film endings, the right way to peel a mango — and made up quietly, without ceremony, with a cup of tea placed gently on a desk, or a hand resting briefly on a shoulder.</p>
      <p>It was the most ordinary love. It was the most extraordinary love.</p>
      <p>For eight months, Roy believed in forever.</p>
    </div>
  </section>

  <!-- PART THREE -->
  <section class="part">
    <span class="part-label">Part Three</span>
    <h2 class="part-title">The Letter</h2>

    <div class="photo-grid single">
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1586339949916-3e9457bef6d3?w=1200&q=80" alt="Envelope letter foreign stamps">
        <div class="caption">A white envelope with foreign stamps — arriving on a Tuesday in June</div>
      </div>
    </div>

    <div class="part-body">
      <p>It arrived on a Tuesday in June, in a white envelope with foreign stamps.</p>
      <p>Aleena had applied for a fellowship — a two-year research position in Edinburgh — months before she and Roy had become <em>Roy and Aleena.</em> She had applied because her dream had always been to study literature abroad, to sit in those old stone libraries and read and write and become the version of herself she had been building toward her whole life.</p>
      <p>She had applied not expecting to get it.</p>
      <p>She got it.</p>
      <p>Roy read the letter over her shoulder. He felt the words land in his chest one by one, each one a small, clean wound.</p>
      <p><em>Congratulations. Two years. Begin in August.</em></p>
      <p>August was six weeks away.</p>
      <p>"Roy—" she began.</p>
      <p>"This is wonderful," he said.</p>
    </div>

    <div class="pull-quote">
      <p>"And he meant it. That was the cruelest part — he truly meant it."</p>
    </div>

    <div class="part-body">
      <p>He knew what this meant to her. He could not ask her to let go of herself for him. And she could not ask him to follow — not then, not when his mother was unwell, not when he had just taken the job he had worked three years to earn, not when his whole life was rooted here like a tree that had only just begun to grow.</p>
      <p>They sat in silence for a long time — Roy's kind of silence, the kind that is heavy with everything unsaid.</p>
      <p>Finally, Aleena put her hand over his. "I don't know what to do," she whispered.</p>
      <p>"You go," he said quietly. "You go, Aleena."</p>
    </div>
  </section>

  <!-- PART FOUR -->
  <section class="part">
    <span class="part-label">Part Four</span>
    <h2 class="part-title">The Weeks Before</h2>

    <div class="photo-grid two">
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1529619768328-e37af76c6fe5?w=800&q=80" alt="Couple farewell embrace sad">
        <div class="caption">Six weeks of memorizing each other</div>
      </div>
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1471341971476-ae15af5dd057?w=800&q=80" alt="City rooftop night view">
        <div class="caption">The rooftop — where Roy counted city lights like prayers</div>
      </div>
    </div>

    <div class="part-body">
      <p>Those six weeks were the most bittersweet of Roy's life.</p>
      <p>They spent them trying to memorize each other. Aleena took photographs of the two of them in all the places they had been — the library terrace, the bookshop on Mirza Lane, the rooftop where Roy counted city lights. Roy read all the books she loved that he hadn't yet read, as if understanding her words would keep some part of her close.</p>
      <p>They talked about the future carefully, the way you step around something broken on the floor. They talked about visits, about calls, about letters — yes, still letters, always letters. They talked about how two years was not forever. They talked about waiting.</p>
      <p>But beneath all of it, in the quiet places, they both understood something they could not bring themselves to say: that two years is long enough for people to change. Long enough for lives to rearrange themselves around new shapes. Long enough for love, even the truest kind, to shift — not die, but shift — into something softer, more distant, more like memory than presence.</p>
      <p>They did not say these things. They held hands instead.</p>
    </div>

    <div class="pull-quote">
      <p>"I love you. Go be everything you're supposed to be."</p>
    </div>

    <div class="part-body">
      <p>The last night before her flight, they sat on the rooftop together. Aleena brought tea. Roy counted the lights. She leaned her head against his shoulder and they stayed like that for a very long time, not speaking, because there was nothing left to say that wasn't too large for words.</p>
    </div>
  </section>

  <!-- PART FIVE -->
  <section class="part">
    <span class="part-label">Part Five</span>
    <h2 class="part-title">After</h2>

    <div class="photo-grid three">
      <div class="photo-frame tall">
        <img src="https://images.unsplash.com/photo-1443188631128-a1b6b1c5c207?w=800&q=80" alt="Man alone window rain sad">
        <div class="caption">Counting lights that seemed fewer now, when counted alone</div>
      </div>
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1455390582262-044cdead277a?w=600&q=80" alt="Writing letters pen paper">
        <div class="caption">She sent letters. Roy kept every one.</div>
      </div>
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1519389950473-47ba0277781c?w=600&q=80" alt="Distance long call phone">
        <div class="caption">Long calls that stretched past midnight</div>
      </div>
    </div>

    <div class="part-body">
      <p>She sent letters. Roy kept every one.</p>
      <p>For the first six months, they spoke often — long calls that stretched past midnight, filling the silence with small stories, the texture of their separate days. Aleena described the cold, the grey sky, the smell of old books in ancient reading rooms. Roy told her about his mother's slowly improving health, about the city, about the rooftop where the lights seemed fewer now, somehow, when counted alone.</p>
      <p>Gradually — not suddenly, not dramatically, but the way seasons change — the calls grew shorter. Not from indifference. Never from indifference. But because their lives were filling in around them, the way soil fills in around roots, and it became harder to translate one world into the language of another.</p>
      <p>Aleena met colleagues who became friends. She began writing again — really writing, the kind she had always dreamed of. She sent Roy the pages, and he read them with a pride that ached.</p>
    </div>

    <div class="pull-quote">
      <p>"Two people can love each other completely and still find that love is not enough to solve the mathematics of distance, timing, and the lives that surround them. This is not a failure. It is simply the saddest truth that love teaches."</p>
    </div>
  </section>

  <!-- PART SIX -->
  <section class="part">
    <span class="part-label">Part Six</span>
    <h2 class="part-title">The Last Letter</h2>

    <div class="photo-grid two">
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1554118811-1e0d58224f24?w=800&q=80" alt="Coffee shop two people reunion">
        <div class="caption">Coffee, three hours, and a love that had changed shape</div>
      </div>
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1474552226712-ac0f0961a954?w=800&q=80" alt="Woman walking away amber light street">
        <div class="caption">She stepped back — and walked away into amber light</div>
      </div>
    </div>

    <div class="part-body">
      <p>Two years passed. Aleena came home.</p>
      <p>She was the same — still Aleena, still the laugh held behind both hands, still the notebooks and the careful smile. But she was also different in the way that people who have lived fully become different: settled into themselves, grown into the shape that had always been waiting for them.</p>
      <p>They met for coffee at a small place near the old library. They hugged at the door, and it felt familiar and distant at once, like a song you loved once and have not heard in a long time.</p>
      <p>They talked for three hours. They laughed. They talked about the past as if it belonged to two younger, sweeter people they were both fond of. They talked about the future — her work, his work, the separate paths that had grown solid and real beneath their feet.</p>
      <p>When they finally stood outside to part, the evening light was the color of amber, the same amber as that October day, long ago, when everything began.</p>
      <p>"Roy," Aleena said softly.</p>
      <p>"I know," he said.</p>
      <p>She nodded. Her eyes were bright, not with tears exactly, but with the emotion that lives just beyond tears — the kind that has no name.</p>
      <p>She hugged him once more, tightly, and then she stepped back.</p>
      <p>He watched her walk away down the street, and he did not call after her. Because some loves are not meant to be held. Some loves are meant to open you — to teach you tenderness, and courage, and the terrifying grace of letting go — and then, gently, to leave you more whole than they found you.</p>
      <p>Roy stood on the pavement until she turned the corner and disappeared.</p>
      <p>Then he put his hands in his pockets, looked up at the pale evening sky, and walked home.</p>
    </div>
  </section>

</div><!-- /story-wrapper -->

<!-- ══════════════════════════════════════ EPILOGUE -->
<section class="epilogue">
  <div class="epilogue-inner">
    <span class="part-label">Epilogue</span>
    <h2 class="part-title" style="text-align:center;">What Remains</h2>

    <div class="photo-grid single" style="margin-bottom:2.5rem;">
      <div class="photo-frame">
        <img src="https://images.unsplash.com/photo-1476900164809-ff19b8ae5968?w=1200&q=80" alt="Man rooftop night city lights alone peaceful">
        <div class="caption">The rooftop. The lights. The gratitude.</div>
      </div>
    </div>

    <div class="part-body" style="color:#c8b89a; font-size:1.18rem; line-height:1.9;">
      <p>He still made tea too strong.</p>
      <p>He still went to the rooftop sometimes, and counted the lights.</p>
      <p>And on quiet evenings, when the city settled into its particular kind of softness, he would take out a letter — one of her letters, any one of them — and read a line or two. Not from sadness. From gratitude.</p>
    </div>

    <div class="pull-quote">
      <p>"Because to have loved Aleena, even briefly, even incompletely, even with all the distance and the ache and the goodbye on a pavement lit by amber light — had been one of the truest things in his life."</p>
    </div>

    <div class="part-body" style="color:#c8b89a; font-size:1.18rem; line-height:1.9; text-align:center; margin-top:2rem;">
      <p>And that, Roy had learned, was enough.</p>
      <p>It had to be enough.</p>
      <p><em>It was.</em></p>
    </div>
  </div>
</section>

<!-- ══════════════════════════════════════ THE END -->
<div class="the-end">
  <p>✦ &nbsp; The End &nbsp; ✦</p>
</div>

</body>
</html>
