---
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '81'
ht-degree: 0%

---
# Hotfixes inbegrepen in de veiligheidsflarden van Oktober (behalve 2.4.4)

Deze release bevat een hotfix om een probleem op te lossen met de Braintree-betaalgateway.

Het systeem bevat nu de velden die nodig zijn om te voldoen aan de vereisten voor 3DS VISA-machtigingen wanneer Braintree wordt gebruikt als betaalgateway. Dit zorgt ervoor dat alle transacties voldoen aan de recentste beveiligingsnormen die door VISA zijn vastgesteld. Voorheen werden deze extra velden niet opgenomen in de verzonden betalingsinformatie, hetgeen tot niet-naleving van de nieuwe VISA-vereisten had kunnen leiden.

<!--
BUNDLE-3360
-->