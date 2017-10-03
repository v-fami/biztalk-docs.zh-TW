---
title: "使用 SQL 配接器的安全程式設計 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c84744a-6595-4d93-afe7-39a7ccf1b6a0
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 44886b490ce63e8c34e1a5bdb41554c96a0873ad
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="secure-programming-with-the-sql-adapter"></a><span data-ttu-id="c125f-102">保護使用 SQL 配接器進行程式設計</span><span class="sxs-lookup"><span data-stu-id="c125f-102">Secure programming with the SQL adapter</span></span>
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a><span data-ttu-id="c125f-103">如何執行保護認證時使用新增配接器服務參考 Visual Studio 外掛程式？</span><span class="sxs-lookup"><span data-stu-id="c125f-103">How Do I Protect Credentials When I Use the Add Adapter Service Reference Visual Studio Plug-in?</span></span>  
 <span data-ttu-id="c125f-104">當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]建立 WCF 用戶端，您可能必須提供使用者名稱和密碼的 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c125f-104">When you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF client, you might have to supply a user name and password for the SQL Server database.</span></span> <span data-ttu-id="c125f-105">您必須輸入認證，從**安全性**索引標籤上**設定配接器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c125f-105">You must enter credentials from the **Security** tab on the **Configure Adapter** dialog box.</span></span> <span data-ttu-id="c125f-106">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]不提供選項，指定連線 URI 的一部分的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="c125f-106">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not provide an option to specify the user name and password as part of the connection URI.</span></span> <span data-ttu-id="c125f-107">這可確保：</span><span class="sxs-lookup"><span data-stu-id="c125f-107">This ensures the following:</span></span>  
  
-   <span data-ttu-id="c125f-108">認證不會顯示在**設定 URI**欄位**加入配接器服務參考外掛程式**對話方塊可以存取您的電腦螢幕的任何人員讀取。</span><span class="sxs-lookup"><span data-stu-id="c125f-108">The credentials will not be displayed in the **Configure a URI** field of the **Add Adapter Service Reference Plug-in** dialog box where anyone with access to your computer screen can read them.</span></span>  
  
-   <span data-ttu-id="c125f-109">認證不會出現在組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。</span><span class="sxs-lookup"><span data-stu-id="c125f-109">The credentials will not appear in the configuration file that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
 <span data-ttu-id="c125f-110">如需有關如何產生 WCF 用戶端使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，包括如何輸入 SQL Server 資料庫的使用者名稱和密碼，請參閱[取得中繼資料的 SQL Server 作業，在 Visual Studio 中使用 SQL 配接器](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).</span><span class="sxs-lookup"><span data-stu-id="c125f-110">For more information about how to generate a WCF client by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], including how to enter a user name and password for the SQL Server database, see [Get metadata for SQL Server operations in Visual Studio using the SQL adapter](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).</span></span>  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a><span data-ttu-id="c125f-111">在程式碼中設定憑證的最佳做法為何？</span><span class="sxs-lookup"><span data-stu-id="c125f-111">What Are Best Practices for Setting Credentials in Code?</span></span>  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]<span data-ttu-id="c125f-112">提供**ClientCredentials**類別，以協助您設定的認證，用戶端通訊物件，例如**ChannelFactory**，用來向服務驗證本身。</span><span class="sxs-lookup"><span data-stu-id="c125f-112"> provides the **ClientCredentials** class to help you configure the credentials that a client communication object, such as a **ChannelFactory**, uses to authenticate itself with a service.</span></span> <span data-ttu-id="c125f-113">使用**ClientCredentials**類別，您確定 WCF 會採用物件的通道堆疊中指定任何驗證機制，並將其套用至您的用戶端和服務之間的交換。</span><span class="sxs-lookup"><span data-stu-id="c125f-113">By using the **ClientCredentials** class, you ensure that WCF takes whatever authentication mechanisms are specified in that object’s channel stack and applies them to the exchange between your client and the service.</span></span>  
  
 <span data-ttu-id="c125f-114">因為[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]裝載內含式與它使用的應用程式，不一定要使用**ClientCredentials**類別來設定認證，用戶端上使用應用程式所使用的通訊物件。</span><span class="sxs-lookup"><span data-stu-id="c125f-114">Because the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is hosted in-process with its consuming application, it is not imperative to use the **ClientCredentials** class to set credentials on the client communication objects that the consuming application uses.</span></span> <span data-ttu-id="c125f-115">不過，並非很好的作法。</span><span class="sxs-lookup"><span data-stu-id="c125f-115">It is, however, considered good practice to do so.</span></span>  
  
 <span data-ttu-id="c125f-116">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]需要使用**ClientCredentials**類別以程式設計方式傳送認證。</span><span class="sxs-lookup"><span data-stu-id="c125f-116">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] requires the use of the **ClientCredentials** class for programmatically passing credentials.</span></span> <span data-ttu-id="c125f-117">**AcceptCredentialsInUri**繫結屬性就會忽略[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]以防止在 URI 中的傳遞認證。</span><span class="sxs-lookup"><span data-stu-id="c125f-117">The **AcceptCredentialsInUri** binding property is ignored by the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] to prevent passing credentials in the URI.</span></span>  
  
 <span data-ttu-id="c125f-118">下列範例示範如何使用**認證**屬性上設定 SQL Server 資料庫的認證**ChannelFactory**。</span><span class="sxs-lookup"><span data-stu-id="c125f-118">The following example shows how to use the **Credentials** property to set credentials for the SQL Server database on a **ChannelFactory**.</span></span>  
  
