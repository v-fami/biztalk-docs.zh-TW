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
# <a name="how-to-enable-tracing-in-bam"></a><span data-ttu-id="4414a-102">如何在 BAM 中啟用追縱</span><span class="sxs-lookup"><span data-stu-id="4414a-102">How to Enable Tracing in BAM</span></span>
<span data-ttu-id="4414a-103">您可以在 BAM 中啟用追蹤，以便協助在下列五個 BAM 元件內疑難排解問題：</span><span class="sxs-lookup"><span data-stu-id="4414a-103">You can enable tracing in BAM to help troubleshoot problems within the following five BAM components:</span></span>  
  
-   <span data-ttu-id="4414a-104">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="4414a-104">BAM Management utility</span></span>  
  
-   <span data-ttu-id="4414a-105">BAM 事件匯流排</span><span class="sxs-lookup"><span data-stu-id="4414a-105">BAM event bus</span></span>  
  
-   <span data-ttu-id="4414a-106">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="4414a-106">BAM portal</span></span>  
  
-   <span data-ttu-id="4414a-107">BAM 警示</span><span class="sxs-lookup"><span data-stu-id="4414a-107">BAM alerting</span></span>  
  
-   <span data-ttu-id="4414a-108">BAM WCF 攔截器</span><span class="sxs-lookup"><span data-stu-id="4414a-108">BAM WCF Interceptor</span></span>  
  
## <a name="enabling-tracing-for-the-bam-management-utility"></a><span data-ttu-id="4414a-109">啟用 BAM 管理公用程式的追蹤</span><span class="sxs-lookup"><span data-stu-id="4414a-109">Enabling Tracing for the BAM Management Utility</span></span>  
 <span data-ttu-id="4414a-110">您可以啟用 [BAM 管理公用程式] 的追蹤，以取得部署失敗的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4414a-110">You can obtain information about deployment failures by enabling tracing for the BAM Management utility.</span></span> <span data-ttu-id="4414a-111">執行這項作業的方法有兩種。</span><span class="sxs-lookup"><span data-stu-id="4414a-111">You can do this in two ways.</span></span> <span data-ttu-id="4414a-112">您可以透過特定 BM.exe 命令的命令列啟用追蹤，或是可以修改 [BAM 管理公用程式] 組態檔以啟用所有 BM.exe 命令的追蹤。</span><span class="sxs-lookup"><span data-stu-id="4414a-112">You can enable tracing via the command line for specific BM.exe commands, or you can modify the BAM Management utility configuration file to enable tracing for all BM.exe commands.</span></span>  
  
### <a name="using-the-command-line"></a><span data-ttu-id="4414a-113">使用命令列</span><span class="sxs-lookup"><span data-stu-id="4414a-113">Using the Command Line</span></span>  
 <span data-ttu-id="4414a-114">使用啟動 BM.exe 命令列追蹤 **-追蹤： 在&#124;關閉**切換。</span><span class="sxs-lookup"><span data-stu-id="4414a-114">BM.exe command line tracing is activated using the **-Trace:on&#124;off** switch.</span></span> <span data-ttu-id="4414a-115">使用 Trace 參數會覆寫組態檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="4414a-115">Using the Trace switch overrides the settings in the configuration file.</span></span>  
  
 <span data-ttu-id="4414a-116">此參數可以搭配任何一般 BM.exe 命令使用。</span><span class="sxs-lookup"><span data-stu-id="4414a-116">The switch is used in conjunction with any normal BM.exe command.</span></span>  
  
 <span data-ttu-id="4414a-117">例如：</span><span class="sxs-lookup"><span data-stu-id="4414a-117">For example:</span></span>  
  
 <span data-ttu-id="4414a-118">**bm.exe 部署-all-DefinitionFile:PO.xml – 追蹤： 在**</span><span class="sxs-lookup"><span data-stu-id="4414a-118">**bm.exe deploy-all -DefinitionFile:PO.xml –Trace:On**</span></span>  
  
