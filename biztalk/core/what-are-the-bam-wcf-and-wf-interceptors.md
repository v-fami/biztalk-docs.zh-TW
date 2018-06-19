---
title: 何謂 BAM WCF 和 WF 攔截器？ | Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 198bfdc9-86ff-4017-b65f-19616deeb9f4
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c819d219a9796b485434101ee1c2f2d4be136ae0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22288886"
---
# <a name="what-are-the-bam-wcf-and-wf-interceptors"></a>何謂 BAM WCF 和 WF 攔截器？
商務活動監控 (Business Activity Monitoring，BAM) 是一組工具、API 和服務的集合，可以讓您管理彙總、警示與設定檔，並進行自動化的程序來傳送事件，以監控相關的商務計量。 這些功能結合在一起後，可以為商務程序提供了端對端的可見性，而且可以讓您持續掌握商務程序的狀態和結果。  
  
 BAM 攔截器將相同的功能擴充至 Windows Workflow Foundation (WF)、Windows Communication Foundation (WCF) 及其他執行階段環境。 藉由使用 BAM 攔截器，您可以追蹤商務程序而不需要重新編譯 WF 或 WCF 解決方案。只要透過組態檔即可完成整合。  
  
 在專案中使用 BAM WF 或 WCF 攔截器可以讓您：  
  
-   使用 BAM 入口網站來檢視在 WF 或 WCF 應用程式中執行之商務程序的資訊。  
  
-   使用 BAM 功能而不需要將其他程式碼加入應用程式。  
  
-   使用熟悉的 BizTalk Server 工具和公用程式來部署解決方案。  
  
-   針對現有和全新的 WF 與 WCF 應用程式，利用您現有的 BizTalk Server 環境。  
  
## <a name="interceptor-components"></a>攔截器元件  
 每個 BAM 攔截器的核心都有 Common Interceptor Foundation，它是一組元件，提供了針對異質環境建置自訂攔截器的基礎。 Common Interceptor Foundation 包含下列共用元件：  
  
-   **bm.exe**，BAM 部署公用程式的增強型的版本擴充為可修改攔截器組態，包括新增、 移除、 更新及清單功能。  
  
-   **CommonInterceptorConfiguration.xsd**，Common Interceptor Foundation 組態 XML 結構描述。 所有的攔截器組態至少都必須根據這個結構描述進行驗證。  
  
## <a name="windows-workflow-foundation-wf-interceptor"></a>Windows Workflow Foundation (WF) 攔截器  
 Windows Workflow Foundation 攔截器可讓您將 BAM 追蹤功能直接新增到全新和現有的 WF 應用程式中。 在將攔截器組態部署到 BAM 主要匯入資料庫，而且 WF 應用程式的每個執行個體也已設定為載入 BAM WF 攔截器之後，工作流程資料便會寫入到 BAM，而不需要額外的程式碼。 WF 攔截器提供下列功能：  
  
-   插入現有的 WF 應用程式，而不需要變更或重新編譯程式碼。  
  
-   啟用變更組態檔的執行階段偵測和支援功能。 如果偵測到攔截器組態檔的新版本，新的工作流程執行個體將會使用新組態，但是舊的工作流程執行個體仍會使用舊的組態來完成。  
  
-   支援交易。 WF 攔截器會保存追蹤的項目，保存的方式在交易上與 WF 交易一致。 只有在 WF 交易和攔截器交易順利完成時，才會保存追蹤的項目。  
  
    > [!NOTE]
    >  Windows Workflow 攔截器不支援在追蹤和保存服務中都使用相同連線的 SharedConnectionWorkflowCommitWorkBatchService。  
  
    > [!NOTE]
    >  在 BizTalk Server 中 Windows Workflow Foundation (WF) 攔截器不適用於.NET Framework 4 中的新 WF 引擎。 WF 攔截器會繼續在.NET Framework 3.5 SP2 中運作。  
  
## <a name="windows-communication-foundation-wcf-interceptor"></a>Windows Communication Foundation (WCF) 攔截器  
 Windows Communication Foundation 擱截器為 WCF 應用程式提供了 BAM 追蹤功能。 這個攔截器提供的功能包括：  
  
-   插入現有的 WCF 應用程式，而不需要變更或重新編譯程式碼。  
  
-   追蹤 WCF 服務呼叫中包含的訊息。  
  
-   從 WCF 服務呼叫的訊息中追蹤資訊。  
  
-   參與來自用戶端的交易，或是針對交易服務呼叫從內部啟動的交易。