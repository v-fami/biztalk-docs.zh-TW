---
title: "診斷追蹤和訊息記錄在 SQL 配接器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d6599b4d-5650-4592-96af-ee43fb36357d
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff799af25c6ba74301eeab19eb793c2e84fd90e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="diagnostic-tracing-and-message-logging-in-the-sql-adapter"></a>診斷追蹤和訊息記錄在 SQL 配接器
診斷追蹤可讓您有效地診斷使用配接器時，可能會遇到的問題。 配接器用戶端可以啟動兩個層級的診斷追蹤：  
  
-   配接器用戶端之間的介面卡  
  
-   配接器內  
  
 本節提供啟動下列層級追蹤的相關資訊。  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a>配接器用戶端與配接器之間的追蹤  
 配接器用戶端可以啟用 WCF 追蹤，配接器用戶端與配接器之間的追蹤問題。 WCF 追蹤用來追蹤來自配接器用戶端使用 WCF 服務模型，且有助於診斷問題序列化輸入的 XML。 WCF 追蹤不是適用於 WCF 通道模型或是從配接器至配接器用戶端的輸出訊息。 若要啟動 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，您可以加入個別的組態檔中的摘錄。 此外，您可以啟用追蹤，同時在設計階段和執行階段。  
  
-   **在執行階段追蹤**。 為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機 >*: \Program Files\Microsoft Visual Studio  *\<版本 >*\Common7\IDE。  
  
-   **在執行階段追蹤**。 進行執行階段追蹤，您必須將根據您使用應用程式的摘要。  
  
    -   如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式中，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。如[!INCLUDE[prague](../../includes/prague-md.md)]，這個檔案位在通常\<安裝磁碟機 >: \Program Files\Microsoft [!INCLUDE[prague](../../includes/prague-md.md)]。  
  
    -   WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。  
  
 若要啟用 WCF 追蹤，加入下列摘錄中的`<configuration>`標記。  
  
```  
\<system.diagnostics>  
    <sources>  
      <source name ="System.ServiceModel" switchValue="Verbose">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name ="System.ServiceModel.MessageLogging"   
              switchValue="Verbose, ActivityTracing">          
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name ="System.Runtime.Serialization" switchValue="Verbose">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
   </sources>  
   <sharedListeners>  
      <add name="xml" type="System.Diagnostics.XmlWriterTraceListener"                
           traceOutputOptions="LogicalOperationStack"   
           initializeData="C:\log\WCFTrace.svclog" />  
   </sharedListeners>  
   <trace autoflush="true" />  
  \</system.diagnostics>  
  \<system.serviceModel>  
    <diagnostics>  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="false"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="false"/>  
    </diagnostics>      
  \</system.serviceModel>  
```  
  
 這將 C:\log\WCFTrace.svclog WCF 追蹤。 如需 WCF 追蹤的詳細資訊，請參閱[追蹤](https://msdn.microsoft.com/library/ms730342.aspx)。  
  
> [!IMPORTANT]
>  請確定您減輕潛在的安全性威脅的啟用追蹤來公開敏感的商業資料。 如建議，請參閱[最佳作法來保護 SQL 配接器](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)。
  
## <a name="tracing-within-the-adapter"></a>配接器內追蹤  
 配接器追蹤檔，例如錯誤、 警告和資訊訊息記錄有用資訊的不同的類別。 這類資訊是用於了解配接器內的程序流程和診斷配接器的問題。 您可以啟動[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，方法是加入個別的組態檔的摘錄。 此外，您可以啟用追蹤，同時在設計階段和執行階段。  
  
-   **在執行階段追蹤**。 為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機 >*: \Program Files\Microsoft Visual Studio  *\<版本 >*\Common7\IDE。  
  
-   **在執行階段追蹤**。 進行執行階段追蹤，您必須將根據您使用應用程式的摘要。  
  
    -   如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式中，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。如[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]，這個檔案位在通常\<安裝磁碟機 >: \Program Files\Microsoft [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]。  
  
    -   WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。  
  
 若要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤，加入下列摘錄中的`<configuration>`標記。  
  
```  
\<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.Sql" switchValue="Information">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="xml" type="System.Diagnostics.XmlWriterTraceListener"   
   traceOutputOptions="LogicalOperationStack"   
          initializeData="C:\log\AdapterTrace.svclog" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  \</system.diagnostics>  
```  
  
 這將 C:\log\AdapterTrace.svclog WCF 追蹤。  
  
## <a name="viewing-the-traces"></a>檢視追蹤  
 您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。 如需此工具的詳細資訊，請參閱[使用服務追蹤檢視器檢視相關追蹤和麻煩](https://msdn.microsoft.com/library/aa751795.aspx)。
  
## <a name="configuring-tracking-for-biztalk-applications"></a>設定追蹤的 BizTalk 應用程式  
 BizTalk Server 管理主控台可讓您設定不同的追蹤選項項目，例如傳送埠和接收埠。 追蹤組態設定可讓您追蹤輸入和輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。 如需有關如何設定追蹤的 BizTalk 應用程式的詳細資訊，請參閱[管理成品](../../core/managing-artifacts.md)。
  
 您也可以使用健全狀況與活動追蹤 (HAT) 來檢視歷史或追蹤資料。 如需詳細資訊，請參閱[檢視歷程記錄和追蹤資料](../../core/viewing-historical-and-tracked-data.md)。
  
## <a name="see-also"></a>另請參閱  
 [SQL 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sql/troubleshoot-the-sql-adapter.md)