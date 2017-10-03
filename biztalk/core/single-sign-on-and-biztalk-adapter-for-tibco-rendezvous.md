---
title: "單一登入與 BizTalk Adapter for TIBCO Rendezvous |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, using with the adapter
- Single Sign-On, using with the adapter
- HTTP requests, processing
ms.assetid: 52e698bb-38ba-4a12-b15a-d1581061d62f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54529d8eefb351471ea1c2bd7278c744737b66f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-tibco-rendezvous"></a><span data-ttu-id="f3797-102">單一登入與 BizTalk Adapter for TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="f3797-102">Single Sign-On and BizTalk Adapter for TIBCO Rendezvous</span></span>
<span data-ttu-id="f3797-103">當您使用單一登入 (SSO) 搭配 Microsoft BizTalk Adapter for TIBCO Rendezvous 時，配接器會從 SSO 認證資料庫取得認證因此，您沒有在伺服器系統輸入登入認證**傳輸屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="f3797-103">When you use Single Sign-On (SSO) with Microsoft BizTalk Adapter for TIBCO Rendezvous, the adapter obtains the credentials from the SSO Credentials database; therefore, you do not have to enter the logon credentials for the server system in the **Transport Properties** window.</span></span>  
  
 <span data-ttu-id="f3797-104">在設計階段，配接器會以啟動 BizTalk Server 專案的使用者身分取得系統的認證 (針對指定的分支機構應用程式)。</span><span class="sxs-lookup"><span data-stu-id="f3797-104">At design time, the adapter obtains the credentials for the system (for the specified affiliate application) under the context of the user who started BizTalk Server project.</span></span> <span data-ttu-id="f3797-105">該使用者應為「應用程式使用者」。</span><span class="sxs-lookup"><span data-stu-id="f3797-105">That user should be an Application User.</span></span> <span data-ttu-id="f3797-106">在執行階段，當使用 SSO 時，請在通過實例中使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 接收配接器做為接收位置。</span><span class="sxs-lookup"><span data-stu-id="f3797-106">At run time, use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Receive Adapter as a receive location in the pass-through scenarios when you use SSO.</span></span>  
  
## <a name="processing-requests"></a><span data-ttu-id="f3797-107">處理要求</span><span class="sxs-lookup"><span data-stu-id="f3797-107">Processing Requests</span></span>  
 <span data-ttu-id="f3797-108">當 Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="f3797-108">When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user.</span></span> <span data-ttu-id="f3797-109">ISAPI 延伸模組會模擬 Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。</span><span class="sxs-lookup"><span data-stu-id="f3797-109">The ISAPI extension impersonates the Windows user and calls the SSO credential store to obtain an encrypted ticket.</span></span> <span data-ttu-id="f3797-110">此票證會在訊息內容中儲存為 SSOTicket 屬性。</span><span class="sxs-lookup"><span data-stu-id="f3797-110">This ticket is stored as the SSOTicket property in the context of the message.</span></span>  
  
 <span data-ttu-id="f3797-111">訊息接著會導向到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f3797-111">The message is then directed to the Message Box database.</span></span> <span data-ttu-id="f3797-112">當 BizTalk Adapter for TIBCO Rendezvous 從 MessageBox 資料庫接收訊息時，它會使用加密票證及分支機構應用程式名稱呼叫 `ValidateAndRedeemTicket`，從 SSO 存放區擷取登入認證。</span><span class="sxs-lookup"><span data-stu-id="f3797-112">When BizTalk Adapter for TIBCO Rendezvous receives the message from the Message Box database, it calls `ValidateAndRedeemTicket` with the encrypted ticket together with the affiliate application name to retrieve the logon credentials from the SSO store.</span></span> <span data-ttu-id="f3797-113">然後此配接器會使用這些外部認證連接至系統並處理要求。</span><span class="sxs-lookup"><span data-stu-id="f3797-113">The adapter then uses the external credentials to connect to the system and process the request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f3797-114">SSO 組態屬於 BizTalk Server 設定的一部分。</span><span class="sxs-lookup"><span data-stu-id="f3797-114">SSO configuration is part of the BizTalk Server setup.</span></span> <span data-ttu-id="f3797-115">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="f3797-115">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="f3797-116">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="f3797-116">SSO only functions under a domain account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3797-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3797-117">See Also</span></span>  
 <span data-ttu-id="f3797-118">[建立分支機構應用程式](../core/creating-affiliate-applications1.md) </span><span class="sxs-lookup"><span data-stu-id="f3797-118">[Creating Affiliate Applications](../core/creating-affiliate-applications1.md) </span></span>  
 [<span data-ttu-id="f3797-119">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="f3797-119">Using Single Sign-On</span></span>](../core/using-single-sign-on5.md)