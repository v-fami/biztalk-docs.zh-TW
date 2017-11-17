---
title: "BizTalk Web 服務疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdc86de8-e41e-4878-a66e-e242bcf3b705
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 666b08e0c7992f8660d005bef51d26c8f51bbed5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-web-services"></a><span data-ttu-id="75216-102">BizTalk Web 服務疑難排解</span><span class="sxs-lookup"><span data-stu-id="75216-102">Troubleshooting BizTalk Web Services</span></span>
<span data-ttu-id="75216-103">本節會針對如何辨識及解決常見 Web 服務問題提供相關建議。</span><span class="sxs-lookup"><span data-stu-id="75216-103">This section offers advice on how to identify and resolve common Web service issues.</span></span>  
  
## <a name="general-troubleshooting"></a><span data-ttu-id="75216-104">一般疑難排解</span><span class="sxs-lookup"><span data-stu-id="75216-104">General Troubleshooting</span></span>  
  
### <a name="enabling-web-services-publishing-wizard-tracing"></a><span data-ttu-id="75216-105">啟用 Web 服務發佈精靈追蹤</span><span class="sxs-lookup"><span data-stu-id="75216-105">Enabling Web Services Publishing Wizard tracing</span></span>  
 <span data-ttu-id="75216-106">您可以啟用追蹤以偵錯 BizTalk Web 服務發佈精靈，取消註解\<新增 > BTSWebSvcWiz.exe.config 檔案中的節點。</span><span class="sxs-lookup"><span data-stu-id="75216-106">You can enable tracing to debug the BizTalk Web Services Publishing Wizard by uncommenting the \<add> node in the BTSWebSvcWiz.exe.config file.</span></span> <span data-ttu-id="75216-107">如需有關如何從 Web 服務發佈精靈取得追蹤資訊的詳細資訊，請參閱[如何修改 BTSWebSvcWiz.exe.config](../core/how-to-modify-btswebsvcwiz-exe-config.md)。</span><span class="sxs-lookup"><span data-stu-id="75216-107">For more information about obtaining trace information from the Web Services Publishing Wizard, see [How to Modify BTSWebSvcWiz.exe.config](../core/how-to-modify-btswebsvcwiz-exe-config.md).</span></span>  
  
### <a name="enabling-soap-message-tracing"></a><span data-ttu-id="75216-108">啟用 SOAP 訊息追蹤</span><span class="sxs-lookup"><span data-stu-id="75216-108">Enabling SOAP message tracing</span></span>  
 <span data-ttu-id="75216-109">您可以啟用 SOAP 訊息追蹤，協助您使用 SOAP 延伸模組來偵錯 Web 服務發佈應用程式。</span><span class="sxs-lookup"><span data-stu-id="75216-109">You can enable SOAP message tracing to help you debug the Web services publishing application by using a SOAP extension.</span></span> <span data-ttu-id="75216-110">如需 SOAP 延伸模組的詳細資訊，請參閱[How to： 實作 SOAP 延伸模組](http://go.microsoft.com/fwlink/?LinkId=62314)。</span><span class="sxs-lookup"><span data-stu-id="75216-110">For more information about SOAP extensions, see [How to: Implement a SOAP Extension](http://go.microsoft.com/fwlink/?LinkId=62314).</span></span>  
  
### <a name="using-the-throwdetailederror-switch"></a><span data-ttu-id="75216-111">使用 ThrowDetailedError 參數</span><span class="sxs-lookup"><span data-stu-id="75216-111">Using the ThrowDetailedError switch</span></span>  
 <span data-ttu-id="75216-112">如果發生錯誤時，Web 用戶端會接收泛型**SoapException**。</span><span class="sxs-lookup"><span data-stu-id="75216-112">If an error occurs, the Web client receives a generic **SoapException**.</span></span>  
  
 <span data-ttu-id="75216-113">若要偵錯已發佈的 Web 服務，您可以在 web.config 檔案中加入某個參數，以便控制從該發佈的 Web 服務傳回之例外狀況詳細資料的等級。</span><span class="sxs-lookup"><span data-stu-id="75216-113">To debug your published Web service, you can add a switch to the web.config file to control the level of the exception details returned from the published Web service.</span></span> <span data-ttu-id="75216-114">參數是**ThrowDetailedError**，當值設定為**True**伺服器 proxy 將內部例外狀況資訊傳回給 Web 用戶端，讓您偵錯已發佈的 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="75216-114">The switch is **ThrowDetailedError**, and when it is set to **True** the server proxy returns inner exception information to the Web client, enabling you to debug the published Web service.</span></span>  
  
 <span data-ttu-id="75216-115">下列 XML 程式碼示範**ThrowDetailedError**下的 web.config 檔案中出現的交換器\<appSettings > 節點：</span><span class="sxs-lookup"><span data-stu-id="75216-115">The following XML code shows the **ThrowDetailedError** switch that appears in the web.config file under the \<appSettings> node:</span></span>  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!WARNING]
