---
title: 使用事件追蹤 Windows2 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ETW
- Event Tracing for Windows
ms.assetid: 88b91b74-2b2e-40e0-a3e9-1ebd6367abe8
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8f022035dd432e818c02289246a2d3a43849557
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980775"
---
# <a name="using-event-tracing-for-windows"></a>使用 Windows 追蹤的事件
Microsoft BizTalk Adapter for JD Edwards OneWorld 會將錯誤、警告和資訊訊息記錄至 Windows 事件檢視器。 您可以使用 Windows 事件追蹤 (ETW) 工具來檢視其他追蹤訊息。 啟動 ETW 時，它會建立一個 *.etl 檔案來接收訊息。 這個檔案是二進位格式，必須經過轉換才能讀取。 若要這樣做，您必須取用者應用程式可供解譯\*.etl 檔案： 例如，tracerpt.exe 或 tracedmp.exe。  
  
## <a name="etw-components"></a>ETW 元件  
 「Windows 事件追蹤」有三個元件：  
  
- **控制器應用程式。** 啟用與停用提供者 (例如，tracelog.exe 或 logman.exe)。  
  
   您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。 這可確保 BTAJDEdwardsOneWorldTrace 呼叫可在您的系統中找出 tracelog.exe。 BTAJDEdwardsOneWorldTrace 預設會搜尋目前的路徑。  
  
  > [!NOTE]
  >  tracelog.exe 可從 Microsoft SDK 取得，而且與 BizTalk Adapter for JD Edwards OneWorld 提供的命令相容。 若要使用 logman.exe，請參閱 logman 文件。  
  
- **取用者應用程式。** 讀取記錄的事件。  
  
   如果要讓取用者應用程式可讀取 .etl 檔案中的事件，「Windows 事件追蹤」必須將它們傾印到該檔案。 通常這是在控制器停用追蹤時完成。  
  
   若要使用的取用者應用程式，而不需要停用追蹤，控制器必須啟用使用即時選項時，追蹤**\<即時\>=-rt**。  
  
- **提供者。** 提供事件。  
  
  BizTalk Adapter for JD Edwards OneWorld 包含五個不同的提供者。 它們是在 Windows Management Instrumentation (WMI) 中註冊的。 若要在 root\WMI\EventTrace 路經中尋找已登錄的提供者，您可以使用諸如 WMI CIM Studio 這類的工具。  
  
  BizTalk Adapter for JD Edwards OneWorld 有五個提供者，可讓您記錄不同種類的訊息：  
  
- **接收器記錄提供者。** \<追蹤元素\>交換器 **-接收者**。  
  
- **接收器 Castdetail 提供者。** \<追蹤元素\>交換器 **-castDetailsReceive**。  
  
- **傳輸器記錄提供者。** \<追蹤元素\>交換器 **-傳輸器**。  
  
- **傳輸器 CastDetails 提供者。** \<追蹤元素\>交換器 **-castDetailsTransmit**。  
  
- **管理記錄提供者。** \<追蹤元素\>交換器 **-管理**。  
  
  BTAJDEOneWorldTrace 命令  
  
  若要使用 ETW，請執行 BizTalk Adapter for JD Edwards OneWorld 命令，BTAJDEOneWorldTrace.cmd。 您可以下列方式使用此命令：  
  
```  
BTAJDEOneWorldTrace <Trace element> -start [-cir <MB>|   
      -seq <MB>] [-rt] logfile  
BTAJDEOneWorldTrace <Trace element> -stop  
```  
  
 其中：  
  
- **\<追蹤項目\>** （必要） 是一種提供者。  
  
- 可用選項包括：  
  
  -   **-castDetailsTransmit**  
  
  -   **-傳輸器**  
  
  -   **-castDetailsReceive**  
  
  -   **-接收者**  
  
  -   **-管理**  
  
  -   **-啟動、-停止**： 啟用或停用提供者。  
  
  -   **-cir \<MB\>**： 檔案的大小與種類。 -cir 是循環檔案。 \<MB\>： 大小以 mb 表示。  
  
  -   **-seq \<MB\>**： 檔案的大小與種類。 -seq 是循序檔案。 \<MB\>： 大小以 mb 表示。  
  
  -   **-rt**： 上設定的即時模式。  
  
  -   **Logfile**： 記錄檔的名稱 （c:\rtlog.etl 是預設值）。  
  
  例如：  
  
```  
BTAJDEOneWorldTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTAJDEOneWorldTrace -transmitter -stop  
```  
  
## <a name="see-also"></a>另請參閱  
 [疑難排解 JD Edwards OneWorld](../core/troubleshooting-jd-edwards-oneworld.md)