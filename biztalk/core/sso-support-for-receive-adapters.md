---
title: 接收配接器的 SSO 支援 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4767387c-f24b-4986-aaed-6724c5d6b347
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e3c992f47ad46b4a9d5ee095ad650f6cc492179
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22276662"
---
# <a name="sso-support-for-receive-adapters"></a><span data-ttu-id="0840c-102">接收配接器的 SSO 支援</span><span class="sxs-lookup"><span data-stu-id="0840c-102">SSO Support for Receive Adapters</span></span>
<span data-ttu-id="0840c-103">「企業單一登入」(SSO) 提供的服務能夠跨本機、網路及網域界限，來儲存和傳輸加密的使用者認證。</span><span class="sxs-lookup"><span data-stu-id="0840c-103">Enterprise Single Sign-On (SSO) provides services to store and transmit encrypted user credentials across local, network, and domain boundaries.</span></span> <span data-ttu-id="0840c-104">傳輸配接器寫入器可以利用 SSO API 來處理使用者認證，以便讓傳輸配接器用來存取後端應用程式。</span><span class="sxs-lookup"><span data-stu-id="0840c-104">Transport adapter writers can leverage SSO APIs to handle the user credentials that a transport adapter uses to access back-end applications.</span></span>  
  
 <span data-ttu-id="0840c-105">不支援 SSO 的傳輸配接器，通常都需要以單一組合的認證予以設定，這些會由配接器用來存取後端應用程式。</span><span class="sxs-lookup"><span data-stu-id="0840c-105">Transport adapters that do not support SSO are usually required to be configured with a single set of credentials that they use for accessing back-end applications.</span></span> <span data-ttu-id="0840c-106">對於許多後端系統，單一帳戶驗證可能無法滿足所有的安全性強制。</span><span class="sxs-lookup"><span data-stu-id="0840c-106">For many back-end systems, single account authentication may not satisfy all security enforcements.</span></span> <span data-ttu-id="0840c-107">許多應用程式都根據存取的使用者，提供不同的存取權限。</span><span class="sxs-lookup"><span data-stu-id="0840c-107">Many applications provide different access rights depending on the user who is accessing them.</span></span> <span data-ttu-id="0840c-108">SSO 讓配接器能夠根據嘗試存取的使用者，動態地選擇要對端點使用的認證。</span><span class="sxs-lookup"><span data-stu-id="0840c-108">SSO allows adapters to dynamically choose the credentials to use for the endpoint based on the user who is trying to access it.</span></span>  
  
## <a name="how-receive-adapters-work-with-sso"></a><span data-ttu-id="0840c-109">接收配接器如何搭配 SSO 運作</span><span class="sxs-lookup"><span data-stu-id="0840c-109">How Receive Adapters Work with SSO</span></span>  
 <span data-ttu-id="0840c-110">支援 SSO 的接收配接器會在接收訊息後，以及將其發佈到 BizTalk Server 前，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="0840c-110">Receive adapters that support SSO perform the following steps after receiving a message and before publishing it to BizTalk Server:</span></span>  
  
1.  <span data-ttu-id="0840c-111">配接器會模擬寄件者，並取得 SSO 票證代表寄件者使用 **ISSOTicket.IssueTicket** API。</span><span class="sxs-lookup"><span data-stu-id="0840c-111">The adapter impersonates the sender and obtains the SSO ticket on behalf of the sender by using the **ISSOTicket.IssueTicket** API.</span></span>  
  
2.  <span data-ttu-id="0840c-112">在成功取得 SSO 票證後，配接器便會將其儲存在系統命名空間下的訊息內容屬性 SSOTicket 中。</span><span class="sxs-lookup"><span data-stu-id="0840c-112">After successfully obtaining an SSO ticket the adapter stores it on the message context property “SSOTicket” under the system namespace.</span></span>  
  
 <span data-ttu-id="0840c-113">下列程式碼片段將示範如何取得票證，以及如何將其儲存在訊息內容中。</span><span class="sxs-lookup"><span data-stu-id="0840c-113">The following code fragment demonstrates how the ticket is obtained and how it is stored on the message context.</span></span>  
  
