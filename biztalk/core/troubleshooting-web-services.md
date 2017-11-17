---
title: "Web 服務疑難排解 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c32bf542-dcc6-4727-b31f-52bb19d4b89d
caps.latest.revision: "24"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c41800d53005d9f0a8f1472cd61abcd873c84394
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-web-services"></a><span data-ttu-id="7851c-102">Web 服務疑難排解</span><span class="sxs-lookup"><span data-stu-id="7851c-102">Troubleshooting Web Services</span></span>
<span data-ttu-id="7851c-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在使用 SOAP 配接器以及將協調流程發佈為 Web 服務時，均大量使用 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="7851c-103">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] makes extensive use of Web services for use with the SOAP adapter and when publishing orchestrations as Web services.</span></span> <span data-ttu-id="7851c-104">本主題提供可供您進行 Web 服務疑難排解的一些步驟，並說明某些常見的 Web 服務問題以及解決這些問題的方式。</span><span class="sxs-lookup"><span data-stu-id="7851c-104">This topic provides some steps that you can follow to troubleshoot Web services, as well as some common Web services problems and how to resolve those problems.</span></span>  
  
## <a name="use-net-framework-tracing-to-capture-and-log-errors-in-a-web-service"></a><span data-ttu-id="7851c-105">使用 .NET Framework 追蹤來擷取和記錄 Web 服務中的錯誤</span><span class="sxs-lookup"><span data-stu-id="7851c-105">Use .NET Framework tracing to capture and log errors in a Web service</span></span>  
 <span data-ttu-id="7851c-106">.NET Framework **System.Diagnostics.Trace**類別可以用來擷取，並將錯誤寫入至文字檔。</span><span class="sxs-lookup"><span data-stu-id="7851c-106">The .NET Framework **System.Diagnostics.Trace** class can be used to capture and write errors to a text file.</span></span>  
  
#### <a name="to-use-the-systemdiagnosticstrace-class-to-capture-and-write-errors-to-a-text-file"></a><span data-ttu-id="7851c-107">使用 System.Diagnostics.Trace 類別來擷取錯誤並將錯誤寫入文字檔中</span><span class="sxs-lookup"><span data-stu-id="7851c-107">To use the System.Diagnostics.Trace class to capture and write errors to a text file</span></span>  
  
1.  <span data-ttu-id="7851c-108">更新 Web 服務設定的 web.config 檔**追蹤**編譯器指示詞， **true**並加入**TraceSwitch**值：</span><span class="sxs-lookup"><span data-stu-id="7851c-108">Update the web.config file for the Web service to set the **TRACE** compiler directive to **true** and add a **TraceSwitch** value:</span></span>  
  
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
    >  <span data-ttu-id="7851c-109">如果**追蹤**編譯器指示詞未設定為**true**則不會產生任何追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="7851c-109">If the **TRACE** compiler directive is not set to **true** then no trace output will be generated.</span></span> <span data-ttu-id="7851c-110">**TraceSwitch**值也可以設定在呼叫類別中，但此處仍會設定為了方便起見在 web.config 檔案中。</span><span class="sxs-lookup"><span data-stu-id="7851c-110">The **TraceSwitch** value can also be set in the calling class, but is set here in the web.config file for convenience.</span></span> <span data-ttu-id="7851c-111">設定**TraceSwitch**值設定為適當的層級，供開發應用程式和開發以減少或禁止追蹤輸出完成之後變更的值。</span><span class="sxs-lookup"><span data-stu-id="7851c-111">Set the **TraceSwitch** value to the appropriate level for development purposes and change the value after development is complete to reduce or inhibit trace output.</span></span>  
  
2.  <span data-ttu-id="7851c-112">建立的執行個體**TraceSwitch**和**TextWriterTraceListener**類別和使用**try … catch**截獲並將錯誤寫入的 Web 服務 [WebMethod] 呼叫中封鎖追蹤輸出檔。</span><span class="sxs-lookup"><span data-stu-id="7851c-112">Create an instance of the **TraceSwitch** and **TextWriterTraceListener** classes and use a **try…catch** block in the Web service [WebMethod] call to trap and write errors to a trace output file.</span></span> <span data-ttu-id="7851c-113">例如，在嘗試將整數變數 s2 設定為物件變數 o2 之 null 執行個體時所產生的錯誤，將由下列程式碼所截獲：</span><span class="sxs-lookup"><span data-stu-id="7851c-113">For example, the following code traps an error that is generated when attempting to set the integer variable s2 to a null instance of the object variable o2:</span></span>  
  
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
                Trace.WriteLineIf(WebSvcTraceSwitch.Level = TraceLevel.Warning, "Exception caught: " + e.Message);  
                //Writes to the trace file if specified TraceLevel switch value (in web.config) >= 2  
                TestTracer.Dispose();  
                return "An error occurred in the Web service, please contact the web server administrator.";  
            }  
        }  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7851c-114">此程式碼是修改的 HelloWorld Web 服務時即建立新產生的預設版本**ASP.Net Web 服務**專案在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7851c-114">This code is a modified version of the default HelloWorld Web service that is generated when you create a new **ASP.Net Web Service** project in Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7851c-115">在 Windows Vista 中，您可能必須擁有系統管理員權限，才能將追蹤輸出檔寫入至根資料夾。</span><span class="sxs-lookup"><span data-stu-id="7851c-115">For Windows Vista, Administrator privileges may be required to write the trace output file to the root folder.</span></span>  
  
