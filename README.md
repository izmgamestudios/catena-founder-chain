# Catena Founder Chain

**Every founder is a link.** Catena is a single-page app for managing ventures as chains. People are the big links, and the departments they share are the small links between them. Crises and opportunities show up on those links, and the team practises resolving them in real time.

Turkish sub-brand: *Girişimci Zinciri*.

**Live demo (local mode):** https://izmgamestudios.github.io/catena-founder-chain/

## How it works

| Concept | Meaning |
| --- | --- |
| Big link | A person (solo founder or co-founder) |
| Small link | A department worn (solo) or shared between neighbours in the chain (team) |
| Cobalt / red / yellow | Healthy / crisis / opportunity |
| Shared-resource link | Two ventures sharing a person or resource; a crisis in that department hits both |

## Features

- **Solo and core-team modes**: departments (Sales, Marketing, Finance, IT, Product, Operations, People, Legal) become links in the chain.
- **Crisis and opportunity engine**: 16 built-in bilingual scenarios, 30-second timed responses, speed bonus, 5-round drill.
- **Chain contagion**: a crisis left open for 2 events weakens its neighbouring links and can spread.
- **AI crisis coach**: describe a real situation, get 3 responses, a lesson and a 3-step action plan (needs the Claude runtime).
- **Action board**: owners, due dates, late flags, playbooks per department, "assigned to me" filter.
- **Weekly retro**: five KPIs against the previous week, events by link, rule-based focus list, optional AI retro.
- **Gamification**: XP, levels, best-move streak, badges, per-person weekly leaderboard.
- **Holding**: several ventures as one chain, holding panel table, shared-resource links.
- **Scenario library**: save good AI scenarios; drills draw from them.
- **Bilingual UI**: Turkish and English; light and dark themes; mobile responsive.
- **Backup**: export and import JSON.

## Run it

It is one self-contained file with no build step and no dependencies.

```bash
# any static server
npx serve .
# or
python3 -m http.server 8080
```

Open `http://localhost:8080`.

### Runtime modes

| Mode | When | Data |
| --- | --- | --- |
| Local | Opened as a plain web page | Browser `localStorage` only |
| Team space | Opened as a published Claude artifact | Shared live database, account linking, AI coach and AI retro |

Outside Claude, the AI coach, AI retro, team sync and backup download are hidden, and everything else works in local mode. Use **Load backup** to import data.

## Data model (summary)

```text
ventures/<id>   { name, mode, members[], links[], tasks[], log[], xp, px{}, wk{}, claims{} }
holding/main    { links: [{ a, b, d, note }] }
library/main    { items: [{ d, t, lang, h, b, o[3], s[3], l }] }
```

All values read from storage are sanitised and escaped before rendering.

## Roadmap

1. Run a 7-day pilot with 2–3 co-founders and measure return rate, real situations logged and action close rate.
2. If the pilot passes, move to Next.js + Supabase: multi-tenant schema with RLS, auth, notifications.

## License

MIT, see [LICENSE](LICENSE).
