---
title: 如何在 BAM 中啟用追蹤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4da99e74-a41d-4ab1-a07d-e3bee6187216
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e116087d0c560822d8a0cc64c0719fe7ba4d6e85
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000807"
---
# <a name="how-to-enable-tracing-in-bam"></a>如何在 BAM 中啟用追縱
您可以在 BAM 中啟用追蹤，以便協助在下列五個 BAM 元件內疑難排解問題：  
  
-   BAM 管理公用程式  
  
-   BAM 事件匯流排  
  
-   BAM 入口網站  
  
-   BAM 警示  
  
-   BAM WCF 攔截器  
  
## <a name="enabling-tracing-for-the-bam-management-utility"></a>啟用 BAM 管理公用程式的追蹤  
 您可以啟用 [BAM 管理公用程式] 的追蹤，以取得部署失敗的相關資訊。 執行這項作業的方法有兩種。 您可以透過特定 BM.exe 命令的命令列啟用追蹤，或是可以修改 [BAM 管理公用程式] 組態檔以啟用所有 BM.exe 命令的追蹤。  
  
### <a name="using-the-command-line"></a>使用命令列  
 使用啟動 BM.exe 命令列追蹤 **-追蹤： 在&#124;關閉**切換。 使用 Trace 參數會覆寫組態檔中的設定。  
  
 此參數可以搭配任何一般 BM.exe 命令使用。  
  
 例如：  
  
 **bm.exe 部署-all-DefinitionFile:PO.xml – 追蹤： 在**  
  
### <a name="using-the-configuration-file"></a>使用組態檔  
 您可以修改位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking 資料夾中的 BM.exe.config 組態檔以啟用追蹤。 此檔案包含**system.diagnostics**區段，其中包含追蹤項目。 請移除註解以啟用追蹤。 根據預設，並不會啟用追蹤。  
  
 `<system.diagnostics>`  
  
 `<!-- To turn on BAM tracing, remove this comment or use the "-trace:on" command-line switch`  
  
 `<switches>`  
  
 `<add name="bm" value="1" />`  
  
 `<add name="Microsoft.BizTalk.Bam.Management" value="1" />`  
  
 `</switches>`  
  
 `-->`  
  
## <a name="enabling-tracing-for-the-bam-event-bus"></a>啟用 BAM 事件匯流排的追蹤  
 啟用 BAM 事件匯流排的追蹤，可以協助您診斷兩種資料庫儲存錯誤類別：  
  
- 使用 [追蹤設定檔編輯器] 時，源自於 BizTalk Server 服務之事件的儲存錯誤。  
  
- 使用緩衝之事件資料流 API 時所產生的儲存錯誤。  
  
  若要啟用 BAM 事件匯流排的追蹤，請在 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] 資料夾中編輯或新增 BTSNTSvc.exe.config 檔案的下列區段。  
  
  `<system.diagnostics>`  
  
  `<switches>`  
  
  `<add name="Microsoft.BizTalk.Bam.EventBus" value="1" />`  
  
  `</switches>`  
  
  `<trace autoflush="true" indentsize="4">`  
  
  `<listeners>`  
  
  `<add name="Text" type="System.Diagnostics.TextWriterTraceListener" initializeData="c:\tdds.log"/>`  
  
  `</listeners>`  
  
  `</trace>`  
  
  `</system.diagnostics>`  
  
#### <a name="to-enable-tracing-for-the-bam-event-bus"></a>若要啟用 BAM 事件匯流排的追蹤  
  
1. 編輯 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BTSNTSvc.exe.config 檔案。  
  
2. 找出\<system.diagnostics\>並\<c s\>標記。 如果這些標記不存在於檔案中，請複製以上列出的程式碼，並將其貼到組態檔中。  
  
3. 取消註解取消註解系統診斷區段移結束註解分隔符號 ('-->') 從之後\<c s\>標記之前\<system.diagnostics\>標記。  
  
4. 儲存檔案。  
  
