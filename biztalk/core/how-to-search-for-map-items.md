---
title: 如何搜尋對應項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.mapper.search
ms.assetid: 3dbb089a-6aa8-4921-a82d-81d3a193e933
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ee61bccfae53a79d8fba6bd0aa5af2c537d98270
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255534"
---
# <a name="how-to-search-for-map-items"></a><span data-ttu-id="8342e-102">如何搜尋對應項目</span><span class="sxs-lookup"><span data-stu-id="8342e-102">How to Search for Map Items</span></span>
<span data-ttu-id="8342e-103">BizTalk 對應工具可讓您搜尋來源結構描述、目的結構描述與格線介面中的項目。</span><span class="sxs-lookup"><span data-stu-id="8342e-103">The BizTalk Mapper enables you to search for items in the source schema, the destination schema, and the grid surface.</span></span> <span data-ttu-id="8342e-104">本主題提供如何執行此作業的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8342e-104">This topic provides information about how to perform this operation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8342e-105">必要條件</span><span class="sxs-lookup"><span data-stu-id="8342e-105">Prerequisites</span></span>  
 <span data-ttu-id="8342e-106">這些指示需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="8342e-106">These instructions require that BizTalk Mapper is running.</span></span>  
  
## <a name="to-search-for-items"></a><span data-ttu-id="8342e-107">搜尋項目</span><span class="sxs-lookup"><span data-stu-id="8342e-107">To search for items</span></span>  
 <span data-ttu-id="8342e-108">選取要搜尋的結構描述。</span><span class="sxs-lookup"><span data-stu-id="8342e-108">Select the schema where you want to search.</span></span> <span data-ttu-id="8342e-109">如果選取來源結構描述，BizTalk 對應工具只會在來源結構描述中搜尋。</span><span class="sxs-lookup"><span data-stu-id="8342e-109">If you select source schema, the BizTalk Mapper searches and looks for the match only in the source schema.</span></span> <span data-ttu-id="8342e-110">但是，您可以同時選取來源和目的結構描述。</span><span class="sxs-lookup"><span data-stu-id="8342e-110">However, you can select both source and destination schemas.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8342e-111">為確認選項，請尋找結構描述或結構描述項目前面的標記。</span><span class="sxs-lookup"><span data-stu-id="8342e-111">To confirm selection, look for the mark before the schema or the schema item.</span></span>  
  
 <span data-ttu-id="8342e-112">![搜尋對應項目](../core/media/searching-map-items.gif "Searching_map_items")</span><span class="sxs-lookup"><span data-stu-id="8342e-112">![Searching for map items](../core/media/searching-map-items.gif "Searching_map_items")</span></span>  
  
 <span data-ttu-id="8342e-113">在**搜尋**對應工具公用程式功能區上的方塊中，輸入您想要搜尋的項目名稱。</span><span class="sxs-lookup"><span data-stu-id="8342e-113">In the **Search** box on the Mapper utility ribbon, type the name of the item you want to search.</span></span> <span data-ttu-id="8342e-114">您可以在來源或目的結構描述的節點名稱中，以及運算質的名稱、標籤、註解、輸入或指令碼中搜尋字串。</span><span class="sxs-lookup"><span data-stu-id="8342e-114">You can search for a string in the name of a node in the source or destination schema, as well as in the name, label, comment, inputs, or scripts for functoids.</span></span>  
  
 <span data-ttu-id="8342e-115">當您輸入搜尋字串時，系統會反白符合搜尋條件的物件。</span><span class="sxs-lookup"><span data-stu-id="8342e-115">As you enter the search string, the objects that meet the search criteria are highlighted.</span></span> <span data-ttu-id="8342e-116">您可以再周遊搜尋結果中使用的箭頭按鍵在鍵盤上或![在清單中向上移動](../core/media/move-up-button.gif "Move_up_button")和![清單中向下移動](../core/media/move-down-button.gif "Move_down_button")公用程式功能區上的圖示。</span><span class="sxs-lookup"><span data-stu-id="8342e-116">You can then traverse through the search results either using the arrow keys on the keyboard or the ![Move up in the list](../core/media/move-up-button.gif "Move_up_button") and ![Moving down in a list](../core/media/move-down-button.gif "Move_down_button") icons on the utility ribbon.</span></span> <span data-ttu-id="8342e-117">如果搜尋結果分佈在三個檢視中，會以來源結構描述、關係檢視和目的結構描述的順序顯示搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="8342e-117">If the search results are spread across all three views, the search results are traversed in the order of the source schema, relationship view, and the destination schema.</span></span> <span data-ttu-id="8342e-118">之後經過搜尋結果，您可以關閉搜尋刪除搜尋字串，或按一下 (![清除對應工具搜尋](../core/media/mapper-search-cancel.gif "Mapper_Search_Cancel")) 搜尋字串旁的圖示。</span><span class="sxs-lookup"><span data-stu-id="8342e-118">After going through the search results, you can close the search either by deleting the search string or by clicking the (![Clear Mapper search](../core/media/mapper-search-cancel.gif "Mapper_Search_Cancel")) icon next to the search string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8342e-119">您也可以按 CTRL+M、CTRL+J/CTRL+M、CTRL+K 來前/後周遊搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="8342e-119">You can also press CTRL+M, CTRL+J or CTRL+M, CTRL+K to traverse through the search results upwards or downwards, respectively.</span></span> <span data-ttu-id="8342e-120">如需對應工具鍵盤快速鍵的清單，請參閱[BizTalk 對應工具鍵盤快速鍵](../core/biztalk-mapper-keyboard-shortcuts.md)。</span><span class="sxs-lookup"><span data-stu-id="8342e-120">For a list of Mapper keyboard shortcuts, see [BizTalk Mapper Keyboard Shortcuts](../core/biztalk-mapper-keyboard-shortcuts.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8342e-121">如果在單一對應檢視中看不到關係檢視的搜尋結果，BizTalk 對應工具會顯示指向其他搜尋結果的閃爍箭號。</span><span class="sxs-lookup"><span data-stu-id="8342e-121">If the search results for the relationship view are not visible in a single map view, the BizTalk Mapper displays blinking arrows in the direction where there are additional hits.</span></span> <span data-ttu-id="8342e-122">例如，向上箭號圖示 (![其他搜尋結果方向](../core/media/mapper-search-direction.gif "Mapper_Search_Direction")) 代表有可以向上捲動以檢視其他搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="8342e-122">For example, the top arrow icon (![Direction for additional search results](../core/media/mapper-search-direction.gif "Mapper_Search_Direction")) denotes that there are additional search results that can be viewed by scrolling up.</span></span> <span data-ttu-id="8342e-123">同樣地，若搜尋結果位於不同的對應頁面，則系統會以黃色反白顯示那些頁面的頁面索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8342e-123">Similarly, if there are search results in different map pages, the page tabs for those pages are highlighted, in yellow.</span></span> <span data-ttu-id="8342e-124">將滑鼠指標移反白顯示的頁面，在工具提示會顯示在該頁面上的搜尋相符項目數目。</span><span class="sxs-lookup"><span data-stu-id="8342e-124">On moving the mouse over the highlighted page, the tooltip displays the number of search matches on that page.</span></span> <span data-ttu-id="8342e-125">狀態列會顯示搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="8342e-125">The status bar displays the search results.</span></span>  
  
 <span data-ttu-id="8342e-126">![狀態列顯示搜尋結果](../core/media/searching-map-items-statusbar.jpg "Searching_map_items_statusbar")</span><span class="sxs-lookup"><span data-stu-id="8342e-126">![Status bar displaying the search results](../core/media/searching-map-items-statusbar.jpg "Searching_map_items_statusbar")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8342e-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8342e-127">See Also</span></span>  
 [<span data-ttu-id="8342e-128">使用 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="8342e-128">Using BizTalk Mapper</span></span>](../core/using-biztalk-mapper.md)