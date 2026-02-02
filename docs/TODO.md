## TODO

- [ ] 1. **Bestäm dataset** (Flickr8k *eller* Kodak) - skriv en avgränsning varför. 
- [ ] 2. **Ta bort Hypotes** (flytta vissa delar till inledningstext?). 
- [ ] 3. **Frågeställningen** byt ut mot mätbara indikatorer.
- [ ] 4. **Inledning** - hitta vetenskapliga källor eller ta bort påståenden.
- [ ] 5. **Metoden**: - behöver skriva ut parametrar (PNG level, AVIF quality/ev lossless), kvantiseringsformel, seed för urval. 

## Föreslag på upplägg
1. **Inledning**
- [x] Nuvarande beskrivning (varför latent-kompression är intressant ML-pipeline, lagring, throughput etc).
- [ ] Kort syfte: “vi undersöker om …”
- [ ] Avslutas med frågeställning?

3. **Bakgrund**
- [ ] VAE & latent representation (Stable diffusion?, SDXL).
- [ ] Bildkomprimering: vad PNG/AVIF gör (på konceptnivå).
- [ ] Kvalitetsmått: PSNR/SSIM (kort + varför just dessa).
- [ ] Relaterad forskning.

4. **Avgränsningar**
- [ ] Endast SDXs VAE (madebyollin/sdxl-vae-fp16-fix ), endast stillbilder, endast PNG/AVIF, endast vissa bitdjup, viss upplösning, osv.
- [ ] Vad vi inte undersöker (t.ex. ingen träning, inga andra codecs, inga humanstudier).

5. **Metod**
Beskrvining av experimentdesignen. Variabler och kontroller som ex:
- [ ] codec, bitdjup, AVIF-quality, ev PNG-level
- [ ] filstorlek/bitrate, PSNR, SSIM
- [ ] OBS! Kontrollera att exvis samma VAE, samma preprocess, samma bildurval
- [ ] Diagram av "pipelinen" + exakt hur kvantisering görs (ex skala/offset, clipping, per-bild vs global normalisering).
- [ ] Dataval: Exakt hur vi väljer 20 bilder (slump med seed, eller motiverat urval etc ).

6. **Referenser**
- [ ] Peer-review
