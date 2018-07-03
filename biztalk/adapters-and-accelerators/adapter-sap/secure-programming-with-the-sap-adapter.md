---
title: SAP 配接器使用的安全程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, considerations when programming on the adapter
- security, secure data exchange
- security, setting credentials in code
ms.assetid: bd5da271-90f1-4a64-9138-a51048a16648
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a7fbdd561c739e6312ca1300bc9b886afdee5376
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37015703"
---
# <a name="secure-programming-with-the-sap-adapter"></a><span data-ttu-id="b2b63-102">安全使用 SAP 配接器進行程式設計</span><span class="sxs-lookup"><span data-stu-id="b2b63-102">Secure programming with the SAP adapter</span></span>
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a><span data-ttu-id="b2b63-103">如何保護認證當我使用 新增配接器服務參考 Visual Studio 外掛程式？</span><span class="sxs-lookup"><span data-stu-id="b2b63-103">How Do I Protect Credentials When I Use the Add Adapter Service Reference Visual Studio Plug-in?</span></span>  
 <span data-ttu-id="b2b63-104">當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]若要建立的 WCF 用戶端，您必須提供使用者名稱和 SAP 系統的密碼。</span><span class="sxs-lookup"><span data-stu-id="b2b63-104">When you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF client, you must supply a user name and password for the SAP system.</span></span> <span data-ttu-id="b2b63-105">您應該只做這**安全性**索引標籤上**設定配接器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="b2b63-105">You should only do this from the **Security** tab on the **Configure Adapter** dialog box.</span></span> <span data-ttu-id="b2b63-106">輸入 SAP 認證從**安全性**按下 tab 鍵而不是直接**Uri**  欄位中，確認下列：</span><span class="sxs-lookup"><span data-stu-id="b2b63-106">By entering the SAP credentials from the **Security** tab instead of directly into the **Uri** field, you ensure the following:</span></span>  
  
- <span data-ttu-id="b2b63-107">認證不會顯示在**Uri**欄位[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]對話方塊，其中以您的電腦螢幕的存取權的任何人都可以讀取它們。</span><span class="sxs-lookup"><span data-stu-id="b2b63-107">The credentials will not be displayed in the **Uri** field of the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] dialog box where anyone with access to your computer screen can read them.</span></span>  
  
- <span data-ttu-id="b2b63-108">認證不會出現在組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。</span><span class="sxs-lookup"><span data-stu-id="b2b63-108">The credentials will not appear in the configuration file that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
  <span data-ttu-id="b2b63-109">如需有關如何使用來產生 WCF 用戶端[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，包括如何輸入 SAP 系統的使用者名稱和密碼，請參閱[取得 SAP 作業，在 Visual Studio 中的中繼資料](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)</span><span class="sxs-lookup"><span data-stu-id="b2b63-109">For more information about how to generate a WCF client by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], including how to enter a user name and password for the SAP system, see [Get Metadata for SAP Operations in Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)</span></span>  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a><span data-ttu-id="b2b63-110">在程式碼中的 設定認證的最佳作法有哪些？</span><span class="sxs-lookup"><span data-stu-id="b2b63-110">What Are Best Practices for Setting Credentials in Code?</span></span>  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]<span data-ttu-id="b2b63-111"> 提供**ClientCredentials**類別，以協助您設定用戶端通訊物件，例如認證**ChannelFactory**，用來向服務驗證本身。</span><span class="sxs-lookup"><span data-stu-id="b2b63-111"> provides the **ClientCredentials** class to help you configure the credentials that a client communication object, such as a **ChannelFactory**, uses to authenticate itself with a service.</span></span> <span data-ttu-id="b2b63-112">藉由使用**ClientCredentials**類別，您確定 WCF 會在該物件的通道堆疊中指定任何的驗證機制，並將它們套用到您的用戶端與服務之間的交換。</span><span class="sxs-lookup"><span data-stu-id="b2b63-112">By using the **ClientCredentials** class, you ensure that WCF takes whatever authentication mechanisms are specified in that object’s channel stack and applies them to the exchange between your client and the service.</span></span>  
  
 <span data-ttu-id="b2b63-113">因為[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]裝載同處理序與其使用的應用程式，不一定需要使用**ClientCredentials**類別來設定認證，用戶端上使用應用程式所使用的通訊物件。</span><span class="sxs-lookup"><span data-stu-id="b2b63-113">Because the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is hosted in-process with its consuming application, it is not imperative to use the **ClientCredentials** class to set credentials on the client communication objects that the consuming application uses.</span></span> <span data-ttu-id="b2b63-114">它是，不過，最佳做法進行此作業。</span><span class="sxs-lookup"><span data-stu-id="b2b63-114">It is, however, considered good practice to do so.</span></span>  
  
 <span data-ttu-id="b2b63-115">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]建議您使用**ClientCredentials**類別透過**AcceptCredentialsInUri**繫結屬性。</span><span class="sxs-lookup"><span data-stu-id="b2b63-115">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] encourages the use of the **ClientCredentials** class through the **AcceptCredentialsInUri** binding property.</span></span> <span data-ttu-id="b2b63-116">此屬性指定配接器是否將接受的使用者名稱和密碼連線 URI 中的 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="b2b63-116">This property specifies whether the adapter will accept the user name and password for the SAP system in the connection URI.</span></span> <span data-ttu-id="b2b63-117">**AcceptCredentialsInUri**預設為**false**，這表示，配接器會擲回例外狀況的連線 URI 包含認證。</span><span class="sxs-lookup"><span data-stu-id="b2b63-117">**AcceptCredentialsInUri** defaults to **false**, which means that the adapter will throw an exception if the connection URI contains credentials.</span></span> <span data-ttu-id="b2b63-118">您可以設定**AcceptCredentialsInUri**要 **，則為 true**提供連線 URI 中的認證。</span><span class="sxs-lookup"><span data-stu-id="b2b63-118">You can set **AcceptCredentialsInUri** to **true** to supply credentials in the connection URI.</span></span> <span data-ttu-id="b2b63-119">事實上，您必須這麼做在某些情況下，例如，當您指定連線 URI 或服務主機端點**IReplyChannel**輸入案例中。</span><span class="sxs-lookup"><span data-stu-id="b2b63-119">In fact, you must do this in certain cases; for example, when you specify a connection URI for a service host endpoint or for an **IReplyChannel** in inbound scenarios.</span></span>  
  
 <span data-ttu-id="b2b63-120">下列範例示範如何使用**ClientCredentials**類別來設定 WCF 用戶端上的 SAP 系統的認證。</span><span class="sxs-lookup"><span data-stu-id="b2b63-120">The following example shows how to use the **ClientCredentials** class to set credentials for the SAP system on a WCF client.</span></span>  
  
