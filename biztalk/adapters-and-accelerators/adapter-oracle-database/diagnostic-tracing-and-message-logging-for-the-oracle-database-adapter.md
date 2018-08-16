---
title: 診斷追蹤和訊息記錄的 Oracle 資料庫配接器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracing
- message logging
- tracing, within the adapter
- tracing, between the adapter client and the adapter
ms.assetid: 971d34e4-5609-42c6-85b9-d9b1989fc47d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e9de4c43e6f1721297b522ae76f5876731aa997
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013399"
---
# <a name="diagnostic-tracing-and-message-logging-for-the-oracle-database-adapter"></a>診斷追蹤和訊息記錄的 Oracle 資料庫配接器
診斷追蹤，可協助有效地診斷中使用配接器時可能遇到的問題。 本主題提供下列兩種支援的追蹤類型的相關資訊[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]:  
  
-   配接器用戶端與配接器之間的 WCF 追蹤  
  
-   配接器內的 WCF 追蹤  
  
## <a name="wcf-tracing-between-the-adapter-client-and-the-adapter"></a>配接器用戶端與配接器之間的 WCF 追蹤  
 配接器用戶端可以啟用 WCF 追蹤，到配接器用戶端和配接器之間的追蹤問題。 WCF 追蹤用來追蹤輸入的 XML，來自配接器用戶端使用 WCF 服務模型，並可用於診斷序列化問題。 WCF 通道模型或從配接器至配接器用戶端的輸出訊息，不會使用 WCF 追蹤。 您可以藉由將個別的組態檔中的摘錄，來啟用 WCF 追蹤的 BizTalk 應用程式和 WCF 服務模型的應用程式。 此外，您可以啟用追蹤，在設計階段和執行階段。  
  
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
  
 這將 C:\log\WCFTrace.svclog 的 WCF 追蹤。 [WCF 追蹤](https://msdn.microsoft.com/library/ms730342.aspx)提供良好的詳細資訊。
  
> [!IMPORTANT]
>  請確定您緩解潛在的安全性威脅的啟用追蹤，以公開機密商務資料。 如需建議，請參閱[最佳作法來保護 Oracle 資料庫配接器](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)
  
## <a name="wcf-tracing-within-the-adapter"></a>配接器內的 WCF 追蹤  
 配接器追蹤檔，例如錯誤、 警告和資訊訊息記錄有用資訊的不同的類別。 這類資訊很有用了解配接器內的程序流程和診斷配接器的問題。 您可以啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和配接器追蹤的 BizTalk 應用程式和 WCF 服務應用程式模型，藉由將個別的組態檔中的摘錄。 此外，您可以啟用追蹤，在設計階段和執行階段。  
  
- **在設計階段追蹤**。 為設計階段體驗，您可以使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]， [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)]，或[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]。 所有這些工具可從[!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]。 因此，若要啟用追蹤的設計階段經驗，您必須將摘要加入 devenv.exe.config 檔案位於*\<安裝磁碟機\>*: \Program Files\Microsoft Visual Studio *\<版本\>* \Common7\IDE。  
  
- **在執行階段追蹤**。 執行階段追蹤中，您必須將根據您使用應用程式的摘要。  
  
  - 針對[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式，您必須加入 BizTalk 組態檔，通常是 BTSNTSvc.exe.config 中的摘要。BizTalk Server 的這個檔案會位於通常\<安裝磁碟機\>: \Program Files\Microsoft BizTalk Server。  
  
  - WCF 服務模型.NET 應用程式，您必須將摘要加入您專案的 app.config 檔案。  
  
  若要啟用[!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)]和 配接器追蹤，加入下列摘錄中的`<configuration>`標記：  
  
```  
<system.diagnostics>  
    <sources>  
      <source name="Microsoft.ServiceModel.Channels" switchValue="Error">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name=" Microsoft.Adapters.OracleDB" switchValue="Information">  
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
  
## <a name="viewing-the-traces"></a>檢視追蹤  
 您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具來檢視追蹤。 請參閱[使用服務追蹤檢視器檢視相關追蹤並進行疑難排解](https://msdn.microsoft.com/library/aa751795.aspx)。
  
## <a name="configuring-tracking-for-biztalk-applications"></a>設定 BizTalk 應用程式的追蹤  
 BizTalk Server 管理主控台可讓您設定不同的追蹤選項項目，例如傳送埠和接收埠。 追蹤組態設定可讓您追蹤輸入和輸出事件資料、 訊息屬性、 訊息內文，以及協調流程。 [管理成品](../../core/managing-artifacts.md)包含詳細的資訊。 

  
## <a name="see-also"></a>另請參閱  
[Oracle 資料庫配接器進行疑難排解](../../adapters-and-accelerators/adapter-oracle-database/troubleshoot-the-oracle-database-adapter.md)