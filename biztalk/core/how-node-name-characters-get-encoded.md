---
title: "如何編碼節點名稱字元 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6462856b-7a52-40c9-9aff-c0579130eec9
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2d2c9410e56b2b50a32ec73ce5f49ae59909f59a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-node-name-characters-get-encoded"></a><span data-ttu-id="84162-102">如何編碼節點名稱字元</span><span class="sxs-lookup"><span data-stu-id="84162-102">How Node Name Characters Get Encoded</span></span>
<span data-ttu-id="84162-103">如果您使用節點名稱中不允許的字元，BizTalk 編輯器會提示您，詢問您是否要繼續進行，不允許的字元編碼 (**確定**或**取消**)。</span><span class="sxs-lookup"><span data-stu-id="84162-103">If you use a character that is not allowed in a node name, BizTalk Editor prompts you, asking if you want to proceed with the disallowed character or characters encoded (**OK** or **Cancel**).</span></span> <span data-ttu-id="84162-104">若您繼續進行，每個不被允許的字元將編碼如下：</span><span class="sxs-lookup"><span data-stu-id="84162-104">If you proceed, each disallowed character is encoded as follows:</span></span>  
  
-   <span data-ttu-id="84162-105">不允許的字元都會編碼為"_xDDDD\_"其中"DDDD"是 4 位數十六進位 Unicode 字元表示法。</span><span class="sxs-lookup"><span data-stu-id="84162-105">Disallowed characters are encoded as "_xDDDD\_" where "DDDD" is the 4-digit hexadecimal Unicode representation of the character.</span></span> <span data-ttu-id="84162-106">例如，空白字元 (0x0020) 會編碼為"_x0020\_"。</span><span class="sxs-lookup"><span data-stu-id="84162-106">For example, the space character (0x0020) is encoded as "_x0020\_".</span></span>  
  
-   <span data-ttu-id="84162-107">若編碼兩個或更多相鄰的不被允許字元，只會在它們之間使用單一底線字元。</span><span class="sxs-lookup"><span data-stu-id="84162-107">If two or more adjacent disallowed characters are encoded, only a single underscore character is used between them.</span></span> <span data-ttu-id="84162-108">例如，三個空格會編碼為"_x0020_x0020_x0020\_"而非"_x0020\__x0020\__x0020\_"。</span><span class="sxs-lookup"><span data-stu-id="84162-108">For example, three spaces are encoded as "_x0020_x0020_x0020\_" rather than "_x0020\__x0020\__x0020\_".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84162-109">您可以停用提示您輸入設定的節點名稱編碼**顯示編碼警告對話方塊**屬性**False**的 [BizTalk 編輯器] 資料夾中**選項**對話方塊中，用於**工具**功能表上，或選取**將來不要顯示此對話方塊**節點名稱編碼對話方塊中的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="84162-109">You can disable prompting for node name encoding by setting the **Show Encode Warning Dialog** property to **False** in the BizTalk Editor folder of the **Options** dialog box, available on the **Tools** menu, or by selecting the **Do not show this dialog in the future** check box in the node name encoding dialog box.</span></span> <span data-ttu-id="84162-110">如需有關此對話方塊中選項的詳細資訊，請參閱[管理結構描述樹狀結構檢視](../core/how-to-manage-the-schema-tree-view.md)。</span><span class="sxs-lookup"><span data-stu-id="84162-110">For more information about the options in this dialog box, see [Managing the Schema Tree View](../core/how-to-manage-the-schema-tree-view.md).</span></span>  
  
 <span data-ttu-id="84162-111">「BizTalk 編輯器」中的結構描述樹狀結構檢視會使用您輸入的字元顯示節點名稱。</span><span class="sxs-lookup"><span data-stu-id="84162-111">The schema tree view in BizTalk Editor displays node names by using the characters you type.</span></span> <span data-ttu-id="84162-112">「BizTalk 對應工具」也會顯示您已輸入的字元，而不顯示已編碼的版本。</span><span class="sxs-lookup"><span data-stu-id="84162-112">BizTalk Mapper also displays the characters you have typed rather than the encoded version.</span></span> <span data-ttu-id="84162-113">在 [BizTalk 編輯器] 的 XSD 檢視中與 XSD 檔案本身，會使用已編碼的節點名稱。</span><span class="sxs-lookup"><span data-stu-id="84162-113">In the XSD view of BizTalk Editor, and in the XSD file itself, the encoded node name is used.</span></span> <span data-ttu-id="84162-114">例如，若您將節點命名為 Purchase Order，則在「BizTalk 編輯器」與「BizTalk 對應工具」的結構描述樹狀結構中，均會顯示為 Purchase Order。</span><span class="sxs-lookup"><span data-stu-id="84162-114">For example, if you name a node Purchase Order, it will be displayed as Purchase Order in the schema trees in both BizTalk Editor and BizTalk Mapper.</span></span> <span data-ttu-id="84162-115">在 [BizTalk 編輯器] 的 XSD 檢視中，當您首次插入對應的項目節點時，它會顯示如下。</span><span class="sxs-lookup"><span data-stu-id="84162-115">In the XSD view of BizTalk Editor, the corresponding element node, when first inserted, will be as follows.</span></span>  
  
```  
<element name="Purchase_x0020_Order" type="xs:string />  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="84162-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84162-116">See Also</span></span>  
 <span data-ttu-id="84162-117">[節點名稱屬性](../core/node-name-property.md) </span><span class="sxs-lookup"><span data-stu-id="84162-117">[Node Name Property](../core/node-name-property.md) </span></span>  
 [<span data-ttu-id="84162-118">哪些節點名稱字元會進行編碼</span><span class="sxs-lookup"><span data-stu-id="84162-118">Which Node Name Characters Get Encoded</span></span>](../core/which-node-name-characters-get-encoded.md)