3.  <span data-ttu-id="7851c-116">重新建立 Web 服務專案。</span><span class="sxs-lookup"><span data-stu-id="7851c-116">Rebuild the Web service project.</span></span> <span data-ttu-id="7851c-117">現在，如果發生錯誤時**再試一次**陳述式中處理例外狀況**攔截**陳述式和錯誤會寫入追蹤輸出檔。</span><span class="sxs-lookup"><span data-stu-id="7851c-117">Now, if an error occurs in the **Try** statement the exception is handled in the **Catch** statement and an error is written to the trace output file.</span></span>  
  
## <a name="known-issues"></a><span data-ttu-id="7851c-118">已知問題</span><span class="sxs-lookup"><span data-stu-id="7851c-118">Known Issues</span></span>  
  
#### <a name="a-web-service-returns-an-http-404-file-not-found-error"></a><span data-ttu-id="7851c-119">Web 服務傳回 HTTP 404 (找不到檔案) 錯誤</span><span class="sxs-lookup"><span data-stu-id="7851c-119">A Web service returns an HTTP 404 (File Not Found) error</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="7851c-120">問題</span><span class="sxs-lookup"><span data-stu-id="7851c-120">Problem</span></span>  
 <span data-ttu-id="7851c-121">嘗試呼叫 Web 服務時傳回 HTTP 404 (找不到檔案) 錯誤。</span><span class="sxs-lookup"><span data-stu-id="7851c-121">Attempts to call a Web service return an HTTP 404 (File Not Found) error.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="7851c-122">原因</span><span class="sxs-lookup"><span data-stu-id="7851c-122">Cause</span></span>  
 <span data-ttu-id="7851c-123">如果裝載 Web 服務的 IIS 伺服器上沒有安裝及/或啟用 ASP.NET，就會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="7851c-123">This error can occur if ASP.NET is not installed and/or enabled on the IIS server that hosts the Web service.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="7851c-124">解決方案</span><span class="sxs-lookup"><span data-stu-id="7851c-124">Resolution</span></span>  
 <span data-ttu-id="7851c-125">確認已安裝及啟用安裝 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="7851c-125">Ensure that ASP.NET is installed and enabled.</span></span> <span data-ttu-id="7851c-126">安裝[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]如果它不是安裝和/或執行**aspnet_regiis.exe**程式位於 %WinDir%\Microsoft.NET\Framework\\*vXXX.XXX*\ IIS 伺服器的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7851c-126">Install the [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] if it is not installed and/or run the **aspnet_regiis.exe** program located in the %WinDir%\Microsoft.NET\Framework\\*vXXX.XXX*\ folder of the IIS server.</span></span>  
  
#### <a name="a-systemiofilenotfoundexception-error-occurs-when-a-web-service-is-called"></a><span data-ttu-id="7851c-127">呼叫 Web 服務時發生 "System.IO.FileNotFoundException" 錯誤</span><span class="sxs-lookup"><span data-stu-id="7851c-127">A "System.IO.FileNotFoundException" error occurs when a Web service is called</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="7851c-128">問題</span><span class="sxs-lookup"><span data-stu-id="7851c-128">Problem</span></span>  
 <span data-ttu-id="7851c-129">在 Microsoft ASP.NET Web 應用程式中呼叫 Web 服務時，您可能會收到下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="7851c-129">When you call a Web service in a Microsoft ASP.NET Web application, you may receive the following error:</span></span>  
  
 <span data-ttu-id="7851c-130">**System.IO.FileNotFoundException**</span><span class="sxs-lookup"><span data-stu-id="7851c-130">**System.IO.FileNotFoundException**</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="7851c-131">原因</span><span class="sxs-lookup"><span data-stu-id="7851c-131">Cause</span></span>  
 <span data-ttu-id="7851c-132">如果下列其中一項條件成立，就會發生這個錯誤：</span><span class="sxs-lookup"><span data-stu-id="7851c-132">This error can occur if either of the following conditions is true:</span></span>  
  
