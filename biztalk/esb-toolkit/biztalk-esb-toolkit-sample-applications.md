---
title: BizTalk ESB 工具組範例應用程式 |Microsoft Docs
description: 安裝 ESB 工具組範例應用程式，並取得有關如何在 BizTalk Server 中使用它們的快速連結
caps.latest.revision: 5
author: MandiOhlinger
manager: anneta
ms.custom: ''
ms.date: 08/10/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 188f8e1f-26fb-4ea6-8e2e-f2ae3e46ca20
ms.author: mandia
ms.openlocfilehash: 81f44a6a34493210b44916a8a88cc85ad693480c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975511"
---
# <a name="biztalk-esb-toolkit-sample-applications"></a>BizTalk ESB 工具組範例應用程式
Microsoft BizTalk ESB 工具組包含數個範例應用程式，您可以安裝和執行以查看 ESB 運作方式，以及如何使用一些 ESB 管線元件。 您可以調整，並修改的程式碼和您自己的應用程式範例中使用的技術。  
  
## <a name="install-the-sample-applications"></a>安裝範例應用程式  
  
1. 建立名為您的 c： 磁碟機的根目錄中的專案資料夾，並建立名為 Microsoft.Practices.ESB，在此資料夾的子資料夾。  
  
   > [!NOTE]
   >  在目前的版本中，支援的安裝是位於資料夾 C:\Projects\Microsoft.Practices.ESB 檔。 BizTalk 繫結檔案所檢附的範例是根據此路徑而定。  
  
2. 當您安裝[ESB Toolkit](install-and-configure-the-microsoft-biztalk-esb-toolkit.md)，其中包含 （依預設，C:\Program Files\Microsoft BizTalk ESB 工具組），在您指定的安裝位置中呼叫 ESBSource.zip.zip 檔案。 解壓縮 ESBSource.zip 檔案到 C:\Projects\Microsoft.Practices.ESB 資料夾。 這會建立名為的資料夾**按鍵**並**來源**包含範例金鑰及範例，其中含有原始碼。 來源資料夾包含範例應用程式的原始程式碼，[金鑰] 資料夾包含用來簽署組件中的範例應用程式的公用金鑰。  
  
3. 執行範例之前，移除 C:\Projects\Microsoft.Practices.ESB\ 資料夾的唯讀屬性，以便正確地安裝範例。  
  
4. 如果您未曾使用 PowerShell 指令碼之前，您必須以系統管理員身分開啟 PowerShell 並執行下列命令：  
  
   ```  
   set-executionpolicy unrestricted  
   ```  
  
   > [!NOTE]
   >  如需有關 PowerShell 的詳細資訊，請參閱 < [Windows PowerShell 部落格](http://go.microsoft.com/fwlink/?LinkId=187593)([http://go.microsoft.com/fwlink/?LinkId=187593](http://go.microsoft.com/fwlink/?LinkId=187593)) 及[Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=187594) ([ http://go.microsoft.com/fwlink/?LinkId=187594](http://go.microsoft.com/fwlink/?LinkId=187594)) MSDN 上。  
  
5. 開啟以系統管理員命令提示字元並執行下列命令，以確保註冊 WCF 指令碼對應：  
  
   ```  
   C:\Windows\Microsoft.NET\Framework\v3.0\Windows Communication Foundation>ServiceModelReg.exe -r -y  
   ```  
  
> [!NOTE]
>  您需要開啟 ESBSource.zip 檔案以取得範例程式碼存取。  

## <a name="sample-applications"></a>範例應用程式  
 下列主題說明的範例應用程式，並包含額外的安裝指示，在適用：  
  
-   [安裝例外狀況管理範例](../esb-toolkit/installing-the-exception-management-samples.md)  
  
-   [執行修復和重新提交自訂例外狀況處理常式範例](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md)  
  
-   [執行訊息保存自訂例外狀況處理常式範例](../esb-toolkit/running-the-message-persisting-custom-exception-handler-sample.md)  
  
-   [執行 BizTalk 失敗訊息路由 ESB 處理範例](../esb-toolkit/running-the-biztalk-failed-message-routing-esb-processing-sample.md)  
  
-   [安裝和執行路線入口範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
-   [安裝和執行 JMS MQRFH2 元件範例](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md)  
  
-   [安裝和執行命名空間元件範例](../esb-toolkit/installing-and-running-the-namespace-component-sample.md)  
  
-   [安裝和執行轉換服務範例](../esb-toolkit/installing-and-running-the-transformation-service-sample.md)  
  
-   [安裝和執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [安裝和執行 BizTalk 作業範例](../esb-toolkit/installing-and-running-the-biztalk-operations-sample.md)  
  
-   [安裝和執行解析程式服務範例](../esb-toolkit/installing-and-running-the-resolver-service-sample.md)  
  
-   [安裝和執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)  
  
-   [安裝和執行訊息豐富範例](../esb-toolkit/installing-and-running-the-message-enrichment-sample.md)  
  
-   [安裝和執行多個 Web 服務範例](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)  
  
-   [安裝和執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)  
  
-   [執行例外狀況處理服務範例](../esb-toolkit/running-the-exception-handling-service-sample.md)