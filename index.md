             HTML

<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Assignment 9.2 — Responsive Typography & Images</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>

  <!-- Step 5: Content container with suitable max-width -->
  <main class="article-container">

    <!-- Step 1 & 2: Article Header with Scalable Headings -->
    <header class="article-header">
      <span class="category-tag">Design Systems</span>
      <h1 class="article-title">The Principles of Fluid Typography & Adaptive Imagery</h1>
      <p class="article-deck">
        Moving beyond rigid breakpoints toward continuous, proportional reading experiences across any viewport.
      </p>
      <div class="article-byline">
        <span>By <strong>Elena Vance</strong></span>
        <span>•</span>
        <time datetime="2026-11-06">November 6, 2026</time>
        <span>•</span>
        <span>6 min read</span>
      </div>
    </header>

    <!-- Step 2 & 4: Hero Image (Adaptive & Constrained) -->
    <figure class="article-figure">
      <img 
        src="https://images.unsplash.com/photo-1499750310107-5fef28a66643?w=1200&auto=format&fit=crop&q=80" 
        alt="Laptop, notebook, and coffee on a minimalist desk"
      >
      <figcaption>Modern responsive design relies on fluid units rather than fixed pixel dimensions.</figcaption>
    </figure>

    <!-- Step 2 & 6: Article Body with Controlled Line Length -->
    <article class="article-content">
      <p class="lead-paragraph">
        Designing for the modern web requires abandoning the assumption of fixed display boundaries. When typography is locked to rigid pixel sizes, text either overflows or strains legibility on small handheld screens, while appearing tiny on high-density ultra-wide desktop monitors.
      </p>

      <h2>The Fluid Power of <code>clamp()</code></h2>
      <p>
        CSS <code>clamp(min, preferred, max)</code> allows font sizes to interpolate fluidly between a floor and ceiling value relative to the user's viewport width. This eliminates jagged jumps between media queries and preserves typographic hierarchy across mobile, tablet, and widescreen environments.
      </p>

      <blockquote>
        "Great typography does not merely resize; it adapts its rhythm, measure, and proportion to the constraints of the reader's screen."
      </blockquote>

      <h2>Managing Image Aspect Ratios and Constraints</h2>
      <p>
        Unconstrained raster assets are one of the most common causes of accidental horizontal scrolling on mobile viewports. By declaring <code>max-width: 100%</code> and <code>height: auto</code>, embedded images shrink harmoniously to fit their parent wrapper without stretching or distorting their native aspect ratio.
      </p>

      <!-- Step 2 & 4: Secondary Inline Image -->
      <figure class="article-figure">
        <img 
          src="https://images.unsplash.com/photo-1488190211105-8b0e65b80b4e?w=1000&auto=format&fit=crop&q=80" 
          alt="Hands sketching wireframes in a journal next to a computer"
        >
        <figcaption>Iterating typographic measures (45–75 characters per line) optimizes reader comfort.</figcaption>
      </figure>

      <h2>Optimal Line Length and Reading Measure</h2>
      <p>
        The human eye experiences fatigue when forced to scan excessively wide lines of text. By constraining prose containers to between 65 and 75 characters using the <code>ch</code> unit, reading rhythm remains consistent regardless of how large the monitor is.
      </p>
    </article>

  </main>

</body>
</html>


                  CSS


/* --- Global Reset & Box Sizing --- */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

:root {
  --text-main: #1e293b;
  --text-muted: #64748b;
  --text-lead: #334155;
  --accent: #2563eb;
  --bg-page: #f8fafc;
  --bg-surface: #ffffff;
  --border: #e2e8f0;
}

body {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", sans-serif;
  background-color: var(--bg-page);
  color: var(--text-main);
  /* Step 6: Comfortable baseline line height */
  line-height: 1.7;
  padding: clamp(1.25rem, 4vw, 3.5rem) 1.25rem;
  /* Step 7: Prevent horizontal layout blowouts */
  overflow-x: hidden;
}

/* ================= STEP 5 & 6: CONTAINER & MEASURE ================= */
.article-container {
  /* Step 5: Suitable max-width container centered on page */
  max-width: 760px;
  margin: 0 auto;
  background-color: var(--bg-surface);
  border: 1px solid var(--border);
  border-radius: 12px;
  padding: clamp(1.5rem, 5vw, 3.5rem);
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.04);
}

/* ================= STEP 3: FLUID TYPOGRAPHY ================= */
.category-tag {
  display: inline-block;
  font-size: 0.8rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  color: var(--accent);
  margin-bottom: 0.75rem;
}

/* Fluid H1: Scales from 1.85rem (29.6px) on mobile to 2.85rem (45.6px) on desktop */
.article-title {
  font-size: clamp(1.85rem, 4vw + 1rem, 2.85rem);
  font-weight: 800;
  line-height: 1.15;
  letter-spacing: -0.025em;
  color: #0f172a;
  margin-bottom: 1rem;
  /* Step 7: Word break guard for small screens */
  overflow-wrap: break-word;
}

/* Fluid Deck / Subtitle */
.article-deck {
  font-size: clamp(1.05rem, 1.5vw + 0.5rem, 1.3rem);
  color: var(--text-muted);
  line-height: 1.5;
  margin-bottom: 1.5rem;
}

.article-byline {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  font-size: 0.875rem;
  color: var(--text-muted);
  padding-bottom: 1.75rem;
  border-bottom: 1px solid var(--border);
  margin-bottom: 2rem;
}

/* Fluid Section Headings */
.article-content h2 {
  font-size: clamp(1.35rem, 2vw + 0.6rem, 1.8rem);
  font-weight: 700;
  color: #0f172a;
  margin-top: 2.25rem;
  margin-bottom: 0.85rem;
  letter-spacing: -0.015em;
  overflow-wrap: break-word;
}

/* Step 6: Controlled Line Length & Spacing */
.article-content p {
  /* Constrain line length to ~65-75 characters for comfortable reading */
  max-width: 68ch;
  font-size: clamp(1rem, 0.25vw + 0.95rem, 1.125rem);
  color: var(--text-lead);
  margin-bottom: 1.4rem;
}

.lead-paragraph {
  font-size: clamp(1.1rem, 0.5vw + 1rem, 1.25rem) !important;
  font-weight: 400;
  color: #0f172a !important;
}

.article-content code {
  font-family: SFMono-Regular, Consolas, Monaco, monospace;
  background-color: #f1f5f9;
  color: var(--accent);
  padding: 0.15rem 0.35rem;
  border-radius: 4px;
  font-size: 0.9em;
}

blockquote {
  border-left: 4px solid var(--accent);
  padding: 0.75rem 0 0.75rem 1.25rem;
  margin: 1.75rem 0;
  font-style: italic;
  font-size: clamp(1.05rem, 1.2vw + 0.6rem, 1.25rem);
  color: #334155;
  background-color: #f8fafc;
  border-radius: 0 8px 8px 0;
}

/* ================= STEP 4 & 7: RESPONSIVE IMAGES ================= */
.article-figure {
  margin: 2rem 0;
  width: 100%;
}

.article-figure img {
  /* Step 4: Prevents image from overflowing container while maintaining natural aspect ratio */
  max-width: 100%;
  height: auto;
  display: block;
  border-radius: 8px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.06);
}

.article-figure figcaption {
  font-size: 0.85rem;
  color: var(--text-muted);
  margin-top: 0.6rem;
  text-align: center;
  line-height: 1.4;
}

/* Mobile-specific fine tuning */
@media (max-width: 480px) {
  .article-container {
    padding: 1.25rem 1rem;
    border: none;
    background: transparent;
    box-shadow: none;
  }
}