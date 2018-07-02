---
title: 步驟 8A： 設定 ADT 系統的合作對象資訊 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0d750c2-a3c6-4571-a4e1-0d0aaaa4d400
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6c1a608571c9cc3f939f9387c2e3a113273af554
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969759"
---
# <a name="step-8a-configure-party-information-for-the-adt-system"></a>步驟 8A： 設定 ADT 系統的合作對象資訊
在此步驟中，您可以設定 ADT 系統的合作對象資訊。  
  
### <a name="to-configure-the-adt-system-party-information"></a>若要設定 ADT 系統的合作對象資訊  
  
1. 在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向**新增**，然後按一下**合作對象**。  
  
2. 在 [合作對象屬性] 對話方塊中，在**名稱**方塊中，輸入**Tutorial_ADTSystem**。 （您在此方塊中輸入的值是從原始 HL7 訊息的執行個體，ADT^A03.txt MSH3）。  
  
3. 在主控台樹狀目錄中，按一下**傳送埠**。  
  
4. 在 傳送埠 窗格中，按一下 中的空白欄位**名稱**欄中，選取**Tutorial_sendAck_ADT**，然後按一下**確定**。  
  
5. 按一下 **開始**，指向**程式**，指向**Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 設定總管**。  
  
6. 在 BTAHL7 設定總管 中，選取**通知** 索引標籤。針對**的通知類型**，選取**EnhancedMode**。  
  
7. 按一下 **儲存**，然後關閉 BTAHL7 設定總管。  
  
   請繼續進行[步驟 8B： 設定 RX 系統的合作對象資訊](../../adapters-and-accelerators/accelerator-hl7/step-8b-configure-party-information-for-the-rx-system.md)。