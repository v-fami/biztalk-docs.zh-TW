---
title: 步驟 8B： 設定合作對象資訊 RX 系統 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b0b34ec9-220d-4a6b-9712-54c8099b663b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8ce204ed2e892a6206f6e2db28bbccd0201e2f0f
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25960668"
---
# <a name="step-8b-configure-party-information-for-the-rx-system"></a>步驟 8B： 設定 RX 系統的合作對象資訊
在此步驟中，您可以設定 RX 系統的合作對象資訊。  
  
### <a name="to-configure-the-rx-system-party-information"></a>若要設定 RX 系統合作對象資訊  
  
1.  在 BizTalk Server 管理主控台中，以滑鼠右鍵按一下**合作對象**，指向 **新增**，然後按一下 **合作對象**。  
  
2.  在 [合作對象屬性] 對話方塊中**名稱**方塊中，輸入**Tutorial_RXSystem**。  
  
3.  在主控台樹狀目錄中，按一下**傳送埠**。  
  
4.  在 傳送埠 窗格中，按一下中的空白欄位**名稱**欄中，選取**Tutorial_sendMsg_RX**，然後按一下 **確定**。  
  
5.  按一下**啟動**，指向 **程式**，指向  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。  
  
6.  在 BTAHL7 組態總管 中，選取**MSH 對應**索引標籤，然後再執行下列動作：  
  
    |使用|動作|  
    |--------------|----------------|  
    |**MSH3**|型別**BTAHL7**左邊的文字方塊中。|  
    |**MSH5**|型別**Tutorial_RXSystem**左邊的文字方塊中。|  
  
7.  按一下**儲存**，然後關閉 [總管] 中 BTAHL7 組態。  
  
 若要繼續[步驟 8 C： 設定合作對象資訊 HI 系統](../../adapters-and-accelerators/accelerator-hl7/step-8c-configure-party-information-for-the-hi-system.md)。