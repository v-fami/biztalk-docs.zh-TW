---
title: "檢查清單： 設定 BizTalk Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: adfb5a5e-2a23-4f6c-865f-a3300bf3d01d
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 11c1348ef4ce34676cd206c08530f66f20730378
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="checklist-configuring-biztalk-server"></a>檢查清單： 設定 BizTalk Server
請遵循下列步驟，當您準備[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]用於[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]實際執行環境。  
  
|步驟|參考|  
|-----------|---------------|  
|設定 BizTalk 主控件和主控件執行個體。|個別傳送、 接收、 處理及追蹤功能分成多個主控件。 這會設定工作負載時提供彈性，並可讓您停止一部主機，而不會影響其他主機。 如需詳細資訊，請參閱[設定主控件和主控件執行個體](../technical-guides/configuring-hosts-and-host-instances.md)。|  
|請確定您遵守並了解 BizTalk 主控件執行個體的記憶體使用量的最大實際限制。|[32 位元 BizTalk 主控件執行個體的記憶體使用量的最大實際限制](../technical-guides/configuring-hosts-and-host-instances.md#BKMK_MemLimit)|  
|設定專用的追蹤主控件。|使用不只一個主控件追蹤的專用的主機。 這可防止裝載追蹤從具有相同的主控件上執行其他 BizTalk 成品的效能的影響。 它也可讓您不會干擾追蹤停止的其他主機。 追蹤主控件應在執行至少兩部電腦上執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]（重複性的情況下提供，其中失敗）。 如需詳細資訊，請參閱[專用追蹤主控件設定](../technical-guides/configuring-a-dedicated-tracking-host.md)。|  
|設定 SOAP、 HTTP 和 HTTP 為基礎的 WCF 配接器的同時連線數|[適用於 IIS 組態設定](../technical-guides/apply-iis-configuration-settings.md)|  
|實作 BizTalk 應用程式升級和版本控制策略。|-如果您需要支援長時間執行的協調流程，和/或您需要執行 BizTalk 應用程式部署包含無 BizTalk 應用程式停機時間，則您需要實作和練習實線、 端對端[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]版本控制策略不同的版本控制案例。<br />-如果您需要支援長時間執行的協調流程、-並存部署或無停機時間升級，您應該實作的組件版本控制和封裝策略，其中包含的建構。<br /><br /> 如需詳細資訊，請參閱[升級和應用程式的版本控制策略](../technical-guides/upgrading-and-versioning-strategies-for-applications.md)。|  
|指令碼的 BizTalk Server 應用程式部署。|BizTalk 應用程式的部署應該編寫指令碼有可能。 您應該記錄詳細的步驟與您不要的指令碼的任何項目。 如需詳細資訊，請參閱：<br /><br /> -   [使用指令碼來部署應用程式](../technical-guides/using-scripts-to-deploy-applications.md)<br />-   [管理應用程式](../technical-guides/managing-applications.md)|  
|預先定義重新提交訊息，並重新啟動工作流程程的序。|建立並檢查有已擱置的服務執行個體，並採取適當動作的程序的文件。 在大部分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，應該在執行此作業的一部分的每日維護您[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。 如需執行每日維護檢查的詳細資訊，請參閱[檢查清單： 執行每日維護檢查](../technical-guides/checklist-performing-daily-maintenance-checks.md)。|  
|定義中可能會遇到的問題的擴大路徑[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。|-判斷角色和責任<br />-定義擴大程序和路徑<br />-定義 」 (short-circuit) 處理程序和路徑時所需的 「 關鍵狀況 」 案例<br />-定義擴大路徑，如需廠商問題，包括 Microsoft 的其他軟體廠商的硬體廠商 （例如伺服器、 SAN、 交換器）|  
|使用時，某些考量遵守[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]64 位元 Windows 作業系統上|[在 64 位元 Windows 作業系統上使用 BizTalk Server 時的考量](../technical-guides/considerations-while-using-biztalk-server-on-a-64-bit-windows-operating-system.md)|  
|遵循的最佳作法[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定。|[BizTalk Server 設定的最佳做法](../technical-guides/best-practices-for-biztalk-server-settings.md)|  
  
## <a name="in-this-section"></a>本節內容  
  
-   [設定主控件和主控件執行個體](../technical-guides/configuring-hosts-and-host-instances.md)  
  
-   [專用的追蹤主控件設定](../technical-guides/configuring-a-dedicated-tracking-host.md)  
  
-   [適用於 IIS 組態設定](../technical-guides/apply-iis-configuration-settings.md)  
  
-   [升級和應用程式的版本控制方法](../technical-guides/upgrading-and-versioning-strategies-for-applications.md)  
  
-   [使用指令碼來部署應用程式](../technical-guides/using-scripts-to-deploy-applications.md)  
  
-   [在 64 位元 Windows 作業系統上使用 BizTalk Server 時的考量](../technical-guides/considerations-while-using-biztalk-server-on-a-64-bit-windows-operating-system.md)  
  
-   [BizTalk Server 設定的最佳做法](../technical-guides/best-practices-for-biztalk-server-settings.md)