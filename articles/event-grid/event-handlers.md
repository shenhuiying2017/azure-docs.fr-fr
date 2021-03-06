---
title: Gestionnaires d’événements Azure Event Grid
description: Décrit les gestionnaires d’événements pris en charge pour Azure Event Grid
services: event-grid
author: tfitzmac
manager: timlt
ms.service: event-grid
ms.topic: conceptual
ms.date: 05/04/2018
ms.author: tomfitz
ms.openlocfilehash: 996bd4b3497861a3bfcbfecebe18a6936f487028
ms.sourcegitcommit: 688a394c4901590bbcf5351f9afdf9e8f0c89505
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2018
ms.locfileid: "34301765"
---
# <a name="event-handlers-in-azure-event-grid"></a>Gestionnaires d’événements dans Azure Event Grid

Un gestionnaire d’événements désigne l’endroit où l’événement est envoyé. Le gestionnaire effectue des actions supplémentaires pour traiter l’événement. Plusieurs services Azure sont automatiquement configurés pour gérer les événements. Vous pouvez également utiliser n’importe quel webhook pour la gestion des événements. À cette fin, il n’est pas nécessaire que le webhook soit hébergé dans Azure.

Cet article fournit des liens vers du contenu pour chaque gestionnaire d’événements.

## <a name="azure-automation"></a>Azure Automation

Utilisez Azure Automation pour traiter les événements avec des runbooks automatisés.

|Intitulé  |Description  |
|---------|---------|
|[Intégrer Azure Automation à Event Grid et Microsoft Teams](ensure-tags-exists-on-new-virtual-machines.md) |Créez une machine virtuelle, qui envoie un événement. L’événement déclenche un runbook Automation qui balise la machine virtuelle et déclenche un message qui est envoyé à un canal Microsoft Teams. |

## <a name="azure-functions"></a>Azure Functions

Utilisez Azure Functions pour les réponses serverless à des événements.

|Intitulé  |Description  |
|---------|---------|
| [Déclencheur Event Grid pour Azure Functions](../azure-functions/functions-bindings-event-grid.md) | Vue d’ensemble de l’utilisation du déclencheur Event Grid dans Functions. |
| [Automatiser le redimensionnement des images chargées à l’aide d’Event Grid](resize-images-on-storage-blob-upload-event.md) | Les utilisateurs chargent les images par le biais de l’application web sur le compte de stockage. Quand un objet blob de stockage est créé, Event Grid envoie un événement à l’application de fonction, qui redimensionne l’image chargée. |
| [Diffuser en continu des Big Data dans un entrepôt de données](event-grid-event-hubs-integration.md) | Quand Event Hubs crée un fichier Capture, Event Grid envoie un événement à une application de fonction. L’application récupère le fichier Capture et migre les données vers un entrepôt de données. |
| [Exemples d’intégration d’Azure Service Bus et d’Azure Event Grid](../service-bus-messaging/service-bus-to-event-grid-integration-example.md?toc=%2fazure%2fevent-grid%2ftoc.json) | Event Grid envoie des messages à partir de la rubrique Service Bus à l’application de fonction et à l’application logique. |

## <a name="hybrid-connections"></a>les connexions hybrides

Utilisez les connexions hybrides Azure Relay pour envoyer des événements aux applications se trouvant dans un réseau d’entreprise et qui ne disposent pas d’un point de terminaison accessible publiquement.

|Intitulé  |Description  |
|---------|---------|
| [Envoyer des évènements à une connexion hybride](custom-event-to-hybrid-connection.md) | Envoie un événement personnalisé vers une connexion hybride existante pour son traitement par une application d’écouteur. |

## <a name="logic-apps"></a>Logic Apps

Utilisez Logic Apps pour automatiser les processus métier afin de répondre aux événements.

|Intitulé  |Description  |
|---------|---------|
| [Surveiller les modifications d’une machine virtuelle avec Azure Event Grid et Azure Logic Apps](monitor-virtual-machine-changes-event-grid-logic-app.md) | Une application logique surveille les modifications apportées à une machine virtuelle et envoie des e-mails à ce sujet. |
| [Envoyer des notifications par e-mail sur des événements Azure IoT Hub à l’aide de Logic Apps](publish-iot-hub-events-to-logic-apps.md) | Une application logique envoie un e-mail de notification chaque fois qu’un appareil est ajouté à votre hub IoT. |
| [Exemples d’intégration d’Azure Service Bus et d’Azure Event Grid](../service-bus-messaging/service-bus-to-event-grid-integration-example.md?toc=%2fazure%2fevent-grid%2ftoc.json) | Event Grid envoie des messages à partir de la rubrique Service Bus à l’application de fonction et à l’application logique. |

## <a name="queue-storage"></a>Stockage File d’attente

Utilisez le stockage File d’attente pour recevoir des événements qui doivent être extraits.

|Intitulé  |Description  |
|---------|---------|
| [Acheminer des événements personnalisés vers le Stockage File d’attente Azure avec Azure CLI et Event Grid](custom-event-to-queue-storage.md) | Décrit comment envoyer des événements personnalisés à un stockage File d’attente. |

## <a name="webhooks"></a>WebHooks

Utilisez des webhooks pour les points de terminaison personnalisables qui répondent aux événements.

|Intitulé  |Description  |
|---------|---------|
| [Recevoir des événements sur un point de terminaison HTTP](receive-events.md) | Décrit comment valider un point de terminaison HTTP pour recevoir des événements à partir d’un abonnement à des événements et désérialiser des événements. |

## <a name="next-steps"></a>Étapes suivantes

* Pour une présentation d’Event Grid, consultez [À propos d’Event Grid](overview.md).
* Pour une prise en main rapide d’Event Grid, consultez [Créer et acheminer des événements personnalisés avec Azure Event Grid](custom-event-quickstart.md).
