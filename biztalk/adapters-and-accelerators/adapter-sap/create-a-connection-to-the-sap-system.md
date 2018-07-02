---
title: 建立 SAP 系統的連線 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SAP system, connecting to
- connection URI
- URI
- Uniform Resource Identifier
ms.assetid: 25d1eaa7-d02a-4fd0-8adf-83505cdb1ab8
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ef25dddf3d30f584b30aa0f35b8b1c4140d285e2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36965807"
---
# <a name="create-a-connection-to-the-sap-system"></a><span data-ttu-id="4e8cb-102">建立 SAP 系統的連線</span><span class="sxs-lookup"><span data-stu-id="4e8cb-102">Create a connection to the SAP system</span></span>
<span data-ttu-id="4e8cb-103">[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-103">The [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="4e8cb-104">因此，它可讓 SAP 系統，透過 WCF 端點位址的通訊。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-104">As such, it enables communication to an SAP system through a WCF endpoint address.</span></span> <span data-ttu-id="4e8cb-105">在 WCF 中的端點位址會識別服務的網路位置，而且通常表示做為統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-105">In WCF the endpoint address identifies the network location of a service and is typically expressed as a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="4e8cb-106">[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]表示此位置做為連線 URI，其中包含屬性的[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]用以連接到 SAP 系統。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-106">The [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] uses to establish a connection to the SAP system.</span></span> <span data-ttu-id="4e8cb-107">您必須指定 URI 的連接時您：</span><span class="sxs-lookup"><span data-stu-id="4e8cb-107">You must specify a connection URI when you:</span></span>  
  
- <span data-ttu-id="4e8cb-108">當您建立通道處理站或通道接聽程式，使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，或當您建立使用 WCF 用戶端或服務主機[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-108">When you create a channel factory or a channel listener using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model or when you create a WCF client or service host using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model.</span></span>  
  
- <span data-ttu-id="4e8cb-109">建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-109">Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
- <span data-ttu-id="4e8cb-110">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]來產生 WCF 用戶端類別或 WCF 服務介面[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型方案。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-110">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class or WCF service interface for a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model solution.</span></span>  
  
- <span data-ttu-id="4e8cb-111">使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]來擷取從訊息結構描述[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]解決方案。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-111">Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] for a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
- <span data-ttu-id="4e8cb-112">您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-112">Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class or WCF service interface for a WCF service model solution.</span></span>  
  
  <span data-ttu-id="4e8cb-113">在本節中的主題描述如何之間建立連線[!INCLUDE[adaptersap](../../includes/adaptersap-md.md)]和 SAP 系統，藉由提供您使用：</span><span class="sxs-lookup"><span data-stu-id="4e8cb-113">The topics in this section describe how to establish a connection between the [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] and the SAP system by providing you with:</span></span>  
  
- <span data-ttu-id="4e8cb-114">有關連接屬性以及 SAP 連線 URI 的結構。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-114">Information about the connection properties and the structure of the SAP connection URI.</span></span>  
  
- <span data-ttu-id="4e8cb-115">示範如何建立連接所使用的主題連結[!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="4e8cb-115">Links to topics that show how to establish a connection by using the [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e8cb-116">本節內容</span><span class="sxs-lookup"><span data-stu-id="4e8cb-116">In This Section</span></span>  
  
-   [<span data-ttu-id="4e8cb-117">建立 SAP 系統連線 URI</span><span class="sxs-lookup"><span data-stu-id="4e8cb-117">Create the SAP system connection URI</span></span>](../../adapters-and-accelerators/adapter-sap/create-the-sap-system-connection-uri.md)