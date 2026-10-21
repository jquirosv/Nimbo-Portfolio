# Visual assets and provenance

[← Nimbo](../../README.md)

The PNG files are unchanged copies of app-generated render fixtures. Synthetic song names, artists, lyrics, totals, and geometric artwork originate in the project's tests. No commercial recording, lyrics catalog, personal account screen, or operational dashboard is included.

| Published file | Original render | Version / context |
| --- | --- | --- |
| `01-player.png` | `Nimbo-v0.7.1-reproductor-texto200.png` | Player, 200% text |
| `02-statistics.png` | `Nimbo-v0.8.0-statistics-overview.png` | Statistics overview |
| `03-appearance.png` | `Nimbo-v0.6.1-apariencia.png` | Theme and typography settings |
| `04-recap-opening.png` | `Nimbo-v0.8.0-story-1.png` | Recap opening |
| `05-recap-summary.png` | `Nimbo-v0.8.0-story-7.png` | Recap closing summary |
| `06-library-selection.png` | `Nimbo-v0.6.1-seleccion.png` | Selection with fictional tracks |
| `07-player-landscape.png` | `Nimbo-v0.7.1-reproductor-horizontal-dinamico-texto200.png` | Landscape, 200% text |
| `08-lyrics.png` | `Nimbo-v0.7.1-letra-texto200.png` | Invented local lyrics, 200% text |

`00-cover.svg` is a presentation graphic created for this case study. It uses Nimbo's existing halo mark and navy, pearl, and lavender palette; it is not an application screenshot. `nimbo-logo.svg` is copied unchanged from the project's brand assets.

StatisticsDesignTest generates the fictional statistics. MonthlyRecapTest generates the recap's placeholder artwork and listening data. Player and appearance layout tests generate the other selected views. The project UI is in Spanish; the primary case study is in English with a Spanish overview.

Lyrics assistance uses [LRCLIB](https://lrclib.net/), credited here for its role in the application. This repository does not include provider responses or redistribute the provider's content. Application dependencies and fonts retain their respective licenses; their source and font binaries are not distributed here.
