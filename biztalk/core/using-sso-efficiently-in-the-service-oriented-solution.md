---
title: "有效使用 SSO，在服務導向解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, service solutions
- service solution tutorial, SSO
- SSO, using from code
ms.assetid: 809e0ad3-cc7f-4095-87d1-63031675a47f
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 66dafba56bdeedb8c7b35b4442623f55e70f1305
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="using-sso-efficiently-in-the-service-oriented-solution"></a><span data-ttu-id="9ba41-102">有效使用 SSO，在服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9ba41-102">Using SSO Efficiently in the Service Oriented Solution</span></span>
<span data-ttu-id="9ba41-103">服務導向解決方案使用「企業單一登入」(SSO) 儲存組態值和處理後端系統的認證。</span><span class="sxs-lookup"><span data-stu-id="9ba41-103">The service oriented solution uses Enterprise Single Sign-On (SSO) both to store configuration values and to handle credentials for the back-end systems.</span></span> <span data-ttu-id="9ba41-104">為減少延遲，此解決方案將使用本機快取做為組態值。</span><span class="sxs-lookup"><span data-stu-id="9ba41-104">To reduce latency, the solution uses a local cache for the configuration values.</span></span> <span data-ttu-id="9ba41-105">此解決方案每五分鐘會重新整理一次快取。</span><span class="sxs-lookup"><span data-stu-id="9ba41-105">The solution refreshes the cache every five minutes.</span></span>  
  
 <span data-ttu-id="9ba41-106">許多應用程式中的配接器可處理 SSO 作業—包括取得 SSO 票證、贖回票證和使用認證以取得分支機構應用程式的存取權。</span><span class="sxs-lookup"><span data-stu-id="9ba41-106">In many applications, the adapters handle the SSO operations—including getting an SSO ticket, redeeming the ticket, and using the credentials to gain access to the affiliate application.</span></span> <span data-ttu-id="9ba41-107">但是內嵌版本的服務導向解決方案不使用配接器，</span><span class="sxs-lookup"><span data-stu-id="9ba41-107">However, the inline version of the service oriented solution does not use adapters.</span></span> <span data-ttu-id="9ba41-108">而必須從程式碼使用 SSO。</span><span class="sxs-lookup"><span data-stu-id="9ba41-108">It must use SSO from code.</span></span>  
  
 <span data-ttu-id="9ba41-109">本主題描述解決方案使用的快取機制，以及內嵌版本的解決方案如何從程式碼使用 SSO。</span><span class="sxs-lookup"><span data-stu-id="9ba41-109">This topic describes the caching mechanism used by the solution, as well as how the inline version of the solution uses SSO from code.</span></span>  
  
## <a name="local-caching-of-configuration-values"></a><span data-ttu-id="9ba41-110">組態值的本機快取</span><span class="sxs-lookup"><span data-stu-id="9ba41-110">Local Caching of Configuration Values</span></span>  
 <span data-ttu-id="9ba41-111">服務導向解決方案會使用兩個物件， **ConfigPropertyBag**和**ConfigParameters**來處理組態值。</span><span class="sxs-lookup"><span data-stu-id="9ba41-111">The service oriented solution uses two objects, **ConfigPropertyBag** and **ConfigParameters**, to handle the configuration values.</span></span> <span data-ttu-id="9ba41-112">**ConfigPropertyBag**類別保留值，而且僅供**ConfigParameters**類別。</span><span class="sxs-lookup"><span data-stu-id="9ba41-112">The **ConfigPropertyBag** class holds the values and is used only by the **ConfigParameters** class.</span></span> <span data-ttu-id="9ba41-113">**ConfigParameters**類別可由其他組件的方案來擷取組態參數。</span><span class="sxs-lookup"><span data-stu-id="9ba41-113">The **ConfigParameters** class is used by the other parts of the solution to retrieve the configuration parameters.</span></span> <span data-ttu-id="9ba41-114">這兩個類別位於**Microsoft.Samples.BizTalk.WoodgroveBank.ConfigHelper**命名空間。</span><span class="sxs-lookup"><span data-stu-id="9ba41-114">Both classes are in the **Microsoft.Samples.BizTalk.WoodgroveBank.ConfigHelper** namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ba41-115">服務導向解決方案固定以 300 秒 (5 分鐘) 的間隔重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="9ba41-115">The Service Oriented solution fixes the cache refresh interval at 300 seconds (5 minutes).</span></span> <span data-ttu-id="9ba41-116">您可能想要在此解決方案中以可設定的屬性自訂重新整理快取的間隔。</span><span class="sxs-lookup"><span data-stu-id="9ba41-116">You may, instead, want to make the cache refresh interval itself  a configurable property in this solution.</span></span> <span data-ttu-id="9ba41-117">這可在「商務程序管理」解決方案中完成。</span><span class="sxs-lookup"><span data-stu-id="9ba41-117">This is done in the Business Process Management solution.</span></span> <span data-ttu-id="9ba41-118">如需解決方案如何處理 SSO 的詳細資訊，請參閱[使用 SSO 有效率地在商務程序管理解決方案中](../core/using-sso-efficiently-in-the-business-process-management-solution.md)。</span><span class="sxs-lookup"><span data-stu-id="9ba41-118">For more information about how that solution handles SSO, see [Using SSO Efficiently in the Business Process Management Solution](../core/using-sso-efficiently-in-the-business-process-management-solution.md).</span></span> <span data-ttu-id="9ba41-119">請注意，在這種情況下，在舊的間隔時間結束時重新整理快取之後，重新整理間隔的變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="9ba41-119">Notice that, in such a case, a change in the refresh interval does not take effect until the cache is refreshed at the end of the old interval time.</span></span>  
  
 <span data-ttu-id="9ba41-120">**ConfigPropertyBag**具有下列方法：</span><span class="sxs-lookup"><span data-stu-id="9ba41-120">The **ConfigPropertyBag** has the following methods:</span></span>  
  
