---
title: 產生和驗證訊息執行個體 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7a306846-3942-4ba1-a74e-6ead8deb0322
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 964f9bd2ee2b8bb20872bc593723cea778b5ed81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257982"
---
# <a name="instance-message-generation-and-validation"></a>產生和驗證執行個體訊息
驗證結構描述之後，您可以用它來產生範例執行個體訊息。 產生的範例執行個體訊息包含由結構描述指定的項目和屬性結構，並且在必要時產生假資料。  
  
> [!NOTE]
>  產生執行個體訊息不不夠精細，產生根據指定的數個屬性值的資料時使用的資料產生機制。 例如，如果結構描述中包含的任何值**模式**屬性，這是用於**限制**類別**欄位項目**節點和**欄位屬性**節點時其**Derived By**屬性設定為**限制**，產生的執行個體訊息不能做為輸入**驗證執行個體**作業。  
  
 若要從結構描述產生範例執行個體訊息，請使用**產生執行個體**在方案總管 中的結構描述相關聯的捷徑功能表上的命令。 執行個體訊息產生作業的結果會顯示在 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 輸出] 視窗中。  
  
> [!NOTE]
>  **產生執行個體**作業包含**驗證結構描述**作業。 若驗證失敗，則不會產生任何範例執行個體訊息。  
  
 如有關如何從結構描述，包括如何設定輸出檔案包含產生的執行個體訊息中，產生執行個體訊息的詳細逐步指示，請參閱[產生執行個體訊息](../core/how-to-generate-instance-messages.md)。  
  
> [!NOTE]
>  如果您未指定的值**根參考**屬性**結構描述**節點，BizTalk 編輯器產生結構描述中的第一個根節點的執行個體訊息。 如果您指定的值**根參考**屬性，BizTalk 編輯器會產生指定之根執行個體訊息。  
  
 若您已驗證結構描述，可以使用「BizTalk 編輯器」判斷執行個體訊息是否符合該結構描述。  
  
 若要驗證執行個體訊息結構描述，使用**驗證執行個體**在方案總管 中的結構描述相關聯的捷徑功能表上的命令。 驗證的結果會顯示在 [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] [輸出] 視窗中。  
  
> [!NOTE]
>  在某些情況下，產生的執行個體訊息無法通過針對產生該執行個體訊息的相同結構描述之驗證。 例如，如果您嘗試驗證由使用產生的執行個體訊息**產生執行個體**BizTalk 編輯器 」 以及相關的結構描述中的命令包含任何**欄位項目**節點或**欄位屬性**有的節點及其**Derived By**屬性設定為**限制**及其中使用**模式**屬性來指定對應的資料必須遵守的模式，驗證將會失敗。 這是因為不產生執行個體訊息時使用的資料產生機制不夠精細，產生的資料，根據指定的值是**模式**屬性。 還有其他狀況也會導致驗證失敗。  
  
 如需詳細的逐步指示，有關如何驗證執行個體訊息，包括如何指定執行個體訊息，進行驗證，請參閱[驗證結構描述](../core/how-to-validate-schemas-in-visual-studio.md)。  
  
## <a name="see-also"></a>另請參閱  
 [關於結構描述](../core/about-schemas.md)   
 [測試結構描述](../core/testing-schemas.md)