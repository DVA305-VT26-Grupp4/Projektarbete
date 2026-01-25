# Projektarbete - SDXL VAE

## Frågeställning
Hur påverkas den uppmätta bildkvaliteten och filstorleken när SDXL:s Latenta rymd 
komprimeras med AVIF i jämförelse med PNG samt en okomprimerad referens.

## Metod 
Vi väljer slumpat urval av bilder från [Flickr 8k Dataset](https://github.com/awsaf49/flickr-dataset) eller [The Kodak Lossless True Color Image Suite](https://github.com/MohamedBakrAli/Kodak-Lossless-True-Color-Image-Suite)

Bilderna konverteras med SDXL:s VAE (madebyollin/sdxl-vae-fp16-fix ) för att omvandla 
varje bild till dess “latent space”, dvs 128x128x4 (float32).

Istället för flyttal approximerar vi värderna (“pixlarna” i kanalerna) med 8 bitar (int8) och sparar
som en vanlig bild (RGBA).

Därefter komprimeras den bilden med ~~JPEG~~ AVIF respektive PNG i tre olika kvalitetslägen (vilket ger
olika filstorlekar).

Slutligen återskapas varje latent bild från de komprimerade filerna och omvandlas tillbaka med
samma VAE till en RGB‑bild.

Vi tar mäter skillnaden med PSNR och SSIM mellan den ursprungliga bilden och varje rekonstruktion och jämför dessa med filstorleken.



## Youtube-länkar
[![Demo video](https://img.youtube.com/vi/ywYuZrLENH0/hqdefault.jpg)](https://www.youtube.com/watch?v=ywYuZrLENH0&t=3s)