|<span data-ttu-id="9ba41-121">方法</span><span class="sxs-lookup"><span data-stu-id="9ba41-121">Method</span></span>|<span data-ttu-id="9ba41-122">Description</span><span class="sxs-lookup"><span data-stu-id="9ba41-122">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="9ba41-123">讀取</span><span class="sxs-lookup"><span data-stu-id="9ba41-123">Read</span></span>|<span data-ttu-id="9ba41-124">擷取指定屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9ba41-124">Retrieves a value for a given property.</span></span>|  
|<span data-ttu-id="9ba41-125">寫入</span><span class="sxs-lookup"><span data-stu-id="9ba41-125">Write</span></span>|<span data-ttu-id="9ba41-126">將值指派給屬性。</span><span class="sxs-lookup"><span data-stu-id="9ba41-126">Assigns a value to a property.</span></span>|  
  
 <span data-ttu-id="9ba41-127">類別會使用.NET 的執行個體**NameValueCollection**來保存的值。</span><span class="sxs-lookup"><span data-stu-id="9ba41-127">The class uses an instance of a .NET **NameValueCollection** to hold the values.</span></span> <span data-ttu-id="9ba41-128">這兩種存取方法實作**IPropertyBag**介面從**ipropertybag**命名空間。</span><span class="sxs-lookup"><span data-stu-id="9ba41-128">The two access methods implement the **IPropertyBag** interface from the **Microsoft.BizTalk.SSOClient.Interop** namespace.</span></span> <span data-ttu-id="9ba41-129">**ConfigPropertyBag**類別是內部的類別，而且只能用於**ConfigParameters**類別。</span><span class="sxs-lookup"><span data-stu-id="9ba41-129">The **ConfigPropertyBag** class is an internal class and used only by the **ConfigParameters** class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ba41-130">屬性包的金鑰名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="9ba41-130">Key names in the property bag are case insensitive.</span></span> <span data-ttu-id="9ba41-131">基礎**NameValueCollection**使用不區分大小寫的雜湊和不區分大小寫的比較。</span><span class="sxs-lookup"><span data-stu-id="9ba41-131">The underlying **NameValueCollection** uses case-insensitive hashing and case-insensitive comparisons.</span></span>  
  
 <span data-ttu-id="9ba41-132">應用程式使用**ConfigParameters**類別來處理 SSO 組態值。</span><span class="sxs-lookup"><span data-stu-id="9ba41-132">The application uses the **ConfigParameters** class to handle the SSO configuration values.</span></span> <span data-ttu-id="9ba41-133">類別有下列公用方法與屬性：</span><span class="sxs-lookup"><span data-stu-id="9ba41-133">The class has the following public methods and attributes:</span></span>  
  
