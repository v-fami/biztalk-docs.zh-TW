---
title: "疑難排解 Internet Information Services |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f77084f1-5797-42ab-bbf6-fe815144232e
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 222d034c2dee38f041bb53b3164869712201bc76
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-internet-information-services"></a>Internet Information Services 疑難排解
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 經常使用 Microsoft Internet Information Services (IIS) 提供各種功能，包括 HTTP、SOAP 和 Windows SharePoint Services 配接器。 本主題描述在使用 IIS 時可能遇到的一些已知問題，以及這些問題的可能解決方案。  
  
## <a name="known-issues"></a>已知問題  
 本主題中記錄的錯誤可能不會顯示，除非您將 Internet Explorer 設定為停用易懂的 HTTP 錯誤訊息。  
  
#### <a name="to-configure-internet-explorer-to-disable-friendly-http-error-messages"></a>將 Internet Explorer 設定為停用易記的 HTTP 錯誤訊息  
  
1.  在**工具**功能表上，按一下 **網際網路選項**。  
  
2.  在**進階**索引標籤的**瀏覽**區段中，清除**顯示易懂的 HTTP 錯誤訊息**核取方塊，然後**確定**。  
  
3.  關閉 Internet Explorer。  
  
#### <a name="http-404---file-not-found-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a>在 IIS 伺服器上存取網頁時發生「HTTP 404 – 找不到檔案」錯誤。  
  
##### <a name="problem"></a>問題  
 當您嘗試存取 IIS 伺服器上的網站時，會出現類似以下的錯誤：  
  
 找不到頁面  
  
 \- 或 -  
  
 HTTP 404 - 找不到檔案  
  
##### <a name="cause"></a>原因  
 發生這個錯誤的原因有下列幾種︰  
  
-   要求的檔案已被重新命名。  
  
-   要求的檔案已經刪除或移至其他位置。  
  
-   由於維護、升級或其他未知的原因，暫時無法使用要求的檔案。  
  
-   要求的檔案不存在。  
  
-   IIS 6.0： 不會啟用適當的 Web 服務延伸模組或 MIME 類型。  
  
-   虛擬目錄對應到另一部伺服器上磁碟機的根目錄。  
  
##### <a name="resolution"></a>解決方案  
 遵循 Microsoft 知識庫文件 248033，"常見原因 IIS 伺服器會傳回 「 HTTP 404-找不到檔案 」 錯誤 」 的解決方案 > 一節中的步驟可在[http://support.microsoft.com/kb/248033](http://support.microsoft.com/kb/248033)。  
  
#### <a name="cannot-find-server-or-dns-error-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a>在 IIS 伺服器上存取網頁時發生「找不到伺服器或 DNS 錯誤」錯誤。  
  
##### <a name="problem"></a>問題  
 當您嘗試存取 IIS 伺服器上的網站時，會出現類似以下的錯誤：  
  
 無法顯示頁面  
  
 \- 或 -  
  
 找不到伺服器或 DNS 錯誤  
  
##### <a name="cause"></a>原因  
 發生這個錯誤的原因有下列幾種︰  
  
-   Internet Explorer 連線設定不正確。  
  
-   安裝的防火牆或 Proxy 軟體設定不正確、未作用或不相容。  
  
-   主機檔案中有不正確的項目。  
  
-   網路配接器未正確作用，或者安裝了不相容的網路配接器驅動程式。  
  
