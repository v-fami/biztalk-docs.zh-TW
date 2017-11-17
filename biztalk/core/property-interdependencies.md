---
title: "屬性相互依存性 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ed5b75e-db1c-43d4-a287-fc4cd1c529f5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15e1a02d82d294c63a33c0682e77585a7934b8ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="property-interdependencies"></a><span data-ttu-id="8b7d8-102">屬性相互依存性</span><span class="sxs-lookup"><span data-stu-id="8b7d8-102">Property Interdependencies</span></span>

## <a name="overview"></a><span data-ttu-id="8b7d8-103">概觀</span><span class="sxs-lookup"><span data-stu-id="8b7d8-103">Overview</span></span>
<span data-ttu-id="8b7d8-104">當您使用「BizTalk 編輯器」，尤其是使用 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗變更屬性值時，會發現屬性之間有相當多的相互依存性。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-104">As you use BizTalk Editor, and specifically the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, to change the values of properties, you will notice that there are extensive interdependencies between properties.</span></span> <span data-ttu-id="8b7d8-105">有時，某個屬性的特定設定會造成其他屬性自動清除、啟用或停用，甚至從 [屬性] 視窗完全顯示或消失。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-105">Sometimes a particular setting for one property will cause other properties to be automatically cleared, become enabled or disabled, or even appear or disappear entirely from the Properties window.</span></span> <span data-ttu-id="8b7d8-106">這些相互依存性為數眾多，無法完全涵蓋。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-106">These interdependencies are too numerous to cover.</span></span> 

<span data-ttu-id="8b7d8-107">不過，下列清單提供了部分常見的範例，讓您對這些相互依存性的運作方式有所瞭解：</span><span class="sxs-lookup"><span data-stu-id="8b7d8-107">However, the following list provides some common examples to give you an idea of how they work:</span></span>  
  
-   <span data-ttu-id="8b7d8-108">設定的屬性時**欄位項目**節點或**欄位屬性**節點的資料類型衍生自簡單型別使用限制機制的整個新類別屬性會變成可用：**限制**。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-108">When setting the properties of a **Field Element** node or **Field Attribute** node for which a data type is being derived from a simple type by using the restriction mechanism, an entire new category of properties becomes available: **Restriction**.</span></span> <span data-ttu-id="8b7d8-109">另外，此新類別中的屬性會根據基底資料型別為字串型別或數字型別而啟用或停用。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-109">Further, the properties in this new category are enabled or disabled based on whether the base data type is of a string type or a numeric type.</span></span> <span data-ttu-id="8b7d8-110">如需這種形式的簡單型別衍生的詳細資訊，請參閱[簡單類型衍生使用限制機制](../core/simple-type-derivation-using-the-restriction-mechanism.md)。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-110">For more information about this form of simple type derivation, see [Simple Type Derivation Using the Restriction Mechanism](../core/simple-type-derivation-using-the-restriction-mechanism.md).</span></span>  
  
-   <span data-ttu-id="8b7d8-111">設定的屬性時**欄位項目**節點或**欄位屬性**節點的資料類型衍生自簡單型別使用清單或聯集機制，**基底資料型別**屬性變更為**項目類型**屬性或**成員型別**屬性，分別。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-111">When setting the properties of a **Field Element** node or **Field Attribute** node for which a data type is being derived from a simple type by using either the list or union mechanism, the **Base Data Type** property is changed to either the **Item Type** property or the **Member Types** property, respectively.</span></span> <span data-ttu-id="8b7d8-112">在後者情況下，對應的下拉式清單會修改為包含核取方塊，允許選取多個型別。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-112">In the latter case, the corresponding drop-down list is modified to include check boxes, allowing multiple types to be selected.</span></span> <span data-ttu-id="8b7d8-113">如需有關這些簡單型別衍生的表單的詳細資訊，請參閱[簡單類型衍生使用清單機制](../core/simple-type-derivation-using-the-list-mechanism.md)和[簡單類型衍生使用聯集機制](../core/simple-type-derivation-using-the-union-mechanism.md)。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-113">For more information about these forms of simple type derivation, see [Simple Type Derivation Using the List Mechanism](../core/simple-type-derivation-using-the-list-mechanism.md) and [Simple Type Derivation Using the Union Mechanism](../core/simple-type-derivation-using-the-union-mechanism.md).</span></span>  
  
-   <span data-ttu-id="8b7d8-114">若要公開與一般檔案結構描述相關聯的屬性，您必須設定**Schema Editor Extensions**屬性**結構描述**要包含的節點**一般檔案延伸模組**.</span><span class="sxs-lookup"><span data-stu-id="8b7d8-114">To expose the properties associated with flat file schemas, you must set the **Schema Editor Extensions** property of the **Schema** node to include the **Flat File Extension**.</span></span> <span data-ttu-id="8b7d8-115">與其他編輯器延伸模組，例如 EDI 延伸模組相關聯的自訂屬性會公開相同的方式： 選擇對應的延伸模組使用**Schema Editor Extensions**屬性。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-115">The custom properties associated with other editor extensions, such as the EDI extension, are exposed in the same way: by choosing the corresponding extension using the **Schema Editor Extensions** property.</span></span>  
  
 <span data-ttu-id="8b7d8-116">此清單所包含的範例是為了說明您在 [屬性] 視窗中會看到的屬性相互依存性類型，但並非這類相互依存性的詳細清單。</span><span class="sxs-lookup"><span data-stu-id="8b7d8-116">This list includes examples that are meant to illustrate the types of property interdependencies that you will see when working within the Properties window, but it is not meant to be an exhaustive list of such interdependencies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7d8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b7d8-117">See Also</span></span>  
-  [<span data-ttu-id="8b7d8-118">節點屬性</span><span class="sxs-lookup"><span data-stu-id="8b7d8-118">Node Properties</span></span>](../core/node-properties.md)   
-  <span data-ttu-id="8b7d8-119">下列屬性[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="8b7d8-119">The following properties [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>
    -  <span data-ttu-id="8b7d8-120">節點屬性的字母順序清單</span><span class="sxs-lookup"><span data-stu-id="8b7d8-120">Node Properties Alphabetical Listings</span></span>
    -  <span data-ttu-id="8b7d8-121">所有結構描述的節點屬性</span><span class="sxs-lookup"><span data-stu-id="8b7d8-121">Node Properties of All Schemas</span></span> 
    -  <span data-ttu-id="8b7d8-122">結構描述編輯器延伸模組</span><span class="sxs-lookup"><span data-stu-id="8b7d8-122">Schema Editor Extensions</span></span>