---
title: 其他活動可能會影響凍結行為 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed940448-d3b1-4308-9b38-887904e03bd0
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4622c77876607664b210de2581929154973b45d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22264038"
---
# <a name="other-activities-that-can-affect-dehydration-behavior"></a>可能影響凍結行為的其他活動
下列活動會直接或間接影響凍結及整體效能，所以應該列入任何測試案例的考量項目。  
  
-   **BizTalk Server 管理主控台查詢。** 這些查詢會依據查詢的類型及頻率，耗用資源並影響整體輸送量。  
  
-   **備份、 封存和清理活動。** 這些活動也會耗用資源，而應該納入任何測試實例的考量。  
  
-   **混合的 32 位元和 64 位元主控件。** 以下是在使用混合 32 位元及 64 位元的主控件時要考量的一些事項：  
  
    -   在使用量很大時，我們要測量消耗的虛擬及實體記憶體，並將其與特定閾值進行比較。 在 64 位元的系統中，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 程序會使用較多的記憶體，所以凍結原則會與使用相同系統及相同預設值的 32 位元系統不同。 請確定分隔協調流程、接收、傳送和訊息方塊主控件。  
  
         在 64 位元系統上使用預設的 32 位元閥值時，並不會有明顯的差別，只要 64 位元方塊上只有協調流程主控件。 不過，在壓力各種**MemoryThrottlingCriteria**設定應該至少兩倍或使用量 （只要有足夠的記憶體），但應該調整案例以最大化輸送量，因為有許多開始執行的因素。 您應該在使用量很大時調整凍結閥值，以找出最佳的設定。  
  
    -   凍結行為是依據每個訂閱的傳遞時間歷程記錄而定；不同訂閱的歷程記錄可能會不同，所以在調整凍結屬性值時，請將這點列入考慮。  
  
    -   當協調流程主控件服務在一個主控件上進行回收，但未在另一個主控件上回收時，歷程記錄就會不同。  
  
    -   當伺服器使用不同版本的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，會有的凍結原則兩者的差異。  
  
## <a name="see-also"></a>另請參閱  
 [BTSNTSvc.exe.config 檔案](../core/btsntsvc-exe-config-file.md)