### <a name="using-the-configuration-file"></a><span data-ttu-id="4414a-119">使用組態檔</span><span class="sxs-lookup"><span data-stu-id="4414a-119">Using the Configuration File</span></span>  
 <span data-ttu-id="4414a-120">您可以修改位於 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking 資料夾中的 BM.exe.config 組態檔以啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="4414a-120">You can enable tracing by modifying the BM.exe.config configuration file located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking folder.</span></span> <span data-ttu-id="4414a-121">此檔案包含**system.diagnostics**區段，其中包含追蹤項目。</span><span class="sxs-lookup"><span data-stu-id="4414a-121">This file contains a **system.diagnostics** section which contains the tracing elements.</span></span> <span data-ttu-id="4414a-122">請移除註解以啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="4414a-122">Remove the comment to enable tracing.</span></span> <span data-ttu-id="4414a-123">根據預設，並不會啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="4414a-123">By default, tracing is not enabled.</span></span>  
  
 `<system.diagnostics>`  
  
 `<!-- To turn on BAM tracing, remove this comment or use the "-trace:on" command-line switch`  
  
 `<switches>`  
  
 `<add name="bm" value="1" />`  
  
 `<add name="Microsoft.BizTalk.Bam.Management" value="1" />`  
  
 `</switches>`  
  
 `-->`  
  
## <a name="enabling-tracing-for-the-bam-event-bus"></a><span data-ttu-id="4414a-124">啟用 BAM 事件匯流排的追蹤</span><span class="sxs-lookup"><span data-stu-id="4414a-124">Enabling Tracing for the BAM Event Bus</span></span>  
 <span data-ttu-id="4414a-125">啟用 BAM 事件匯流排的追蹤，可以協助您診斷兩種資料庫儲存錯誤類別：</span><span class="sxs-lookup"><span data-stu-id="4414a-125">Enabling tracing for the BAM event bus can help you diagnose two classes of database storage errors:</span></span>  
  
- <span data-ttu-id="4414a-126">使用 [追蹤設定檔編輯器] 時，源自於 BizTalk Server 服務之事件的儲存錯誤。</span><span class="sxs-lookup"><span data-stu-id="4414a-126">Storage errors originating from events from the BizTalk Server service when using the Tracking Profile Editor.</span></span>  
  
- <span data-ttu-id="4414a-127">使用緩衝之事件資料流 API 時所產生的儲存錯誤。</span><span class="sxs-lookup"><span data-stu-id="4414a-127">Storage errors generated when using the buffered event stream APIs.</span></span>  
  
  <span data-ttu-id="4414a-128">若要啟用 BAM 事件匯流排的追蹤，請在 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] 資料夾中編輯或新增 BTSNTSvc.exe.config 檔案的下列區段。</span><span class="sxs-lookup"><span data-stu-id="4414a-128">To enable tracing for the BAM event bus, edit or add the following section of the BTSNTSvc.exe.config file located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)] folder.</span></span>  
  
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
  
#### <a name="to-enable-tracing-for-the-bam-event-bus"></a><span data-ttu-id="4414a-129">若要啟用 BAM 事件匯流排的追蹤</span><span class="sxs-lookup"><span data-stu-id="4414a-129">To enable tracing for the BAM Event bus</span></span>  
  
1. <span data-ttu-id="4414a-130">編輯 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BTSNTSvc.exe.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="4414a-130">Edit the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BTSNTSvc.exe.config file.</span></span>  
  
2. <span data-ttu-id="4414a-131">找出\<system.diagnostics\>並\<c s\>標記。</span><span class="sxs-lookup"><span data-stu-id="4414a-131">Locate the \<system.diagnostics\> and \</system.diagnostics\> tag.</span></span> <span data-ttu-id="4414a-132">如果這些標記不存在於檔案中，請複製以上列出的程式碼，並將其貼到組態檔中。</span><span class="sxs-lookup"><span data-stu-id="4414a-132">If they are not present in the file, copy the code listed above and paste it into the configuration file.</span></span>  
  
