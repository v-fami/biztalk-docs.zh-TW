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
# <a name="how-to-diagnose-problems-with-the-wcf-adapters"></a><span data-ttu-id="41e23-102">如何診斷 WCF 配接器問題</span><span class="sxs-lookup"><span data-stu-id="41e23-102">How to Diagnose Problems with the WCF Adapters</span></span>
<span data-ttu-id="41e23-103">本章節包含的步驟可協助您診斷 WCF 配接器的問題。</span><span class="sxs-lookup"><span data-stu-id="41e23-103">This section contains steps that you can follow to help diagnose problems with the WCF adapters.</span></span>  
  
### <a name="check-the-iis-log-and-httperr-log-of-the-iis-server-for-errors"></a><span data-ttu-id="41e23-104">檢查 IIS 伺服器的 IIS 記錄和 HTTPERR 記錄中是否記載發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="41e23-104">Check the IIS log and HTTPERR log of the IIS server for errors</span></span>  
  
- <span data-ttu-id="41e23-105">IIS 伺服器來源或目標記錄檔可能包含疑難排解外掛式 WCF 配接器問題的實用資訊。</span><span class="sxs-lookup"><span data-stu-id="41e23-105">The source or target IIS server log files can contain information that is helpful for troubleshooting problems with the isolated WCF adapters.</span></span> <span data-ttu-id="41e23-106">根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 電腦上的 IIS 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="41e23-106">By default the IIS log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] computer are located in the following directory:</span></span>  
  
   <span data-ttu-id="41e23-107"><em>%Windir%\\</em>system32\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="41e23-107"><em>%WinDir%\\</em>system32\LogFiles\W3SVC1\\</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="41e23-108">*%Windir%* 預留位置代表的位置[!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)]目錄在 IIS 伺服器上。</span><span class="sxs-lookup"><span data-stu-id="41e23-108">*%WinDir%* is a placeholder for the location of the [!INCLUDE[btsWinNoVersion](../includes/btswinnoversion-md.md)] directory on the IIS server.</span></span>  
  
   <span data-ttu-id="41e23-109">根據預設，[!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 和 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上的 HTTPERR 記錄檔位於下列目錄：</span><span class="sxs-lookup"><span data-stu-id="41e23-109">By default the HTTPERR log files on a [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] based computers are located in the following directory:</span></span>  
  
  > [!NOTE]
  >  <span data-ttu-id="41e23-110">只有在 [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] 和 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] 電腦上才能使用 HTTPERR 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="41e23-110">The HTTPERR log file is available only on [!INCLUDE[btsWinSvr2k3](../includes/btswinsvr2k3-md.md)] and [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] based computers.</span></span>  
  
   <span data-ttu-id="41e23-111"><em>%Windir%\\</em>system32\LogFiles\HTTPERR\\</span><span class="sxs-lookup"><span data-stu-id="41e23-111"><em>%WinDir%\\</em>system32\LogFiles\HTTPERR\\</span></span>  
  
### <a name="use-wcf-message-logging-for-fault-monitoring-and-diagnosis-of-problems-from-the-wcf-adapters"></a><span data-ttu-id="41e23-112">使用 WCF 訊息記錄，進行 WCF 配接器問題的錯誤監控與診斷</span><span class="sxs-lookup"><span data-stu-id="41e23-112">Use WCF message logging for fault monitoring and diagnosis of problems from the WCF adapters</span></span>  
  
