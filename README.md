# Videographia

## Felvétel 

* Golden hour, szép színek, árnyékos kép.
* Nap az alany mögött.
* Key light (főfény), fill light (derítőfény), back light (díszítő- vagy élfény). Rembrandt-háromszög. Kontraszt-arány: 4:1 - 8:1.
* Smart side vs. dumb side.
* Állókép:
  * Shutter speed: **`1/100`** sec vagy gyorsabb. Ökölszabály: `1 / (2 × fókusztávolság[mm, @35mm])` sec.
  * RAW-ban is mentsük.
  * Aperture egy stoppal a maximális fölött, a lencseélesség miatt: pl. ha max. aperture = 2.8, akkor 3.5 vagy magasabb.
  * **Manual mód plusz auto ISO**, én állítom a shutter speedet és az aperture-t.
* Videó: 
  * felbontás: 4k UHD (3840 × 2160),
  * 25 (vagy 24) fps, 1/50 (vagy 1/48) sec. shutter speed (180˚),
  * Expozíció:
    * HLG-nél +0,7 ... +1 EV,
    * Rec.709-nél -0,7 ... -1 EV,
    * Natív ISO és ND filter, ha túl világos,
  * Log format:
    * **HLG3**: jobb dinamika (+0,7 EV!),
    * HLG2: jó kompromisszum,
    * HLG1: jobb zajelnyomás.
* Tripodról, állványról, **sosem kézből**.
* Hangot mindig külön kell felvenni (Zoom F2, LMF-2), később, hullámforma alapján szikronizálni.

### Sorrend (WASEF)

#### Global

1. Resolution
1. Frame rate
1. Color mode

#### Local

1. White balance
1. Aperture
1. Shutter speed
1. Exposition (ISO = `auto`, ND filter)
1. Focus

## Kompozíció

* Rule of thirds.
* Vezető vonalak.
* Shotok minden jelenethez (scene):
  * WIDE: establishing shot,
  * WIDE: master shot, amiben bemutatjuk a főszereplőt,
  * MEDIUM-tól CLOSE-UP-ig: ahogy halad a sztori és megismerődnek a szereplők,
  * INSERT: valami specifikusra,
  * WIDE: kivezető shot.
* B-roll.

## DaVinci Resolve Settings

`DaVinci Resolve` --> `Preferences`:
* `User`:
  * `Project Save and Load`:
    * `Live save`: be,
    * `Project backups`: be,
    * `Timeline backups`: be.
  * `Editing`:
    * `New Timeline Settings` --> `Start timecode`: `00:00:00`, különben elcsúszik a felirat (subtitle).
* `DaVinci Resolve` --> `Keyboard mapping`: [keymap](Davinci%20Resolve%20Keymap.txt)
* Dual screen: `Workspace` --> `Video Clean Feed`: a másik monitor.
* `Log` táblázat: `Clip Name`, `Input Color Space`, `Proxy`, `Scene`, `Shot`, `Good Take`, `Date Modified`.

## Project Settings

* Color Management: `Davinci YRGB Color Managed`.
* `File` --> `Project Settings` --> `Master Settings` --> `Frame Interpolation` --> `Retime Process`: `Optical flow`. Ezzel a beállítással bármikor lehet slow motion-t csinálni Retime Curve-vel. A `Motion estimation mode`-ot lehet állítani, finomhangolni.
* `Timeline` --> `Selection Follows Playhead`: vágásnál fontos, hogy mindig az éppen aktuálisan látott klipet vágjuk.
* `Playback` --> `Render Cache` --> `Smart`.
* Proxy:
  * `File` --> `Project Settings` --> `Master Settings`:
    * `Proxy media resolution` és `Optimized media resolution`:
      * 1080p HD: Half,
      * 4k UHD: Quarter.
    * `Proxy media format`, `Optimized media format` és `Render cache format`: `DNxHR`:
      * **SQ**: standard quality (etherneten),
      * LB: low bandwidth (pl. Wifin).
* Audio target level: 
  * `File` --> `Project Settings` --> `Fairlight` --> `Target loudness level`: -14 dB LUFS.

## Vágás

* `Generate Proxy Media`.
* `Stabilize`, a legjobb eredményt a `Planar Tracker` adja.
* Crop: `Transform` --> `Zoom` és `Position`.
* Van lassítás, gyursítás (retime) optikal flow hatással:
  * `Retime Control`,
  * `Retime Curve`: `ALT`-tal lehet keyframe-et hozzáadni,
