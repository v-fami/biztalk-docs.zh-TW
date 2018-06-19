---
title: 如何將本機使用者登入非 Windows 應用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b55957f4-22c4-48b5-827a-ab41d8f846ac
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3c2e9ffaede20e29987938a436ad2a091920fce
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22253870"
---
# <a name="how-to-log-a-local-user-on-to-a-non-windows-application"></a><span data-ttu-id="8466b-102">如何登入非 Windows 應用程式的本機使用者</span><span class="sxs-lookup"><span data-stu-id="8466b-102">How to Log a Local User on to a Non-Windows Application</span></span>
<span data-ttu-id="8466b-103">當您以分支機構應用程式設定使用者之後，就可以使用「單一登入」(SSO) 存取外部使用者名稱和目前使用者的認證。</span><span class="sxs-lookup"><span data-stu-id="8466b-103">After you set up your user with an affiliate application, you can use Single Sign-On (SSO) to access the external user name and credentials of the current user.</span></span> <span data-ttu-id="8466b-104">然後您可以使用這些認證將使用者登入在主控件伺服器上執行的分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466b-104">Using these credentials, you can then log your user on to the affiliate application that is running on a host server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8466b-105">除了為 SSO 設定適當的安全性通訊協定之外，您可能也需要設定其他安全性，好讓您的應用程式能夠在正確的資訊安全內容中呼叫 SSO。</span><span class="sxs-lookup"><span data-stu-id="8466b-105">In addition to setting the appropriate security protocols for SSO, you might also need to set additional security to allow your application to call SSO in the correct security context.</span></span> <span data-ttu-id="8466b-106">如果您的應用程式無法在正確的資訊安全內容中呼叫 SSO，SSO 將會拒絕對應用程式的存取。</span><span class="sxs-lookup"><span data-stu-id="8466b-106">If your application cannot call SSO in the correct security context, SSO will deny access to your application.</span></span>  
  
### <a name="to-set-the-security-context-for-an-sso-application"></a><span data-ttu-id="8466b-107">若要為 SSO 應用程式設定資訊安全內容</span><span class="sxs-lookup"><span data-stu-id="8466b-107">To set the security context for an SSO application</span></span>  
  
1.  <span data-ttu-id="8466b-108">識別讓您的應用程式順利執行所需的認證為何。</span><span class="sxs-lookup"><span data-stu-id="8466b-108">Identify what credentials your application needs to run successfully.</span></span>  
  
     <span data-ttu-id="8466b-109">例如，使用 Web 服務或 IIS 中裝載的.NET Framework 遠端處理的應用程式需要模擬用戶端，才能將傳遞適當的認證傳遞 SSO。</span><span class="sxs-lookup"><span data-stu-id="8466b-109">For example, an application that uses Web services or .NET Framework remoting hosted in IIS needs to impersonate the client in order to pass the appropriate credentials on to SSO.</span></span>  
  
2.  <span data-ttu-id="8466b-110">確認相關的安全性設定 (如虛擬目錄、應用程式集區和 web.config 檔案上的設定) 已妥善設定，以便為您的應用程式提供這些認證。</span><span class="sxs-lookup"><span data-stu-id="8466b-110">Confirm that the relevant security settings, such as those on virtual directories, application pools, and web.config files, are set to provide your application with those credentials.</span></span>  
  
     <span data-ttu-id="8466b-111">如需如何設定安全性認證的詳細資訊，請參閱[建構安全 ASP.NET 應用程式： 驗證、 授權和安全通訊](http://go.microsoft.com/fwlink/?LinkId=193906)。</span><span class="sxs-lookup"><span data-stu-id="8466b-111">For more information about how to set security credentials, see [Building Secure ASP.NET Applications: Authentication, Authorization, and Secure Communication](http://go.microsoft.com/fwlink/?LinkId=193906).</span></span>  
  
     <span data-ttu-id="8466b-112">如需 ASP.NET Web 服務傳遞認證的詳細資訊，請參閱[HOW TO： 將傳遞至 ASP.NET Web 服務的目前認證](http://go.microsoft.com/fwlink/?LinkId=193907)。</span><span class="sxs-lookup"><span data-stu-id="8466b-112">For more information about passing credentials for an ASP.NET Web service, see [HOW TO: Pass Current Credentials to an ASP.NET Web Service](http://go.microsoft.com/fwlink/?LinkId=193907).</span></span>  
  
### <a name="to-log-a-local-user-on-to-a-host-application"></a><span data-ttu-id="8466b-113">將本機使用者登入主控件應用程式</span><span class="sxs-lookup"><span data-stu-id="8466b-113">To log a local user on to a host application</span></span>  
  
1.  <span data-ttu-id="8466b-114">接收讓目前使用者登入在主控件伺服器上執行之應用程式的要求。</span><span class="sxs-lookup"><span data-stu-id="8466b-114">Receive the request to log the current user on to an application running on the host server.</span></span>  
  
     <span data-ttu-id="8466b-115">您要負責決定目前使用者以何種方式要求登入主控件應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466b-115">It is your responsibility to determine how the current user requests to be logged on to a host application.</span></span>  
  
2.  <span data-ttu-id="8466b-116">為使用 `ISSOLookup1.GetCredentials` 或 `ISSOLookup2.GetCredentials` 的目前使用者擷取認證。</span><span class="sxs-lookup"><span data-stu-id="8466b-116">Retrieve the credentials for the current user who is using `ISSOLookup1.GetCredentials` or `ISSOLookup2.GetCredentials`.</span></span>  
  
     <span data-ttu-id="8466b-117">您必須提供主應用程式，以及任何相關旗標的名稱。</span><span class="sxs-lookup"><span data-stu-id="8466b-117">You must supply the name of the host application together with any relevant flags.</span></span> <span data-ttu-id="8466b-118">`GetCredentials`傳回的相關聯的使用者名稱與主應用程式的認證。</span><span class="sxs-lookup"><span data-stu-id="8466b-118">`GetCredentials` returns the associated user name and credentials for the host application.</span></span>  
  
     <span data-ttu-id="8466b-119">請注意，您可以使用 `ISSOLookup1` 或 `ISSOLookup2`。</span><span class="sxs-lookup"><span data-stu-id="8466b-119">Note that you can use either `ISSOLookup1` or `ISSOLookup2`.</span></span> <span data-ttu-id="8466b-120">唯一的差別是 `ISSOLookup2` 也有一個將遠端使用者登入本機 Windows 應用程式的方法。</span><span class="sxs-lookup"><span data-stu-id="8466b-120">The only difference is that `ISSOLookup2` also has a method for logging a remote user on to a local windows application.</span></span>  
  
3.  <span data-ttu-id="8466b-121">使用外部使用者名稱和認證登入主控件應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466b-121">Use the external user name and credentials to log on to the host application.</span></span>  
  
     <span data-ttu-id="8466b-122">您要負責決定如何使用認證登入主控件應用程式。</span><span class="sxs-lookup"><span data-stu-id="8466b-122">It is your responsibility to determine how to use the credentials to log on to the host application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8466b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8466b-123">See Also</span></span>  
 [<span data-ttu-id="8466b-124">如何將遠端使用者登入本機應用程式</span><span class="sxs-lookup"><span data-stu-id="8466b-124">How to Log a Remote User on to a Local Application</span></span>](../core/how-to-log-a-remote-user-on-to-a-local-application.md)