-   <span data-ttu-id="7851c-133">背景工作處理序沒有權限可以讀取處理序暫存目錄，也沒有權限可以寫入處理序暫存目錄。</span><span class="sxs-lookup"><span data-stu-id="7851c-133">The worker process does not have permissions to read to the process Temp directory, and the worker process does not have permissions to write to the process Temp directory.</span></span>  
  
-   <span data-ttu-id="7851c-134">XmlSerializer 產生的程式碼中有編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="7851c-134">There are compilation errors in the code that XmlSerializer generated.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="7851c-135">解決方案</span><span class="sxs-lookup"><span data-stu-id="7851c-135">Resolution</span></span>  
 <span data-ttu-id="7851c-136">此錯誤已記錄在 Microsoft 知識庫文件 823196 [PRB： 您會收到"System.IO.FileNotFoundException"錯誤時用戶端應用程式會呼叫 Web 服務](http://go.microsoft.com/fwlink/?LinkID=84694)"。</span><span class="sxs-lookup"><span data-stu-id="7851c-136">This error is documented in Microsoft Knowledge Base article 823196, [PRB: You Receive a "System.IO.FileNotFoundException" Error When the Client Application Calls a Web Service](http://go.microsoft.com/fwlink/?LinkID=84694)".</span></span> <span data-ttu-id="7851c-137">請依照此知識庫文件中＜解決方法＞一節的步驟執行，解決這項錯誤。</span><span class="sxs-lookup"><span data-stu-id="7851c-137">Follow the steps in the Resolution section of this Knowledge Base article to resolve this error.</span></span>  
  
#### <a name="date-fields-are-removed-from-documents-processed-by-a-web-service-generated-with-the-biztalk-server-web-services-publishing-wizard"></a><span data-ttu-id="7851c-138">使用 BizTalk Server Web 服務發佈精靈產生之 Web 服務所處理的文件已移除日期欄位</span><span class="sxs-lookup"><span data-stu-id="7851c-138">Date fields are removed from documents processed by a web service generated with the BizTalk Server Web Services Publishing Wizard</span></span>  
  
##### <a name="problem"></a><span data-ttu-id="7851c-139">問題</span><span class="sxs-lookup"><span data-stu-id="7851c-139">Problem</span></span>  
 <span data-ttu-id="7851c-140">當您處理的 web 服務所產生的 BizTalk Server Web 服務發佈精靈，任何包含的欄位中的資料與文件**資料型別**的**xs: date**和**Nillable**屬性**True**從文件中移除。</span><span class="sxs-lookup"><span data-stu-id="7851c-140">When you process a document with a web service that was generated with the BizTalk Server Web Services Publishing Wizard, any data contained in a field with a **Data Type** of **xs:date** and a **Nillable** property of **True** is removed from the document.</span></span>  
  
##### <a name="cause"></a><span data-ttu-id="7851c-141">原因</span><span class="sxs-lookup"><span data-stu-id="7851c-141">Cause</span></span>  
 <span data-ttu-id="7851c-142">這個問題發生的原因，是因為 Microsoft .NET Framework 類別庫命名空間 System.Xml.Serialization 所提供的 XmlSerializer 類別發生已知問題。</span><span class="sxs-lookup"><span data-stu-id="7851c-142">This problem occurs because of a known issue with the XmlSerializer class that is available with the Microsoft .NET Framework Class Library namespace System.Xml.Serialization.</span></span>  
  
##### <a name="resolution"></a><span data-ttu-id="7851c-143">解決方案</span><span class="sxs-lookup"><span data-stu-id="7851c-143">Resolution</span></span>  
 <span data-ttu-id="7851c-144">若要解決此問題，請安裝.NET Framework 2.0 hotfix 記載於 Microsoft 知識庫文件 925272"[修正： XML 序列化可能會遺失某些選用項目在.NET Framework 2.0 的 XSD 結構描述](http://go.microsoft.com/fwlink/?LinkId=84696)"。</span><span class="sxs-lookup"><span data-stu-id="7851c-144">To resolve this issue, install the .NET Framework 2.0 hotfix documented in Microsoft Knowledge Base article 925272, "[FIX: The XML serialization may lose some optional elements in an XSD schema in the .NET Framework 2.0](http://go.microsoft.com/fwlink/?LinkId=84696)".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7851c-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7851c-145">See Also</span></span>  
 <span data-ttu-id="7851c-146">[解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md) </span><span class="sxs-lookup"><span data-stu-id="7851c-146">[Guidelines for Resolving IIS Permissions Problems](../core/guidelines-for-resolving-iis-permissions-problems.md) </span></span>  
 [<span data-ttu-id="7851c-147">解決 Web 服務的權限問題的指導方針</span><span class="sxs-lookup"><span data-stu-id="7851c-147">Guidelines for Resolving Web Services Permissions Problems</span></span>](../core/guidelines-for-resolving-web-services-permissions-problems.md)