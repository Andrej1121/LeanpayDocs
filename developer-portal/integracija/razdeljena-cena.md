## Prikaz razdeljene cene na domači, kategorni in produktni strani

_**Kot kupec bom kupil boljše in več, če bom dobro informiran o višini obroka**_

Najučinkovitejši način, da stranko prepričate v nakup je, da stranki na vseh vaših straneh zraven artiklov prikažete še razdeljeno ceno.

<!--
type: tab
title: Notesniki.si - Domača stran
-->

![](//s3.amazonaws.com/user-content.stoplight.io/27159/1629185856328)

<!--
type: tab
title: Stran z iskanjem / kategorije
-->

![](//s3.amazonaws.com/user-content.stoplight.io/27159/1629186324900)

<!--
type: tab
title: Produkt
-->

![](//s3.amazonaws.com/user-content.stoplight.io/27159/1629185957030)

<!-- type: tab-end -->

<!--
type: tab
title: Topohistvo.si - Domača stran
-->

![](//s3.amazonaws.com/user-content.stoplight.io/27159/1629968830434)

<!--
type: tab
title: Stran z iskanjem
-->

![](//s3.amazonaws.com/user-content.stoplight.io/27159/1629969001643)

<!--
type: tab
title: Produkt
-->

![](//s3.amazonaws.com/user-content.stoplight.io/27159/1629968535439)

<!-- type: tab-end -->

<!--
type: tab
title: Lorexcenter.si
-->

![](//s3.amazonaws.com/user-content.stoplight.io/27159/1629966974879)

<!--
type: tab
title: Bigbang.si
-->

![](//s3.amazonaws.com/user-content.stoplight.io/27159/1629966120413)

<!-- type: tab-end -->

<!--
type: tab
title: Anni.si - Desktop
-->

![Produkt](//s3.amazonaws.com/user-content.stoplight.io/27159/1579956316032 "Produkt")

<!--
type: tab
title: Mobile
-->

![Produkt](//s3.amazonaws.com/user-content.stoplight.io/27159/1579956363280 "Produkt")

<!-- type: tab-end -->

<!-- type: tab-end -->

<!--  inline: true -->

<!--  inline: true -->

## Najboljši način prikaza razdeljene cene in hitrih dodatnih informacij o leanpay

![Najboljši način prikaza razdeljene cene in hitrih dodatnih informacij o leanpay](//s3.amazonaws.com/user-content.stoplight.io/27159/1629114538926 "Najboljši način prikaza razdeljene cene in hitrih dodatnih informacij o leanpay")

Pri prikazu razdeljenih cen se držimo navodil:

- Pod redno ceno z --ali-- ločimo redno in razdeljene cene
- Najprej izpišemo najnižjno ceno obroka in najvišjo možno ročnost **v enaki velikosti pisave kot je zapisana redna cena**
- Ne izpisujemo **več kot 3 razdeljene cene** saj s tem podamo preveč informacij
- Pod razdeljenimi cenami izpišemo še polog
- Stranki na najlažji način podamo osnovne informacije s pomočjo **hoverboxa** v katerem prikažemo:
  - Vse možne ročnosti
  - Kratke informacije "Leanpay omogoča enostavne obročne nakupe preko spleta. Za obročno plačilo nakupa v košarici izberite leanpay. Informativni izračun ne vključuje stroškov ocene tveganja. Za nakup potrebujete vašo davčno številko, številko transakcijskega računa (SI56..) in plačilno kartico Mastercard/Visa pri nakupih višjih od 1000€

## Implementation guide

Call to our API <https://app.leanpay.si/vendor/installment-plans> will return all instalment options for all financial products available to you

### Integration recommendation:

1. Once per week get latest instalment prices from our API
2. Save JSON response to your DB
3. Calculate downpayment:

- 0 EUR for purchases up to 999.99 EUR
- 100 EUR for purchases from 1000 EUR to 1999.99 EUR
- 150 EUR for purchases from 2000 EUR to 2999.99 EUR
- 200 EUR for purchases from 3000 EUR to 3999.99 EUR
- 250 EUR for purchases from 3000 EUR to 4999.99 EUR
- 300 EUR for purchases from 5000 EUR

4. Case product price is 139,15€ we recomend rounding to 140€
5. API specification can be found at \[API - vendor/installment-plans] (<https://docs.leanpay.com/povecajte-prodajo/ze-od/instalment-plans/standard/installment-plans>)

### API response sample

```
{
    "groups": [
        {
            "groupId": "2ac1010b-2675-4aed-ab92-81b34ac6312f",
            "groupName": "SPLET - REDNA PONUDBA",
            "vendorProductCode": "2ac1010b-2675-4aed-ab92-81b34ac6312f",
            "currencyCode": "EUR",
            "loanAmounts": [
                {
                    "loanAmount": 50.0,
                    "possibleInstallments": [
                        {
                            "numberOfMonths": 3,
                            "installmentAmout": 16.86
                        }
                    ]
                },
                {
                    "loanAmount": 51.0,
                    "possibleInstallments": [
                        {
                            "numberOfMonths": 3,
                            "installmentAmout": 17.20
                        }
                    ]
                },
								                {
                    "loanAmount": 2999.0,
                    "possibleInstallments": [
                        {
                            "numberOfMonths": 24,
                            "installmentAmout": 132.86
                        }
                    ]
                },
                {
                    "loanAmount": 3000.0,
                    "possibleInstallments": [
                        {
                            "numberOfMonths": 12,
                            "installmentAmout": 252.59
                        }
                    ]
                },
                {
                    "loanAmount": 3000.0,
                    "possibleInstallments": [
                        {
                            "numberOfMonths": 18,
                            "installmentAmout": 171.29
                        }
                    ]
                },
                {
                    "loanAmount": 3000.0,
                    "possibleInstallments": [
                        {
                            "numberOfMonths": 24,
                            "installmentAmout": 130.67
                        }
                    ]
                }
            ]
        },
				
```

<!--  inline: true -->

![](//s3.amazonaws.com/user-content.stoplight.io/27159/1610109352410)

<html>
<head>
<meta name="viewport" content="width=device-width, initial-scale=1">
<!-- Add icon library -->
<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/4.7.0/css/font-awesome.min.css">
</head>
<body>
  <br><br>
  <div class="wrapper"><p>Potrebujete pomoč pri implementaciji ali imate vprašanje?</p>
  <a href="mailto:partner@leanpay.si?subject=Pomoč pri implementaciji" target="_blank" download>
 <button class="btn"><i class="fa fa-paper-plane"></i> Pišite nam</button></div>
</body>
</html>
