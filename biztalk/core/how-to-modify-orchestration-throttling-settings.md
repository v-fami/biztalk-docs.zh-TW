---
title: 如何修改協調流程節流設定 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Bts10.settings.HostOrchestration
ms.assetid: 30086994-cb55-4ff7-9940-df197e5e35ce
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f868c0b6d686871211410e8861acbdec118ac302
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-orchestration-throttling-settings"></a>如何修改協調流程節流設定
您可以使用「BizTalk 設定儀表板」來修改 BizTalk 群組中指定主控件的協調流程節流組態設定。 這些設定會套用至指派給指定主控件的所有主控件執行個體。 本主題提供修改這些設定的逐步程序。  
  
 協調流程節流設定，指定在**btsntsvc.exe.config**檔案中，使協調流程耗用太多記憶體，來限制它可以有未處理的訊息數目。 所有訊息會繼續傳遞至 MessageBox；不過，在協調流程處理一些未處理的訊息之前，已排入佇列的訊息不會傳遞至協調流程。  
  
## <a name="prerequisites"></a>必要條件  
 若要執行此作業，您必須以 BizTalk Server Administrators 群組的成員身分登入。  
  
### <a name="to-modify-the-orchestrations-throttling-settings-of-a-host"></a>修改主控件的協調流程節流設定  
  
1.  在**BizTalk Server 管理主控台**，依序展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下 **設定**。  
  
2.  在**BizTalk 設定儀表板**對話方塊**主機**索引標籤上，按一下 [**協調流程節流**] 索引標籤。  
  
3.  執行下列命令，，然後按一下**套用**以套用所做的修改，並前進到另一個索引標籤。或按一下**確定**以套用變更並結束 設定儀表板。  
  
    |使用|動作|界限值|預設值|升級邏輯|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**Host**|從下拉式清單選取代表 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 執行階段執行個體的主控件。|-|-|-|  
    |**凍結行為**|選取協調流程 (XLANG) 引擎的凍結行為。 請注意，只有在您選取「自訂」時才可編輯其他 XLANG 設定。<br /><br /> [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 會使用凍結屬性決定何時凍結和解除凍結協調流程。 在正常負載下，預設的凍結值就足夠，但在負載過重時，若要變更效能特性，您應該調整設定值。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的凍結行為主要取決於可用和使用中的記憶體數量。|永遠<br /><br /> 永不<br /><br /> Custom|Custom|-|  
  
     **以時間為基礎**  
  
    |使用|動作|界限值|預設值|升級邏輯|  
    |--------------|----------------|---------------------|-------------------|-------------------|  
    |**上限臨界值**|指定協調流程執行個體可能被凍結之前封鎖的最大閒置時間。|(閾值下限 – 整數類型的最大值]|1800 秒|-|  
    |**最小臨界值**|指定的最小的閒置時間，可能被凍結之前封鎖協調流程執行個體。|[1 – 整數類型的最大值)|1 秒|-|  
    |**訂閱**|選取此選項，以手動設定訂閱的 [暫停於] 與 [繼續於] 值。 根據預設，系統在執行階段期間會處理訂閱。|開啟、關閉|關閉|-|  
    |**在暫停**|指定希望訂閱儲存的訊息數目上限。<br /><br /> 當訂閱中等待消耗的訊息數大於或等於指定的數目時，就不會將訊息傳遞至訂閱執行個體。 最小的訊息數目會是 [繼續於] 值。<br /><br /> 例如，如果您設定**暫停**值為 100，表示協調流程有 100 個未處理的訊息，而 MessageBox 將停止傳送其他訊息。|(繼續時間 – 整數類型的最大值]。<br /><br /> 當兩者都為 0 時例外。|關閉|-|  
    |**在繼續進行**|指定您希望 MessageBox 恢復傳送訊息至訂閱的訊息數目。<br /><br /> 例如，設定**在繼續**值為 50。 當未處理訊息的協調流程的數目降到 50 個時，它會指定 MessageBox 可以繼續傳送訊息。|[0 – 整數型別的最大值)|關閉|-|  
  
    > [!NOTE]
    >  若要還原預設設定，請按一下**還原預設值**。  
  
## <a name="see-also"></a>另請參閱  
 [如何修改主控件設定](../core/how-to-modify-host-settings.md)