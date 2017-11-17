---
title: "信封結構描述 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: af296c30-95dc-4fef-9aa3-bea2f2cd8caf
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 03c44f1a5d9797ec09cc164789148287c98b4399
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="envelope-schemas"></a><span data-ttu-id="0125d-102">信封結構描述</span><span class="sxs-lookup"><span data-stu-id="0125d-102">Envelope Schemas</span></span>

## <a name="overview"></a><span data-ttu-id="0125d-103">概觀</span><span class="sxs-lookup"><span data-stu-id="0125d-103">Overview</span></span>
<span data-ttu-id="0125d-104">您可以使用和建立商務文件的 XML 結構描述一樣的方式，來建立信封結構描述。</span><span class="sxs-lookup"><span data-stu-id="0125d-104">You can create an envelope schema in all of the same ways that you can create an XML schema for a business document.</span></span> <span data-ttu-id="0125d-105">您可以從格式正確的 XML 信封執行個體訊息、「文件類型定義」(DTD) 或信封結構描述的 XML-Data Reduced (XDR) 表示法建立結構描述。</span><span class="sxs-lookup"><span data-stu-id="0125d-105">You can create a schema from a well-formed XML envelope instance message, or from Document Type Definition (DTD) or XML-Data reduced (XDR) representations of the envelope schema.</span></span> <span data-ttu-id="0125d-106">或者，您可以結合或不結合其他結構描述，來建立新的結構描述。</span><span class="sxs-lookup"><span data-stu-id="0125d-106">Or, you can create a new schema, either in conjunction with other schemas or not.</span></span> <span data-ttu-id="0125d-107">由於信封結構描述通常較大多數商務文件結構描述小且簡單，因此建立新的信封結構描述通常是一種可行的替代方法。</span><span class="sxs-lookup"><span data-stu-id="0125d-107">Because envelope schemas are generally much smaller and less complicated than most business document schemas, creating new envelope schemas is usually a viable alternative.</span></span>  
  
 <span data-ttu-id="0125d-108">若要定義為信封結構描述的結構描述，您需要設定**信封**屬性**結構描述**節點的值**是**。</span><span class="sxs-lookup"><span data-stu-id="0125d-108">To define a schema as an envelope schema, you need to set the **Envelope** property of the **Schema** node to the value **Yes**.</span></span> <span data-ttu-id="0125d-109">當您定義信封結構描述時，您應該指向信封的**Body XPath**送給父節點僅包含\<任何 > 子元素。</span><span class="sxs-lookup"><span data-stu-id="0125d-109">When you define an envelope schema, you should point the envelope's **Body XPath** to the parent node that contains only the \<any> child element.</span></span> <span data-ttu-id="0125d-110">為了讓 XML 組合器能夠使用信封，父節點不可包含任何其他項目。</span><span class="sxs-lookup"><span data-stu-id="0125d-110">In order for the XML assembler to use the envelope, the parent node must not contain any other elements.</span></span>  
  
 <span data-ttu-id="0125d-111">當您將**信封**屬性**是**，它表示實際訊息內容 （稱為訊息內文） 的 XML 執行個體訊息的某處存在於根**記錄**這個結構描述中所指定的節點**Body XPath**該節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="0125d-111">When you set **Envelope** property to **Yes**, it means that the actual message content of the XML instance message (called the body of the message) is present somewhere inside the root **Record** node of this schema, as specified by the **Body XPath** property of that node.</span></span> <span data-ttu-id="0125d-112">因此，您也必須根據下列各種條件，設定其他的屬性：</span><span class="sxs-lookup"><span data-stu-id="0125d-112">Therefore, you must also set additional properties based on a variety of conditions:</span></span>  
  
-   <span data-ttu-id="0125d-113">如果信封結構描述具有單一根節點，您必須設定**Body XPath**該根的屬性。</span><span class="sxs-lookup"><span data-stu-id="0125d-113">If an envelope schema has a single root, you must set the **Body XPath** property for that root.</span></span>  
  
-   <span data-ttu-id="0125d-114">若信封結構描述具有多重根目錄和**根參考**屬性未設定，您必須設定**Body XPath**所有根節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="0125d-114">If an envelope schema has multiple roots and the **Root Reference** property is not set, you must set the **Body XPath** property for all roots.</span></span>  
  
-   <span data-ttu-id="0125d-115">若信封結構描述具有多重根目錄和**根參考**屬性時，您必須設定**Body XPath**屬性對應根**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="0125d-115">If an envelope schema has multiple roots and the **Root Reference** property is set, you must set the **Body XPath** property of the corresponding root **Record** node.</span></span> <span data-ttu-id="0125d-116">您可以選擇設定**Body XPath**剩餘根節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="0125d-116">You can optionally set the **Body XPath** property for the remaining roots.</span></span>  
  
-   <span data-ttu-id="0125d-117">不論信封結構描述是否有單一根節點或多個根節點，設定**[根參考**不是必要屬性。</span><span class="sxs-lookup"><span data-stu-id="0125d-117">Regardless of whether an envelope schema has a single root or multiple roots, setting the **[Root Reference** property is not required.</span></span>  

<span data-ttu-id="0125d-118">這些屬性的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="0125d-118">More details on these properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="0125d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0125d-119">See Also</span></span>  
 <span data-ttu-id="0125d-120">[不同類型的 BizTalk 結構描述](../core/different-types-of-biztalk-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="0125d-120">[Different Types of BizTalk Schemas](../core/different-types-of-biztalk-schemas.md) </span></span>  
 [<span data-ttu-id="0125d-121">如何建立信封的結構描述</span><span class="sxs-lookup"><span data-stu-id="0125d-121">How to Create Schemas for Envelopes</span></span>](../core/how-to-create-schemas-for-envelopes.md)