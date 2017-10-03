---
title: "災害復原的最佳作法 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: afbb0a57-0d31-4a2f-847c-02b40361c0ed
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e988055205203c5c4bc7a4d9d6e84706414967c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="best-practices-for-disaster-recovery"></a>災害復原的最佳作法
如需有關災害復原的最佳作法資訊[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，請參閱[的備份與還原最佳作法](http://go.microsoft.com/fwlink/?LinkId=151391)(http://go.microsoft.com/fwlink/?LinkId=151391) 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]協助。  
  
 **建立備份和還原計劃**  
  
-   確定您的備份計劃指定了下列項目：  
  
    -   用以儲存備份的電腦  
  
    -   用以備份系統的程式  
  
    -   您要備份的電腦  
  
    -   產生備份的排程  
  
    -   可封存備份的公司之外位置  
  
 **BizTalk Server 系統保留所有變更的記錄**  
  
-   請確定記下系統的所有變更，例如已套用的 Service Pack、Hotfix 以及 QFE。 這個動作非常重要，它可讓您的系統儘可能還原成接近硬體失敗前的狀態。  
  
 **實作下列措施來協助防止或嚴重損壞的影響降至最低**  
  
-   取得軟體和韌體更新。  
  
-   安全存放軟體磁片以便隨時取用。  
  
-   擬定主動監視伺服器的計劃。 這是非常重要，因為失敗之主控件上的協調流程執行個體可能會復原第二部主機的最多 10 分鐘的時間。  
  
-   維護硬體記錄。  
  
-   維護軟體記錄。  
  
 **在硬體或軟體層級組織中實作容錯功能**  
  
-   實作叢集及獨立磁碟容錯陣列 (RAID) 可確保您的系統能在硬體失敗之後繼續運作。  
  
 **保存在安全的位置以規則為基礎的備份媒體**  
  
-   建立排程，以定期封存備份媒體，並將封存儲存在公司外安全的位置。 這可確保您需要備份時可隨時取得備份。  
  
 **確認備份的完整性，並執行無誤**  
  
-   監視所有的備份工作，確定其成功完成，沒有任何錯誤。  
  
 **保留相同的備用硬體**  
  
-   具有相同的備用硬體，可確保您可以快速地取代才能啟動硬體故障和更快速地執行。  
  
 **文件和測試您的復原程序**  
  
-   在實際環境中執行系統之前，應該先執行損毀修復測試。 妥當計畫並執行發行前測試，將確保您的 IT 人員可復原 BizTalk Server 系統。  
  
 **訓練您的 IT 人員在嚴重損壞修復程序**  
  
-   確定您的 IT 人員隨時可在必要時復原系統。  
  
 **練習在測試環境中從備份還原**  
  
-   在測試環境中練習還原您的 BizTalk Server 系統，確保您可在失敗發生時將其還原為實際執行環境。  
  
## <a name="see-also"></a>另請參閱  
 [嚴重損壞修復](../technical-guides/disaster-recovery.md)