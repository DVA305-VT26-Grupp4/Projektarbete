# Projektarbete - SDXL VAE

## Frågeställning
Hur påverkas den uppmätta bildkvaliteten och filstorleken när SDXL:s latenta rymd 
komprimeras med AVIF i jämförelse med PNG samt en okomprimerad referens.

## Metod 
Vi väljer 20 bilder från [Flickr 8k Dataset](https://github.com/awsaf49/flickr-dataset) (eller alternativt [The Kodak Lossless True Color Image Suite](https://github.com/MohamedBakrAli/Kodak-Lossless-True-Color-Image-Suite)).

Bilderna konverteras med SDXL:s VAE (madebyollin/sdxl-vae-fp16-fix ) för att omvandla 
varje bild till dess latenta rymd, exempelvis 128x128x4@f32 om bilden är 1024x1024xRGB (HxWxC). 

Istället för flyttal kvantifierar vi värderna som heltal med 8/10/12/16 bitar och sparar
som vanligt bildformat (RGBA) inför nästa steg.

Bilddatan komprimeras med PNG respektive AVIF i tre olika kvalitetslägen, låg/medel/hög (vilket ger
olika filstorlekar). AVIF väljs då detta format stödjer fyra kanaler (RGBA), till skillnad från JPG (RGB).

Slutligen återskapas varje latent representation från de komprimerade filerna och omvandlas tillbaka med
samma VAE till en RGB‑bild.

Vi mäter skillnaden uttryckt i PSNR och SSIM mellan den ursprungliga bilden och varje rekonstruktion och jämför dessa med respektive filstorlek.


## Länkar/Referenser
### PSNR/SSIM
[Image Quality Metrics: PSNR vs. SSIM](https://ieeexplore.ieee.org/document/5596999)

### VAE
[![Demo video](https://img.youtube.com/vi/ywYuZrLENH0/hqdefault.jpg)](https://www.youtube.com/watch?v=ywYuZrLENH0&t=3s)
[![Demo video](https://img.youtube.com/vi/9NgC0sh9Msc/hqdefault.jpg)](https://www.youtube.com/watch?v=9NgC0sh9Msc)

