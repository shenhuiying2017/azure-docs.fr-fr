---
title: Créer des rapports d’instantané Cloud App Discovery dans Azure Active Directory | Microsoft Docs
description: Fournit une vue d'ensemble de la recherche et de la gestion d'applications avec Cloud App Discovery, ainsi que des informations sur ses avantages et son fonctionnement.
services: active-directory
keywords: détection d'applications cloud, gestion d'applications
documentationcenter: ''
author: barbkess
manager: mtillman
ms.service: active-directory
ms.component: app-mgmt
ms.workload: identity
ms.topic: article
ms.date: 09/22/2017
ms.author: barbkess
ms.reviewer: nigu
ms.custom: it-pro
ms.openlocfilehash: 68585edad6e7d1b6b21a48f1cf4242875cea538a
ms.sourcegitcommit: d28bba5fd49049ec7492e88f2519d7f42184e3a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2018
---
# <a name="create-cloud-app-discovery-snapshot-reports"></a>Créer des rapports d’instantané Cloud App Discovery

Avant de configurer le collecteur de journaux automatique, chargez un journal manuellement afin que Cloud App Security l’analyse. Si vous ne disposez pas encore d’un journal et que vous souhaitez voir un exemple de ce à quoi il doit ressembler, utilisez la procédure ci-dessous pour télécharger un exemple de fichier journal.

## <a name="to-create-a-snapshot-report"></a>Pour créer un instantané de rapport

1. Collectez les fichiers journaux à partir des pare-feu et serveur proxy via lesquels les utilisateurs de votre organisation accèdent à Internet. Collectez les journaux pendant les heures de pointe représentatives de l’activité des utilisateurs au sein de votre organisation.
2. Dans la [barre de menus de Cloud App Security](https://portal.cloudappsecurity.com), sélectionnez **Découvrir**, puis **Créer un rapport d’instantané**.
  
  ![Créer un rapport d’instantané](./media/cloud-app-discovery-create-snapshot-reports/create-snapshot-command.png)
3. Entrez un **nom de rapport** et une **description**.
    
  ![Nouveau rapport d’instantané](./media/cloud-app-discovery-create-snapshot-reports/create-snapshot-form.png)
4. Sélectionnez la **source de données** à partir de laquelle vous souhaitez charger les fichiers journaux.
5. Vérifiez que le format du journal est correct par rapport à l’exemple que vous pouvez télécharger. Cliquez sur **Afficher et vérifier**, puis sur **Télécharger l’exemple de journal**. Ensuite, comparez votre journal à l’exemple fourni pour vérifier qu’il est compatible.
  
  ![Vérifier le format de votre journal](./media/cloud-app-discovery-create-snapshot-reports/create-snapshot-verify.png)
  >  [!NOTE]
  > L’exemple de format FTP est pris en charge dans les instantanés et dans le chargement automatique, tandis que syslog n’est pris en charge que dans le chargement automatique. Télécharger un exemple de journal télécharge un exemple de journal FTP.
6. **Choisissez les journaux de trafic** que vous souhaitez charger. Vous pouvez charger jusqu’à 20 fichiers à la fois. Les fichiers compressés et zippés sont également pris en charge.
  
7. Cliquez sur **Créer**. Une fois le chargement effectué, leur analyse peut prendre un certain temps. Dans ce cas, Cloud App Discovery envoie une notification par e-mail quand ils sont prêts.

8. Sélectionnez **Gérer des rapports d’instantanés**, puis sélectionnez votre rapport d’instantané.
  
  ![Gestion des rapports d’instantanés](./media/cloud-app-discovery-create-snapshot-reports/create-snapshot-manage.png)

## <a name="next-steps"></a>Étapes suivantes

* [Bien démarrer avec Cloud App Discovery dans Azure AD](cloud-app-discovery.md)
* [Configurer le chargement automatique des journaux pour des rapports continus](https://docs.microsoft.com/cloud-app-security/discovery-docker)
* [Utiliser un analyseur de journal personnalisé](https://docs.microsoft.com/cloud-app-security/custom-log-parser)
