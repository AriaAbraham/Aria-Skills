---
name: album-rater
description: Rate and review a music album using a detailed 6-category weighted scoring system on a 10-point scale. Use this skill whenever the user asks to rate, review, score, or evaluate an album — even if they just say "rate this album", "what would you give X album", "how good is [album]", "review this album for me", or anything implying they want a score or critique of a music release. Always triggers for album evaluation requests, even casual ones.
---

# Album Rater Skill

Rate a music album across 6 weighted categories, producing a final score out of 10 and an interactive visual display.

## Scoring Categories & Weights

Use this exact weighted breakdown (totals 100%):

| # | Category | Weight |
|---|----------|--------|
| 1 | Production / Sound Quality | 25% |
| 2 | Lyrics / Songwriting | 22% |
| 3 | Cohesion / Flow | 18% |
| 4 | Emotional Impact | 15% |
| 5 | Instrumentation / Musicianship | 12% |
| 6 | Vocal Performance | 8% |

Each category is scored **1–10** (decimals allowed, e.g. 7.5).

**Final Score** = weighted average of all 6 categories, rounded to 1 decimal place.

## Scoring Rubric

**1–3 (Poor):** Major flaws, detracts from the listening experience  
**4–5 (Below Average):** Noticeable weaknesses, falls short of expectations  
**6–7 (Good):** Solid, enjoyable, meets the standard for the genre  
**8–9 (Excellent):** Standout quality, memorable, above average  
**10 (Masterpiece):** Near-flawless, genre-defining, timeless

## Workflow

1. **Research the album** — Use web search to gather info on the album: artist, release year, genre, tracklist, critical reception, production notes, notable lyrics/themes. Do this before scoring.
2. **Score each category** — Apply the rubric thoughtfully. Be specific and genre-aware (e.g., instrumental albums get N/A for Vocal Performance → redistribute that 8% to Production).
3. **Write brief justifications** — 1–2 sentences per category explaining the score.
4. **Calculate the weighted final score.**
5. **Render the interactive widget** — Use the `show_widget` tool to display results visually (see Output Format below).

## Output Format

Render an interactive HTML widget using `show_widget`. The widget should include:

- **Album header**: Title, artist, year, genre
- **Radar/spider chart** OR **horizontal bar chart** showing all 6 category scores visually
- **Score breakdown table**: Category | Score | Weight | Weighted Score
- **Final score** displayed prominently (large, styled)
- **Short written verdict** (2–3 sentences overall take)
- Color coding: red (1–4), yellow (5–6), green (7–8), blue (9–10)

Use the `frontend-design` skill's visual style if available. Otherwise use clean, modern CSS with dark or light theme.

## Edge Cases

- **Instrumental albums**: Skip Vocal Performance, redistribute its 8% weight proportionally to the remaining categories.
- **EPs**: Note it's an EP, apply the same rubric.
- **Unknown/obscure albums**: Still score based on what you can find; note limited info if relevant.
- **If the user provides their own scores**: Accept them and calculate the weighted final, then render the widget with their numbers.
