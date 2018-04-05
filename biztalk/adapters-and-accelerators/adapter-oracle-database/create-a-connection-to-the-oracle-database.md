---
title: 建立連接到 Oracle 資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- adapter, connecting to the Oracle Database
ms.assetid: 95f7905a-abad-4841-85c4-62cf0cc1e044
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3f9a42994f0cde9df19e3b80e16fcbafbb2d8d5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-connection-to-the-oracle-database"></a><span data-ttu-id="2db71-102">建立 Oracle 資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="2db71-102">Create a connection to the Oracle Database</span></span>
<span data-ttu-id="2db71-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="2db71-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="2db71-104">因此，它可讓 Oracle 資料庫，透過 WCF 端點位址的通訊。</span><span class="sxs-lookup"><span data-stu-id="2db71-104">As such, it enables communication to an Oracle database through a WCF endpoint address.</span></span> <span data-ttu-id="2db71-105">在 WCF 中，端點位址通常表示做為統一資源識別元 (URI)，用來識別服務的網路位置。</span><span class="sxs-lookup"><span data-stu-id="2db71-105">In WCF, the endpoint address is typically expressed as a Uniform Resource Identifier (URI), which identifies the network location of the service.</span></span> <span data-ttu-id="2db71-106">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表示這個位置做為連接 URI，其中包含屬性的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]用以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2db71-106">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses to establish a connection to the Oracle database.</span></span>  
  
 <span data-ttu-id="2db71-107">您必須指定連線 URI 時您：</span><span class="sxs-lookup"><span data-stu-id="2db71-107">You must specify a connection URI when you:</span></span>  
  
