---
title: "MDVA-44147: [!DNL GraphQL]  het verzoek keert niet terug [!UICONTROL Requisition Lists]"
description: Het flard MDVA-44147 lost de kwestie op waar  [!DNL GraphQL]  verzoek niet [!UICONTROL Requisition Lists] terugkeert. Deze patch is beschikbaar wanneer [Quality Patches Tool (QPT)] (https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 is geïnstalleerd. De patch-id is MDVA-44147. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.
feature: B2B, GraphQL
role: Admin
exl-id: 534c4e45-6521-45c0-ae4e-c60b754f432f
source-git-commit: fa95ca5ac2f7606386a785fb3b29f56672d555b1
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# MDVA-44147: [!DNL GraphQL] request does not return [!UICONTROL Requisition Lists]

De patch MDVA-44147 verhelpt het probleem waarbij [!DNL GraphQL] request does not return [!UICONTROL Requisition Lists] . Dit flard is beschikbaar wanneer het [ Hulpmiddel van de Patches van de Kwaliteit (QPT) ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.14 geïnstalleerd is. De patch-id is MDVA-44147. Het probleem wordt volgens de planning opgelost in Adobe Commerce 2.4.5.

## Betrokken producten en versies

**het flard wordt gecreeerd voor de versie van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.3-p1

**Compatibel met de versies van Adobe Commerce:**

* Adobe Commerce (alle implementatiemethoden) 2.4.2 - 2.4.4

>[!NOTE]
>
>De patch kan van toepassing worden op andere versies met nieuwe versies van het Hulpprogramma voor kwaliteitspatches. Om te controleren of de patch compatibel is met uw Adobe Commerce-versie, werkt u het `magento/quality-patches` -pakket bij naar de meest recente versie en controleert u de compatibiliteit op de [[!DNL Quality Patches Tool] : zoek naar patches op de pagina ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) . Gebruik de patch-id als een zoekwoord om de patch te zoeken.

## Probleem

[!DNL GraphQL] request does not return [!UICONTROL Requisition Lists].

<u> Stappen om </u> te reproduceren:

1. Ga naar **Opslag** > **Montages** > **Configuratie** > **Algemeen** > **B2B Eigenschappen** en laat **[!UICONTROL Requisition List]** toe.
1. Meld u aan als klant en voeg een product toe aan [[!UICONTROL Requisition List] ](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/requisition-lists/requisition-lists) .
1. Creeer het Symbolische van de a [ Klant ](https://developer.adobe.com/commerce/webapi/graphql/mutations/generate-customer-token.html).

   <pre>
    <code class="language-graphql">
    mutation {
      generateCustomerToken(
        email: "test@gmail.com"
        password: "xxxxxxxx"
        ) {
          token
        }
      }
      </code>
      </pre>

1. Gebruik de volgende query om alle [!UICONTROL Requisition Lists] van de klant op te halen. Gebruik de **kopbal van de Vergunning** met de waarde `Bearer <customer_token>`. Verwijs naar het [ artikel van de Vraag van de Klant ](https://developer.adobe.com/commerce/webapi/graphql/schema/customer/queries/customer/) in onze ontwikkelaardocumentatie voor meer informatie.

   Verzoek:

   <pre>
    <code class="language-graphql">
    query {
      customer {
        requisition_lists(
          pageSize: 20
          ) {
            items {
              uid
              name
              description
              items(pageSize: 20) {
                items {
                  uid
                  product {
                    uid
                    name
                    sku
                    __typename
                  }
                  quantity
                }
                total_pages
              }
            }
            total_count
          }
        }
      }
      </code>
      </pre>

   Reactie:

   <pre>
    <code class="language-graphql">
    {
      "data": {
        "customer": {
          "requisition_lists": {
            "items": [
            {
              "uid": "MQ==",
              "name": "Name",
              "description": "Description",
              "items": {
                "items": [
                {
                  "uid": "MQ==",
                  "product": {
                    "uid": "MQ==",
                    "name": "Simple 01",
                    "sku": "s00001",
                    "__typename": "SimpleProduct"
                    },
                    "quantity": 1
                  }
                  ],
                  "total_pages": 1
                }
              }
              ],
              "total_count": 1
            }
          }
        }
      }
      </code>
      </pre>

1. Kopieer de UID van een item uit de geretourneerde lijst (MQ==) en gebruik de volgende query om de lijst te laten filteren door de UID.

   <pre>
    <code class="language-graphql">
    query {
      customer {
        requisition_lists(
          pageSize: 20,
          filter: {
            uids: {
              eq: "MQ=="
            }
          }
          ) {
            items {
              uid
              name
              description
              items(pageSize: 20) {
                items {
                  uid
                  product {
                    uid
                    name
                    sku
                    __typename
                  }
                  quantity
                }
                total_pages
              }
            }
            total_count
          }
        }
      }
      </code>
      </pre>

<u> Verwachte resultaten </u>:

Eén resultaat wordt geretourneerd.

<u> Ware resultaten </u>:

Er worden geen resultaten geretourneerd.

## De patch toepassen

Om individuele flarden toe te passen, gebruik de volgende verbindingen afhankelijk van uw plaatsingsmethode:

* Adobe Commerce of Magento Open Source op locatie: [[!DNL Quality Patches Tool]  > Gebruik ](/help/tools/quality-patches-tool/usage.md) in de handleiding [!DNL Quality Patches Tool] .
* Adobe Commerce op wolkeninfrastructuur: [ Verbeteringen en Patches > Pas Patches ](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) in Commerce op de gids van de Infrastructuur van de Wolk toe.

## Gerelateerde lezing

Raadpleeg voor meer informatie over het gereedschap Kwaliteitspatches:

* [ vrijgegeven het Hulpmiddel van de Patches van de Kwaliteit: een nieuw hulpmiddel om kwaliteitspatches ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) in de steunkennisbasis zelf-te dienen.
* [ Controle als het flard voor uw kwestie van Adobe Commerce beschikbaar is gebruikend het Hulpmiddel van de Patches van de Kwaliteit ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) in de [!DNL Quality Patches Tool] gids.

Voor informatie over andere flarden beschikbaar in QPT, verwijs naar [[!DNL Quality Patches Tool]: Onderzoek naar flarden ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) in de [!DNL Quality Patches Tool] gids.
