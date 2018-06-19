---
title: 啟用 System.Net 記錄功能 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5eea50b9-1f46-45fc-a327-585adb4583a0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e672f2b9e7ae8b0ef3889493273660c8ef9140c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239934"
---
# <a name="enabling-systemnet-logging"></a><span data-ttu-id="6111f-102">啟用 System.Net 記錄功能</span><span class="sxs-lookup"><span data-stu-id="6111f-102">Enabling System.Net Logging</span></span>
<span data-ttu-id="6111f-103">您可以啟用為記錄`System.Net`和`System.Net.Sockets` [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] BTSNtSvc.exe 服務命名空間。</span><span class="sxs-lookup"><span data-stu-id="6111f-103">You can enable logging for the `System.Net` and `System.Net.Sockets`[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] namespace for the BTSNtSvc.exe service.</span></span> <span data-ttu-id="6111f-104">這會建立詳細的記錄檔，其中的資訊有助於您識別 BizTalk Server 安裝的相關問題。</span><span class="sxs-lookup"><span data-stu-id="6111f-104">This will cause a detailed log file to be created containing information that may help you identify issues with your BizTalk Server installation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6111f-105">此為 Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 的功能，並可在 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 或更新版本中使用。</span><span class="sxs-lookup"><span data-stu-id="6111f-105">This is a feature of the Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] and will work in [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] or later.</span></span>  
  
 <span data-ttu-id="6111f-106">藉由修改應用程式組態檔來啟用追蹤**BTSNtSvc.exe**， **BTSNtSvc.exe.config**。BtsNtSvc.exe 位於 BizTalk Server 安裝路徑中；如果 BizTalk Server 安裝在預設位置，則在 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] 目錄中。</span><span class="sxs-lookup"><span data-stu-id="6111f-106">Tracing is enabled by modifying the application configuration file for **BTSNtSvc.exe**,  **BTSNtSvc.exe.config**. It can be found in the BizTalk Server installation path; if you installed BizTalk Server to the default location, BtsNtSvc.exe will be in the directory [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
 <span data-ttu-id="6111f-107">若要修改**BTSNtSvc.exe.config**中開啟組態檔，然後貼上下列程式碼`<configuration>`使用 [記事本] 或您慣用的文字編輯器的項目。</span><span class="sxs-lookup"><span data-stu-id="6111f-107">To modify **BTSNtSvc.exe.config**, open the configuration file and paste the code below into the `<configuration>` element using Notepad or your favorite text editor.</span></span>  
  
```  
<system.diagnostics>  
  <sources>  
    <source name="System.Net" switchValue="Verbose">  
      <listeners>  
        <add name="System.Net"/>  
      </listeners>  
    </source>  
    <source name="System.Net.Sockets" switchValue="Verbose">  
      <listeners>  
        <add name="System.Net"/>  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="System.Net"  
          type="System Diagnostics.TextWriterTraceListener"  
          initializeData="System.Net..log"/>  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="6111f-108">記錄檔會寫入到相同的目錄，其中包含 BTSNtSvc.exe。</span><span class="sxs-lookup"><span data-stu-id="6111f-108">The log file will be written to the same directory that contains BTSNtSvc.exe.</span></span> <span data-ttu-id="6111f-109">如果您安裝到預設位置，則會寫入至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6111f-109">If you installed to the default location, it will be written to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6111f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6111f-110">See Also</span></span>  
 [<span data-ttu-id="6111f-111">解譯網路追蹤</span><span class="sxs-lookup"><span data-stu-id="6111f-111">Interpreting Network Tracing</span></span>](http://go.microsoft.com/fwlink/?LinkId=78679)