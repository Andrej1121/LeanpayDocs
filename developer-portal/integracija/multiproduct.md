_**opcijsko**_

_**Kot trgovec bi strankam ponudili različne finančne produkte v primeru akcij. Naprimer vsi artikli znamke PHILIPS brez obresti in brez stroškov - EOM0**_

**Odličen način povečanja in pospeševanja prodaje je možnost izbire finančnega produkta kot so kredit brez stroškov in obresti in kredit brez obresti**

## Implementation guide

_Trgovec se odloči, da bo ponudil vse artikle znamke PHILIPS brez obresti in brez stroškov - EOM0._

Preverimo razpoložljive produkte - "vendor product code" v [POST /vendor/installment-plans](https://docs.leanpay.si/integracija_z_leanpay/api-integracija/API/custom/installment-plans) :
Primer:
"groupName": "SPLET - EOM0 - STANDARD",
"vendorProductCode": "2afbd87f-484a-4541-a726-b3429565f53a",

"groupName": "SPLET - OM0 - STANDARD",
"vendorProductCode": "d7dcf291-8fd6-4b23-9c14-369af9fbb79d",

_Kupec doda 2 produkta znamke PHILIPS v košarico in izbere leanpay kot način plačila._

V "vendorProductCode" dodamo "db834c45-6ddb-4207-bbe3-0396bbffbbd5" pri klicu POST /vendor/token API in stranki bo za nakup veljala ponudba EOM0 - kredit brez obresti in brez stroškov.

<!--  inline: true -->

![SAMPLE PRODUCT FOR EOM0 FINANCIAL PRODUCT](//s3.amazonaws.com/user-content.stoplight.io/27159/1598446583751 "SAMPLE PRODUCT FOR EOM0 FINANCIAL PRODUCT")

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
