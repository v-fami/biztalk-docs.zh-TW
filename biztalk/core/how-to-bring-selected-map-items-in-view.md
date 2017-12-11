---
title: "如何將選取的對應項目在檢視 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e287b22-5738-428a-aa35-cced877e51ea
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1dff8e981b65b6b91c744ce26648a5f4e06adea
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-bring-selected-map-items-in-view"></a><span data-ttu-id="b362e-102">如何在檢視中顯示選取的對應項目</span><span class="sxs-lookup"><span data-stu-id="b362e-102">How to Bring Selected Map Items in View</span></span>
<span data-ttu-id="b362e-103">使用舊版的 BizTalk 對應工具時，如果對應包含大型的結構描述，您必須手動捲動來源結構描述窗格、格線頁和目標結構描述窗格，才能在單一檢視中包含所有相關的對應項目。</span><span class="sxs-lookup"><span data-stu-id="b362e-103">With earlier versions of BizTalk Mapper, if a map comprised big schemas, you had to manually scroll the source schema pane, the grid page, and the target schema pane to bring all the relevant map items into a single view.</span></span> <span data-ttu-id="b362e-104">BizTalk Server 與 BizTalk 對應工具可讓您選取的運算質/連結的所有相關對應項目帶入自動捲動格線頁的單一檢視。</span><span class="sxs-lookup"><span data-stu-id="b362e-104">The BizTalk Mapper with BizTalk Server allows you to bring all the relevant map items of the selected functoid/link into a single view by automatically scrolling the grid page.</span></span> <span data-ttu-id="b362e-105">本主題提供如何執行此作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b362e-105">This topic provides information about how to perform the operation.</span></span>  
  
 <span data-ttu-id="b362e-106">依據您的選項 (來源結構描述節點、關係檢視中的元素或目標結構描述節點) 而定，BizTalk 對應工具會以同步方式自動捲動結構描述檢視與關係檢視，並顯示所選項目的整體關係檢視。</span><span class="sxs-lookup"><span data-stu-id="b362e-106">Depending on your selection (a source schema node, an element in the relationship view, or a target schema node), the BizTalk Mapper auto-scrolls the schema views and relationship view in a synchronized fashion, and displays the overall relationship view of the selected item.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b362e-107">自動捲動功能要在 BizTalk 對應工具反白所有相關的對應項目後才會生效。</span><span class="sxs-lookup"><span data-stu-id="b362e-107">The auto-scroll feature comes into effect after the BizTalk Mapper has emphasized all the relevant map items.</span></span> <span data-ttu-id="b362e-108">換句話說，首先要反白與選項相關的元素，BizTalk 對應工具才會自動捲動以將相關的元素包含在檢視中。</span><span class="sxs-lookup"><span data-stu-id="b362e-108">In other words, first the elements related to the selection are highlighted, and then the BizTalk Mapper auto-scrolls to bring the related elements into view.</span></span>  
  
 <span data-ttu-id="b362e-109">BizTalk 對應工具實際上不會移動格線物件。</span><span class="sxs-lookup"><span data-stu-id="b362e-109">The BizTalk Mapper does not actually move the grid objects.</span></span> <span data-ttu-id="b362e-110">當您移除或修改選項時，格線物件會回到它們各自的位置。</span><span class="sxs-lookup"><span data-stu-id="b362e-110">The grid objects return to their respective locations when you remove or modify the selection.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b362e-111">必要條件</span><span class="sxs-lookup"><span data-stu-id="b362e-111">Prerequisites</span></span>  
 <span data-ttu-id="b362e-112">此作業需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="b362e-112">This operation requires that BizTalk Mapper is running.</span></span>  
  
### <a name="to-bring-the-selected-map-items-in-view"></a><span data-ttu-id="b362e-113">將所選對應項目包含在檢視中</span><span class="sxs-lookup"><span data-stu-id="b362e-113">To bring the selected map items in view</span></span>  
  
1.  <span data-ttu-id="b362e-114">在對應工具公用程式功能區中，按一下自動捲動圖示![自動 &#45; 捲動圖示](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll")以將它關閉。</span><span class="sxs-lookup"><span data-stu-id="b362e-114">On the Mapper utility ribbon, click the auto-scroll icon ![Auto&#45;scroll icon](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") to switch it OFF.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b362e-115">![自動 &#45; 捲動圖示](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll")切換圖示依預設關閉。</span><span class="sxs-lookup"><span data-stu-id="b362e-115">The ![Auto&#45;scroll icon](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") icon is switched OFF by default.</span></span>  
  
2.  <span data-ttu-id="b362e-116">按一下運算質或連結，就會反白關係中的相關對應項目。</span><span class="sxs-lookup"><span data-stu-id="b362e-116">Click a functoid or a link; the relevant map items in the relationship are emphasized.</span></span>  
  
     <span data-ttu-id="b362e-117">下圖以藍色顯示選取的連結。</span><span class="sxs-lookup"><span data-stu-id="b362e-117">The following figure displays the selected link in blue color.</span></span> <span data-ttu-id="b362e-118">接著，BizTalk 對應工具會強調其他對應項目中的選取範圍，綠色相關。</span><span class="sxs-lookup"><span data-stu-id="b362e-118">In turn, BizTalk Mapper emphasizes the other map items relevant to the selection, in green color.</span></span> <span data-ttu-id="b362e-119">在下圖中，您可以看到所選關係的所有元素雖已反白，卻未顯示於目前的檢視中。</span><span class="sxs-lookup"><span data-stu-id="b362e-119">From the figure, you can see that all the elements of the selected relationship, though emphasized, are completely not in the current view.</span></span>  
  
     <span data-ttu-id="b362e-120">![連結時自動 &#45; 捲動關閉](../core/media/autoscroll-switchoff.gif "AutoScroll_SwitchOff")</span><span class="sxs-lookup"><span data-stu-id="b362e-120">![Links when auto&#45;scrolling is switched off](../core/media/autoscroll-switchoff.gif "AutoScroll_SwitchOff")</span></span>  
  
3.  <span data-ttu-id="b362e-121">按一下自動捲動圖示![自動 &#45; 捲動圖示](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll")以將它開啟。</span><span class="sxs-lookup"><span data-stu-id="b362e-121">Click the auto-scroll icon ![Auto&#45;scroll icon](../core/media/mapper-intelliscroll.gif "Mapper_IntelliScroll") to switch it ON.</span></span>  
  
     <span data-ttu-id="b362e-122">BizTalk 對應工具會自動捲動，以將選項中所有相關的項目包含在目前的對應檢視中。</span><span class="sxs-lookup"><span data-stu-id="b362e-122">The BizTalk Mapper automatically scrolls to bring all the relevant items in the selection into the current map view.</span></span>  
  
     <span data-ttu-id="b362e-123">![開啟自動捲動時檢視](../core/media/autoscroll-switchon.gif "AutoScroll_SwitchOn")</span><span class="sxs-lookup"><span data-stu-id="b362e-123">![View when autoscrolling is switched on](../core/media/autoscroll-switchon.gif "AutoScroll_SwitchOn")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b362e-124">或者，您也可以按鍵盤的 CTRL+M、CTRL+U。</span><span class="sxs-lookup"><span data-stu-id="b362e-124">Alternatively, you can press CTRL+M, CTRL+U from the keyboard.</span></span> <span data-ttu-id="b362e-125">如需對應工具鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="b362e-125">For a list of Mapper keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b362e-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="b362e-126">See Also</span></span>  
 [<span data-ttu-id="b362e-127">在 BizTalk 對應工具中使用增強功能</span><span class="sxs-lookup"><span data-stu-id="b362e-127">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)