##### <a name="resolution"></a>解決方案  
 遵循 Microsoft 知識庫文章 326155，解決方案 > 一節中的步驟 」 當您嘗試存取網站，Internet Explorer 中的錯誤訊息: 「 無法顯示頁面 」 」 可在[http://support.microsoft.com/kb/326155](http://support.microsoft.com/kb/326155).  
  
#### <a name="401---access-denied-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a>在 IIS 伺服器上存取網頁時發生「401 – 拒絕存取」錯誤。  
  
##### <a name="problem"></a>問題  
 當您嘗試存取 IIS 伺服器上的網站時，會出現類似以下的錯誤：  
  
 401 - 拒絕存取。  
  
##### <a name="cause"></a>原因  
 IIS 定義數種不同的 401 錯誤，指示更為特定的錯誤原因。 這些特定的錯誤碼會顯示在瀏覽器中：  
  
-   401.1 - 未經授權: 因為認證不正確而拒絕存取。  
  
-   401.2 - 登入由於伺服器組態而失敗。  
  
-   401.3 - 未經授權: 因為要求的資源上已設定 ACL 而拒絕存取。  
  
-   401.4 - 未經授權: 網頁伺服器上安裝的篩選器導致授權失敗。  
  
-   401.5 - 未經授權: ISAPI/CGI 應用程式導致授權失敗。  
  
-   401.7 – 存取已遭 Web 伺服器上的 URL 授權原則拒絕。 這個錯誤碼是 IIS 6.0 特有的。  
  
 如需 IIS 7.0 狀態碼的完整清單，請參閱 Microsoft 知識庫文件 943891 「 HTTP 狀態碼 IIS 7.0 中 」 可在[http://support.microsoft.com/kb/943891](http://support.microsoft.com/kb/943891)。  
  
##### <a name="resolution"></a>解決方案  
 請依照[解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)解決 IIS 權限問題。  
  
#### <a name="500---internal-server-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a>在 IIS 伺服器上存取網頁時發生「500 – 內部伺服器錯誤」。  
  
##### <a name="problem"></a>問題  
 當您嘗試存取 IIS 伺服器上的網站時，會出現類似以下的錯誤：  
  
 500 - 內部伺服器錯誤  
  
##### <a name="cause"></a>原因  
 這個錯誤訊息可能是由於各種伺服器端問題所造成。  
  
##### <a name="resolution"></a>解決方案  
 若要解決這個問題，請執行下列動作：  
  
-   如需這個錯誤發生原因的詳細資訊，請檢視 IIS 伺服器的應用程式日誌。  
  
-   如需有助於判斷錯誤原因的詳細資訊，請檢視 IIS 記錄檔或 HTTPERR 記錄檔。 依預設，IIS 記錄檔執行的電腦上[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)]作業系統位於下列目錄：  
  
     *%Windir%\\*system32\LogFiles\W3SVC1\  
  
    > [!NOTE]
    >  *%Windir%*是 IIS 伺服器上的 Windows 目錄位置的預留位置。  
  
     根據預設，在執行 Windows Server 2008 或 Windows Vista 的電腦上，IIS 記錄檔位於下列目錄：  
  
     C:\inetpub\logs\LogFiles\W3SVC1\  
  
     根據預設，[!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] 上的 HTTPERR 記錄檔位於下列目錄：  
  
     *%Windir%*system32LogFilesHTTPERR  
  
    > [!NOTE]
    >  才能使用 HTTPERR 記錄檔上才有[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)]，或 Windows Vista 的電腦。  
  
#### <a name="service-unavailable-error-occurs-when-accessing-a-web-page-on-an-iis-server"></a>在 IIS 伺服器上存取網頁時發生「無法使用服務」錯誤  
  
##### <a name="problem"></a>問題  
 當您嘗試存取 IIS 伺服器上的網站時，會出現類似以下的錯誤：  
  
 服務無法使用  
  
##### <a name="cause"></a>原因  
 此錯誤最常見的原因是網頁的應用程式集區 （IIS 6.0 和 IIS 7.0） 已停止。 使用所指定使用者名稱及/或密碼無效的識別來設定應用程式集區或 COM+ 應用程式時，經常會發生這個錯誤。  
  
##### <a name="resolution"></a>解決方案  
 請依照下列主題的 「 設定 IIS 應用程式主機處理序識別 」 一節中的步驟[解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)設定適當的主機處理序身分識別。  
  
## <a name="see-also"></a>另請參閱  
 [解決 IIS 權限問題的指導方針](../core/guidelines-for-resolving-iis-permissions-problems.md)