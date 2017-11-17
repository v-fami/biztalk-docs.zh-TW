---
title: "建立連接到 SQL Server |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44a03b2c-55b5-49a0-92cc-6f017720d34a
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3b87b4141c9e14c680d8100a7c505dda0a0093c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-connection-to-sql-server"></a><span data-ttu-id="b222f-102">建立 SQL Server 的連接</span><span class="sxs-lookup"><span data-stu-id="b222f-102">Create a connection to SQL Server</span></span>
<span data-ttu-id="b222f-103">[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="b222f-103">The [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="b222f-104">因此，它可讓 SQL Server 資料庫，透過 WCF 端點位址的通訊。</span><span class="sxs-lookup"><span data-stu-id="b222f-104">As such, it enables communication to a SQL Server database through a WCF endpoint address.</span></span> <span data-ttu-id="b222f-105">在 WCF 中，識別服務的網路位置的端點位址，以及通常表示做為統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="b222f-105">In WCF, the endpoint address identifies the network location of a service and is typically expressed as a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="b222f-106">[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]表示這個位置做為連接 URI，其中包含屬性的[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]用以連接到 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="b222f-106">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses to establish a connection to the SQL Server database.</span></span> <span data-ttu-id="b222f-107">您必須指定連線 URI 時您：</span><span class="sxs-lookup"><span data-stu-id="b222f-107">You must specify a connection URI when you:</span></span>  
  
-   <span data-ttu-id="b222f-108">建立通道處理站或通道接聽程式使用 WCF 通道模型，或當您建立使用 WCF 服務模型的 WCF 用戶端或服務主機。</span><span class="sxs-lookup"><span data-stu-id="b222f-108">Create a channel factory or a channel listener using the WCF channel model or when you create a WCF client or service host using the WCF service model.</span></span>  
  
-   <span data-ttu-id="b222f-109">建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="b222f-109">Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="b222f-110">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="b222f-110">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or WCF service interface for a WCF service model solution.</span></span>  
  
-   <span data-ttu-id="b222f-111">使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]擷取訊息結構描述從[!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]BizTalk Server 解決方案。</span><span class="sxs-lookup"><span data-stu-id="b222f-111">Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] for a BizTalk Server solution.</span></span>  
  
-   <span data-ttu-id="b222f-112">您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="b222f-112">Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class or WCF service interface for a WCF service model solution.</span></span>  
  
 <span data-ttu-id="b222f-113">此章節的主題描述如何之間建立連線[!INCLUDE[adaptersql](../../includes/adaptersql-md.md)]和藉由提供您的 SQL Server 資料庫：</span><span class="sxs-lookup"><span data-stu-id="b222f-113">The topics in this section describe how to establish a connection between the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] and the SQL Server database by providing you with:</span></span>  
  
-   <span data-ttu-id="b222f-114">連接屬性和結構的 SQL Server 連接 URI 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b222f-114">Information about the connection properties and the structure of the SQL Server connection URI.</span></span>  
  
-   <span data-ttu-id="b222f-115">主題連結，示範如何透過指定連線 URI [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b222f-115">Links to topics that show how to specify a connection URI by using the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
-   <span data-ttu-id="b222f-116">連接到 SQL Server 使用 Windows 驗證的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b222f-116">Information about connecting to SQL Server using Windows Authentication.</span></span>  
  
  
  
## <a name="see-also"></a><span data-ttu-id="b222f-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b222f-117">See Also</span></span>  
[<span data-ttu-id="b222f-118">開發 SQL 應用程式</span><span class="sxs-lookup"><span data-stu-id="b222f-118">Develop your SQL applications</span></span>](../../adapters-and-accelerators/adapter-sql/develop-your-sql-applications.md)