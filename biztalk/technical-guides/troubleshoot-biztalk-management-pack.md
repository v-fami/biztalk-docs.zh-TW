---
title: 疑難排解 BizTalk Server 管理組件 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 676fd891-ee7f-49fc-a6d7-204dc6f2f382
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 506e65565e841b4f601dc1cb8dcef64a0aeb7956
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302478"
---
# <a name="troubleshooting"></a>疑難排解
有一些您可採取來疑難排解 BizTalk Server 管理組件問題的動作：  
  
-   請確定已正確安裝 Operations Manager。  
  
-   確定已正確設定 Operations Manager 組態設定。  
  
-   請確認您匯入管理組件完整及成功。  
  
-   請確定啟用所有相關實體，例如規則和監視。  
  
-   請確定電腦群組會填入正確的電腦。 您可以使用**製作**模式**群組**在主控台中執行這項檢查的節點。  
  
-   請確定所有 SCOM 代理程式都均狀況良好。  
  
-   確定已正確設定活動訊號間隔時間，且規則已傳播到 Operations Manager 2007 R2/2012年代理程式電腦。  
  
-   請確定已正確安裝所有效能計數器。  
  
## <a name="known-issues"></a>已知問題
下表列出所有已知的問題的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Operations Manager 管理組件。  
  
|問題|Description|解決方案|  
|-----------|-----------------|----------------|  
|重新啟動之後的效能計數器相關錯誤和警告|您可能會看到效能逆相關的錯誤和警告 Operations Manager 事件記錄檔中的代理程式之後重新啟動。|管理組件發生錯誤後復原，而且會繼續運作。|  
|物件探索相關的 Operations Manager 事件記錄檔中的警告|當探索 （包括關聯性探索） 失敗時，若要尋找執行個體時，Operations Manager 事件記錄檔指出探索指令碼傳回的 null 會寫入警告。||  
|在叢集環境中的實體節點中的警示不可靠|有兩個叢集環境中監視相關聯的已知的問題：<br /><br /> -當節點從作用中變更到被動，可能不會正確反映節點及其相關的成品的監視狀態 Operations 主控台中。<br />位在叢集環境中，Operations Manager 會建立重複的狀態和警示可能顯示的虛擬節點。|在叢集環境中包含主動/被動節點。依賴虛擬節點中顯示的監視資訊。 這是因為虛擬節點一律會指向時間是在任何時間點作用中的實體節點。|  
|關聯性和相依性監視|以下是與關聯性和相依性監視器相關的已知的問題： 發生這種情況通常 BizTalk 管理組件時重新匯入已知的 SCOM 伺服器上。 然後要求使用者請參閱註解指定 」 步驟來重現行為 > 一節中先前的狀態。<br /><br /> -不會探索 BizTalk 成品之間的關聯性。<br />相依性關聯性不會如預期般顯示。<br />-彙總套件監視的狀態不會發生。<br />-即使關聯性探索某些相依性監視未初始化的。|若要解決這些問題的解決方法如下所示：<br /><br /> <ul><li>重新啟動 BizTalk 代理程式電腦上的 Operations Manager 健全狀況服務。 <br />     -或-</li><li>執行排清健全狀況服務狀態及快取的工作。 若要這樣做的步驟如下所示：<br /><br /> <ol><li>在瀏覽樹狀目錄中，選取 Operations Manager 代理程式的代理程式健全狀況狀態。</li><li>選取下的代理程式狀態正在執行的 BizTalk Server 從健全狀況服務監看員的電腦。</li><li>選取代理程式狀態下的代理程式狀態。</li><li>按一下右方面板中排清健全狀況服務狀態及快取的工作。</li><li>在 [執行工作-排清健全狀況服務狀態和快取] 對話方塊中，按一下 [執行]。</li></ol></li></ul>|  
|顯示錯誤狀態的傳送埠和接收位置|當 SSO 服務已關閉時，BizTalk Server 管理組件不會不會顯示正確的傳送埠的狀態和接收位置。||