-   <span data-ttu-id="2db71-108">建立通道處理站或通道接聽程式使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，或當您建立使用 WCF 用戶端或服務主機[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型。</span><span class="sxs-lookup"><span data-stu-id="2db71-108">Create a channel factory or a channel listener using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model or when you create a WCF client or service host using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model.</span></span>  
  
-   <span data-ttu-id="2db71-109">建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="2db71-109">Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="2db71-110">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別或 WCF 服務介面[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型方案。</span><span class="sxs-lookup"><span data-stu-id="2db71-110">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or WCF service interface for a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model solution.</span></span>  
  
-   <span data-ttu-id="2db71-111">使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]擷取訊息結構描述從[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="2db71-111">Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] for a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="2db71-112">您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="2db71-112">Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class or WCF service interface for a WCF service model solution.</span></span>  
  
 <span data-ttu-id="2db71-113">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援兩種方式建立連接到 Oracle 資料庫：</span><span class="sxs-lookup"><span data-stu-id="2db71-113">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports two ways of establishing a connection to the Oracle database:</span></span>  
  
-   <span data-ttu-id="2db71-114">**使用 tnsnames.ora**。</span><span class="sxs-lookup"><span data-stu-id="2db71-114">**Using tnsnames.ora**.</span></span> <span data-ttu-id="2db71-115">這種方法，連線配接器用戶端所提供的 URI 包含只 tnsnames.ora 檔案中指定的網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="2db71-115">In this approach, the connection URI provided by the adapter client contains only the net service name specified in the tnsnames.ora file.</span></span> <span data-ttu-id="2db71-116">配接器會擷取連線參數，例如伺服器名稱、 服務名稱，連接埠編號，從檔案中的網路服務名稱的項目等等。</span><span class="sxs-lookup"><span data-stu-id="2db71-116">The adapter extracts the connection parameters such as server name, service name, port no, etc. from the net service name entry in the file.</span></span> <span data-ttu-id="2db71-117">若要使用這種方法，執行 Oracle 用戶端的電腦必須設定要在 tnsnames.ora 檔案中包含之 Oracle 資料庫的網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="2db71-117">To use this approach, the computer running the Oracle client must be configured to include the net service name for the Oracle database in the tnsnames.ora file.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2db71-118">由於 Oracle 用戶端的限制， **DataSourceName**中的參數 (net service name)[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)不能包含超過 39 個字元，如果您正在執行在交易中的作業。</span><span class="sxs-lookup"><span data-stu-id="2db71-118">Due to an Oracle Client limitation, the **DataSourceName** parameter (net service name) in the [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md) cannot contain more than 39 characters if you are performing operations in a transaction.</span></span> <span data-ttu-id="2db71-119">因此，請確定為指定的值**DataSourceName**參數為小於或等於 39 個字元，如果您將在交易中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="2db71-119">Therefore, make sure that the value specified for the **DataSourceName** parameter is less than or equal to 39 characters if you will be performing operations in a transaction.</span></span>  
  
-   <span data-ttu-id="2db71-120">**不使用 tnsnames.ora**。</span><span class="sxs-lookup"><span data-stu-id="2db71-120">**Without using tnsnames.ora**.</span></span> <span data-ttu-id="2db71-121">在這種方式，配接器用戶端會指定直接在 連線 URI 中的連接參數。</span><span class="sxs-lookup"><span data-stu-id="2db71-121">In this approach, the adapter clients specify the connection parameters directly in the connection URI.</span></span> <span data-ttu-id="2db71-122">這不需要網路服務名稱必須存在於用戶端電腦上 tnsnames.ora 檔案。</span><span class="sxs-lookup"><span data-stu-id="2db71-122">This does not require the net service name to be present in the tnsnames.ora file on the client computer.</span></span> <span data-ttu-id="2db71-123">這個方法甚至不需要 tnsname.ora 檔案存在於用戶端電腦上。</span><span class="sxs-lookup"><span data-stu-id="2db71-123">This approach does not even require the tnsname.ora file to be present on the client computer.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="2db71-124">如果您在交易中執行作業，則不支援這種連線模式。</span><span class="sxs-lookup"><span data-stu-id="2db71-124">This mode of connectivity is not supported if you are performing operations in a transaction.</span></span> <span data-ttu-id="2db71-125">這是因為 Oracle 用戶端的限制。</span><span class="sxs-lookup"><span data-stu-id="2db71-125">This is due to a limitation of Oracle Client.</span></span>  
  
 <span data-ttu-id="2db71-126">此章節的主題描述如何之間建立連線[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]和 Oracle 資料庫，藉由提供您具有：</span><span class="sxs-lookup"><span data-stu-id="2db71-126">The topics in this section describe how to establish a connection between the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] and the Oracle database by providing you with:</span></span>  
  
-   <span data-ttu-id="2db71-127">設定 Oracle 用戶端的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2db71-127">Information about configuring the Oracle client.</span></span>  
  
-   <span data-ttu-id="2db71-128">連接屬性和結構的 Oracle 連接 URI 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2db71-128">Information about the connection properties and the structure of the Oracle connection URI.</span></span>  
  
-   <span data-ttu-id="2db71-129">示範如何建立連接所使用的主題連結[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="2db71-129">Links to topics that show how to establish a connection by using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
-   <span data-ttu-id="2db71-130">連接到 Oracle 資料庫使用 Windows 驗證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="2db71-130">Information about connecting to the Oracle database using Windows Authentication.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2db71-131">本節內容</span><span class="sxs-lookup"><span data-stu-id="2db71-131">In This Section</span></span>  
  
-   [<span data-ttu-id="2db71-132">設定 Oracle 資料庫配接器的 Oracle 用戶端</span><span class="sxs-lookup"><span data-stu-id="2db71-132">Configure the Oracle Client for the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)  
  
-   [<span data-ttu-id="2db71-133">建立 Oracle 資料庫連線 URI</span><span class="sxs-lookup"><span data-stu-id="2db71-133">Create the Oracle Database connection URI</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)  
  
-   [<span data-ttu-id="2db71-134">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="2db71-134">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="2db71-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2db71-135">See Also</span></span>  
[<span data-ttu-id="2db71-136">開發應用程式的 Oracle 資料庫</span><span class="sxs-lookup"><span data-stu-id="2db71-136">Develop your Oracle Database applications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)