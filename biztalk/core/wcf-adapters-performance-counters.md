---
title: WCF 配接器效能計數器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance, WCF adapters
- performance, performance counters
- WCF adapters, performance
ms.assetid: 9feb052f-5674-419f-84ab-9b5d312a04a5
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e5b916b6212da18dcf4aa48d4ca941e23413513d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016249"
---
# <a name="wcf-adapters-performance-counters"></a>WCF 配接器效能計數器
效能計數器可讓您針對服務在網站或系統上所執行的工作，監控其特定層面。 效能計數器也可以幫助您識別和疑難排解伺服器的效能問題。 WCF 配接器本身並未提供效能計數器。 然而，監控 Windows Communication Foundation (WCF) 的效能計數器，即可量測 WCF 接收位置的效能。 若要針對 WCF 接收位置使用 WCF 效能計數器，您必須為執行接收位置之主控件執行個體啟用效能計數器。  
  
> [!NOTE]
>  WCF 傳送埠無法使用 WCF 效能計數器。  
  
 對於內含式 WCF 配接器，您可以透過 BTSNTSvc.exe.config 檔案啟用效能計數器。 若為外掛式 WCF 配接器，則可以修改 Web.config 檔案來啟用效能計數器。 WCF 效能計數器的詳細資訊，請參閱 < WCF 效能計數器 」，網址[ http://go.microsoft.com/fwlink/?LinkID=87245 ](http://go.microsoft.com/fwlink/?LinkID=87245)。  
  
## <a name="enabling-the-wcf-performance-counters-for-the-wcf-receive-locations"></a>為 WCF 接收位置啟用 WCF 效能計數器  
 對於內含式 WCF 配接器，您可以透過 BTSNTSvc.exe.config 檔案啟用效能計數器。  
  
 若為外掛式 WCF 配接器，您可以修改 Web.config 檔案 (「BizTalk WCF 服務發佈精靈」在 Web 應用程式資料夾中建立的檔案) 來啟用 WCF 追蹤  
  
 若要修改 BTSNtSvc.exe.config 或 Web.config，請開啟組態檔並設定 WCF 追蹤，如以下組態範例所示：  
  
> [!NOTE]
>  BTSNTSvc.exe.config 永遠與 BTSNTSvc.exe 檔案位於相同的目錄中，此目錄通常是 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。  
  
```  
<configuration>  
 <system.serviceModel>  
 <diagnostics performanceCounters="All" />  
 </system.serviceModel>  
 </configuration>  
```  
  
 **PerformanceCounters**屬性可以設定以啟用特定類型的效能計數器。 有效值如下：  
  
- **所有**： 所有類別的計數器 (**ServiceModelService**， **ServiceModelEndpoint**，和**ServiceModelOperation**) 會啟用。  
  
- **ServiceOnly**： 僅**ServiceModelService**類別的計數器會啟用。  
  
- **關閉**: ServiceModel * 效能計數器已停用。 這是預設值。  
  
  修改 BTSNTSvc.exe.config 檔案後，您必須重新啟動執行內含式 WCF 接收位置的主控件執行個體。  
  
## <a name="types-of-performance-counters"></a>效能計數器型別  
 WCF 效能計數器分為三種不同的層級： 服務、 端點和作業。  
  
 **服務效能計數器**  
  
 服務效能計數器會以整體的方式測量服務行為，而且可用來診斷整個服務的效能。 下找到它們**ServiceModelService 3.0.0.0**以效能監視器檢視時的效能物件。 執行個體的命名模式如下：  
  
```  
biztalkserviceinstance@<URI of a receive location>  
```  
  
 由於 WCF 配接器會為各接收位置建立個別的服務，因此也會為每個接收位置建立效能計數器執行個體。 如需有關服務類別實作 WCF 服務合約，請參閱 < **BizTalkServiceInstance 類別** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 
  
 **端點效能計數器**  
  
 端點效能計數器可讓您檢視反映端點如何接收訊息的資料。 下找到它們**ServiceModelEndpoint 3.0.0.0**以效能監視器檢視時的效能物件。 執行個體的命名模式如下：  
  
```  
biztalkserviceinstance.<WCF service contract>@<URI of a receive location>  
```  
  
 會為每個接收位置建立一個效能計數器執行個體。 在前述的模式中，WCF 服務合約的名稱，代表 WCF 配接器選擇透過接收位置接收訊息的服務合約。 如需有關 WCF 配接器從可用的 WCF 所選擇的服務合約的服務合約，請參閱 < **WCF 配接器服務合約參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。  
  
 **作業效能計數器**  
  
 找到作業效能計數器**ServiceModelOperation 3.0.0.0**以效能監視器檢視時的效能物件。 會為每個接收位置建立兩個效能計數器執行個體。 其中一個物件執行個體的命名模式如下：  
  
```  
biztalkserviceinstance.<WCF service contract>biztalksubmit@<URI of a receive location>  
```  
  
 在前述的模式中，WCF 服務合約的名稱，代表 WCF 配接器選擇透過接收位置接收訊息的服務合約。 **biztalksubmit**是服務合約中宣告的作業名稱，並造成執行階段在中繼資料建立 WSDL 作業。  
  
> [!NOTE]
>  如需有關 WCF 配接器從可用的 WCF 所選擇的服務合約的服務合約，請參閱 < **WCF 配接器服務合約參考** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。
  
 另外一個物件執行個體的命名模式如下：  
  
```  
biztalkserviceinstance.<WCF service contract><twowaymethod|onewaymethod>@<URI of a receive location>  
```  
  
 此效能計數器執行個體代表以非同步的方式處理透過接收位置內送之訊息的作業。 這個執行個體的作業名稱部分可以是**twowaymethod**或是**onewaymethod**視接收位置中所使用的 WCF 配接器類型而定。 如果您使用 Wcf-netmsmq 配接器執行個體擁有**onewaymethod**建立作業名稱。 為其他配接器， **twowaymethod**用於作業名稱部分。