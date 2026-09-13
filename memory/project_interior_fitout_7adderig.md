---
name: project-interior-fitout-7adderig
description: "Interior fit-out of a 3-bed Dublin townhouse (7 adderig farm), WAT scaffold + /fitout skill, run one room at a time toward a costed shopping list + 3D walkthrough."
metadata: 
  node_type: memory
  type: project
  originSessionId: 8be7445d-5221-4c1a-b698-fe77a467765e
---

# Interior Fit-Out · "7 adderig farm"

**Folder:** `C:\Users\Dell\Documents\7 adderig farm` · **Status:** ⏸ **PARKED (2026-07-03) · ⚠️ THE CREDIT UNION REJECTED THE HOUSE LOAN; only the CAR loan was approved** (King's disclosure at the Council of LOGOS-OS, 2026-07-03: "They rejected loan to house, only gave loan for car, we will talk more about it"). The whole-house design stays locked and ready, but there is NO funding → no scheduled work blocks. The funding conversation moves into the FULL finance re-review (awaiting King's Revolut/BOI exports + the credit-union decision details, amount/rate/term of the car loan). When money is real, the project wakes here. *(The 06-22 "awaiting approval" status below is superseded.)*

## ✅ 2026-06-22 (EVENING) · LOAN MEETING DONE, AMY'S TERMS (KEY UPDATE)
**The meeting with the credit union loan officer (Amy) went well.** Real terms she gave King, which DIFFER from our planned budget, capture these as the live truth:
- **Term: 5 years (60 months), NOT 24 months.** If the loan is approved it is structured over 5 years.
- **Repayment: ~€600/month** (the figure Amy quoted; lines up with ~€30k @ ~7-8% over 5 yrs ≈ €600-625/mo).
- **King can pay it back within 2 years if he wants.** Credit unions charge interest on the REDUCING balance with NO early-repayment penalty, so overpaying to clear it in ~2 years means he pays far less total interest than the full 5-year run.
- **Why this is GOOD:** the required monthly commitment drops from our planned €1,393 to ~€600 → much easier to get approved + big monthly breathing room, while he keeps the freedom to clear it fast and save interest. Best of both.
- **Status: awaiting the approval decision.** Our earlier budget pack (€30,794 / 24 mo / €1,393) was the affordability case King brought in; Amy's 5-year/€600 structure is how the CU actually wants to write it. The Junior Cert Household Budget still stands strong (surplus only grows when the required payment is €600 not €1,393).
- **TODO when approved / on King's word:** if useful, re-cut the household budget + any pack to show the 5-year/€600 line with a "clears in ~2 yrs via overpayment" note. Not built yet, confirm with King first.
- **💶 LOAN AMOUNT CORRECTED (King, evening):** max is now **~€25,000 total**, NOT the old €30,794. Split King confirmed = **~€22,700 home + €2,300 car**, and the **old PCU loan is kept SEPARATE this time (NOT consolidated).** Amy also asked King to **bring (a) a written labour quote from the builder + (b) a breakdown of where the loan is spent.** CU also pulls his **Revolut + BOI** statements (affordability check); decision NOT certain yet.
- **🧾 COST-BY-ROOM REBUILT to fit €22,700** = `knowledge\house\HOUSE_COST_BY_ROOM_2026-06-22.md` (committed/pushed). **APPLIANCES were missing before, now INCLUDED, mid-range €2,650** (oven 400 / hob 375 / dishwasher 400 / washer 450 / dryer 400 / fridge 625). To fit: **floor switched to laminate €1,895** (SPC €2,999 = +€1,104 lever), **master trimmed €4,500→€3,000**, **Bed 2 €1,800**. Locked-real rooms: Living €3,760, Kitchen island+finish €3,780, Josh €1,602, Bathroom €960, Labour €2,330. Master + Bed 2 = the flex/estimate points. NOTE: kitchen €3,780 was island+finish ONLY (units/extractor already builder-finish).
- **📧 EMAIL LIMITATION:** this was a Claude Code **web/remote** session, Gmail send pipeline (laptop `google_auth.py`) NOT reachable, so cost sheet was delivered via the kd-brain repo (syncs to phone) + pasted in chat, NOT emailed. Send to Gmail properly next time King is at the laptop.

