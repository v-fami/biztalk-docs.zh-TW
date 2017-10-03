---
title: "如何建立一般檔案訊息的結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48f2747b-7f26-4fb2-a855-523e093f3813
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58583037b8fae945dea07aa8af62e969b96e073f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="create-schemas-for-flat-file-messages"></a><span data-ttu-id="806e6-102">建立一般檔案訊息的結構描述</span><span class="sxs-lookup"><span data-stu-id="806e6-102">Create Schemas for Flat File Messages</span></span>

## <a name="overview"></a><span data-ttu-id="806e6-103">概觀</span><span class="sxs-lookup"><span data-stu-id="806e6-103">Overview</span></span>
<span data-ttu-id="806e6-104">建立 XML 訊息結構描述中所述之後[建立 XML 訊息的結構](../core/how-to-create-schemas-for-xml-messages.md)，使用**Schema Editor Extensions**屬性**結構描述**節點，以啟用一般檔案延伸模組。</span><span class="sxs-lookup"><span data-stu-id="806e6-104">After creating an XML message schema as described in [Creating Schemas for XML Messages](../core/how-to-create-schemas-for-xml-messages.md), use the **Schema Editor Extensions** property of the **Schema** node to enable the flat file extension.</span></span> <span data-ttu-id="806e6-105">啟用一般檔案延伸模組會在結構描述中的許多節點類型加入相當多的屬性。</span><span class="sxs-lookup"><span data-stu-id="806e6-105">Enabling the flat file extension adds a considerable number of properties to many of the node types within a schema.</span></span> <span data-ttu-id="806e6-106">這些屬性通常用來控制如何將一般檔案商務文件轉譯為對等的 XML 商務文件，以及從 XML 商務文件轉譯為對等的一般檔案商務文件，屬性值以 XML 結構描述定義 (XSD) 語言註解儲存在結構描述檔案中。</span><span class="sxs-lookup"><span data-stu-id="806e6-106">These properties are generally used to control how a flat file business document is translated to and from its equivalent XML business document, and their values are stored as XML Schema definition language (XSD ) annotations within the schema file.</span></span> <span data-ttu-id="806e6-107">要正確地使用這些屬性需要多加練習，並全盤瞭解每個一般檔案格式分別管理哪些方面。</span><span class="sxs-lookup"><span data-stu-id="806e6-107">Using these properties properly takes some practice and a thorough understanding of which aspects of the flat file format they each govern.</span></span> 

<span data-ttu-id="806e6-108">針對概念和參考的一般檔案屬性的相關資訊，請參閱[考量當建立一般檔案訊息結構描述](../core/considerations-when-creating-flat-file-message-schemas.md)和**一般檔案結構描述的增補節點屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="806e6-108">For conceptual and reference information about the flat file properties, see [Considerations When Creating Flat File Message Schemas](../core/considerations-when-creating-flat-file-message-schemas.md) and **Supplemental Node Properties for Flat File Schemas** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="806e6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="806e6-109">See Also</span></span>  
-  [<span data-ttu-id="806e6-110">管理專案中的結構描述</span><span class="sxs-lookup"><span data-stu-id="806e6-110">Managing Schemas Within Projects</span></span>](../core/managing-schemas-within-projects.md)
-  <span data-ttu-id="806e6-111">這些屬性的更多詳細資料[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="806e6-111">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>