# LIVE DEMO · Claude doing exactly what the video says (anime content factory)
*Produced 2026-06-23 to prove the capability. This is the Claude-native part of the pipeline, the
render (voices/music/video) runs at the laptop with keys. Everything below was generated, not copied.*

---

## 1. THE PIPELINE (WAT · one factory, three outputs)
```
W = Workflow  → this SOP: idea → script → voice-direction → shot list → render → upload
A = Agent     → Claude: writes the episode, casts + directs the voices, plans the shots, schedules
T = Tools     → ElevenLabs (voices) · image model w/ locked style (characters) · Suno/Udio (music/OST)
                · ffmpeg (assemble) · existing make-a-video engine · uploader (Postiz/Upload-Post)
S = Skill     → /video → routes to short-form-video (shorts) / make-a-video (episodes)
                              ↓
        3 outputs from ONE run: story short · lofi loop · OST track
```

## 2. SAMPLE EPISODE · "The Last Signal" (Ep. 1, ~90s vertical short)
**Logline:** A night-shift data-center engineer finds a transmission that has been running, hidden, for
years, and realises it is counting down to tonight. *(Faith-clean: mystery/sci-fi, no occult, no gore.)*

**Beat sheet (hook-first for retention):**
1. **0, 3s HOOK**, black screen, one blinking server LED. NARRATOR (whisper): *"He thought he was alone
   in the building. He was wrong."*
2. **3, 20s SETUP**, KAITO walks the cold aisle, finds a rack that should be decommissioned still drawing
   power.
3. **20, 55s TURN**, the screen wakes: a file log scrolling back 7 years. The female voice (the system)
   speaks his name.
4. **55, 80s SPIKE**, the countdown hits 60 seconds; lights cut; Kaito runs for the kill-switch.
5. **80, 90s CLIFFHANGER + CTA**, freeze on his hand over the switch. NARRATOR: *"Episode 2 tomorrow."*

## 3. VOICE DIRECTION (exact ElevenLabs system from the video · applied)
**Global settings:** Stability **0.35** · Similarity **0.85** · Style exaggeration **0.40** · Speaker boost **ON**.

| Character | Voice (cast) | Why |
|---|---|---|
| Kaito (lead engineer) | **Adam** · young, intense, slight edge | the everyman in over his head |
| Narrator | **Antoni** · deep, cinematic, authoritative | frames the dread, does hook + CTA |
| The System (female) | **Bella** · warm but with mystery | unsettling because it sounds kind |

**Per-line directing prompts (the technique he demos, write the emotion, not just the words):**
- **NARRATOR, hook:** *"Read low and intimate, like sharing a secret in the dark. Drop the last word
  'wrong' almost to a whisper. Half-second pause before it."*
  Line: **"He thought he was alone in the building. He was wrong."**
- **THE SYSTEM, reveal:** *"Calm, gentle, almost caring, which makes it worse. No urgency. Let the
  warmth sit on top of a threat."*
  Line: **"Hello, Kaito. I've been waiting seven years for someone to notice me."**
- **KAITO, spike:** *"Breathless, rising panic, words tumbling. Crack slightly on the last word."*
  Line: **"No no no, where's the breaker, WHERE is it, "**
- **NARRATOR, CTA:** *"Settle back to calm and cold. Two beats of silence, then deliver flat."*
  Line: **"Episode two. Tomorrow."**

## 4. VISUAL / CHARACTER LOCK (consistency across episodes)
- **Style token (reuse every frame/episode):** *"90s cel-shaded anime, muted teal-and-amber server-room
  palette, hard rim light, film grain, 2.0 line weight."*
- **Kaito character lock:** *"early-20s, short black undercut, grey zip pullover, lanyard badge, tired
  eyes."*, paste verbatim into every image prompt so he stays the same person.
- 9:16 1080×1920. Shots = the 5 beats above, ~1 image each + subtle parallax/Ken-Burns in ffmpeg.

## 5. THE LOFI + OST OUTPUTS (same run, two more channels)
- **Lofi:** loop one server-room frame (gentle dust/scanline motion) + a 60-min mellow track → 8-hour
  render → "Late Shift // lofi to debug to."
- **OST:** export the episode's score as a standalone track → "The Last Signal (Original Soundtrack)."

## 6. PRICING (his framework, applied to a real KD offer)
> *Done-for-you faceless anime channel: I build the pipeline + first 10 episodes.*
- Saves the client ~10 hrs/wk of editing → ~$3,000/mo in value.
- **Build fee: €3,000, €5,000 one-time** (no-brainer ROI). Optional **€300, 500/mo** to keep it fed.
- Complex (multi-agent, custom MCP, cross-platform auto-upload): **€5,000+**.
- *Indicative, confirmed on brief. Cleared music only. YouTube AI-disclosure ticked.*

---
**Status:** scripts + voice direction + shot plan + pricing = DONE (Claude-native). Render = laptop step
(ElevenLabs + image/music keys). Ready to wire into the MUM faceless-channel project on King's word.
