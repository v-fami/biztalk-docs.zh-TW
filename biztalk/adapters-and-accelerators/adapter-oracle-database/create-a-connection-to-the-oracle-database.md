---
title: 建立 Oracle 資料庫的連接 |Microsoft Docs
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
ms.openlocfilehash: c79af51280879e1cf6c72053a42822cd24fae68e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36988455"
---
# <a name="create-a-connection-to-the-oracle-database"></a><span data-ttu-id="0a172-102">建立 Oracle 資料庫的連接</span><span class="sxs-lookup"><span data-stu-id="0a172-102">Create a connection to the Oracle Database</span></span>
<span data-ttu-id="0a172-103">[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="0a172-103">The [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="0a172-104">因此，它可讓 Oracle 資料庫，透過 WCF 端點位址的通訊。</span><span class="sxs-lookup"><span data-stu-id="0a172-104">As such, it enables communication to an Oracle database through a WCF endpoint address.</span></span> <span data-ttu-id="0a172-105">在 WCF 中，端點位址通常被表示做為統一資源識別元 (URI)，用來識別服務的網路位置。</span><span class="sxs-lookup"><span data-stu-id="0a172-105">In WCF, the endpoint address is typically expressed as a Uniform Resource Identifier (URI), which identifies the network location of the service.</span></span> <span data-ttu-id="0a172-106">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]表示此位置做為連線 URI，其中包含屬性的[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]用以連接到 Oracle 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0a172-106">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] uses to establish a connection to the Oracle database.</span></span>  
  
 <span data-ttu-id="0a172-107">您必須指定 URI 的連接時您：</span><span class="sxs-lookup"><span data-stu-id="0a172-107">You must specify a connection URI when you:</span></span>  
  
- <span data-ttu-id="0a172-108">建立通道處理站或通道接聽程式，使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，或當您建立使用 WCF 用戶端或服務主機[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型。</span><span class="sxs-lookup"><span data-stu-id="0a172-108">Create a channel factory or a channel listener using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model or when you create a WCF client or service host using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model.</span></span>  
  
- <span data-ttu-id="0a172-109">建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。</span><span class="sxs-lookup"><span data-stu-id="0a172-109">Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
- <span data-ttu-id="0a172-110">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 WCF 用戶端類別或 WCF 服務介面[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型方案。</span><span class="sxs-lookup"><span data-stu-id="0a172-110">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or WCF service interface for a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model solution.</span></span>  
  
- <span data-ttu-id="0a172-111">使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來擷取從訊息結構描述[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。</span><span class="sxs-lookup"><span data-stu-id="0a172-111">Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] for a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
- <span data-ttu-id="0a172-112">您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="0a172-112">Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class or WCF service interface for a WCF service model solution.</span></span>  
  
  <span data-ttu-id="0a172-113">[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]支援兩種方式來建立 Oracle 資料庫的連接：</span><span class="sxs-lookup"><span data-stu-id="0a172-113">The [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] supports two ways of establishing a connection to the Oracle database:</span></span>  
  
- <span data-ttu-id="0a172-114">**使用 tnsnames.ora**。</span><span class="sxs-lookup"><span data-stu-id="0a172-114">**Using tnsnames.ora**.</span></span> <span data-ttu-id="0a172-115">這種方法，連線配接器用戶端所提供的 URI 會包含只 tnsnames.ora 檔案中指定的網路服務名稱。</span><span class="sxs-lookup"><span data-stu-id="0a172-115">In this approach, the connection URI provided by the adapter client contains only the net service name specified in the tnsnames.ora file.</span></span> <span data-ttu-id="0a172-116">配接器會擷取連線參數，例如伺服器名稱、 服務名稱、 連接埠不會，從檔案中的 net 的服務名稱項目等等。</span><span class="sxs-lookup"><span data-stu-id="0a172-116">The adapter extracts the connection parameters such as server name, service name, port no, etc. from the net service name entry in the file.</span></span> <span data-ttu-id="0a172-117">若要使用這種方法，執行 Oracle 用戶端的電腦，必須設定為包含 tnsnames.ora 檔案中的 net 的服務名稱的 Oracle 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="0a172-117">To use this approach, the computer running the Oracle client must be configured to include the net service name for the Oracle database in the tnsnames.ora file.</span></span>  
  
  > [!IMPORTANT]
  >  <span data-ttu-id="0a172-118">執行 Oracle 用戶端的限制，因為**DataSourceName**中的參數 （net 的服務名稱）[建立 Oracle 資料庫連線 URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)不能包含超過 39 個字元，如果您正在執行在交易中的作業。</span><span class="sxs-lookup"><span data-stu-id="0a172-118">Due to an Oracle Client limitation, the **DataSourceName** parameter (net service name) in the [Create the Oracle Database connection URI](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md) cannot contain more than 39 characters if you are performing operations in a transaction.</span></span> <span data-ttu-id="0a172-119">因此，請確定為指定的值**DataSourceName**參數是否小於或等於 39 個字元，如果您將會在交易中執行作業。</span><span class="sxs-lookup"><span data-stu-id="0a172-119">Therefore, make sure that the value specified for the **DataSourceName** parameter is less than or equal to 39 characters if you will be performing operations in a transaction.</span></span>  
  
- <span data-ttu-id="0a172-120">**不使用 tnsnames.ora**。</span><span class="sxs-lookup"><span data-stu-id="0a172-120">**Without using tnsnames.ora**.</span></span> <span data-ttu-id="0a172-121">在此方法中，配接器用戶端會指定連線參數，直接在 連線 URI 中。</span><span class="sxs-lookup"><span data-stu-id="0a172-121">In this approach, the adapter clients specify the connection parameters directly in the connection URI.</span></span> <span data-ttu-id="0a172-122">這不需要網路的服務名稱會出現在用戶端電腦上的 tnsnames.ora 檔案。</span><span class="sxs-lookup"><span data-stu-id="0a172-122">This does not require the net service name to be present in the tnsnames.ora file on the client computer.</span></span> <span data-ttu-id="0a172-123">這種方法甚至不需要 tnsname.ora 檔案必須存在於用戶端電腦上。</span><span class="sxs-lookup"><span data-stu-id="0a172-123">This approach does not even require the tnsname.ora file to be present on the client computer.</span></span>  
  
  > [!IMPORTANT]
  >  <span data-ttu-id="0a172-124">如果您要在交易中執行作業，則不支援這種連線模式。</span><span class="sxs-lookup"><span data-stu-id="0a172-124">This mode of connectivity is not supported if you are performing operations in a transaction.</span></span> <span data-ttu-id="0a172-125">這是因為 Oracle 用戶端的限制。</span><span class="sxs-lookup"><span data-stu-id="0a172-125">This is due to a limitation of Oracle Client.</span></span>  
  
  <span data-ttu-id="0a172-126">在本節中的主題描述如何之間建立連線[!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)]和 Oracle 資料庫，藉由提供您使用：</span><span class="sxs-lookup"><span data-stu-id="0a172-126">The topics in this section describe how to establish a connection between the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] and the Oracle database by providing you with:</span></span>  
  
- <span data-ttu-id="0a172-127">設定 Oracle 用戶端的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0a172-127">Information about configuring the Oracle client.</span></span>  
  
- <span data-ttu-id="0a172-128">連接屬性和 Oracle 連接 URI 的結構資訊。</span><span class="sxs-lookup"><span data-stu-id="0a172-128">Information about the connection properties and the structure of the Oracle connection URI.</span></span>  
  
- <span data-ttu-id="0a172-129">示範如何建立連接所使用的主題連結[!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0a172-129">Links to topics that show how to establish a connection by using the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
- <span data-ttu-id="0a172-130">連接到 Oracle 資料庫使用 Windows 驗證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0a172-130">Information about connecting to the Oracle database using Windows Authentication.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a172-131">本節內容</span><span class="sxs-lookup"><span data-stu-id="0a172-131">In This Section</span></span>  
  
-   [<span data-ttu-id="0a172-132">設定 Oracle 用戶端，Oracle 資料庫配接器</span><span class="sxs-lookup"><span data-stu-id="0a172-132">Configure the Oracle Client for the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/configure-the-oracle-client-for-the-oracle-database-adapter.md)  
  
-   [<span data-ttu-id="0a172-133">建立 Oracle 資料庫連線 URI</span><span class="sxs-lookup"><span data-stu-id="0a172-133">Create the Oracle Database connection URI</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-the-oracle-database-connection-uri.md)  
  
-   [<span data-ttu-id="0a172-134">連接到 Oracle 資料庫使用 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="0a172-134">Connect to the Oracle Database Using Windows Authentication</span></span>](../../adapters-and-accelerators/adapter-oracle-database/connect-to-the-oracle-database-using-windows-authentication.md)  
  
## <a name="see-also"></a><span data-ttu-id="0a172-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a172-135">See Also</span></span>  
[<span data-ttu-id="0a172-136">開發您的 Oracle 資料庫應用程式</span><span class="sxs-lookup"><span data-stu-id="0a172-136">Develop your Oracle Database applications</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-your-oracle-database-applications.md)