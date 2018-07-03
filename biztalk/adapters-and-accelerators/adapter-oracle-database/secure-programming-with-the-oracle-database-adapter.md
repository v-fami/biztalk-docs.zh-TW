---
title: 安全使用 Oracle 資料庫配接器進行程式設計 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- credentials
- adapter, security considerations when programming on
- credentials, setting in code
- credentials, protecting
- security
ms.assetid: 06213c14-42b8-4d4a-b238-0aedbc27ab6a
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15860ad8a0e1f4417229da2a87c83b0a54ea0120
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008183"
---
# <a name="secure-programming-with-the-oracle-database-adapter"></a><span data-ttu-id="129b1-102">安全使用 Oracle 資料庫配接器進行程式設計</span><span class="sxs-lookup"><span data-stu-id="129b1-102">Secure programming with the Oracle Database adapter</span></span>
## <a name="how-do-i-protect-credentials-when-i-use-the-add-adapter-service-reference-visual-studio-plug-in"></a><span data-ttu-id="129b1-103">如何保護認證當我使用 新增配接器服務參考 Visual Studio 外掛程式？</span><span class="sxs-lookup"><span data-stu-id="129b1-103">How Do I Protect Credentials When I Use the Add Adapter Service Reference Visual Studio Plug-in?</span></span>  
 <span data-ttu-id="129b1-104">當您使用[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]若要建立的 WCF 用戶端，您必須提供使用者名稱和密碼的 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="129b1-104">When you use the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] to create a WCF client, you must supply a user name and password for the Oracle database.</span></span> <span data-ttu-id="129b1-105">您應該只做這**安全性**索引標籤上**設定配接器** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="129b1-105">You should only do this from the **Security** tab on the **Configure Adapter** dialog box.</span></span> <span data-ttu-id="129b1-106">輸入 Oracle 認證從**安全性**按下 tab 鍵而不是直接**設定 URI**  欄位中，確認下列：</span><span class="sxs-lookup"><span data-stu-id="129b1-106">By entering the Oracle credentials from the **Security** tab instead of directly into the **Configure a URI** field, you ensure the following:</span></span>  
  
- <span data-ttu-id="129b1-107">認證不會顯示在**Uri**欄位[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]對話方塊，其中以您的電腦螢幕的存取權的任何人都可以讀取它們。</span><span class="sxs-lookup"><span data-stu-id="129b1-107">The credentials will not be displayed in the **Uri** field of the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] dialog box where anyone with access to your computer screen can read them.</span></span>  
  
- <span data-ttu-id="129b1-108">認證不會出現在組態檔[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]產生。</span><span class="sxs-lookup"><span data-stu-id="129b1-108">The credentials will not appear in the configuration file that the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] generates.</span></span>  
  
  <span data-ttu-id="129b1-109">如需有關如何使用來產生 WCF 用戶端[!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)]，包括 Oracle 資料庫輸入使用者名稱和密碼，請參閱[取得 Visual Studio 中的 Oracle 資料庫作業的中繼資料](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="129b1-109">For more information about how to generate a WCF client by using the [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], including how to enter a user name and password for the Oracle database, see [Get metadata for Oracle Database operations in Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md).</span></span>  
  
## <a name="what-are-best-practices-for-setting-credentials-in-code"></a><span data-ttu-id="129b1-110">在程式碼中的 設定認證的最佳作法有哪些？</span><span class="sxs-lookup"><span data-stu-id="129b1-110">What Are Best Practices for Setting Credentials in Code?</span></span>  
 [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]<span data-ttu-id="129b1-111"> 提供**ClientCredentials**類別，以協助您設定用戶端通訊物件，例如認證**ChannelFactory**，用來向服務驗證本身。</span><span class="sxs-lookup"><span data-stu-id="129b1-111"> provides the **ClientCredentials** class to help you configure the credentials that a client communication object, such as a **ChannelFactory**, uses to authenticate itself with a service.</span></span> <span data-ttu-id="129b1-112">藉由使用**ClientCredentials**類別，您確定 WCF 會在該物件的通道堆疊中指定任何的驗證機制，並將它們套用到您的用戶端與服務之間的交換。</span><span class="sxs-lookup"><span data-stu-id="129b1-112">By using the **ClientCredentials** class, you ensure that WCF takes whatever authentication mechanisms are specified in that object’s channel stack and applies them to the exchange between your client and the service.</span></span>  
  
 <span data-ttu-id="129b1-113">因為[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]裝載同處理序與其使用的應用程式，不一定需要使用**ClientCredentials**類別來設定認證，用戶端上使用應用程式所使用的通訊物件。</span><span class="sxs-lookup"><span data-stu-id="129b1-113">Because the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is hosted in-process with its consuming application, it is not imperative to use the **ClientCredentials** class to set credentials on the client communication objects that the consuming application uses.</span></span> <span data-ttu-id="129b1-114">它是，不過，最佳做法進行此作業。</span><span class="sxs-lookup"><span data-stu-id="129b1-114">It is, however, considered good practice to do so.</span></span>  
  
 <span data-ttu-id="129b1-115">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]建議您使用**ClientCredentials**類別。</span><span class="sxs-lookup"><span data-stu-id="129b1-115">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] encourages the use of the **ClientCredentials** class.</span></span> <span data-ttu-id="129b1-116">此屬性會指定是否接受使用者名稱和密碼連線 URI 中的 Oracle 資料庫配接器。</span><span class="sxs-lookup"><span data-stu-id="129b1-116">This property specifies whether the adapter will accept the user name and password for the Oracle database in the connection URI.</span></span> <span data-ttu-id="129b1-117">**AcceptCredentialsInUri**預設為**false**，這表示，配接器會擲回例外狀況的連線 URI 包含認證。</span><span class="sxs-lookup"><span data-stu-id="129b1-117">**AcceptCredentialsInUri** defaults to **false**, which means that the adapter will throw an exception if the connection URI contains credentials.</span></span> <span data-ttu-id="129b1-118">您可以設定**AcceptCredentialsInUri**要 **，則為 true**提供連線 URI 中的認證。</span><span class="sxs-lookup"><span data-stu-id="129b1-118">You can set **AcceptCredentialsInUri** to **true** to supply credentials in the connection URI.</span></span>  
  
 <span data-ttu-id="129b1-119">下列範例示範如何使用**認證**屬性上設定 Oracle 資料庫的認證**ChannelFactory**。</span><span class="sxs-lookup"><span data-stu-id="129b1-119">The following example shows how to use the **Credentials** property to set credentials for the Oracle database on a **ChannelFactory**.</span></span>  
  
