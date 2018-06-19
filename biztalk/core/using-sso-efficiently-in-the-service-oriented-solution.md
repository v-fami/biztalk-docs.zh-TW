---
title: 有效使用 SSO，在服務導向解決方案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SSO, service solutions
- service solution tutorial, SSO
- SSO, using from code
ms.assetid: 809e0ad3-cc7f-4095-87d1-63031675a47f
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66dafba56bdeedb8c7b35b4442623f55e70f1305
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22289262"
---
# <a name="using-sso-efficiently-in-the-service-oriented-solution"></a>有效使用 SSO，在服務導向解決方案
服務導向解決方案使用「企業單一登入」(SSO) 儲存組態值和處理後端系統的認證。 為減少延遲，此解決方案將使用本機快取做為組態值。 此解決方案每五分鐘會重新整理一次快取。  
  
 許多應用程式中的配接器可處理 SSO 作業—包括取得 SSO 票證、贖回票證和使用認證以取得分支機構應用程式的存取權。 但是內嵌版本的服務導向解決方案不使用配接器， 而必須從程式碼使用 SSO。  
  
 本主題描述解決方案使用的快取機制，以及內嵌版本的解決方案如何從程式碼使用 SSO。  
  
## <a name="local-caching-of-configuration-values"></a>組態值的本機快取  
 服務導向解決方案會使用兩個物件， **ConfigPropertyBag**和**ConfigParameters**來處理組態值。 **ConfigPropertyBag**類別保留值，而且僅供**ConfigParameters**類別。 **ConfigParameters**類別可由其他組件的方案來擷取組態參數。 這兩個類別位於**Microsoft.Samples.BizTalk.WoodgroveBank.ConfigHelper**命名空間。  
  
> [!NOTE]
>  服務導向解決方案固定以 300 秒 (5 分鐘) 的間隔重新整理快取。 您可能想要在此解決方案中以可設定的屬性自訂重新整理快取的間隔。 這可在「商務程序管理」解決方案中完成。 如需解決方案如何處理 SSO 的詳細資訊，請參閱[使用 SSO 有效率地在商務程序管理解決方案中](../core/using-sso-efficiently-in-the-business-process-management-solution.md)。 請注意，在這種情況下，在舊的間隔時間結束時重新整理快取之後，重新整理間隔的變更才會生效。  
  
 **ConfigPropertyBag**具有下列方法：  
  
|方法|Description|  
|------------|-----------------|  
|讀取|擷取指定屬性的值。|  
|寫入|將值指派給屬性。|  
  
 類別會使用.NET 的執行個體**NameValueCollection**來保存的值。 這兩種存取方法實作**IPropertyBag**介面從**ipropertybag**命名空間。 **ConfigPropertyBag**類別是內部的類別，而且只能用於**ConfigParameters**類別。  
  
> [!NOTE]
>  屬性包的金鑰名稱不區分大小寫。 基礎**NameValueCollection**使用不區分大小寫的雜湊和不區分大小寫的比較。  
  
 應用程式使用**ConfigParameters**類別來處理 SSO 組態值。 類別有下列公用方法與屬性：  
  
|方法或屬性|Description|  
|-------------------------|-----------------|  
|SSOConfigParameter|指定組態參數的列舉。|  
|GetConfigParameters|用來擷取指定參數值的方法。 使用 SSOConfigParameter 來指示參數。|  
  
 **ConfigParameters**類別使用.NET Timer 類別和委派函式來設定的重新整理**ConfigPropertyBag**:  
  
