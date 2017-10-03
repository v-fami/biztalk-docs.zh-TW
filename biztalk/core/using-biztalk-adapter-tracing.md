---
title: "使用 BizTalk 配接器追蹤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Adapter Trace Utility, installing
- installing, Adapter Trace Utility
- Adapter Trace Utility, enabling
- Adapter Trace Utility, running
- enabling, Adapter Trace Utility
ms.assetid: ddc6b2c7-9dee-43c1-950b-8fd580bfcb26
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45d83e1a250850d372c2e12c7ffebc79f823c287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-biztalk-adapter-tracing"></a>使用 BizTalk 配接器追蹤
本主題描述如何安裝 Trace Log tool (追蹤記錄工具) 以及如何啟用 BizTalk 配接器追蹤。  
  
## <a name="install-the-trace-log-tool"></a>安裝 Trace Log Tool (追蹤記錄工具)  
  
#### <a name="to-install-the-trace-log-tool-tracelogexe"></a>安裝 Trace Log tool (追蹤記錄工具) (tracelog.exe)  
  
1.  從 [Microsoft® Windows® Software Development Kit Update for Windows Vista](http://go.microsoft.com/fwlink/?LinkId=128279) 網站 (英文) 下載追蹤記錄工具。  
  
    > [!NOTE]
    >  即使您是執行 [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，也是安裝這個版本 (6.0) 的 SDK。 如果您安裝**Windows SDK for Windows Server 2008 和.NET Framework 3.5**版本 (v。 6.1)，則不會安裝追蹤記錄工具。  
  
2.  按一下網頁下方的 **PSDK-x86.exe** 檔案連結，啟動 **Microsoft® Windows® Software Development Kit Update for Windows Vista** Web 安裝程式。  
  
    > [!NOTE]
    >  如果您使用 64 位元版本的 Windows，請選擇適合您系統的正確下載檔案。  
  
3.  在 [選取安裝類型]  對話方塊中，選擇 [自訂]  安裝的選項，然後再按 [下一步] 。  
  
4.  接受預設安裝位置，然後按 [下一步] 。  
  
5.  在 **[自訂安裝]** 對話方塊中，按一下以清除所有可用的功能。  
  
6.  展開 **[Microsoft Windows Core SDK]** 功能，然後展開 **[工具]** 功能。  
  
7.  選擇 **[工具 (Intel 64 位元)]** 功能，然後按一下 **[將會安裝至本機硬碟]**。  
  
8.  按 **[下一步]**，然後再按 **[下一步]** ，以開始安裝。  
  
    > [!NOTE]
    >  在安裝 **Microsoft ® Windows ® Software Development Kit Update for Windows Vista** 之後，可能會提示您重新開機，視您選擇要與追蹤記錄工具一起安裝的其他功能而定。 這是因為 **Microsoft ® Windows ® Software Development Kit Update for Windows Vista** 的特定元件必須等到完成重新開機之後才能正常運作。 Trace Log tool (追蹤記錄工具) 不需重新開機就可使用。  
  
## <a name="enable-biztalk-adapter-tracing-with-tracecmd"></a>使用 trace.cmd 啟用 BizTalk 配接器追蹤  
  
#### <a name="to-enable-biztalk-adapter-tracing"></a>啟用 BizTalk 配接器追蹤  
  
1.  在命令提示字元，將目前的目錄變更為已安裝 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 的目錄。 根據預設，[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]安裝在[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]目錄。  如果使用 64 位元版本的 Windows 和[!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]，安裝路徑是[!INCLUDE[btsBizTalkServerPathx64](../includes/btsbiztalkserverpathx64-md.md)]。  
  
2.  輸入下列命令，然後按 ENTER：  
  
     **trace-tools"追蹤記錄工具的路徑 」**  
  
     依照預設，追蹤記錄工具 (tracelog.exe) 位於 **C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin** 目錄中。 如果使用 64 位元版本的 Windows，追蹤記錄工具位於 **C:\Program Files (x86)\Microsoft SDKs\Windows\v6.0\Bin**。  您必須用引號括住追蹤記錄工具的路徑。  
  
     例如，輸入下列命令，然後按 ENTER：  
  
     **trace-tools"C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin"**  
  
    > [!NOTE]
    >  **-tools** 參數在 Trace.cmd 檔案中指示 Tracelog.exe 檔案的位置。  
    >   
    >  如果命令成功執行，則輸出類似如下：  
    >   
    >  **追蹤 2.0-管理 BizTalk 2006 版本位元追蹤。**  
    >   
    >  **設定到"C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin"TRACE_TOOL_SEARCH_PATH**  
  
## <a name="capture-trace-output-with-tracecmd"></a>使用 trace.cmd 擷取追蹤輸入  
  
#### <a name="to-capture-trace-output"></a>擷取追蹤輸入  
  
1.  在命令提示字元，將目前的目錄變更為已安裝 [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] 的目錄。  
  
2.  在命令提示字元，輸入下列命令，然後按 ENTER：  
  
     **追蹤-開始**  
  
3.  重現要擷取追蹤輸出的實例。  
  
4.  在命令提示字元，輸入下列命令，然後按 ENTER：  
  
     **追蹤-停止**  
  
5.  停止追蹤，名為二進位檔案之後**Btstrace.bin**資料夾中產生其中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝。  
  
6.  可以將 **Btstrace.bin** 檔案傳送至 Microsoft 產品支援服務以供分析。  
  
## <a name="see-also"></a>另請參閱  
 [使用配接器](../core/using-adapters.md)   
 [Windows SharePoint Services 配接器疑難排解](../core/troubleshooting-the-windows-sharepoint-services-adapter.md)