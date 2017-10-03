---
title: "使用 BAM WCF 和 WF 攔截器的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2407809-1f71-41a9-b305-722a7f86af5b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 42078eb2b1272072016ded9a117e88ddf4fda038
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-the-bam-wcf-and-wf-interceptors"></a>BAM WCF 與 WF 攔截器的已知問題
本節會提供在使用 Windows Workflow Foundation 或 Windows Communication Foundation 的 BAM 攔截器時，可能發生之已知問題的相關資訊。  
  
## <a name="intercepting-a-dynamically-generated-wcf-assembly-hosted-in-iis"></a>攔截在 IIS 中裝載的動態產生 WFC  
 當您使用 IIS 來裝載內嵌的 Windows Communication Foundation 應用程式時 (例如，指定組件來源的服務檔案)，系統便會動態產生 WCF 組件，並為其指定任意檔案名稱，並將它放置在 asp.net 暫存資料夾中。 由於攔截器組態檔需要資訊清單資訊，而且在攔截器組態檔中無法使用萬用字元或其他動態方法來指定資訊清單，所以，您必須重新編譯服務，接著再建置您的攔截組態檔，或是在部署過包含內嵌 WCF 程式碼的所有 .asp.net 網頁後，再重新部署您的攔截器組態檔。  
  
## <a name="use-of-the-bam-interceptor-for-windows-workflow-foundation-is-not-supported-in-office-and-sharepoint-server"></a>在 Office 和 Sharepoint Server 中並不支援使用 Windows Workflow Foundation 的 BAM 攔截器。  
 Office 與 Windows Sharepoint Server 兩者，都不會在初始化 WF 執行階段時讀取應用程式組態檔的內容。 因此，或許您可以針對應用程式設定 WF 適用的 BAM 攔截器，但在裝載於這些環境時，這項設定並不會載入到工作流程執行階段。  
  
## <a name="client-service-locks-when-intiating-a-distributed-transaction"></a>初始化分散式交易時的用戶端服務鎖定  
 如果服務作業不會參與由用戶端啟始的交易，而該用戶端是從交易範圍的內容叫用服務，這時可能會發生鎖死情形。如果在傳送要求之前會從用戶端收集資料，以及接收要求針對相同活動而從服務收集資料時，就更容易發生這種鎖死情形。  
  
 若要避免這種狀況，您應該依照以下所示，藉由在用戶端之 app.config 檔案的 BAM 行為擴充的用戶端 `ConnectionString` 屬性 (Attribute) 中宣告 "Enlist = false"，指定該用戶端不參與交易。  
  
```  
<behavior name="bamClientBehavior">  
  <bamClientBehaviorExtension ConnectionString="Integrated Security=SSPI;Initial Catalog=BAMPrimaryImport;Data Source=.;  Enlist=false"  PollingIntervalSec="1500" />  
</behavior>  
```  
  
## <a name="open-wcf-channel-before-sending-a-message-when-bam-interceptors-are-used"></a>使用 BAM 攔截器時先 開啟 WCF 通道再傳送訊息  
 使用 BasicHttp 繫結為 WCF 啟用 BAM 攔截器時，Proxy 應該呼叫 proxy.Open() 以明確開啟通道。 如果未明確開啟通道，BAM 攔截可能會失敗並傳回例外狀況。