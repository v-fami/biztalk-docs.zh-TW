---
title: SSO 和 BizTalk Adapter for TIBCO 企業訊息服務 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 68e85ceb-bf4c-489a-a2c2-1558e718ceed
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 577fa596fadee68c94dfa510de101d01b0ab06e4
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24013413"
---
# <a name="single-sign-on-and-biztalk-adapter-for-tibco-enterprise-message-service"></a><span data-ttu-id="bf07f-102">單一登入與 BizTalk Adapter for TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="bf07f-102">Single Sign-On and BizTalk Adapter for TIBCO Enterprise Message Service</span></span>

## <a name="overview"></a><span data-ttu-id="bf07f-103">概觀</span><span class="sxs-lookup"><span data-stu-id="bf07f-103">Overview</span></span>
<span data-ttu-id="bf07f-104">當您使用單一登入 (SSO) 搭配 Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS) 時，配接器會從 SSO 認證資料庫取得認證因此，您沒有在伺服器系統輸入登入認證**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bf07f-104">When you use Single Sign-On (SSO) with Microsoft BizTalk Adapter for TIBCO Enterprise Message Service (EMS), the adapter obtains the credentials from the SSO Credentials database; therefore, you do not have to enter the logon credentials for the server system in the **Transport Properties** dialog box.</span></span>  
  
 <span data-ttu-id="bf07f-105">在設計階段，配接器會以啟動 BizTalk Server 專案的使用者身分取得系統的認證 (針對指定的分支機構應用程式)。</span><span class="sxs-lookup"><span data-stu-id="bf07f-105">At design time, the adapter obtains the credentials for the system (for the specified affiliate application) under the context of the user who started BizTalk Server project.</span></span> <span data-ttu-id="bf07f-106">該使用者應為「應用程式使用者」。</span><span class="sxs-lookup"><span data-stu-id="bf07f-106">That user should be an Application User.</span></span> <span data-ttu-id="bf07f-107">在執行階段，當使用 SSO 時，請在通過實例中使用 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 接收配接器做為接收位置。</span><span class="sxs-lookup"><span data-stu-id="bf07f-107">At run time, use the Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Receive Adapter as a receive location in the pass-through scenarios when you use SSO.</span></span>  
  
## <a name="processing-requests"></a><span data-ttu-id="bf07f-108">處理要求</span><span class="sxs-lookup"><span data-stu-id="bf07f-108">Processing Requests</span></span>  
 <span data-ttu-id="bf07f-109">當 Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="bf07f-109">When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user.</span></span> <span data-ttu-id="bf07f-110">ISAPI 延伸模組會模擬 Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。</span><span class="sxs-lookup"><span data-stu-id="bf07f-110">The ISAPI extension impersonates the Windows user and calls the SSO credential store to obtain an encrypted ticket.</span></span> <span data-ttu-id="bf07f-111">此票證會在訊息內容中儲存為 SSOTicket 屬性。</span><span class="sxs-lookup"><span data-stu-id="bf07f-111">This ticket is stored as the SSOTicket property in the context of the message.</span></span>  
  
 <span data-ttu-id="bf07f-112">訊息接著會導向到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bf07f-112">The message is then directed to the Message Box database.</span></span> <span data-ttu-id="bf07f-113">當 BizTalk Adapter for TIBCO EMS 從 MessageBox 資料庫接收訊息時，它會呼叫具有加密票證及分支機構應用程式名稱的 ValidateAndRedeemTicket 方法，從 SSO 存放區擷取登入認證。</span><span class="sxs-lookup"><span data-stu-id="bf07f-113">When BizTalk Adapter for TIBCO EMS receives the message from the Message Box database, it calls ValidateAndRedeemTicket with the encrypted ticket together with the affiliate application name to retrieve the logon credentials from the SSO store.</span></span> <span data-ttu-id="bf07f-114">然後此配接器會使用這些外部認證連接至系統並處理要求。</span><span class="sxs-lookup"><span data-stu-id="bf07f-114">The adapter then uses the external credentials to connect to the system and process the request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf07f-115">SSO 組態屬於 BizTalk Server 設定的一部分。</span><span class="sxs-lookup"><span data-stu-id="bf07f-115">SSO configuration is part of the BizTalk Server setup.</span></span> <span data-ttu-id="bf07f-116">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="bf07f-116">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="bf07f-117">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="bf07f-117">SSO only functions under a domain account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf07f-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf07f-118">See Also</span></span>  
 <span data-ttu-id="bf07f-119">[建立分支機構應用程式](../core/creating-affiliate-applications5.md) </span><span class="sxs-lookup"><span data-stu-id="bf07f-119">[Creating Affiliate Applications](../core/creating-affiliate-applications5.md) </span></span>  
 [<span data-ttu-id="bf07f-120">保護配接器</span><span class="sxs-lookup"><span data-stu-id="bf07f-120">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-tibco-ems.md)