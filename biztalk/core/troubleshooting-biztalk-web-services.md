---
title: 疑難排解 BizTalk Web 服務 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cdc86de8-e41e-4878-a66e-e242bcf3b705
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2c2e14955b05397e69c326ce7302108cb6c0eb00
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990663"
---
# <a name="troubleshooting-biztalk-web-services"></a>BizTalk Web 服務疑難排解
本節會針對如何辨識及解決常見 Web 服務問題提供相關建議。  
  
## <a name="general-troubleshooting"></a>一般疑難排解  
  
### <a name="enabling-web-services-publishing-wizard-tracing"></a>啟用 Web 服務發佈精靈追蹤  
 您可以啟用追蹤以偵錯 BizTalk Web 服務發佈精靈，取消註解\<新增\>BTSWebSvcWiz.exe.config 檔案中的節點。 如需有關從 Web 服務發佈精靈取得追蹤資訊的詳細資訊，請參閱 <<c0> [ 如何修改 BTSWebSvcWiz.exe.config](../core/how-to-modify-btswebsvcwiz-exe-config.md)。  
  
### <a name="enabling-soap-message-tracing"></a>啟用 SOAP 訊息追蹤  
 您可以啟用 SOAP 訊息追蹤，協助您使用 SOAP 延伸模組來偵錯 Web 服務發佈應用程式。 如需有關 SOAP 擴充功能的詳細資訊，請參閱 <<c0> [ 如何： 實作 SOAP 延伸模組](http://go.microsoft.com/fwlink/?LinkId=62314)。  
  
### <a name="using-the-throwdetailederror-switch"></a>使用 ThrowDetailedError 參數  
 發生錯誤時，Web 用戶端會接收泛型**SoapException**。  
  
 若要偵錯已發佈的 Web 服務，您可以在 web.config 檔案中加入某個參數，以便控制從該發佈的 Web 服務傳回之例外狀況詳細資料的等級。 交換器**ThrowDetailedError**，且設定為當 **，則為 True**伺服器 proxy 將內部例外狀況資訊傳回給 Web 用戶端，讓您偵錯已發佈的 Web 服務。  
  
 下列 XML 程式碼所示**ThrowDetailedError**下的 web.config 檔案中顯示交換器\<appSettings\>節點：  
  
```  
<appSettings>  
  <add key="ThrowDetailedError" value="False" />  
<appSettings/>  
```  
  
> [!WARNING]
>  內部例外狀況可能包含機密資訊。 偵錯之後，您應該設定**ThrowDetailedError**切換至**False**。  
  
### <a name="using-net-framework-tracing-to-capture-and-log-errors-in-the-web-service"></a>使用 .NET Framework 追蹤來擷取和記錄 Web 服務中的錯誤  
 .NET Framework **System.Diagnostics.Trace**類別可以用來擷取，並將錯誤寫入至文字檔。  
  
##### <a name="to-use-the-systemdiagnosticstrace-class-to-capture-and-write-errors-to-a-text-file"></a>使用 System.Diagnostics.Trace 類別來擷取錯誤並將錯誤寫入文字檔中  
  
1. 更新將 TRACE 編譯器指示詞設定為 Web 服務的 web.config 檔案**真**並加入**TraceSwitch**值：  
  
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
   >  如果 TRACE 編譯器指示詞未設定為 **，則為 true**則不會產生任何追蹤輸出。 **TraceSwitch**值也可以設定在發出呼叫的類別，但這裡設定方便的 web.config 檔案中。 設定**TraceSwitch**值適當的層級，適用於開發用途，並在開發完成以減少或禁止追蹤輸出後變更的值。  
  
2. 建立的執行個體**TraceSwitch**並**TextWriterTraceListener**類別，並使用**try...catch**截獲並將錯誤寫入的 Web 服務 [WebMethod] 呼叫中封鎖追蹤輸出檔。 例如，在嘗試將整數變數 s2 設定為物件變數 o2 之 null 執行個體時所產生的錯誤，將由下列程式碼所截獲：  
  
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
   >  此程式碼是當您建立新時，所預設產生 HelloWorld Web 服務的修改的版本**ASP.Net Web 服務**專案中[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]。  
   > 
   > [!NOTE]
   >  在 Windows Vista 中，您可能必須擁有系統管理員權限，才能將追蹤輸出檔寫入至根資料夾。  
  
3. 重新建立 Web 服務專案。 現在，如果發生錯誤時**嘗試**陳述式中處理例外狀況**攔截**陳述式，且出現錯誤，會寫入追蹤輸出檔。  
  
## <a name="general-troubleshooting-questions-and-answers"></a>一般疑難排解問答集  
 本節包含針對協助您解決與 Web 服務相關問題的一組問答集。  
  
### <a name="i-am-receiving-errors-when-consuming-a-web-service-how-can-i-avoid-them"></a>我在使用 Web 服務時發生錯誤，我要如何避免這些錯誤？  
 使用 Web 服務時要考慮許多細節，其中包括下列幾點：  
  
- 避免在參數名稱中使用兩個底線字元。  
  
- 利用**任何**項目或有**anyAttribute** Web 方法中不支援屬性。  
  
- 避免將 XLANG/s 關鍵字做為 Web 服務名稱或 Web 方法名稱。  
  
- 避免使用 XLANG/s 不支援的 Web 方法參數類型。  
  
- 結構描述中不要使用 C# 關鍵字的項目名稱或無效 C# 識別項的項目名稱。  
  
- 避免存在具有多個服務或連接埠類型定義的「Web 服務描述語言」(WSDL) 檔案。  
  
- Web 方法參數必須為可序列化的 Xml。  
  
- 避免參考對象為包含多重根目錄結構描述的已使用 Web 服務。  
  
- 避免使用預期應有泛型參數 (例如可為 null 的參數) 的 Web 方法來參考 Web 服務。  
  
- 不支援 WSDL Import 項目。  
  
  如需這些詳細資訊和相關的考量，請參閱[考量當 Consuming Web Services](../core/considerations-when-consuming-web-services.md)。  
  
### <a name="why-am-i-getting-errors-publishing-my-schema-that-uses-the-include-element"></a>為什麼我會收到發行我使用的結構描述的錯誤\<包括\>項目？  
 無法發行結構描述，如果它們包含循環參考 (包含結構描述已**包括**要包含的結構描述項目) 或有無法解析**schemaLocation**屬性。  
  
 如需限制的詳細資訊**包括**項目，請參閱[Include 項目繫結支援](http://go.microsoft.com/fwlink/?LinkId=62312)。 Web 服務發佈精靈 會具有相同的限制，和 XSD.exe.NET Framework 2.0;如需詳細資訊，請參閱 < [Import 項目繫結支援](http://go.microsoft.com/fwlink/?LinkId=119606)。  
  
### <a name="why-do-i-receive-errors-when-publishing-my-envelope-schema"></a>為什麼我在發佈信封結構描述時會發生錯誤？  
 如果擁有將要發佈為 Web 服務的信封結構描述，您就必須手動修改產生的 Web 專案。  
  
##### <a name="to-modify-the-generated-web-project-for-envelope-schemas"></a>若要針對信封結構描述修改所產生的 Web 專案  
  
1.  開啟 *\<myWebService\>*。 asmx.cs 檔案。  
  
2.  編輯檔案，並將 `bodyTypeAssemblyQualifiedName = <dll.name.version>``bodyTypeAssemblyQualifiedName = null` 變更為  
  
> [!NOTE]
>  如果先前的 .dll 檔案仍存在於 ASP.NET 背景工作處理序中，您可能需要重設 Internet Information Services (IIS)。  
  
### <a name="clients-of-published-web-services-may-not-receive-server-script-time-out-errors"></a>已發佈的 Web 服務用戶端可能無法接收伺服器指令碼逾時錯誤  
 如果使用 .NET Framework 的 Web 用戶端將會呼叫 [[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Web 服務發佈精靈] 所產生的 Web 服務，這時因為用戶端要求逾時依預設會先行發生，所以用戶端可能就無法接收到伺服器指令碼逾時錯誤。 若要解決這個問題，您可以執行下列其中一項工作：  
  
-   藉由增加的值增加為大於伺服器指令碼逾時的用戶端要求逾時**HttpWebRequest.Timeout**用戶端上的屬性。  
  
-   藉由減少的值減少為小於用戶端要求逾時伺服器指令碼逾時值**HttpServerUtility.ScriptTimeout**伺服器上的屬性。  
  
## <a name="common-errors"></a>一般錯誤  
  
### <a name="a-web-service-returns-an-http-404-file-not-found-error"></a>Web 服務傳回 HTTP 404 (找不到檔案) 錯誤  
  
#### <a name="problem"></a>問題  
 嘗試呼叫 Web 服務時傳回 HTTP 404 (找不到檔案) 錯誤。  
  
#### <a name="cause"></a>原因  
 如果裝載 Web 服務的 IIS 伺服器上沒有安裝及/或啟用 ASP.NET，就會發生這個錯誤。  
  
#### <a name="resolution"></a>解決方案  
 確認已安裝及啟用安裝 ASP.NET。 安裝 .NET Framework (如果尚未安裝的話)，並/或執行 aspnet_regiis.exe 程式；此程式位於 IIS 伺服器的 %WinDir%\Microsoft.NET\Framework\vXXX.XXX\ 資料夾中。  
  
### <a name="date-fields-are-removed-from-documents-processed-by-a-web-service-generated-with-the-biztalk-server-web-services-publishing-wizard"></a>使用 BizTalk Server Web 服務發佈精靈產生之 Web 服務所處理的文件已移除日期欄位  
  
#### <a name="problem"></a>問題  
 當您處理具有與 BizTalk Server Web 服務發佈精靈，與欄位中包含的任何資料產生 web 服務的文件**資料型別**的**xs: date**從移除文件。  
  
#### <a name="cause"></a>原因  
 如果已發佈的協調流程包含有一或多個欄位的結構描述，會發生此問題**資料型別**的**xs: date**並**Nillable** 屬性**True**。  
  
#### <a name="workaround"></a>解決方式  
 若要解決這個問題，請在已發行的結構描述中找出欄位**資料型別**的**xs: date** ，並確認**Nillable**這些欄位的屬性設定為**False**。  
  
### <a name="a-systemiofilenotfoundexception-error-occurs-when-a-web-service-is-called"></a>呼叫 Web 服務時發生 "System.IO.FileNotFoundException" 錯誤  
  
#### <a name="problem"></a>問題  
 在 Microsoft ASP.NET Web 應用程式中呼叫 Web 服務時，您可能會收到下列錯誤：  
  
 System.IO.FileNotFoundException  
  
#### <a name="cause"></a>原因  
 如果下列其中一項條件成立，就會發生這個錯誤：  
  
-   背景工作處理序沒有權限可以讀取處理序暫存目錄，也沒有權限可以寫入處理序暫存目錄。  
  
-   XmlSerializer 產生的程式碼中有編譯錯誤。  
  
#### <a name="resolution"></a>解決方案  
 此錯誤已記錄在 Microsoft 知識庫文件[823196](http://support.microsoft.com/kb/823196)。 請依照此知識庫文件中＜解決方法＞一節的步驟執行，解決這項錯誤。