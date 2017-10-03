---
title: "低延遲案例 Optimizations1 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd2a891a-ee4b-4542-b3ce-434e2a6474be
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2957888253826845ea9a941ad7fce8fd7a2ed7f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="low-latency-scenario-optimizations"></a>低延遲案例最佳化
根據預設，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]最佳化輸送量，而不是低度延遲。 下列最佳化已套用至[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用本指南中的測試案例。  
  
> [!NOTE]  
>  這些最佳化將會改善延遲可能因此而在某些整體輸送量成本。  
  
## <a name="increase-the-biztalk-server-host-internal-message-queue-size"></a>增加 BizTalk Server 主控件的內部訊息佇列大小  
 每個 BizTalk 主控件都有它自己內部記憶體中佇列。 增加此佇列，從 100 到 1000 之間以增進效能的低延遲案例的預設值的大小。 如需修改內部訊息佇列大小值的詳細資訊，請參閱 [如何以修改預設主控件節流設定] 中[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]協助在[http://go.microsoft.com/fwlink/?LinkID=120225](http://go.microsoft.com/fwlink/?LinkID=120225)。  
  
## <a name="reduce-the-maxreceiveinterval-value-in-the-admserviceclass-table-of-the-biztalk-server-management-database"></a>減少 「 BizTalk Server 管理 」 資料庫的 adm_ServiceClass 資料表中的 MaxReceiveInterval 值  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]您可以使用輪詢機制，從其在 Messagebox 中的主控件佇列接收訊息。 **MaxReceiveInterval** BizTalk 管理 (BizTalkMgmtDb) 資料庫的 adm_ServiceClass 資料表中的值是以每個 BizTalk 主控件執行個體將等候的毫秒為單位的最大值之前它會輪詢 MessageBox。 Adm_ServiceClass 資料表包含下列服務類型的記錄：  
  
-   **XLANG/S** – BizTalk 協調流程主控件執行個體  
  
-   **Messaging InProcess** – 內含式主控件執行個體  
  
-   **MSMQT** – MSMQT 配接器主控件執行個體  
  
-   **Messaging Isolated** – 從處理序主控件執行個體，使用 HTTP、 SOAP 和特定 WCF 接收配接器處理常式  
  
 根據預設，這個值設定為 500 毫秒，這最佳化輸送量，而不是低度延遲。 在某些情況下，來降低此值可改善延遲。  
  
> [!NOTE]  
>  變更此值會影響所有類型的執行個體相關聯的服務，因此，請小心變更此值之前先評估所有的主控件執行個體上的影響。  
  
> [!NOTE]  
>  如果 Messagebox 沒有剩餘的未處理的訊息，才使用這個值。 如果沒有未處理的訊息在 messagebox 中，常數待處理項目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會嘗試處理訊息，而不會等到上輪詢延遲。 處理所有訊息之後，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會開始輪詢使用 MaxReceiveInterval 為指定的值。  
  
> [!NOTE]  
>  在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]主控件執行個體到 Messagebox 資料庫執行個體，降低此值的 MaxReceiveInterval 可能造成裝載 Messagebox 資料庫執行個體的 SQL Server 電腦上的 CPU 使用率過高的比率較高的環境。 例如，如果 MaxReceiveInterval 就會減少至較低的值 (\< 100) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]SQL Server 上的 CPU 使用率可能會升高環境中的單一 Messagebox 和主控件執行個體的 > 50，50%以上。 這種現象可能是因為持續地輪詢的主控件佇列相關聯的額外負荷很重要。 如果您 MaxReceiveInterval 的值減少到小於 100，您也應該評估 SQL Server 電腦的 CPU 使用率，這有影響。