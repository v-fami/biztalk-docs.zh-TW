---
title: 建立連結 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maps, links
- BizTalk Mapper, links
ms.assetid: e8596c50-62e9-40a7-ad61-29cbdb4f4fc9
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87570b82dc63a02c629e0fc024c2e44d57df1401
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238566"
---
# <a name="creating-links"></a><span data-ttu-id="53540-102">建立連結</span><span class="sxs-lookup"><span data-stu-id="53540-102">Creating Links</span></span>
<span data-ttu-id="53540-103">BizTalk 對應工具可協助您自動化連結建立作業的部分項目。</span><span class="sxs-lookup"><span data-stu-id="53540-103">BizTalk Mapper helps you automate some elements involved in link creation.</span></span> <span data-ttu-id="53540-104">簡單連結建立作業與簡單資料型別相似。</span><span class="sxs-lookup"><span data-stu-id="53540-104">Simple link creation is similar to simple data types.</span></span> <span data-ttu-id="53540-105">更加複雜的連結建立作業形式則比較類似程式設計語言中的結構指派。</span><span class="sxs-lookup"><span data-stu-id="53540-105">There are more sophisticated forms of link creation that are more like structure assignment in a programming language.</span></span> <span data-ttu-id="53540-106">例如，指定如何從輸入執行個體訊息將資料的多個項目移至對應的輸出執行個體訊息的單一連結建立作業。</span><span class="sxs-lookup"><span data-stu-id="53540-106">An example is a single link creation that specifies how multiple items of data are to be moved from input instance messages to corresponding output instance messages.</span></span>  
  
 <span data-ttu-id="53540-107">使用下列方法建立連結：</span><span class="sxs-lookup"><span data-stu-id="53540-107">You create links using the following methods:</span></span>  
  
-   <span data-ttu-id="53540-108">**簡單連結建立作業。**</span><span class="sxs-lookup"><span data-stu-id="53540-108">**Simple link creation.**</span></span> <span data-ttu-id="53540-109">在簡單連結建立作業中，可藉由拖曳以產生連結。</span><span class="sxs-lookup"><span data-stu-id="53540-109">In simple link creation, you produce a link by dragging.</span></span> <span data-ttu-id="53540-110">將來源結構描述中的欄位拖曳至目的結構描述中的欄位，可在輸出執行個體訊息中建立項目或屬性，並將項目或屬性的值插入訊息中。</span><span class="sxs-lookup"><span data-stu-id="53540-110">Dragging a field in the source schema to a field in the destination schema causes the creation of an element or attribute in an output instance message and inserts the value of the element or attribute in the message.</span></span> <span data-ttu-id="53540-111">這類連結可以之間直接建立**記錄**和**欄位**來源和目的地結構描述中的節點或它們可以包含一或多個運算質之間的連結路徑中**記錄**和**欄位**來源和目的地結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="53540-111">Such links can be made directly between **Record** and **Field** nodes in the source and destination schema, or they can include one or more functoids in a link path between **Record** and **Field** nodes in the source and destination schemas.</span></span>  
  
-   <span data-ttu-id="53540-112">**結構連結。**</span><span class="sxs-lookup"><span data-stu-id="53540-112">**Structure links.**</span></span> <span data-ttu-id="53540-113">在建立結構連結時，您必須產生多個簡單連結之間同時**記錄**和**欄位**中擁有相同相對結構的來源和目的地結構描述的節點。</span><span class="sxs-lookup"><span data-stu-id="53540-113">In creating structure links, you produce multiple simple links at the same time between **Record** and **Field** nodes in the source and destination schemas that have the same relative structure.</span></span> <span data-ttu-id="53540-114">若要使用結構連結，則兩個結構描述相對部分的結構必須相同。</span><span class="sxs-lookup"><span data-stu-id="53540-114">To use structure linking, the structure of the relevant parts of the two schemas must be the same.</span></span> <span data-ttu-id="53540-115">如需有關設定結構連結的詳細資訊，請參閱[如何自動連結記錄](../core/how-to-link-records-automatically.md)。</span><span class="sxs-lookup"><span data-stu-id="53540-115">For more information about configuring structure links, see [How to Link Records Automatically](../core/how-to-link-records-automatically.md).</span></span>  
  
