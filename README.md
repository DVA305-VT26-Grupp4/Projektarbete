# Projektarbete - SDXL VAE

## Frågeställning
Hur påverkas den uppmätta bildkvaliteten och filstorleken när SDXL:s latenta rymd 
komprimeras med AVIF i jämförelse med PNG samt en okomprimerad referens.

## Metod 
Vi väljer slumpat urval av bilder från [Flickr 8k Dataset](https://github.com/awsaf49/flickr-dataset) eller [The Kodak Lossless True Color Image Suite](https://github.com/MohamedBakrAli/Kodak-Lossless-True-Color-Image-Suite)

Bilderna konverteras med SDXL:s VAE (madebyollin/sdxl-vae-fp16-fix ) för att omvandla 
varje bild till dess latenta rymd, dvs 128x128x4@f32 om bilden är 1024x1024x3.

Istället för flyttal kvantifierar vi värderna (“pixlarna” i kanalerna) med 8 bitar (uint8) och sparar
som vanligt bildformat (RGBA) inför nästa steg.

Därefter komprimeras datan med ~~JPEG~~ AVIF respektive PNG i tre olika kvalitetslägen (vilket ger
olika filstorlekar). AVIF väljs då detta format stödjer fyra kanaler (RGBA), till skillnad från JPG (RGB).

Slutligen återskapas varje latent representation från de komprimerade filerna och omvandlas tillbaka med
samma VAE till en RGB‑bild.

Vi tar mäter skillnaden mätt i PSNR och SSIM mellan den ursprungliga bilden och varje rekonstruktion och jämför dessa med filstorleken.



## Youtube-länkar
[![Demo video](https://img.youtube.com/vi/ywYuZrLENH0/hqdefault.jpg)](https://www.youtube.com/watch?v=ywYuZrLENH0&t=3s)
