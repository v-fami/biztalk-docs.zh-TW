---
title: "BizTalk Server 的已知問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1aa5fb60-e8db-4cd2-88be-3c71b7b1d44d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b7998225af7ca598d4df5b4fd98f2826edce3a4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="known-issues-with-biztalk-server"></a>BizTalk Server 的已知的問題
本主題列出一些 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的已知問題。  
  
## <a name="dtc-firewall-rules"></a>DTC 防火牆規則  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 安裝在不同的電腦時，分散式交易協調器 (MS DTC) 會處理電腦間的交易。 如此一來，在上啟用防火牆規則內的 DTC 通訊埠[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
 設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，未在防火牆中啟用的 DTC 通訊埠時，可能會發生下列錯誤：  
  
 **資料庫建立; 發生 WMI 錯誤嘗試回復，並刪除部分建立的資料庫 'SQLServerName\BizTalkMsgBoxDb'**  
  
 **產生 WMI 錯誤描述： 類型 'System.EnterpriseServices.TransactionProxyException' 擲回的例外狀況。**  
  
 下列連結提供詳細資訊：  
  
 [管理伺服器的連接埠](http://go.microsoft.com/fwlink/p/?LinkID=275568)  
  
 [BizTalk Server 2013 和 2013 R2 的後續安裝步驟](../install-and-config-guides/post-installation-steps-for-biztalk-server-2013-and-2013-r2.md)  
  
##  <a name="BKMK_BAM"></a>商務活動監控  
 此區段會列出與商務活動監控 (BAM) 模組的已知的問題。  
  
### <a name="bam-definition-deployment-fails-due-to-a-sql-login-error"></a>BAM 定義部署失敗，因為發生 SQL 登入錯誤  
 同時部署 BAM 定義，此作業可能會因為登入錯誤，錯誤碼為 42000。  
  
```  
...  
Deploying Activity... Done.   
Deploying View... ERROR: The BAM deployment failed.   
Server: The current operation was cancelled because another operation in the transaction failed.   
OLE DB error: OLE DB or ODBC error: Login failed for user <username>.; 42000.   
…  
```  
  
 若要修正此問題，請確定 SQL Analysis Service 登入帳戶對與 BAM 相關的所有資料庫的權限。  
  
### <a name="bam-configuration-might-result-in-warnings-related-to-the-bam-analysis-logon-account"></a>BAM 組態可能會導致 BAM 分析的登入帳戶相關的警告  
 BAM 組態會加入 BAM 分析登入帳戶的權限可以存取它們的 BAM 相關的所有資料庫中。 不過，設定可能會失敗，並發出警告，如果不符合任何下列必要條件：  
  
-   使用者執行 BAM 組態應該安裝 Analysis Services 的電腦上的系統管理員。  
  
-   必須允許通過防火牆的遠端管理該電腦上。  
  
-   BAM 分析登入帳戶是否與 BAM 相關的資料庫安裝所在的 SQL Server 的系統管理員，您也可能會收到警告。 您可以忽略此警告，並往前移動。  
  
 **因應措施**– 您必須手動將 BAM 分析登入帳戶的權限與 BAM 相關的所有資料庫上。  
  
### <a name="bam-portal-compatibility-with-internet-explorer-10"></a>Internet Explorer 10 與 BAM 入口網站的相容性  
 若要使用 Internet Explorer 10 中的 BAM 入口網站，您一律必須使用瀏覽器相容性模式中。  
  
### <a name="receiving-notification-e-mails-even-after-the-alert-host-service-is-stopped"></a>接收通知電子郵件，即使警示的主機服務已停止  
 如果您使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，如果您想要使用 BAM 警示，您必須在 SQL Server 中設定 Database Mail 功能。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Database Mail 功能搭配使用警示的主機服務，來傳送通知的警示。 警示的主機服務之後處理通知, 傳遞通知的工作負載中 SQL Server Database Mail 元件。 因此，即使您停止警示的主機服務時，可能仍可使用幾個警示的主機服務，但不是由 Database Mail 元件已處理的事件通知。  
  
### <a name="configuring-tracing-for-bam-alerts"></a>設定 BAM 警示的追蹤  
 如果您使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，而且您想要啟用 BAM 警示的診斷追蹤，您必須藉由建立 BAM 警示主機組態檔執行。 您必須為檔案名稱**BAMAlerts.exe.config**並將它複製到相同的位置與 EXE (**BAMAlerts.exe**)，這是在 \Program Files\Microsoft BizTalk Server\Tracking\\。  
  
 範例組態檔看起來如下。 這個檔案會記錄**資訊**層級的事件檢視器的詳細資料。  
  
```  
<configuration>  
  <system.diagnostics>  
    <switches>  
      <add name="LogEventProvider" value="Info"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
##  <a name="BKMK_Upgrade"></a>使用 BizTalk Server 與 SQL Server 2012 時問題  
 同時使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]您可以設定**遠端登入逾時**SQL Server 中的值為 20 秒。 如果您不要這樣做，您可能會遇到負荷過重的狀況中的錯誤。 如需有關如何在中設定的遠端登入逾時值指示[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，請參閱[http://msdn.microsoft.com/library/ms175136.aspx](http://msdn.microsoft.com/library/ms175136.aspx)  
  
##  <a name="BKMK_Adapters"></a>配接器問題  
 此區段會列出的已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。  
  
### <a name="dynamic-port-may-fail-while-using-the-windows-sharepoint-services-wss-adapter"></a>動態連接埠可能會使用 Windows SharePoint Services (WSS) 配接器時失敗  
 使用 WSS 配接器的動態連接埠可能會失敗，發生下列錯誤：  
  
```  
Error details: The Windows SharePoint Services site was not found. The URL "http://server:443/site" points to a SharePoint object for which there is no Windows SharePoint Services site.  
```  
  
 **因應措施**:  
  
-   在連接埠組態中，對於此站台 URL，包括連接埠號碼。 例如， `http://server:80/site`。  
  
-   啟用**Windows Identity Foundation 3.5**功能。  
  
-   確認執行 BizTalk 主控件的帳戶具有存取 SharePoint。  
  
### <a name="adapters-available-with-biztalk-adapter-pack-cannot-be-administered-on-a-computer-that-only-has-biztalk-server-administration-component-installed"></a>使用 BizTalk Adapter Pack 配接器無法管理只具有 BizTalk Server 管理元件安裝在電腦上  
 如果您有只在電腦上安裝 BizTalk Adapter Pack[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中安裝，安裝 BizTalk Adapter Pack 的一部分的介面卡沒有可用當您建立傳送埠或接收位置。 這是因為這些配接器對在同一部電腦上安裝 BizTalk 執行階段有相依性。  
  
 因應措施 – 安裝 BizTalk Server 執行階段有配接器組件和 BizTalk Server 管理元件安裝在電腦上。 您不需要該電腦上設定 BizTalk Server。  
  
## <a name="other-issues"></a>其他問題  
  
### <a name="setupbat-for-biztalk-server-samples-runs-with-a-32-bit-command-prompt"></a>Setup.bat，以便讓 BizTalk Server 範例與 32 位元命令提示字元執行  
 如[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]隨附於此版本的範例，您必須只從 32 位元命令提示字元執行隨附的 setup.bat 檔案。 64 位元命令提示字元執行批次檔，可能會導致失敗。  
  
### <a name="run-setup-as-administrator"></a>以系統管理員身分執行安裝程式  
 安裝時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，使用**系統管理員身分執行**選項。 否則，可能會發生下列錯誤：  
  
 內部錯誤 2761年。 傳回碼： 1  
  
 MSI 安裝傳回 1603-安裝時發生嚴重錯誤。  
  
### <a name="using-certificates-with-1024-key-for-encoding-and-signing-results-in-failure-of-mime-smime-decoding"></a>具有 1024年索引鍵使用憑證來進行編碼，並簽署產生的 MIME SMIME 解碼失敗  
 在 Windows 8 上加密並以 1024年的索引鍵使用憑證來簽署訊息時 MIME SMIME 解碼失敗中驗證訊息。 若要避免這個問題，您可以使用憑證具有 2048年索引鍵。  
  
### <a name="uddi-resolver-with-esb-toolkit-gives-a-serialization-error"></a>UDDI 解析程式使用 ESB Toolkit 提供序列化錯誤  
 使用 UDDI 時[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]時查閱繫結的詳細資訊，您可能會遇到 XML 序列化錯誤。 如果未指定繫結索引鍵，就會發生此錯誤。  
  
### <a name="the-itinerary-designer-for-esb-toolkit"></a>ESB Toolkit 路線設計工具  
 路線設計工具的[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]屬於現在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝媒體。 您可以找到媒體的根資料夾在路線設計工具中，名稱`Microsoft.Practices.Services.Itinerary.DslPackage.vsix`。 較舊版本，此檔案時可用的安裝位置[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]，這通常是 \Program Files\Microsoft [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]。  
  
### <a name="edi"></a>EDI  
 EDI 批次處理正在使用中。 使用阿拉伯曆或阿拉伯文本機設定時，協調流程會暫停，發生下列錯誤：  
  
 **錯誤碼： 0xC0C01B52 （協調流程引擎錯誤） 的錯誤描述： 凍結期間暫停由於持續性失敗。** 阿拉伯文西曆支援日期*04/30/1900 00.00.00*至*05/13/2029年 23:59:59*。  
  
 若要解決這個問題，請輸入有效阿拉伯文結束日期。  
  
### <a name="enterprise-single-sign-on"></a>企業單一登入  
 當您安裝企業單一登入 (ESSO)，或當您重新啟動 ESSO 服務時，您可能會看到下列錯誤記錄到事件檢視器。  
  
 **無法載入 \Program Files\Common Files\Enterprise 單一登 On\SSOPSServer.dll 錯誤碼： 0x8007007E，找不到指定的模組。** 您可以放心忽略這個錯誤。