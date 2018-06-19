---
title: 如何驗證執行個體訊息 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9f6302c6-b56b-4572-aa76-0f4c4599672a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bd0baa898f801c924cffc5a446aa1a22d063a8fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256790"
---
# <a name="how-to-validate-instance-messages"></a>如何驗證執行個體訊息
建構結構描述之後，您可以根據此結構描述，驗證您所知可正確代表這類執行個體訊息的已存在執行個體訊息，來檢查您的工作。  
  
 本主題提供此驗證工作的逐步說明。  
  
### <a name="to-validate-an-instance-message-against-a-schema"></a>依據結構描述驗證執行個體訊息  
  
1.  在 方案總管 中，結構描述中，以滑鼠右鍵按一下，然後按一下 **屬性**。  
  
2.  如有必要，在 [屬性] 視窗中，依序展開**一般**區段**一般**索引標籤上，按一下其加號 （+） 圖示。  
  
3.  在**輸入執行個體檔案名稱**屬性值欄位中，輸入檔案名稱或使用省略符號 (**...**) 按鈕來瀏覽檔案包含執行個體訊息來進行驗證的結構描述，然後按一下 [值] 欄位右端**開啟**。  
  
4.  在**方案總管 中**，結構描述名稱，以滑鼠右鍵按一下，然後按一下**驗證執行個體**。  
  
5.  在 [輸出] 視窗中檢視結果。 成功和錯誤訊息會顯示在此視窗中。  
  
> [!NOTE]
>  在某些情況下，從特定結構描述產生的執行個體訊息，可能無法通過依據該相同結構描述進行的驗證。 如需這種情況下的詳細資訊，請參閱[已知問題與結構描述產生和驗證](../core/known-issues-with-schema-generation-and-validation.md)。 通常，您會想要編輯產生的執行個體訊息和變更所含的資料，使其更能實際表現您的狀況。 然後再使用此變更過的執行個體訊息來驗證您的結構描述。  
  
## <a name="see-also"></a>另請參閱  
 [測試結構描述](../core/testing-schemas.md)   
 [結構描述驗證](../core/schema-validation1.md)   
 [執行個體訊息產生和驗證](../core/instance-message-generation-and-validation.md)