## <a name="enabling-tracing-for-the-bam-portal"></a>啟用 BAM 入口網站的追蹤  
 啟用 BAM 入口網站的追蹤可讓您疑難排解連線能力問題。  
  
 BAM 入口網站是一種 ASP.NET 應用程式，並會遵循追蹤的標準通訊協定。 內[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config 檔案中，沒有一個小節稱為\<追蹤\>供您啟用。  
  
#### <a name="to-enable-tracing-for-the-bam-portal"></a>若要啟用 BAM 入口網站的追蹤  
  
1. 編輯 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config 檔案。  
  
2. 找出\<system.diagnostics\>並\<c s\>標記。  
  
3. 取消註解系統診斷區段移動結束註解分隔符號 ('-->') 從之後\<c s\>標記之前\<system.diagnostics\>標記。  
  
4. 修改 initializeData 屬性以指定寫入交易記錄檔的位置。  
  
5. 找出\<system.web\>標記。  
  
6. 在 system.web 區段中，找出 trace 標記，並將分隔符號 ('-->') 從 trace 標記後移動 trace 標記前，以便取消註解 trace 命令。  
  
7. 儲存檔案。  
  
   `<!--`  
  
   `TRACING: To turn tracing on:`  
  
   `1) Uncomment this tag and specify a file path for trace output`  
  
   `2) Uncomment the <trace tag> under <system.web>`  
  
   `The trace will be saved to the file pointed to by "initializeData" below.`  
  
   `Ensure that the target directory exists (C:\temp by default).`  
  
   `Make sure that the IIS worker process user account (usually Network Service or ASPNET)`  
  
   `and the BAM Portal user have write permissions for the trace log file directory (C:\temp below).`  
  
   `To turn tracing on, you will need to uncomment the <trace> tag under <system.web>`  
  
   `<system.diagnostics>`  
  
   `<trace autoflush="true" indentsize="2">`  
  
   `<listeners>`  
  
   `<add name="BAMPortalListener"`  
  
   `type="System.Diagnostics.TextWriterTraceListener"`  
  
   `initializeData="C:\temp\BAMPortalTrace.log" />`  
  
   `</listeners>`  
  
   `</trace>`  
  
   `</system.diagnostics>`  
  
   `-->`  
  
   `<!--`  
  
   `TRACING: To turn tracing on:`  
  
   `1) Uncomment this tag`  
  
   `2) Uncomment the <system.diagnostics> tag above and specify a file path for trace output`  
  
   `<trace enabled="true"`  
  
   `requestLimit="40"`  
  
   `pageOutput="false"`  
  
   `traceMode="SortByTime"`  
  
   `localOnly="true"`  
  
   `writeToDiagnosticsTrace="true" />`  
  
   `-->`  
  
## <a name="bam-alerting"></a>BAM 警示  
 啟用 BAM 警示的追蹤可協助您疑難排解警示傳遞失敗。  
  
 BAM 警示建立在 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services 基礎結構上。 若要啟用 BAM 警示的追蹤，請參閱 Notification Services 疑難排解主題[ http://go.microsoft.com/fwlink/?LinkId=79416 ](http://go.microsoft.com/fwlink/?LinkId=79416)。  
  
## <a name="bam-interceptors"></a>BAM 攔截器  
 若要啟用 BAM 攔截器的端點對端點追蹤，您必須修改應用程式的組態檔。這對 Web 主控的應用程式會是 Web.config，對於自我主控的應用程式則會是 Appname.config。 下列是如何能夠修改檔案的範例：  
  
```  
<system.diagnostics>  
  </sources>  
    <source name="Microsoft BizTalk Bam Interceptors" switchValue="All">  
      <listeners>  
  
        <add name="myListener"  
             type="System.Diagnostics.TextWriterTraceListener"  
             initializeData="TextWriterOutput.log" />  
      </listeners>  
    </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Windows Workflow Foundation 和 Windows Communication Foundation 的 BAM 攔截器，都會寫入名為 "Microsoft BizTalk Bam Interceptors" 的來源。  
  
> [!NOTE]
>  來源字串會區分大小寫，而且必須與在此顯示者完全相同。 如果您的字串不同於所示的字串，您就不會接收到 BAM 攔截器的追蹤資訊。  
  
 您可以設定 switchValue 以控制追蹤等級。 下表摘要可用的追蹤等級。  
  
|追蹤等級|描述|  
|-----------------|-----------------|  
|嚴重|記錄「快速失敗」和「事件記錄檔」項目，並追蹤相互關聯資訊。|  
|錯誤|記錄所有例外狀況。|  
|警告|存在可能造成後續錯誤或重大失敗的狀況。|  
|[資訊]|會產生有助於監視和診斷系統狀態、測量效能，或是設定資料的訊息。 您可以利用此種資訊進行容量計劃和效能管理。|  
|「詳細資訊」|對使用者程式碼和服務進行偵錯層級追蹤。|  
|All|所有訊息。|  
  
> [!NOTE]
>  追蹤可能會對效能具有不利效果。 請只在執行疑難排解活動時啟用追蹤。  
  
### <a name="viewing-the-wcf-trace-file"></a>檢視 WCF 追蹤檔  
 若要分析 WCF 追蹤，您可以使用 WCF Service Trace Viewer Tool。 如需有關 Service Trace Viewer Tool 的詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=75218 ](http://go.microsoft.com/fwlink/?LinkId=75218)。  
  
## <a name="see-also"></a>另請參閱  
 [管理 BAM](../core/managing-bam.md)