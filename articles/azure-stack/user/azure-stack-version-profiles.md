---
title: Gérer des profils de version des API dans Azure Stack | Microsoft Docs
description: En savoir plus sur les profils de version des API dans Azure Stack.
services: azure-stack
documentationcenter: ''
author: mattbriggs
manager: femila
ms.service: azure-stack
ms.workload: na
pms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 04/23/2018
ms.author: mabrigg
ms.reviewer: sijuman
ms.openlocfilehash: e568ffd2c3adb97ed0b727b85e7888fb797db1f9
ms.sourcegitcommit: 96089449d17548263691d40e4f1e8f9557561197
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34258207"
---
# <a name="manage-api-version-profiles-in-azure-stack"></a>Gérer les profils de version des API dans Azure Stack

*S’applique à : systèmes intégrés Azure Stack et Kit de développement Azure Stack*

Les profils d’API précisent le fournisseur de ressources Azure ainsi que la version d’API des points de terminaison Azure REST. Vous pouvez créer des clients personnalisés dans différents langages à l’aide des profils d’API. Chaque client utilise un profil d’API pour contacter le fournisseur de ressources et la version d’API appropriés pour Azure Stack.

Vous pouvez créer une application qui fonctionne avec les fournisseurs de ressources Azure sans savoir exactement quelle version des API de fournisseur de ressources est compatible avec Azure Stack. Il vous suffit d’aligner votre application sur un profil. Le kit de développement logiciel (SDK) rétablit la version d’API appropriée.

Cette rubrique vous aide à :

 - comprendre les profils d’API pour Azure Stack,
 - comprendre l’utilisation des profils d’API pour développer vos solutions,
 - obtenir des conseils spécifiques au code.

## <a name="summary-of-api-profiles"></a>Résumé des profils d’API

- Les profils d’API représentent un ensemble de fournisseurs de ressources Azure et leurs versions d’API.
- Les profils d’API ont été créés pour les développeurs, afin qu’ils puissent générer des modèles utilisables sur plusieurs clouds Azure. Les profils sont conçus pour répondre aux besoins en offrant une interface compatible et stable.
- La mise en production des profils intervient quatre fois par an.
- Trois conventions d’appellation des profils sont utilisées :
    - **le plus récent**  
        Contient les versions d’API les plus récentes publiées dans Azure global.
    - **yyyy-mm-dd-hybrid**  
    Version publiée tous les semestres. Elle se concentre sur la cohérence et la stabilité d’un cloud à l’autre. Ce profil vise à assurer une compatibilité optimale avec Azure Stack.
    - **yyyy-mm-dd-profile** Version se situant entre celle offrant une stabilité optimale et celle proposant les fonctionnalités les plus récentes.

### <a name="azure-api-profiles-and-azure-stack-compatibility"></a>Profils d’API Azure et compatibilité avec Azure Stack

Les profils d’API Azure les plus récents ne sont pas compatibles avec Azure Stack. Vous pouvez utiliser les conventions d’affectation de noms suivantes pour identifier les profils à utiliser pour vos solutions Azure Stack.

**La plus récente**  
Ce profil comprend les versions d’API les plus à jour proposées dans Azure global. Ces versions ne sont pas compatibles avec Azure Stack. Le profil **La plus récente** présente le plus grand nombre de changements importants. Ce profil ne vise pas la stabilité et la compatibilité avec les autres clouds. Si vous essayez d’utiliser les versions d’API les plus à jour, **La plus récente** est le profil que vous devez utiliser.

**Yyyy-mm-dd-hybrid**  
Ce profil est publié deux fois par an, en mars et en septembre. Il garantit une stabilité et une compatibilité optimales avec les autres clouds. Le profil **Yyyy-mm-dd-hybrid** est conçu pour cibler les environnements Azure global et Azure Stack. Les versions d’API Azure répertoriées dans ce profil sont les mêmes que celles disponibles dans Azure Stack. Utilisez ce profil si vous souhaitez développer des solutions cloud hybrides.

**yyyy-mm-dd-profile**  
Ce profil pour Azure global est publié deux fois par an, en juin et en décembre. Ce profil n’est pas compatible avec Azure Stack. Il présente généralement de nombreux changements importants. Même s’il offre une stabilité optimale et les fonctionnalités les plus récentes, il n’est pas identique au profil **La plus récente**. La différence entre les deux est que le profil **La plus récente** propose toujours les toutes dernières versions des API, quelle que soit la date de publication des API. Par exemple, si une nouvelle version de l’API Compute est créée demain, cette version sera aussitôt proposée dans le profil **La plus récente**, mais pas dans le profil **yyyy-mm-dd-profile**, car ce profil existe déjà.  Le profil **yyyy-mm-dd-profile** fournit les dernières versions mises à jour ayant été publiées avant juin ou avant décembre.

