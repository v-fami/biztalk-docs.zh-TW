---
title: "診斷追蹤和訊息記錄 Siebel 配接器的 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tracing, between the adapter client and the adapter
- logging, troubleshooting
- troubleshooting, tracing and message logging
- tracing, between the adapter and the LOB application
- message logging, troubleshooting
- tracing, troubleshooting
ms.assetid: fd2de692-45b7-45bc-b79c-381f3b1cf592
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f6b27dd6d169c9ea7e5012be3e03329e6888522
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="diagnostic-tracing-and-message-logging-for-the-siebel-adapter"></a>診斷追蹤和 Siebel 配接器的訊息記錄
配接器用戶端可以啟用診斷追蹤，才能有效地診斷使用配接器時所遇到的問題。 配接器用戶端可以啟動在三個不同的層級的追蹤：  
  
-   配接器用戶端之間的介面卡  
  
-   配接器內  
  
-   配接器之間的特定業務 (LOB) 應用程式  
  
 本節提供啟動下列層級追蹤的相關資訊。  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a>配接器用戶端與配接器之間的追蹤  
 配接器用戶端可以啟用 WCF 追蹤，配接器用戶端與配接器之間的追蹤問題。 WCF 追蹤用來追蹤來自配接器用戶端會使用 WCF 服務模型的輸入的 Xml，在診斷序列化問題很有用。 WCF 追蹤不是適用於 WCF 通道模型或是從配接器至配接器用戶端的輸出訊息。 若要啟動 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，您可以加入個別的組態檔中的摘錄。 此外，您可以啟用追蹤，在設計階段和執行階段。  
  
-   **在設計階段追蹤**。 為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>*\Common7\IDE。  
  
-   **在執行階段追蹤**。 進行執行階段追蹤，您必須將根據您使用應用程式的摘要。  
  
    -   如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。BizTalk Server 的這個檔案是通常在\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。  
  
    -   WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。  
  
 若要啟用 WCF 追蹤，您必須新增下列摘錄中的`<configuration>`標記：
  
```  
<system.diagnostics>  
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
  </system.diagnostics>  
  <system.serviceModel>  
    <diagnostics>  
      <messageLogging   
           logEntireMessage="true"   
           logMalformedMessages="false"  
           logMessagesAtServiceLevel="true"   
           logMessagesAtTransportLevel="false"/>  
    </diagnostics>      
  </system.serviceModel>  
```  
  
 這將 C:\log\WCFTrace.svclog WCF 追蹤。 [WCF 追蹤](https://msdn.microsoft.com/library/ms730342.aspx)提供詳細的資訊。
  
> [!IMPORTANT]
>  請確定您減輕潛在的安全性威脅的啟用追蹤來公開敏感的商業資料。 請參閱[最佳作法來保護在 Siebel 介面卡](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md) 
  
## <a name="tracing-within-the-adapter"></a>配接器內追蹤  
 BizTalk Adapter Pack 中的介面卡登追蹤檔案，例如錯誤、 警告和資訊的有用資訊的不同類別。 這類資訊是用於了解配接器內的程序流程和診斷配接器的問題。 您可以啟動[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務模型應用程式，方法是加入個別的組態檔的摘錄。 此外，您可以啟用追蹤，在設計階段和執行階段。  
  
-   **在設計階段追蹤**。 為設計階段經驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 所有這些工具可以從使用[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 因此，若要啟用的設計階段經驗的追蹤，您必須加入摘要內的 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>*\Common7\IDE。  
  
-   **在執行階段追蹤**。 進行執行階段追蹤，您必須將根據您使用應用程式的摘要。  
  
    -   如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入至 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 的摘錄。BizTalk Server 的這個檔案是通常在\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。  
  
    -   WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。  
  
 若要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤，您必須新增下列摘錄中的`<configuration>`標記：  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.Siebel" switchValue="Information">  
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
  </system.diagnostics>  
```  
  
 這樣會將 WCF 追蹤儲存至 C:\log\AdapterTrace.svclog。  
  
## <a name="tracing-between-the-adapter-and-the-lob-application"></a>配接器與 LOB 應用程式之間的追蹤  
 您必須啟用追蹤，配接器與 LOB 應用程式，以診斷的問題，您懷疑內 LOB 應用程式之間的通訊。 配接器也會取決於 LOB 追蹤 （用戶端/伺服器端） 來存取這項資訊。 開啟 LOB 追蹤的細節會排除這份文件。  
  
 此外，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]提供的繫結屬性 (**LogData**)，在設定為**True**而追蹤層級設定為**Verbose**、 [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]記錄介面卡與 Siebel 系統之間的資訊流程。 這項資訊會記錄以及相同的追蹤檔案中的配接器追蹤。  
  
 如需此繫結屬性的詳細資訊，請參閱[閱讀 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
## <a name="viewing-the-traces"></a>檢視追蹤  
 您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。 如需此工具的詳細資訊，請參閱[使用服務追蹤檢視器檢視相關追蹤和疑難排解](https://msdn.microsoft.com/library/aa751795.aspx)。  
  
## <a name="configuring-tracking-for-biztalk-applications"></a>設定追蹤的 BizTalk 應用程式  
 BizTalk 管理主控台可讓您設定各種追蹤選項，針對像是傳送埠、 接收埠。 追蹤組態設定可讓您追蹤輸入/輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。 如需有關如何設定追蹤的 BizTalk 應用程式的詳細資訊，請參閱[管理成品](../../core/managing-artifacts.md)。
  
您也可以使用 群組中樞[檢視追蹤的訊息和執行個體資料](../../core/viewing-tracked-message-and-instance-data.md)，包括追蹤檢查清單和最佳作法。
  
## <a name="see-also"></a>請參閱  
[Siebel 配接器進行疑難排解](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)