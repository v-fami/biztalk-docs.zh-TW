---
title: 診斷追蹤和訊息記錄 Siebel 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracing, between the adapter client and the adapter
- logging, troubleshooting
- troubleshooting, tracing and message logging
- tracing, between the adapter and the LOB application
- message logging, troubleshooting
- tracing, troubleshooting
ms.assetid: fd2de692-45b7-45bc-b79c-381f3b1cf592
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ab369a74058f374ee229eb25d0697dc96f539ed
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36994575"
---
# <a name="diagnostic-tracing-and-message-logging-for-the-siebel-adapter"></a>診斷追蹤和 Siebel 配接器的訊息記錄
配接器用戶端可以啟用診斷追蹤，才能有效地診斷使用的配接器時所遇到的問題。 配接器用戶端可以啟動三個不同層級的追蹤：  
  
- 配接器用戶端與配接器  
  
- 配接器內  
  
- 配接器之間的營運 (LOB) 應用程式  
  
  本節提供啟動下列層級追蹤的相關資訊。  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a>配接器用戶端與配接器之間的追蹤  
 配接器用戶端可以啟用 WCF 追蹤，到配接器用戶端和配接器之間的追蹤問題。 WCF 追蹤用來追蹤來自配接器用戶端會使用 WCF 服務模型的輸入的 Xml，且有助於診斷序列化問題。 WCF 通道模型或從配接器至配接器用戶端的輸出訊息，不會使用 WCF 追蹤。 您可以藉由將個別的組態檔中的摘錄，來啟用 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型的應用程式。 此外，您可以啟用追蹤，在設計階段和執行階段。  
  
- **在設計階段追蹤**。 為設計階段體驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 所有這些工具可從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 因此，若要啟用追蹤的設計階段經驗，您必須將摘要加入 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。  
  
- **在執行階段追蹤**。 執行階段追蹤中，您必須將根據您使用應用程式的摘要。  
  
  - 針對[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 中的摘要。BizTalk Server 的這個檔案會位於通常\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。  
  
  - WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。  
  
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
  
 這將 C:\log\WCFTrace.svclog 的 WCF 追蹤。 [WCF 追蹤](https://msdn.microsoft.com/library/ms730342.aspx)提供詳細的資訊。
  
> [!IMPORTANT]
>  請確定您緩解潛在的安全性威脅的啟用追蹤，以公開機密商務資料。 請參閱[最佳作法來保護 Siebel 配接器](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md) 
  
## <a name="tracing-within-the-adapter"></a>追蹤配接器內  
 BizTalk Adapter Pack 中的配接器追蹤檔，例如錯誤、 警告和資訊記錄有用資訊的不同的類別。 這類資訊很有用了解配接器內的程序流程和診斷配接器的問題。 您可以啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務應用程式模型，藉由將個別的組態檔中的摘錄。 此外，您可以啟用追蹤，在設計階段和執行階段。  
  
- **在設計階段追蹤**。 為設計階段體驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 所有這些工具可從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 因此，若要啟用追蹤的設計階段經驗，您必須將摘要加入 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。  
  
- **在執行階段追蹤**。 執行階段追蹤中，您必須將根據您使用應用程式的摘要。  
  
  - 針對[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 中的摘要。BizTalk Server 的這個檔案會位於通常\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。  
  
  - WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。  
  
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
  
 這會將 WCF 追蹤儲存到 C:\log\AdapterTrace.svclog。  
  
## <a name="tracing-between-the-adapter-and-the-lob-application"></a>配接器與 LOB 應用程式之間的追蹤  
 您必須啟用追蹤配接器和診斷問題，您懷疑 LOB 應用程式中的 LOB 應用程式之間進行通訊。 配接器也相依於追蹤 （用戶端/伺服器端） 來存取這項資訊的 LOB。 開啟 LOB 追蹤的細節會排除這份文件。  
  
 此外，[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]提供的繫結屬性 (**LogData**)，如果設定為**True**且的追蹤層級設定為**Verbose**， [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]記錄配接器與 Siebel 系統之間的資訊流程。 這項資訊會記錄以及相同的追蹤檔案中的配接器追蹤。  
  
 如需有關這個繫結屬性的詳細資訊，請參閱[了解 BizTalk Adapter for Siebel 繫結屬性](../../adapters-and-accelerators/adapter-siebel/read-about-biztalk-adapter-for-siebel-binding-properties.md)。  
  
## <a name="viewing-the-traces"></a>檢視追蹤  
 您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。 如需有關此工具的詳細資訊，請參閱[使用服務追蹤檢視器檢視相互關聯的追蹤和疑難排解](https://msdn.microsoft.com/library/aa751795.aspx)。  
  
## <a name="configuring-tracking-for-biztalk-applications"></a>設定 BizTalk 應用程式的追蹤  
 BizTalk 管理主控台可讓您設定各種不同的追蹤選項，針對像是傳送埠、 接收埠。 追蹤組態設定可讓您追蹤輸入/輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。 如需有關如何設定追蹤的 BizTalk 應用程式的詳細資訊，請參閱[管理成品](../../core/managing-artifacts.md)。
  
您也可以使用 群組中樞[檢視追蹤的訊息和執行個體資料](../../core/viewing-tracked-message-and-instance-data.md)，包括追蹤的檢查清單，以及最佳作法。
  
## <a name="see-also"></a>另請參閱  
[Siebel 配接器進行疑難排解](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)