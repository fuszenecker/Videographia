# Videographia

## Felvétel 

* Golden hour, szép színek, árnyékos kép.
* Nap az alany mögött.
* Key light, fill light, back light. Rembrandt-háromszög.
* Shutter speed: **1/100** vagy gyorsabb.
* Aperture egy stoppal a maximális fölött, a lencseélesség miatt (ha max. aperture = 2.8, akkor 3.5 vagy magasabb).
* **Manual mód plusz auto ISO**, én állítom a shutter speedet és az aperture-t.
* Videó: 
  * felbontás: 4k UHD (3840 × 2160),
  * 25 (vagy 24) fps, 1/50 sec. shutter speed,
  * Expozíció: -0,7 ... -1 EV,
    * ND filter, ha túl világos,
  * log format (Sony SLog-3),
* Tripodról, állványról, **sosem kézből**.

## Kompozíció

* Rule of thirds.
* Vezető vonalak.
* Shotok:
  * Establishing shot,
  * (master shot),
  * kivezető shot.
* B-roll.

## Project Settings

* Color Management: `Davinci YRGB Color Managed`.
* `Frame Interpolation` --> `Retime Process`: `Optical flow`.

## Vágás

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
* Kamera mozgatása: 4k széles kép és a Dinamic Zoommal kameramozgatás.

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

## Hang

* `Analyze Audio Levels` / `Normalize Audio Levels`
  * `ITU-R BS.177044`
    * YouTube: -14 dB LUFS.
    * TikTok: -13-15 dB LUFS.
* Audio layerek (`Timeline` --> `Layered Audio Editing`).
* ALT + kattingás a hangerő vonalon = audio keyframes.
* ADR.

#$ Export

* H.265
  * 17 = optikai lossless,
  * 28 = default,
  * +/- 6 a méretben kettes szorzó.

