---
title: 診斷追蹤和訊息記錄 SAP 配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracing, between the adapter client and adapter
- tracing, within the adapter
- tracing, between the adapter and the LOB application
- troubleshooting, tracing and logging
ms.assetid: 5c60af54-896d-4873-acbf-32fbcd051ee2
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 40204b7d8835a4cc7231cee2b20938b03042f7a3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966823"
---
# <a name="diagnostic-tracing-and-message-logging-for-the-sap-adapter"></a>診斷追蹤和 SAP 配接器的訊息記錄
診斷追蹤，可協助有效地診斷中使用配接器時可能遇到的問題。 配接器用戶端可以啟動三個層級的診斷追蹤：  
  
- 配接器用戶端與配接器  
  
- 配接器內  
  
- 配接器之間的營運 (LOB) 應用程式  
  
  本節提供啟動下列層級追蹤的相關資訊。  
  
## <a name="tracing-between-the-adapter-client-and-the-adapter"></a>配接器用戶端與配接器之間的追蹤  
 配接器用戶端可以啟用 WCF 追蹤，到配接器用戶端和配接器之間的追蹤問題。 WCF 追蹤用來追蹤輸入的 XML 來源配接器用戶端使用 WCF 服務模型，且有助於診斷序列化問題。 WCF 通道模型或從配接器至配接器用戶端的輸出訊息，不會使用 WCF 追蹤。 您可以藉由將個別的組態檔中的摘錄，來啟用 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型的應用程式。 此外，您可以啟用追蹤，在設計階段和執行階段。  
  
- **在設計階段追蹤**。 為設計階段體驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 所有這些工具可從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 因此，若要啟用追蹤的設計階段經驗，您必須將摘要加入 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。  
  
- **在執行階段追蹤**。 執行階段追蹤中，您必須將根據您使用應用程式的摘要。  
  
  - 針對[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 中的摘要。BizTalk Server 的這個檔案會位於通常\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。  
  
  - WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。  
  
  若要啟用 WCF 追蹤，加入下列摘錄中的`<configuration>`標記。  
  
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
  
 這將 C:\log\WCFTrace.svclog 的 WCF 追蹤。 如需有關 WCF 追蹤的詳細資訊，請參閱 <<c0> [ 追蹤](https://msdn.microsoft.com/library/ms730342.aspx)。 
  
> [!IMPORTANT]
>  請確定您緩解潛在的安全性威脅的啟用追蹤，以公開機密商務資料。 如需建議請參閱[最佳做法來保護 SAP 配接器](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)。  
  
## <a name="tracing-within-the-adapter"></a>追蹤配接器內  
 配接器追蹤檔，例如錯誤、 警告和資訊訊息記錄有用資訊的不同的類別。 這類資訊很有用了解配接器內的程序流程和診斷配接器的問題。 您可以啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務應用程式模型，藉由將個別的組態檔中的摘錄。 此外，您可以啟用追蹤，在設計階段和執行階段。  
  
- **在設計階段追蹤**。 為設計階段體驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 所有這些工具可從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 因此，若要啟用追蹤的設計階段經驗，您必須將摘要加入 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。  
  
- **在執行階段追蹤**。 執行階段追蹤中，您必須將根據您使用應用程式的摘要。  
  
  - 針對[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 中的摘要。BizTalk Server 的這個檔案會位於通常\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。  
  
  - WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。  
  
  若要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和 配接器追蹤，加入下列摘錄中的`<configuration>`標記。  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="Microsoft.Adapters.SAP" switchValue="Information">  
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
  
 這將 C:\log\AdapterTrace.svclog 的 WCF 追蹤。  
  
## <a name="tracing-between-the-adapter-and-the-lob-application"></a>配接器與 LOB 應用程式之間的追蹤  
 診斷您懷疑的問題相關的 LOB 應用程式中，您必須啟用追蹤配接器與 LOB 應用程式之間進行通訊。 配接器也相依於追蹤 （用戶端/伺服器端） 來存取這項資訊的 LOB。 [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]可讓配接器用戶端的連線 URI 中指定 」 RfcSdkTrace"參數開啟 SAP 系統內的追蹤。 您必須指定此參數，以啟用 RFC SDK 到 SAP 系統內的追蹤資訊流程。 如需連線 URI 的詳細資訊，請參閱[建立 SAP 系統連線 URI](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)。  
  
 此外，您也可以建立的追蹤層級設定 RFC SDK RFC_TRACE 環境變數。 RFC_TRACE 是 SAP 所定義的環境變數，並可由 RFC SDK。 如果這個變數未定義，或設為 0，RFC SDK 追蹤層級會是最低限度。 如果變數設定為 1 或 2 時，會更詳細的追蹤層級。  
  
> [!NOTE]
>  無論是否設定 RFC_TRACE 環境變數，已啟用的 RFC SDK 追蹤*只*如果"RfcSdkTrace 」 參數設定為在 連線 URI，則為 true。 這個環境變數的值只會控管 RFC SDK 追蹤層的級。 如果 RfcSdkTrace 設為 true，訊息追蹤配接器與 SAP 系統之間會複製到您電腦上的"system32"資料夾。 若要將 RFC SDK 追蹤儲存至某些其他位置，您可以設定 RFC_TRACE_DIR 環境變數。 如需這些環境變數的詳細資訊，請參閱 SAP 文件。  
  
## <a name="viewing-the-traces"></a>檢視追蹤  
 您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。 如需有關此工具的詳細資訊，請參閱[使用服務追蹤檢視器檢視相互關聯的追蹤和麻煩](https://msdn.microsoft.com/library/aa751795.aspx)。
  
## <a name="configuring-tracking-for-biztalk-applications"></a>設定 BizTalk 應用程式的追蹤  
 BizTalk Server 管理主控台可讓您設定不同的追蹤選項項目，例如傳送埠和接收埠。 追蹤組態設定可讓您追蹤輸入和輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。 如需有關如何設定追蹤的 BizTalk 應用程式的詳細資訊，請參閱[管理成品](../../core/managing-artifacts.md)。
  
 您也可以使用健全狀況與活動追蹤 (HAT) 來檢視歷史或追蹤資料。 如需詳細資訊，請參閱 <<c0> [ 檢視歷程記錄和追蹤資料](../../core/viewing-historical-and-tracked-data.md)。
 
## <a name="see-also"></a>另請參閱  
[SAP 配接器進行疑難排解](../../adapters-and-accelerators/adapter-sap/troubleshoot-the-sap-adapter.md)