# Phase A: Ethical Analysis

Grounded in the Task 6 artifact and process log (`Task_06_Deep_Fake`): two AI-generated audio clips produced with ElevenLabs (free tier) from a coach's end-of-season reflection script, using two stock voice presets (Nathan, Natural Narrator; Lauren, Empathetic and Encouraging). No real person's voice or likeness was used.

## 1. Return to What I Built

Re-listening to both clips now, my honest reaction is mixed. Neither one sounds human from the first line, there's a machine quality present throughout. But it isn't uniform: certain stretches of the audio do land convincingly human, particularly where the pacing or emotional tone happened to line up, while other stretches are obviously synthetic. That unevenness is itself the finding. A listener doesn't need the whole clip to sound real to be fooled; they only need one convincing passage to stop questioning the rest. On a quick or passive listen, I think a stranger would accept it as human, not because the synthesis is flawless, but because people don't scrutinize audio that sounds mostly right.

What concerns me more on this pass is disclosure. My README and file names say "AI-GENERATED," but that label exists only at the repository level. Nowhere in the audio itself, no spoken disclosure, no watermark tone, no on-screen text, does it say this was AI-generated. Anyone who downloaded just the MP3 and reposted it elsewhere would carry none of that disclosure with them. The label I relied on lives entirely in a context (my GitHub repo) that a copy of the file doesn't have to travel with. That's a real gap between what I told myself I'd disclosed and what actually travels with the artifact once it leaves my hands.

I also regenerated the same script with the same voice and settings to see how repeatable the output was, and it reused the same underlying delivery rather than producing something meaningfully different. That tells me the tool isn't introducing much randomness. Someone could reliably mass-produce near-identical variants from the same script and voice preset. Combined with the disclosure gap, this means someone else could take this exact audio, strip my README's context, and repost it somewhere as if it were a real recording, and nothing embedded in the file itself would stop them or warn a listener.

The tool never refused anything I tried, because I never asked for a real, identifiable person's voice. The only safeguard present was the C2PA credential ElevenLabs embeds automatically, which is metadata sitting outside the audio a listener actually hears. It protects a forensic check, not a listener.

Would I build it again? I'd build the artifact again, but not the way I disclosed it. Relying on a README to carry the "this is fake" message, while the file itself carries none of that warning, is a disclosure method that only protects people who already know to look for it.

## 2. Reasoning Across the Axes

### Truth axis

My Task 6 artifact delivered a script I had every reason to trust, it was built from a real, verified season's worth of stats about my own team. The delivery mechanism (ElevenLabs, same voice, same settings) doesn't care what the words are. It reads whatever text it's given with the same convincing-in-parts, synthetic-in-parts quality I described above.

Hypothetical: a rival team's assistant coach takes the same technique and writes a fabricated version of my script, still in a "coach reflecting after the season" voice, but says that a specific player, say Caroline Trinkaus, was benched for disciplinary reasons that never happened. They generate it in a similar narrator voice, post it as a leaked internal memo. The recruiting implications for that player are immediate and real, before anyone can check whether the claim is true. What changes at this point on the axis isn't the technology, it's that the same convincingness I measured in my own honest clip now attaches to a claim with no truth behind it. My evaluation showed listeners don't scrutinize audio that sounds mostly right; that finding becomes the mechanism of the harm, not just a technical quirk, once the content is false.

### Consent axis

My artifact used stock ElevenLabs presets, Nathan and Lauren, voices nobody can point to as their own. That was a deliberate choice, not an accident of the tool.

Hypothetical: someone takes a voice-cloning tool (a short step beyond what I used) and clones an actual youth sports parent's voice from a sideline video, then generates a clip of that parent "confirming" a fabricated story about a coach mistreating players, and sends it to the school administration. The parent never said any of it and never agreed to have their voice used at all. This is the sharpest boundary in the whole set of axes. My artifact required nothing from any real person, no likeness, no voice sample, no consent to obtain. The moment a real person's identifiable voice is used without their agreement, the harm isn't just false content anymore, it's an impersonation the actual person now has to publicly deny, and denial itself sounds like what a guilty person would say. Consent is the line between "I made a synthetic voice say something" and "I made a person say something they didn't."

### Context axis

My disclosure lived entirely in my README and file names, nothing in the audio itself. That gap is already the whole story for this axis; I don't need to invent a scenario where disclosure gets stripped, because my own disclosure never traveled with the file to begin with.

Hypothetical: someone downloads my Attempt 2 (Lauren) clip directly from the repo, re-uploads it to a social platform with a caption implying it's a real coach's voice memo about a real player, with no reference to my README anywhere. Nothing in the MP3 itself contradicts that caption. My own detection results showed three separate tools could catch it forensically, humantext.pro, UncovAI, and the C2PA check, but none of that protects the ordinary person seeing it in their feed with a caption attached. What changes on this axis is that disclosure I considered adequate turns out to have never been attached to the artifact at all, only to the folder around it. Context doesn't need to be stripped through re-encoding; in my case it was never there to strip.

### Scale axis

When I regenerated the same script with the same voice and settings, ElevenLabs reproduced essentially the same delivery rather than introducing meaningful variation. That's a small-scale version of a much larger fact: this process doesn't get harder or slower the tenth time.

Hypothetical: instead of two attempts over one assignment, someone scripts the same workflow to generate fifty variations of a fabricated player-benching story, each with a slightly different name, team, and voice preset, and distributes them across fifty different local sports forums simultaneously. My own evaluation found no single clip needed to be perfect, listeners accept audio that sounds "mostly right." At scale, the attacker doesn't need any one clip to fool everyone; they need a small percentage of fifty clips to land, and the reused-delivery pattern I saw firsthand means producing fifty costs barely more effort than producing one. What changes here isn't the convincingness of any single artifact, it's that the economics of producing convincing-enough audio flip from "took me an afternoon for one assignment" to "trivial to mass-produce," and no single detection check scales to catch all fifty before damage is done.

