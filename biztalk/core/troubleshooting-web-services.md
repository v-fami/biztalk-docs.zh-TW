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
# <a name="troubleshooting-web-services"></a>Web 服務疑難排解
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 在使用 SOAP 配接器以及將協調流程發佈為 Web 服務時，均大量使用 Web 服務。 本主題提供可供您進行 Web 服務疑難排解的一些步驟，並說明某些常見的 Web 服務問題以及解決這些問題的方式。  
  
## <a name="use-net-framework-tracing-to-capture-and-log-errors-in-a-web-service"></a>使用 .NET Framework 追蹤來擷取和記錄 Web 服務中的錯誤  
 .NET Framework **System.Diagnostics.Trace**類別可以用來擷取，並將錯誤寫入至文字檔。  
  
#### <a name="to-use-the-systemdiagnosticstrace-class-to-capture-and-write-errors-to-a-text-file"></a>使用 System.Diagnostics.Trace 類別來擷取錯誤並將錯誤寫入文字檔中  
  
1.  更新 Web 服務設定的 web.config 檔**追蹤**編譯器指示詞， **true**並加入**TraceSwitch**值：  
  
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
    >  如果**追蹤**編譯器指示詞未設定為**true**則不會產生任何追蹤輸出。 **TraceSwitch**值也可以設定在呼叫類別中，但此處仍會設定為了方便起見在 web.config 檔案中。 設定**TraceSwitch**值設定為適當的層級，供開發應用程式和開發以減少或禁止追蹤輸出完成之後變更的值。  
  
2.  建立的執行個體**TraceSwitch**和**TextWriterTraceListener**類別和使用**try … catch**截獲並將錯誤寫入的 Web 服務 [WebMethod] 呼叫中封鎖追蹤輸出檔。 例如，在嘗試將整數變數 s2 設定為物件變數 o2 之 null 執行個體時所產生的錯誤，將由下列程式碼所截獲：  
  
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
    >  此程式碼是修改的 HelloWorld Web 服務時即建立新產生的預設版本**ASP.Net Web 服務**專案在 Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
  
    > [!NOTE]
    >  在 Windows Vista 中，您可能必須擁有系統管理員權限，才能將追蹤輸出檔寫入至根資料夾。  
  
3.  重新建立 Web 服務專案。 現在，如果發生錯誤時**再試一次**陳述式中處理例外狀況**攔截**陳述式和錯誤會寫入追蹤輸出檔。  
  
## <a name="known-issues"></a>已知問題  
  
#### <a name="a-web-service-returns-an-http-404-file-not-found-error"></a>Web 服務傳回 HTTP 404 (找不到檔案) 錯誤  
  
##### <a name="problem"></a>問題  
 嘗試呼叫 Web 服務時傳回 HTTP 404 (找不到檔案) 錯誤。  
  
##### <a name="cause"></a>原因  
 如果裝載 Web 服務的 IIS 伺服器上沒有安裝及/或啟用 ASP.NET，就會發生這個錯誤。  
  
##### <a name="resolution"></a>解決方案  
 確認已安裝及啟用安裝 ASP.NET。 安裝[!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)]如果它不是安裝和/或執行**aspnet_regiis.exe**程式位於 %WinDir%\Microsoft.NET\Framework\\*vXXX.XXX*\ IIS 伺服器的資料夾。  
  
#### <a name="a-systemiofilenotfoundexception-error-occurs-when-a-web-service-is-called"></a>呼叫 Web 服務時發生 "System.IO.FileNotFoundException" 錯誤  
  
##### <a name="problem"></a>問題  
 在 Microsoft ASP.NET Web 應用程式中呼叫 Web 服務時，您可能會收到下列錯誤：  
  
 **System.IO.FileNotFoundException**  
  
##### <a name="cause"></a>原因  
 如果下列其中一項條件成立，就會發生這個錯誤：  
  
-   背景工作處理序沒有權限可以讀取處理序暫存目錄，也沒有權限可以寫入處理序暫存目錄。  
  
-   XmlSerializer 產生的程式碼中有編譯錯誤。  
  
##### <a name="resolution"></a>解決方案  
 此錯誤已記錄在 Microsoft 知識庫文件 823196 [PRB： 您會收到"System.IO.FileNotFoundException"錯誤時用戶端應用程式會呼叫 Web 服務](http://go.microsoft.com/fwlink/?LinkID=84694)"。 請依照此知識庫文件中＜解決方法＞一節的步驟執行，解決這項錯誤。  
  
#### <a name="date-fields-are-removed-from-documents-processed-by-a-web-service-generated-with-the-biztalk-server-web-services-publishing-wizard"></a>使用 BizTalk Server Web 服務發佈精靈產生之 Web 服務所處理的文件已移除日期欄位  
  
##### <a name="problem"></a>問題  
 當您處理的 web 服務所產生的 BizTalk Server Web 服務發佈精靈，任何包含的欄位中的資料與文件**資料型別**的**xs: date**和**Nillable**屬性**True**從文件中移除。  
  
##### <a name="cause"></a>原因  
 這個問題發生的原因，是因為 Microsoft .NET Framework 類別庫命名空間 System.Xml.Serialization 所提供的 XmlSerializer 類別發生已知問題。  
  
##### <a name="resolution"></a>解決方案  
 若要解決此問題，請安裝.NET Framework 2.0 hotfix 記載於 Microsoft 知識庫文件 925272"[修正： XML 序列化可能會遺失某些選用項目在.NET Framework 2.0 的 XSD 結構描述](http://go.microsoft.com/fwlink/?LinkId=84696)"。  
  
## <a name="see-also"></a>另請參閱  
 [解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)   
 [解決 Web 服務的權限問題的指導方針](../core/guidelines-for-resolving-web-services-permissions-problems.md)