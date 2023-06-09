# Videographia

## Felvétel 

* Golden hour, szép színek, árnyékos kép.
* Nap az alany mögött.

* Key light, full light, back light. Rembrandt-háromszög.

* Shutter speed minél gyorsabb.
* Aperture egy stoppal a maximális fölött, a lencseélesség miatt.

* Manual mód plusz auto ISO.
* Videó: 4k, 25 fps, 1/50 sec. shutter speed, ND filter, log format (Sony SLog-3), -0,7 ... -1 EV.
* Tripod, sosem kézből.

## Kompozíció

* Rule of thirds.
* Vezető vonalak.
* Establishing shot, master shot, kivezető shot.
* B-roll.

## Vágás

* Cut on action, match cut.
* L-cut (ALT gomb)
  * a B-rollra,
  * insert shotra,
  * párbeszéd **első** mindatára (kvázi odafordul az ember figyelme).
* J-cut (ALT gomb) a párbeszédben **további** ide-oda váltogatásnál, néha akkor is, ha a másik ember nem is szólal meg (kvázi elvárja az ember a választ).
* Smash cut, hangosról másik, halk jelenetre. Határeset: vágás ütemre.
* Match cut.
* Jump cut az idő telésének felgyorsítására.
* Van lassítás (retime) optikal flow hatással.
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

* Color Management: `Davinci YRGB Color Managed`.
  * Clipek csoportosítása: klipek kijelölése, `Add to Current (New) Group`.
    * Pre (első pötty): SLog3 --> Davinci Color Managed.
    * Klipenként (második pötty): amit kell.
    * Post (hatmadik pötty): Davinci Color Managed --> Rec-709.
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

