---
title: 原則 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rules Engine, policies
- policies, about policies
- policies, deploying
- policies, Business Rules Engine
- policies
- business rules, policies
- policies, versioning
- policies, testing
- policies, creating
- policies, updating
ms.assetid: 2e0ae081-938d-4e2a-947e-1c0ecfebb4b8
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bd05d6cf67d89ee811cac45ac3950697db74f59
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264430"
---
# <a name="policies"></a>原則
「原則」 (Policy) 是規則的邏輯群組。 您可以編輯原則的版本、儲存它、藉由將它套用到事實來測試，以及當您對結果感到滿意時，將它發佈和部署到生產環境。  
  
## <a name="policy-composition"></a>原則撰寫  
 您可以藉由建構來自事實與定義的規則，在商務規則編輯器中編輯原則。 原則可以包含任意的大量規則集合，但是一般而言，您會從規則編輯原則，而那些規則會與使用原則之應用程式內容中的特定商務網域有關。  
  
## <a name="policy-testing"></a>原則測試  
 將原則發佈和部署在生產環境之前，您可以先有效地執行原則的測試。 商務規則編輯器允許您提供事實的執行個體給原則、執行該原則，以及檢視其輸出。 輸出會包含事實活動、規則執行、條件評估，以及對議程的更新。  
  
## <a name="policy-versions"></a>原則版本  
 在定義原則中的所有規則之後，您可以發佈原則版本。 在此方式中，原則會被鎖定，且其行為是妥善定義的。  
  
 指定的原則版本可用於您商務環境中的一組指定情況下，當那些情況變更時，會以另一個版本來取代。 此外，新版本與舊版本可以同時由不同的應用程式所使用。  
  
## <a name="policy-deployment"></a>原則部署  
 當您的原則已經準備在生產環境中執行時，您可以部署它，使其可為裝載應用程式所使用。  
  
## <a name="dynamic-policy-updates"></a>動態原則更新  
 動態原則更新允許您獨立修改執行中商務程序的原則。 您可以建立和部署原則的更新版本，裝載應用程式幾乎會即時併入該項更新。 此更新不會要求您變更任何的程式碼，因此，您可以避免重新開發與重新部署應用程式的負擔。  
  
## <a name="see-also"></a>另請參閱  
 [商務規則引擎](../core/business-rules-engine.md)