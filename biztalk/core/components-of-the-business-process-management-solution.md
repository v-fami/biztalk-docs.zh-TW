---
title: 元件的商務處理管理解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- process management solution tutorial, back-end systems, process management solutions
- process management solution tutorial, client applications
- orchestrations, process management solutions
- adapters, process management solutions
- process management solution tutorial, adapters
- client applications, process management solutions
- process management solution tutorial, components
- process management solution tutorial, orchestrations
- pipelines, process management solutions
- process management solution tutorial, pipelines
- assemblies, process management solutions
- process management solution tutorial, assemblies
ms.assetid: e3ccebb9-b677-4c17-acd2-0f986f7bd3f0
caps.latest.revision: 22
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b63234dbf4a8dc62a620bf2b384b832e4887b0d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22234142"
---
# <a name="components-of-the-business-process-management-solution"></a>商務程序管理解決方案的元件
本節描述商務程序管理解決方案的主要 BizTalk Server 元件。 來源檔案的相關資訊，請參閱[商務程序管理解決方案的檔案庫存](../core/file-inventory-for-the-business-process-management-solution.md)。  
  
## <a name="orchestrations"></a>協調流程  
 有兩個主要的協調流程： **OrderBroker**和**OrderManager**。 **OrderBroker**協調流程接受客戶要求透過 Web 服務或是透過 FTP，批次，並將傳送回透過 Microsoft Message Queuing (MSMQ) 佇列的回覆。 要求會從**OrderBroker**至**OrderManager**。 兩個協調流程是透過 MessageBox 資料庫直接繫結。  
  
 **OrderManager**透過使用兩個非同步處理階段會執行要求**CableOrder1**和**CableOrder2**協調流程。 整體而言， **CableOrder1**和**CableOrder2**協調流程即代表單一商務程序。 不過，這個程序已經分為兩個協調流程，如此一來階段可以變更，而不會中斷訂單處理。 如需有關設計的階段，請參閱 < 分割商務程序 」 中的[商務程序管理解決方案中的部分設計原則](../core/some-design-principles-in-the-business-process-management-solution.md)。  
  
 **CableOrder1**協調流程使用**驗證**協調流程來驗證訂單，並將要求程式碼轉譯為動作呼叫分析 」 協調流程分析購物次序，然後再呼叫**Activate**，**取消**，或**變更**協調流程根據所需的動作。 **CableOrder2**協調流程會完成訂單處理藉由呼叫**完成**協調流程。 請注意， **CableOrder1**和**CableOrder2**使用**呼叫**叫用附屬協調流程圖形。  
  
> [!NOTE]
>  **取消**協調流程包含在呼叫的補償區塊**Activate**協調流程。 這可確保訂單會針對取消的要求，適當地還原為補償的一部分。  
  
 **CableOrder1**和**CableOrder2**協調流程會使用直接繫結。 這些協調流程直接繫結的相關資訊，請參閱[實作會反白顯示的商務程序管理解決方案](../core/implementation-highlights-of-the-business-process-management-solution.md)。  
  
 許多協調流程會寫入，如此才能被中斷期間處理使用**中斷**協調流程。 如需中斷機制的詳細資訊，請參閱[程序管理員邏輯](../core/process-manager-logic.md)。  
  
## <a name="back-end-applications"></a>後端應用程式  
 商務程序管理解決方案會使用所有後端應用程式的模擬。 **CableOrder1**， **CableOrder2**，和他們使用所有的協調流程採用特殊**OrderHandler**物件。 **OrderHandler**用以通訊的模擬訂單管理系統的.NET 遠端處理。 **CableProvisioningSystemClient**和**BTSScnBPMProvisioning** ( **CableProvisioningSystemServer**專案) 組件模擬的前端與後端管理系統的順序。  
  
 解決方案會使用 Windows form 應用程式， **BSTScnBPMFacilities** ( **FacilitiesSimulator**專案)，以模擬處理功能要求的 MSMQ 伺服器。  
  
 除了這些元件以外，協調流程也會在 SQL Server 資料庫中建立項目，以維護訂單與其處理的歷程記錄。  
  
## <a name="pipelines"></a>管線  
 這個解決方案僅會使用透過 BizTalk 管理主控台或繫結檔案所設定的標準預設管線。 不過，管線會大量使用個別執行個體的組態。 由 FTP 傳送之訂單的接收埠會使用個別執行個體組態來設定信封。 如需每個執行個體組態的詳細資訊，請參閱[如何部署管線](../core/how-to-deploy-pipelines.md)。  
  
## <a name="custom-adapter"></a>自訂配接器  
 解決方案會使用自訂的配接器， **OpsAdapter**、 處理中偵測到一些錯誤**OrderManager**和**ErrorHandler**協調流程。 這個解決方案會使用指定錯誤報告之連接埠上的配接器。 配接器會取得錯誤並傳送到作業系統上。 如需錯誤報告的詳細資訊，請參閱[使用失敗訊息路由](../core/using-failed-message-routing.md)。  
  
## <a name="client-application"></a>用戶端應用程式  
 解決方案包括由 C# 程式，ASP.NET Web 網頁**CSRMain.aspx**，以模擬客戶服務系統。  
  
## <a name="other-assemblies"></a>其他組件  
 解決方案會使用兩個額外的組件，**結構描述**和**公用程式**。 **結構描述**組件定義這個解決方案會使用不同的協調流程之間通訊的這類訊息**中斷**訊息。 解決方案也會使用定義在數個.NET 訊息**SchemaClasses**組件。  
  
 **公用程式**組件包括公用程式類別和方法，以協助處理訊息、 特定的例外狀況類型定義加入方案中，從 SSO 密碼存放區中，讀取組態值，以及協助進行錯誤處理。 組件也包括**Recaller**物件。  
  
 其他組件包括對應和結構描述的組件，例如**OrderBrokerMaps**， **OrderBrokerSchemas**，**對應**， **MessagingSchemas**，和**SchemaClasses**。  
  
 **ServiceLevelTracking**組件包含一般的成品與 BAM 搭配使用，以追蹤訂單和處理。 訂單處理動作階段所使用的是在**CableOrderActions**組件。  
  
## <a name="see-also"></a>另請參閱  
 [商務程序管理解決方案中的模式](../core/patterns-in-the-business-process-management-solution.md)   
 [商務程序管理解決方案中的處理](../core/processing-in-the-business-process-management-solution.md)   
 [商務程序管理解決方案的實作重點](../core/implementation-highlights-of-the-business-process-management-solution.md)   
 [監視與 BAM 商務程序管理解決方案](../core/monitoring-the-business-process-management-solution-with-bam.md)   
 [版本控制商務程序管理解決方案](../core/versioning-the-business-process-management-solution.md)   
 [商務程序管理解決方案參考](../core/business-process-management-solution-reference.md)   
 [開發商務程序管理解決方案](../core/developing-a-business-process-management-solution.md)   
 [商務程序管理解決方案的檔案庫存](../core/file-inventory-for-the-business-process-management-solution.md)