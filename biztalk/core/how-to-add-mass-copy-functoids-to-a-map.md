---
title: 如何新增大量複製運算質至對應 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1cff63fc-8f34-4bd0-8501-a8401bde6349
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 52d79dc07c884d284fe4f6985453b86bb91b0660
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022140"
---
# <a name="how-to-add-mass-copy-functoids-to-a-map"></a><span data-ttu-id="7db57-102">如何將大量複製運算質新增至對應</span><span class="sxs-lookup"><span data-stu-id="7db57-102">How to Add Mass Copy Functoids to a Map</span></span>
<span data-ttu-id="7db57-103">**大量複製**運算質可讓您使用包含的結構描述的對應**任何**並**anyAttribute**項目。</span><span class="sxs-lookup"><span data-stu-id="7db57-103">The **Mass Copy** functoid enables your maps to use schemas that include **any** and **anyAttribute** elements.</span></span> <span data-ttu-id="7db57-104">這些項目實際上是在 XML 結構描述定義語言中提供的萬用字元，以符合未知的結構或屬性集。</span><span class="sxs-lookup"><span data-stu-id="7db57-104">These elements are, in essence, wildcards provided in the XML Schema definition language to match unknown structures or sets of attributes.</span></span>  
  
 <span data-ttu-id="7db57-105">如需概念性資訊**大量複製**運算質，請參閱[大量複製運算質](../core/mass-copy-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="7db57-105">For conceptual information about the **Mass Copy** functoid, see [Mass Copy Functoid](../core/mass-copy-functoid.md).</span></span>  
  
### <a name="to-add-the-mass-copy-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="7db57-106">將大量複製運算質新增至對應並加以設定</span><span class="sxs-lookup"><span data-stu-id="7db57-106">To add the Mass Copy functoid to a map and configure it</span></span>  
  
1. <span data-ttu-id="7db57-107">具有[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)][工具箱]，按一下 [**進階運算質**来選取該運算質類別索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7db57-107">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
    <span data-ttu-id="7db57-108">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="7db57-108">The list of advanced functoids in the chosen category appears.</span></span>  
  
2. <span data-ttu-id="7db57-109">拖曳**大量複製**運算質 (![](../core/media/advmasscopy.gif "advmasscopy")) 從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="7db57-109">Drag the **Mass Copy** functoid (![](../core/media/advmasscopy.gif "advmasscopy")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7db57-110">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="7db57-110">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="7db57-111">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="7db57-111">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7db57-112">若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="7db57-112">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="7db57-113">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="7db57-113">Functoids are executed from left to right.</span></span> <span data-ttu-id="7db57-114">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="7db57-114">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3. <span data-ttu-id="7db57-115">若要建立的輸入的參數**大量複製**運算質建立輸入的連結，從來源結構描述拖曳記錄**大量複製**運算質，或拖曳**大量複製**運算質將來源結構描述中的記錄。</span><span class="sxs-lookup"><span data-stu-id="7db57-115">To establish the input parameter for the **Mass Copy** functoid, create an input link by dragging a record from the source schema to the **Mass Copy** functoid, or dragging the **Mass Copy** functoid to a record in the source schema.</span></span>  
  
4. <span data-ttu-id="7db57-116">若要使用的輸出參數**大量複製**運算質，建立輸出連結，藉由拖曳**大量複製**」 運算質至目的結構描述，或將記錄拖曳至目的結構描述中的記錄**大量複製**運算質。</span><span class="sxs-lookup"><span data-stu-id="7db57-116">To use the output parameter from the **Mass Copy** functoid, create an output link by dragging the **Mass Copy** functoid to a record in the destination schema, or by dragging a record in the destination schema to the **Mass Copy** functoid.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="7db57-117">不同於其他運算質中，您無法使用的輸出**大量複製**運算質，做為另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="7db57-117">Unlike other functoids, you cannot use the output of the **Mass Copy** functoid as input to another functoid.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7db57-118">您可以插入並設定**大量複製**藉由兩個連結的運算質會直接記錄。</span><span class="sxs-lookup"><span data-stu-id="7db57-118">You can insert and configure the **Mass Copy** functoid by linking two records directly.</span></span> <span data-ttu-id="7db57-119">如需詳細資訊，請參閱 < 使用大量複製運算質的連結 」 一節中[如何自動連結記錄](../core/how-to-link-records-automatically.md)。</span><span class="sxs-lookup"><span data-stu-id="7db57-119">For more information, see the section “To link using a mass copy functoid” in [How to Link Records Automatically](../core/how-to-link-records-automatically.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db57-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7db57-120">See Also</span></span>  
 [<span data-ttu-id="7db57-121">將進階運算質新增至對應</span><span class="sxs-lookup"><span data-stu-id="7db57-121">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)