```  
private static Timer cacheRefreshTimer;  
private static ISSOConfigStore ssoConfigStore;  
private static ReaderWriterLock syncLock;  
  
// Cache refresh interval in milliseconds  
private const int CacheRefreshInterval = 5 * 60 * 1000;  
private static ConfigPropertyBag ssoPropBag;  
  
static ConfigParameters()  
{  
    ssoConfigStore = new ISSOConfigStore();  
    ssoPropBag = new ConfigPropertyBag();  
    syncLock = new ReaderWriterLock();  
  
    ssoConfigStore.GetConfigInfo(SSO_CONFIG_APP,  
         SSO_IDENTIFIER_NAME, SSOFlag.SSO_FLAG_RUNTIME,  
         ssoPropBag);  
  
    cacheRefreshTimer = new Timer(  
        new TimerCallback(ConfigParameters.cacheRefreshCallback),  
        null, CacheRefreshInterval, CacheRefreshInterval);  
}  
```  
  
 請注意，靜態建構函式可初始化靜態成員變數，因此無需建立類別的執行個體便可使用類別方法。 建構函式建立 SSO 組態存放區的執行個體 (**ISSOConfigStore**)，組態屬性包 (**ConfigPropertyBag**)，以及同步處理鎖定 (**ReaderWriterLock**) 用來控制存取**ConfigurationPropertyBag**期間更新和讀取。 建構函式接著會使用**GetConfigInfo**擷取 SSO 組態值，並將它們放在屬性包。 最後，建構函式會建立**計時器**物件，指定的間隔之後呼叫委派函式， **cacheRefreshCallback**。  
  
 **計時器**委派函式是相當直接：  
  
```  
private static void cacheRefreshCallback(object state)  
{  
    // Disable the timer until we are done loading the cache.  
    cacheRefreshTimer.Change(Timeout.Infinite, CacheRefreshInterval);  
  
    // Put the data from SSO in a new property bag so that  
    // we don't have to lock the property bag and block it from being  
    // used. The SSO call is a remote call and may take a while.  
    ConfigPropertyBag propBag2 = new ConfigPropertyBag();  
    ssoConfigStore.GetConfigInfo(SSO_CONFIG_APP,   
        SSO_IDENTIFIER_NAME, SSOFlag.SSO_FLAG_RUNTIME, propBag2);  
  
    // Get a writer lock before updating the cached values.  
    syncLock.AcquireWriterLock(Timeout.Infinite);  
  
    try  
    {  
        ssoPropBag = propBag2;  
    }  
    finally   
    {  
        syncLock.ReleaseWriterLock();  
    }  
    // Enable the timer.  
    cacheRefreshTimer.Change(CacheRefreshInterval,   
        CacheRefreshInterval);  
}  
```  
  
 請注意，快取重新整理回呼方法會停用計時器，所以讓此方法可以一直執行至完成為止。 同時也請注意使用鎖定來控制存取屬性包。 **ReaderWriterLock**是最佳選擇 — 它針對案例有讀取操作多於寫入。 也請注意鎖定、 **syncLock**、 是靜態的在類別宣告所有執行緒均都共用它的相同且單一執行個體層級。  
  
## <a name="using-sso-from-code"></a>從程式碼使用 SSO  
 當使用單一登入從程式碼時，程式碼必須扮演配接器的角色： 也就是從訊息擷取 SSO 票證、 贖回票證，以取得針對後端系統的使用者名稱和密碼，最後，使用後端系統。 服務導向解決方案會透過**Pendingtransactionscaller**方法**Getpendingtransactionsresponse**物件。  
  
 方法如下所示：  
  
