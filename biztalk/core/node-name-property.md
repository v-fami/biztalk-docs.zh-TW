---
title: "節點名稱屬性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95d9e5bf-7439-4ef4-ad14-e8d3e8eff911
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1d39c71a425e20c5a9228e418cfa86acb579fa5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="node-name-property"></a><span data-ttu-id="a00de-102">節點名稱屬性</span><span class="sxs-lookup"><span data-stu-id="a00de-102">Node Name Property</span></span>
<span data-ttu-id="a00de-103">使用「BizTalk 編輯器」將節點插入結構描述樹狀結構時，有些節點必須重新命名，有些則不用。</span><span class="sxs-lookup"><span data-stu-id="a00de-103">As you use BizTalk Editor to insert nodes into the schema tree, some nodes are meant to be renamed and others are not.</span></span> <span data-ttu-id="a00de-104">基本上，您可以也應該重新命名**記錄**節點**欄位項目**節點，和**欄位屬性**節點。</span><span class="sxs-lookup"><span data-stu-id="a00de-104">Essentially, you can and should rename **Record** nodes, **Field Element** nodes, and **Field Attribute** nodes.</span></span> <span data-ttu-id="a00de-105">您提供給這些節點的名稱會成為結構描述定義的訊息中，XML 項目及屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="a00de-105">The names that you give to these nodes will become the names of the XML elements and attributes in the message that the schema defines.</span></span>  
  
 <span data-ttu-id="a00de-106">在結構描述樹狀目錄中，您無法重新命名的節點會顯示 XML 標記; 表單中也就是說，小於比 (\<) 和大於 (\>) 符號。</span><span class="sxs-lookup"><span data-stu-id="a00de-106">In the schema tree, the nodes that you cannot rename are shown in the form of XML tags; that is, with the less than (\<) and greater than (\>) signs.</span></span> <span data-ttu-id="a00de-107">例如，**結構描述** 節點， **Choice 群組**節點**Any 項目**節點，和**Any 屬性**節點表示結構描述中樹狀目錄的名稱\<結構描述\>，\<選擇\>，\<任何\>，和\<AnyAttribute\>分別。</span><span class="sxs-lookup"><span data-stu-id="a00de-107">For example, the **Schema** node, **Choice Group** nodes, **Any Element** nodes, and **Any Attribute** nodes are represented in the schema tree with the names \<Schema\>, \<Choice\>, \<Any\>, and \<AnyAttribute\>, respectively.</span></span> <span data-ttu-id="a00de-108">**節點名稱**這類節點的屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="a00de-108">The **Node Name** property for such nodes is read-only.</span></span>  
  
 <span data-ttu-id="a00de-109">內給定**記錄** 節點，您不能有兩個**欄位屬性**具有相同名稱的節點。</span><span class="sxs-lookup"><span data-stu-id="a00de-109">Within a given **Record** node, you cannot have two **Field Attribute** nodes with the same name.</span></span> <span data-ttu-id="a00de-110">不過，您可以擁有多個**欄位項目**節點或**記錄**具有相同名稱做為子節點的相同節點**記錄**節點，只要它們都有相同的資料類型(依指定其**資料型別**屬性**欄位項目**節點或其**資料結構型別**如**記錄**節點）。</span><span class="sxs-lookup"><span data-stu-id="a00de-110">However, you can have more than one **Field Element** node or **Record** node with the same name as child nodes of the same **Record** node, as long as they all have the same data type (as specified by their **Data Type** property for **Field Element** nodes or their **Data Structure Type** for **Record** nodes).</span></span>  
  
 <span data-ttu-id="a00de-111">當您提供名稱，以**記錄**節點**欄位項目**節點，和**欄位屬性**節點，使用描述性的該項目的角色或是屬性內的名稱結構描述所定義之訊息。</span><span class="sxs-lookup"><span data-stu-id="a00de-111">When you give names to **Record** nodes, **Field Element** nodes, and **Field Attribute** nodes, use names that are descriptive of the role of that element or attribute within the message being defined by the schema.</span></span> <span data-ttu-id="a00de-112">例如，FirstName 可能是不錯的選擇的名稱**欄位項目**節點會用來儲存地址結構中某人的名字。</span><span class="sxs-lookup"><span data-stu-id="a00de-112">For example, FirstName is probably a good choice for the name of a **Field Element** node that will be used to store the first name of someone in an address structure.</span></span> <span data-ttu-id="a00de-113">在 XML 執行個體訊息中，若名字為 James，則對應的項目看起來如下。</span><span class="sxs-lookup"><span data-stu-id="a00de-113">In an XML instance message where the first name James occurs, the corresponding element would look like the following.</span></span>  
  
```  
    <FirstName>James</FirstName>  
```  
  
 <span data-ttu-id="a00de-114">當您要重新命名**記錄**節點**欄位項目**節點，和**欄位屬性**節點，您應該知道並非所有的字元可在節點名稱。</span><span class="sxs-lookup"><span data-stu-id="a00de-114">When you are renaming **Record** nodes, **Field Element** nodes, and **Field Attribute** nodes, you should be aware that not all characters are allowed in node names.</span></span> <span data-ttu-id="a00de-115">如需有關這些不允許的字元資訊，請參閱[的節點名稱字元會進行編碼](../core/which-node-name-characters-get-encoded.md)。</span><span class="sxs-lookup"><span data-stu-id="a00de-115">For information about these disallowed characters, see [Which Node Name Characters Get Encoded](../core/which-node-name-characters-get-encoded.md).</span></span> <span data-ttu-id="a00de-116">雖然「BizTalk 編輯器」可讓您將不允許的字元加以編碼來使用，但避免使用這些字元通常是較簡單的作法。</span><span class="sxs-lookup"><span data-stu-id="a00de-116">Although BizTalk Editor allows you to use disallowed characters by encoding them, it is often simpler to avoid such characters altogether.</span></span> <span data-ttu-id="a00de-117">如需有關資訊不被允許的字元編碼，請參閱[如何節點名稱字元編碼](../core/how-node-name-characters-get-encoded.md)。</span><span class="sxs-lookup"><span data-stu-id="a00de-117">For information about how disallowed characters are encoded, see [How Node Name Characters Get Encoded](../core/how-node-name-characters-get-encoded.md).</span></span>  
  
 <span data-ttu-id="a00de-118">除了節點名稱中不允許的字元編碼結構描述之 XSD 表示法中，除非您不應該使用 C# 保留字當作結構描述樹狀結構中任何根節點的名稱 (除非您提供有效**根節點TypeName**屬性值) 或結構描述檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a00de-118">In addition to the characters that are disallowed in node names, unless they are encoded in the XSD representation of the schema, you should not use C# reserved words as the names of any root nodes in the schema tree (unless you provide a valid **RootNode TypeName** property value) or as schema file names.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a00de-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="a00de-119">In This Section</span></span>  
  
-   [<span data-ttu-id="a00de-120">編碼哪些節點名稱字元</span><span class="sxs-lookup"><span data-stu-id="a00de-120">Which Node Name Characters Get Encoded</span></span>](../core/which-node-name-characters-get-encoded.md)  
  
-   [<span data-ttu-id="a00de-121">如何編碼節點名稱字元</span><span class="sxs-lookup"><span data-stu-id="a00de-121">How Node Name Characters Get Encoded</span></span>](../core/how-node-name-characters-get-encoded.md)