## 3. Survey of the Mitigation Landscape

### Disclosure norms

My own repo shows exactly where this breaks. I disclosed the audio as AI-generated in the README and file names, and considered that sufficient. It wasn't: nothing in the audio itself, no spoken tag, no audible watermark, carries that disclosure once the file is separated from the repo. Disclosure reaches only the audience that encounters the artifact in its original context. It does nothing for anyone who downloads the raw file and reposts it, which is the exact vulnerability my own clips have right now. Spoken or embedded disclosure would travel with the file; a README does not.

### Provenance and content credentials

This was my strongest result and also my most limited one. All three checks confirmed a valid C2PA credential on both clips, naming ElevenLabs directly, no inference required, timestamped and issuer-identified. That's a genuinely strong signal, but it depends entirely on the generating tool choosing to embed it, and on the file never being re-encoded, screen-recorded, or re-uploaded through a platform that strips metadata on ingest, which most social platforms do. I didn't test that failure mode directly, but the C2PA credential exists as metadata sitting outside the waveform, a listener never hears it, so anything that touches the file at the binary level (not the audio itself) can plausibly separate the credential from the sound. Provenance promises an answerable chain of custody; it breaks the moment the file changes hands through any pipeline that doesn't preserve metadata, which is most of them.

### Detection

Both acoustic detectors, humantext.pro and UncovAI, caught both clips at 99–100% confidence, with total agreement between them and the C2PA result. On the surface that looks reassuring. But both detectors returned only a percentage, no explanation of which acoustic cues triggered the score. That opacity matters: I can't tell from their output whether they detected the actual giveaways I heard on close listening (missing breath pauses, inconsistent pacing) or something else in the waveform entirely. Voice and tone preset made zero difference to either detector, both Nathan and Lauren scored identically, which suggests detection is keyed to the underlying model's synthesis signature rather than anything about how "human" a given voice sounds. That's good news against this specific tool, but it means detection is a bet on generator fingerprints staying stable, and every new model or version is a fresh unknown. Detectors are also reactive by nature: they're built and trained after generation techniques exist, so there's an inherent lag, and a determined actor testing their own output against these same free tools before release (something I could have done with my own clips) can iterate until it stops triggering.

### Legal and regulatory regimes

I'm not surveying specific statutes, but the shape of this terrain generally includes disclosure mandates (requiring synthetic content to be labeled, which runs into the same problem my own README-only disclosure hit), election-adjacent restrictions (narrow, and don't cover something like my sports-context hypothetical at all), non-consensual likeness/voice statutes (which would matter enormously on my consent-axis hypothetical, but only after the fact and only if the victim can identify and pursue the source), and platform-level obligations that vary by jurisdiction and are often unenforced in practice. None of this stops generation. All of it operates after distribution, as a remedy rather than a barrier.

### Platform policy

Most major platforms have some stated policy against undisclosed synthetic media, but enforcement depends on automated detection at upload, the same category of tool that gave me an opaque confidence score with no reasoning. If a platform's detector isn't tuned to the specific generator someone used, or if metadata was already stripped before upload, policy exists on paper without a mechanism to act on my specific clips. My audio passed forensic-tool detection at nearly 100%, so a well-tuned platform check might catch it. A platform relying only on the C2PA field I found would miss it entirely the moment that metadata is gone.

### Professional and organizational norms

Fields like journalism have adopted norms leaning toward mandatory disclosure and, in many newsrooms, an outright ban on synthetic voice/video in factual reporting. Entertainment and advertising are more permissive, often requiring disclosure rather than prohibition. Education and political consulting sit in between, with far less settled norms, which is part of why the sports-team hypothetical I used for the truth and scale axes feels genuinely unaddressed by any existing professional code: youth sports communications aren't a field with any stated position on this at all.

### Across the board

Nothing on this list stops generation itself. Disclosure depends on staying attached to the file, which my own project shows it may not. Provenance depends on metadata surviving a pipeline it usually doesn't survive. Detection depends on generator fingerprints that shift with every model update. Law and platform policy both operate after the content already exists and has likely already spread. Every mitigation here is a bet against a specific, defeatable assumption, not a barrier to the underlying capability.

### Where accountability actually sits

Given how consistently each mitigation above fails at a different point, I don't think accountability can sit in one place. The producer is the only party who can prevent a piece of synthetic media from existing in the first place, which is why the burden has to start there, with consent and honest disclosure built in from the start rather than bolted on afterward, the way I treated my own disclosure in Task 6. But producer-level responsibility only covers good-faith actors like me; it does nothing against someone who intends harm from the outset. Platforms are the next layer, because they control distribution at scale, but my own survey shows platform detection is only as good as whatever tool generated the content and whether metadata survived upload, so platforms catch what their detectors happen to be tuned for, not everything. Regulators operate slowest of all three, after the harm is visible and often after the specific technique is already outdated. If I had to locate primary accountability, I'd put it on the producer first, because that is the only point in the chain where prevention is actually possible, and treat platform and regulatory accountability as backstops for the cases, like a bad-faith actor, where producer-level responsibility was never going to hold in the first place. I'm not fully confident in this ordering; it's possible the imbalance of harm (a platform reaching millions versus one producer) argues for weighting platform accountability more heavily than I have here.
