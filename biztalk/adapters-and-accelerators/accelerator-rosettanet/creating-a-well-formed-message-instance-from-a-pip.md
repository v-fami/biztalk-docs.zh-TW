---
title: "從 PIP 建立格式正確的訊息執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- message templates
- PIPs, message templates
ms.assetid: fed3698c-25d9-40ca-878a-60171f425bec
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e16020afb17d17c8add8e973ade0cd0c5cfcbbc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-a-well-formed-message-instance-from-a-pip"></a>從 PIP 建立格式正確的訊息執行個體
本主題描述如何產生格式正確的訊息執行個體。 您可從交易夥伴介面程序 (PIP) 產生訊息執行個體的範本。 執行這個動作後，您必須修改該範本，使其格式正確，才可新增您的資料。  
  
### <a name="to-generate-a-message-instance-template-from-the-pip"></a>從 PIP 產生格式正確的訊息執行個體  
  
1.  啟動**Microsoft Visual Studio 2012**。  
  
2.  在**檔案**功能表上，指向**開啟**，然後按一下 **專案**。  
  
3.  找出\<*磁碟機*> \Program Files\Microsoft BizTalk\<版本 > Accelerator for RosettaNetSDK\Schemas，按一下**RNPIPs.btproj**，然後按一下  **開啟**。  
  
4.  在 [方案總管] 中，展開**Rnpip**，然後以滑鼠右鍵按一下您要建立執行個體的 PIP。  
  
5.  按一下**產生執行個體**。  
  
    > [!NOTE]
    >  這會產生一個以該 PIP 命名的檔案，該檔案名稱後附加上「_output」，且其副檔名為 .xml。 [輸出] 窗格中的一行陳述式會指出 [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] 產生執行個體的地方。  
  
### <a name="to-modify-the-message-instance-template"></a>修改訊息執行個體範本  
  
1.  在 [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer 中，找出包含 XML 檔案的資料夾，並按兩下檔案名稱開啟資料夾。  
  
2.  在指出 XML 版本和編碼的所有其他文字之前加入 XML 標頭標記。 例如：  
  
    ```  
    <?xml version="1.0" encoding="UTF-8" ?>  
    ```  
  
3.  在您剛才加入的程式碼行之後，加入指出 DTD 的 DOCTYPE 行。 例如，對於 3A4 Purchase Order Request 執行個體，該行應如下所示：  
  
    ```  
    <!DOCTYPE Pip3A4PurchaseOrderRequest SYSTEM "3A4_MS_V02_02_PurchaseOrderRequest.dtd">  
    ```  
  
    > [!NOTE]
    >  每個訊息執行個體都應包含要處理的 DOCTYPE 行。  
  
4.  您現在可以自訂此訊息，以符合您的商務需求。 請修改 XML 執行個體，使它不使用 XML 命名空間或命名空間前置詞。  
  
## <a name="see-also"></a>另請參閱  
 [程式設計指南](../../adapters-and-accelerators/accelerator-rosettanet/programming-guide2.md)