```  
// Create binding and endpoint  
OracleDBBinding binding = new OracleDBBinding();  
EndpointAddress endpointAddress = new EndpointAddress("oracleDB://Adapter");  
  
// Create the channel factory   
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, endpointAddress))  
  
// Set user name and password  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
  
// Open the channel factory  
factory.Open();  
```  
  
 <span data-ttu-id="129b1-120">下列範例示範如何使用**ClientCredentials**類別來設定 WCF 用戶端上的 Oracle 資料庫的認證。</span><span class="sxs-lookup"><span data-stu-id="129b1-120">The following example shows how to use the **ClientCredentials** class to set credentials for the Oracle database on a WCF client.</span></span>  
  
```  
// Initialize a new client for the SQLEXECUTE operation from configuration   
SQLEXECUTEClient sqlExecuteClient = new SQLEXECUTEClient("OracleDBBinding_SQLEXECUTE");  
  
// Set user name and password  
sqlExecuteClient.ClientCredentials.UserName.UserName = "SCOTT";  
sqlExecuteClient.ClientCredentials.UserName.Password = "TIGER";  
  
// Open the client  
sqlExecuteClient.Open();  
```  
  
## <a name="how-can-i-provide-for-more-secure-data-exchange-across-process-boundaries"></a><span data-ttu-id="129b1-121">如何跨處理序界限提供更安全的資料交換？</span><span class="sxs-lookup"><span data-stu-id="129b1-121">How Can I Provide for More Secure Data Exchange Across Process Boundaries?</span></span>  
 <span data-ttu-id="129b1-122">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]裝載同處理序的應用程式或取用它的服務。</span><span class="sxs-lookup"><span data-stu-id="129b1-122">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] is hosted in-process with the application or service that consumes it.</span></span> <span data-ttu-id="129b1-123">因為配接器裝載同處理序與取用者，就不需要在取用者之間交換的訊息提供安全性和[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="129b1-123">Because the adapter is hosted in-process with the consumer, there is no need to provide security on messages exchanged between the consumer and the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="129b1-124">不過，如果使用的應用程式或服務會傳送包含跨處理序界限，另一個服務或用戶端機密的資料庫資訊的訊息，您應該提供適當的保護，這項資料在您的環境中的量值。</span><span class="sxs-lookup"><span data-stu-id="129b1-124">However, if the consuming application or service sends messages that contain sensitive database information across a process boundary to another service or client, you should take measures to provide adequate protection for this data in your environment.</span></span> [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]<span data-ttu-id="129b1-125"> 提供許多選項來協助保護用戶端與服務之間傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="129b1-125"> provides many options for helping to secure messages sent between clients and services.</span></span> <span data-ttu-id="129b1-126">如需有關協助保護用戶端與服務之間傳送的訊息[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]，請參閱 < [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx)。</span><span class="sxs-lookup"><span data-stu-id="129b1-126">For more information about helping to secure messages sent between clients and services in [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)], see [Securing Services and Clients](https://msdn.microsoft.com/library/ms734736.aspx).</span></span> <span data-ttu-id="129b1-127">如需一般資訊的安全性功能[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]提供，請參閱 < [Windows Communication Foundation 安全性](https://msdn.microsoft.com/library/ms732362.aspx)。</span><span class="sxs-lookup"><span data-stu-id="129b1-127">For more general information about security features that [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] provides, see [Windows Communication Foundation Security](https://msdn.microsoft.com/library/ms732362.aspx).</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="129b1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="129b1-128">See Also</span></span>  
<span data-ttu-id="129b1-129">[保護您的 Oracle 資料庫應用程式](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md) </span><span class="sxs-lookup"><span data-stu-id="129b1-129">[Secure your Oracle Database applications](../../adapters-and-accelerators/adapter-oracle-database/secure-your-oracle-database-applications.md) </span></span>  
[<span data-ttu-id="129b1-130">最佳作法</span><span class="sxs-lookup"><span data-stu-id="129b1-130">Best Practices</span></span>](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)