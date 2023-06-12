# Videographia

## Felvétel 

* Golden hour, szép színek, árnyékos kép.
* Nap az alany mögött.
* Key light, fill light, back light. Rembrandt-háromszög.
* Állókép:
  * Shutter speed: **1/100** vagy gyorsabb. Ökölszabály: `1 / fókusztávolság[mm, @35mm]`.
  * RAW-ban is mentsük.
  * Aperture egy stoppal a maximális fölött, a lencseélesség miatt: pl. ha max. aperture = 2.8, akkor 3.5 vagy magasabb.
  * **Manual mód plusz auto ISO**, én állítom a shutter speedet és az aperture-t.
* Videó: 
  * felbontás: 4k UHD (3840 × 2160),
  * 25 (vagy 24) fps, 1/50 sec. shutter speed,
  * Expozíció: -0,7 ... -1 EV,
    * ND filter, ha túl világos,
  * log format (Sony SLog-3),
* Tripodról, állványról, **sosem kézből**.
* Hangot mindig külön kell felvenni (Zoom F2, LMF-2), később, hullámforma alapján szikronizálni.

## Kompozíció

* Rule of thirds.
* Vezető vonalak.
* Shotok:
  * (establishing shot),
  * master shot, amiben bemutatjuk a főszereplőt,
  * kivezető shot.
* B-roll.

## DaVinci Resolve Settings

`DaVinci Resolve` --> `Preferences`:
* `User`:
  * `Project Save and Load`:
    * `Live save`: be
    * `Project backups`: be
    * `Timeline backups`: be
  * `Editing`:
    * `New Timeline Settings` --> `Start timecode`: `00:00:00`, különben elcsúszik a felirat (subtitle). 

## Project Settings

* Color Management: `Davinci YRGB Color Managed`.
* `File` --> `Project Settings` --> `Master Settings` --> `Frame Interpolation` --> `Retime Process`: `Optical flow`. Ezzel a beállítással bármikor lehet slow motion-t csinálni Retime Curve-vel. A `Motion estimation mode`-ot lehet állítani, finomhangolni.
* `Timeline` --> `Selection Follows Playhead`: vágásnál fontos, hogy mindig az éppen aktuálisan látott klipet vágjuk.
* `Playback` --> `Render Cache` --> `Smart`.
* Proxy:
  * `File` --> `Project Settings` --> `Master Settings`:
    * `Proxy media resolution` és `Optimized media resolution`:
      * 1080p HD: Half
      * 4k UHD: Quarter
    * `Proxy media format`, `Optimized media format` és `Render cache format`: `DNxHR` valamenyik.
* Audio target level: 
  * `File` --> `Project Settings` --> `Fairlight` --> `Target loudness level`: -14 dB LUFS.

## Vágás

* `Generate Proxy Media`.
* Cut on action,
* Match cut.
* ALT gomb: a vágást a kép- vagy hangsávon lehet ida-oda mozgatni
  * L-cut:
    * a B-rollra,
    * insert shotra,
    * párbeszéd **első** mindatára: kvázi odafordul az ember figyelme.
  * J-cut:
    *  a párbeszédben **további** ide-oda váltogatásnál: kvázi várja az ember a választ, 
    *  néha akkor is, ha a másik ember nem is szólal meg, csak az érzelmet mutatjuk,
* Smash cut, hangosról másik, halk jelenetre. 
* Vágás ütemre, zenére.
* Jump cut: az idő telésének felgyorsítására.
* Van lassítás, gyursítás (retime) optikal flow hatással:
  * `Retime Control`,
  * `Retime Curve`: ALT-tal lehet keyframe-et hozzáadni,
* Kamera mozgatása: 4k UHD széles kép és a `Zoomm` + `Transform`-mal kameramozgatás.

## FX

* Stabilizálás
  * Planar trackerrel:
    * ha van planar transform node, a planar trackert le lehet törölni, a transform node-ban megvan a mozgatási infó.
  * ~ (pont) Trackerrel~.
* Effektekre (pl. szöveg mozgatás), motion blur.
* Planar trackerrel valamit odaehet tenni, ami követ, pl. eget.
* Ég lecserélése.

## Színezés

* Clipek csoportosítása: klipek kijelölése, `Add to Current (New) Group`.
  * Pre (első pötty): `Sony S-Gamut3`+`S-Log3` --> `DaVinci Wide Gamut` + `DaVinci Intermediate`.
  * Klipenként (második pötty): amit kell.
  * Post (hatmadik pötty): `DaVinci Wide Gamut` + `DaVinci Intermediate` --> `Rec-709`+`Rec-709-A`.
* Zajeltávolítás (`Motion Effects`):
  * temporal, 
  * majd esetleg spatial.
* Égszín kiemelése (`Curves` --> `Hue vs Sat`).
* Motion blur (`Motion Effects`) rossz klipre.
* Ciánozás a színpókhálóval (`Color Warper`).
* Van `Gallery` a bal felső sarokban, oda lehet menteni:
  * állóképeket (still),
  * színezés fázisait, ami később össze lehet hasonlítani előtte-utána nézetben.
* A kontraszt S-t tesz a görbébe, a `Pivot` az S-t mozgatja világos-sötét tengelyen.
* Az árnyékos részeket el lehet tolni cián irányba:
  * `Color Wheels` --> `Log Wheels` --> `Shadows`-t kell cián irányba állítani.
  * Az `↑ Rng` és `↓ Rng` beállítja az "árnyék" tartományt.
* Lehet a végén `Vignette`-t adni a filmre.

## Hang

* **Voice Isolation**.
* `Analyze Audio Levels`, `Normalize Audio Levels`: `ITU-R BS.177044` értékek:
  * YouTube: -14 dB LUFS.
  * TikTok: -13-15 dB LUFS.
* Hangot jelalak alapján szinkronizálni.
* Audio layerek (`Timeline` --> `Layered Audio Editing`), ezek közül csak a legfelső hallatszik.
* ALT + kattingás a hangerő vonalon = audio keyframes.
* A Lavalier mikrofon elég steril hangot ad, lehet rá kis zengést adni `Reverb` pluginnel, és a magasat kicsit kiemelni, közepet elnyomni equalizerrel.
* **Zene vége**:
  * Megvágni a zenét, hogy egy dobütés még benne legyen.
  * Másolatot készíteni az utolsó dobütésről, áttenni új trackre.
  * Új tracket compound clippé konvertálni (`Create New`).
  * Meghosszabbítani a compound clipet, hogy legyen hely a zengésnek:
    * Megnyitni a compound clipet,
    * a benne levő zenét lemásolni.
    * meghosszabbítani a másolatot.
    * némítani.
  * Rátenni egy `Reverb` effektet, hogy amikor az utolsót üti a dobos, kicsit visszhangozzon, és úgy érjen véget.
* ADR.

## Export

* H.265, HVEC:
  * 17-18 = optikai lossless,
  * 26-28 = default,
  * ± 6 a méretben kettes szorzó.
  * Rate Control: Constant Bitrate
  * Video bitrate: 
    * 2160p (4K):	35–45 Mbps,
    * 1080p	8 Mbps,
    * 720p	5 Mbps.
  * Audio bitrate:
    * Mono:	128 kbps,
    * Stereo:	384 kbps.
