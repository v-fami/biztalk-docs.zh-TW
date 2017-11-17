---
title: "如何開啟、 儲存、 關閉和重新命名對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aa88ca7-a731-4295-8692-6dd36fdf0872
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bad04c72e4c3f0caf1af8e223d3f17e4687b736
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-open-save-close-and-rename-maps"></a><span data-ttu-id="bff78-102">如何開啟、儲存、關閉和重新命名對應</span><span class="sxs-lookup"><span data-stu-id="bff78-102">How to Open, Save, Close, and Rename Maps</span></span>
<span data-ttu-id="bff78-103">在 Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，對應為檔案系統中存在的檔案以.btm 為副檔名。</span><span class="sxs-lookup"><span data-stu-id="bff78-103">In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], maps exist as files in the file system with .btm extensions.</span></span> <span data-ttu-id="bff78-104">不過，更常見的狀況是將對應作為 BizTalk 專案中的項目使用，您可以從 BizTalk 專案中執行如開啟、儲存和關閉對應等作業。</span><span class="sxs-lookup"><span data-stu-id="bff78-104">Nevertheless, it is much more common to work with maps as items in a BizTalk project, from which you perform operations such as opening, saving, and closing maps.</span></span>  
  
### <a name="to-open-a-map"></a><span data-ttu-id="bff78-105">開啟對應</span><span class="sxs-lookup"><span data-stu-id="bff78-105">To open a map</span></span>  
  
1.  <span data-ttu-id="bff78-106">在 [方案總管] 中，選取要開啟的對應。</span><span class="sxs-lookup"><span data-stu-id="bff78-106">In Solution Explorer, select the map you want to open.</span></span>  
  
2.  <span data-ttu-id="bff78-107">在**檢視**功能表上，按一下 **開啟**。</span><span class="sxs-lookup"><span data-stu-id="bff78-107">On the **View** menu, click **Open**.</span></span>  
  
     <span data-ttu-id="bff78-108">對應就會在 BizTalk 對應工具中開啟。</span><span class="sxs-lookup"><span data-stu-id="bff78-108">The map opens in BizTalk Mapper.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bff78-109">您可以也以滑鼠右鍵按一下 [方案總管] 中的對應，然後按一下**開啟**，或直接按兩下 [方案總管] 中的對應。</span><span class="sxs-lookup"><span data-stu-id="bff78-109">You can also right-click the map in Solution Explorer, and then click **Open**, or simply double-click the map in Solution Explorer.</span></span>  
  
### <a name="to-save-a-map"></a><span data-ttu-id="bff78-110">儲存對應</span><span class="sxs-lookup"><span data-stu-id="bff78-110">To save a map</span></span>  
  
1.  <span data-ttu-id="bff78-111">在 [方案總管] 中，選取要儲存的對應。</span><span class="sxs-lookup"><span data-stu-id="bff78-111">In Solution Explorer, select the map you want to save.</span></span>  
  
2.  <span data-ttu-id="bff78-112">在**檔案**功能表上，按一下 **儲存*\<名稱的對應 >***。</span><span class="sxs-lookup"><span data-stu-id="bff78-112">On the **File** menu, click **Save *\<Name of Map>***.</span></span>  
  
### <a name="to-save-a-map-to-a-new-location"></a><span data-ttu-id="bff78-113">將對應儲存至新位置</span><span class="sxs-lookup"><span data-stu-id="bff78-113">To save a map to a new location</span></span>  
  
1.  <span data-ttu-id="bff78-114">在 [方案總管] 中，選取要儲存至新位置的對應。</span><span class="sxs-lookup"><span data-stu-id="bff78-114">In Solution Explorer, select the map you want to save to a new location.</span></span>  
  
2.  <span data-ttu-id="bff78-115">在**檔案**功能表上，按一下 **儲存*\<名稱的對應 >*為**。</span><span class="sxs-lookup"><span data-stu-id="bff78-115">On the **File** menu, click **Save *\<Name of Map>* As**.</span></span>  
  
