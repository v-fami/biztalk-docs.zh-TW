---
title: 使用事件追蹤 Windows3 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ETW
- provider
- Receiver Logging Provider
- Transmitter Logging Provider
- controller application
- consumer application
- BTATIBCOEMSTrace command
- Event Tracing for Windows
ms.assetid: 71954431-2015-4d50-b69e-500c883b1e04
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dd37de9c38dce752f61b92e0240f7b2f2fff832
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984351"
---
# <a name="using-event-tracing-for-windows"></a>使用 Windows 追蹤的事件
Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 會將錯誤、警告與資訊訊息記錄到 Windows 事件檢視器中。 您可以使用「Windows 事件追蹤」工具來查看其他追蹤訊息。 啟動 ETW 時，它會建立一個 *.etl 檔案來接收訊息。 這個檔案是二進位格式，必須經過轉換才能讀取。 若要這樣做，您必須取用者應用程式可供解譯\*.etl 檔案，例如，tracerpt.exe 或 tracedmp.exe。 例如，tracerpt.exe 應用程式會將轉換\*成兩個文字檔的.etl 檔案： summary.txt 與 dumpfile.csv。  
  
## <a name="etw-components"></a>ETW 元件  
 「Windows 事件追蹤」有三個元件：  
  
- **控制器應用程式**： 啟用和停用提供者 （例如，tracelog.exe 或 logman.exe）。  
  
   您會將 PATH 環境變數設定成指向 tracelog.exe 的位置。 這可確保 BTATIBCO EMSTrace 呼叫可在系統中找出 tracelog.exe。 依照預設，BTATIBCO EMSTrace 會搜尋目前的路徑。  
  
  > [!NOTE]
  >  tracelog.exe 可以從 Microsoft SDK 取得，且和 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service 提供的命令相容。 如果要使用 logman.exe，請參閱 logman 文件。  
  
- **取用者應用程式**： 讀取記錄的事件。  
  
   為了讓消費者應用程式能夠讀取 etl 檔案中的事件，Windows 事件追蹤必須將事件傾印到該檔案中。 此動作通常是在控制器停用追蹤後完成的。  
  
   若要使用的取用者應用程式，而不需要停用追蹤，控制器必須啟用使用即時選項時，追蹤\<即時\>=-rt。  
  
- **提供者**： 提供事件。  
  
   BizTalk Adapter for TIBCO Enterprise Message Service 包含三種不同的提供者。 它們是在 Windows Management Instrumentation (WMI) 中註冊的。 若要在 root\WMI\EventTrace 路經中尋找已登錄的提供者，您可以使用諸如 WMI CIM Studio 這類的工具。  
  
  BizTalk Adapter for TIBCO Enterprise Message Service 有五個提供者，可讓您記錄不同種類的訊息：  
  
- **接收器記錄提供者**:\<追蹤項目\>交換器 **-接收者**。  
  
   使用 **-接收者**可從接收配接器在執行階段記錄中取得任何訊息。  
  
- **傳輸器記錄提供者**:\<追蹤項目\>交換器 **-傳輸器**。  
  
   使用 **-傳輸器**從傳輸配接器在執行階段記錄中取得任何訊息。  
  
### <a name="btatibcoemstrace-command"></a>BTATIBCOEMSTrace 命令  
 若要使用 ETW，請執行 BizTalk Adapter for TIBCO Enterprise Message Service 命令 BTATIBCOEMSTrace.cmd。 您可以下列方式使用此命令：  
  
```  
BTATIBCOEMSTrace <Trace element> -start [-cir <MB>|   
    -seq <MB>] [-rt] logfile  
BTA TIBCOEMSTrace <Trace element> -stop  
```  
  
 其中：  
  
- **\<追蹤項目\>** （必要） 是一種提供者。  
  
  可用選項如下：  
  
- **-傳輸器**  
  
- **-接收者**  
  
- **-啟動、-停止**： 啟用或停用提供者。  
  
- **-cir \<MB\>**： 檔案的大小與種類。 **-cir**是循環檔案。 **\<MB\>**： 以 mb 為單位的大小。  
  
- **-seq \<MB\>**： 檔案的大小與種類。 **-seq**是循序檔案。 **\<MB\>**： 以 mb 為單位的大小。  
  
- **-rt**： 上設定的即時模式。  
  
- **Logfile**： 記錄檔的名稱 （c:\rtlog.etl 是預設值）。  
  
  例如：  
  
```  
BTATIBCOEMSTrace -transmitter -start -cir 10 -rt c:\log\mylog.etl  
BTATIBCOEMSTrace -transmitter -stop  
```  
  
## <a name="see-also"></a>另請參閱  
 [TIBCO Enterprise Message Service 疑難排解](../core/troubleshooting-tibco-enterprise-message-service.md)