```  
public static PendingTransactionsResponse GetPendingTransactionsResponse(XLANGMessage requestMsg)  
{  
    try  
    {  
        // Get config parameter values.  
        int ptTimeout = Convert.ToInt32(  
            ConfigParameters.GetConfigParameter(  
                ConfigParameters.  
                    SSOConfigParameter.  
                        PENDING_TRANSACTIONS_INLINE_TIMEOUT  
            )  
        );  
  
        string ptURL = ConfigParameters.GetConfigParameter(  
            ConfigParameters.  
                SSOConfigParameter.  
                    PENDING_TRANSACTIONS_URL  
        );  
        string ssoAffliateApp = ConfigParameters.  
            GetConfigParameter(ConfigParameters.  
                SSOConfigParameter.  
                    PENDING_TRANSACTIONS_SSO_AFFILIATE_APP  
            );  
  
        // Redeem the SSO ticket and get the userid/password to   
        // use to interact with Pending Transaction System.  
  
        // Extract the ticket…  
        string msgTicket = (string)requestMsg.  
            GetPropertyValue(typeof(BTS.SSOTicket));  
  
        // and the user name of the originating user.  
        string originatorSID = (string)requestMsg.  
            GetPropertyValue(  
                typeof(  
                    Microsoft.BizTalk.XLANGs.BTXEngine.OriginatorSID  
                )  
            );  
  
        string pendTransUserName;  
        // Now, redeem the ticket.  
        string[] pendTransCredential =   
            ssoTicket.RedeemTicket(  
                ssoAffliateApp,  
                originatorSID,  
                msgTicket,  
                SSOFlag.SSO_FLAG_NONE,  
                out pendTransUserName  
            );   
  
        PendingTransactionsRequest req =   
            (PendingTransactionsRequest)requestMsg[0].  
                RetrieveAs(  
                    typeof(PendingTransactionsRequest)  
                );  
        PendingTransactionsResponse resp;  
  
        using (PendingTransactionsWebService  
            svc = new PendingTransactionsWebService())  
        {  
            svc.Url = ptURL;  
            svc.Timeout = ptTimeout;  
  
            // The web service uses basic authentication, so we  
            //need to send the user id and password in the request.  
            CredentialCache credCache = new CredentialCache();  
            NetworkCredential credentialToUse =  
                new NetworkCredential(  
                    pendTransUserName, pendTransCredential[0]  
                );  
            credCache.Add(new Uri(svc.Url), "Basic", credentialToUse);  
            svc.Credentials = credCache;  
  
            resp = svc.GetPendingTransactions(req);  
        }  
        return resp;                  
    }  
    catch (System.Net.WebException webEx)  
    {  
        if (webEx.Status == WebExceptionStatus.Timeout)  
        {  
            throw new PendingTransactionsTimeoutException();  
        }  
        else  
        {  
            Trace.WriteLine("Other Net.WebException: "  
                + webEx.ToString()   
                + (null == webEx.InnerException ? "" :  
                     ("Inner Exception: "   
                        + webEx.InnerException.ToString())  
                )  
            );  
            throw;  
        }  
    }  
    catch(System.Exception ex)  
    {  
        Trace.WriteLine("Other Exception: "  
            + ex.ToString()   
            + (null == ex.InnerException ? "" :   
                 ("Inner Exception: "  
                    + ex.InnerException.ToString())  
                  )  
            );  
        throw;  
    }  
}  
```  
  
 方法一開始會擷取包括 URL 在內的後端系統組態資訊以及後端 (分支機構) 應用程式的名稱。  
  
 此方法必須從訊息擷取票證和原始的要求使用者名稱，才能贖回票證。 訊息做為訊息內容屬性，其中包含票證**BTS。SSOTicket**。 如需詳細資訊，請參閱**訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。 方法也會解壓縮**OriginatorSID**從訊息內容屬性。 取得票證和建立者名稱後，此方法會呼叫票證上的 RedeemTicket 方法以擷取認證。  
  
 剩餘的程式碼則建立認證的 .NET NetworkCredential 快取以及呼叫後端 Web 服務。  
  
> [!NOTE]
>  因為使用者名稱和密碼是以純文字從 SSO 送回，所以會想要將保留該資訊的變數存留時間降至最低。 請注意，程式碼會宣告認證變數內**再試一次**區塊。 變數在從結束時就會過期，**再試一次**區塊。  
  
## <a name="see-also"></a>另請參閱  
 [實作會反白顯示的服務導向解決方案](../core/implementation-highlights-of-the-service-oriented-solution.md)