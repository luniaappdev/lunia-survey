# Lunia — Pilote Survey

Formulaire de consultation pilote pour [Lunia](https://github.com/luniaappdev/lunia),
hébergé sur GitHub Pages, données stockées dans Supabase (ca-central-1, Loi 25).

## Vagues actives

- **Vague 1** (2026-05-20) — `index.html` — comprendre vocabulaire,
  chevauchement multi-conditions, douleur de fond, charge cognitive et
  tonalité préférée.

## Architecture

- **Front** : HTML/CSS/JS vanilla, single-file, ~20 KB, mobile-first
- **Storage local** : `localStorage` (clé `lunia-vague1-2026`) — résume si
  réseau coupe
- **Storage serveur** : Supabase table `pilote_survey_responses` (project
  `hioaymokoffwmhbieitc`, région ca-central-1)
- **Auto-sync** : debounced 800 ms après chaque interaction
- **RLS** : anon role peut INSERT/UPDATE sa session (par UUID),
  authenticated role peut SELECT (lecture admin)

## Pour consulter les réponses

Dashboard Supabase → Table editor → `pilote_survey_responses` → filtrer par
`survey_id = 'vague1-2026-05-20'`.

## Schéma table

Voir `supabase/migrations/0010_pilote_survey_responses.sql` dans le repo
principal `luniaappdev/lunia` (privé).
