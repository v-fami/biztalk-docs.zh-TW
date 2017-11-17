---
title: "使用複雜全域型別的方式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ddea1c7b-eb0e-4521-8576-0ea6f9460847
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f84b8b872d047a62a913514a695b4bba2d482c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ways-to-use-complex-global-types"></a><span data-ttu-id="a5b6f-102">使用複雜全域型別的方式</span><span class="sxs-lookup"><span data-stu-id="a5b6f-102">Ways to Use Complex Global Types</span></span>
<span data-ttu-id="a5b6f-103">在您將複雜型別轉換為全域複雜型別之後，它就可以在結構描述的其他位置中重複使用。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-103">After you have converted a complex type to a global complex type, it becomes available for reuse in other locations within your schema.</span></span> <span data-ttu-id="a5b6f-104">如需有關定義複雜類型，而且再將它轉換成全域複雜類型的詳細資訊，請參閱[複雜全域型別定義和命名](../core/complex-global-type-definition-and-naming.md)。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-104">For more information about defining a complex type and then converting it to a global complex type, see [Complex Global Type Definition and Naming](../core/complex-global-type-definition-and-naming.md).</span></span>  
  
 <span data-ttu-id="a5b6f-105">首先，插入新**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-105">First, you insert a new **Record** node.</span></span> <span data-ttu-id="a5b6f-106">接著選取插入的節點，並在 [屬性] 視窗中設定下列兩個節點屬性的其中之一，每個屬性都有不同的效果：</span><span class="sxs-lookup"><span data-stu-id="a5b6f-106">Then you select the inserted node and set one of the following two node properties in the Properties window, each for a different effect:</span></span>  
  
-   <span data-ttu-id="a5b6f-107">**資料結構型別屬性**。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-107">**Data Structure Type property**.</span></span> <span data-ttu-id="a5b6f-108">若您想要使用複雜全域型別且完全不修改，請將此屬性設定成您為複雜全域型別指定的型別名稱，它可以在下拉式清單中做為選項使用。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-108">If you want to use the complex global type without modifying it in any way, set this property to the type name you gave to the complex global type, which is available as a choice in the drop-down list.</span></span> <span data-ttu-id="a5b6f-109">在結構描述樹狀結構中，選擇的全域節點結構將會在新位置中以圖形化的方式複製，而且在結構描述樹狀結構的任何位置中，對節點結構的任何後續變更，會自動套用到使用該複雜全域型別的所有位置。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-109">In the schema tree, the chosen global node structure will be graphically duplicated in the new location, and any subsequent changes to the node structure in any of its locations in the schema tree are automatically made to all locations that use that complex global type.</span></span>  
  
-   <span data-ttu-id="a5b6f-110">**基底資料型別屬性**。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-110">**Base Data Type property**.</span></span> <span data-ttu-id="a5b6f-111">如果您想要使用複雜全域型別上的一種，將它擴充或限制在某些方面，請您為複雜全域型別，也就是可從下拉式清單中選擇的型別名稱來設定此屬性。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-111">If you want to use a variation on the complex global type, either extending it or restricting it in some way, set this property to the type name you gave to the complex global type, which is available as a choice in the drop-down list.</span></span> <span data-ttu-id="a5b6f-112">當您設定此屬性， **Derived By**節點屬性變更為**延伸**(和**內容類型**屬性變更為**ComplexContent**)，表示延伸複雜全域型別是預設的衍生類型。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-112">When you set this property, the **Derived By** node property changes to **Extension** (and the **Content Type** property changes to **ComplexContent**), indicating that extending the complex global type is the default derivation type.</span></span> <span data-ttu-id="a5b6f-113">您可以將它變更為**限制**如果您的修改屬於該本質。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-113">You can change it to **Restriction** if your modifications are of that nature.</span></span> <span data-ttu-id="a5b6f-114">在您進行衍生的基底複雜全域型別中的變更，會自動反映在衍生的型別中，但是在衍生型別中的變更永遠不會反映在基底型別中。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-114">Changes to the base complex global type from which you are deriving are automatically reflected in the derived type, but changes in the derived type are never reflected in the base type.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5b6f-115">設定這些屬性的其中一個會自動造成其他屬性移除任何現有的設定。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-115">Setting either one of these properties automatically causes the other one to have any existing setting removed.</span></span> <span data-ttu-id="a5b6f-116">此外，您會注意到其他的之間的關聯的屬性，例如設定自動互動**Derived By**屬性**（預設）**移除任何現有的設定，從**基底資料型別**屬性。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-116">Further, you will notice other automatic interactions between the related properties, such as setting the **Derived By** property to **(Default)** removes any existing setting from the **Base Data Type** property.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5b6f-117">您可以建立測試結構描述並使用這些屬性的不同值，以觀察 XSD 檢視中的變更。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-117">You can create a test schema and use different values for these properties, observing the changes in the XSD view.</span></span>  
  
 <span data-ttu-id="a5b6f-118">本節描述如何藉由延伸和限制方式使用複雜全域型別，而這兩種方式都是由本主題中描述的屬性設定來控制。</span><span class="sxs-lookup"><span data-stu-id="a5b6f-118">This section describes using complex global types, both as is, and by extending and restricting them, as controlled by the settings of the properties described in this topic.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a5b6f-119">本節內容</span><span class="sxs-lookup"><span data-stu-id="a5b6f-119">In This Section</span></span>  
  
-   [<span data-ttu-id="a5b6f-120">複雜全域型別重複使用</span><span class="sxs-lookup"><span data-stu-id="a5b6f-120">Complex Global Type Re-use</span></span>](../core/complex-global-type-re-use.md)  
  
-   [<span data-ttu-id="a5b6f-121">複雜全域型別衍生</span><span class="sxs-lookup"><span data-stu-id="a5b6f-121">Complex Global Type Derivation</span></span>](../core/complex-global-type-derivation.md)