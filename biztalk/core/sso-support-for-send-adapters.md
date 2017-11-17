---
title: "傳送配接器的 SSO 支援 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 45dc2597-0036-4444-8b35-d18621b003d8
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d590ada6b8ee80c942714a698d0001c207ac6751
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="sso-support-for-send-adapters"></a><span data-ttu-id="58108-102">傳送配接器的 SSO 支援</span><span class="sxs-lookup"><span data-stu-id="58108-102">SSO Support for Send Adapters</span></span>
<span data-ttu-id="58108-103">「企業單一登入」(SSO) 提供的服務能夠跨本機、網路及網域界限，來儲存和傳輸加密的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="58108-103">Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local, network, and domain boundaries.</span></span> <span data-ttu-id="58108-104">當您建立傳輸配接器時，便可利用 SSO API 來處理使用者認證 (傳輸配接器使用者會使用該認證來存取後端應用程式)。</span><span class="sxs-lookup"><span data-stu-id="58108-104">When you create a transport adapter, you can leverage SSO APIs to handle the user credentials that a transport adapter uses to access back-end applications.</span></span>  
  
 <span data-ttu-id="58108-105">不支援 SSO 的傳輸配接器，通常都需要以單一組合的認證予以設定，這些會由配接器用來存取後端應用程式。</span><span class="sxs-lookup"><span data-stu-id="58108-105">Transport adapters that do not support SSO are usually required to be configured with a single set of credentials that they use for accessing back-end applications.</span></span> <span data-ttu-id="58108-106">對於許多後端系統，單一帳戶驗證可能無法滿足所有的安全性強制。</span><span class="sxs-lookup"><span data-stu-id="58108-106">For many back-end systems, single account authentication may not satisfy all security enforcements.</span></span> <span data-ttu-id="58108-107">許多應用程式都根據存取的使用者，提供不同的存取權限。</span><span class="sxs-lookup"><span data-stu-id="58108-107">Many applications provide different access rights depending on the user who is accessing them.</span></span> <span data-ttu-id="58108-108">SSO 讓配接器能夠根據嘗試存取的使用者，動態地選擇要對端點使用的認證。</span><span class="sxs-lookup"><span data-stu-id="58108-108">SSO allows adapters to dynamically choose the credentials to use for the endpoint based on the user who is trying to access it.</span></span>  
  
## <a name="how-send-adapters-work-with-sso"></a><span data-ttu-id="58108-109">傳送配接器如何搭配 SSO 運作</span><span class="sxs-lookup"><span data-stu-id="58108-109">How Send Adapters Work with SSO</span></span>  
 <span data-ttu-id="58108-110">傳送配接器支援 SSO 的驗證及贖回票證，並使用從 SSO 系統取得使用者認證**ISSOTicket.ValidateAndRedeemTicket**應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="58108-110">Send adapters that support SSO validate and redeem the ticket and obtain the user credentials from the SSO system by using the **ISSOTicket.ValidateAndRedeemTicket** API.</span></span> <span data-ttu-id="58108-111">配接器會使用取得的認證來對目的端點進行驗證。</span><span class="sxs-lookup"><span data-stu-id="58108-111">The adapter uses the obtained credentials to authenticate with the destination endpoint.</span></span>  
  
 <span data-ttu-id="58108-112">下列程式碼片段示範傳送配接器如何從 SSO 系統取得使用者認證：</span><span class="sxs-lookup"><span data-stu-id="58108-112">The following code fragment demonstrates how a send adapter obtains the user credentials from the SSO system:</span></span>  
  
```  
public class MyAdapter : IBTTransport,   
                         IBTTransportConfig,   
                         IBTTransportControl,  
                        IPersistPropertyBag,   
                         IBaseComponent  
{  
...  
     private string m_UserName = null;  
     private string m_UserPassword = null;  
  
 // Get user credentials from SSO  
 // AffiliateAppVal is the name of SSO affiliate   
 // application for the specific destination endpoint  
     private void GetUserCredentials(  
 IBaseMessage message,   
 string AffiliateAppVal )  
     {  
 string creds[] = null;  
 string externalUserName = null;  
  
 ISSOTicket ssoTicket = new ISSOTicket();  
 creds = ssoTicket.ValidateAndRedeemTicket(  
 message,   
 AffiliateAppVal,   
 0,   
 out externalUserName);  
  
 m_UserName = externalUserName;  
 m_UserPassword = creds[0];  
     }  
...  
}  
```  
  
## <a name="party-resolution"></a><span data-ttu-id="58108-113">合作對象解析</span><span class="sxs-lookup"><span data-stu-id="58108-113">Party Resolution</span></span>  
 <span data-ttu-id="58108-114">合作對象解析管線元件負責將傳送者憑證或傳送者安全性識別碼 (SID) 對應至所對應的已設定 BizTalk Server 合作對象。</span><span class="sxs-lookup"><span data-stu-id="58108-114">The Party Resolution pipeline component is responsible for mapping the sender certificate or the sender security identifier (SID) to the corresponding configured BizTalk Server party.</span></span> <span data-ttu-id="58108-115">擁有這項資訊提供給他們的配接器應該設定兩個系統訊息內容屬性**WindowsUser**和**SignatureCertificate**，可供下游合作對象解析如果設定的元件。</span><span class="sxs-lookup"><span data-stu-id="58108-115">Adapters that have this information available to them should set the two system message context properties, **WindowsUser** and **SignatureCertificate**, to be consumed by the downstream party resolution component if configured.</span></span>  
  
 <span data-ttu-id="58108-116">**WindowsUser**屬性填入傳送者，例如 redmond\myBtsUser 的網域使用者。</span><span class="sxs-lookup"><span data-stu-id="58108-116">The **WindowsUser** property is populated with the domain user of the sender, for example redmond\myBtsUser.</span></span> <span data-ttu-id="58108-117">**SignatureCertificate**屬性會填入用戶端驗證憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="58108-117">The **SignatureCertificate** property is populated with the thumbprint of the client authentication certificate.</span></span>  
  
## <a name="managing-passwords"></a><span data-ttu-id="58108-118">管理密碼</span><span class="sxs-lookup"><span data-stu-id="58108-118">Managing passwords</span></span>  
 <span data-ttu-id="58108-119">如果您將認證直接放在端點的屬性中，當您需要匯出繫結檔案時，密碼欄位就會變成空白。</span><span class="sxs-lookup"><span data-stu-id="58108-119">If you put credentials directly in the properties of an endpoint, the password field will be blanked out when you need to export a binding file.</span></span> <span data-ttu-id="58108-120">這樣您的使用者就需要重新輸入系統管理員的密碼。</span><span class="sxs-lookup"><span data-stu-id="58108-120">This will require your user to re-enter the password as an administrator.</span></span> <span data-ttu-id="58108-121">您可以對認證使用 SSO 以避免這種困難狀況。</span><span class="sxs-lookup"><span data-stu-id="58108-121">You can avoid this difficulty by using SSO for credentials.</span></span>