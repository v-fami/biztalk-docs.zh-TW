---
title: BizTalk Server 的已知問題 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1aa5fb60-e8db-4cd2-88be-3c71b7b1d44d
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ab3522254ea7cd965ed1b9172de2c382d214fb6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37014455"
---
# <a name="known-issues-with-biztalk-server"></a>使用 BizTalk Server 的已知的問題
本主題列出一些 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的已知問題。  
  
## <a name="dtc-firewall-rules"></a>DTC 防火牆規則  
 當 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 和 [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] 安裝在不同的電腦時，分散式交易協調器 (MS DTC) 會處理電腦間的交易。 如此一來，在上啟用 DTC 連接埠，在您的防火牆規則[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]電腦。  
  
 設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，DTC 連接埠不在防火牆中啟用時，可能會發生下列錯誤：  
  
 **在資料庫建立; 期間，發生 WMI 錯誤嘗試復原和刪除建立不完整的資料庫 'SQLServerName\BizTalkMsgBoxDb'**  
  
 **產生 WMI 錯誤描述： 類型 'System.EnterpriseServices.TransactionProxyException' 擲回的例外狀況。**  
  
 下列連結提供詳細資訊：  
  
 [管理伺服器的連接埠](http://go.microsoft.com/fwlink/p/?LinkID=275568)  
  
 [BizTalk Server 2013 和 2013 R2 的後續安裝步驟](../install-and-config-guides/post-installation-steps-for-biztalk-server-2013-and-2013-r2.md)  
  
##  <a name="BKMK_BAM"></a> 商務活動監控  
 本節列出商務活動監控 (BAM) 模組的已知的問題。  
  
### <a name="bam-definition-deployment-fails-due-to-a-sql-login-error"></a>BAM 定義部署失敗，因為 SQL 登入錯誤  
 在部署 BAM 定義，此作業可能會因為登入錯誤，錯誤碼為 42000。  
  
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
 BAM 組態會加入至 BAM，若要能夠存取相關的所有資料庫中的 BAM 分析登入帳戶的權限。 不過，組態可能會無法執行這項操作，並提供警告，若不符合任何下列必要條件：  
  
- 執行 BAM 組態的使用者應該安裝分析服務的電腦上的系統管理員。  
  
- 在該電腦上必須允許通過防火牆的遠端管理。  
  
- BAM 分析登入帳戶是否與 BAM 相關的資料庫安裝所在的 SQL Server 的系統管理員，您也可能會收到警告。 您可以略過警告，並往前移動。  
  
  **因應措施**– 您必須與 BAM 相關的所有資料庫上手動新增 BAM 分析登入帳戶的權限。  
  
### <a name="bam-portal-compatibility-with-internet-explorer-10"></a>BAM 入口網站的相容性標記與 Internet Explorer 10  
 若要使用 Internet Explorer 10 中的 BAM 入口網站，您一律必須使用瀏覽器相容性模式中。  
  
### <a name="receiving-notification-e-mails-even-after-the-alert-host-service-is-stopped"></a>接收通知電子郵件，即使警示的主機服務已停止  
 如果您使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，如果您想要使用 BAM 警示，您必須在 SQL Server 中設定 Database Mail 功能。 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 使用與 Database Mail 功能搭配使用的警示的主機服務，來傳送通知的警示。 警示的主機服務，在處理通知之後，傳遞通知的工作負載在 SQL Server Database Mail 元件。 因此，即使您停止警示的主機服務時，您仍可能會收到幾個警示的主機服務，但不是由 Database Mail 元件已處理的事件通知。  
  
### <a name="configuring-tracing-for-bam-alerts"></a>設定 BAM 警示的追蹤  
 如果您使用[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]與[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，和您想要啟用 BAM 警示的診斷追蹤，您必須藉由建立 BAM 警示主機的組態檔。 您必須為檔案名稱**BAMAlerts.exe.config**並將它複製到相同的位置與 EXE (**BAMAlerts.exe**)，其位於 \Program Files\Microsoft BizTalk Server\Tracking\\。  
  
 範例組態檔看起來如下所示。 此檔案會記錄**資訊**層級的事件檢視器的詳細資料。  
  
```  
<configuration>  
  <system.diagnostics>  
    <switches>  
      <add name="LogEventProvider" value="Info"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
##  <a name="BKMK_Upgrade"></a> 使用 BizTalk Server 與 SQL Server 2012 時的問題  
 在使用時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]具有[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]您可以設定**遠端登入逾時**SQL Server 中的值為 20 秒。 如果您不這樣做，您可能會遇到負荷過重的狀況中的錯誤。 如需有關如何在中設定的遠端登入逾時值[!INCLUDE[sqlserver2012](../includes/sqlserver2012-md.md)]，請參閱 [http://msdn.microsoft.com/library/ms175136.aspx](http://msdn.microsoft.com/library/ms175136.aspx)  
  
##  <a name="BKMK_Adapters"></a> 配接器問題  
 此區段會列出已知的問題[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器。  
  
### <a name="dynamic-port-may-fail-while-using-the-windows-sharepoint-services-wss-adapter"></a>使用 Windows SharePoint Services (WSS) 配接器時的動態連接埠可能會失敗  
 使用 WSS 配接器的動態連接埠可能會失敗，發生下列錯誤：  
  
```  
Error details: The Windows SharePoint Services site was not found. The URL "http://server:443/site" points to a SharePoint object for which there is no Windows SharePoint Services site.  
```  
  
 **因應措施**:  
  
-   在 連接埠組態的 網站 url，包括連接埠號碼。 例如， `http://server:80/site`。  
  
-   啟用**Windows Identity Foundation 3.5**功能。  
  
-   確認執行 BizTalk 主控件的帳戶具有 SharePoint 的存取。  
  
### <a name="adapters-available-with-biztalk-adapter-pack-cannot-be-administered-on-a-computer-that-only-has-biztalk-server-administration-component-installed"></a>使用 BizTalk Adapter Pack 配接器無法管理只具有 [已安裝的 BizTalk Server 管理] 元件的電腦上  
 如果您有只在電腦上安裝 BizTalk Adapter Pack[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝的管理主控台，做為 BizTalk Adapter Pack 的一部分安裝的配接器不提供當您建立傳送埠或接收位置。 這是因為這些配接器會對同一部電腦上安裝 BizTalk 執行階段中的相依性。  
  
 因應措施 – 安裝 BizTalk Server 執行階段有配接器組件和 BizTalk Server 管理元件安裝在電腦上。 您不需要在該電腦上設定 BizTalk Server。  
  
## <a name="other-issues"></a>其他問題  
  
### <a name="setupbat-for-biztalk-server-samples-runs-with-a-32-bit-command-prompt"></a>Setup.bat，以便讓 BizTalk Server 範例與 32 位元命令提示字元執行  
 針對[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]隨附此版本的範例，您必須只從 32 位元命令提示字元執行隨附的 setup.bat 檔案。 從 64 位元命令提示字元中執行批次檔，可能會導致失敗。  
  
### <a name="run-setup-as-administrator"></a>以系統管理員身分執行安裝程式  
 安裝時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，使用**系統管理員身分執行**選項。 否則，可能會發生下列錯誤：  
  
 內部錯誤 2761年。 傳回碼： 1  
  
 MSI 安裝傳回 1603-安裝時發生嚴重錯誤。  
  
### <a name="using-certificates-with-1024-key-for-encoding-and-signing-results-in-failure-of-mime-smime-decoding"></a>使用 1024年索引鍵中的憑證，用於編碼和簽署的 MIME SMIME 解碼失敗結果  
 在 Windows 8 中，當訊息使用加密與簽署憑證以 1024年金鑰 MIME SMIME 解碼失敗驗證訊息。 若要避免這個問題，您可以使用以 2048年金鑰的憑證。  
  
### <a name="uddi-resolver-with-esb-toolkit-gives-a-serialization-error"></a>使用 ESB 工具組的 UDDI 解析程式可讓序列化錯誤  
 同時使用 UDDI[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]查閱繫結詳細資料時，可能會遇到的 XML 序列化錯誤。 如果未指定繫結索引鍵，就會發生此錯誤。  
  
### <a name="the-itinerary-designer-for-esb-toolkit"></a>ESB 工具組在路線設計工具  
 路線設計工具[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]目前是[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]安裝媒體。 您可以找到路線設計工具，在媒體的根資料夾，並具有名稱`Microsoft.Practices.Services.Itinerary.DslPackage.vsix`。 更早版本，此檔案時可用的安裝位置[!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]，這通常是 \Program Files\Microsoft [!INCLUDE[esbToolkit_short](../includes/esbtoolkit-short-md.md)]。  
  
### <a name="edi"></a>EDI  
 正在使用 EDI 批次處理。 使用阿拉伯曆或阿拉伯文的本機設定時，協調流程會暫停，發生下列錯誤：  
  
 **錯誤碼： 0xC0C01B52 （協調流程引擎錯誤） 的錯誤描述： 凍結期間因為持續性失敗而暫停。** 阿拉伯文西曆支援從*04/30/1900 00.00.00*要*05/13/2029年 23:59:59*。  
  
 若要解決此問題，請輸入有效的阿拉伯文結束日期。  
  
### <a name="enterprise-single-sign-on"></a>企業單一登入  
 當您安裝企業單一登入 (ESSO)，或當您重新啟動 ESSO 服務時，您可能會看到下列錯誤記錄到事件檢視器。  
  
 **無法載入 \Program Files\Common Files\Enterprise 單一登 On\SSOPSServer.dll 錯誤程式碼： 0x8007007E，找不到指定的模組。** 您可以放心忽略此錯誤。