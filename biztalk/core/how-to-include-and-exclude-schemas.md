---
title: 如何包含和排除結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e9206458-e5d6-48d7-87a6-9471ba60dca7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8dfa1f610cef6e67f17ca14737c6ca853dd5cd16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22254342"
---
# <a name="how-to-include-and-exclude-schemas"></a>如何包含和排除結構描述
結構描述檔案可存在於 BizTalk 專案資料夾中，但不能包含在該專案中。 這類結構描述會排除在專案之外。 當您建置 BizTalk 專案時，不會編譯排除的結構描述。 本主題描述在 BizTalk 專案中包含排除的結構描述，以及從 BizTalk 專案排除結構描述所需的步驟。  
  
### <a name="to-include-a-schema-in-a-biztalk-project"></a>在 BizTalk 專案中包含結構描述  
  
1.  在 [方案總管] 中，開啟包含要在其專案資料夾中包含的結構描述之 BizTalk 專案。  
  
2.  如果所有檔案尚未都顯示，在**專案**功能表上，按一下 **顯示所有檔案**。  
  
3.  在 方案總管 中，以滑鼠右鍵按一下您想要包含，然後按一下 已排除結構描述**包含在專案**。  
  
     在 [方案總管] 中先前排除的結構描述圖示會從空的外框變成一般結構描述圖示。  
  
4.  （選擇性） 在**專案**功能表上，按一下 **顯示所有檔案**隱藏專案資料夾中不包含在專案中的所有檔案。  
  
### <a name="to-exclude-a-schema-from-a-biztalk-project"></a>從 BizTalk 專案中排除結構描述  
  
-   在 方案總管 中，以滑鼠右鍵按一下您想要排除，然後按一下 結構描述**從專案移除**。  
  
     結構描述現在已從 BizTalk 專案排除。  
  
    > [!NOTE]
    >  當您從專案排除結構描述時，並不會從檔案系統移除結構描述。 不過，當您建置專案時，不會包含結構描述。 您可以選擇是否要在專案資料夾中顯示排除的檔案，藉由切換**顯示所有檔案**工具在 [方案總管] 視窗的頂端。  
  
    > [!NOTE]
    >  若您想要從檔案系統刪除結構描述，並從專案移除結構描述檔案，則您需要刪除該結構描述。 如需有關刪除結構描述的詳細資訊，請參閱[刪除結構描述](../core/how-to-delete-schemas.md)。  
  
## <a name="see-also"></a>另請參閱  
 [管理專案中的結構描述](../core/managing-schemas-within-projects.md)