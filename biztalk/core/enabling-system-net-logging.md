---
title: "啟用 System.Net 記錄功能 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5eea50b9-1f46-45fc-a327-585adb4583a0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e672f2b9e7ae8b0ef3889493273660c8ef9140c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="enabling-systemnet-logging"></a>啟用 System.Net 記錄功能
您可以啟用為記錄`System.Net`和`System.Net.Sockets` [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] BTSNtSvc.exe 服務命名空間。 這會建立詳細的記錄檔，其中的資訊有助於您識別 BizTalk Server 安裝的相關問題。  
  
> [!NOTE]
>  此為 Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] 的功能，並可在 [!INCLUDE[btsBizTalkServer2006](../includes/btsbiztalkserver2006-md.md)] 或更新版本中使用。  
  
 藉由修改應用程式組態檔來啟用追蹤**BTSNtSvc.exe**， **BTSNtSvc.exe.config**。BtsNtSvc.exe 位於 BizTalk Server 安裝路徑中；如果 BizTalk Server 安裝在預設位置，則在 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] 目錄中。  
  
 若要修改**BTSNtSvc.exe.config**中開啟組態檔，然後貼上下列程式碼`<configuration>`使用 [記事本] 或您慣用的文字編輯器的項目。  
  
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
  
 記錄檔會寫入到相同的目錄，其中包含 BTSNtSvc.exe。 如果您安裝到預設位置，則會寫入至[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [解譯網路追蹤](http://go.microsoft.com/fwlink/?LinkId=78679)