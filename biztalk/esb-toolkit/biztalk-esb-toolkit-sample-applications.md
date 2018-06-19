---
title: BizTalk ESB 工具組範例應用程式 |Microsoft 文件
description: 安裝 ESB Toolkit 範例應用程式，並取得有關如何在 BizTalk Server 中使用它們的快速連結
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
ms.openlocfilehash: f9d1af5c2bc8c16ec14f8e13109f0edfe13b86cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22290686"
---
# <a name="biztalk-esb-toolkit-sample-applications"></a>BizTalk ESB 工具組範例應用程式
[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]包含數個範例應用程式，您可以安裝和執行，以查看 ESB 運作，以及如何使用某些 ESB 管線元件。 您可以調整，並修改程式碼和您自己的應用程式範例中所使用的技術。  
  
## <a name="install-the-sample-applications"></a>安裝範例應用程式  
  
1.  建立名為 c： 磁碟機的根目錄中的專案的資料夾，並建立這個資料夾內名為 Microsoft.Practices.ESB 子資料夾。  
  
    > [!NOTE]
    >  在目前版本中，支援的安裝是位於 C:\Projects\Microsoft.Practices.ESB 的資料夾中檔案的檔案。 這些範例隨附的 BizTalk 繫結檔取決於這個路徑。  
  
2.  當您安裝[ESB Toolkit](install-and-configure-the-microsoft-biztalk-esb-toolkit.md)，它包含在您指定的安裝位置中呼叫 ESBSource.zip.zip 檔案 (根據預設，C:\Program Files\\[!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)])。 程式 ESBSource.zip 檔案解壓縮到 C:\Projects\Microsoft.Practices.ESB 資料夾。 這會建立名為的資料夾**金鑰**和**來源**其中包含範例金鑰和範例原始程式碼。 來源資料夾中包含範例應用程式的原始程式碼，而且金鑰資料夾包含用來簽署組件中的範例應用程式的公用金鑰。  
  
3.  執行範例之前，移除 C:\Projects\Microsoft.Practices.ESB\ 資料夾的唯讀屬性，以便正確地安裝範例。  
  
4.  如果您不使用 PowerShell 指令碼之前，您必須以系統管理員身分開啟 PowerShell 並執行下列命令：  
  
    ```  
    set-executionpolicy unrestricted  
    ```  
  
    > [!NOTE]
    >  如需 PowerShell 的詳細資訊，請參閱[Windows PowerShell 部落格](http://go.microsoft.com/fwlink/?LinkId=187593)([http://go.microsoft.com/fwlink/?LinkId = 187593](http://go.microsoft.com/fwlink/?LinkId=187593)) 和[Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=187594) ([http://go.microsoft.com/fwlink/?LinkId = 187594](http://go.microsoft.com/fwlink/?LinkId=187594)) MSDN 上。  
  
5.  開啟以系統管理員命令提示字元並執行下列命令，以確保註冊 WCF 指令碼對應：  
  
    ```  
    C:\Windows\Microsoft.NET\Framework\v3.0\Windows Communication Foundation>ServiceModelReg.exe -r -y  
    ```  
  
> [!NOTE]
>  您需要開啟 ESBSource.zip 檔案以取得範例程式碼存取。  

## <a name="sample-applications"></a>範例應用程式  
 下列主題描述的範例應用程式，並包含額外的安裝指示，在適用情況：  
  
-   [安裝例外狀況管理範例](../esb-toolkit/installing-the-exception-management-samples.md)  
  
-   [執行修復並重新送出的自訂例外狀況處理常式範例](../esb-toolkit/running-the-repair-and-resubmit-custom-exception-handler-sample.md)  
  
-   [執行保存自訂例外狀況處理常式範例訊息](../esb-toolkit/running-the-message-persisting-custom-exception-handler-sample.md)  
  
-   [執行 BizTalk 失敗訊息路由 ESB 處理範例](../esb-toolkit/running-the-biztalk-failed-message-routing-esb-processing-sample.md)  
  
-   [安裝及執行路線上手範例](../esb-toolkit/installing-and-running-the-itinerary-on-ramp-sample.md)  
  
-   [安裝和執行 JMS MQRFH2 元件範例](../esb-toolkit/installing-and-running-the-jms-mqrfh2-component-sample.md)  
  
-   [安裝及執行 「 命名空間元件 」 範例](../esb-toolkit/installing-and-running-the-namespace-component-sample.md)  
  
-   [安裝及執行 「 轉換服務 」 範例](../esb-toolkit/installing-and-running-the-transformation-service-sample.md)  
  
-   [安裝及執行動態解析範例](../esb-toolkit/installing-and-running-the-dynamic-resolution-sample.md)  
  
-   [安裝及執行 BizTalk 作業範例](../esb-toolkit/installing-and-running-the-biztalk-operations-sample.md)  
  
-   [安裝及執行解析程式服務範例](../esb-toolkit/installing-and-running-the-resolver-service-sample.md)  
  
-   [安裝及執行分散-集中範例](../esb-toolkit/installing-and-running-the-scatter-gather-sample.md)  
  
-   [安裝及執行 「 訊息豐富 」 範例](../esb-toolkit/installing-and-running-the-message-enrichment-sample.md)  
  
-   [安裝及執行多個 Web 服務範例](../esb-toolkit/installing-and-running-the-multiple-web-services-sample.md)  
  
-   [安裝及執行設計工具擴充性範例](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md)  
  
-   [執行的例外狀況處理服務範例](../esb-toolkit/running-the-exception-handling-service-sample.md)