## <a name="azure-resource-manager-api-profiles"></a>Profils d’API Azure Resource Manager

Azure Stack n’utilise pas les versions d’API les plus récentes disponibles dans Azure global. Quand vous créez votre solution, vous devez rechercher la version d’API pour chaque fournisseur de ressources Azure qui est compatible avec Azure Stack.

Plutôt que d’effectuer des recherches sur chaque fournisseur de ressources et sur chacune des versions spécifiques prises en charge par Azure Stack, vous pouvez utiliser un profil d’API. Le profil spécifie un ensemble de fournisseurs de ressources et de versions d’API. Le SDK, ou un outil intégré au SDK, vous oriente vers la version d’API cible indiquée dans le profil. Avec les profils d’API, vous pouvez spécifier une version de profil qui s’applique à tout un modèle. Puis, au moment de l’exécution, Azure Resource Manager sélectionne la version appropriée de la ressource.

Les profils d’API fonctionnent avec des outils qui utilisent Azure Resource Manager, par exemple PowerShell, Azure CLI, le code fourni dans le SDK et Microsoft Visual Studio. Les outils et les SDK peuvent utiliser des profils pour lire la version des modules et des bibliothèques à inclure au moment de créer une application.

**Scénario de développement pour l’utilisation d’un profil**  
Supposons que vous utilisez PowerShell pour créer :

* Un compte de stockage qui utilise le fournisseur de ressources **Microsoft.Storage**, lequel prend en charge la version d’API 2016-03-30.
* Une machine virtuelle qui utilise le fournisseur de ressources **Microsoft.Compute**, lequel prend en charge la version d’API 2015-12-01.

Au lieu de rechercher et d’installer les modules PowerShell qui prennent en charge les versions d’API dont vous avez besoin pour le stockage et le calcul, vous pouvez utiliser un profil. Utilisez l’applet de commande **Install-Profile *nom_profil***. PowerShell charge alors la version appropriée des modules.

De même, si vous utilisez le SDK Python pour générer une application basée sur Python, vous pouvez utiliser un profil. Le SDK charge les modules appropriés pour les fournisseurs de ressources que vous avez spécifiés dans votre script.

En tant que développeur, vous pouvez ainsi vous concentrer sur l’écriture de votre solution. Vous pouvez utiliser un profil, en sachant que votre code fonctionnera sur tous les clouds qui prennent en charge ce profil.

## <a name="api-profile-code-samples"></a>Exemples de code de profil d’API

Il existe des exemples de code pour vous aider à intégrer votre solution et votre langage par défaut à Azure Stack à l’aide des profils. Actuellement, vous pouvez trouver des conseils et des exemples pour les langages suivants :

- **PowerShell**  
Le module **AzureRM.Bootstrapper**, disponible via PowerShell Gallery, fournit les cmdlets PowerShell nécessaires pour utiliser des profils de version d’API. Pour plus d’informations, consultez [Utiliser des profils de version d’API pour PowerShell](azure-stack-version-profiles-powershell.md).
- **Azure CLI 2.0**  
Vous pouvez mettre à jour la configuration de votre environnement pour utiliser le profil de version d’API spécifique à Azure Stack. Pour plus d’informations, consultez [Utiliser les profils de version d’API pour Azure CLI 2.0](azure-stack-version-profiles-azurecli2.md).
- **GO**  
Dans le SDK GO, un profil est une combinaison de différents types de ressources dans différentes versions provenant de différents services. Les profils sont disponibles sous les profils/chemin d’accès, leur version étant au format **YYYY-MM-DD**. Pour plus d’informations, consultez [Utiliser des profils de version d’API pour GO](azure-stack-version-profiles-go.md).
- **Ruby**  
Le kit SDK Ruby pour le Gestionnaire des ressources Azure Stack fournit des outils pour vous aider à créer et gérer votre infrastructure. Les fournisseurs de ressources du SDK incluent le calcul, les réseaux virtuels et le stockage avec le langage Ruby. Pour plus d’informations, consultez [Utiliser des profils de version d’API avec Ruby](azure-stack-version-profiles-ruby.md)

## <a name="next-steps"></a>Étapes suivantes

* [Installer PowerShell pour Azure Stack](azure-stack-powershell-install.md)
* [Configurez l’environnement PowerShell de l’utilisateur Azure Stack.](azure-stack-powershell-configure-user.md)
* [Passer en revue les détails sur les versions d’API du fournisseur de ressources prises en charge par les profils](azure-stack-profiles-azure-resource-manager-versions.md).
