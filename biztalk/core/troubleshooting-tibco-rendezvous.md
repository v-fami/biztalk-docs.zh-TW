---
title: 疑難排解 TIBCO Rendezvous |Microsoft 文件
description: 使用 Windows 事件追蹤來 troubl = esdhoot Microsoft BizTalk Adapter for TIBCO Rendezvous 在 BizTalk Server
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5b7bc3ab-16fa-4e91-8730-9431473b2fb4
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 18ae8d599b67a1a572021cae0ebc9bfc64992a9b
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="troubleshoot-tibco-rendezvous"></a>對 TIBCO Rendezvous 進行疑難排解
  
## <a name="use-event-tracing-for-windows"></a>使用 Windows 事件追蹤
Microsoft BizTalk Adapter for TIBCO Rendezvous 會將錯誤、警告和資訊訊息記錄至 Windows 事件檢視器。 您可以使用「Windows 事件追蹤」工具來查看其他追蹤訊息。 啟動 ETW 時，它會建立一個 *.etl 檔案來接收訊息。 這個檔案是二進位格式，必須經過轉換才能讀取。 若要這樣做，您必須取用者應用程式可供解譯 \*.etl 檔案，例如，tracerpt.exe 或 tracedmp.exe。 例如，tracerpt.exe 應用程式會將轉換 \*.etl 檔案到兩個文字檔案︰ summary.txt 與 dumpfile.csv。  
  
## <a name="etw-components"></a>ETW 元件  
 「Windows 事件追蹤」有三個元件：  
  
-   **控制器應用程式**︰ 啟用和停用提供者 （例如，tracelog.exe 或 logman.exe）。  
  
     您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。 如此可確保 BTATIBCO RendezvousTrace 呼叫可以在系統中找到 tracelog.exe。 BTATIBCO RendezvousTrace 預設會搜尋目前的路徑。  
  
> [!NOTE]
>  tracelog.exe 可從 Microsoft SDK 取得，而且與 Microsoft BizTalk Adapter for TIBCO Rendezvous 提供的命令相容。 如果要使用 logman.exe，請參閱 logman 文件。  
  
-   **取用者應用程式**︰ 讀取記錄的事件。  
  
     為了讓消費者應用程式能夠讀取 etl 檔案中的事件，Windows 事件追蹤必須將事件傾印到該檔案中。 此動作通常是在控制器停用追蹤後完成的。  
  
     若要使用取用者應用程式，而不停用追蹤，控制器必須啟動使用即時選項時，追蹤\<即時\>=-rt。  
  
-   **提供者**︰ 提供事件。  
  
     BizTalk Adapter for TIBCO Rendezvous 包含三個不同的提供者。 它們是在 Windows Management Instrumentation (WMI) 中註冊的。 若要在 root\WMI\EventTrace 路經中尋找已登錄的提供者，您可以使用諸如 WMI CIM Studio 這類的工具。  
  
 BizTalk Adapter for TIBCO Rendezvous 有三個提供者。 這可讓您記錄不同種類的訊息：  
  
-   **接收器記錄提供者**:\<追蹤項目\>交換器**-接收者**。  
  
-   使用 **-接收者** 從已在執行階段的配接器收到的記錄檔中取得任何訊息。  
  
-   **傳輸器記錄提供者**:\<追蹤項目\>交換器**-傳輸器**。  
  
     使用 **-transmitter** 從傳輸配接器在執行階段的記錄檔中取得任何訊息。  
  
-   **管理記錄提供者 —**\<追蹤項目\>交換器**-管理**。  
  
     使用 **-管理**可瀏覽伺服器系統期間所產生的記錄檔中取得任何訊息。  
  
## <a name="btatibcorvtrace-command"></a>BTATIBCORVTrace 命令  
 若要使用 ETW，請執行 BizTalk Adapter for TIBCO Rendezvous 命令，BTATIBCORVTrace.cmd。 您可以下列方式使用此命令：  
  
```  
BTATIBCORVTrace <Trace element> -start [-cir <MB>|   
-seq <MB>] [-rt] logfile  
BTATIBCORVTrace <Trace element> -stop  
```  
  
 位置： **\<追蹤項目\>** （必要） 是提供者的類型。  
  
 可用選項如下：  
  
-   **-傳輸器**  
  
-   **-接收者**  
  
-   **-管理**  
  
-   **-start、-stop**︰ 啟用或停用提供者。  
  
-   **-cir \<MB\>**： 檔案的大小與種類。 **-cir** 是循環檔案。 **\<MB\>**： 以 mb 為單位的大小。  
  
-   **-seq \<MB\>**： 檔案的大小與種類。 **-seq** 是循序檔案。 **\<MB\>**： 以 mb 為單位的大小。  
  
-   **-rt**︰ 上設定的即時模式。  
  
-   **記錄檔**︰ 記錄檔的名稱 （c:\rtlog.etl 是預設值）。  
  
 例如：  
  
```  
BTATIBCORVTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCORVTrace -transmitter -stop  
```  
## <a name="see-more"></a>查看更多
[處理例外狀況](../core/using-biztalk-server-exception-handling4.md)  
[安全性](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)  
[架構](../core/architecture-of-biztalk-adapter-for-tibco-rendezvous.md)