```  
// Create binding and endpoint  
SqlAdapterBinding binding = new SqlAdapterBinding();  
EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress))  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "myuser";  
factory.Credentials.UserName.Password = "mypassword";  
  
// Open the channel factory  
factory.Open();  
```  
  
 <span data-ttu-id="c125f-119">下列範例示範如何使用**ClientCredentials**類別來設定 WCF 用戶端上的 SQL Server 資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="c125f-119">The following example shows how to use the **ClientCredentials** class to set credentials for the SQL Server database on a WCF client.</span></span>  
  
```  
// Initialize a new client for the SELECT operation on the Employee table   
SqlAdapterBinding binding = new SqlAdapterBinding();  
EndpointAddress address = new EndpointAddress("mssql://mysqlserver//mydatabase?");  
TableOp_dbo_EmployeeClient client = new TableOp_dbo_EmployeeClient(binding,address);  
  
// Set user name and password  
client.ClientCredentials.UserName.UserName = "myuser";  
client.ClientCredentials.UserName.Password = "mypassword";  
  
// Open the client  
client.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a><span data-ttu-id="c125f-120">如何可提供更安全的資料交換的跨處理序界限？</span><span class="sxs-lookup"><span data-stu-id="c125f-120">How Can I Provide for More Secure Data Exchange Across Process Boundaries?</span></span>  
 <span data-ttu-id="c125f-121">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]裝載同處理序的應用程式或服務，則是使用它。</span><span class="sxs-lookup"><span data-stu-id="c125f-121">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] is hosted in-process with the application or service that consumes it.</span></span> <span data-ttu-id="c125f-122">因為配接器裝載同處理序的取用者，您就不必在取用者之間交換的訊息提供安全性和[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c125f-122">Because the adapter is hosted in-process with the consumer, there is no need to provide security on messages exchanged between the consumer and the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="c125f-123">不過，如果使用的應用程式或服務傳送包含跨處理序界限，另一個服務或用戶端機密的資料庫資訊的訊息，您應該採取措施，以提供適當的保護，此環境中的資料。</span><span class="sxs-lookup"><span data-stu-id="c125f-123">However, if the consuming application or service sends messages that contain sensitive database information across a process boundary to another service or client, you should take measures to provide adequate protection for this data in your environment.</span></span> [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]<span data-ttu-id="c125f-124">提供許多選項協助保護用戶端與服務之間傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="c125f-124"> provides many options for helping to secure messages sent between clients and services.</span></span> <span data-ttu-id="c125f-125">如需有關協助保護用戶端與服務之間傳送的訊息[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，請參閱[保護服務和用戶端](https://msdn.microsoft.com/library/ms734736.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c125f-125">For more information about helping to secure messages sent between clients and services in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], see [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx).</span></span> <span data-ttu-id="c125f-126">如需一般資訊的安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱[Windows Communication Foundation 安全性](https://msdn.microsoft.com/library/ms732362.aspx)。</span><span class="sxs-lookup"><span data-stu-id="c125f-126">For more general information about security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c125f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c125f-127">See Also</span></span>  
[<span data-ttu-id="c125f-128">保護 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="c125f-128">Secure your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/secure-your-sql-applications.md)  
[<span data-ttu-id="c125f-129">若要保護的 SQL 配接器的最佳作法</span><span class="sxs-lookup"><span data-stu-id="c125f-129">Best practices to secure the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)