---
title: "在步驟 8A： 設定合作對象資訊 ADT System_hl7_main |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 693fda8b-9a99-4a6e-89b7-294f84676350
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9683fd02f94b96ead6817c72298338c064a14cc1
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="step-8a-configure-party-information-for-the-adt-systemhl7main"></a>在步驟 8A： 設定 ADT System_hl7_main 合作對象資訊
在此步驟中，您可以設定 ADT 系統的合作對象資訊。  
  
### <a name="to-configure-the-adt-system-party-information"></a>若要設定 ADT 系統合作對象資訊  
  
1.  在 BizTalk 管理主控台中，展開**BizTalk Server 管理**，然後展開**BizTalk 群組**。 以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。  
  
2.  在 [合作對象屬性] 對話方塊中**名稱**欄位中，輸入**ADT**。 （您在此方塊中輸入的值應該符合原始 HL7 訊息執行個體，QRY^Q01.txt MSH3）。  
  
3.  在主控台樹狀目錄中，按一下**傳送埠**。  
  
4.  在**傳送埠**] 窗格中，針對**名稱**在第一個資料列中，選取**ADT_Send**，然後按一下 [ **[確定]**。  
  
5.  按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。  
  
6.  在 [BTAHL7 組態總管] 中，按一下 [**通知**] 索引標籤。如**的通知類型**，選取**EnhancedMode**。  
  
7.  在通知中的屬性 Inboiund 訊息 窗格中，針對**MSH15-接受的通知類型**，選取**AL**。  
  
8.  在通知屬性 窗格中，針對**MSH16-應用程式的通知類型**，選取**NE**。  
  
9. 按一下**儲存**，然後關閉 BTAHL7 Configuration 總管。  
  
 若要繼續[步驟 8B： 設定合作對象資訊 HI 系統](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-hi-system.md)。