---
title: 如何新增值對應運算質至對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc70067a-67a1-4a0e-95e5-b0cb327d2cee
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 47e463489332c3a1d2887dab5f7bd734fdd20af5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247838"
---
# <a name="how-to-add-value-mapping-functoids-to-a-map"></a><span data-ttu-id="65394-102">如何新增值對應運算質至對應</span><span class="sxs-lookup"><span data-stu-id="65394-102">How to Add Value Mapping Functoids to a Map</span></span>
<span data-ttu-id="65394-103">**值對應**運算質會傳回其第二個參數的值，如果第一個參數為 true。</span><span class="sxs-lookup"><span data-stu-id="65394-103">The **Value Mapping** functoid returns the value of its second parameter if its first parameter is true.</span></span> <span data-ttu-id="65394-104">運算質的一般用途是將欄位的屬性變更為記錄的屬性。</span><span class="sxs-lookup"><span data-stu-id="65394-104">A common use of the functoid is to change the attributes of a field into the attributes of a record.</span></span>  
  
 <span data-ttu-id="65394-105">如需概念資訊**值對應**運算質，請參閱[值對應運算質](../core/value-mapping-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="65394-105">For conceptual information about the **Value Mapping** functoid, see [Value Mapping Functoid](../core/value-mapping-functoid.md).</span></span>  
  
### <a name="to-add-the-value-mapping-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="65394-106">新增值對應運算質至對應並進行設定</span><span class="sxs-lookup"><span data-stu-id="65394-106">To add the Value Mapping functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="65394-107">與[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱作用中，按一下**進階運算質**索引標籤，選取該運算質類別。</span><span class="sxs-lookup"><span data-stu-id="65394-107">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="65394-108">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="65394-108">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="65394-109">拖曳**值對應**運算質 (![](../core/media/bts-tls-valmap.gif "bts_tls_valmap")) 從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="65394-109">Drag the **Value Mapping** functoid (![](../core/media/bts-tls-valmap.gif "bts_tls_valmap")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65394-110">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="65394-110">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="65394-111">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="65394-111">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65394-112">若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="65394-112">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="65394-113">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="65394-113">Functoids are executed from left to right.</span></span> <span data-ttu-id="65394-114">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="65394-114">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="65394-115">若要建立的第一個輸入的參數**值對應**運算質，拖曳以建立輸入的連結**值對應**來源結構描述中的記錄或欄位節點或另一個運算質到運算質其左邊，具有布林資料類型，而且，將會產生"true"或"false"的輸入的值。</span><span class="sxs-lookup"><span data-stu-id="65394-115">To establish the first input parameter for the **Value Mapping** functoid, create an input link by dragging the **Value Mapping** functoid to a record or field node in the source schema, or to another functoid to its left, that has a Boolean data type and that will produce an input value of "true" or "false".</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65394-116">您也可以拖曳以相反的方向，將布林值的來源拖曳**值對應**運算質。</span><span class="sxs-lookup"><span data-stu-id="65394-116">You can also drag in the opposite direction, dragging the source of the Boolean value to the **Value Mapping** functoid.</span></span>  
  
4.  <span data-ttu-id="65394-117">若要建立的第二個輸入的參數**值對應**運算質，拖曳以建立輸入的連結**值對應**記錄或欄位節點來源結構描述，或將記錄拖曳運算質來源結構描述中的 [欄位] 節點或**值對應**運算質。</span><span class="sxs-lookup"><span data-stu-id="65394-117">To establish the second input parameter for the **Value Mapping** functoid, create an input link by dragging the **Value Mapping** functoid to a record or field node in the source schema, or by dragging a record or field node in the source schema to the **Value Mapping** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65394-118">第二個輸入參數來**值對應**運算質也可以從另一個運算質的輸出的左側。</span><span class="sxs-lookup"><span data-stu-id="65394-118">The second input parameter to the **Value Mapping** functoid can also be from the output of another functoid to its left.</span></span> <span data-ttu-id="65394-119">藉由將其中一個相關運算質拖曳到其他相關運算質，建立代表這類輸入來源的連結。</span><span class="sxs-lookup"><span data-stu-id="65394-119">Create the links that represent such sources of input by dragging one of the relevant functoids to the other relevant functoid.</span></span>  
  
5.  <span data-ttu-id="65394-120">若要使用的輸出參數**值對應**運算質，拖曳以建立輸出連結**值對應**的記錄或欄位與目的結構描述，或是拖曳記錄欄位的運算質目的地結構描述為**值對應**運算質。</span><span class="sxs-lookup"><span data-stu-id="65394-120">To use the output parameter from the **Value Mapping** functoid, create an output link by dragging the **Value Mapping** functoid to a record or field in the destination schema, or by dragging a record field in the destination schema to the **Value Mapping** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="65394-121">與其他運算質的輸出**值對應**運算質可做為另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="65394-121">As with other functoids, the output of the **Value Mapping** functoid can serve as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65394-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65394-122">See Also</span></span>  
 [<span data-ttu-id="65394-123">新增進階運算質至對應</span><span class="sxs-lookup"><span data-stu-id="65394-123">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)