>  <span data-ttu-id="75216-116">內部例外狀況可能包含機密資訊。</span><span class="sxs-lookup"><span data-stu-id="75216-116">The inner exception may contain sensitive information.</span></span> <span data-ttu-id="75216-117">偵錯之後，您應該設定**ThrowDetailedError**切換至**False**。</span><span class="sxs-lookup"><span data-stu-id="75216-117">After debugging, you should set the **ThrowDetailedError** switch to **False**.</span></span>  
  
### <a name="using-net-framework-tracing-to-capture-and-log-errors-in-the-web-service"></a><span data-ttu-id="75216-118">使用 .NET Framework 追蹤來擷取和記錄 Web 服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="75216-118">Using .NET Framework tracing to capture and log errors in the Web service</span></span>  
 <span data-ttu-id="75216-119">.NET Framework **System.Diagnostics.Trace**類別可以用來擷取，並將錯誤寫入至文字檔。</span><span class="sxs-lookup"><span data-stu-id="75216-119">The .NET Framework **System.Diagnostics.Trace** class can be used to capture and write errors to a text file.</span></span>  
  
##### <a name="to-use-the-systemdiagnosticstrace-class-to-capture-and-write-errors-to-a-text-file"></a><span data-ttu-id="75216-120">使用 System.Diagnostics.Trace 類別來擷取錯誤並將錯誤寫入文字檔中</span><span class="sxs-lookup"><span data-stu-id="75216-120">To use the System.Diagnostics.Trace class to capture and write errors to a text file</span></span>  
  
