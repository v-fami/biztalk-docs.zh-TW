---
title: 如何診斷 WCF 配接器的問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 997a4ecd-6077-45d6-82d3-3f658ca62fd4
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c9bcb513704753363e054d689d2409925ffcd483
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995383"
---
# <a name="how-to-diagnose-problems-with-the-wcf-adapters"></a>如何診斷 WCF 配接器問題
本章節包含的步驟可協助您診斷 WCF 配接器的問題。  
  
### <a name="check-the-iis-log-and-httperr-log-of-the-iis-server-for-errors"></a>檢查 IIS 伺服器的 IIS 記錄和 HTTPERR 記錄中是否記載發生的錯誤  
  
- IIS 伺服器來源或目標記錄檔可能包含疑難排解外掛式 WCF 配接器問題的實用資訊。 根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 電腦上的 IIS 記錄檔位於下列目錄：  
  
   <em>%Windir%\\</em>system32\LogFiles\W3SVC1\  
  
  > [!NOTE]
  >  *%Windir%* 預留位置代表的位置[!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]目錄在 IIS 伺服器上。  
  
   根據預設，[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 和 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上的 HTTPERR 記錄檔位於下列目錄：  
  
  > [!NOTE]
  >  只有在 [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 和 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上才能使用 HTTPERR 記錄檔。  
  
   <em>%Windir%\\</em>system32\LogFiles\HTTPERR\  
  
### <a name="use-wcf-message-logging-for-fault-monitoring-and-diagnosis-of-problems-from-the-wcf-adapters"></a>使用 WCF 訊息記錄，進行 WCF 配接器問題的錯誤監控與診斷  
  
1. WCF 能夠記錄內送與外寄訊息的離線耗用量。 您可以使用訊息記錄，瞭解訊息如何透過 WCF 配接器進行內送和外寄。 依預設，WCF 不會記錄訊息。 若要啟動訊息記錄，您必須修改 WCF 配接器所使用的組態檔。 如需有關 WCF 訊息記錄的詳細資訊，請參閱 < 訊息記錄 >，網址[ http://go.microsoft.com/fwlink/?LinkId=89003 ](http://go.microsoft.com/fwlink/?LinkId=89003)。  
  
2. 內含式 WCF 配接器，您可以藉由修改應用程式組態檔中，啟用 WCF 訊息記錄**BTSNtSvc.exe.config**，如**BTSNtSvc.exe**。 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝路徑中即可找到組態檔。 若將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝於預設位置，BtsNtSvc.exe 就位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] 目錄中。  
  
3. 外掛式 WCF 配接器中，您可以啟用 WCF 訊息記錄，藉由修改**Web.config** BizTalk WCF 服務發佈精靈建立 Web 應用程式資料夾中的檔案。  
  
4. 若要修改**BTSNtSvc.exe.config**或是**Web.config**使用 「 記事本 」 中開啟組態檔，然後設定 WCF 訊息記錄，如下列組態範例所示：  
  
   ```  
   <configuration>  
     <system.serviceModel>  
       <diagnostics>  
         <messageLogging   
              logEntireMessage="true"   
              logMalformedMessages="false"  
              logMessagesAtServiceLevel="true"   
              logMessagesAtTransportLevel="true"  
              maxMessagesToLog="300000"  
              maxSizeOfMessageToLog="200000"   
       />  
       </diagnostics>  
     </system.serviceModel>  
  
     <system.diagnostics>  
       <sources>  
         <source name="System.ServiceModel.MessageLogging">  
           <listeners>  
             <add name="messages"  
             type="System.Diagnostics.XmlWriterTraceListener"  
             initializeData="c:\wcfTrace.e2e" />  
           </listeners>  
         </source>  
       </sources>  
     </system.diagnostics>  
   </configuration>  
   ```  
  
5. 您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具分析 WCF 所記錄的訊息。 Windows Vista 和 [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 執行階段元件的 Microsoft Windows 軟體開發套件 (SDK) 內含服務追蹤檢視器。 您可以從 Microsoft 下載中心下載 Windows SDK [ http://go.microsoft.com/fwlink/?LinkID=75636 ](http://go.microsoft.com/fwlink/?LinkID=75636)。 如需使用此工具的詳細資訊，請參閱 「 服務追蹤檢視器工具 (Svctraceviewer.exe [ http://go.microsoft.com/fwlink/?LinkId=88991 ](http://go.microsoft.com/fwlink/?LinkId=88991)。  
  
### <a name="return-managed-exception-information-to-the-client-in-a-soap-fault-to-ease-debugging"></a>將 Managed 例外狀況資訊傳回 SOAP 錯誤中的用戶端以便偵錯  
  
1. 您可以選取**錯誤中包含例外狀況**選項標準的 WCF 接收位置，以受管理的例外狀況資訊傳回 SOAP 錯誤中的用戶端以便偵錯。 使用下列步驟來選取**錯誤中包含例外狀況**選項。  
  
   1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，展開**BizTalk 群組**，展開**應用程式**，展開**接收位置**，以滑鼠右鍵按一下使用標準 WCF 配接器的接收位置，然後按一下**屬性**。  
  
   2. 在 [**接收位置屬性**] 對話方塊中，按一下**設定**。  
  
   3. 在 [傳輸] 對話方塊中，在**訊息**索引標籤上，選取**錯誤中包含例外狀況**選項。  
  
2. 如果您使用 Wcf-custom 或 Wcf-customisolated 配接器，您可以設定**IncludeExceptionDetailInFaults**屬性[ServiceDebugElement](http://go.microsoft.com/fwlink/?LinkId=89004)傳回 managed 例外狀況資訊用戶端。 若要這樣做，請使用下列步驟：  
  
   1. 在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，展開**BizTalk 群組**，展開**應用程式**，展開**接收位置**，以滑鼠右鍵按一下使用 Wcf-custom 或 Wcf-customisolated 配接器的接收位置，然後按一下**屬性**。  
  
   2. 在 [**接收位置屬性**] 對話方塊中，按一下**設定**。  
  
   3. 在 [傳輸] 對話方塊中，在**行為**索引標籤上，以滑鼠右鍵按一下**ServiceBehavior**節點，然後再按一下**新增擴充功能**。  
  
   4. 在 **選取行為延伸模組** 對話方塊中，選取**serviceDebug**，然後按一下 **確定**。  
  
   5. 在 傳輸 對話方塊中，在**行為**索引標籤上，按一下  **serviceDebug**節點，然後再選取 **，則為 True**如**includeExceptionDetail**中的屬性**組態**清單檢視。  
  
   > [!NOTE]
   >  將 Managed 例外狀況資訊傳回用戶端可能構成安全性風險，因為例外狀況詳細資料所公開的資訊，與內部服務實作相關，可能遭未經授權的用戶端使用。  
  
## <a name="see-also"></a>另請參閱  
 [工具和公用程式來使用，以進行疑難排解](../core/tools-and-utilities-to-use-for-troubleshooting.md)   
 [WCF 配接器疑難排解](../core/troubleshooting-the-wcf-adapters.md)   
 [BTSNTSvc.exe.config 檔案](../core/btsntsvc-exe-config-file.md)