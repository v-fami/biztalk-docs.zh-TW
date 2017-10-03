---
title: "如何修改 BTSWebSvcWiz.exe.config |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web services, code samples
- Web services, debugging
ms.assetid: 8466e460-faa9-45ea-9586-19174858d194
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1686932099baa98f36af9ef8a2ca384f7f27a0ce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-modify-btswebsvcwizexeconfig"></a>如何修改 BTSWebSvcWiz.exe.config
您可以啟用追蹤以偵錯 BizTalk Web 服務發佈精靈，取消註解\<新增 > BTSWebSvcWiz.exe.config 檔案中的節點。 如果追蹤接聽項節點已取消註解和*initializeData*參數是不變，BizTalk Server 追蹤檔案輸出寫入目前的目錄。 或者，您可以設定追蹤層級**ApplicationTraceSwitch**和設定追蹤檔案的路徑名稱。  
  
 BTSWebSvcWiz.exe.config 與 BTSWebSvcWiz.exe 檔案位於相同的目錄中，通常是 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]。  
  
 以下是範例取消註解的\<新增 > BTSWebSvcWiz.exe.config 檔案中的節點：  
  
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
  
 此追蹤功能使用.NET Framework 中的 Trace 類別。 如需有關追蹤類別的詳細資訊，請參閱 Microsoft MSDN 網站，網址[http://go.microsoft.com/fwlink/?LinkId=67886](http://go.microsoft.com/fwlink/?LinkId=67886)。  
  
 如需有關資訊**TextWriterTraceListener**，請參閱中的 「 TextWriterTraceListener 」[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]協助處[http://go.microsoft.com/fwlink/?LinkId=62267](http://go.microsoft.com/fwlink/?LinkId=62267)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯已發佈的 Web 服務](../core/debugging-published-web-services.md)