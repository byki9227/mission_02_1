# 4. 미해결 기록

프롬프트를 여러 차례 수정·개선해도 끝내 텍스트 프롬프트만으로는 원하는 결과를 얻지 못한 과업 2건을 기록합니다.

---

## [미해결 1] FPV 드론의 5단계 연속 시네마틱 영상 생성 (이륙 → 호버링 → 선회 → 정렬 → 출격)

* **시도한 프롬프트 원문:**

```markdown
G01 — Intro 6s — hangar lift, hover, yaw to exit, sortie
Save as: raw-assets/video/intro/intro_hangar_launch.mp4
Type: video/mp4
Suggested duration: 6s
Beat sheet (for Flow Omni 1.1 Flash):
Lift-off (~0.8–1.0s) — rotors spool, lead Falcon rises a short distance off the hangar deck
Hover hold (~0.8–1.0s) — stable hover in place, nose still facing trench depth / camera
Hover-yaw to exit (~1.8–2.2s) — while hovering, yaw-rotate so the front FPV camera / nose turns to face the hangar exit (sortie doorway)
Brief aligned hover (~0.4–0.6s) — pause facing the exit
Fly-out sortie (~1.6–2.0s) — accelerate straight through the hangar exit into open battlefield sky
Notes: Do not blast straight out immediately. Must show lift → hover → yaw-to-exit → short aligned hover → exit fly-out. Continuous single-shot feel. Supporting drones idle on deck or light hover in background.
===== FLOW PROMPT (COPY ALL BELOW) =====
[COMMON]
Project: FPV Hunter cinematic cutscene (MP4).
Art style: Semi-realistic cell shading 3D game art, reality 60% cartoon 40%, Valorant-like clean material bands, readable military silhouette, subtle ink outline on hero subject, no photoreal skin pores, high clarity for mobile game, crisp edges, game-ready asset look, tactical military atmosphere, semi-realistic cell shading environments.
Technical: duration about 6 seconds, cinematic but readable, no letterbox bars preferred (full frame), no on-screen text, no logos.
Tone: tense focused FPV strike fantasy, not horror gore.
Mandatory beat order: (1) lift-off (2) stable hover (3) hover-yaw so nose/FPV camera faces hangar exit (4) short hover facing exit (5) accelerate through exit into open sky.

[NEGATIVE PROMPT]
photorealistic CGI skin, muddy blur, low resolution, watermark, logo text, UI chrome overlay, subtitle burn-in, extra limbs, deformed propellers, random floating text, NSFW, gore closeup faces, child characters, busy cluttered background noise, lens dirt covering subject, overexposed bloom, purple neon cyberpunk city, anime chibi proportions, UI HUD, crosshair overlay, watermark, modern skyscraper city, extreme gore, real-world political flags, real nation insignia, news broadcast look, instant rocket blast launch, no hover, no yaw turn, flying out without rotating, teleport cut, whip-pan chaos, flipping upside-down, spinning out of control, sudden jump cuts, reverse direction confusion

[SCENE]
Dark hangar trench tunnel interior, multiple FPV drones spooling on the deck, cyan LED rings, dusty volumetric light shafts, clearly readable hangar exit doorway as the sortie departure axis with open battlefield sky visible through that exit

[ACTION]
Lead Falcon FPV drone spools propellers and lifts off a short distance, then holds a clear stable hover. While still hovering, it yaw-rotates in place so its front nose and FPV camera aim toward the hangar exit doorway. After a brief aligned hover facing that exit, it accelerates forward through the hangar exit and departs into open battlefield sky as a controlled tactical sortie. Supporting drones remain mostly grounded or idle-hovering in the background. Do not blast out immediately; the hover and yaw-to-exit must be readable.

[VIEW]
Continuous single-shot feel, start inside hangar on the lead Falcon, keep the drone centered and readable during lift, hover, and yaw, then track it through the hangar exit into a wide outside sky; full frame 16:9; camera path stable and clear

[QUALITY]
Stable camera path, clear subject focus, readable hover and yaw rotation toward hangar exit, dramatic but clean lighting, game-cinematic finish.
===== END =====
```

* **받은 결과 요약:**
  위 프롬프트를 Flow의 `Omni 1.2 Flash`에서 실행하면 드론이 정지 상태에서 호버링과 선회(Yaw) 과정을 건너뛰고 곧바로 밖으로 튀어나가 버리는 영상만 반복 생성되었습니다. 또한 네거티브 프롬프트에 로켓 분사 금지를 명시했음에도 로터에서 불꽃·로켓 분사가 나오는 오류가 계속 발생했습니다.

