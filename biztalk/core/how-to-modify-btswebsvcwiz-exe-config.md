---
title: 如何修改 BTSWebSvcWiz.exe.config |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Web services, code samples
- Web services, debugging
ms.assetid: 8466e460-faa9-45ea-9586-19174858d194
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4862e347fd74c1431f253a1cccedbd844c97c63c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25971124"
---
# <a name="how-to-modify-btswebsvcwizexeconfig"></a><span data-ttu-id="5e52a-102">如何修改 BTSWebSvcWiz.exe.config</span><span class="sxs-lookup"><span data-stu-id="5e52a-102">How to Modify BTSWebSvcWiz.exe.config</span></span>
<span data-ttu-id="5e52a-103">您可以啟用追蹤以偵錯 BizTalk Web 服務發佈精靈，取消註解\<新增\>BTSWebSvcWiz.exe.config 檔案中的節點。</span><span class="sxs-lookup"><span data-stu-id="5e52a-103">You can enable tracing to debug the BizTalk Web Services Publishing Wizard by uncommenting the \<add\> node in the BTSWebSvcWiz.exe.config file.</span></span> <span data-ttu-id="5e52a-104">如果追蹤接聽項節點已取消註解和*initializeData*參數是不變，BizTalk Server 追蹤檔案輸出寫入目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="5e52a-104">If the trace listener node is uncommented and the *initializeData* parameter is unchanged, BizTalk Server writes the trace file output to the current directory.</span></span> <span data-ttu-id="5e52a-105">或者，您可以設定追蹤層級**ApplicationTraceSwitch**和設定追蹤檔案的路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="5e52a-105">Alternatively, you can set the trace level of **ApplicationTraceSwitch** and set the path name of the trace file.</span></span>  
  
 <span data-ttu-id="5e52a-106">BTSWebSvcWiz.exe.config 與 BTSWebSvcWiz.exe 檔案位於相同的目錄中，通常是 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="5e52a-106">BTSWebSvcWiz.exe.config is located in the same directory as the BTSWebSvcWiz.exe file, which is usually [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)].</span></span>  
  
 <span data-ttu-id="5e52a-107">以下是範例取消註解\<新增\>BTSWebSvcWiz.exe.config 檔案中的節點：</span><span class="sxs-lookup"><span data-stu-id="5e52a-107">The following is an example of an uncommented \<add\> node in BTSWebSvcWiz.exe.config file:</span></span>  
  
```  
<system.diagnostics>  
  <switches>  
    <!-- TraceLevel 0=Off, 1=Error, 2=Warning, 3=Info, 4=Verbose -->  
    <add name="ApplicationTraceSwitch" value="4" />  
  </switches>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <!--add name="Trace"  
       type="System.Diagnostics.TextWriterTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
       initializeData="BTSWebSvcWiz.trace.log" /-->  
    </listeners>  
  </trace>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="5e52a-108">此追蹤功能使用.NET Framework 中的 Trace 類別。</span><span class="sxs-lookup"><span data-stu-id="5e52a-108">This tracing feature uses the Trace class in the .NET Framework.</span></span> <span data-ttu-id="5e52a-109">如需有關追蹤類別的詳細資訊，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/?LinkId=67886](http://go.microsoft.com/fwlink/?LinkId=67886)。</span><span class="sxs-lookup"><span data-stu-id="5e52a-109">For more information about the Trace class, see the Microsoft MSDN Web site at [http://go.microsoft.com/fwlink/?LinkId=67886](http://go.microsoft.com/fwlink/?LinkId=67886).</span></span>  
  
 <span data-ttu-id="5e52a-110">如需有關資訊**TextWriterTraceListener**，請參閱中的 「 TextWriterTraceListener 」[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]協助處[http://go.microsoft.com/fwlink/?LinkId=62267](http://go.microsoft.com/fwlink/?LinkId=62267)。</span><span class="sxs-lookup"><span data-stu-id="5e52a-110">For information about **TextWriterTraceListener**, see "TextWriterTraceListener" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Help Collection at [http://go.microsoft.com/fwlink/?LinkId=62267](http://go.microsoft.com/fwlink/?LinkId=62267).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e52a-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="5e52a-111">See Also</span></span>  
 [<span data-ttu-id="5e52a-112">偵錯已發佈的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="5e52a-112">Debugging Published Web Services</span></span>](../core/debugging-published-web-services.md)