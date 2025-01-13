---
title: Web Flash-tool
description: Firmware Web Installer
---

<style>
  .md-content__button {
    display: none;
  }
  .pick-variant select {
    background: transparent;
    width: 300px;
    padding: 1px;
    font-size: 16pt;
    border: 1px solid #ddd;
    height: 51px;
    border-radius: 15px;
  }
  .invisible {
    visibility: hidden;
  }
  .radios li {
    list-style: none;
    line-height: 2em;
  }
</style>

# "Web Flash-tool

Flash of vind je apparaat met de volgende opties:

1. Sluit je ESP32 aan op een USB-poort.
2. Klik op "Installeren" en selecteer de juiste COM-poort.
3. Krijg de OpenDTU-firmware geïnstalleerd en verbonden in minder dan 3 minuten!

<p>Selecteer je product</p>
<ul class="radios">
<li>
    <label><input type="radio" name="type" value="luxmeter" /> luxmeter</label>
    ![](../images/images/bh1750.webp)
<li>
    <label><input type="radio" name="type" value="vindriktning" /> vindriktning met wemos d1 mini</label>
    ![](../images/vindriktning.avif)
</li>
<li>
    <label><input type="radio" name="type" value="bluetoothproxy" /> bluetoothproxy</label>
    ![](../images/icon_ORmG5v707-GcOoCIPLAKEq_wCuuxqAQTUNtc3z23ufw=.png)
    
</li>
</ul>
<p class="button-row" align="center">
<esp-web-install-button class="invisible">
  <button slot="activate" class="md-button md-button--primary">INSTALL</button>
  <span slot="unsupported">Use Chrome Desktop</span>
  <span slot="not-allowed">Not allowed to use this on HTTP!</span>
</esp-web-install-button>
</p>

Powered by [ESP Web Tools](https://esphome.github.io/esp-web-tools/){target=_blank}

<script>
    document.querySelectorAll('input[name="type"]').forEach(radio =>
    radio.addEventListener("change", () => {
        const button = document.querySelector('esp-web-install-button');
        button.manifest = `../files/manifest_${radio.value}.json`;
        button.classList.remove('invisible');
    }
    ));
</script>
<script type="module" src="https://unpkg.com/esp-web-tools@8.0.1/dist/web/install-button.js?module"></script>

## Probleemoplossing

* Het kan nodig zijn om handmatig de bootloader-modus in te voeren
  voordat je probeert de ESP te flashen met de WebFlasher.
* Probeer de `BOOT`-knop op je bord ingedrukt te houden totdat je ziet dat de WebFlasher 
  het flashgeheugen aan het wissen is en daadwerkelijk de firmware installeert. Dit kan helpen 
  wanneer een reset wordt uitgevoerd in de voorbereidingsstap, omdat het ingedrukt houden van de 
  `BOOT`-knop ervoor zorgt dat de ESP32 opnieuw opstart in de bootloader-modus.