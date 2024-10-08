---
source-git-commit: 5ef5c2dedbbef2858a6bbc6c0aca13fd9adae0c8
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# Hotfixes inbegrepen in de veiligheidsflarden van Oktober (behalve 2.4.4)

Deze release bevat een hotfix om een probleem op te lossen met de betaalgateway van de Braintree.

Het systeem omvat nu de noodzakelijke gebieden om aan de 3DS VISA mandaatvereisten te voldoen wanneer het gebruiken van Braintree als betalingsgateway. Dit zorgt ervoor dat alle transacties voldoen aan de recentste beveiligingsnormen die door VISA zijn vastgesteld. Voorheen werden deze extra velden niet opgenomen in de verzonden betalingsinformatie, hetgeen tot niet-naleving van de nieuwe VISA-vereisten had kunnen leiden.

<!--
BUNDLE-3360
-->