## ✅ 2026-06-22 (PM) · FLOOR-PLAN-FIRST CAD SET + JOSH LOCKED (BIGGER TV) + LOAN PRINT PACK + MASTER CARRIED
**Read `handoffs\handoff_2026-06-22_cad-set_save.md` FIRST.** King's method locked: design from the to-scale floor plan FIRST, then make the photo match (the Josh method). Built this pass:
- **LOAN (meeting was TODAY):** one-pager `deliverables\showhome\MEETING_DAY.png` (ask + numbers + bring-list + script) + print-ready `LOAN_MEETING_PRINT.pdf` (3 pages: one-sheet + budget + proposal) + soft copies, emailed to King x2 + pushed to phone so he could print at the library. Numbers unchanged: €30,794 / 7.99% / 24 mo / €1,393 / ~€999.50 surplus / clears Jul 2028.
- **JOSH (Bed 3) FULLY LOCKED:** he is happy, wanted a **bigger TV** -> enlarged on `JOSH_room_PLAN.png`, lock email sent. Watch loop retired.
- **CAD SET for the whole house except master:** reusable generators `.tmp\room_plan.py` (9 to-scale 2D plans) + `.tmp\room_elevation.py` (10 key-wall elevations), Josh's approved PIL style, brand colours, confidence badges (Josh TAPE-LOCKED, rest "estimate, confirm with tape"). Output `deliverables\showhome\room_plans\`.
- **3D TOUR finished + locked "like a google studio":** new gallery page `deliverables\walkthrough\plans.html` (all plans + elevations, lightbox) wired into the hub `index.html` as a "Floor plans & elevations" card. Master carried as a labelled **"Master bedroom (Mum) reserved €4,500, designed later"** line so €24k stays whole. Deployed + re-aliased **kd-house-tour.vercel.app** (verified 200, plan assets 200, 0 console errors). Plan PNGs copied into `walkthrough\plans\` so Vercel serves them.
- **IMAGE-FROM-PLAN METHOD documented** (`room_plans\IMAGE_FROM_PLAN_METHOD.md`). Photoreal re-renders of Living/Kitchen/Bed 2 = **TO DO LIVE WITH KING** (need his eye per QA-until-approves; WebGL/AI renders can't be QA'd headless). **Bed 2 (King's room) plan is a DRAFT** -> he said 1 or 2 things to change; get them before rendering.
- **MASTER (Bed 1, Mum):** INCLUDED + carried as ~€4,000-5,000 reserve, designed later her own way (separate mini-project). Not drawn this pass.
- **NEXT:** (1) get King's 1-2 changes to his room -> update plan; (2) run the image-from-plan renders live with King for Living/Kitchen/Bed 2; (3) optional: add geometry-driven furniture to walk3d (deferred, can't QA WebGL headless); (4) tape-measure rooms to lock dims (only Josh tape-locked).

### 2026-06-22 (late) · BROCHURE METHOD CONFIRMED + dims reconcile + upstairs circulation + store/ensuite reality
- **King's method (agreed):** COPY the brochure for the 2D plan, design the room inside it, then 3D-generate like Josh's + King's rooms. Apply across the house.
- **KEY FINDING (good news):** the brochure scale reconciles with reality. Detected orange walls in `floorplan.png` (1206x2622): building ~470 px/floor wide, habitable depth ~771 px (rows 1026..1797), the two floors stack (same ~470 px width). At the **area-anchored scale ~83.5 px/m** (52 m2/floor, building ~5.63 x 9.24 m) Josh's room traces to **~2.49 m deep vs his real 2.56 m tape** = basically spot on. So the earlier "3.3 m depth" was a MEASUREMENT ERROR, NOT a brochure-vs-build gap. The brochure IS the trusted 2D base; tape-lock each room at the end (only Bed 3 so far). Tool: `.tmp\measure_plan.py`.
- **UPSTAIRS CIRCULATION (King):** stairs continue up from the ground-floor hall to the landing; off it you see the BATHROOM door then BED 2 (King) on one side, and continuing round the STORE (water pump), the MASTER (Bed 1), and BED 3 (Josh). Upstairs rooms sit above the ground floor (same footprint) but their sizes need not match the rooms below exactly. Captured in `geometry.json` top note + floor-1 note; floor-1 width set to 5.86 to match ground.
- **STORE / ENSUITE REAL DIFFERS FROM BROCHURE (King):** as-built STORE is BIGGER (took ensuite space, holds the water pump); ENSUITE is SMALLER (only fits a shower now, nothing installed; expand later by taking store space, a wall to break down, council ok). Marked `conf:"real-differs"` on both in geometry.json. **Master + ensuite = Mum's later project. Awaiting King's pic/vid to set the real store/ensuite split.**
- **WHAT I NEED FROM KING to finish exact:** (a) his 1-2 changes to Bed 2; (b) a quick tape (width x depth) of the LIVING + KITCHEN to lock them like Josh's; (c) the store/ensuite pic/vid. Then run the 3D renders live with him.
- **2D LAYOUT FIXED + REDEPLOYED (King: "fix the 2d layout first ... then when im back ill lock them in"):** Traced floorplan.png with a 0..1 grid (`.tmp\grid_crops.py`), REBUILT `geometry.json` so rooms TILE the footprint cleanly and match the brochure. Ground floor = 2 columns (hall/WC/utility 1.75 wide + living/kitchen 4.11 wide). Upstairs rebuilt per King's circulation: Josh top-left (tape 2.82x2.56), master top-right (3.04x4.06), landing where stairs arrive, store(1.7x1.5)+ensuite(2.31x1.5) middle (both `conf:real-differs`), bathroom back-left, Bed2 back-right above the kitchen. Floor-1 width set 5.86 = ground (stacks). Built whole-house 2D image `room_plans\HOUSE_2D_LAYOUT.png` (both floors, brochure-style, `.tmp\floorplan_2d.py` reads geometry.json). Synced the embedded GEO into walk3d.html + plan2d.html (`.tmp\sync_geo.py`), QA'd both floors of plan2d (0 console errors), redeployed + re-aliased kd-house-tour.vercel.app, emailed King the layout + pushed. **Sizes still estimates except Josh; King tape-locks each room next.**

## ✅ 2026-06-22 · WALKTHROUGH REBUILT CORRECT + LOAN BUDGET + JOSH ROOM LOCKED + NO-DASH RULE
**Read `handoffs\handoff_2026-06-22_03-00_save.md` FIRST.**
- **🌐 WALKTHROUGH FIXED + LIVE = kd-house-tour.vercel.app.** Old one (King: "completely wrong") replaced. Root cause: I was eyeballing the layout + using a circular area-assumption for scale. Fix: **traced the real brochure ("The Dargle", 104 m² gross / 91 m² net), anchored scale to Josh's tape measure, saved ONE source of truth `deliverables\walkthrough\geometry.json`.** Built 3 formats off it via a 3-agent workflow (all read geometry.json so nothing can be misplaced): to-scale 2D plan `plan2d.html`, first-person 3D walk `walk3d.html`, hub + phone-scan guide `index.html`. Re-alias after any deploy.
- **💶 LOAN BUDGET for the credit union (Junior Cert Household Budget template, in King's name).** Full term **July 2026 to July 2028**, loan hits "cleared" July 2028. **Top-up/consolidation:** old PCU loan (~€4,494 @ 10.4%, €160/mo) rolled into the new €30,794 @ 7.99%; old €160 paid a final time July 2026; on its own the old loan ran to **~March 2029 (2y9m)**. **Credit card = €1,500 LIMIT**, tops up in full what he uses, leaves the rest, no interest/debt. **Income €4,400/mo minimum, can be more. FREELANCE REMOVED** (King shows the CU and wants it clean). Surplus **€999.50/mo**, debt-free July 2028 (then €2,392.50/mo). Files `deliverables\showhome\HOUSEHOLD_BUDGET.html/.png` + meeting pack `TOMORROW_CU_PACK.html/.png` (what to bring + what to say). Consolidated into a "FOR TOMORROW" email.
- **🛏️ JOSH ROOM (Bedroom 3) DESIGN LOCKED:** bed LEFT wall, TV RIGHT wall, WINDOW far wall ACROSS from the WARDROBE, wardrobe foreground beside the door (you see its side walking in), queen, greige curtain, pale oak, no drawer. Render `JOSH_room_v12.png` + plan `JOSH_room_PLAN.png`. ~€1,602 + a wall TV. (Sent to King labelled "correct"; pending King's nod to send Josh + lock.)
- **🔑 DIMENSIONS STANDARD (King set):** brochure trace = accurate LAYOUT + total area, but per-room sizes are ESTIMATES (±~30 cm) until King tape-measures. Only Josh's room is tape-locked (his real 2.82×2.56 was 24% under my derived 8.9 m²). geometry.json is the one source of truth; measuring each room locks it + reflows the whole house.
- **🛑 PROVEN AGAIN:** AI photo renders CANNOT place furniture reliably (took 5 tries on Josh's wardrobe). The to-scale PLAN is the agreed truth the fitter builds from. With Josh: LISTEN + confirm in his words, never assume. **🆕 HARD RULE: NO em-dashes/en-dashes anywhere, every task** ([[feedback-sound-human-not-ai]]).

> ⚠️ **READ `plans\ok-so-im-im-effervescent-dewdrop.md` + `handoffs\handoff_2026-06-20_09-45_save.md` FIRST.** **2026-06-20 hard reset:** the 3D walkthrough (`house.html`) + parallax (`kitchen_moving.html`) + the multi-card gallery are **DROPPED**, they had a wrong/guessed layout and confused King. **The only correct method: render the pale-oak floor onto King's REAL room images** (`tools\gemini_render.py --ref`) so the layout is right by definition. Sources: the **empty walkthrough video** (furniture-free frames for kitchen/3 beds/bath/WC/hall/stairs) + King's **new slow per-room videos** for living/utility/terrace/bike (clutter ok, strip it). **Foundation (floor) first, interior design later.** Layout locked: kitchen = street-window room, living = terrace-doors room (no window). King's Drive links are LOCKED (send photos via Gmail/chat). New rules: [[feedback-no-overselling-verify-before-send]] + strengthened [[feedback-always-send-gmail-and-link]] (deliver to phone every time incl. testing). **NEXT = King sends LIVING-ROOM video → floor it on his real frames.**

## ⚠️ 2026-06-21 (LATE PM) · BATHROOM LOCKED · JOSH LOOP · /humanize · WALKTHROUGH BUILT **but KING SAYS WRONG**
**Read `handoffs\handoff_2026-06-21_23-45_save.md` FIRST.**
- **🛑 WALKTHROUGH FLAGGED WRONG:** built + deployed an interactive floor-plan virtual tour
  (`deliverables\walkthrough\tour.html` → **kd-house-tour.vercel.app**, public), SVG dollhouse hub both
  floors + tap-to-photoreal room view + dims + products + price + running total. King's verdict at save:
  **"the walkthrough is complete wrong man."** Do NOT assume the format/layout is right. **NEXT = ask King
  EXACTLY what's wrong** (flat floor-plan vs a real moving/3D tour like the TikTok/Evara ref? layout? dims?)
  and rework. Approved plan was `plans\thats-fine-what-is-memoized-fog.md` (now needs revisiting).
- **MATH (dimensions):** calibrated `floorplan.png` (orange walls → both floors 468px wide, habitable 792px)
  to 104 m2 → **84.4 px/m, building 5.54 m wide**; derived NET ~90 m2 (=91 m2 floor) + GROSS ~104 m2 (both
  brochure figures reconciled). `deliverables\walkthrough\room_dimensions_DERIVED.csv`. DERIVED ESTIMATE;
  tape-confirm at end. **Josh tape-measured Bed 3 = 2.82 x 2.56 m (~7.2 m2).**
- **🛁 BATHROOM LOCKED:** custom lift-up mirror across the wall (fitter-built; a true whole-wall pull-up
  mirror does NOT exist off-the-shelf) ~€600-900 + fixed 8mm toughened glass bath screen + bracing bar
  ~€175-250; stays tiled, basin+toilet kept. Pulled the BATH angle from the walkthrough video → `BATHROOM_all_refs.jpg`;
  drew the glass pane onto the REAL bath photo (`BATHROOM_pane_real.jpg`) after AI kept inventing a window
  (King: stop over-generating → draw on the real photo with PIL, not full AI render).
- **🛏️ JOSH'S ROOM, looping (NOT locked):** King set up an email loop, I email Josh directly, background
  agents render Bed 3 per his feedback + reply, loop until he's happy (then lock + tell King). v1→v7 done.
  **FAST MODE** (King: Josh said replies were slow) = instant "on it" ack on every reply + 180s poll. Josh is
  6ft, wants a comfortable queen even though 7.2 m2 is snug; wardrobe back against the door wall. Loop STILL
  RUNNING at save (laptop-on). ~€1,602 (bed may change with fit).
- **🆕 /humanize skill** (`commands\humanize.md`), auto-strip AI tells + write in King's voice before any
  person-to-person message. Master = still PARKED for Mum. WC/hall/utility/store still to design; appliances
  (cooker/washer/dryer) NOT yet sourced.

## ✅ 2026-06-21 (PM) · DOWNSTAIRS LOCKED (value re-source + kitchen reconfirmed) + 2 NEW RULES
**King: "lock in downstairs for kitchen and living room and prices and we save."** Downstairs is **LOCKED.**
Final shopping list + prices = `deliverables\showhome\DOWNSTAIRS_LOCKED.jpg`. Records: `cost_tracker.md`
(top banner + VALUE RE-SOURCE + KITCHEN CONFIRMED) + `decisions.md`.
- **LIVING €3,760:** King **KEEPS his €3,000 bespoke sofa** (J&B); cheaper look-alikes for the rest, Udsbjerg
  beige tub chair €70, Sandfiol ivory rug €110, Farsund oak/black TV €115, Spodsbjerg dark-oak coffee €100,
  Nordlux Grant brass globe pendant €57, Clara ochre cushions €36, **own mirror €0**, Dunelm sheers €12, + 6-spot
  share €260. Render `LIVING_mood_v3.png`.
- **KITCHEN €3,780 (island-only):** built-in island per **King's OG inspo** (IMG_7686); **5 taupe Bas stools**
  (2 front + 3 side, he went 6→8→7→**5**); **Hisense 632L black fridge in the WINDOW corner** (8:30-render spot,   do NOT move); **seamless light-greige splashback** (Josh's pic IMG_2526, Splashwall matt acrylic €241 or
  microcement ~€350-600, NOT black/tile); brass globe pendant €34; **under-cabinet LED strip lights**; styling €120;
  **bin = King sources** (black/green compost). Render `KITCHEN_mood_v7.png`.
- **FLOOR = King's LAST pick** (91 m²): Canadia Tokyo Oak laminate Co-Op €18.95/m² ~€1,895 / **Olympus SPC
  waterproof Des Kelly €29.99/m² ~€2,999 (recommended)** / engineered real oak ~€5,899. **ALL-IN €9,435, €10,539**
  (was ~€13,200 → saves ~€2,700-3,800, keeping the €3k sofa + bigger fridge).
- **🆕 AI MOOD RENDERS WORKED** (`gemini_render.py --ref <real empty room> --ref <product>` + "keep
  walls/windows/units, only add the design"): living v3 + kitchen v7 both accurate + King liked. Earlier fatigue
  was floor-swap/exact renders; a fresh mood render anchored to the real room is fine, labelled vision.
- **🆕 OPTION-BOARD method:** King wanted 3-4 priced options per item to pick → `OPTIONS_living/kitchen/floor_decor.jpg`
  (5 research subagents → real products + direct image URLs; og:image + Playwright for JS sites).
- **CHINA/global (King asked):** only worth importing small stuff (cushion covers ~€4-7, sheers, pendants); big
  items buy local. Ireland VAT on all imports; ≤€150 = VAT at checkout, >€150 = +duty +VAT +handling.
- 🆕 **2 STANDING RULES:** [[feedback-confirm-spec-before-send]] (confirm EXACTLY how he wants it before
  building/sending, "confirm so we dont get design mix up") + the **Drive-login-lock lesson** (his Gmail "Drive
  video" links need a login → I can't open them → SAY SO + ask for a plain photo/screenshot, NEVER guess; a normal
  photo like `IMG_7703.png` works; gdrive_dl fails on locked links; Drive MCP reads metadata but 72MB video ≠
  base64-able).
- **NEXT:** King picks the floor; set upstairs videos (IMG_7558, 7565) to "Anyone with the link" OR send as photos
  → design **Bedroom 2** (King's own room).

## ✅ 2026-06-21 · LIVING ROOM DESIGNED + LOCKED (King: "im happy") + VISUAL HARD-LIMIT PROVEN
**King is happy with the living-room LOOK.** All pieces chosen, real, **NO IKEA** (King's hard rule):
- **Couch:** **Nesco** beige FABRIC corner **SOFA BED** (J&B Furniture), **3 seats + lie-down chaise**, bespoke (~€3,000 EST, exact 3+chaise price TBC at J&B). Pull-out + storage for guests. (Nesco shop photo = 2+chaise → customised to **3+1**. King + Josh agree.)
- **Chair:** **Flora** beige tub (Harvey Norman) **€399**. **Rug:** **Globe** ivory 200×290 (HN) **€276**. **TV unit:** **Richmond DARK smoked-oak** 140cm (HN) **€329** + matching **Richmond round** coffee table **€149**. **Cushions:** **Clara** ochre velvet (Dunelm) ~€12 ea.
- **Lighting:** **6 dimmable LED spotlights** (Ledex €9.55 ea) in living + 6 in dining, **each zone its own dimmer** (electrician cuts 12 downlights on 2 circuits, confirmed from the ceiling video IMG_7677.mov: white, partly-sloped ceiling, existing single pendant points) **+ the brass globe pendant kept** (King likes the middle light). Brass cluster (Bright Lights €142) optional.
- **Mirror = King's OWN** (€0). Sheer curtains ~€40 (to source, websearch was down). **Sony 4K TV** ~€700, 1,000 (pick 55 vs 65"). **Living-room all-in ≈ €4,620.**
- **Floor area updated to 110 m²** (King's measure) × €31.95 = **€3,514.50** material (was ~100 m²/€3,200). Terrace is **PAVED** (no garden/grass).
- **Mustard velvet accent chair = DISCONTINUED everywhere** (EZ Living Lily gone, M&B Oliver 404, Atkin&Thyme out, Cult none). → Option B = **neutral Flora chair + Clara ochre mustard cushions** (in stock); swap to a velvet chair later if one returns.

### 🛑 THE VISUAL HARD-LIMIT (proven this session · READ THIS)
You **cannot perfectly drop the client's chosen products into their real show-home photo.** Both routes fail:
- **AI full-regen (gemini_render) REDRAWS the whole room**, it invented a garden, lightened the dark Richmond TV unit to pale oak, and recomposed the entire show-home photo. King: *"everything changed… wtf… stop and QA before send."*
- **Manual PIL paste-in FAILS too**, catalogue product photos are a **different camera angle** than the show-home sofa, so the pasted couch looks stuck-on and the **old grey sofa shows through** (proven: `.tmp/COMPOSITE_v1.jpg`).
- **✅ CONCLUSION:** rely on the **real show-home photo (the look) + the real product photos (what they buy) + the cost.** Don't chase the one perfect combined picture, no tool makes it cleanly. AI render = **MOOD only, labelled**. The sheer-curtain trick (draw sheers across the doors) hides the outside so AI can't invent a garden, but it still redraws the room. Full detail → [[reference-floor-swap-ai-limit-showhome-method]].

### Rules King set/reinforced 2026-06-21
- **NO IKEA furniture** (whole house). · **QA BEFORE SEND**, screenshot + compare to the target + loop (regenerate→check) until ONLY the agreed items changed; **never send un-QA'd work**. · **Always send to Josh too** (joshagbidi6@gmail.com) but **verified-correct only**, never AI slop/mistakes (King was embarrassed when the garden render reached Josh). See [[feedback-house-send-to-josh]].
- **NEXT:** give the **full living-room cost** vs €15, 20k; then next room (kitchen/dining or bedroom) with **real products + show-home as the vibe** (no fake combined renders); confirm Nesco 3+chaise price at J&B; source sheer curtains when websearch is back.

## 🟡 2026-06-21 (PM) · KITCHEN & DINING DESIGNED (board sent, awaiting King's approval)
Built from **King's Gmail island inspo** (`references\kitchen-dining\island_inspo_king.png` = IMG_7686) + the
**show-home kitchen sh_18s** (his house type) + **real product photos + real € prices** (the proven method, no
fake combined render). Board = `deliverables\showhome\KD_board.jpg`; full spec = `rooms\kitchen-dining.md`.
- **KITCHEN (units stay, we add):** an **ISLAND like the inspo but NO sink, 3 stools across**, waterfall top
  (custom-to-match ~€2,200 / freestanding ~€600) · **Bas taupe counter stools €149×3** (HN) · **black
  fridge-freezer in the corner** (Tesla 582L €870 / Hisense 632L 4-door €1,290) · **black splashback at the
  sink** (King's ask) ~€280 · **bin in the old dishwasher gap** ~€80 · brass globe island pendant ~€120 ·
  lights = same as living (6 spotlights + middle pendant, already in the open-plan job).
- **DINING (dark smoked oak + beige, full zone):** **Bari 140, 200cm smoked-oak extending table €749** (seats
  6→8; Hudson 2m €899 alt) · **Jessie taupe tub chairs €149×6** (oatmeal + black legs = the show-home bouclé
  look) · dark-oak sideboard ~€499 · greige blind ~€120 · rug ~€199 · decor ~€120.
- **COST:** kitchen+dining **~€6,700** (custom island, value fridge) / leaner **~€5,100**. **House so far
  ~€19,600, near the €20k ceiling**; the island is the swing (leaner kitchen → house ~€18,000). Flagged honestly.
- **Accents = brown/black/green** (ties to living room). Floor = pale oak (locked). Sent to King ×3 + Josh + ntfy.
- **3 open calls for King:** island custom vs freestanding · fridge €870 vs €1,290 · table Bari vs Hudson.
- 🆕 **LIVING ROOM design image = Josh's photo** (`references\living-room\JOSH_living_design.png` +
  `deliverables\showhome\LIVING_design_josh.png`), King: "use josh image as living room design, closest to what
  we want with the stuff we want." It really shows our pieces (beige chaise sofa + mustard cushions + round
  dark-oak coffee table + beige tub chair + cream rug + round mirror). Adopt it as THE living-room visual.
- Reliable retailers this session: **Harvey Norman** (imgix images), **EZ Living Furniture** (smoked-oak tables,   page JS-blocks WebFetch but search works), **BuyItDirect** (black American fridges). EZ-Living-Interiors + Tisbury HN page 404'd.

## ✅ 2026-06-21 (evening) · KITCHEN/DINING LOCKED + FULL LOAN PROPOSAL BUILT
**Kitchen/dining = 🔒 LOCKED.** King's final picks: **built-in island (VALUE) ~€1,200**, white base to match units + top matching his **existing GREY worktop** (a white quartz waterfall would CLASH with the grey worktop AND cost ~€1k more → matching-worktop built-in is best price+look, Claude's call on "do what's best for price+output"). Black **Tesla 582L** fridge in the corner beside the window · **pull-down shutter blind** (NOT plantation) · black splashback at sink · bin in old dishwasher gap · **keep BOTH** island (3 stools one side, 3-either-side clashes with the table) + smoked-oak Bari extending table €749 + 6 Jessie taupe tub chairs €894 · "cooking station" = existing hob (no cost). **NO PAINT** (King 2026-06-21, dropped). Floor confirmed **91 m² = €2,907** (Co-Op ~€22-25/m² = cheaper option). Boards: `KD_board.jpg`, vision `KD_mood_v2.png` (shutters+fridge), `TWO_ROOMS_prices.jpg`, `ISLAND_compare.jpg`.

**💶 FINANCE, FULL LOAN PROPOSAL DONE (the big new thing).** King is borrowing from **Palmerstown Credit Union**. Read his real loan chat (claude.ai share link) via **Playwright browser** (WebFetch returned blank, JS page; Playwright `browser_navigate` + `browser_evaluate(()=>document.body.innerText)` rendered it). **Key real facts:**
- **Palmerstown rate = 7.99% (8.29% APR)** for loans €10k, €75k (his €30k sits in this band). Existing PCU loan **€4,493.83 left @ 10.4%, €160/mo** (consolidate/top-up into new loan → old payment stops).
- **Income €4,400/mo net** (engineer) + freelance (excluded = conservative). **Rent €0** (lives with parents, mum covers rent, the key to affordability). **Living spend ~€1,500/mo** (food/fuel via credit card cleared in full). **€2,000 CU shares = collateral** (frozen, not spendable). Fixed costs: gym €99 + WiFi €55 + insurance €197 + road tax €56.50 + electric €100 = €507.50.
- BNPL to clear before applying: **Very ~€457** (arrears), **Klarna ~€299** (in collection). Credit card opened Mar 2026, cleared full monthly.
- **FINAL PLAN (King chose option B = every room new):** loan **€30,794 @ 7.99% / 24 mo = ~€1,393/mo** = €24,000 home + €2,300 car (work-critical) + €4,494 old-loan top-up. **Cash-flow surplus ~€999.50/mo** (salary only). **Caught a double-count in King's own draft** (he listed the old €160 loan AND the new loan, old one is folded in, so it stops → surplus is bigger).
- **Proposal doc for the loan officer:** `deliverables\showhome\LOAN_PROPOSAL.jpg`. Full finance detail in `deliverables\cost_tracker.md` (FINAL LOAN PLAN section).

**⚠️ BUDGET TENSION (flag for next room):** €24k home − foundation €8k − living €4.6k − kitchen/dining €5.7k = **only ~€5,680 left for 3 beds + bath + WC + hall + utility.** That won't fully furnish every bedroom NEW. As we design the bedrooms: reuse furniture the family already has where possible, OR the €24k home figure flexes up (loan can take it, surplus is healthy). Be honest about this per room.

**NEXT:** design the **bedrooms** (King said "show me next room" → start MASTER). Have real frames: `deliverables\walkthrough\floored_up\bedroom1/2/3.jpg` (wood floor) + `upstairs_real\` + show-home stills `sh_28s/34s/38s.jpg`. Method = real products + show-home vibe + cost board (NO AI room renders, King fatigued by those). Bedrooms have sloped/vaulted ceilings + Velux/dormer, plan around eaves; check for built-in wardrobes.

## ✅ 2026-06-20 (evening) · FLOOR PRODUCT LOCKED + COSTED + AI-LIMIT NAMED + SHOW-HOME METHOD FOUND
- **FLOOR LOCKED:** **Canadia "Annalee Oak"** 12mm AC5 water-resistant laminate, 147×1216mm, pack 1.83 m², **€31.95/m²** (Tallaght, Springfield shop). Josh emailed the real shop-tag photo (`IMG_2521.png` → clean swatch `deliverables\flooring_previews\MATERIAL_josh_real.jpg`). Whole house ~100 m² = **~€3,200**.
- **FOUNDATION BUDGET (cost_tracker.md):** **~€8,290 projected vs €15k target / €20k ceiling.** Saving flagged: same-spec Canadia 12mm AC5 ~€22, 25/m² at **Co-Op Superstores** (could cut floor ~€700, 900).
- **🛑 NAMED THE AI LIMIT (King caught it):** generative AI **redraws the WHOLE room** every render → "floor only" is never truly only the floor → looks like slop + the outside/window view changes + rooms inconsistent. **Stop faking floor-only on real photos with AI.** Full lesson + the manual-composite recipe → [[reference-floor-swap-ai-limit-showhome-method]].
- **Built a TRUE floor-only MANUAL composite** (PIL perspective + floor mask + real-lighting transfer, no cv2): `deliverables\walkthrough\manual_living.jpg` + 3-way `COMPARE_methods.jpg` (real | AI | manual). Keeps the real room 100%; floor reads flat. Recommended a **free sample board** as the truly-accurate route.
- **🔑 BREAKTHROUGH, SHOW-HOME METHOD:** King's inspiration video = the **Aderig show home (#55), his EXACT house type, fully designed.** Watched it (Gemini) → extracted whole-house design (greige walls · light oak floor · white units · accents **mustard/sage-green/brass/matte-black** · contemporary cosy + luxury = his brief). Per-room stills `deliverables\showhome\sh_*.jpg` (hall 12s · living 54s · kitchen 14/16s · dining 18s · understairs bench 20s · bathroom 26s · bedroom 28s · master 34s · sage bedroom 38s).
- **Built the LIVING ROOM design board** `deliverables\showhome\BOARD_living.jpg` = his real room beside the SAME room designed + products/cost (~€1,608 decor). **This is the method to draw out the whole house** (real room | designed show-home room | plan). No AI faking.
- **Floors done on real frames + made CONSISTENT** (floors only, walls unchanged): downstairs `floored\` (hall/living/kitchen/openplan/boiler/understairs, hall stairs left bare) + `floored_up\bedroom1/2/3`.
- **Delivered the living-room VISION render** `deliverables\showhome\VISION_living.jpg` (AI mood, flagged as vision): grey sofa + mustard/cream cushions, brass globe chandelier, cream rug, gold mirror, pale oak, terrace doors. **Awaiting King's tweaks** (sofa colour, accent colour, walls, rug/table) → redo to his taste → roll his style through the whole house.
- **⚠️ DESIGN-SOURCE RULE (King, 20:30):** the **utility/boiler room is NOT in the show-home inspiration video** → design it from **King's OWN footage** (`deliverables\walkthrough\empty_real\boiler_room.jpg`), not the show home. Same for any room the show home doesn't cover (WC, under-stairs): use his real frames. Show home covers: hall, living, kitchen, dining, under-stairs bench, bathroom, 3 bedrooms, NOT utility/WC.

## ✅ 2026-06-20 (afternoon) · DOWNSTAIRS FLOORED + APPROVED + GROUND-FLOOR LAYOUT CONFIRMED
- **King APPROVED the pale-oak floor ("im happy")** on: 3 bedrooms + kitchen + open-plan kitchen/dining + living/window room. All rendered on **CLEAN empty-walkthrough frames** (no clutter -> accurate) via `gemini_render.py --ref <empty_frame> --ref TARGET_pale_oak_josh.jpg`. Delivered to phone each time (email 3 inboxes + ntfy). Renders in `deliverables\walkthrough\img\` (bed1/2/3_floored, gf_openplan_floored, gf_window_floored, kitchen_designed).
- **METHOD THAT WORKED (reuse):** floor on the **empty-walkthrough's clutter-free frames** (`references\_walkthrough\_gf_frames\` t15/t20/t24, `kitchen_empty.jpg`), NOT the new move-in clips (packed with boxes -> floor hidden). Combine: empty frames for the render + new videos for room IDs.
- **GROUND-FLOOR LAYOUT CONFIRMED by King** -> `deliverables\walkthrough\GROUND_FLOOR_layout.md`. Split-level townhouse #7: street -> external steps up -> shared terrace (#7+#5, bike store, heat-pump, patio doors) -> **hall (front door #7 + stairs UP to 3 beds/bath)**; from hall an **open door -> LIVING ROOM** and a **closed door -> KITCHEN**, both flow into the **back open-plan kitchen/dining** (patio doors); + **WC** (tiled, sun-tunnel - stays tiled), **utility/boiler room** off kitchen, **under-stairs store**. Downstairs floor = one dark laminate -> replaced with pale oak. (NOTE: this supersedes the old "kitchen = street-window room, living = terrace-doors room" line in the warning above.)
- **VIDEO RESCUE (reusable):** King's 3 walkthrough clips formed one walk (outside -> living -> full inside, ~4:44). **iCloud shared-link upload STALLED 3+ hrs** (pauses when phone locks / leaves Photos; `share.icloud.com/photos/<token>` = CloudKit `/icloudlinks/`, sharedstreams API 404s, only the live web viewer renders status). **WIN = Josh emailed the same clips as Google Drive links -> downloadable** (King's OWN Drive copies were LOGIN-LOCKED; Josh's were link-accessible). Big Drive files hit the "virus-scan warning" interstitial -> `.tmp\gdrive_dl.py` parses the confirm form + downloads. Then ffmpeg -> 720p -> `tools\watch_video.py` (Gemini) for the room-by-room read. Files in `references\_walkthrough\_oneshot\`.
- **NEXT:** do the **hall + stairs** the same way (clean frames) to finish the ground-floor set -> then **cost the floor** (pale-oak SPC ~€3,000 + stairs) + the foundation budget / cash-flow loan. King may send an upstairs walk if needed.

## 📥 MEDIA RECEIVED + SITE ANALYSED (2026-06-19, phone session)
King sent **4 files: floor plan + empty-house walkthrough + 2 finished-look inspiration videos.** Full read-out: **`knowledge\7adderig_farm\MEDIA_INVENTORY.md`**; target aesthetic distilled in **`knowledge\7adderig_farm\INSPIRATION_LOOK.md`**. (Cloud-readable mirror, `floorplan.png` + all contact sheets live there; the video originals stay on the laptop, blocked from the brain by `.gitignore`.) **Read BOTH at the start of every `/fitout`.**
- 🎯 **FINISHED-LOOK TARGET (King's 2 refs):** warm greige walls · light-oak wood floors · existing white handleless kitchen · **mustard + charcoal accents** · mocha/sage feature walls · brass globe lighting · upholstered headboards, modern cosy minimalist + touch of luxury. **Ref A is a show home in the SAME "Aderig" development** (closest possible match); Ref B (Evara duplex) confirms the same palette. Go room by room, "change a few things", guide not copy.

Key findings that change scope:
- **House is handed over at builder-finish, NOT a bare shell.** Already in: **kitchen** (white handleless gloss units + extractor), **all wet rooms tiled + sanitaryware** (WC, main bath = bath+toilet, ensuite basin), **upstairs bedrooms carpeted** (neutral beige). So kitchen + bathrooms + WC + ensuite = **refresh/style rooms, not full builds**, adjust subtotals.
- **Open decisions to lock early:** ground-floor flooring (currently bare grey screed in hall/living/kitchen-dining) + **staircase finish** (bare untreated pine treads, white balustrade).
- **Upstairs bedrooms have sloped/vaulted ceilings + Velux + dormer windows** (top-floor under-roof rooms). Always plan bedroom layouts around the slopes/eaves.
- ⚠️ **ENSUITE DISCREPANCY, ask King:** plan + video both show an **ensuite off Bedroom 1**, but the rule says "NO ensuite for Bedroom 1." Resolve before designing the master/bathrooms.
- ⚠️ Plan shows **2 rooms not in the 11-room list: Bicycle Storage** (off terrace) + the **Ensuite**. Reconcile the `/fitout` room list.

> ✅ Media done: real videos pulled from Gmail + filed; `floorplan.png` + `floorplan.jpeg` in root; brain mirror in `.claude\knowledge\7adderig_farm\`.

## 🟢 FOUNDATION PHASE · King's working model (2026-06-19/20) · READ THIS
King reframed the project into **TWO PHASES** (decor/inspiration parked for later):
- **Phase 1 = FOUNDATION (now):** finish the house essentials, flooring/varnishing, blinds, curtain poles, appliances. **A handyman does the labour** (fixed quote); **King sources the parts**, room by room, off the floor plan + empty-house video. Build the 3D walkthrough on this.
- **Phase 2 = DIY / decor (later):** furniture, styling, the showhome look, extra cost, room by room. Inspiration videos parked for here.
- **BUDGET: €15,000 target / €20,000 ceiling.** Live budget = `deliverables\cost_tracker.md`.

### Locked decisions
- **Whole-house flooring = ONE floor everywhere, 91 m²** (~100 m² to buy). Colour = **PALE WASHED / SCANDI OAK** (Josh's pick, ref `deliverables\flooring_previews\TARGET_pale_oak_josh.jpg`), lighter/cooler than Royale "Light Oak" (too honey). SPC/LVT waterproof, **~€3,000**. Exact in-stock SKU still to source (Royale pale shades sold out → Wood Floor Warehouse "Stranmillis/Nordic Oak" type, ~€25, 34/m²).
- **Stairs = Style B** (oak treads + white risers, clad in the same SPC). Est ~€400 material + labour TBD.
- **Bedrooms get the new floor too** (builder carpet lifted). **WC + Main Bathroom STAY TILED.** **Ensuite NOT designed** (rule stands). **Bicycle Storage added → 12 rooms.**
- **Handyman labour = €2,330 FIXED** (kitchen/living/hall/utility/3 beds flooring+varnish, blinds ×5 @€50, poles ×5 @€30, cooker €120, washer €30, dryer €30). Stairs labour TBD 2026-06-20. → Foundation so far ≈ **€5,730** + stairs labour.

### 3D WALKTHROUGH · method locked after 3 attempts (IMPORTANT)
- ❌ **AI equirectangular panoramas (Pannellum) = REJECTED.** They invent geometry that does NOT match the floor plan ("where are the doors and rooms?"). **Do NOT loop AI image-gen for an EXACT layout, it guesses every time.** (`walkthrough\index.html` = old panorama tour, superseded.)
- ✅ **Walkable 3D built FROM the floor plan** = `deliverables\walkthrough\house.html` (Three.js r128, first-person). **WHOLE HOUSE, both floors, all rooms**, floor toggle (⬆/⬇), top-down dollhouse view (▣), minimap + live room labels. **LIVE: walkthrough-six-mu.vercel.app/house.html.** Exact layout; clean architectural look (NOT photoreal) = the trade for exactness. Geometry = the `F0`/`F1` data objects (easy to nudge a wall/door).
- ✅ **Truly-exact + photoreal = a PHONE SCAN** (Polycam/Scaniverse) King does once the house is clear / floor laid → turn into a real walk-anywhere model. Guide: `deliverables\walkthrough\HOW_TO_SCAN.md` (emailed). **A shaky 2D phone video CANNOT be auto-converted to 3D**, needs a deliberate scan.

### Tools built this session (`.claude\tools\`)
- `gemini_render.py`, Gemini 3 Pro Image with **reference-image input** + `--equirect`. Renders match a real room photo. (Sibling of gemini_image.py.)
- `extract_room_frames.py`, evenly-spaced stills from a room video (ffmpeg).
- Emails to Josh (`joshagbidi6@gmail.com`, NOT his iCloud, it's full/bouncing) + King via Gmail SMTP (`GMAIL_APP_PASSWORD`). Send scripts in `7 adderig farm\.tmp\`.

## What it is
Full interior fit-out of an empty **3-bed, two-floor Dublin townhouse** for a **family of four** (2 parents + 2 **adult sons**, 20 & 24, their rooms = adult spaces). Modern · cosy · minimalist + touch of luxury + eclectic character. **Real, currently-available Irish/EU products with real € prices.** Done **one room at a time**, building to a **costed master shopping list + 3D walkthrough render** so the family sees the exact total spend. Source of truth = `MASTER_PROMPT.md` (King's brief, copied into the folder from `Downloads\interior-design-master-prompt.md`).

## WAT chain
- **W:** `workflow\fitout_sop.md`, per-room loop: read `decisions.md`+floorplan+refs → 2-3 line direction summary → thumbs-up → full room spec (§4) → lock to `decisions.md` → render brief → next room.
- **A:** Claude as senior interior designer / FF&E specialist.
- **T:** read `floorplan.jpeg` + `references\<room>\` pics + **WebSearch** for real € prices; later 3D renders feed global `tools\gemini_image.py` / KIE (keys in `.env.master`), no new keys.
- **S:** **`/fitout [room]`**, registered globally in `.claude\commands\fitout.md`. No arg = next "not started" room.

## Standing rules (baked into the project CLAUDE.md)
Warm-greige base walls (Dulux Egyptian Cotton / F&B Elephant's Breath, one shade darker than builder white, TBC vs sample) · flooring decided **per room** (wood/wood-effect + carpet + LVT/tile in wet rooms, cohesive tones) · **NO ensuite for Bedroom 1** · one cohesive palette varied per room · sons' rooms = adult · real available products + real € prices only · always flag **splurge vs save** · currency € · **auto-decide threshold €150** (under = decide + log assumption; at/over or structural = stop & ask).

## State files
- `decisions.md`, the running ledger, **read at the start of every session** (palette row, 11-room floor table, locked-pieces table, assumptions log, threshold €150, GRAND TOTAL). Append after each room; keep the total in sync with `deliverables\master_shopping_list.md`.
- `rooms\`, one spec per room (template `_TEMPLATE_room_spec.md`).
- `deliverables\`, master_shopping_list · global_palette_board · mood_boards · render_briefs · phasing (stubs, filled as rooms lock).
- `references\<room>\`, 11 room subfolders for King's mood/palette pics.

## NEXT (2026-06-20)
1. **King confirms the 3D layouts match his house** (open `house.html`, hit ▣ Top view, both floors). Nudge any wrong wall/door in the `F0`/`F1` data in `house.html` → redeploy (`vercel --prod --yes` in `deliverables\walkthrough\`, re-aliases `walkthrough-six-mu.vercel.app`).
2. **Source the exact in-stock pale-oak SPC** SKU + final price → lock into `cost_tracker.md`.
3. **Firm up stairs cost** (handyman measuring 2026-06-20) → add material + labour to `cost_tracker.md`.
4. Source remaining foundation parts: **blinds ×5, curtain poles ×5, cooker/washer/dryer units**.
5. Phase 2 (decor/furniture) comes later, inspiration parked. **Polycam scan = the photoreal-exact walkthrough** once the floor's laid.

Defaults King can change anytime: skill `/fitout`, threshold €150. Note: original "one room per session /fitout design" flow is now subordinate to the foundation-first model above.

## 🖥️➡️ DESKTOP · DO THIS FIRST (planted by phone session 2026-06-20)
King wants the desktop Claude to pick up the walkthrough work + his new house video. Steps:
1. **Pull the phone-session work:** `git fetch origin claude/house-walkthrough-design-d3rxl3`,
   copy the `knowledge\7adderig_farm\walkthrough\` folder from that branch into the project,
   read `walkthrough\README_empty_to_designed.md`.
2. **King's one-shot whole-house video (4:44):**
   **https://share.icloud.com/photos/0e0HAFwiLbB8U2gRhmeq3XjhQ**
   Download it → watch with Gemini → pull ONE clean, well-lit still per room →
   save as `walkthrough\img\<room>_empty.jpg`.
3. **Use BOTH videos** (this one-shot + the empty walkthrough) to pick the best frame per room
   AND confirm each room's walls/windows/doors before any render. Start with the living room.
4. Render each designed view ON the real empty frame (`gemini_render.py --ref`, corrected prompt
   in the README, keep real geometry, only ADD design) → drop into the `ROOMS` array in
   `empty_to_designed.html` → QA with King until approved → deploy.

## 🎬 2026-06-20 (phone session) · KING'S WALKTHROUGH VISION LOCKED: "EMPTY → DESIGNED"
King watched a real empty-house walkthrough and said: *"I should be able to see every part of my house
EMPTY, and then it fills out as we design, maybe I should change some prompt for it."* This is the right
instinct AND it fixes the geometry problem. **He chose all 3 delivery layers.**
- **THE METHOD / PROMPT FIX:** never generate a room from scratch, **anchor every render to King's REAL
  empty frame** and prompt "keep the exact walls/windows/doors/shape, ONLY add the design." (Proven once:
  `deliverables\renders\living_real_floor_v1.jpg`.) Full corrected prompt template + build steps in the
  new **`knowledge\7adderig_farm\walkthrough\README_empty_to_designed.md`**.
- **BUILT THIS SESSION (cloud/brain repo):** `knowledge\7adderig_farm\walkthrough\empty_to_designed.html`,   a before/after drag-slider page (NOW ⇆ DESIGNED) per room + a "X of 12 rooms designed" progress bar +
  ground/upper floor filter. The empty house shows now; each room's card auto-flips to a live slider the
  moment its `designed:` image is filled in. **Laptop just drops in one rendered designed image per room.**
- **3 layers (all chosen):** (1) this before/after page [build first] · (2) add an empty↔designed toggle to
  `house.html` · (3) Polycam photoreal scan once the house is clear + floor laid (parked).
- **NEXT on laptop:** watch King's new single-shot whole-house video (Gemini), extract one clean empty
  still per room → `walkthrough\img\<room>_empty.jpg`, render each designed view with `gemini_render.py
  --ref`, wire into the HTML, deploy. QA-until-King-approves per room. (Couldn't watch the .mp4 or render
  in the cloud session, no ffmpeg/keys; concept + page + prompt prepared instead.)

## 🛑 2026-06-20 (laptop session) · QA-until-approved rule + layout pause
- 🆕 **King's standing QA rule:** QA isn't done until he approves, keep sending until he's satisfied. → [[feedback-qa-until-king-approves]].
- ⚠️ This laptop session (unaware of the phone session's walkthrough work) RE-RAN AI living-room renders and hit the SAME problem already locked above: **AI image-gen guesses geometry → "way wrong."** Reinforced: **do NOT loop AI renders for exact layout**, use `house.html` + a phone scan.
- 🆕 Created **`LAYOUT_TRUTH.md`** (project root) = per-room geometry QA tracker; lock each room ✅ before finish/furniture.
- ✅ **Room IDs confirmed by King:** big **street-window room = KITCHEN** (not living room); **living room = the terrace-doors room**; **utility** near the kitchen. Real frames at `references\living-room\_realframes\` (t8, t20).
- ⏸️ **King will send a single-shot whole-house video in a few hours** → use it to verify/correct `house.html` geometry (NEXT item 1) + map rooms in `LAYOUT_TRUTH.md`.
- Provisional/Phase-2 only: foundation palette §1 in `decisions.md` (greige · white trim · brass+black) + `global_palette_board.md` + a Living Room furniture spec `rooms\living-room.md` (€1,578, **layout unverified, revisit after the video**). Preview site `previewsite-theta.vercel.app` (made public via Vercel API `ssoProtection:null`).
