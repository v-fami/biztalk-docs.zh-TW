---
title: 建立連接至 Siebel 系統 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- connecting, to the Siebel system
ms.assetid: 5810eeb1-6e26-4620-a731-fb352eebea2e
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a108335263e85db832f4db144d27b64b92429683
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22221846"
---
# <a name="create-a-connection-to-the-siebel-system"></a><span data-ttu-id="0cbd7-102">建立連接至 Siebel 系統</span><span class="sxs-lookup"><span data-stu-id="0cbd7-102">Create a connection to the Siebel system</span></span>
<span data-ttu-id="0cbd7-103">[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]是[!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)]自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-103">The [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] is a [!INCLUDE[firstref_btsWinCommFoundation](../../includes/firstref-btswincommfoundation-md.md)] custom binding.</span></span> <span data-ttu-id="0cbd7-104">因此，它可讓透過 WCF 端點位址的 Siebel 系統的通訊。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-104">As such, it enables communication to a Siebel system through a WCF endpoint address.</span></span> <span data-ttu-id="0cbd7-105">在 WCF 中的端點位址識別服務的網路位置，以及通常表示做為統一資源識別元 (URI)。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-105">In WCF the endpoint address identifies the network location of a service and is typically expressed as a Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="0cbd7-106">[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]表示這個位置做為連接 URI，其中包含屬性的[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]用以連接至 Siebel 系統。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-106">The [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] expresses this location as a connection URI, which contains properties that the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] uses to establish a connection to the Siebel system.</span></span> <span data-ttu-id="0cbd7-107">您必須指定連線 URI 時您：</span><span class="sxs-lookup"><span data-stu-id="0cbd7-107">You must specify a connection URI when you:</span></span>  
  
-   <span data-ttu-id="0cbd7-108">建立通道處理站或通道接聽程式使用[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]通道模型，或建立使用 WCF 用戶端或服務主機[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-108">Create a channel factory or a channel listener using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] channel model, or create a WCF client or service host using the [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model.</span></span>  
  
-   <span data-ttu-id="0cbd7-109">建立實體連接埠繫結中的[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-109">Create a physical port binding in a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="0cbd7-110">使用[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]產生 WCF 用戶端類別或 WCF 服務介面[!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)]服務模型方案。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-110">Use the [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] to generate a WCF client class, or WCF service interface for a [!INCLUDE[nextref_btsWinCommFoundation](../../includes/nextref-btswincommfoundation-md.md)] service model solution.</span></span>  
  
-   <span data-ttu-id="0cbd7-111">使用[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]擷取訊息結構描述從[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]如[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]方案。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-111">Use the [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] to retrieve message schemas from the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] for a [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] solution.</span></span>  
  
-   <span data-ttu-id="0cbd7-112">您可以使用 ServiceModel Metadata Utility 工具 (svcutil.exe) 來產生 WCF 用戶端類別或 WCF 服務模型方案的 WCF 服務介面。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-112">Use the ServiceModel Metadata Utility tool (svcutil.exe) to generate a WCF client class, or WCF service interface for a WCF service model solution.</span></span>  
  
 <span data-ttu-id="0cbd7-113">此章節的主題描述如何之間建立連線[!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]與藉由提供您與 Siebel 系統：</span><span class="sxs-lookup"><span data-stu-id="0cbd7-113">The topics in this section describe how to establish a connection between the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] and the Siebel system by providing you with:</span></span>  
  
-   <span data-ttu-id="0cbd7-114">連接屬性和結構的 Siebel 連線 URI 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-114">Information about the connection properties and the structure of the Siebel connection URI.</span></span>  
  
-   <span data-ttu-id="0cbd7-115">示範如何建立連接所使用的主題連結[!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="0cbd7-115">Links to topics that show how to establish a connection by using the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="0cbd7-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cbd7-116">See Also</span></span>  
[<span data-ttu-id="0cbd7-117">開發 Siebel 應用程式</span><span class="sxs-lookup"><span data-stu-id="0cbd7-117">Develop your Siebel applications</span></span>](../../adapters-and-accelerators/adapter-siebel/develop-your-siebel-applications.md)