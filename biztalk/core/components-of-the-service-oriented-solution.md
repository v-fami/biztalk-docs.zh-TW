---
title: "元件的服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service solution tutorial, pipelines
- pipelines, service solutions
- service solution tutorial, assemblies
- service solution tutorial, components [BizTalk Server]
- service solution tutorial, client applications
- assemblies, service solutions
- orchestrations, service solutions
- client applications, service solutions
- back-end systems
- service solution tutorial, orchestrations
- service solution tutorial, back-end applications
ms.assetid: 97b7b754-abfb-48f9-87bf-7fe171121166
caps.latest.revision: "22"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a50743b178f9394c74b137e265532542af2b579c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="components-of-the-service-oriented-solution"></a>元件的服務導向解決方案
本節描述服務導向解決方案的主要 BizTalk Server 元件。 下列圖表顯示解決方案的主要元件：  
  
 ![服務導向解決方案流程圖](../core/media/service-oriented-flow-diagram.gif "Service_Oriented_Flow_Diagram")  
  
 服務導向解決方案有三個協調流程版本。  
  
-   一個是其中所有三個後端應用程式都是虛設的版本  
  
-   一個是其中所有三個後端應用程式都是內嵌叫用的版本  
  
-   一個則是使用配接器連接到應用程式的版本  
  
 所有的協調流程版本都會出現在 SDK\Senarios\SO\BTSSoln\Orchestrations 目錄中。  
  
 協調流程的內嵌版本提供解決方案內要求和回應之間的最低延遲時間。  
  
 來源檔案的相關資訊，請參閱[服務導向解決方案的檔案庫存](../core/file-inventory-for-the-service-oriented-solution.md)。  
  
## <a name="orchestrations-in-the-service-oriented-solution"></a>服務導向解決方案中的協調流程  
 三個協調流程， **CustomerServiceReceiveSend**， **CustomerServiceNativeRequestResponse**，和**CustomerService**組成方案。 **CustomerServiceReceiveSend**和**CustomerServiceNativeRequestResponse**協調流程做為前端呼叫**CustomerService**協調流程。 **CustomerService**協調流程會執行大部分的工作，將要求傳送到後端應用程式、 收集回應，回應結合為單一訊息，並傳送訊息至適當前端協調流程。 由於前端協調流程呼叫**CustomerService**協調流程，因此前端協調流程等候直到**CustomerService**協調流程完成。  
  
 解決方案會公開**CustomerServiceNativeRequestResponse**為 Web 服務的協調流程。 **CustomerServiceReceiveSend**協調流程會從 MQSeries 佇列的訊息。  
  
## <a name="back-end-applications"></a>後端應用程式  
 服務導向解決方案會與三個後端應用程式通訊：  
  
-   **付款追蹤器**應用程式會傳回最近付款的模擬的清單。 **付款追蹤器**從 MQSeries 佇列讀取要求並傳送回應至另一個 MQSeries 佇列。  
  
-   **PendingTransaction**應用程式會報告根據客戶帳戶擱置的交易總數。 應用程式是 Web 服務，會接著使用 Microsoft Host Integration Server (HIS) 與大型主機電腦上的 CICS/COBOL 程式通訊。  
  
-   SAP 應用程式會提供有關客戶整個信用限制的資訊。 解決方案會連接到 SAP 應用程式以做為 Web 服務。 應用程式使用中的 SAP 配接器[!INCLUDE[adapterpacknoversion](../includes/adapterpacknoversion-md.md)]與 SAP 系統進行通訊。  
  
## <a name="pipelines"></a>管線  
 服務導向解決方案會使用預設管線，除了在兩個地方： 的接收管線**CustomerServiceReceiveSend**協調流程，而**CustomerService**協調流程的傳送管線**付款追蹤器**。 這兩個管線均使用自訂元件。  
  
 接收管線**CustomerServiceReceiveSend**包含自訂合作對象解析 」 元件， **SSO 票證發照者管線元件**。 訊息的**CustomerServiceReceiveSend**協調流程收到沒有認證。 這可模擬若訊息來自「互動式語音回應」(Interactive Voice Response) 系統時會發生的情形。 自訂管線元件會使用 BizTalk 接收主控件的服務帳戶，來新增認證。  
  
 相較之下，訊息**CustomerSericeNativeRequestResponse**協調流程收到已經具有認證。 由於 Web 服務的虛擬資料夾是針對整合式安全性所設定，而 SOAP 接收位置則是設定為要整合「企業單一登入」(SSO)，因此 SOAP 配接器會產生訊息票證。  
  
 其他的自訂管線會出現在**CustomerService**傳送管線**付款追蹤器**應用程式。 MQSeries Header Setter Pipeline Component 元件會設定兩個 MQSeries 訊息標頭屬性的值。 元件設定的第一個訊息資料格式 (**MQMD_Format**)，以指示訊息的形式**MQCIH**結構，通常用來與 CICS 程式通訊的結構。 第二個，資料本身的格式內**MQCIH**結構 (**MQCIH_Format**)，設定為 顯示訊息是一個字串。  
  
 使用**MQCIH**格式可讓您傳遞使用者 ID 和密碼在**MQCIH**結構。 SSO 分支機構應用程式會將 BizTalk 應用程式的 Windows 使用者識別碼對應至付款追蹤系統的使用者識別碼傳入**MQCIH**結構。  
  
> [!NOTE]
>  解決方案的內嵌版本可從協調流程呼叫相同的管線來使用。 這樣即可重複使用管線程式碼。  
  
## <a name="client-application"></a>用戶端應用程式  
 解決方案包含以 C# 撰寫的用戶端應用程式。 您可以使用應用程式，以 SOAP 或 MQSeries 訊息傳送要求，並檢查結果。  
  
## <a name="other-assemblies"></a>其他組件  
 應用程式包含上述摘要圖表中沒有顯示的數個輔助組件。 **公用程式**方案的組件公用程式函式。  
  
 **ErrorHelper**組件包含類別，將錯誤碼轉譯為訊息，以及將錯誤訊息轉換為錯誤碼。  
  
 **ServiceLevelTracking**組件包括 helper 方法來追蹤服務等級協定的資料使用商務活動監控 (BAM) API。  
  
 **ConfigHelper**組件包含協助程式方法，以擷取組態值，從方案**SSOConfigStore**應用程式。  
  
## <a name="see-also"></a>另請參閱  
 [開發服務導向解決方案](../core/developing-a-service-oriented-solution.md)   
 [檔案庫存服務導向解決方案](../core/file-inventory-for-the-service-oriented-solution.md)