1.  <span data-ttu-id="75216-121">更新將 TRACE 編譯器指示詞設定為 Web 服務的 web.config 檔**true**並加入**TraceSwitch**值：</span><span class="sxs-lookup"><span data-stu-id="75216-121">Update the web.config file for the Web service to set the TRACE compiler directive to **true** and add a **TraceSwitch** value:</span></span>  
  
    ```  
    <?xml version="1.0"?>  
    <configuration>  
      <system.codedom>  
        <compilers>  
          <compiler language="c#;cs;csharp"   
                    extension=".cs"   
                    compilerOptions="/d:TRACE"  
                    type="Microsoft.CSharp.CSharpCodeProvider, System, Version=2.0.3500.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" warningLevel="1" />  
          </compilers>  
      </system.codedom>  
      <system.diagnostics>  
        <switches>  
          <add name="WebSvcTraceSwitch" value="2" />  
          <!-- Set to 0, 1, 2, 3, or 4, which corresponds   
          to TraceLevel.Off, TraceLevel.Error, TraceLevel.Warning  
          TraceLevel.Info, and TraceLevel.Verbose. -->  
        </switches>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="75216-122">如果 TRACE 編譯器指示詞未設定為**true**則不會產生任何追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="75216-122">If the TRACE compiler directive is not set to **true** then no trace output will be generated.</span></span> <span data-ttu-id="75216-123">**TraceSwitch**值也可以呼叫類別中設定，但此處為了方便起見在 web.config 檔案中設定。</span><span class="sxs-lookup"><span data-stu-id="75216-123">The **TraceSwitch** value can also be set in the calling class but is set here in the web.config file for convenience.</span></span> <span data-ttu-id="75216-124">設定**TraceSwitch**值設定為適當的層級，供開發應用程式和開發以減少或禁止追蹤輸出完成之後變更的值。</span><span class="sxs-lookup"><span data-stu-id="75216-124">Set the **TraceSwitch** value to the appropriate level for development purposes and change the value after development is complete to reduce or inhibit trace output.</span></span>  
  
2.  <span data-ttu-id="75216-125">建立的執行個體**TraceSwitch**和**TextWriterTraceListener**類別和使用**try … catch**截獲並將錯誤寫入的 Web 服務 [WebMethod] 呼叫中封鎖追蹤輸出檔。</span><span class="sxs-lookup"><span data-stu-id="75216-125">Create an instance of the **TraceSwitch** and **TextWriterTraceListener** classes and use a **try…catch** block in the Web service [WebMethod] call to trap and write errors to a trace output file.</span></span> <span data-ttu-id="75216-126">例如，在嘗試將整數變數 s2 設定為物件變數 o2 之 null 執行個體時所產生的錯誤，將由下列程式碼所截獲：</span><span class="sxs-lookup"><span data-stu-id="75216-126">For example, the following code traps an error that is generated when attempting to set the integer variable s2 to a null instance of the object variable o2:</span></span>  
  
    ```  
    using System;  
    using System.Web;  
    using System.Web.Services;  
    using System.Web.Services.Protocols;  
    using System.Diagnostics;  
  
    [WebService(Namespace = "http://tempuri.org/")]  
    [WebServiceBinding(ConformsTo = WsiProfiles.BasicProfile1_1)]  
    public class Service : System.Web.Services.WebService  
    {  
        TraceSwitch WebSvcTraceSwitch = new TraceSwitch("WebSvcTraceSwitch", "Web Service Trace");  
        TextWriterTraceListener TestTracer = new TextWriterTraceListener("C:\\traceout.txt");  
    // Note that by default the local ASPNET account(IIS 5.x) or the   
    // local NETWORK SERVICE account(IIS 6.0) needs write access to  
    // this directory so that the instance of the   
    // TextWriterTraceListener can write to the trace output file.  
    );  
  
        public Service () {  
        }  
  
        [WebMethod]  
        public string HelloWorld()   
        {  
        string h2 = "Hello World";  
        //object o2 = 1;  
        object o2 = null;  
            try  
            {  
                int s2 = (int)o2; //Error if o2 set to null   
                return h2;  
            }  
            catch(Exception e)  
            {  
                Trace.Listeners.Add(TestTracer);  
                Trace.WriteLineIf(WebSvcTraceSwitch.Level = TraceLevel.Warning,"Exception caught: " + e.Message);  
                //Writes to the trace file if specified TraceLevel switch value (in web.config) >= 2  
                TestTracer.Dispose();  
                return "An error occurred in the Web service, please contact the web server administrator.";  
            }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="75216-127">此程式碼是當您建立新時，所預設產生 HelloWorld Web 服務的修改的版本**ASP.Net Web 服務**專案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="75216-127">This code is a modified version of the HelloWorld Web service that is generated by default when you create a new **ASP.Net Web Service** project in [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="75216-128">在 Windows Vista 中，您可能必須擁有系統管理員權限，才能將追蹤輸出檔寫入至根資料夾。</span><span class="sxs-lookup"><span data-stu-id="75216-128">For Windows Vista, Administrator privileges may be required to write the trace output file to the root folder.</span></span>  
  
3.  <span data-ttu-id="75216-129">重新建立 Web 服務專案。</span><span class="sxs-lookup"><span data-stu-id="75216-129">Rebuild the Web service project.</span></span> <span data-ttu-id="75216-130">現在，如果發生錯誤時**再試一次**陳述式中處理例外狀況**攔截**陳述式和錯誤會寫入追蹤輸出檔。</span><span class="sxs-lookup"><span data-stu-id="75216-130">Now, if an error occurs in the **Try** statement the exception is handled in the **Catch** statement and an error is written to the trace output file.</span></span>  
  
## <a name="general-troubleshooting-questions-and-answers"></a><span data-ttu-id="75216-131">一般疑難排解問答集</span><span class="sxs-lookup"><span data-stu-id="75216-131">General Troubleshooting Questions and Answers</span></span>  
 <span data-ttu-id="75216-132">本節包含針對協助您解決與 Web 服務相關問題的一組問答集。</span><span class="sxs-lookup"><span data-stu-id="75216-132">This section contains a set of questions and answers designed to help you resolve issues with Web services.</span></span>  
  
### <a name="i-am-receiving-errors-when-consuming-a-web-service-how-can-i-avoid-them"></a><span data-ttu-id="75216-133">我在使用 Web 服務時發生錯誤，我要如何避免這些錯誤？</span><span class="sxs-lookup"><span data-stu-id="75216-133">I am receiving errors when consuming a Web service; how can I avoid them?</span></span>  
 <span data-ttu-id="75216-134">使用 Web 服務時要考慮許多細節，其中包括下列幾點：</span><span class="sxs-lookup"><span data-stu-id="75216-134">There are many details to consider when consuming a Web service, including the following:</span></span>  
  
-   <span data-ttu-id="75216-135">避免在參數名稱中使用兩個底線字元。</span><span class="sxs-lookup"><span data-stu-id="75216-135">Avoid using two underscore characters in a parameter name.</span></span>  
  
-   <span data-ttu-id="75216-136">使用**任何**項目或**anyAttribute** Web 方法中不支援屬性。</span><span class="sxs-lookup"><span data-stu-id="75216-136">Use of the **any** element or the **anyAttribute** attribute is not supported in Web methods.</span></span>  
  
-   <span data-ttu-id="75216-137">避免將 XLANG/s 關鍵字做為 Web 服務名稱或 Web 方法名稱。</span><span class="sxs-lookup"><span data-stu-id="75216-137">Avoid using XLANG/s keywords as a Web service name or Web method name.</span></span>  
  
-   <span data-ttu-id="75216-138">避免使用 XLANG/s 不支援的 Web 方法參數類型。</span><span class="sxs-lookup"><span data-stu-id="75216-138">Avoid using Web method parameter types that are not supported by XLANG/s.</span></span>  
  
-   <span data-ttu-id="75216-139">結構描述中不要使用 C# 關鍵字的項目名稱或無效 C# 識別項的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="75216-139">Do not use element names that are C# keywords or will be invalid as a C# identifier in your schemas.</span></span>  
  
-   <span data-ttu-id="75216-140">避免存在具有多個服務或連接埠類型定義的「Web 服務描述語言」(WSDL) 檔案。</span><span class="sxs-lookup"><span data-stu-id="75216-140">Avoid Web Services Description Language (WSDL) files with multiple service or port type definitions.</span></span>  
  
-   <span data-ttu-id="75216-141">Web 方法參數必須為可序列化的 Xml。</span><span class="sxs-lookup"><span data-stu-id="75216-141">Web method parameters must be Xml Serializable.</span></span>  
  
-   <span data-ttu-id="75216-142">避免參考對象為包含多重根目錄結構描述的已使用 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="75216-142">Avoid references to consumed Web services that contain multi-rooted schemas.</span></span>  
  
-   <span data-ttu-id="75216-143">避免使用預期應有泛型參數 (例如可為 null 的參數) 的 Web 方法來參考 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="75216-143">Avoid referencing Web services with Web methods expecting generic-based parameters such as nullable parameters.</span></span>  
  
-   <span data-ttu-id="75216-144">不支援 WSDL Import 項目。</span><span class="sxs-lookup"><span data-stu-id="75216-144">The WSDL import element is not supported.</span></span>  
  
 <span data-ttu-id="75216-145">如需有關這些及相關的考量，請參閱[考量當 Consuming Web Services](../core/considerations-when-consuming-web-services.md)。</span><span class="sxs-lookup"><span data-stu-id="75216-145">For more information about these and related considerations, see [Considerations When Consuming Web Services](../core/considerations-when-consuming-web-services.md).</span></span>  
  
### <a name="why-am-i-getting-errors-publishing-my-schema-that-uses-the-include-element"></a><span data-ttu-id="75216-146">為什麼我會收到錯誤發佈我使用的結構描述\<包括 > 項目？</span><span class="sxs-lookup"><span data-stu-id="75216-146">Why am I getting errors publishing my schema that uses the \<include> element?</span></span>  
 <span data-ttu-id="75216-147">無法發行結構描述，如果它們包含循環參考 (包含結構描述具有**包含**要包含的結構描述項目) 或有無法解析**schemaLocation**屬性。</span><span class="sxs-lookup"><span data-stu-id="75216-147">Schemas cannot be published if they include circular references (the included schema has an **include** element to the including schema) or have an unresolved **schemaLocation** attribute.</span></span>  
  
 <span data-ttu-id="75216-148">如需有關的限制**包含**項目，請參閱[Include 項目繫結支援](http://go.microsoft.com/fwlink/?LinkId=62312)。</span><span class="sxs-lookup"><span data-stu-id="75216-148">For more information about the limitation of the **include** element, see [Include Element Binding Support](http://go.microsoft.com/fwlink/?LinkId=62312).</span></span> <span data-ttu-id="75216-149">Web 服務發佈精靈已在.NET Framework 2.0; XSD.exe 相同的限制如需詳細資訊，請參閱[Import 項目繫結支援](http://go.microsoft.com/fwlink/?LinkId=119606)。</span><span class="sxs-lookup"><span data-stu-id="75216-149">The Web Services Publishing Wizard has the same limitations as XSD.exe in .NET Framework 2.0; for more information, see [Import Element Binding Support](http://go.microsoft.com/fwlink/?LinkId=119606).</span></span>  
  
### <a name="why-do-i-receive-errors-when-publishing-my-envelope-schema"></a><span data-ttu-id="75216-150">為什麼我在發佈信封結構描述時會發生錯誤？</span><span class="sxs-lookup"><span data-stu-id="75216-150">Why do I receive errors when publishing my envelope schema?</span></span>  
 <span data-ttu-id="75216-151">如果擁有將要發佈為 Web 服務的信封結構描述，您就必須手動修改產生的 Web 專案。</span><span class="sxs-lookup"><span data-stu-id="75216-151">If you have an envelope schema that you are publishing as a Web service, you need to manually modify the generated Web project.</span></span>  
  
##### <a name="to-modify-the-generated-web-project-for-envelope-schemas"></a><span data-ttu-id="75216-152">若要針對信封結構描述修改所產生的 Web 專案</span><span class="sxs-lookup"><span data-stu-id="75216-152">To modify the generated Web project for envelope schemas</span></span>  
  
1.  <span data-ttu-id="75216-153">開啟 *\<myWebService >*。.asmx.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="75216-153">Open the *\<myWebService>*.asmx.cs file.</span></span>  
  
2.  <span data-ttu-id="75216-154">編輯檔案，並將 `bodyTypeAssemblyQualifiedName = <dll.name.version>``bodyTypeAssemblyQualifiedName = null` 變更為</span><span class="sxs-lookup"><span data-stu-id="75216-154">Edit the file and change `bodyTypeAssemblyQualifiedName = <dll.name.version>` to `bodyTypeAssemblyQualifiedName = null`</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75216-155">如果先前的 .dll 檔案仍存在於 ASP.NET 背景工作處理序中，您可能需要重設 Internet Information Services (IIS)。</span><span class="sxs-lookup"><span data-stu-id="75216-155">You may need to reset Internet Information Services (IIS) if the previous .dll file is still in the ASP.NET worker process.</span></span>  
  
### <a name="clients-of-published-web-services-may-not-receive-server-script-time-out-errors"></a><span data-ttu-id="75216-156">已發佈的 Web 服務用戶端可能無法接收伺服器指令碼逾時錯誤</span><span class="sxs-lookup"><span data-stu-id="75216-156">Clients of published Web services may not receive server script time-out errors</span></span>  
 <span data-ttu-id="75216-157">如果使用 .NET Framework 的 Web 用戶端將會呼叫 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web 服務發佈精靈] 所產生的 Web 服務，這時因為用戶端要求逾時依預設會先行發生，所以用戶端可能就無法接收到伺服器指令碼逾時錯誤。</span><span class="sxs-lookup"><span data-stu-id="75216-157">If Web clients that use .NET Framework are calling a Web service generated with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web Services Publishing Wizard, it is possible that the client cannot receive server script time-out errors because the client request time-out occurs first by default.</span></span> <span data-ttu-id="75216-158">若要解決這個問題，您可以執行下列其中一項工作：</span><span class="sxs-lookup"><span data-stu-id="75216-158">To resolve this problem you can do one of the following:</span></span>  
  
-   <span data-ttu-id="75216-159">增加的值大於伺服器指令碼逾時的用戶端要求逾時的值**HttpWebRequest.Timeout**用戶端上的屬性。</span><span class="sxs-lookup"><span data-stu-id="75216-159">Increase the client request time-out to a value greater than the server script time-out by increasing the value for the **HttpWebRequest.Timeout** property on the client.</span></span>  
  
-   <span data-ttu-id="75216-160">伺服器指令碼逾時的值減少到小於用戶端要求逾時減少可能的值**HttpServerUtility.ScriptTimeout**在伺服器上的屬性。</span><span class="sxs-lookup"><span data-stu-id="75216-160">Reduce the server script time-out to a value less than the client request time-out by reducing the value for the **HttpServerUtility.ScriptTimeout** property on the server.</span></span>  
  
## <a name="common-errors"></a><span data-ttu-id="75216-161">一般錯誤</span><span class="sxs-lookup"><span data-stu-id="75216-161">Common Errors</span></span>  
  
### <a name="a-web-service-returns-an-http-404-file-not-found-error"></a><span data-ttu-id="75216-162">Web 服務傳回 HTTP 404 (找不到檔案) 錯誤</span><span class="sxs-lookup"><span data-stu-id="75216-162">A Web service returns an HTTP 404 (File Not Found) error</span></span>  
  
#### <a name="problem"></a><span data-ttu-id="75216-163">問題</span><span class="sxs-lookup"><span data-stu-id="75216-163">Problem</span></span>  
 <span data-ttu-id="75216-164">嘗試呼叫 Web 服務時傳回 HTTP 404 (找不到檔案) 錯誤。</span><span class="sxs-lookup"><span data-stu-id="75216-164">Attempts to call a Web service return an HTTP 404 (File Not Found) error.</span></span>  
  
#### <a name="cause"></a><span data-ttu-id="75216-165">原因</span><span class="sxs-lookup"><span data-stu-id="75216-165">Cause</span></span>  
 <span data-ttu-id="75216-166">如果裝載 Web 服務的 IIS 伺服器上沒有安裝及/或啟用 ASP.NET，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="75216-166">This error can occur if ASP.NET is not installed and/or enabled on the IIS server that hosts the Web service.</span></span>  
  
#### <a name="resolution"></a><span data-ttu-id="75216-167">解決方案</span><span class="sxs-lookup"><span data-stu-id="75216-167">Resolution</span></span>  
 <span data-ttu-id="75216-168">確認已安裝及啟用安裝 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="75216-168">Ensure that ASP.NET is installed and enabled.</span></span> <span data-ttu-id="75216-169">安裝 .NET Framework (如果尚未安裝的話)，並/或執行 aspnet_regiis.exe 程式；此程式位於 IIS 伺服器的 %WinDir%\Microsoft.NET\Framework\vXXX.XXX\ 資料夾中。</span><span class="sxs-lookup"><span data-stu-id="75216-169">Install the .NET Framework if it is not installed and/or run the aspnet_regiis.exe program located in the %WinDir%\Microsoft.NET\Framework\vXXX.XXX\ folder of the IIS server.</span></span>  
  
### <a name="date-fields-are-removed-from-documents-processed-by-a-web-service-generated-with-the-biztalk-server-web-services-publishing-wizard"></a><span data-ttu-id="75216-170">使用 BizTalk Server Web 服務發佈精靈產生之 Web 服務所處理的文件已移除日期欄位</span><span class="sxs-lookup"><span data-stu-id="75216-170">Date fields are removed from documents processed by a web service generated with the BizTalk Server Web Services Publishing Wizard</span></span>  
  
#### <a name="problem"></a><span data-ttu-id="75216-171">問題</span><span class="sxs-lookup"><span data-stu-id="75216-171">Problem</span></span>  
 <span data-ttu-id="75216-172">當您處理的 web 服務所產生的 BizTalk Server Web 服務發佈精靈，任何包含的欄位中的資料與文件**資料型別**的**xs: date**被移除了文件。</span><span class="sxs-lookup"><span data-stu-id="75216-172">When you process a document with a web service that was generated with the BizTalk Server Web Services Publishing Wizard, any data contained in a field with a **Data Type** of **xs:date** is removed from the document.</span></span>  
  
#### <a name="cause"></a><span data-ttu-id="75216-173">原因</span><span class="sxs-lookup"><span data-stu-id="75216-173">Cause</span></span>  
 <span data-ttu-id="75216-174">如果發佈的協調流程包含結構描述有一或多個欄位，可能會發生這個問題**資料型別**的**xs: date**和**Nillable** 屬性**True**。</span><span class="sxs-lookup"><span data-stu-id="75216-174">This problem can occur if the published orchestration contains a schema with one or more fields that have a **Data Type** of **xs:date** and a **Nillable** property of **True**.</span></span>  
  
#### <a name="workaround"></a><span data-ttu-id="75216-175">解決方式</span><span class="sxs-lookup"><span data-stu-id="75216-175">Workaround</span></span>  
 <span data-ttu-id="75216-176">若要解決這個問題，請在已發行的結構描述中尋找欄位**資料型別**的**xs: date**並確認**Nillable**這些欄位的屬性設定為**False**。</span><span class="sxs-lookup"><span data-stu-id="75216-176">To workaround this problem, locate the fields in the published schema that have a **Data Type** of **xs:date** and verify that the **Nillable** property of these fields is set to **False**.</span></span>  
  
### <a name="a-systemiofilenotfoundexception-error-occurs-when-a-web-service-is-called"></a><span data-ttu-id="75216-177">呼叫 Web 服務時發生 "System.IO.FileNotFoundException" 錯誤</span><span class="sxs-lookup"><span data-stu-id="75216-177">A "System.IO.FileNotFoundException" error occurs when a Web service is called</span></span>  
  
#### <a name="problem"></a><span data-ttu-id="75216-178">問題</span><span class="sxs-lookup"><span data-stu-id="75216-178">Problem</span></span>  
 <span data-ttu-id="75216-179">在 Microsoft ASP.NET Web 應用程式中呼叫 Web 服務時，您可能會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="75216-179">When you call a Web service in a Microsoft ASP.NET Web application, you may receive the following error:</span></span>  
  
 <span data-ttu-id="75216-180">System.IO.FileNotFoundException</span><span class="sxs-lookup"><span data-stu-id="75216-180">System.IO.FileNotFoundException</span></span>  
  
#### <a name="cause"></a><span data-ttu-id="75216-181">原因</span><span class="sxs-lookup"><span data-stu-id="75216-181">Cause</span></span>  
 <span data-ttu-id="75216-182">如果下列其中一項條件成立，就會發生這個錯誤：</span><span class="sxs-lookup"><span data-stu-id="75216-182">This error can occur if either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="75216-183">背景工作處理序沒有權限可以讀取處理序暫存目錄，也沒有權限可以寫入處理序暫存目錄。</span><span class="sxs-lookup"><span data-stu-id="75216-183">The worker process does not have permissions to read to the process Temp directory, and the worker process does not have permissions to write to the process Temp directory.</span></span>  
  
-   <span data-ttu-id="75216-184">XmlSerializer 產生的程式碼中有編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="75216-184">There are compilation errors in the code that XmlSerializer generated.</span></span>  
  
#### <a name="resolution"></a><span data-ttu-id="75216-185">解決方案</span><span class="sxs-lookup"><span data-stu-id="75216-185">Resolution</span></span>  
 <span data-ttu-id="75216-186">此錯誤已記錄在 Microsoft 知識庫文章[823196](http://support.microsoft.com/kb/823196)。</span><span class="sxs-lookup"><span data-stu-id="75216-186">This error is documented in Microsoft Knowledge Base article [823196](http://support.microsoft.com/kb/823196).</span></span> <span data-ttu-id="75216-187">請依照此知識庫文件中＜解決方法＞一節的步驟執行，解決這項錯誤。</span><span class="sxs-lookup"><span data-stu-id="75216-187">Follow the steps in the Resolution section of this Knowledge Base article to resolve this error.</span></span>