* **막힌 이유 (직접 작성):**
  6초짜리 단일 컷 안에 `이륙 → 제자리 호버링 → 출구 방향 선회 → 잠시 정지 → 출격`이라는 5단계 시간 순서와 방향 전환을 텍스트 프롬프트만으로 제어하려 했으나, 모델이 '출격(sortie)' 키워드에 과도하게 반응해 중간 호버링과 회전 단계를 생략하고 로켓처럼 발사해 버리는 한계가 반복되었습니다. "클래식한 드론의 로터 움직임만으로 표현하라", "1m 위에서 스크린 반대 방향으로 턴하는 호버링을 절대로 생략하지 말라" 등 수차례 프롬프트를 고쳐도 일관된 재현이 불가능해, 텍스트 프롬프트만으로 자동 생성하는 과업은 미해결로 남겼습니다.

---

## [미해결 2] 8프로펠러 중량 드론(Titan)의 에어브레이크(Airbrake) 회피 모션 클립 생성

* **시도한 프롬프트 원문:**

```markdown
H_titan_dodge_brake — Titan — dodge_brake
Save as: raw-assets/motion/drones/titan/titan_dodge_brake.mp4
Type: motion/mp4
Suggested duration: 2s
Notes: classic nose-up airbrake; no thruster jets
===== FLOW PROMPT (COPY ALL BELOW) =====
[COMMON]
Project: FPV Hunter motion clip for game (MP4). Target generator: Flow Omni 1.2 Flash.
Art style: Semi-realistic cell shading 3D game art, reality 60% cartoon 40%, Valorant-like clean material bands, readable military silhouette, subtle ink outline on hero subject, no photoreal skin pores, high clarity for mobile game, crisp edges, game-ready asset look.
Background: pure chroma key green screen (#00FF00 flat), even lighting, no shadows on screen, subject fully inside frame.
Technical: loop-friendly motion, stable framing, no camera whip unless specified, 24–30 fps feel, duration about 2 seconds.
No text, no HUD, no watermark. Subject keeps consistent design across frames.
Propulsion lock: classic electric multirotor ONLY. All thrust from spinning propellers. No flame jets, rocket boosters, afterburners, or thruster nozzles. Grey/black smoke trails are allowed when useful; fire is not.
Omni 1.2 moderation: keep motion controlled and readable — moderate amplitude only, no wild exaggeration, no acrobatic flips unless this clip is crash_spin, bank/pitch angles stay within about 15–30 degrees, stay fully inside frame, no morphing parts, no camera whip.

[NEGATIVE PROMPT]
photorealistic CGI skin, muddy blur, low resolution, watermark, logo text, UI chrome overlay, subtitle burn-in, extra limbs, deformed propellers, random floating text, NSFW, gore closeup faces, child characters, busy cluttered background noise, lens dirt covering subject, overexposed bloom, purple neon cyberpunk city, anime chibi proportions, ground plane, environment background, studio softbox stands, tripod, people, flames, fire jets, blue fire, orange fire, sprouting flames, jet exhaust, rocket plume, afterburner, thruster blast, nozzle flame, plasma booster, missile flame trail, firework burst, cartoon fire boost, top thruster jets, reverse thrusters, flame brake

[SUBJECT]
heavy coaxial octocopter FPV bomber drone Titan, gunmetal grey armor plates, yellow hazard stripes, thick arms, dual battery packs, 8 lifting propellers, heavy bomb bay for 8 bombs, fortress-like bulky silhouette — pure propeller craft, no jet engines

[ACTION]
Classic multirotor AIRBRAKE — rotor thrust only.
Beat 1: true side profile with slight forward lean, propellers spinning, no FX fire.
Beat 2: sudden flare — nose pitches UP ~15–25°, body decelerates (brief settle/back-slide feel). Optional faint grey dust/smoke OK. No orange/blue thruster flames from top or rear.
Beat 3: nose levels, recover near start pose for loop.
Motion should complete a clear cycle and end near the start pose for looping when possible.

[VIEW]
locked true side profile (left-to-right); pitch change readable; keep fully inside frame

[QUALITY]
Readable silhouette, propellers/rotors visibly spinning with motion blur discs, cel-shaded materials stay consistent, no morphing parts, zero fire.
===== END =====
```

* **받은 결과 요약:**
  드론이 지상의 적(NPC) 공격을 피하기 위해 공중에서 기수를 15~25도 들어 올리며 급제동(Airbrake)하는 '멈칫' 동작을 전혀 만들어내지 못했습니다. 프로펠러 회전만으로 급제동하는 물리적 자세 변화 대신 제자리에 떠 있거나 의도와 다른 부자연스러운 움직임만 반복되었습니다.

* **막힌 이유 (직접 작성):**
  수십 번에 걸쳐 각도(`15~25°`), 측면 시점 고정(`locked true side profile`), 불꽃·역추진 제트 금지 조건을 상세히 넣어 프롬프트를 수정했으나, 모델이 텍스트 설명만으로는 멀티로터 특유의 '기수 들기(Nose-up) 급제동' 물리 동작을 이해하지 못했습니다. 결국 텍스트 프롬프트 개선을 중단하고 다른 드론의 Airbrake 레퍼런스 모션 영상을 별도로 참조시키는 우회 방식을 써야 했기 때문에, 프롬프트만으로 해결하는 과업으로서는 실패한 것으로 판단해 미해결 기록으로 남겼습니다.