-   <span data-ttu-id="53540-116">**名稱相符連結。**</span><span class="sxs-lookup"><span data-stu-id="53540-116">**Name-matching links.**</span></span> <span data-ttu-id="53540-117">當您使用這個方法時，在相同的時間之間建立多個簡單連結**記錄**和**欄位**的名稱為基礎的來源和目的地結構描述中的節點**記錄**和**欄位**節點。</span><span class="sxs-lookup"><span data-stu-id="53540-117">When you use this method, you create multiple simple links at the same time between **Record** and **Field** nodes in the source and destination schemas based on the names of the **Records** and **Field** nodes.</span></span> <span data-ttu-id="53540-118">若要使用名稱相符連結，則來源與目的結構描述的結構必須非常相似，但並非完全相同。</span><span class="sxs-lookup"><span data-stu-id="53540-118">To use name-matching linking, the structure of the source and destination schemas must be very similar, but not exactly the same.</span></span> <span data-ttu-id="53540-119">如需設定名稱比對連結的詳細資訊，請參閱[如何自動連結記錄](../core/how-to-link-records-automatically.md)。</span><span class="sxs-lookup"><span data-stu-id="53540-119">For more information about configuring name-matching links, see [How to Link Records Automatically](../core/how-to-link-records-automatically.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="53540-120">您也可以查看[如何管理現有連結](../core/how-to-manage-existing-links.md)如需有關如何變更/修改現有的連結資訊。</span><span class="sxs-lookup"><span data-stu-id="53540-120">You can also see [How to Manage Existing Links](../core/how-to-manage-existing-links.md) for information about how to change/modify the existing links.</span></span>  
  
## <a name="preserving-whitespace-in-a-link"></a><span data-ttu-id="53540-121">保留連結中的空白字元</span><span class="sxs-lookup"><span data-stu-id="53540-121">Preserving Whitespace in a Link</span></span>  
 <span data-ttu-id="53540-122">如果您想要在對應至目標項目或運算質時保留來源項目中的空白字元，則需要撰寫自訂指令碼。</span><span class="sxs-lookup"><span data-stu-id="53540-122">If you want to preserve whitespace from a source element when mapping to a target element or functoid, you will need to write a custom script.</span></span>  
  
 <span data-ttu-id="53540-123">在對應工具或是執行階段系統中，不會保留空白字元。</span><span class="sxs-lookup"><span data-stu-id="53540-123">Whitespace is not preserved either in the Mapper or in the runtime system.</span></span> <span data-ttu-id="53540-124">對應工具與執行階段系統都使用 BTSXslTransform.Transform 來處理大量訊息的轉換，並透過 XPath 資料模型以便依賴 XmlReader 來瀏覽。</span><span class="sxs-lookup"><span data-stu-id="53540-124">Both the Mapper and the runtime system use BTSXslTransform.Transform which handles large-message transformations and relies on XmlReader to navigate using the XPath data model.</span></span>  
  
 <span data-ttu-id="53540-125">如需保留空白字元，您可以撰寫一份自訂指令碼來傳回所需的空白字元數。</span><span class="sxs-lookup"><span data-stu-id="53540-125">To preserve whitespace, you can write a custom script that returns the required amount of whitespace.</span></span> <span data-ttu-id="53540-126">例如，下列程式碼會永遠傳回一個包含 5 個空白字元的字串：</span><span class="sxs-lookup"><span data-stu-id="53540-126">For example, the code below always returns a string containing 5 whitespace characters:</span></span>  
  
```  
public string Whitespace(string param1)  
{  
  return "     ";  
}  
```  
  
 <span data-ttu-id="53540-127">如果您連結的來源項目到此指令碼和目標元素的輸入做為輸出，執行對應時，輸出項目會包含 5 個空白字元。</span><span class="sxs-lookup"><span data-stu-id="53540-127">If you link a source element to the input of this script and a target element as the output, when the map is executed, the output element will contain 5 whitespace characters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53540-128">如果您檢視輸出使用[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]，項目會出現空白。</span><span class="sxs-lookup"><span data-stu-id="53540-128">If you view the output using [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], the element will appear empty.</span></span> <span data-ttu-id="53540-129">這是因為 XML 檢視器會將僅包含空白字元的項目視為空白。</span><span class="sxs-lookup"><span data-stu-id="53540-129">This is because the XML viewer treats elements containing whitespace only as empty.</span></span> <span data-ttu-id="53540-130">若要查看空白字元，以滑鼠右鍵按一下 XML 檢視，然後選取**檢視原始檔**。</span><span class="sxs-lookup"><span data-stu-id="53540-130">To see the whitespace, right-click the XML view and select **View Source**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53540-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53540-131">See Also</span></span>  
 [<span data-ttu-id="53540-132">如何編輯連結屬性</span><span class="sxs-lookup"><span data-stu-id="53540-132">How to Edit Link Properties</span></span>](../core/how-to-edit-link-properties.md)