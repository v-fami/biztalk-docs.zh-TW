---
title: 設定通用後援屬性，適用於 X12 和 EDIFACT 編碼的訊息 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7393d6ac-b901-43ef-a8d6-c5b0b3033257
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e6f6fa22298221369bfb2c5600bb0ef086ee167d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996759"
---
# <a name="configuring-common-fallback-properties-for-x12-and-edifact-encoded-messages"></a>設定通用後援屬性，適用於 X12 和 EDIFACT 編碼訊息
後援屬性套用至 （包括 HIPAA）-X12 和 EDIFACT 編碼交換。 當所有後援協議屬性，這些屬性會套用時，才[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]尚未判定協議的連入我們的外寄訊息解析為。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」或「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] B2B 操作員」群組成員的身分來登入。  
  
### <a name="to-set-common-global-properties"></a>若要設定通用全域屬性  
  
1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點，然後再按一下**X12 後援設定**或**EDIFACT 後援設定**。  
  
2. 在 **後援設定一般頁面**索引標籤**一般**頁面上，執行下列動作：  
  
   1. 按一下 **啟用後援設定**若要啟用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用後援協議設定，如果沒有協議解析內送或外寄訊息。  
  
      > [!IMPORTANT]
      >  如果未選取此選項，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]不會使用後援協議中設定的屬性。  
  
   2. 按一下 **啟動 EDI 報告**啟動報告所有 EDI 訊息。 這可確保訊息會顯示在狀態報告畫面底部的連結，即可顯示**群組中樞**的 BizTalk Server 管理主控台 窗格。  
  
   3. 如果您按下**啟動 EDI 報告**，按一下**儲存交易集/內容報告**，將交易集追蹤 (BizTalkDTADb) 資料庫 EDI 資料表中。  
  
   4. 按一下  **EDI 錯誤和記錄至 Windows 事件記錄檔的 EDI 引擎產生的警告**記錄產生 EDI 引擎 （EDI 管線、 批次處理協調流程、 路由協調流程等），與內容相關的錯誤/警告訊息Windows 事件檢視器的資訊。 取消選取時，這些錯誤/警告訊息就不會記錄至事件檢視器。  
  
      > [!NOTE]
      >  不論是否選取此核取方塊，系統/處理錯誤都會記錄在事件檢視器中。  
  
3. 按一下 **套用**以接受變更，再繼續進行設定，或按一下**確定**來驗證和接受變更，然後關閉對話方塊。  
  
## <a name="see-also"></a>另請參閱  
 [設定全域或後援協議屬性](../core/configuring-global-or-fallback-agreement-properties.md)