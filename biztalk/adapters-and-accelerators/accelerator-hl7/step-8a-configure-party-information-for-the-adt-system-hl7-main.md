---
title: 步驟 8A： 設定 ADT _hl7_main 的合作對象資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 693fda8b-9a99-4a6e-89b7-294f84676350
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f407f549404744d76eccdfe1af47f12cbb64ef82
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36971159"
---
# <a name="step-8a-configure-party-information-for-the-adt-systemhl7main"></a>步驟 8A： 設定 ADT _hl7_main 的合作對象資訊
在此步驟中，您可以設定 ADT 系統的合作對象資訊。  
  
### <a name="to-configure-the-adt-system-party-information"></a>若要設定 ADT 系統的合作對象資訊  
  
1. 在 BizTalk 管理主控台中，依序展開**BizTalk Server 管理**，然後展開**BizTalk 群組**。 以滑鼠右鍵按一下**合作對象**，指向**新增**，然後按一下**合作對象**。  
  
2. 在 [合作對象屬性] 對話方塊中，在**名稱**欄位中，輸入**ADT**。 （您在此方塊中輸入的值應該符合原始 HL7 訊息的執行個體，QRY^Q01.txt MSH3）。  
  
3. 在主控台樹狀目錄中，按一下**傳送埠**。  
  
4. 中**傳送埠**窗格中，如**名稱**在第一個資料列中，選取**ADT_Send**，然後按一下 **[確定]**。  
  
5. 按一下 **開始**，指向**程式**，指向**Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 設定總管**。  
  
6. 在 BTAHL7 設定總管 中，按一下**通知** 索引標籤。針對**的通知類型**，選取**EnhancedMode**。  
  
7. 在通知中的屬性 Inboiund 訊息 窗格中，如**MSH15-接受的通知類型**，選取**AL**。  
  
8. 在通知屬性 窗格中，如**MSH16-應用程式的通知類型**，選取**NE**。  
  
9. 按一下 **儲存**，然後關閉 BTAHL7 設定總管。  
  
   請繼續進行[步驟 8B： 設定 HI 系統的合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-hi-system.md)。