# Projektarbete - SDXL VAE

## Frågeställning 1
Vilken krypteringsalgoritm (AES vs RSA) är mest effektiv för att säkra
dataöverföring utan att orsaka hög latens?
## Metod 1
Genom implementering av ett skript (i Python) kan variablerna isoleras för att
säkerställa ett tillförlitligt resultat. Hårdvaran och filinnehållet hålls konstanta
under hela testprocessen medan endast algoritmen och filstorleken
manipuleras. Varje enskilt test utförs 10 gånger för att generera ett
genomsnittligt värde och minimera felmarginaler orsakade av
bakgrundsprocesser i datorn.

---

## Frågeställning 2
Hur påverkas den återgivna bildkvaliteten när SDXL:s latenta rum (latent space)
komprimeras med JPEG (lossy) jämfört med PNG (lossless) vid olika filstorlekar?

## Metod 2
Vi väljer slumpat urval av bilder från Flickr 8k Dataset. Bilderna konverteras med SDXL:s VAE
(madebyollin/sdxl-vae-fp16-fix ) för att omvandla varje bild till dess “latent space”, dvs 128x128x4
(float32).
Istället för flyttal approximerar vi värderna (“pixlarna” i kanalerna) med 8 bitar (int8) och sparar
som en vanlig bild (RGBA).
Därefter komprimeras den bilden med JPEG respektive PNG i tre olika kvalitetslägen (vilket ger
olika filstorlekar).
Slutligen återskapas varje latent bild från de komprimerade filerna och omvandlas tillbaka med
samma VAE till en RGB‑bild.
Vi tar skillnaden mellan den ursprungliga bilden och varje rekonstruktion och samlar även in
filstorlekarna.