3.  <span data-ttu-id="bff78-116">在**另存新檔**對話方塊中，瀏覽至您要儲存對應的資料夾位置。</span><span class="sxs-lookup"><span data-stu-id="bff78-116">In the **Save File As** dialog box, browse to the folder location where you want to save the map.</span></span>  
  
4.  <span data-ttu-id="bff78-117">在**檔案名稱**方塊中，輸入檔案的名稱，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="bff78-117">In the **File name** box, type a name for the file, and then click **Save**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="bff78-118">請勿使用下列對應名稱："XmlContent"、"SourceSchemas"、"TargetSchemas" 或 "XsltArgumentListContent"；若使用這些名稱將導致對應的 .NET 組件中產生的 C# 程式碼發生編譯問題。</span><span class="sxs-lookup"><span data-stu-id="bff78-118">Do not use the following names for maps: "XmlContent", "SourceSchemas", "TargetSchemas", or "XsltArgumentListContent"; doing so will cause compilation problems in the generated C# code in the corresponding .NET assembly.</span></span> <span data-ttu-id="bff78-119">如需問題和解決方法資訊，請參閱[疑難排解對應](../core/troubleshooting-maps.md)。</span><span class="sxs-lookup"><span data-stu-id="bff78-119">For information about issues and their resolution, see [Troubleshooting Maps](../core/troubleshooting-maps.md).</span></span>  
  
### <a name="to-rename-a-map"></a><span data-ttu-id="bff78-120">重新命名對應</span><span class="sxs-lookup"><span data-stu-id="bff78-120">To rename a map</span></span>  
  
1.  <span data-ttu-id="bff78-121">在 [方案總管] 中，以滑鼠右鍵按一下您想要重新命名，然後按一下對應**重新命名**。</span><span class="sxs-lookup"><span data-stu-id="bff78-121">In Solution Explorer, right-click the map that you want to rename, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="bff78-122">在 [方案總管] 中對應所在位置出現的 [編輯] 方塊中，輸入對應的新名稱，或改變它的現有名稱，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="bff78-122">In the editing box that appears in the location of the map in Solution Explorer, type the new name for the map, or alter its existing name, and then press ENTER.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bff78-123">您也可能想要變更**型別名稱**時將它重新命名對應。</span><span class="sxs-lookup"><span data-stu-id="bff78-123">You may also want to change the **Type Name** of the map when you rename it.</span></span> <span data-ttu-id="bff78-124">您變更**型別名稱**選取**對應**在 方案總管 並輸入新的名稱在**型別名稱**屬性 視窗中。</span><span class="sxs-lookup"><span data-stu-id="bff78-124">You change the **Type Name** by selecting the **map** in the solution explorer and entering the new name in the **Type Name** in the Properties window.</span></span>  
  
#### <a name="to-close-a-map"></a><span data-ttu-id="bff78-125">關閉對應</span><span class="sxs-lookup"><span data-stu-id="bff78-125">To close a map</span></span>  
  
1.  <span data-ttu-id="bff78-126">在 [方案總管] 中，選取要關閉的對應。</span><span class="sxs-lookup"><span data-stu-id="bff78-126">In Solution Explorer, select the map you want to close.</span></span>  
  
2.  <span data-ttu-id="bff78-127">在 **[檔案]** 功能表上按一下 **[關閉]**。</span><span class="sxs-lookup"><span data-stu-id="bff78-127">On the **File** menu, click **Close**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bff78-128">您也可以按一下關閉圖示 ([**x**]) 的 Microsoft 右上角[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]編輯視窗。</span><span class="sxs-lookup"><span data-stu-id="bff78-128">You can also click the close icon ([**x**]) in the upper-right corner of the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bff78-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bff78-129">See Also</span></span>  
 [<span data-ttu-id="bff78-130">管理專案中的對應</span><span class="sxs-lookup"><span data-stu-id="bff78-130">Managing Maps Within Projects</span></span>](../core/managing-maps-within-projects.md)