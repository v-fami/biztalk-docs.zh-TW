---
title: "單一登入與 BizTalk Adapter for JD Edwards EnterpriseOne |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JD Edwards EnterpriseOne adapters, Single Sign-On
- Single Sign-On, JD Edwards EnterpriseOne adapters
- adapters [JD Edwards EnterpriseOne adapters], Single Sign-On
ms.assetid: efcc3a2d-18a6-4090-9e95-143fb7a356b2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 182e73ed45a1473286a301cf859e619cc5d21287
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-and-biztalk-adapter-for-jd-edwards-enterpriseone"></a><span data-ttu-id="e504d-102">單一登入與 BizTalk Adapter for JD Enterprise OneWorld</span><span class="sxs-lookup"><span data-stu-id="e504d-102">Single Sign-On and BizTalk Adapter for JD Edwards EnterpriseOne</span></span>
<span data-ttu-id="e504d-103">當您將單一登入 (SSO) 與 Microsoft Adapter for JD Edwards EnterpriseOne 搭配使用時，此配接器會從 SSO 認證資料庫取得認證。</span><span class="sxs-lookup"><span data-stu-id="e504d-103">When you use Single Sign-On (SSO) with Microsoft   Adapter for JD Edwards EnterpriseOne, the adapter obtains the credentials from the SSO Credentials database.</span></span> <span data-ttu-id="e504d-104">因此，您不需要在伺服器系統輸入登入認證**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e504d-104">Therefore, you do not need to enter the logon credentials for the server system in the **Transport Properties** dialog box.</span></span>  
  
 <span data-ttu-id="e504d-105">在設計階段，BizTalk Adapter for JD Edwards EnterpriseOne 會以啟動 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 專案的使用者身分取得系統 (所指定分支機構應用程式的系統) 的認證。</span><span class="sxs-lookup"><span data-stu-id="e504d-105">At design-time, BizTalk Adapter for JD Edwards EnterpriseOne obtains the credentials for the system (for the specified affiliate application) under the context of the user who started the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="e504d-106">該使用者應為「應用程式使用者」。</span><span class="sxs-lookup"><span data-stu-id="e504d-106">That user should be an Application User.</span></span> <span data-ttu-id="e504d-107">使用 SSO 的通過實例時，請在執行階段使用 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP 接收配接器做為接收位置。</span><span class="sxs-lookup"><span data-stu-id="e504d-107">At run time, use the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] HTTP Receive Adapter as a receive location in the pass-through scenarios when using SSO.</span></span>  
  
## <a name="processing-requests"></a><span data-ttu-id="e504d-108">處理要求</span><span class="sxs-lookup"><span data-stu-id="e504d-108">Processing Requests</span></span>  
 <span data-ttu-id="e504d-109">當 Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="e504d-109">When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user.</span></span> <span data-ttu-id="e504d-110">ISAPI 延伸模組會模擬 Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。</span><span class="sxs-lookup"><span data-stu-id="e504d-110">The ISAPI extension impersonates the Windows user and calls the SSO credential store to obtain an encrypted ticket.</span></span> <span data-ttu-id="e504d-111">此票證會在訊息內容中儲存為 SSOTicket 屬性。</span><span class="sxs-lookup"><span data-stu-id="e504d-111">This ticket is stored as the SSOTicket property in the context of the message.</span></span>  
  
 <span data-ttu-id="e504d-112">訊息接著會導向到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="e504d-112">The message is then directed to the Message Box database.</span></span> <span data-ttu-id="e504d-113">當 BizTalk Adapter for JD Edwards EnterpriseOne 從 MessageBox 資料庫收到訊息時，它會以加密票證和分支機構應用程式名稱呼叫 `ValidateAndRedeemTicket`，以從 SSO 存放區擷取登入認證。</span><span class="sxs-lookup"><span data-stu-id="e504d-113">When BizTalk Adapter for JD Edwards EnterpriseOne receives the message from the Message Box database, it calls `ValidateAndRedeemTicket` with the encrypted ticket along with the affiliate application name to retrieve the logon credentials from the SSO store.</span></span> <span data-ttu-id="e504d-114">然後此配接器會使用這些外部認證連接至系統並處理要求。</span><span class="sxs-lookup"><span data-stu-id="e504d-114">The adapter then uses the external credentials to connect to the system and process the request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e504d-115">SSO 組態屬於 BizTalk Server 設定的一部分。</span><span class="sxs-lookup"><span data-stu-id="e504d-115">SSO configuration is part of the BizTalk Server setup.</span></span> <span data-ttu-id="e504d-116">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="e504d-116">If you get SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="e504d-117">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="e504d-117">SSO only functions under a domain account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e504d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e504d-118">See Also</span></span>  
 <span data-ttu-id="e504d-119">[建立分支機構應用程式](../core/creating-affiliate-applications4.md) </span><span class="sxs-lookup"><span data-stu-id="e504d-119">[Creating Affiliate Applications](../core/creating-affiliate-applications4.md) </span></span>  
 [<span data-ttu-id="e504d-120">使用單一登入</span><span class="sxs-lookup"><span data-stu-id="e504d-120">Using Single Sign-On</span></span>](../core/using-single-sign-on1.md)