---
title: "資料和結構的節點直接對應到訊息執行個體 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18cf721c-2972-43c6-8ae4-f2f8f83ba2c5
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d5ed1aae517bb81e5a6cfb888300015e99ec017
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="nodes-that-correspond-directly-to-message-instance-data-and-structure"></a><span data-ttu-id="5ee32-102">直接對應到訊息執行個體資料與結構的節點</span><span class="sxs-lookup"><span data-stu-id="5ee32-102">Nodes That Correspond Directly to Message Instance Data and Structure</span></span>
<span data-ttu-id="5ee32-103">某些用來在 BizTalk 編輯器中建立結構描述的節點類型，會直接對應到由結構描述所決定之執行個體訊息的 XML 表示法中的項目與屬性 (對於像是一般檔案格式之類的其它執行個體訊息格式，只有從其它格式轉換後並轉譯為其它格式前，才會有這種對應存在)。</span><span class="sxs-lookup"><span data-stu-id="5ee32-103">Some of the node types that you use to create schemas in BizTalk Editor correspond directly to elements and attributes in XML representation of instance messages governed by the schema (for other instance message formats, such as flat file formats, this correspondence only exists after translation from the other format and before translation to the other format).</span></span> <span data-ttu-id="5ee32-104">這些節點型別是**記錄**節點 (包括根**記錄**節點)，**欄位項目**節點，和**欄位屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="5ee32-104">These node types are **Record** nodes (including root **Record** nodes), **Field Element** nodes, and **Field Attribute** nodes.</span></span>  
  
 <span data-ttu-id="5ee32-105">值提供給**節點名稱**屬性**記錄**和**欄位項目**節點所控管的 XML 執行個體訊息中指定的對應項目名稱結構描述。</span><span class="sxs-lookup"><span data-stu-id="5ee32-105">The values you give to the **Node Name** property of **Record** and **Field Element** nodes specify the name of the corresponding element in XML instance messages governed by the schema.</span></span> <span data-ttu-id="5ee32-106">同樣地，這些值提供給**節點名稱**屬性**欄位屬性**節點在結構描述所決定之 XML 執行個體訊息中指定對應屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="5ee32-106">Likewise, the values you give to the **Node Name** property of **Field Attribute** nodes specify the name of the corresponding attribute in XML instance messages governed by the schema.</span></span> <span data-ttu-id="5ee32-107">這個屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="5ee32-107">More details on this property [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
 <span data-ttu-id="5ee32-108">本章節的其餘部分提供的根節點，這個類別的詳細資訊**記錄**由於其特殊角色的個別處理方式接收結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="5ee32-108">The remainder of this section provides more information about this class of nodes, with root **Record** nodes receiving separate treatment due to their special role in schemas.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5ee32-109">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="5ee32-109">Next steps</span></span> 
  
-   [<span data-ttu-id="5ee32-110">根節點</span><span class="sxs-lookup"><span data-stu-id="5ee32-110">Root Nodes</span></span>](../core/root-nodes.md)  
  
-   [<span data-ttu-id="5ee32-111">記錄節點</span><span class="sxs-lookup"><span data-stu-id="5ee32-111">Record Nodes</span></span>](../core/record-nodes.md)  
  
-   [<span data-ttu-id="5ee32-112">欄位項目節點</span><span class="sxs-lookup"><span data-stu-id="5ee32-112">Field Element Nodes</span></span>](../core/field-element-nodes.md)  
  
-   [<span data-ttu-id="5ee32-113">欄位屬性節點</span><span class="sxs-lookup"><span data-stu-id="5ee32-113">Field Attribute Nodes</span></span>](../core/field-attribute-nodes.md)