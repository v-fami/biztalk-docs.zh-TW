---
title: 更新使用並排顯示版本設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9721a091-98ec-4f0b-ad1f-6ca184956e7c
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36be63c9cef6a016ea4ad34d98a2750be86491d5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974255"
---
# <a name="updating-using-side-by-side-versioning"></a>使用並排顯示的版本控制更新
如果您不能以排定停機時間，或有非常長時間執行的協調流程執行個體無法終止，可能必須使用--並存版本控制。 在這種升級，相同的應用程式或應用程式成品的兩個版本會執行並排顯示。 .NET 執行階段原本就是可以相同名稱但不同版本的組件，以部署且正在執行，以及 BizTalk Server 也允許它。  
  
 並排顯示的應用程式的版本控制時，您想要推出的主要應用程式升級以累加的方式，例如將它提供給商務合作夥伴的子集一開始，而不是所有合作夥伴一次。 使用這種方式，可讓您繼續執行現有的應用程式來服務尚未使用新版本的使用者，直到您準備好完全轉入新版本為止。  
  
 與建立組件版本不同，您並非以遞增版本號碼的方式建立應用程式版本。 相反地，您會建立新的應用程式具有不同的名稱，從原始的應用程式，並填入應用程式成品的新版本。  
  
 因為有許多類型的成品 (例如，組件) 只能存在於 BizTalk 群組中的一個應用程式，所以您必須遞增已存在於群組內之任何組件的版本號碼，才可以將它們部署到新的應用程式中。  
  
 如需逐步更新應用程式或使用並排顯示版本設定的協調流程所需的工作，請參閱[檢查清單： 更新應用程式使用的並存版本控制](../technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md)和[檢查清單： 更新使用並排顯示版本設定的協調流程](../technical-guides/checklist-updating-an-orchestration-using-side-by-side-versioning.md)。 如需如何以並排顯示部署的應用程式的詳細指示，請參閱 「[如何部署執行的並行應用程式與現有版本的新版本](http://go.microsoft.com/fwlink/?LinkId=155143)(<http://go.microsoft.com/fwlink/?LinkId=155143>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何使用並存版本控制更新對應](../technical-guides/how-to-update-a-map-using-side-by-side-versioning.md)  
  
-   [如何使用並存版本控制更新管道](../technical-guides/how-to-update-a-pipeline-using-side-by-side-versioning.md)  
  
-   [使用並存版本控制更新結構描述](../technical-guides/updating-a-schema-using-side-by-side-versioning.md)