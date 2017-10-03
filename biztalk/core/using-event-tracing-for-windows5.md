---
title: "事件追蹤用於 Windows5 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ETW
- events, Event Tracing for Windows
- controller application
- ETW components
- consumer application
- Provider
- Event Tracing for Windows
- Event Tracing for Windows, components
- BTAPeopleSoftTrace command
ms.assetid: 330ef84b-5e2a-4b79-85a9-72271eb489d2
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bba68613c924c8ada9db13581856794543057e85
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-event-tracing-for-windows"></a>使用 Windows 事件追蹤
Microsoft BizTalk Adapter for PeopleSoft Enterprise 會將錯誤、警告與資訊訊息記錄到 Windows 事件檢視器中。 您可以使用「Windows 事件追蹤」工具來查看其他追蹤訊息。 當 ETW 啟用時，它會建立 *.etl 檔案以接收訊息。 檔案是二進位格式，必須經過轉換才能讀取。 若要這樣做，您必須具有取用者應用程式可供解譯\*.etl 檔案; 例如，tracerpt.exe 或 tracedmp.exe。  
  
## <a name="etw-components"></a>ETW 元件  
 「Windows 事件追蹤」有三個元件：  
  
-   **控制器應用程式**： 啟用和停用提供者 （例如，tracelog.exe 或 logman.exe）。  
  
     您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。 這樣可確保`BTAPeopleSoftTrace`呼叫可在系統中找到 tracelog.exe。 根據預設，BTAPeopleSoftTrace 會搜尋目前的路徑。  
  
    > [!NOTE]
    >  tracelog.exe 可以從 Microsoft SDK 取得，且和 BizTalk Adapter for PeopleSoft Enterprise 提供的命令相容。 如果要使用 logman.exe，請參閱 logman 文件。  
  
-   **取用者應用程式**： 讀取記錄的事件。  
  
     如果要讓取用者應用程式可讀取 .etl 檔案中的事件，「Windows 事件追蹤」必須將它們傾印到該檔案。 此動作通常是在控制器停用追蹤後完成的。  
  
     若要使用取用者，而不停用追蹤，控制器必須啟動使用即時選項時，追蹤\<即時 > =-rt。  
  
-   **提供者：**提供事件。  
  
     BizTalk Adapter for PeopleSoft Enterprise 有五個不同的提供者。 它們是在 Windows Management Instrumentation (WMI) 中註冊的。 若要尋找中已註冊的提供者**root\WMI\EventTrace**路徑，您可以使用 WMI CIM Studio 之類的工具。  
  
 BizTalk Adapter for PeopleSoft Enterprise 有五個提供者，可讓您記錄不同種類的訊息：  
  
-   **接收器記錄提供者**:\<追蹤項目 > 參數是**-接收者**。  
  
-   **接收器 Castdetail 提供者**:\<追蹤項目 > 參數是**-castDetailsReceive**。  
  
-   **傳輸器記錄提供者**:\<追蹤項目 > 參數是**-傳輸器**。  
  
-   **傳輸器 CastDetails 提供者**:\<追蹤項目 > 參數是**-castDetailsTransmit**。  
  
-   **管理記錄提供者**:\<追蹤項目 > 參數是**-管理**。  
  
## <a name="btapeoplesofttrace-command"></a>BTAPeopleSoftTrace 命令  
 若要使用 ETW，請執行配接器命令**BTAPeopleSoftTrace.cmd**。 您可以下列方式使用此命令：  
  
```  
BTAPeopleSoftTrace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTAPeopleSoftTrace <Trace element> -stop  
```  
  
 其中：  
  
-   \<追蹤項目 > （必要） 是提供者的類型。  
  
     選項如下：  
  
    -   **-castDetailsTransmit**  
  
    -   **-傳輸器**  
  
    -   **-castDetailsReceive**  
  
    -   **-接收者**  
  
    -   **-管理**  
  
    -   **-開始、-停止**： 啟用或停用提供者。  
  
-   **-cir \<MB >**： 檔案的大小與種類。 -cir 是循環檔案。 \<MB >： 以 mb 為單位的大小。  
  
-   **-seq \<MB >**： 檔案的大小與種類。 -seq 是循序檔案。 \<MB >： 以 mb 為單位的大小。  
  
-   **-rt**： 設定即時模式。  
  
-   **記錄檔**: （C:\rtlog.etl 是預設值） 的記錄檔的名稱。  
  
 例如：  
  
```  
BTAPeopleSoftTrace -transmitter -start -cir 10 -rt C:\log\mylog.etl  
BTAPeopleSoftTrace -transmitter -stop  
```  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 peoplesoft 問題](../core/troubleshooting-peoplesoft.md)