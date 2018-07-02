---
title: 安全使用 Oracle EBS 配接器進行程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 35b494f8-cb21-45c2-9bb4-097ba59ec52c
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eae7e2c1be56a886578f7bba83901f218c42b94e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36972175"
---
# <a name="secure-programming-with-the-oracle-ebs-adapter"></a><span data-ttu-id="9d77b-102">安全使用 Oracle EBS 配接器進行程式設計</span><span class="sxs-lookup"><span data-stu-id="9d77b-102">Secure programming with the Oracle EBS adapter</span></span>
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a><span data-ttu-id="9d77b-103">如何保護認證當我使用 新增配接器服務參考 Visual Studio 外掛程式？</span><span class="sxs-lookup"><span data-stu-id="9d77b-103">How Do I Protect Credentials When I Use the Add Adapter Service Reference Visual Studio Plug-in?</span></span>  
 <span data-ttu-id="9d77b-104">當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]若要建立的 WCF 用戶端，您必須提供使用者名稱和密碼 for Oracle E-business Suite。</span><span class="sxs-lookup"><span data-stu-id="9d77b-104">When you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF client, you must supply a user name and password for the Oracle E-Business Suite.</span></span> <span data-ttu-id="9d77b-105">您應該只做這**安全性**索引標籤上**設定配接器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9d77b-105">You should only do this from the **Security** tab on the **Configure Adapter** dialog box.</span></span> <span data-ttu-id="9d77b-106">輸入 Oracle 認證從**安全性**按下 tab 鍵而不是直接**設定 URI**  欄位中，確認下列：</span><span class="sxs-lookup"><span data-stu-id="9d77b-106">By entering the Oracle credentials from the **Security** tab instead of directly into the **Configure a URI** field, you ensure the following:</span></span>  
  
- <span data-ttu-id="9d77b-107">認證不會顯示在**設定 URI**欄位[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]對話方塊，其中以您的電腦螢幕的存取權的任何人都可以讀取它們。</span><span class="sxs-lookup"><span data-stu-id="9d77b-107">The credentials will not be displayed in the **Configure a URI** field of the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] dialog box where anyone with access to your computer screen can read them.</span></span>  
  
- <span data-ttu-id="9d77b-108">認證不會出現在組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。</span><span class="sxs-lookup"><span data-stu-id="9d77b-108">The credentials will not appear in the configuration file that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
  <span data-ttu-id="9d77b-109">如需有關如何使用來產生 WCF 用戶端[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，包括如何 for Oracle E-business Suite 中輸入使用者名稱和密碼，請參閱[取得 Visual Studio中的OracleE-businessSuite作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="9d77b-109">For more information about how to generate a WCF client by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], including how to enter a user name and password for the Oracle E-Business Suite, see [Get metadata for Oracle E-Business Suite operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md).</span></span>  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a><span data-ttu-id="9d77b-110">在程式碼中的 設定認證的最佳作法有哪些？</span><span class="sxs-lookup"><span data-stu-id="9d77b-110">What Are Best Practices for Setting Credentials in Code?</span></span>  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]<span data-ttu-id="9d77b-111"> 提供**ClientCredentials**類別，以協助您設定用戶端通訊物件，例如認證**ChannelFactory**，用來向服務驗證本身。</span><span class="sxs-lookup"><span data-stu-id="9d77b-111"> provides the **ClientCredentials** class to help you configure the credentials that a client communication object, such as a **ChannelFactory**, uses to authenticate itself with a service.</span></span> <span data-ttu-id="9d77b-112">藉由使用**ClientCredentials**類別，您確定 WCF 會在該物件的通道堆疊中指定任何的驗證機制，並將它們套用到您的用戶端與服務之間的交換。</span><span class="sxs-lookup"><span data-stu-id="9d77b-112">By using the **ClientCredentials** class, you ensure that WCF takes whatever authentication mechanisms are specified in that object’s channel stack and applies them to the exchange between your client and the service.</span></span>  
  
 <span data-ttu-id="9d77b-113">因為[!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)]裝載同處理序與其使用的應用程式，不一定需要使用**ClientCredentials**類別來設定認證，用戶端上使用應用程式所使用的通訊物件。</span><span class="sxs-lookup"><span data-stu-id="9d77b-113">Because the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] is hosted in-process with its consuming application, it is not imperative to use the **ClientCredentials** class to set credentials on the client communication objects that the consuming application uses.</span></span> <span data-ttu-id="9d77b-114">它是，不過，最佳做法進行此作業。</span><span class="sxs-lookup"><span data-stu-id="9d77b-114">It is, however, considered good practice to do so.</span></span>  
  
 <span data-ttu-id="9d77b-115">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]建議您使用**ClientCredentials**類別。</span><span class="sxs-lookup"><span data-stu-id="9d77b-115">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] encourages the use of the **ClientCredentials** class.</span></span> <span data-ttu-id="9d77b-116">此屬性會指定是否接受使用者名稱和密碼連線 URI 中的 Oracle 資料庫配接器。</span><span class="sxs-lookup"><span data-stu-id="9d77b-116">This property specifies whether the adapter will accept the user name and password for the Oracle database in the connection URI.</span></span> <span data-ttu-id="9d77b-117">**AcceptCredentialsInUri**預設為**false**，這表示，配接器會擲回例外狀況的連線 URI 包含認證。</span><span class="sxs-lookup"><span data-stu-id="9d77b-117">**AcceptCredentialsInUri** defaults to **false**, which means that the adapter will throw an exception if the connection URI contains credentials.</span></span> <span data-ttu-id="9d77b-118">您可以設定**AcceptCredentialsInUri**要 **，則為 true**提供認證，在 連線 URI，視需要在用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d77b-118">You can set **AcceptCredentialsInUri** to **true** to supply credentials in the connection URI, if required in the client application.</span></span>  
  
 <span data-ttu-id="9d77b-119">下列範例示範如何使用**認證**屬性來設定認證 for Oracle E-business Suite **ChannelFactory**。</span><span class="sxs-lookup"><span data-stu-id="9d77b-119">The following example shows how to use the **Credentials** property to set credentials for the Oracle E-Business Suite on a **ChannelFactory**.</span></span>  
  
