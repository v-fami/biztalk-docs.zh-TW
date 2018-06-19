---
title: 啟用錯誤報告 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1131bbd5-7ab3-4422-b6df-747c722f0b2c
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca862a57bfd2389f3be2b7ff6932ed356232abc8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241246"
---
# <a name="enabling-error-reporting"></a>啟用錯誤報告
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 可讓您選擇是否要在 Windows 事件檢視器中顯示增強型錯誤和警告。  
  
 下列程序可啟用或停用 EDI 報告機制或 EDI 引擎所產生的錯誤或警告報告。 您可以在一般協議或後援協議中，啟用這類錯誤或警告的報告功能。 在一般協議中，預設會啟用此報告功能。 在後援協議中，預設會停用此報告功能。 不過，系統/處理所產生的錯誤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]一定都會記錄在事件檢視器 (輸入顯示`eventvwr`中**執行**對話方塊)，無論是否啟用 EDI 錯誤或警告。  
  
## <a name="prerequisites"></a>必要條件  
 您必須以「[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 系統管理員」群組的成員身分登入。  
  
### <a name="to-enable-error-reporting-for-an-agreement"></a>若要啟用一般協議中的錯誤報告  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]和**BizTalk 群組**節點，按一下**合作對象**節點。  
  
2.  在**合作對象與商務設定檔** 窗格中，按一下您要啟用記錄錯誤和警告事件記錄檔的 X12 或 EDIFACT 協議的合作對象。  
  
    > [!NOTE]
    >  若為 AS2 協議，您無法將錯誤與警告記錄至事件檢視器。  
  
3.  在**協議**區段中，以滑鼠右鍵按一下您要啟用記錄錯誤和警告，然後按一下 X12 或 EDIFACT 協的議**屬性**。  
  
4.  在**一般主控件設定**區段中，按一下**錯誤記錄到事件記錄檔**或**記錄到事件記錄檔的警告**。  
  
5.  按一下**確定**或按一下**套用**。  
  
### <a name="to-enable-error-reporting-as-part-of-a-fallback-agreement"></a>若要啟用後援協議中的錯誤報告功能  
  
1.  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**合作對象**節點下的**BizTalk 群組**節點，然後再按一下**X12 後援設定**或**EDIFACT 後援設定**。  
  
2.  在**後援設定一般頁面**索引標籤上，若要啟用記錄的 EDI 錯誤或警告 BizTalk EDI 引擎產生的按一下**EDI 錯誤和記錄到 Windows 事件記錄檔EDI引擎產生的警告**. 錯誤記錄檔中將會包含錯誤資料和內容資訊。  
  
    > [!NOTE]
    >  不論是否選取此核取方塊，系統/處理錯誤都會記錄在事件檢視器中。  
  
    > [!NOTE]
    >  您沒有選取**啟動 EDI 報告**屬性，就可以選取**EDI 錯誤和記錄到 Windows 事件記錄檔的 EDI 引擎產生的警告**屬性。  
  
## <a name="see-also"></a>另請參閱  
 [監控 EDI 和 AS2 解決方案](../core/monitoring-edi-and-as2-solutions.md)   
 [EDI 通知錯誤代碼](../core/edi-acknowledgment-error-codes.md)   
 [AS2 事件](../core/as2-events.md)