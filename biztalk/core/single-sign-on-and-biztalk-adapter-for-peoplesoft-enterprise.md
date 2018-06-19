---
title: 單一登入與 BizTalk Adapter for PeopleSoft Enterprise |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- processing HTTP requests
- Single Sign-On, using with the adapter
- HTTP requests, processing
ms.assetid: d8ad75f1-a83f-4722-a43f-50dc95df2f9d
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bb898906bfd3087ef909e59990a16ce16c2822c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2017
ms.locfileid: "24015597"
---
# <a name="single-sign-on-and-biztalk-adapter-for-peoplesoft-enterprise"></a><span data-ttu-id="32d27-102">單一登入與 BizTalk Adapter for PeopleSoft Enterprise</span><span class="sxs-lookup"><span data-stu-id="32d27-102">Single Sign-On and BizTalk Adapter for PeopleSoft Enterprise</span></span>
<span data-ttu-id="32d27-103">當您使用單一登入 (SSO) 搭配 Microsoft BizTalk Adapter for PeopleSoft Enterprise 時，配接器會從 SSO 認證資料庫取得認證因此，您沒有在伺服器系統輸入登入認證**傳輸屬性** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="32d27-103">When you use Single Sign-On (SSO) with Microsoft BizTalk Adapter for PeopleSoft Enterprise, the adapter obtains the credentials from the SSO Credentials database; therefore, you do not have to enter the logon credentials for the server system in the **Transport Properties** dialog box.</span></span>  
  
 <span data-ttu-id="32d27-104">在設計階段，BizTalk Adapter for PeopleSoft Enterprise 會以用於啟動 BizTalk Server 專案的使用者身分取得系統的認證 (針對指定的分支機構應用程式)。</span><span class="sxs-lookup"><span data-stu-id="32d27-104">At design-time, BizTalk Adapter for PeopleSoft Enterprise obtains the credentials for the system (for the specified affiliate application) under the context of the user who started the BizTalk Server project.</span></span> <span data-ttu-id="32d27-105">該使用者應為「應用程式使用者」。</span><span class="sxs-lookup"><span data-stu-id="32d27-105">That user should be an Application User.</span></span>  
  
## <a name="processing-requests"></a><span data-ttu-id="32d27-106">處理要求</span><span class="sxs-lookup"><span data-stu-id="32d27-106">Processing Requests</span></span>  
 <span data-ttu-id="32d27-107">當 Internet Information Services (IIS) 從 Web 用戶端收到 HTTP 要求時，IIS 會驗證使用者。</span><span class="sxs-lookup"><span data-stu-id="32d27-107">When Internet Information Services (IIS) receives an HTTP request from a Web client, IIS authenticates the user.</span></span> <span data-ttu-id="32d27-108">ISAPI 延伸模組會模擬 Windows 使用者，然後呼叫 SSO 認證存放區以取得加密的票證。</span><span class="sxs-lookup"><span data-stu-id="32d27-108">The ISAPI extension impersonates the Windows user and then calls the SSO credential store to obtain an encrypted ticket.</span></span> <span data-ttu-id="32d27-109">此票證會在訊息內容中儲存為 SSOTicket 屬性。</span><span class="sxs-lookup"><span data-stu-id="32d27-109">This ticket is stored as the SSOTicket property in the context of the message.</span></span>  
  
 <span data-ttu-id="32d27-110">訊息接著會導向到 MessageBox 資料庫。</span><span class="sxs-lookup"><span data-stu-id="32d27-110">The message is then directed to the Message Box database.</span></span> <span data-ttu-id="32d27-111">當 BizTalk Adapter for PeopleSoft Enterprises 從 MessageBox 資料庫收到訊息時，它會以加密票證和分支機構應用程式名稱呼叫 ValidateAndRedeemTicket，以從 SSO 存放區擷取登入認證。</span><span class="sxs-lookup"><span data-stu-id="32d27-111">When BizTalk Adapter for PeopleSoft Enterprises receives the message from the Message Box database, it calls ValidateAndRedeemTicket with the encrypted ticket together with the affiliate application name to retrieve the logon credentials from the SSO store.</span></span> <span data-ttu-id="32d27-112">然後此配接器會使用這些外部認證連接至系統並處理要求。</span><span class="sxs-lookup"><span data-stu-id="32d27-112">The adapter then uses the external credentials to connect to the system and process the request.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32d27-113">SSO 組態屬於 BizTalk Server 設定的一部分。</span><span class="sxs-lookup"><span data-stu-id="32d27-113">SSO configuration is part of the BizTalk Server setup.</span></span> <span data-ttu-id="32d27-114">收到 SSO 錯誤時，請確認您設定 BizTalk Server 時有使用網域帳戶，因為企業單一登入服務的功能會受影響。</span><span class="sxs-lookup"><span data-stu-id="32d27-114">If you receive SSO errors, verify that you used a domain account when you configured BizTalk Server, as this affects the function of the Enterprise SSO service.</span></span> <span data-ttu-id="32d27-115">SSO 僅能在網域帳戶運作。</span><span class="sxs-lookup"><span data-stu-id="32d27-115">SSO only functions under a domain account.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d27-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32d27-116">See Also</span></span>  
 <span data-ttu-id="32d27-117">[建立分支機構應用程式](../core/creating-affiliate-applications2.md) </span><span class="sxs-lookup"><span data-stu-id="32d27-117">[Creating Affiliate Applications](../core/creating-affiliate-applications2.md) </span></span>  
 [<span data-ttu-id="32d27-118">保護配接器</span><span class="sxs-lookup"><span data-stu-id="32d27-118">Secure the adapter</span></span>](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)