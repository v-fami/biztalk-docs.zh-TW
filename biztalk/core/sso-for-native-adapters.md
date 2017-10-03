---
title: "原生配接器的 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, SSO
- SSO, adapters
ms.assetid: d8527f0f-910c-42ce-9bd3-83ab6d4349c0
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45aaf357d943853cc9504762437f554f1d28efb7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sso-for-native-adapters"></a><span data-ttu-id="29a24-102">原生配接器的 SSO</span><span class="sxs-lookup"><span data-stu-id="29a24-102">SSO for Native Adapters</span></span>
<span data-ttu-id="29a24-103">「企業單一登入」(SSO) 可讓您在與不同電腦系統或網站互通時，只需登入一次即可。</span><span class="sxs-lookup"><span data-stu-id="29a24-103">Enterprise Single Sign-On (SSO) enables you to sign on only once when interoperating with different computer systems or Web sites.</span></span> <span data-ttu-id="29a24-104">Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 的這項功能讓 BizTalk 配接器能夠提供適當的使用者識別碼和認證給網路中的多個應用程式，這些應用程式都使用以 Microsoft Windows 認證為基礎的通用驗證機制。</span><span class="sxs-lookup"><span data-stu-id="29a24-104">This feature of Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enables BizTalk adapters to provide the appropriate user ID and credentials to multiple applications within your network that use a common authentication mechanism based on your Microsoft Windows credentials.</span></span> <span data-ttu-id="29a24-105">Windows 驗證您的認證之後，您不必提供其他認證來連接應用程式。</span><span class="sxs-lookup"><span data-stu-id="29a24-105">After Windows authenticates your credentials, you do not need to provide additional credentials to connect to the applications.</span></span>  
  
 <span data-ttu-id="29a24-106">雖然依照預設 SSO 為停用，但 HTTP 和 SOAP 配接器仍然可以使用 SSO。</span><span class="sxs-lookup"><span data-stu-id="29a24-106">SSO is available for the HTTP and SOAP adapters, although it is disabled by default.</span></span> <span data-ttu-id="29a24-107">您可以設定 HTTP 配接器的傳送埠和接收位置以使用 SSO，但您只能設定 SOAP 配接器的接收位置以使用 SSO。</span><span class="sxs-lookup"><span data-stu-id="29a24-107">For the HTTP adapter, you can configure the send port and receive location to use SSO; for the SOAP adapter, you can configure only the receive location to use SSO.</span></span> <span data-ttu-id="29a24-108">兩種配接器都是使用 BizTalk Server 管理主控台或設定單一登入。</span><span class="sxs-lookup"><span data-stu-id="29a24-108">For both adapters, you use the BizTalk Server Administration console to configure SSO.</span></span>  
  
 <span data-ttu-id="29a24-109">SSO 的驗證主要依賴 Windows 驗證以及在 Active Directory 中建立的 Windows 群組。</span><span class="sxs-lookup"><span data-stu-id="29a24-109">Authentication in SSO relies primarily on Windows authentication and the Windows groups created in Active Directory.</span></span> <span data-ttu-id="29a24-110">使用者或系統管理員使用 SSO 完成的所有作業都需要 Windows 先驗證使用者或系統管理員。</span><span class="sxs-lookup"><span data-stu-id="29a24-110">All operations completed by a user or administrator with SSO require that Windows authenticate the user or administrator first.</span></span>  
  
 <span data-ttu-id="29a24-111">如需有關 SSO 如何與 HTTP 和 SOAP 配接器搭配使用的詳細資訊，請參閱＜另請參閱＞中的適當主題。</span><span class="sxs-lookup"><span data-stu-id="29a24-111">For more information about how SSO works with the HTTP and SOAP adapters, see the appropriate topics in See Also.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a24-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29a24-112">See Also</span></span>  
 <span data-ttu-id="29a24-113">[使用 SSO](../core/using-sso.md) </span><span class="sxs-lookup"><span data-stu-id="29a24-113">[Using SSO](../core/using-sso.md) </span></span>  
 <span data-ttu-id="29a24-114">[HTTP 配接器](../core/http-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="29a24-114">[HTTP Adapter](../core/http-adapter.md) </span></span>  
 [<span data-ttu-id="29a24-115">SOAP 配接器</span><span class="sxs-lookup"><span data-stu-id="29a24-115">SOAP Adapter</span></span>](../core/soap-adapter.md)