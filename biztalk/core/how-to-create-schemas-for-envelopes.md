---
title: 如何建立信封的結構描述 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ae1c991c-447f-497e-803c-1cb8cad2846b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7308a093f9f95ce2342f268554deb67193aea053
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22249590"
---
# <a name="create-schemas-for-envelopes"></a><span data-ttu-id="a5479-102">建立信封的結構描述</span><span class="sxs-lookup"><span data-stu-id="a5479-102">Create Schemas for Envelopes</span></span>

## <a name="overview"></a><span data-ttu-id="a5479-103">概觀</span><span class="sxs-lookup"><span data-stu-id="a5479-103">Overview</span></span>
<span data-ttu-id="a5479-104">建立 XML 訊息結構描述中所述之後[建立 XML 訊息的結構](../core/how-to-create-schemas-for-xml-messages.md)，將**信封**屬性**結構描述**節點**是**.</span><span class="sxs-lookup"><span data-stu-id="a5479-104">After creating an XML message schema as described in [Creating Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md), set the **Envelope** property of the **Schema** node to **Yes**.</span></span> <span data-ttu-id="a5479-105">視信封結構描述的某些特性而定 (例如是否有多個根節點)，您將需要設定幾個其他信封特定屬性。</span><span class="sxs-lookup"><span data-stu-id="a5479-105">Depending on certain characteristics of your envelope schema, such as whether there are multiple root nodes, you will need to set several other envelope-specific properties.</span></span> <span data-ttu-id="a5479-106">如需詳細資訊，請參閱[信封結構描述](../core/envelope-schemas.md)。</span><span class="sxs-lookup"><span data-stu-id="a5479-106">For more information, see [Envelope Schemas](../core/envelope-schemas.md).</span></span>  
  
 <span data-ttu-id="a5479-107">信封的內文 XPath 屬性會指向包含文件項目的項目。</span><span class="sxs-lookup"><span data-stu-id="a5479-107">The body XPath property of the envelope points to the element that contains the document elements.</span></span> <span data-ttu-id="a5479-108">XPath 所指的實際項目則不屬於該文件。</span><span class="sxs-lookup"><span data-stu-id="a5479-108">The actual element where the XPath points to does not belong to the document.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5479-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5479-109">See Also</span></span>  
-  [<span data-ttu-id="a5479-110">管理專案中的結構描述</span><span class="sxs-lookup"><span data-stu-id="a5479-110">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)
-  <span data-ttu-id="a5479-111">**信封**屬性[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="a5479-111">**Envelope** property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>