1. <span data-ttu-id="41e23-113">WCF 能夠記錄內送與外寄訊息的離線耗用量。</span><span class="sxs-lookup"><span data-stu-id="41e23-113">WCF provides the capability to log incoming and outgoing messages for offline consumption.</span></span> <span data-ttu-id="41e23-114">您可以使用訊息記錄，瞭解訊息如何透過 WCF 配接器進行內送和外寄。</span><span class="sxs-lookup"><span data-stu-id="41e23-114">You can use message logging to see what the messages incoming and outgoing through the WCF adapters look like.</span></span> <span data-ttu-id="41e23-115">依預設，WCF 不會記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="41e23-115">WCF does not log messages by default.</span></span> <span data-ttu-id="41e23-116">若要啟動訊息記錄，您必須修改 WCF 配接器所使用的組態檔。</span><span class="sxs-lookup"><span data-stu-id="41e23-116">To activate message logging, you have to modify the configuration files that the WCF adapters use.</span></span> <span data-ttu-id="41e23-117">如需有關 WCF 訊息記錄的詳細資訊，請參閱 < 訊息記錄 >，網址[ http://go.microsoft.com/fwlink/?LinkId=89003 ](http://go.microsoft.com/fwlink/?LinkId=89003)。</span><span class="sxs-lookup"><span data-stu-id="41e23-117">For more information about WCF message logging, see "Message Logging" at [http://go.microsoft.com/fwlink/?LinkId=89003](http://go.microsoft.com/fwlink/?LinkId=89003).</span></span>  
  
2. <span data-ttu-id="41e23-118">內含式 WCF 配接器，您可以藉由修改應用程式組態檔中，啟用 WCF 訊息記錄**BTSNtSvc.exe.config**，如**BTSNtSvc.exe**。</span><span class="sxs-lookup"><span data-stu-id="41e23-118">For the in-process WCF adapters, you can enable WCF message logging by modifying the application configuration file, **BTSNtSvc.exe.config**, for **BTSNtSvc.exe**.</span></span> <span data-ttu-id="41e23-119">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝路徑中即可找到組態檔。</span><span class="sxs-lookup"><span data-stu-id="41e23-119">The configuration file can be found in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] installation path.</span></span> <span data-ttu-id="41e23-120">若將 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 安裝於預設位置，BtsNtSvc.exe 就位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] 目錄中。</span><span class="sxs-lookup"><span data-stu-id="41e23-120">If you installed [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] to the default location, BtsNtSvc.exe will be in the directory [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
3. <span data-ttu-id="41e23-121">外掛式 WCF 配接器中，您可以啟用 WCF 訊息記錄，藉由修改**Web.config** BizTalk WCF 服務發佈精靈建立 Web 應用程式資料夾中的檔案。</span><span class="sxs-lookup"><span data-stu-id="41e23-121">For the isolated WCF adapters, you can enable WCF message logging by modifying the **Web.config** file that the BizTalk WCF Service Publishing Wizard creates in the Web application folder.</span></span>  
  
4. <span data-ttu-id="41e23-122">若要修改**BTSNtSvc.exe.config**或是**Web.config**使用 「 記事本 」 中開啟組態檔，然後設定 WCF 訊息記錄，如下列組態範例所示：</span><span class="sxs-lookup"><span data-stu-id="41e23-122">To modify **BTSNtSvc.exe.config** or **Web.config**, open the configuration file by using Notepad, and then configure WCF message logging, as indicated in the following configuration example:</span></span>  
  
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
  
5. <span data-ttu-id="41e23-123">您可以使用 Windows Communication Foundation (WCF) 服務追蹤檢視器工具分析 WCF 所記錄的訊息。</span><span class="sxs-lookup"><span data-stu-id="41e23-123">You can use the Windows Communication Foundation (WCF) Service Trace Viewer Tool to analyze messages logged by WCF.</span></span> <span data-ttu-id="41e23-124">Windows Vista 和 [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 執行階段元件的 Microsoft Windows 軟體開發套件 (SDK) 內含服務追蹤檢視器。</span><span class="sxs-lookup"><span data-stu-id="41e23-124">Service Trace Viewer is included in the Microsoft Windows Software Development Kit (SDK) for Windows Vista and [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] Runtime Components.</span></span> <span data-ttu-id="41e23-125">您可以從 Microsoft 下載中心下載 Windows SDK [ http://go.microsoft.com/fwlink/?LinkID=75636 ](http://go.microsoft.com/fwlink/?LinkID=75636)。</span><span class="sxs-lookup"><span data-stu-id="41e23-125">You can download the Windows SDK from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=75636](http://go.microsoft.com/fwlink/?LinkID=75636).</span></span> <span data-ttu-id="41e23-126">如需使用此工具的詳細資訊，請參閱 「 服務追蹤檢視器工具 (Svctraceviewer.exe [ http://go.microsoft.com/fwlink/?LinkId=88991 ](http://go.microsoft.com/fwlink/?LinkId=88991)。</span><span class="sxs-lookup"><span data-stu-id="41e23-126">For more information about using this tool, see "Service Trace Viewer Tool (SvcTraceViewer.exe)"at [http://go.microsoft.com/fwlink/?LinkId=88991](http://go.microsoft.com/fwlink/?LinkId=88991).</span></span>  
  
### <a name="return-managed-exception-information-to-the-client-in-a-soap-fault-to-ease-debugging"></a><span data-ttu-id="41e23-127">將 Managed 例外狀況資訊傳回 SOAP 錯誤中的用戶端以便偵錯</span><span class="sxs-lookup"><span data-stu-id="41e23-127">Return managed exception information to the client in a SOAP fault to ease debugging</span></span>  
  
1. <span data-ttu-id="41e23-128">您可以選取**錯誤中包含例外狀況**選項標準的 WCF 接收位置，以受管理的例外狀況資訊傳回 SOAP 錯誤中的用戶端以便偵錯。</span><span class="sxs-lookup"><span data-stu-id="41e23-128">You can select the **Include exception in faults** option for the standard WCF receive location to return managed exception information to the client in SOAP faults to ease debugging.</span></span> <span data-ttu-id="41e23-129">使用下列步驟來選取**錯誤中包含例外狀況**選項。</span><span class="sxs-lookup"><span data-stu-id="41e23-129">Use the following steps to select the **Include exception in faults** option.</span></span>  
  
   1. <span data-ttu-id="41e23-130">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，展開**BizTalk 群組**，展開**應用程式**，展開**接收位置**，以滑鼠右鍵按一下使用標準 WCF 配接器的接收位置，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="41e23-130">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, expand **Receive Locations**, right-click a receive location using a standard WCF adapter, and then click **Properties**.</span></span>  
  
   2. <span data-ttu-id="41e23-131">在 [**接收位置屬性**] 對話方塊中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="41e23-131">In the **Receive Location Properties** dialog box, click **Configure**.</span></span>  
  
   3. <span data-ttu-id="41e23-132">在 [傳輸] 對話方塊中，在**訊息**索引標籤上，選取**錯誤中包含例外狀況**選項。</span><span class="sxs-lookup"><span data-stu-id="41e23-132">In the transport dialog box, on the **Messages** tab, select the **Include exception in faults** option.</span></span>  
  
2. <span data-ttu-id="41e23-133">如果您使用 Wcf-custom 或 Wcf-customisolated 配接器，您可以設定**IncludeExceptionDetailInFaults**屬性[ServiceDebugElement](http://go.microsoft.com/fwlink/?LinkId=89004)傳回 managed 例外狀況資訊用戶端。</span><span class="sxs-lookup"><span data-stu-id="41e23-133">If you use the WCF-Custom or the WCF-CustomIsolated adapter, you can set the **IncludeExceptionDetailInFaults** property of the [ServiceDebugElement](http://go.microsoft.com/fwlink/?LinkId=89004) to return managed exception information to the client.</span></span> <span data-ttu-id="41e23-134">若要這樣做，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="41e23-134">To do so, use the following steps:</span></span>  
  
   1. <span data-ttu-id="41e23-135">在 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**管理**，展開**BizTalk 群組**，展開**應用程式**，展開**接收位置**，以滑鼠右鍵按一下使用 Wcf-custom 或 Wcf-customisolated 配接器的接收位置，然後按一下**屬性**。</span><span class="sxs-lookup"><span data-stu-id="41e23-135">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Applications**, expand **Receive Locations**, right-click a receive location using the WCF-Custom or the WCF-CustomIsolated adapter, and then click **Properties**.</span></span>  
  
   2. <span data-ttu-id="41e23-136">在 [**接收位置屬性**] 對話方塊中，按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="41e23-136">In the **Receive Location Properties** dialog box, click **Configure**.</span></span>  
  
   3. <span data-ttu-id="41e23-137">在 [傳輸] 對話方塊中，在**行為**索引標籤上，以滑鼠右鍵按一下**ServiceBehavior**節點，然後再按一下**新增擴充功能**。</span><span class="sxs-lookup"><span data-stu-id="41e23-137">In the transport dialog box, on the **Behavior** tab, right-click the **ServiceBehavior** node, and then click **Add extension**.</span></span>  
  
   4. <span data-ttu-id="41e23-138">在 **選取行為延伸模組** 對話方塊中，選取**serviceDebug**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="41e23-138">In the **Select Behavior Extension** dialog box, select **serviceDebug**, and then click **OK**.</span></span>  
  
   5. <span data-ttu-id="41e23-139">在 傳輸 對話方塊中，在**行為**索引標籤上，按一下  **serviceDebug**節點，然後再選取 **，則為 True**如**includeExceptionDetail**中的屬性**組態**清單檢視。</span><span class="sxs-lookup"><span data-stu-id="41e23-139">In the transport dialog box, on the **Behavior** tab, click the **serviceDebug** node, and then select **True** for the **includeExceptionDetail** property in the **Configuration** list view.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="41e23-140">將 Managed 例外狀況資訊傳回用戶端可能構成安全性風險，因為例外狀況詳細資料所公開的資訊，與內部服務實作相關，可能遭未經授權的用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="41e23-140">Returning managed exception information to clients can be a security risk because exception details expose information about the internal service implementation that could be used by unauthorized clients.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41e23-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41e23-141">See Also</span></span>  
 <span data-ttu-id="41e23-142">[工具和公用程式來使用，以進行疑難排解](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="41e23-142">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 <span data-ttu-id="41e23-143">[WCF 配接器疑難排解](../core/troubleshooting-the-wcf-adapters.md) </span><span class="sxs-lookup"><span data-stu-id="41e23-143">[Troubleshooting the WCF Adapters](../core/troubleshooting-the-wcf-adapters.md) </span></span>  
 [<span data-ttu-id="41e23-144">BTSNTSvc.exe.config 檔案</span><span class="sxs-lookup"><span data-stu-id="41e23-144">BTSNTSvc.exe.config File</span></span>](../core/btsntsvc-exe-config-file.md)