3. <span data-ttu-id="4414a-133">取消註解取消註解系統診斷區段移結束註解分隔符號 ('-->') 從之後\<c s\>標記之前\<system.diagnostics\>標記。</span><span class="sxs-lookup"><span data-stu-id="4414a-133">Uncomment the Uncomment the system diagnostics section by moving the end comment delimiter ('-->') from after the \</system.diagnostics\> tag to before the \<system.diagnostics\> tag.</span></span>  
  
4. <span data-ttu-id="4414a-134">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="4414a-134">Save the file.</span></span>  
  
## <a name="enabling-tracing-for-the-bam-portal"></a><span data-ttu-id="4414a-135">啟用 BAM 入口網站的追蹤</span><span class="sxs-lookup"><span data-stu-id="4414a-135">Enabling Tracing for the BAM Portal</span></span>  
 <span data-ttu-id="4414a-136">啟用 BAM 入口網站的追蹤可讓您疑難排解連線能力問題。</span><span class="sxs-lookup"><span data-stu-id="4414a-136">Enabling tracing for the BAM portal allows you to troubleshoot connectivity issues.</span></span>  
  
 <span data-ttu-id="4414a-137">BAM 入口網站是一種 ASP.NET 應用程式，並會遵循追蹤的標準通訊協定。</span><span class="sxs-lookup"><span data-stu-id="4414a-137">The BAM portal is an ASP.NET application, and follows the standard protocol for tracing.</span></span> <span data-ttu-id="4414a-138">內[!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config 檔案中，沒有一個小節稱為\<追蹤\>供您啟用。</span><span class="sxs-lookup"><span data-stu-id="4414a-138">Within the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config file, there is a section called \<trace\> which you can enable.</span></span>  
  
#### <a name="to-enable-tracing-for-the-bam-portal"></a><span data-ttu-id="4414a-139">若要啟用 BAM 入口網站的追蹤</span><span class="sxs-lookup"><span data-stu-id="4414a-139">To enable tracing for the BAM portal</span></span>  
  
1. <span data-ttu-id="4414a-140">編輯 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="4414a-140">Edit the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]BAMPortal\web.config file.</span></span>  
  
2. <span data-ttu-id="4414a-141">找出\<system.diagnostics\>並\<c s\>標記。</span><span class="sxs-lookup"><span data-stu-id="4414a-141">Locate the \<system.diagnostics\> and \</system.diagnostics\> tags.</span></span>  
  
3. <span data-ttu-id="4414a-142">取消註解系統診斷區段移動結束註解分隔符號 ('-->') 從之後\<c s\>標記之前\<system.diagnostics\>標記。</span><span class="sxs-lookup"><span data-stu-id="4414a-142">Uncomment the system diagnostics section by moving end comment delimiter ('-->') from after the \</system.diagnostics\> tag to before the \<system.diagnostics\> tag.</span></span>  
  
4. <span data-ttu-id="4414a-143">修改 initializeData 屬性以指定寫入交易記錄檔的位置。</span><span class="sxs-lookup"><span data-stu-id="4414a-143">Modify the initializeData attribute to specify the location to write the tracing log.</span></span>  
  
5. <span data-ttu-id="4414a-144">找出\<system.web\>標記。</span><span class="sxs-lookup"><span data-stu-id="4414a-144">Locate \<system.web\> tag.</span></span>  
  
6. <span data-ttu-id="4414a-145">在 system.web 區段中，找出 trace 標記，並將分隔符號 ('-->') 從 trace 標記後移動 trace 標記前，以便取消註解 trace 命令。</span><span class="sxs-lookup"><span data-stu-id="4414a-145">In the system.web section locate the trace tag and uncomment the trace command by moving the delimiter ('-->') from after the trace tag to before it.</span></span>  
  
7. <span data-ttu-id="4414a-146">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="4414a-146">Save the file.</span></span>  
  
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
  
