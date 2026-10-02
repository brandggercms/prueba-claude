# Diagnóstico de cardinaltulum.com (2 oct 2026)

Leído con acceso de red completo: home, `/villas-for-sale/` (EN y ES) y `/financing-options/`. No leí Instagram/Facebook (piden login) ni el resto de páginas (about, location, contact, blog).

## Lo que hay
- **Estructura:** WordPress + Elementor. Menú: Home, About us, Amenities and typologies, Location, Financing options, Blog, Contact + botón "villas for sale". Versión ES en `/es/`. Pie: "Developed by Brandgger" y "Bancorp".
- **`/villas-for-sale/`:** hero ("A limited collection of villas in Selva Zama · 15 private residences ready for final customization · Get Brochure & Pricelist"), cifras (15 villas · 3 a 4 recámaras · 787K precio inicial · Mortgage), y secciones 01 Location, 02 The residences ("Personalize Your Home. Delivered in 90 Days", dos paquetes de acabados), 03 Typologies (Type A 3 rec. 274 m², "starting at $787K"; Type B 4 rec. 288 m², "starting at $833K"), 04 Amenities, 05 Beach & Cenote, 06 Certified Investment Security (financiamiento), 07 Request Information ("Secure your residence. Only a select number of residences remain... Our team responds within 24 hours"). Subnavegación con anclas: Location, Residences, Typologies, Amenities, Safe investment, Inquire.
- **Captura:** un formulario de GoHighLevel/LeadConnector (iframe `SjDKiqRzjazTG2oynV6J`) en la sección final, botón "Get Brochure & Pricelist" y widget de WhatsApp (Joinchat: "I need more information!").
- **Medición:** Google Tag Manager `GTM-WS99TH8K`, gtag `GT-NBJ8G3C` y Google Ads `AW-17761829800`. **No vi el píxel de Meta** directamente en la página; puede estar dentro de GTM. Hay que verificarlo.
- **Protección:** el servidor (ModSecurity) rechaza solicitudes sin cabeceras de navegador; no afecta a visitantes.

## Hallazgos que afectan a Fly & Buy
1. **La web publica $787K** (cifra de inicio y Type A), no $780K. Hay que corregirla en EN y ES para unificar con la versión oficial.
2. **La home y `/financing-options/` publican "15 to 30 years financing"**, "Fractional Co-ownership", "Crypto friendly" y "70 installments". Contradice que el plan a 30 años no tiene cupo, y cuenta otra historia que Fly & Buy ("compra una villa construida"). Hay que decidir qué se retira o se matiza.
3. **El bloque de financiamiento de `/villas-for-sale/` coincide con lo oficial** (30 % enganche, 20 % a la entrega, saldo a 1 año sin intereses; hipoteca para mexicanos y estadounidenses; plan de 10 años para canadienses). Ojo: ahí el plan de 10 años figura para canadienses, mientras que el dato oficial que recibí habla de "10 años con HIR". Confirmar a quién aplica.
4. **La página ya usa la CTA aprobada** "Only a select number of residences remain" y "Our team responds within 24 hours": esto hay que respetarlo en la sección de Fly & Buy (promesa de respuesta).
5. **Ortografía:** el título de la página y el hero dicen "Selva Zama"; debe ser "Selvazamá". En ES el menú de anclas mezcla idiomas ("Location", "Residences" sin traducir).
6. **Dónde encaja la sección:** entre el hero y "01 Location", y como ítem nuevo en la subnavegación ("Fly & Buy"), con ancla `#fly-and-buy`. Los CTA existentes ("Get Brochure & Pricelist") apuntan a un formulario distinto; no deben mezclarse.
7. **Terceros con cifras distintas** (17 y 20 villas, "from $878,915", unidades de 2 recámaras): pedir a los brokers que corrijan.

## Pendiente de verificar
- Meta Pixel y Conversions API dentro de GTM; eventos configurados para el formulario GHL.
- Campos y automatizaciones del formulario `SjDKiqRzjazTG2oynV6J` y si se puede crear uno nuevo con origen `fly-and-buy`.
- Páginas About, Location, Contact y Blog; Instagram/Facebook (necesito capturas por el login).