|<span data-ttu-id="9ba41-134">方法或屬性</span><span class="sxs-lookup"><span data-stu-id="9ba41-134">Method or Attribute</span></span>|<span data-ttu-id="9ba41-135">Description</span><span class="sxs-lookup"><span data-stu-id="9ba41-135">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="9ba41-136">SSOConfigParameter</span><span class="sxs-lookup"><span data-stu-id="9ba41-136">SSOConfigParameter</span></span>|<span data-ttu-id="9ba41-137">指定組態參數的列舉。</span><span class="sxs-lookup"><span data-stu-id="9ba41-137">An enumeration for specifying configuration parameters.</span></span>|  
|<span data-ttu-id="9ba41-138">GetConfigParameters</span><span class="sxs-lookup"><span data-stu-id="9ba41-138">GetConfigParameters</span></span>|<span data-ttu-id="9ba41-139">用來擷取指定參數值的方法。</span><span class="sxs-lookup"><span data-stu-id="9ba41-139">A method used to retrieve a value for a given parameter.</span></span> <span data-ttu-id="9ba41-140">使用 SSOConfigParameter 來指示參數。</span><span class="sxs-lookup"><span data-stu-id="9ba41-140">Uses the SSOConfigParameter to indicate the parameter.</span></span>|  
  
 <span data-ttu-id="9ba41-141">**ConfigParameters**類別使用.NET Timer 類別和委派函式來設定的重新整理**ConfigPropertyBag**:</span><span class="sxs-lookup"><span data-stu-id="9ba41-141">The **ConfigParameters** class uses the .NET Timer class and a delegate function to set up the refresh of the **ConfigPropertyBag**:</span></span>  
  
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
  
 <span data-ttu-id="9ba41-142">請注意，靜態建構函式可初始化靜態成員變數，因此無需建立類別的執行個體便可使用類別方法。</span><span class="sxs-lookup"><span data-stu-id="9ba41-142">Notice that the static constructor initializes the static member variables thus enabling the use of class methods without creating an instance of the class.</span></span> <span data-ttu-id="9ba41-143">建構函式建立 SSO 組態存放區的執行個體 (**ISSOConfigStore**)，組態屬性包 (**ConfigPropertyBag**)，以及同步處理鎖定 (**ReaderWriterLock**) 用來控制存取**ConfigurationPropertyBag**期間更新和讀取。</span><span class="sxs-lookup"><span data-stu-id="9ba41-143">The constructor creates instances of the SSO configuration store (**ISSOConfigStore**), the configuration property bag (**ConfigPropertyBag**), and a synchronization lock (**ReaderWriterLock**) used to control access to the **ConfigurationPropertyBag** during updates and reads.</span></span> <span data-ttu-id="9ba41-144">建構函式接著會使用**GetConfigInfo**擷取 SSO 組態值，並將它們放在屬性包。</span><span class="sxs-lookup"><span data-stu-id="9ba41-144">The constructor then uses **GetConfigInfo** to retrieve the SSO configuration values and to put them in the property bag.</span></span> <span data-ttu-id="9ba41-145">最後，建構函式會建立**計時器**物件，指定的間隔之後呼叫委派函式， **cacheRefreshCallback**。</span><span class="sxs-lookup"><span data-stu-id="9ba41-145">Finally, the constructor creates a **Timer** object that, after the specified interval, calls the delegate function, **cacheRefreshCallback**.</span></span>  
  
 <span data-ttu-id="9ba41-146">**計時器**委派函式是相當直接：</span><span class="sxs-lookup"><span data-stu-id="9ba41-146">The **Timer** delegate function is relatively straightforward:</span></span>  
  
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
  
 <span data-ttu-id="9ba41-147">請注意，快取重新整理回呼方法會停用計時器，所以讓此方法可以一直執行至完成為止。</span><span class="sxs-lookup"><span data-stu-id="9ba41-147">Notice that the cache refresh callback method disables the timer so that the method can run all the way through.</span></span> <span data-ttu-id="9ba41-148">同時也請注意使用鎖定來控制存取屬性包。</span><span class="sxs-lookup"><span data-stu-id="9ba41-148">Also notice the use of the locks to control access to the property bag.</span></span> <span data-ttu-id="9ba41-149">**ReaderWriterLock**是最佳選擇 — 它針對案例有讀取操作多於寫入。</span><span class="sxs-lookup"><span data-stu-id="9ba41-149">The **ReaderWriterLock** is the best choice here—it is designed for cases where there are more reads than writes.</span></span> <span data-ttu-id="9ba41-150">也請注意鎖定、 **syncLock**、 是靜態的在類別宣告所有執行緒均都共用它的相同且單一執行個體層級。</span><span class="sxs-lookup"><span data-stu-id="9ba41-150">Notice also that the lock, **syncLock**, is static and declared at the class level that all threads share the same, single instance of it.</span></span>  
  