```  
// Create binding and endpoint  
OracleEBSBinding binding = new OracleEBSBinding();  
EndpointAddress address = new EndpointAddress("oracleebs://ebs-instance");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open the channel factory  
factory.Open();  
```  
  
 <span data-ttu-id="9d77b-120">下列範例示範如何使用**ClientCredentials** for Oracle E-business Suite 設定 WCF 用戶端認證類別。</span><span class="sxs-lookup"><span data-stu-id="9d77b-120">The following example shows how to use the **ClientCredentials** class to set credentials for the Oracle E-Business Suite on a WCF client.</span></span>  
  
```  
// Initialize a new client for the SQLEXECUTE operation from configuration   
ConcurrentPrograms_ARClient client =   
  new ConcurrentPrograms_ARClient("OracleEBSBinding_ConcurrentPrograms_AR");  
  
// Set user name and password  
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
// Open the client  
client.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a><span data-ttu-id="9d77b-121">如何跨處理序界限提供更安全的資料交換？</span><span class="sxs-lookup"><span data-stu-id="9d77b-121">How Can I Provide for More Secure Data Exchange Across Process Boundaries?</span></span>  
 <span data-ttu-id="9d77b-122">[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]裝載同處理序的應用程式或取用它的服務。</span><span class="sxs-lookup"><span data-stu-id="9d77b-122">The [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] is hosted in-process with the application or service that consumes it.</span></span> <span data-ttu-id="9d77b-123">因為配接器裝載同處理序與取用者，就不需要在取用者之間交換的訊息提供安全性和[!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9d77b-123">Because the adapter is hosted in-process with the consumer, there is no need to provide security on messages exchanged between the consumer and the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="9d77b-124">不過，如果使用的應用程式或服務會傳送包含跨處理序界限，另一個服務或用戶端機密的資料庫資訊的訊息，您應該提供適當的保護，這項資料在您的環境中的量值。</span><span class="sxs-lookup"><span data-stu-id="9d77b-124">However, if the consuming application or service sends messages that contain sensitive database information across a process boundary to another service or client, you should take measures to provide adequate protection for this data in your environment.</span></span> [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]<span data-ttu-id="9d77b-125"> 提供許多選項來協助保護用戶端與服務之間傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="9d77b-125"> provides many options for helping to secure messages sent between clients and services.</span></span> <span data-ttu-id="9d77b-126">如需有關協助保護用戶端與服務之間傳送的訊息[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，請參閱 「 保護服務和用戶端 」，網址[ http://go.microsoft.com/fwlink/?LinkId=89725 ](http://go.microsoft.com/fwlink/?LinkId=89725)。</span><span class="sxs-lookup"><span data-stu-id="9d77b-126">For more information about helping to secure messages sent between clients and services in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], see "Securing Services and Clients" at [http://go.microsoft.com/fwlink/?LinkId=89725](http://go.microsoft.com/fwlink/?LinkId=89725).</span></span> <span data-ttu-id="9d77b-127">如需一般資訊的安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱 < Windows Communication Foundation 安全性 >，網址[ http://go.microsoft.com/fwlink/?LinkId=89726 ](http://go.microsoft.com/fwlink/?LinkId=89726)。</span><span class="sxs-lookup"><span data-stu-id="9d77b-127">For more general information about security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see "Windows Communication Foundation Security" at [http://go.microsoft.com/fwlink/?LinkId=89726](http://go.microsoft.com/fwlink/?LinkId=89726).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d77b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d77b-128">See Also</span></span>  
 [<span data-ttu-id="9d77b-129">保護您的 Oracle EBS 應用程式</span><span class="sxs-lookup"><span data-stu-id="9d77b-129">Secure your Oracle EBS applications</span></span>](secure-your-oracle-ebs-applications.md)