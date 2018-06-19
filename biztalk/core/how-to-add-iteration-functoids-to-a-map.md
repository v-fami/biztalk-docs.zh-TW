---
title: 如何新增反覆項目運算質至對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1eaea929-e352-447d-b119-bd69b6b24e6c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2df7cda082a9a85e54e1dce427d73ea15d8f920
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247030"
---
# <a name="how-to-add-iteration-functoids-to-a-map"></a><span data-ttu-id="adff7-102">如何新增重複項目運算質至對應</span><span class="sxs-lookup"><span data-stu-id="adff7-102">How to Add Iteration Functoids to a Map</span></span>
<span data-ttu-id="adff7-103">**反覆項目**運算質的輸出中迴圈的目前記錄的索引結構，在第一筆記錄，而第二個資料錄，2 的 1 開始等等。</span><span class="sxs-lookup"><span data-stu-id="adff7-103">The **Iteration** functoid outputs the index of the current record in a looping structure, beginning at 1 for the first record, 2 for the second record, and so on.</span></span>  
  
 <span data-ttu-id="adff7-104">如需概念資訊**反覆項目**運算質，請參閱[反覆項目運算質](../core/iteration-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="adff7-104">For conceptual information about the **Iteration** functoid, see [Iteration Functoid](../core/iteration-functoid.md).</span></span>  
  
### <a name="to-add-the-index-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="adff7-105">新增索引運算質至對應並加以設定</span><span class="sxs-lookup"><span data-stu-id="adff7-105">To add the Index functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="adff7-106">與[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱作用中，按一下**進階運算質**索引標籤，選取該運算質類別。</span><span class="sxs-lookup"><span data-stu-id="adff7-106">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="adff7-107">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="adff7-107">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="adff7-108">拖曳**索引**運算質 (![](../core/media/bts-tls-iteration.gif "bts_tls_iteration")) 從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="adff7-108">Drag the **Index** functoid (![](../core/media/bts-tls-iteration.gif "bts_tls_iteration")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="adff7-109">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="adff7-109">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="adff7-110">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="adff7-110">If you want to put the functoid onto a different grid page, you need to display that other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="adff7-111">若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="adff7-111">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="adff7-112">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="adff7-112">Functoids are executed from left to right.</span></span> <span data-ttu-id="adff7-113">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="adff7-113">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="adff7-114">若要建立的迴圈記錄輸入的參數**反覆項目**運算質，迴圈記錄拖曳至來源結構描述建立輸入的連結**反覆項目**運算質，或藉由拖曳**反覆項目**運算質到來源結構描述中迴圈記錄。</span><span class="sxs-lookup"><span data-stu-id="adff7-114">To establish the looping record input parameter for the **Iteration** functoid, create an input link by dragging a looping record from the source schema to the **Iteration** functoid, or by dragging the **Iteration** functoid to a looping record in the source schema.</span></span>  
  
4.  <span data-ttu-id="adff7-115">若要使用的輸出參數**反覆項目**運算質，拖曳以建立輸出連結**反覆項目**欄位與目的結構描述中，或是將目的結構描述中的欄位拖曳到運算質**反覆項目**運算質。</span><span class="sxs-lookup"><span data-stu-id="adff7-115">To use the output parameter from the **Iteration** functoid, create an output link by dragging the **Iteration** functoid to a field in the destination schema, or by dragging a field in the destination schema to the **Iteration** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="adff7-116">在目的結構描述的對應欄位的資料類型必須是數值或可轉換為數值，使其符合的輸出資料型別**反覆項目**運算質。</span><span class="sxs-lookup"><span data-stu-id="adff7-116">The data type of the relevant field in the destination schema must be numeric or convertible to numeric so that it matches the output data type of the **Iteration** functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adff7-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adff7-117">See Also</span></span>  
 [<span data-ttu-id="adff7-118">新增進階運算質至對應</span><span class="sxs-lookup"><span data-stu-id="adff7-118">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)