---
title: Prise en main d’Azure Data Lake Analytics à l’aide du portail Azure
description: Découvrez comment utiliser le portail Azure pour créer un compte Data Lake Analytics, créer un travail Data Lake Analytics avec U-SQL et envoyer le travail.
services: data-lake-analytics
author: saveenr
ms.author: saveenr
manager: kfile
ms.assetid: b1584d16-e0d2-4019-ad1f-f04be8c5b430
ms.service: data-lake-analytics
ms.topic: hero-article
ms.workload: big-data
ms.date: 03/21/2017
ms.openlocfilehash: 63fc4272dc4b26e9eb4846118bc57cd6aa5bf361
ms.sourcegitcommit: b6319f1a87d9316122f96769aab0d92b46a6879a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2018
ms.locfileid: "34358283"
---
# <a name="get-started-with-azure-data-lake-analytics-using-azure-portal"></a>Prise en main d’Azure Data Lake Analytics à l’aide du Portail Azure
[!INCLUDE [get-started-selector](../../includes/data-lake-analytics-selector-get-started.md)]

Découvrez comment utiliser le portail Azure pour créer des comptes Azure Data Lake Analytics, définir des travaux dans [U-SQL](data-lake-analytics-u-sql-get-started.md) et envoyer des travaux au service Data Lake Analytics. Pour plus d’informations sur Analytique Data Lake, consultez [Présentation d’Analytique Data Lake Azure](data-lake-analytics-overview.md).

## <a name="prerequisites"></a>Prérequis


Avant de commencer ce didacticiel, vous devez disposer d’un **abonnement Azure**. Consultez la page [Obtention d’un essai gratuit d’Azure](https://azure.microsoft.com/pricing/free-trial/).

## <a name="create-a-data-lake-analytics-account"></a>Créer un compte Data Lake Analytics

À présent, vous allez créer un compte Data Lake Analytics et un compte Data Lake Store simultanément.  Cette étape est simple et ne prend qu’environ 60 secondes.

1. Connectez-vous au [Portail Azure](https://portal.azure.com).
2. Cliquez sur **Créer une ressource** >  **Données + Analytique**  > **Data Lake Analytics**.
3. Sélectionnez des valeurs pour les éléments suivants :
   * **Nom** : donnez un nom à votre compte Data Lake Analytics (utilisez uniquement des lettres minuscules et des chiffres).
   * **Abonnement**: choisissez l’abonnement Azure utilisé pour le compte Analytics.
   * **Groupe de ressources**. Sélectionnez un groupe de ressources Azure existant ou créez-en un.
   * **Emplacement**. Sélectionnez un centre de données Azure pour le compte Data Lake Analytics.
   * **Data Lake Store** : suivez les instructions pour créer un compte Data Lake Store ou sélectionnez un compte existant. 
4. Si vous le souhaitez, sélectionnez un niveau tarifaire pour votre compte Data Lake Analytics.
5. Cliquez sur **Créer**. 


## <a name="your-first-u-sql-script"></a>Votre premier script U-SQL

Le texte suivant est un script U-SQL très simple. Il ne fait que définir un petit jeu de données dans le script puis de l’écrire dans le Data Lake Store par défaut comme un fichier appelé `/data.csv`.

```
@a  = 
    SELECT * FROM 
        (VALUES
            ("Contoso", 1500.0),
            ("Woodgrove", 2700.0)
        ) AS 
              D( customer, amount );
OUTPUT @a
    TO "/data.csv"
    USING Outputters.Csv();
```

## <a name="submit-a-u-sql-job"></a>Envoyer un travail U-SQL

1. À partir du compte Data Lake Analytics, sélectionnez **Nouveau travail**.
2. Collez le texte du script U-SQL précédent. Attribuez un nom au travail. 
3. Sélectionnez le bouton **Soumettre** pour démarrer le travail.   
4. Surveillez **l’état** du travail et attendez qu’il passe à **Réussi**.
5. Sélectionnez l’onglet **Données**, puis l’onglet **Sorties**. Sélectionnez le fichier de sortie `data.csv` et affichez les données de sortie.

## <a name="see-also"></a>Voir aussi

* Pour commencer à développer des applications U-SQL, consultez [Développer des scripts U-SQL avec Data Lake Tools pour Visual Studio](data-lake-analytics-data-lake-tools-get-started.md).
* Pour connaître U-SQL, voir [Prise en main du langage U-SQL d’Analytique Data Lake Azure](data-lake-analytics-u-sql-get-started.md).
* Pour les tâches de gestion, consultez [Gestion d’Azure Data Lake Analytics à l’aide du portail Azure](data-lake-analytics-manage-use-portal.md).
