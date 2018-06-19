---
title: RetractByType |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- RetractByType function [Business Rules Engine], TypedXMLDocument
- RetractByType function [Business Rules Engine]
- RetractByType function [Business Rules Engine], .NET objects
- RetractByType function [Business Rules Engine], TypedData table
- RetractByType function [Business Rules Engine], DataConnection
- .NET objects
ms.assetid: e8867553-ee3c-46be-84cd-d5373eaf3337
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: da8cd4581007ad2bd93ed66ebce4f5de6378280c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22268734"
---
# <a name="retractbytype"></a><span data-ttu-id="0ca39-102">RetractByType</span><span class="sxs-lookup"><span data-stu-id="0ca39-102">RetractByType</span></span>
<span data-ttu-id="0ca39-103">**RetractByType**函式會撤回工作記憶體中的指定類型的所有執行個體，而**Retract**函式會撤回只有特定類型的特定項目。</span><span class="sxs-lookup"><span data-stu-id="0ca39-103">The **RetractByType** function retracts all instances of a specified type in the working memory, whereas the **Retract**function retracts only specific items of a certain type.</span></span> <span data-ttu-id="0ca39-104">以下段落描述如何**RetractByType**函式如何使用不同類型的實體。</span><span class="sxs-lookup"><span data-stu-id="0ca39-104">The following paragraphs describe how the **RetractByType** function works with entities of different types.</span></span>  
  
## <a name="net-objects"></a><span data-ttu-id="0ca39-105">.NET 物件</span><span class="sxs-lookup"><span data-stu-id="0ca39-105">.NET Objects</span></span>  
 <span data-ttu-id="0ca39-106">特定的類別類型的所有物件會從工作記憶體都撤回。</span><span class="sxs-lookup"><span data-stu-id="0ca39-106">All objects for a given class type are retracted from working memory.</span></span> <span data-ttu-id="0ca39-107">您只需從.NET 類別事實窗格將拖曳類別**RetractByType**函式。</span><span class="sxs-lookup"><span data-stu-id="0ca39-107">You simply drag the class from the .NET Classes fact pane into the **RetractByType** function.</span></span>  
  
## <a name="typedxmldocument"></a><span data-ttu-id="0ca39-108">TypedXmlDocument</span><span class="sxs-lookup"><span data-stu-id="0ca39-108">TypedXmlDocument</span></span>  
 <span data-ttu-id="0ca39-109">會撤回所有執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ca39-109">All instances are retracted.</span></span> <span data-ttu-id="0ca39-110">這表示所有**TypedXmlDocument**具有相同**Typedxmldocument**不當所致。</span><span class="sxs-lookup"><span data-stu-id="0ca39-110">This means that all **TypedXmlDocument**s with the same **DocumentType.Selector** are retracted.</span></span> <span data-ttu-id="0ca39-111">您應該適當的節點從 XML 結構描述事實窗格拖曳到**RetractByType**函式。</span><span class="sxs-lookup"><span data-stu-id="0ca39-111">You should drag the appropriate node from the XML Schemas fact pane into the **RetractByType** function.</span></span> <span data-ttu-id="0ca39-112">與一致**Retract**函式中，如果您執行**RetractByType**的文件根節點上，不只將全部**TypedXmlDocuments**該與判斷提示**DocumentType**撤回，但所有的子**TypedXmlDocuments** (**XmlNode**樹狀結構階層架構中) 與那些父關聯**TypedXmlDocuments**也會被撤回。</span><span class="sxs-lookup"><span data-stu-id="0ca39-112">Consistent with the **Retract** function, if you perform a **RetractByType** on the document root node, not only will all **TypedXmlDocuments** asserted with that **DocumentType** be retracted, but all child **TypedXmlDocuments** (**XmlNode**s in the tree hierarchy) associated with those parent **TypedXmlDocuments** will also be retracted.</span></span>  
  
## <a name="typeddatatable-and-dataconnection"></a><span data-ttu-id="0ca39-113">TypedDataTable 和 DataConnection</span><span class="sxs-lookup"><span data-stu-id="0ca39-113">TypedDataTable and DataConnection</span></span>  
 <span data-ttu-id="0ca39-114">**撤銷**和**RetractByType**是兩個相等**TypedDataTable**和**DataConnection**。</span><span class="sxs-lookup"><span data-stu-id="0ca39-114">**Retract** and **RetractByType** are equivalent for both **TypedDataTable** and **DataConnection**.</span></span> <span data-ttu-id="0ca39-115">因為**DataSetName.DataTableName**是唯一的識別碼這兩種類型，只有一個執行個體中沒有引擎在任何時間點的時間。</span><span class="sxs-lookup"><span data-stu-id="0ca39-115">Because **DataSetName.DataTableName** is a unique identifier for both types, there is only one instance in the engine at any point in time.</span></span> <span data-ttu-id="0ca39-116">如同**Retract**，拖曳到資料表**RetractByType**函式。</span><span class="sxs-lookup"><span data-stu-id="0ca39-116">As with **Retract**, you drag the table into the **RetractByType** function.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ca39-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ca39-117">See Also</span></span>  
 [<span data-ttu-id="0ca39-118">引擎控制函式</span><span class="sxs-lookup"><span data-stu-id="0ca39-118">Engine Control Functions</span></span>](../core/engine-control-functions.md)