```  
public class MyAdapter : IBTTransport,   
                         IBTTransportConfig,   
                         IBTTransportControl,  
                         IPersistPropertyBag,   
                         IBaseComponent  
{  
...  
     private string m_SSOToken = null;  
  
 // Get a ticket for the sender  
     private void GetSSOTicket(IntPtr token)  
     {  
       bool impersonated = false;  
      WindowsImpersonationContext wic = null;  
  
 if (token != (IntPtr)0)   
 {  
     try   
 {  
         // Impersonate the user using his security  
 // token  
            WindowsIdentity wi =   
 new WindowsIdentity(token);  
            wic = wi.Impersonate();  
            impersonated = true;  
  
         // Get an SSO ticket for the impersonated  
 // user  
            ISSOTicket ssoTicket = new ISSOTicket();  
            m_SSOToken = ssoTicket.IssueTicket(0);  
         }  
         finally   
 {  
           if (impersonated)  
            // Revert the impersonation  
            wic.Undo();  
          }  
}  
}  
...  
  
     private void WriteSSOTicketToContext(  
 IBaseMessage message )  
     {  
         if (m_SSOTicket != null)   
 {  
 // Write the SSO ticket to the message context  
          message.Context.Write(  
 “SSOTicket”,  
 http://schemas.microsoft.com/BizTalk/2003/system-properties,   
 m_SSOToken);  
        }  
      }  
}  
```  
  
## <a name="party-resolution"></a><span data-ttu-id="0840c-114">合作對象解析</span><span class="sxs-lookup"><span data-stu-id="0840c-114">Party Resolution</span></span>  
 <span data-ttu-id="0840c-115">合作對象解析管線元件負責將傳送者憑證或傳送者安全性識別碼 (SID) 對應至所對應的已設定 BizTalk Server 合作對象。</span><span class="sxs-lookup"><span data-stu-id="0840c-115">The Party Resolution pipeline component is responsible for mapping the sender certificate or the sender security identifier (SID) to the corresponding configured BizTalk Server party.</span></span> <span data-ttu-id="0840c-116">這項資訊提供給他們的介面卡應該設定兩個系統訊息內容屬性 **WindowsUser** 和 **SignatureCertificate**, ，而如果設定，可供下游合作對象解析元件。</span><span class="sxs-lookup"><span data-stu-id="0840c-116">Adapters that have this information available to them should set the two system message context properties, **WindowsUser** and **SignatureCertificate**, to be consumed by the downstream party resolution component if configured.</span></span>  
  
 <span data-ttu-id="0840c-117">**WindowsUser** 屬性填入傳送者，例如 redmond\myBtsUser 的網域使用者。</span><span class="sxs-lookup"><span data-stu-id="0840c-117">The **WindowsUser** property is populated with the domain user of the sender, for example redmond\myBtsUser.</span></span> <span data-ttu-id="0840c-118">**SignatureCertificate** 屬性填入用戶端驗證憑證的指紋。</span><span class="sxs-lookup"><span data-stu-id="0840c-118">The **SignatureCertificate** property is populated with the thumbprint of the client authentication certificate.</span></span>  
  
## <a name="managing-passwords"></a><span data-ttu-id="0840c-119">管理密碼</span><span class="sxs-lookup"><span data-stu-id="0840c-119">Managing Passwords</span></span>  
 <span data-ttu-id="0840c-120">如果您將認證直接放在端點的屬性中，當您需要匯出繫結檔案時，密碼欄位就會變成空白。</span><span class="sxs-lookup"><span data-stu-id="0840c-120">If you put credentials directly in the properties of an endpoint, the password field will be blanked out when you need to export a binding file.</span></span> <span data-ttu-id="0840c-121">這樣您的使用者就需要重新輸入系統管理員的密碼。</span><span class="sxs-lookup"><span data-stu-id="0840c-121">This will require your user to re-enter the password as an administrator.</span></span> <span data-ttu-id="0840c-122">您可以對認證使用 SSO 以避免這種困難狀況。</span><span class="sxs-lookup"><span data-stu-id="0840c-122">You can avoid this difficulty by using SSO for credentials.</span></span>  
  
 <span data-ttu-id="0840c-123">如果配接器端點具有 **密碼** 屬性，請注意，實際值會儲存在 SSO 設定存放區資料庫中的純文字。</span><span class="sxs-lookup"><span data-stu-id="0840c-123">If the adapter endpoint has a **Password** property, be aware that the actual value is stored in clear text in the SSO Configure Store database.</span></span> <span data-ttu-id="0840c-124">即使在使用者介面中顯示為 "\*"，依然會是如此。</span><span class="sxs-lookup"><span data-stu-id="0840c-124">This is despite the fact that it is displayed in the user interface as "\*".</span></span> <span data-ttu-id="0840c-125">這個屬性也可透過網路傳輸，而且使用 BizTalk Server 範例 ExplorerOM 的簡單指令碼即可加以讀取。</span><span class="sxs-lookup"><span data-stu-id="0840c-125">This property is also transferred through the network and a simple script using the BizTalk Server sample ExplorerOM will be able to read it.</span></span>