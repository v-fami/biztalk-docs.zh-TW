---
title: "限制字元範圍 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e12213bf-750e-43a2-998a-949fa4255b73
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 74f1399aaa828d5c23c2600ebabeb7063a982447
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="restricted-character-ranges"></a>限制的字元範圍

## <a name="overview"></a>概觀
建立一般檔案訊息的結構描述時，您可以指示 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 封鎖特定字元或某範圍的字元，使它們不會包含在任何外寄訊息中。 若要這麼做，請在 BizTalk 編輯器中，開啟將用來做為目的結構描述的結構描述。 選取**結構描述**節點並使用**限制的字元**屬性可開啟**限制的字元** 對話方塊。 輸入範圍，您想要在 BizTalk Server 傳送任何訊息中包含的字元，然後按一下**確定**。 每當 BizTalk Server 嘗試處理中指定的字元**限制的字元**處理停駐點和錯誤訊息的目的地結構描述 對話方塊就會產生。  
  
> [!NOTE]
>  在 BizTalk Server 中，字元範圍限制是「一般檔案延伸模組」的函式，因此不適用於 XML 訊息。 未來為不同類型的訊息所提供的延伸模組之間，可能在它們如何為其支援的訊息格式實作字元範圍限制的方面有所差異。  
  
## <a name="see-also"></a>另請參閱  
-  [考量當建立一般檔案訊息結構描述](../core/considerations-when-creating-flat-file-message-schemas.md)   
-  **限制的字元 (一般檔案結構描述的節點屬性**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]