* Kamera mozgatása: 4k UHD széles kép és a `Zoomm` + `Transform`-mal kameramozgatás.
* **Multicam**:
  * Media Poolban kijelölöm a klipeket,
  * `Create New Multicam Clip Using Selected Clips`,
  * Feljövő ablakban: `Angle Sync`: `Sound`.

### Vágások

* Cut on action, vagy egy kicsit utána.
* Vágás ütemre, zenére.
* Insert shot, B-rollra.
* L-cut (`ALT` gomb: a vágást a kép- vagy hangsávon lehet ida-oda mozgatni):
  * a B-rollra,
  * insert shotra,
  * párbeszéd **első** mindatára: kvázi odafordul az ember figyelme.
* J-cut:
  *  a párbeszédben **további** ide-oda váltogatásnál: kvázi várja az ember a választ, 
  *  néha akkor is, ha a másik ember nem is szólal meg, csak az érzelmet mutatjuk,
* Jump cut: az idő telésének felgyorsítására.
* Match cut.
* Smash cut, hangosról másik, halk jelenetre.

## FX

* Stabilizálás
  * `Planar Tracker`-rel:
    * ha van planar transform node, a planar trackert le lehet törölni, a transform node-ban megvan a mozgatási infó.
  * ~(pont) `Tracker`-rel~.
* Effektekre (pl. szöveg mozgatás) motion blur.
* `Planar Tracker`-rel valamit oda lehet tenni, ami követ, pl. eget.
* Ég lecserélése.
* `Keyframe Stretcher`.

## Színezés

Pipeline:
* Group Pre-Clip:
  * `Color Space Transform` effekt
* Clip (külön node-okon):
  * Általános:
    * Temporal NR (`Motion Effects` tab)
    * Expozíció: `Offset`, `Gain`,
    * `White Balance`, `Tint` (ld. vector scope: WB-ra merőlegesen mozgat),
    * `Contrast`, `Gamma`, S-görbe,
    * `Saturation`,
  * Stílizálás (ha lehet, egymással párhuzamos node-okon):
    * árnyékok ciánozása,
    * ég kékítése,
    * extra fények stb.
  * Motion blur (`Motion Effects` tab),
  * Élesítés (`Blur` tab),
  * `Film Grain` effekt.
* Group Post-Clip:
  * `Color Space Transform` effekt.

### Globális beállítások

* Clipek csoportosítása: klipek kijelölése, `Add to Current (New) Group`.
  * Pre (első pötty): `Rec.2020`+`HGL3` --> `DaVinci Wide Gamut` + `DaVinci Intermediate`.
  * Klipenként (második pötty): amit kell.
  * Post (harmadik pötty): `DaVinci Wide Gamut` + `DaVinci Intermediate` --> `Rec-709`+`Rec-709-A`.
* Zajeltávolítás (`Motion Effects`):
  * temporal, 
  * majd esetleg spatial.
* Égszín kiemelése (`Curves` --> `Hue vs Sat`), vagy ki lehet cserélni.
* Motion blur (`Motion Effects`) rossz klipre.
* Ciánozás a színpókhálóval (`Color Warper`), különösen az árnyékokat (shadows).
* Van `Gallery` a bal felső sarokban, oda lehet menteni:
  * állóképeket (still),
  * színezés fázisait, ami később össze lehet hasonlítani előtte-utána nézetben,
  * projektek között átvihető color gradingeket: `Power Grades`.
* A kontraszt S-t tesz a görbébe, a `Pivot` az S-t mozgatja világos-sötét tengelyen.
* Az árnyékos részeket el lehet tolni cián irányba:
  * `Color Wheels` --> `Log Wheels` --> `Shadows`-t kell cián irányba állítani.
  * Az `↑ Rng` és `↓ Rng` beállítja az "árnyék" tartományt.
* Lehet a végén `Vignette`-t adni a filmre.

### Lokális grading

* `Window`-ban kijelölt részt lehet külön trackeltetni: `Tracker` --> `Window`.
* Nagy ellipszis ablakkal irányított fényt lehet hozzáadni, mintha pl. az ablakon jönne be, de a `Relight` valószínűleg jobb.
* `Qualifier`-rel lehet bizonyos színeket, tónusokat kijelölni.

## Hang

