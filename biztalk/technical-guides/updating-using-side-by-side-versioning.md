---
title: 更新使用來並行版本設定 |Microsoft 文件
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
ms.openlocfilehash: fe8264b76867c2f4fa3200f906e1d99975c9e0eb
ms.sourcegitcommit: 36350889f318e1f7e0ac9506dc8df794d475bda6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="updating-using-side-by-side-versioning"></a>更新使用-並存版本控制
如果您不能以排定停機時間，或有非常長時間執行協調流程執行個體，無法終止，可能需要的並存版本控制。 在這種升級，相同應用程式或應用程式成品的兩個版本會執行的並行。 .NET 執行階段原本可相同名稱但不同版本的組件部署且正在執行，而且 BizTalk Server 也可讓它。  
  
 並存版本控制的應用程式時，您想要以累加的方式，轉出主要應用程式升級，例如以供商務合作夥伴的子集一開始，而不是所有合作夥伴一次。 使用這種方式，可讓您繼續執行現有的應用程式來服務尚未使用新版本的使用者，直到您準備好完全轉入新版本為止。  
  
 與建立組件版本不同，您並非以遞增版本號碼的方式建立應用程式版本。 相反地，您會建立具有不同的名稱，從原始的應用程式的新應用程式，並填入應用程式成品的新版本。  
  
 因為有許多類型的成品 (例如，組件) 只能存在於 BizTalk 群組中的一個應用程式，所以您必須遞增已存在於群組內之任何組件的版本號碼，才可以將它們部署到新的應用程式中。  
  
 如需逐步更新應用程式或使用-並存版本控制的協調流程所需的工作，請參閱[檢查清單： 更新應用程式使用的並存版本控制](../technical-guides/checklist-updating-an-application-using-side-by-side-versioning.md)和[檢查清單： 更新協調流程使用的並存版本控制](../technical-guides/checklist-updating-an-orchestration-using-side-by-side-versioning.md)。 如需如何讓應用程式的並存部署的詳細指示，請參閱"[如何部署與現有版本的新版本的應用程式來執行的並行](http://go.microsoft.com/fwlink/?LinkId=155143)(http://go.microsoft.com/fwlink/?LinkId=155143)中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [如何使用並存版本控制更新對應](../technical-guides/how-to-update-a-map-using-side-by-side-versioning.md)  
  
-   [如何使用並存版本控制更新管道](../technical-guides/how-to-update-a-pipeline-using-side-by-side-versioning.md)  
  
-   [使用並存版本控制更新結構描述](../technical-guides/updating-a-schema-using-side-by-side-versioning.md)