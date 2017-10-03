---
title: "合併 XML 文件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML, documents
- process management solution tutorial, merging XML documents
ms.assetid: 444c983a-397a-4342-85e1-80bb152986d9
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94684cd9bf1992a592efd7b97c46838c9c9a3134
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="merging-xml-documents"></a><span data-ttu-id="8714f-102">合併 XML 文件</span><span class="sxs-lookup"><span data-stu-id="8714f-102">Merging XML Documents</span></span>
<span data-ttu-id="8714f-103">其中一個訊息， **OrderBroker**協調流程會建立一個 SQL Server 歷程記錄資料庫更新。</span><span class="sxs-lookup"><span data-stu-id="8714f-103">One of the messages that the **OrderBroker** orchestration creates is one to update the SQL Server history database.</span></span> <span data-ttu-id="8714f-104">此訊息包含來自訂單訊息的欄位，以及原始訂單訊息。</span><span class="sxs-lookup"><span data-stu-id="8714f-104">This message contains fields from the order message as well as the original order message.</span></span> <span data-ttu-id="8714f-105">原始訂單會在此訊息中以字串顯示。</span><span class="sxs-lookup"><span data-stu-id="8714f-105">The original order appears in this message a string.</span></span> <span data-ttu-id="8714f-106">這符合資料庫中訂單歷程記錄的資料型別。</span><span class="sxs-lookup"><span data-stu-id="8714f-106">This matches the data type for the order history in the database.</span></span>  
  
 <span data-ttu-id="8714f-107">取得訊息、將它轉換為字串，並利用對應將它放置於另一個訊息中，是不可能做到的。</span><span class="sxs-lookup"><span data-stu-id="8714f-107">It isn't possible to take a message, convert it to a string, and place it in another message with a map.</span></span> <span data-ttu-id="8714f-108">協調流程會使用 helper 函式， **InsertOrderBody**，若要將原始訂單訊息為字串加入至基底歷程記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="8714f-108">The orchestration uses a helper function, **InsertOrderBody**, to add the original order message as a string to the base history message.</span></span>  
  
 <span data-ttu-id="8714f-109">**OrderBroker**協調流程會使用對應， **CSR_OrderRequest_To_SQLHistoryInsert**，以將訂單訊息轉換成基底歷程記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="8714f-109">The **OrderBroker** orchestration uses the map, **CSR_OrderRequest_To_SQLHistoryInsert**, to convert the order message into the base history message.</span></span> <span data-ttu-id="8714f-110">訂單的資訊會顯示為屬性**OrderLog**項目。</span><span class="sxs-lookup"><span data-stu-id="8714f-110">The information for an order appears as attributes of an **OrderLog** element.</span></span> <span data-ttu-id="8714f-111">原始訊息則會顯示為此項目的另一個屬性。</span><span class="sxs-lookup"><span data-stu-id="8714f-111">The original message appears as another attribute of this element.</span></span>  
  
 <span data-ttu-id="8714f-112">**InsertOrderBody**方法做為引數，會採用原始訂單訊息、 基底歷程記錄訊息，並傳回完成的歷程記錄訊息。</span><span class="sxs-lookup"><span data-stu-id="8714f-112">The **InsertOrderBody** method takes as arguments the original order message, the base history message, and returns the completed history message.</span></span> <span data-ttu-id="8714f-113">下列程式碼會顯示將訊息當成字串插入之方法的一部分：</span><span class="sxs-lookup"><span data-stu-id="8714f-113">The following code shows the portions of the method that inserts the message as a string:</span></span>  
  
```  
public static XmlDocument InsertOrderBody( XmlDocument orderDoc,   
                                    XmlDocument historyInsertDoc)  
{  
...  
    XmlNode root = historyInsertDoc.FirstChild;  
  
    //Create a new attribute.  
    XmlNode attr = historyInsertDoc.CreateNode(XmlNodeType.Attribute,  
                                     "OriginalMsg", root.NamespaceURI);  
    attr.Value = orderDoc.OuterXml;  
  
    try  
    {  
        // XPath expression not shown for formatting reasons and  
        // replaces ".." in the following code  
        XmlNode destnode = historyInsertDoc.SelectSingleNode("..");  
        //Add the attribute to the document.  
        destnode.Attributes.SetNamedItem(attr);  
    }  
...  
  
    return historyInsertDoc;  
}  
```  
  
 <span data-ttu-id="8714f-114">在確認收到兩個引數之後, **InsertOrderBody**方法會尋找歷程記錄更新訊息的根節點。</span><span class="sxs-lookup"><span data-stu-id="8714f-114">After verifying that it received both arguments, the **InsertOrderBody** method finds the root node of the history update message.</span></span> <span data-ttu-id="8714f-115">然後它會建立一個節點，其中包含**OriginalMsg**屬性，並將原始訂單訊息指派給屬性的值。</span><span class="sxs-lookup"><span data-stu-id="8714f-115">It then creates a node containing the **OriginalMsg** attribute and assigns the original order message to the attribute's value.</span></span> <span data-ttu-id="8714f-116">此時，節點只是存在而已。</span><span class="sxs-lookup"><span data-stu-id="8714f-116">At this point, the node simply exists.</span></span> <span data-ttu-id="8714f-117">還不是項目的一部分。</span><span class="sxs-lookup"><span data-stu-id="8714f-117">It is not yet part of a element.</span></span>  
  
 <span data-ttu-id="8714f-118">在建立屬性節點之後，此方法會尋找將使用 XPath 運算式來附加屬性的節點。</span><span class="sxs-lookup"><span data-stu-id="8714f-118">After creating the attribute node, the method finds the node where it will attach the attribute using an XPath expression.</span></span> <span data-ttu-id="8714f-119">找到該節點之後，此方法會將屬性節點加入至該節點的屬性集合中。</span><span class="sxs-lookup"><span data-stu-id="8714f-119">After it locates the node, the method adds the attribute node to the attributes collection of the node.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8714f-120">雖然**OriginalMsg**屬性一開始沒有基底歷程記錄訊息中，它是，當然，結構描述中指定。</span><span class="sxs-lookup"><span data-stu-id="8714f-120">Although the **OriginalMsg** attribute does not initially exist in the base history message, it is, of course, specified in the schema.</span></span> <span data-ttu-id="8714f-121">在程式碼中加入至訊息的 XML 項目，應該在那些訊息的結構描述中予以指定。</span><span class="sxs-lookup"><span data-stu-id="8714f-121">XML elements that you add to your messages in code should be specified in the schemas for those messages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8714f-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8714f-122">See Also</span></span>  
 [<span data-ttu-id="8714f-123">商務程序管理解決方案的實作重點</span><span class="sxs-lookup"><span data-stu-id="8714f-123">Implementation Highlights of the Business Process Management Solution</span></span>](../core/implementation-highlights-of-the-business-process-management-solution.md)