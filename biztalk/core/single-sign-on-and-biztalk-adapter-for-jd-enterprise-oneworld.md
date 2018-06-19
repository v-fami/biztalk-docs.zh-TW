---
title: 單一登入與 BizTalk Adapter for JD Enterprise OneWorld |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Single Sign-On
ms.assetid: 44fea3a4-8073-4b64-94e5-1eacbae845d9
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3b0fbe7aa671d543a0fd6cd7da78e05d18c63c3
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24016065"
---
# <a name="single-sign-on-and-biztalk-adapter-for-jd-enterprise-oneworld"></a><span data-ttu-id="7796f-102">單一登入與 BizTalk Adapter for JD Enterprise OneWorld</span><span class="sxs-lookup"><span data-stu-id="7796f-102">Single Sign-On and BizTalk Adapter for JD Enterprise OneWorld</span></span>
<span data-ttu-id="7796f-103">從 SSO 認證資料庫取得單一登入 (SSO) 認證因此，您不需要輸入伺服器系統的登入認證在**傳輸屬性**視窗。</span><span class="sxs-lookup"><span data-stu-id="7796f-103">Single Sign-On (SSO) credentials are obtained from the SSO credentials database; therefore, you do not need to enter the server system's logon credentials in the **Transport Properties** window.</span></span>  
  
 <span data-ttu-id="7796f-104">在設計階段，Microsoft BizTalk Adapter for JD Edwards OneWorld 會以啟動 BizTalk Server 專案的使用者身分取得系統的認證 (針對指定分支機構應用程式)。</span><span class="sxs-lookup"><span data-stu-id="7796f-104">At design-time, Microsoft BizTalk Adapter for JD Edwards OneWorld obtains the credentials for the system (for the specified affiliate application) under the context of the user who started BizTalk Server project.</span></span> <span data-ttu-id="7796f-105">該使用者應為「應用程式使用者」。</span><span class="sxs-lookup"><span data-stu-id="7796f-105">That user should be an Application User.</span></span>  
  
 <span data-ttu-id="7796f-106">在執行階段，當使用 SSO 時，請在通過實例中使用 BizTalk Adapter for JD Edwards OneWorld 做為接收位置。</span><span class="sxs-lookup"><span data-stu-id="7796f-106">At run time, use the BizTalk Adapter for JD Edwards OneWorld as a receive location in the pass-through scenarios when using SSO.</span></span>  
  
 <span data-ttu-id="7796f-107">當 Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="7796f-107">When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user.</span></span> <span data-ttu-id="7796f-108">ISAPI 延伸模組會模擬 Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。</span><span class="sxs-lookup"><span data-stu-id="7796f-108">The ISAPI extension impersonates the Windows user and calls the SSO credential store to obtain an encrypted ticket.</span></span> <span data-ttu-id="7796f-109">此票證會在訊息內容中儲存為 SSOTicket 屬性。</span><span class="sxs-lookup"><span data-stu-id="7796f-109">This ticket is stored as the SSOTicket property in the context of the message.</span></span>  
  
 <span data-ttu-id="7796f-110">訊息接著會導向到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7796f-110">The message is then directed to the Message Box database.</span></span> <span data-ttu-id="7796f-111">當配接器從 MessageBox 資料庫接收訊息時，它會呼叫具有加密票證及分支機構應用程式名稱的 IBTSTicket.ValidateAndRedeemTicket 方法，從 SSO 存放區擷取登入認證。</span><span class="sxs-lookup"><span data-stu-id="7796f-111">When the adapter receives the message from the Message Box database, it calls the IBTSTicket.ValidateAndRedeemTicket method with the encrypted ticket along with the affiliate application name to retrieve the logon credentials from the SSO store.</span></span> <span data-ttu-id="7796f-112">BizTalk Adapter for JD Edwards OneWorld 配接器接著就會使用外部認證連接到系統並處理要求。</span><span class="sxs-lookup"><span data-stu-id="7796f-112">BizTalk Adapter for JD Edwards OneWorld then uses the external credentials to connect to the system and process the request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7796f-113">SSO 組態屬於 BizTalk Server 設定的一部分。</span><span class="sxs-lookup"><span data-stu-id="7796f-113">SSO configuration is part of the BizTalk Server setup.</span></span> <span data-ttu-id="7796f-114">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="7796f-114">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, because this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="7796f-115">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="7796f-115">SSO only functions under a domain account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7796f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7796f-116">See Also</span></span>  
 <span data-ttu-id="7796f-117">[建立分支機構應用程式](../core/creating-affiliate-applications3.md) </span><span class="sxs-lookup"><span data-stu-id="7796f-117">[Creating Affiliate Applications](../core/creating-affiliate-applications3.md) </span></span>  
 [<span data-ttu-id="7796f-118">在配接器的安全性</span><span class="sxs-lookup"><span data-stu-id="7796f-118">Security in the adapter</span></span>](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)