```  
SAPBinding binding = new SAPBinding();  
  
// Set endpoint address  
EndpointAddress endpointAddress = new EndpointAddress("sap://CLIENT=800;LANG=EN;@a/YourSAPHost/00?RfcSdkTrace=False&AbapDebug=False&UseSapGui=Without");  
  
// Create client and set credentials  
RfcClient rfcClient = new RfcClient(binding, endpointAddress);  
rfcClient.ClientCredentials.UserName.UserName = "YourUserName";  
rfcClient.ClientCredentials.UserName.Password = "YourPassword";  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a><span data-ttu-id="b2b63-121">如何跨處理序界限提供更安全的資料交換？</span><span class="sxs-lookup"><span data-stu-id="b2b63-121">How Can I Provide for More Secure Data Exchange Across Process Boundaries?</span></span>  
 <span data-ttu-id="b2b63-122">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]裝載同處理序的應用程式或取用它的服務。</span><span class="sxs-lookup"><span data-stu-id="b2b63-122">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] is hosted in-process with the application or service that consumes it.</span></span> <span data-ttu-id="b2b63-123">因為配接器裝載同處理序與取用者，就不需要在取用者之間交換的訊息提供安全性和[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b2b63-123">Because the adapter is hosted in-process with the consumer, there is no need to provide security on messages exchanged between the consumer and the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span> <span data-ttu-id="b2b63-124">不過，如果使用的應用程式或服務會傳送包含跨處理序界限，另一個服務或用戶端機密的資料庫資訊的訊息，您應該提供適當的保護，這項資料在您的環境中的量值。</span><span class="sxs-lookup"><span data-stu-id="b2b63-124">However, if the consuming application or service sends messages that contain sensitive database information across a process boundary to another service or client, you should take measures to provide adequate protection for this data in your environment.</span></span> [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]<span data-ttu-id="b2b63-125"> 提供許多選項來協助保護用戶端與服務之間傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="b2b63-125"> provides many options for helping to secure messages sent between clients and services.</span></span> <span data-ttu-id="b2b63-126">如需有關協助保護用戶端與服務之間傳送的訊息[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，請參閱 < [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b2b63-126">For more information about helping to secure messages sent between clients and services in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], see [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx).</span></span> <span data-ttu-id="b2b63-127">如需一般資訊的安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱 < [Windows Communication Foundation 安全性](https://msdn.microsoft.com/library/ms732362.aspx)。</span><span class="sxs-lookup"><span data-stu-id="b2b63-127">For more general information about security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b63-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2b63-128">See Also</span></span>  
[<span data-ttu-id="b2b63-129">最佳作法來保護 SAP 配接器</span><span class="sxs-lookup"><span data-stu-id="b2b63-129">Best practices to secure the SAP adapter</span></span>](../../adapters-and-accelerators/adapter-sap/best-practices-to-secure-the-sap-adapter.md)  
[<span data-ttu-id="b2b63-130">保護您的 SAP 應用程式</span><span class="sxs-lookup"><span data-stu-id="b2b63-130">Secure your SAP applications</span></span>](../../adapters-and-accelerators/adapter-sap/secure-your-sap-applications.md)   