* **Voice Isolation**.
* `Analyze Audio Levels`, `Normalize Audio Levels`: `ITU-R BS.1770-4` értékek:
  * YouTube: -14 dB LUFS,
  * TikTok: -13 dB ... -15 dB LUFS.
* Hangot jelalak alapján szinkronizálni:
  * A **Media Poolban** kijelölni az összes videót-hangot,
  * Jobb gomb --> `Auto Sync Audio` --> `Based on Waveform` vagy `Based on Waveform and Append Tracks` (ha kell a régi hang is),
  * A DaVinci Resolve így kicseréli az eredeti hangot a jó imnőségű külsőre. Ha mégis kell az eredeti: Timeline-on jobb klikk a clipen --> `Clip Attributes` --> `Audio` tab. A `Linked Channel` a jó minőségű, kicserélt.
* Audio layerek (`Timeline` --> `Layered Audio Editing`), ezek közül csak a legfelső hallatszik.
* ALT + kattingás a hangerő vonalon = audio keyframes.
* A Lavalier mikrofon elég steril hangot ad, lehet rá kis zengést adni `Reverb` pluginnel, és a magasat kicsit kiemelni, közepet elnyomni equalizerrel.
* **Zene vége**:
  * Megvágni a zenét az `Edit` page-en, hogy egy dobütés még benne legyen.
  * Másolatot készíteni az utolsó dobütésről, áttenni új trackre.
  * Új tracket compound clippé konvertálni (jobb gomb --> `New Compound Clip`).
  * Meghosszabbítani a compound clipet, hogy legyen hely a zengésnek:
    * Megnyitni a compound clipet: jobb gomb --> `Open in Timeline`,
    * a benne levő zenét lemásolni,
    * meghosszabbítani a másolatot,
    * némítani: `Mute [M]`.
  * Meghosszabbítani a compount clipet az *eredeti* timeline-on,
  * Rátenni egy `Reverb` effektet (70 m² körüli terem), hogy amikor az utolsót üti a dobos, kicsit visszhangozzon, és úgy érjen véget.
* ADR.

### Lavalier mikrofonhoz az equalizer

`Band 1` aluláteresztő szűrővel 
* +20 dB erősítés,
* Q minél kisebb,
* 50 Hz ... 250 Hz közötti törésponti frekvenciát megkeresni, ahol még éppen nincs dobozhang (mostani mikrofonnal: 90 Hz).

## Export

* H.265, HVEC:
  * 17-18 = optikai lossless.
  * 26 = default.
  * ± 6 a méretben kettes szorzó.
  * Rate Control: `Constant Bitrate`.
  * Video bitrate:
    * 2160p (4K):	35–45 Mbps,
    * 1080p:	8 Mbps,
    * 720p:	5 Mbps.
  * Audio bitrate:
    * Mono:	128 kbps,
    * Stereo:	384 kbps.

### HDR10+ REC.2020 ST.2084 (PQ)

Project szinten és/vagy timeline szinten állítsd be (`Color` tab):

* `Color science`: `DaVinci YRGB Color Managed`,
* `Automatic color management`: off,
* `Color Processing Mode`: `HDR DaVinci Wide Gamut Intermediate`,
* `Use separate color space and gamma`: on,
* `Color Space`: `Rec.2020`, `Gamma Tag`: `Rec.2100 ST.2084`,
* `Output color space`: `Rec.2020`, (gamma) `Rec.2100 ST.2084`,
* `HDR mastering is for "500" nits.`, vagy amennyi a kijelző ([Samsung TV](https://www.rtings.com/tv/reviews/samsung/q60-q60t-qled): 446 nits, Xiaomi 11: 500 nits)
* `Mastering display`: `1000-nit, BT.2020, D65, ST2084, full`,
* `Enable HDR10+`: on, `Enable HDR Vivid`: on, `Enable Dolby Vision`: off,
* Exportálás:
  * `Data Levels`: `Full`.
  * H.265:
    * `MP4` container, `Main10` profile, a lenti videó bitrate-eket 20%-kal meg kell emelni.
    * Embeddáljuk a HDR10+ és a HDR Vivid metadatát.
  * DNxHR:
    * `Format`: `QuickTime`, `Codec`: `DNxHR`, `Type`: `DNxHR HQX 10-bit`.

YouTube-on nagyon sokat kell várni a HDR10+ konverzióra.