## <a name="bam-alerting"></a><span data-ttu-id="4414a-147">BAM 警示</span><span class="sxs-lookup"><span data-stu-id="4414a-147">BAM Alerting</span></span>  
 <span data-ttu-id="4414a-148">啟用 BAM 警示的追蹤可協助您疑難排解警示傳遞失敗。</span><span class="sxs-lookup"><span data-stu-id="4414a-148">Enabling tracing for BAM alerting helps you troubleshoot alert delivery failures.</span></span>  
  
 <span data-ttu-id="4414a-149">BAM 警示建立在 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services 基礎結構上。</span><span class="sxs-lookup"><span data-stu-id="4414a-149">BAM alerting is built on the [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Notification Services infrastructure.</span></span> <span data-ttu-id="4414a-150">若要啟用 BAM 警示的追蹤，請參閱 Notification Services 疑難排解主題[ http://go.microsoft.com/fwlink/?LinkId=79416 ](http://go.microsoft.com/fwlink/?LinkId=79416)。</span><span class="sxs-lookup"><span data-stu-id="4414a-150">To enable tracing on BAM alerting, see the Notification Services troubleshooting topics at [http://go.microsoft.com/fwlink/?LinkId=79416](http://go.microsoft.com/fwlink/?LinkId=79416).</span></span>  
  
## <a name="bam-interceptors"></a><span data-ttu-id="4414a-151">BAM 攔截器</span><span class="sxs-lookup"><span data-stu-id="4414a-151">BAM Interceptors</span></span>  
 <span data-ttu-id="4414a-152">若要啟用 BAM 攔截器的端點對端點追蹤，您必須修改應用程式的組態檔。這對 Web 主控的應用程式會是 Web.config，對於自我主控的應用程式則會是 Appname.config。</span><span class="sxs-lookup"><span data-stu-id="4414a-152">To enable end-to-end tracing of the BAM interceptors, you modify the application’s configuration file—either Web.config for Web-hosted applications, or Appname.config for self-hosted applications.</span></span> <span data-ttu-id="4414a-153">下列是如何能夠修改檔案的範例：</span><span class="sxs-lookup"><span data-stu-id="4414a-153">The following is an example of how you can modify the file:</span></span>  
  
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
  
 <span data-ttu-id="4414a-154">Windows Workflow Foundation 和 Windows Communication Foundation 的 BAM 攔截器，都會寫入名為 "Microsoft BizTalk Bam Interceptors" 的來源。</span><span class="sxs-lookup"><span data-stu-id="4414a-154">BAM Interceptor for Windows Workflow Foundation and Windows Communication Foundation are written to the source named "Microsoft BizTalk Bam Interceptors".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4414a-155">來源字串會區分大小寫，而且必須與在此顯示者完全相同。</span><span class="sxs-lookup"><span data-stu-id="4414a-155">The source string is case-sensitive and must appear exactly as shown.</span></span> <span data-ttu-id="4414a-156">如果您的字串不同於所示的字串，您就不會接收到 BAM 攔截器的追蹤資訊。</span><span class="sxs-lookup"><span data-stu-id="4414a-156">If your string is different than the one shown, you will not receive trace information for the BAM interceptors.</span></span>  
  
 <span data-ttu-id="4414a-157">您可以設定 switchValue 以控制追蹤等級。</span><span class="sxs-lookup"><span data-stu-id="4414a-157">You control the tracing level by setting switchValue.</span></span> <span data-ttu-id="4414a-158">下表摘要可用的追蹤等級。</span><span class="sxs-lookup"><span data-stu-id="4414a-158">The available tracing levels are summarized in the following table.</span></span>  
  
|<span data-ttu-id="4414a-159">追蹤等級</span><span class="sxs-lookup"><span data-stu-id="4414a-159">Trace Level</span></span>|<span data-ttu-id="4414a-160">描述</span><span class="sxs-lookup"><span data-stu-id="4414a-160">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="4414a-161">嚴重</span><span class="sxs-lookup"><span data-stu-id="4414a-161">Critical</span></span>|<span data-ttu-id="4414a-162">記錄「快速失敗」和「事件記錄檔」項目，並追蹤相互關聯資訊。</span><span class="sxs-lookup"><span data-stu-id="4414a-162">Logs Fail-Fast and Event Log entries, and trace correlation information.</span></span>|  
|<span data-ttu-id="4414a-163">錯誤</span><span class="sxs-lookup"><span data-stu-id="4414a-163">Error</span></span>|<span data-ttu-id="4414a-164">記錄所有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4414a-164">Logs all exceptions.</span></span>|  
|<span data-ttu-id="4414a-165">警告</span><span class="sxs-lookup"><span data-stu-id="4414a-165">Warning</span></span>|<span data-ttu-id="4414a-166">存在可能造成後續錯誤或重大失敗的狀況。</span><span class="sxs-lookup"><span data-stu-id="4414a-166">A condition exists that may subsequently result in an error or critical failure.</span></span>|  
|<span data-ttu-id="4414a-167">[資訊]</span><span class="sxs-lookup"><span data-stu-id="4414a-167">Information</span></span>|<span data-ttu-id="4414a-168">會產生有助於監視和診斷系統狀態、測量效能，或是設定資料的訊息。</span><span class="sxs-lookup"><span data-stu-id="4414a-168">Messages helpful for monitoring and diagnosing system status, measuring performance, or profiling are generated.</span></span> <span data-ttu-id="4414a-169">您可以利用此種資訊進行容量計劃和效能管理。</span><span class="sxs-lookup"><span data-stu-id="4414a-169">You can utilize such information for capacity planning and performance management.</span></span>|  
|<span data-ttu-id="4414a-170">「詳細資訊」</span><span class="sxs-lookup"><span data-stu-id="4414a-170">Verbose</span></span>|<span data-ttu-id="4414a-171">對使用者程式碼和服務進行偵錯層級追蹤。</span><span class="sxs-lookup"><span data-stu-id="4414a-171">Debug-level tracing for both user code and servicing.</span></span>|  
|<span data-ttu-id="4414a-172">All</span><span class="sxs-lookup"><span data-stu-id="4414a-172">All</span></span>|<span data-ttu-id="4414a-173">所有訊息。</span><span class="sxs-lookup"><span data-stu-id="4414a-173">All messages.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4414a-174">追蹤可能會對效能具有不利效果。</span><span class="sxs-lookup"><span data-stu-id="4414a-174">Tracing can have an adverse affect on performance.</span></span> <span data-ttu-id="4414a-175">請只在執行疑難排解活動時啟用追蹤。</span><span class="sxs-lookup"><span data-stu-id="4414a-175">Only enable tracing when you are performing troubleshooting activities.</span></span>  
  
### <a name="viewing-the-wcf-trace-file"></a><span data-ttu-id="4414a-176">檢視 WCF 追蹤檔</span><span class="sxs-lookup"><span data-stu-id="4414a-176">Viewing the WCF Trace File</span></span>  
 <span data-ttu-id="4414a-177">若要分析 WCF 追蹤，您可以使用 WCF Service Trace Viewer Tool。</span><span class="sxs-lookup"><span data-stu-id="4414a-177">To analyze the WCF trace you use the WCF Service Trace Viewer Tool.</span></span> <span data-ttu-id="4414a-178">如需有關 Service Trace Viewer Tool 的詳細資訊，請參閱 < [ http://go.microsoft.com/fwlink/?LinkId=75218 ](http://go.microsoft.com/fwlink/?LinkId=75218)。</span><span class="sxs-lookup"><span data-stu-id="4414a-178">For more information about the Service Trace Viewer Tool, see [http://go.microsoft.com/fwlink/?LinkId=75218](http://go.microsoft.com/fwlink/?LinkId=75218).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4414a-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4414a-179">See Also</span></span>  
 [<span data-ttu-id="4414a-180">管理 BAM</span><span class="sxs-lookup"><span data-stu-id="4414a-180">Managing BAM</span></span>](../core/managing-bam.md)