## <a name="using-sso-from-code"></a><span data-ttu-id="9ba41-151">從程式碼使用 SSO</span><span class="sxs-lookup"><span data-stu-id="9ba41-151">Using SSO from Code</span></span>  
 <span data-ttu-id="9ba41-152">當使用單一登入從程式碼時，程式碼必須扮演配接器的角色： 也就是從訊息擷取 SSO 票證、 贖回票證，以取得針對後端系統的使用者名稱和密碼，最後，使用後端系統。</span><span class="sxs-lookup"><span data-stu-id="9ba41-152">When using single sign-on from code, the code must take on the role of the adapter: that is,retrieve the SSO ticket from the message, redeem the ticket to get the user name and password for the back-end system, and, finally, use the back-end system.</span></span> <span data-ttu-id="9ba41-153">服務導向解決方案會透過**Pendingtransactionscaller**方法**Getpendingtransactionsresponse**物件。</span><span class="sxs-lookup"><span data-stu-id="9ba41-153">The service-oriented solution does this through the **GetPendingTransactionsResponse** method of the **PendingTransactionsCaller** object.</span></span>  
  
 <span data-ttu-id="9ba41-154">方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="9ba41-154">The method appears as follows:</span></span>  
  
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
  
 <span data-ttu-id="9ba41-155">方法一開始會擷取包括 URL 在內的後端系統組態資訊以及後端 (分支機構) 應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ba41-155">The method begins by retrieving configuration information, including the URL, for the back-end system and the name of the backend (affiliate) application.</span></span>  
  
 <span data-ttu-id="9ba41-156">此方法必須從訊息擷取票證和原始的要求使用者名稱，才能贖回票證。</span><span class="sxs-lookup"><span data-stu-id="9ba41-156">To redeem the ticket, the method must extract the ticket and original requesting user name from the message.</span></span> <span data-ttu-id="9ba41-157">訊息做為訊息內容屬性，其中包含票證**BTS。SSOTicket**。</span><span class="sxs-lookup"><span data-stu-id="9ba41-157">The message contains the ticket as one of the message context properties, **BTS.SSOTicket**.</span></span> <span data-ttu-id="9ba41-158">如需詳細資訊，請參閱**訊息內容屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ba41-158">For more information, see **Message Context Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> <span data-ttu-id="9ba41-159">方法也會解壓縮**OriginatorSID**從訊息內容屬性。</span><span class="sxs-lookup"><span data-stu-id="9ba41-159">The method also extracts the **OriginatorSID** from the message context properties.</span></span> <span data-ttu-id="9ba41-160">取得票證和建立者名稱後，此方法會呼叫票證上的 RedeemTicket 方法以擷取認證。</span><span class="sxs-lookup"><span data-stu-id="9ba41-160">With the ticket and the originator's name in hand, the method calls the RedeemTicket method on the ticket to retrieve the credentials.</span></span>  
  
 <span data-ttu-id="9ba41-161">剩餘的程式碼則建立認證的 .NET NetworkCredential 快取以及呼叫後端 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="9ba41-161">The remainder of the code creates a .NET NetworkCredential cache for the credentials and calls the back-end Web service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ba41-162">因為使用者名稱和密碼是以純文字從 SSO 送回，所以會想要將保留該資訊的變數存留時間降至最低。</span><span class="sxs-lookup"><span data-stu-id="9ba41-162">Because the user name and password come back from SSO in clear text, you want to minimize the lifetime of variables holding that information.</span></span> <span data-ttu-id="9ba41-163">請注意，程式碼會宣告認證變數內**再試一次**區塊。</span><span class="sxs-lookup"><span data-stu-id="9ba41-163">Notice that the code declares the credential variables within a **try** block.</span></span> <span data-ttu-id="9ba41-164">變數在從結束時就會過期，**再試一次**區塊。</span><span class="sxs-lookup"><span data-stu-id="9ba41-164">Here, the variables expire upon exit from the **try** block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ba41-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ba41-165">See Also</span></span>  
 [<span data-ttu-id="9ba41-166">實作會反白顯示的服務導向解決方案</span><span class="sxs-lookup"><span data-stu-id="9ba41-166">Implementation Highlights of the Service Oriented Solution</span></span>](../core/implementation-highlights-of-the-service-oriented-solution.md)