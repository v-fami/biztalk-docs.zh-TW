---
title: "步驟 7： 建立範例 LOB 訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, LOB
- loopback tutorial, creating LOB message
- creating, LOB messages
- LOBs, creating messages
ms.assetid: 3023bbc0-5bc4-4e5a-a345-c3253874f0d3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1246f56615381d2627db3058dc821ba85bf8b74d
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-7-create-a-sample-lob-message"></a>步驟 7： 建立範例 LOB 訊息
在此步驟中，您將使用 LOB 應用程式公用程式建立範例商務營運系統 (LOB) 訊息。  
  
### <a name="to-create-a-sample-message-using-the-lob-application-utility"></a>若要使用 LOB 應用程式公用程式建立範例訊息  
  
1.  在[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]總管] 中，移至\<*磁碟機*\>: \Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK 資料夾，然後按兩下 [ **LOBApplication.exe**。  
  
2.  在**LOB 應用程式**對話方塊方塊中，執行下列動作：  
  
    |**使用此選項**|**若要這樣做**|  
    |------------------|--------------------|  
    |**主要設定檔名稱**|型別**首頁**。|  
    |**交易夥伴名稱**|型別**夥伴**。|  
    |**PIP 名稱**|型別**0c1**。|  
    |**PIP 版本**|型別**R01.02**。|  
    |**檔案名稱**|按一下省略符號按鈕 (**...**)，並移至\<*磁碟機*:\>\Program Files\Microsoft BizTalk\<版本\>Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances。 選取**0C1_Request.xml**從清單中的檔案，然後再按一下**開啟**。|  
    |**訊息類別**|選取**動作**從下拉式清單。|  
  
3.  在**LOB 應用程式**對話方塊中，按一下 **提交訊息**。  
  
 LOB 應用程式會針對 Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 產生訊息，以模擬 LOB 應用程式所產生的原始訊息。 您可以在 [狀態] 視窗中檢視訊息的狀態。  
  
> [!NOTE]
>  範例訊息假設「組織」和「交易夥伴」的「全球商務識別碼」(Global Business Identifier，GBI) 分別是 123456789 和 987654321。 若要使用不同的 GBI，您必須修改這些檔案的內容。  
  
## <a name="see-also"></a>請參閱  
 [步驟 8：檢視 BTARN 資料庫中的訊息](../../adapters-and-accelerators/accelerator-rosettanet/step-8-view-messages-in-the-btarn-databases.md)