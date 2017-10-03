---
title: "在來源中的空節點值執行個體訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76f9d7c8-5a82-41e9-9077-7b1ddd80a837
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2a36271f5e9d66efc8ef0c50cdc9582f4de1261
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="empty-node-values-in-source-instance-messages"></a>來源執行個體訊息中的空節點值
當您測試對應時，有時可能不想要所有結構描述節點的內容。  
  
## <a name="ceate-empty-node-values"></a>請建立空節點值  
  
1.  使用 BizTalk 總管產生執行個體資料。 如需產生執行個體資料的詳細資訊，請參閱[如何產生執行個體訊息](../core/how-to-generate-instance-messages.md)。  
  
2.  在文字編輯器中開啟輸入執行個體訊息，刪除您想要變空白的項目和屬性的資料，然後儲存已修改的執行個體檔案。  
  
3.  當結構描述已驗證和已測試時，設定 BizTalk 對應工具以使用剛才修改的檔案。 您在結構描述的 [屬性] 視窗設定檔案。 如需有關設定屬性的詳細資訊，請參閱**對應檔屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
## <a name="see-also"></a>另請參閱  
-  [如何產生執行個體訊息](../core/how-to-generate-instance-messages.md)   
-  **結構描述屬性參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]