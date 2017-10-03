---
title: "MSMQ 配接器的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ce77cdac-79c1-4529-8f09-0fb1f87ca037
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 67f210d0e480a311aed0bed5d50f6a827bd6ea4e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-msmq-adapter"></a>MSMQ 配接器的已知問題
本節包含可幫助您避免錯誤的資訊。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="msmq-adapter-receive-locations-do-not-process-documents"></a>MSMQ 配接器接收位置無法處理文件  
  
##### <a name="problem"></a>問題  
 MSMQ 配接器接收位置無法處理文件。  
  
##### <a name="cause"></a>原因  
 如果與執行 MSMQ 配接器接收處理常式之 BizTalk 主控件執行個體關聯的 .NET 執行緒集區中沒有足夠的可用執行緒，MSMQ 配接器接收位置就會因為執行緒嚴重短缺而無法處理文件。  
  
##### <a name="resolution"></a>解決方案  
 若要增加主控件執行個體的.NET 執行緒集區中的可用執行緒數目，請遵循**主應用程式的 CLR 裝載執行緒值**主題的章節[組態參數，會影響配接器效能](../core/configuration-parameters-that-affect-adapter-performance.md)。  
  
 因為每個 MSMQ 接收位置繫結至 MSMQ 接收處理常式需要.NET 執行緒集區的執行緒，設定**MinIOThreads**和**MinWorkerThreads**的值大於或等於MSMQ 接收位置的個數繫結至接收處理常式。 因此，將值設定**MaxIOThreads**和**MaxWorkerThreads**等於 MSMQ 數目的值繫結接收位置的接收處理常式 * 2 以允許空餘空間：  
  
|DWORD 項目|建議值|  
|-----------------|-----------------------|  
|MaxIOThreads|MSMQ 配接器接收處理常式所繫結之 MSMQ 接收位置的數目乘以 2。|  
|MaxWorkerThreads|MSMQ 配接器接收處理常式所繫結之 MSMQ 接收位置的數目乘以 2。|  
|MinIOThreads|MSMQ 配接器接收處理常式所繫結之 MSMQ 接收位置的數目。|  
|MinWorkerThreads|MSMQ 配接器接收處理常式所繫結之 MSMQ 接收位置的數目。|  
  
 這些建議值不會將其他配接器處理常式或主控件執行個體中執行的協調流程所使用的執行緒當做因子，因此，值應該隨之增加。  
  
#### <a name="msmq-adapter-receive-locations-shut-down-shortly-after-they-are-enabled"></a>MSMQ 配接器接收位置在啟用後很快就關閉  
  
##### <a name="problem"></a>問題  
 MSMQ 接收位置在啟用後很快就關閉。  
  
##### <a name="cause"></a>原因  
 如果 MSMQ 接收處理常式的主控件執行個體執行所在的相同電腦上，未執行訊息佇列服務的本機非叢集執行個體，就可能會發生這個問題。  
  
##### <a name="resolution"></a>解決方案  
 在 MSMQ 接收處理常式的主控件執行個體執行所在的電腦上，啟動訊息佇列服務。 使用 MSMQ 配接器接收處理常式時，電腦上必須已在執行訊息佇列服務的本機執行個體，即使該電腦上已有該服務的叢集執行個體在執行中。  
  
#### <a name="sc-tool-causes-error-when-attempting-to-stop-service-for-host-instance"></a>SC 工具在嘗試停止主控件執行個體的服務時導致錯誤  
  
##### <a name="problem"></a>問題  
 當您嘗試使用 SC 工具 (Sc.exe) 關閉 BizTalk 主控件執行個體的服務時，可能會收到如下錯誤訊息：  
  
 **ControlService FAILED 1053:**  
  
 **服務未啟動或控制要求能夠及時回應。**  
  
 當您收到此錯誤訊息後，BizTalk 主控件執行個體的服務即會停止。 但 SC 工具可能需要兩分鐘或更久的時間來關閉服務。  
  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 中已啟用 Microsoft Message Queuing 接收位置時，就會發生這個問題。  
  
 此外，系統記錄檔中也可能會記錄如下的錯誤訊息：  
  
 **事件類型： 錯誤**  
  
 **事件來源： 服務控制管理員**  
  
 **事件類別目錄： 無**  
  
 **事件識別碼： 7011**  
  
 **描述：**  
  
 **逾時 （30000 毫秒） 等候來自 BTSSvc$ BizTalkServerApplication 服務的交易回應。**  
  
##### <a name="resolution"></a>解決方案  
 Microsoft 已提供支援的 Hotfix。 但此 Hotfix 僅適用於更正本文所說明的問題。 只將此 Hotfix 套用在發生此特定問題的系統。 此 Hotfix 可能還會接受其他測試。 因此，如果此問題對您的影響不大，建議您靜待內含此 Hotfix 的下一個 Service Pack 推出。  
  
 若要解決此問題，請提交要求至 Microsoft Online Customer Services 以取得此 Hotfix。  
  
> [!NOTE]
>  若有其他問題發生，或需要其他方面的疑難排解，您可以建立個別的服務要求。 其他不是此 Hotfix 要解決的支援問題，將酌收適當的支援費用。  
  
## <a name="see-also"></a>另請參閱  
 [MSMQ 配接器疑難排解](../core/troubleshooting-the-msmq-adapter.md)