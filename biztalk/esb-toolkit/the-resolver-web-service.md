---
title: "解析程式的 Web 服務 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 236cff15-562a-41d5-bfdc-d250186fb616
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 916181431686ca729c0751d9362570afb7dddeee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolver-web-service"></a><span data-ttu-id="02e69-102">解析程式的 Web 服務</span><span class="sxs-lookup"><span data-stu-id="02e69-102">The Resolver Web Service</span></span>
<span data-ttu-id="02e69-103">解析程式 Web 服務是一個閘道到 ESB 動態解析機制。</span><span class="sxs-lookup"><span data-stu-id="02e69-103">The Resolver Web service is a gateway into the ESB dynamic resolution mechanism.</span></span> [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]<span data-ttu-id="02e69-104">包含此服務的兩個版本： ASP.NET (ASMX) 版本和 Windows Communication Foundation (WCF) 版本。</span><span class="sxs-lookup"><span data-stu-id="02e69-104"> includes two versions of this service: an ASP.NET (ASMX) version and a Windows Communication Foundation (WCF) version.</span></span> <span data-ttu-id="02e69-105">服務名稱就是**ESB。ResolverServices**和**ESB。ResolverServices.WCF**分別和服務會公開下列方法：</span><span class="sxs-lookup"><span data-stu-id="02e69-105">The service names are **ESB.ResolverServices** and **ESB.ResolverServices.WCF**, respectively, and the services expose the following methods:</span></span>  
  
-   <span data-ttu-id="02e69-106">**解決。**</span><span class="sxs-lookup"><span data-stu-id="02e69-106">**Resolve.**</span></span> <span data-ttu-id="02e69-107">這個方法會採用做為其單一參數**字串**，其中包含解析程式的連接字串，針對要求符合標準的連接字串的已註冊的解析程式例如**靜態、 BRE、 UDDI，XPATH、 路線、 路線靜態、 BRI，**或**LDAP。**</span><span class="sxs-lookup"><span data-stu-id="02e69-107">This method takes as its single parameter a **String** that contains the resolver connection string for the request, which conforms to the standard connection strings for registered resolvers such as **STATIC, BRE, UDDI, XPATH, ITINERARY, ITINERARY-STATIC, BRI,** or **LDAP.**</span></span>  
  
-   <span data-ttu-id="02e69-108">**ResolveMessage。**</span><span class="sxs-lookup"><span data-stu-id="02e69-108">**ResolveMessage.**</span></span> <span data-ttu-id="02e69-109">這個方法會採用做為其第一個參數包含要求中，符合標準的連接字串的已註冊的解析程式這類的解析程式連接字串的字串**靜態、 BRE、 UDDI、 XPATH、 路線，行程靜態、 BRI，**或**LDAP**。</span><span class="sxs-lookup"><span data-stu-id="02e69-109">This method takes as its first parameter a String that contains the resolver connection string for the request, which conforms to the standard connection strings for registered resolvers such as  **STATIC, BRE, UDDI, XPATH, ITINERARY, ITINERARY-STATIC, BRI,** or **LDAP**.</span></span> <span data-ttu-id="02e69-110">此外，該方法會接受選擇性的第二個參數，做為**字串**包含服務可以使用做為選擇性的事實，以協助解決的 XML 訊息文件; 例如，BRE 解析程式可能需要訊息本文封裝事實。</span><span class="sxs-lookup"><span data-stu-id="02e69-110">In addition, the method accepts an optional second parameter as a **String** that contains an XML message document that the service can use as optional facts to assist in a resolution; for example, the BRE resolver may require a message body that encapsulates facts.</span></span>  
  
 <span data-ttu-id="02e69-111">如需解析器和 ResolverDictionary 類別和其使用方式的詳細資訊，請參閱[使用協助程式類別](../esb-toolkit/using-the-helper-classes.md)。</span><span class="sxs-lookup"><span data-stu-id="02e69-111">For more information about the Resolver and ResolverDictionary classes and their usage, see [Using the Helper Classes](../esb-toolkit/using-the-helper-classes.md).</span></span>  
  
## <a name="resolver-connection-strings"></a><span data-ttu-id="02e69-112">解析程式的連接字串</span><span class="sxs-lookup"><span data-stu-id="02e69-112">Resolver Connection Strings</span></span>  
 <span data-ttu-id="02e69-113">ESB 動態解析機制會使用連接字串，加上表示的解析度來執行類型的 moniker。</span><span class="sxs-lookup"><span data-stu-id="02e69-113">The ESB dynamic resolution mechanism uses a connection string preceded by a moniker that indicates the type of resolution to perform.</span></span> <span data-ttu-id="02e69-114">包含支援的 moniker**靜態、 BRE、 UDDI、 UDDI3、 XPATH、 路線、 路線靜態、 BRI，**和**LDAP**。</span><span class="sxs-lookup"><span data-stu-id="02e69-114">The supported monikers include **STATIC, BRE, UDDI, UDDI3, XPATH, ITINERARY, ITINERARY-STATIC, BRI,** and **LDAP**.</span></span> <span data-ttu-id="02e69-115">下列連接字串示範**UDDI** moniker:</span><span class="sxs-lookup"><span data-stu-id="02e69-115">The following connection string shows an example of a **UDDI** moniker:</span></span>  
  
```  
  
//UDDI  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=PurchaseOrder;serviceProvider=Microsoft.Practices.ESB  
```  
  
 <span data-ttu-id="02e69-116">如需支援的動態解析機制的連接字串的類型資訊，請參閱[使用動態解析和路由](../esb-toolkit/using-dynamic-resolution-and-routing.md)。</span><span class="sxs-lookup"><span data-stu-id="02e69-116">For information about the types of connections strings supported by the dynamic resolution mechanism, see [Using Dynamic Resolution and Routing](../esb-toolkit/using-dynamic-resolution-and-routing.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02e69-117">您必須設定此服務使用 Windows 整合式安全性，以及內建網路服務帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="02e69-117">You must configure this service to use either Windows Integrated Security and to run under the built-in NETWORK SERVICE account.</span></span>  
>   
>  <span data-ttu-id="02e69-118">根據預設，解析程式的 Web 服務不會設定為需要安全通訊端層 (SSL) 用戶端存取時。</span><span class="sxs-lookup"><span data-stu-id="02e69-118">By default, the Resolver Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients.</span></span> <span data-ttu-id="02e69-119">您應該設定服務，讓需要 SSL 用戶端存取，並保護網際網路資訊服務 (IIS) Web 服務主機電腦與您使用網路層級 IPSec 和適當的檔案層級存取權的 BizTalk Server 之間的連線控制清單 (ACL) 權限。</span><span class="sxs-lookup"><span data-stu-id="02e69-119">You should configure the service so that it requires SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and your BizTalk Server using network-level IPSec and appropriate file-level access control list (ACL) permissions.</span></span> <span data-ttu-id="02e69-120">若要避免安全性風險，不建議以公開此服務的受信任的子系統界限之外。</span><span class="sxs-lookup"><span data-stu-id="02e69-120">To avoid security risks, it is not recommended to expose this service outside the boundary of the trusted subsystem.</span></span>