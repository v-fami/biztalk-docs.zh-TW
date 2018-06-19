---
title: 如何新增記錄計數運算質至對應 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fbfd2a0-fac5-49f1-bcbb-873c287cd278
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cd315a637b3efd069361dfa2d780cff179559da3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247662"
---
# <a name="how-to-add-record-count-functoids-to-a-map"></a><span data-ttu-id="1f86e-102">如何將記錄計數運算質新增至對應</span><span class="sxs-lookup"><span data-stu-id="1f86e-102">How to Add Record Count Functoids to a Map</span></span>
<span data-ttu-id="1f86e-103">**記錄計數**運算質可讓您產生執行個體訊息中的一筆記錄發生次數的計數。</span><span class="sxs-lookup"><span data-stu-id="1f86e-103">The **Record Count** functoid enables you to generate a count of the number of times a record occurs in an instance message.</span></span>  
  
 <span data-ttu-id="1f86e-104">如需概念資訊**記錄計數**運算質，請參閱[記錄計數運算質](../core/record-count-functoid.md)。</span><span class="sxs-lookup"><span data-stu-id="1f86e-104">For conceptual information about the **Record Count** functoid, see [Record Count Functoid](../core/record-count-functoid.md).</span></span>  
  
### <a name="to-add-the-record-count-functoid-to-a-map-and-configure-it"></a><span data-ttu-id="1f86e-105">新增記錄計數運算質至對應並設定</span><span class="sxs-lookup"><span data-stu-id="1f86e-105">To add the Record Count functoid to a map and configure it</span></span>  
  
1.  <span data-ttu-id="1f86e-106">與[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]工具箱作用中，按一下**進階運算質**索引標籤，選取該運算質類別。</span><span class="sxs-lookup"><span data-stu-id="1f86e-106">With the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Toolbox active, click the **Advanced Functoids** tab to select that category of functoids.</span></span>  
  
     <span data-ttu-id="1f86e-107">顯示所選類別中的進階運算質清單。</span><span class="sxs-lookup"><span data-stu-id="1f86e-107">The list of advanced functoids in the chosen category appears.</span></span>  
  
2.  <span data-ttu-id="1f86e-108">拖曳**記錄計數**運算質 (![](../core/media/bts-tls-recordcount.gif "bts_tls_recordcount")) 從工具箱拖曳至格線頁上的適當位置。</span><span class="sxs-lookup"><span data-stu-id="1f86e-108">Drag the **Record Count** functoid (![](../core/media/bts-tls-recordcount.gif "bts_tls_recordcount")) from the Toolbox to the appropriate location on a grid page.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1f86e-109">運算質將放置在顯示的格線頁上。</span><span class="sxs-lookup"><span data-stu-id="1f86e-109">The functoid will be placed on the displayed grid page.</span></span> <span data-ttu-id="1f86e-110">若要將運算質放在其他格線頁上，必須先顯示該格線頁。</span><span class="sxs-lookup"><span data-stu-id="1f86e-110">If you want to put the functoid onto a different grid page, you need to display the other grid page first.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1f86e-111">若您同時使用一個以上的運算質來建構對應，您必須考慮其左右相對位置。</span><span class="sxs-lookup"><span data-stu-id="1f86e-111">If you are constructing a map using more than one functoid together, you need to consider their relative left to right placement.</span></span> <span data-ttu-id="1f86e-112">運算質是由左至右執行。</span><span class="sxs-lookup"><span data-stu-id="1f86e-112">Functoids are executed from left to right.</span></span> <span data-ttu-id="1f86e-113">某個運算質的輸出，只能是其較右邊另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="1f86e-113">The output of a functoid can only be input to another functoid that is farther to the right.</span></span>  
  
3.  <span data-ttu-id="1f86e-114">若要建立的輸入的參數**記錄計數**運算質，迴圈記錄拖曳至來源結構描述建立輸入的連結**記錄計數**運算質，或拖曳**記錄計數**運算質到來源結構描述中迴圈記錄。</span><span class="sxs-lookup"><span data-stu-id="1f86e-114">To establish the input parameter for the **Record Count** functoid, create an input link by dragging a looping record from the source schema to the **Record Count** functoid, or dragging the **Record Count** functoid to a looping record in the source schema.</span></span>  
  
4.  <span data-ttu-id="1f86e-115">若要使用的輸出參數**記錄計數**運算質，拖曳以建立輸出連結**記錄計數**運算質至目的結構描述，或將欄位拖曳目的地中的欄位結構描述以**記錄計數**運算質。</span><span class="sxs-lookup"><span data-stu-id="1f86e-115">To use the output parameter from the **Record Count** functoid, create an output link by dragging the **Record Count** functoid to a field in the destination schema, or by dragging a field in the destination schema to the **Record Count** functoid.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1f86e-116">與其他運算質的輸出**記錄計數**運算質可用做為另一個運算質的輸入。</span><span class="sxs-lookup"><span data-stu-id="1f86e-116">As with other functoids, the output of the **Record Count** functoid can be used as input to another functoid.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f86e-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f86e-117">See Also</span></span>  
 [<span data-ttu-id="1f86e-118">新增進階運算質至對應</span><span class="sxs-lookup"><span data-stu-id="1f86e-118">Adding Advanced Functoids to a Map</span></span>](../core/adding-advanced-functoids-to-a-map.md)