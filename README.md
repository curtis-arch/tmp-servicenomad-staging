# ServiceNomad "Stay on the roof." spot: working files

Everything generated for the spot, including versions that did not make the cut, so the progression is visible.
Files ending in `.b64` are base64 text (the only way the render sandbox could pull them). Rebuild any of them with:

```
base64 -d img/v2/s1.jpg.b64 > s1.jpg
cat vid/v2/s3.mp4.part*.b64 | base64 -d > s3.mp4      # split files: join parts in order, then decode
```

## Progression

| Round | What | Verdict |
| --- | --- | --- |
| v1 | Stills on GPT Image 2.6 Flare (`img/*.jpg.b64`), clips on MiniMax H3 Max at 768p (`vid/`), first audio (`vo/`, `sfx/`, `music/`) | Worked end to end, but looked generated: plain pickup, AC shroud on, softer faces. Replaced. |
| Base v2 | John's hyper-real roof image (`img/IMG_3554.png`) | New anchor for everything. Service-body Ford, open AC unit, Hill Country. |
| Stills v2 | GPT Image 2.6 Sunburst edit, each referencing the base (`img/v2/`) | Approved. s5 redone once to remove the tool pouch at the kitchen table. |
| Model test 1 | Roof shot on H3 Max, FLUX 3 Max, FLUX 3 at 1080p (`cmp/h3max`, `cmp/flux3max`, `cmp/flux3`) | H3 Max won on acting. FLUX 3 steadiest but looked into the lens. FLUX 3 Max jerkiest. No phone movement in any. |
| Model test 2 | Same shot with an explicit vibrating-phone prompt (`cmp/h3max_v2`, `cmp/flux3_v2`) | FLUX 3 fixed the eye contact but still ignored the phone. H3 Max moved the phone too much (about 30 degrees of rotation, 108 px drift). |
| Final clips | Nine clips on H3 Max at 1080p with a restrained buzz prompt (`vid/v2/`) | Used. Phone in s3 now moves for about 1 s then lies still (12 px drift). |
| Final audio | All new, written to the cut (`audio/v2/`) | Used. See below. |

## Final audio
- **Music** (`audio/v2/music/`): ElevenLabs music_v2_5 with a hand-written composition plan timed to the edit: 27 s sparse opening, 3.5 s near-silent hold under the title card, 17.5 s build, 6 s resolve to silence. Plan saved next to the track.
- **Voiceover** (`audio/v2/vo/`): one continuous take on Eleven v4, voice "Sam - Deep Americana" (`iRc49NKOKzEg1DVxmcRs`), split at the silent gaps between lines (all about -90 dB, 110 to 310 ms) so no line is clipped. Alignment JSON included.
- **Sound effects** (`audio/v2/sfx/`): 16 new effects on eleven_text_to_sound_v2, prompts in `prompts.json`. Phone buzzes were trimmed to the measured phone motion in s3 (10.4 to 11.4 s) and s4 (14.4 to 16.6 s).

## Edit (54 s, 1920x1080, 24 fps)
| Time | Shot | VO line |
| --- | --- | --- |
| 0:00 | s1 truck at dawn, "6:40 a.m." | You didn't start this business to answer a phone. |
| 0:05 | s2 ladder | You started it to fix things. On your own terms. |
| 0:10 | s3 roof, phone buzzes, "10:15 a.m. Missed call" | But the phone rings when you're on a roof. |
| 0:14 | s4 under the slide, "1:40 p.m. Missed call" | It rings when you're under a slide. |
| 0:18 | s5 kitchen, "9:12 p.m." | And every call you miss... the next guy. |
| 0:27 | Title card | So stay on the roof. |
| 0:30 | s6a phone, "New job booked" card; s6b nod | ServiceNomad answers... the way you would. |
| 0:38 | s7 paid at the campsite | Your customer knows you're coming... |
| 0:43 | s8 home, daughter | And you're home for dinner. |
| 0:47 | End card, logo | ServiceNomad. Stay on the roof. |

Request IDs, input stills and prompts for the final clips: `vid/v2/requests.json`; output URLs: `vid/v2/output_urls.json` (fal links expire).

## Not in this repo yet
Rendered outputs were made in a sandbox that can't push here, so these were delivered in chat: the v1 and v2 finished spots, the web version, the model comparison videos, contact sheets. Add them by hand (the GitHub web uploader takes files up to 25 MB; the web version of v2 is under that).

## Approximate cost
- v1 spot: about $2.90 (video $1.65, stills $0.67, audio about $0.55)
- Stills v2 plus s5 fix: about $0.65
- Model tests: about $1.43
- Final v2 clips: $1.65 (47 s at $0.035/s); final v2 audio: about 2,800 ElevenLabs credits (about $0.55)
- Total so far: roughly $7 to $7.50
