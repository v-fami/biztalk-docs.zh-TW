---
title: 如何在本機伺服器上檢視組件和類型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6ddf6f60-9fef-4997-8b42-24eefd7ab0d1
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37c0f49559de7c4b1a13982578478cf249520479
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257318"
---
# <a name="how-to-view-assemblies-and-types-on-the-local-server"></a><span data-ttu-id="06a43-102">如何在本機伺服器上檢視組件和類型</span><span class="sxs-lookup"><span data-stu-id="06a43-102">How to View Assemblies and Types on the Local Server</span></span>
<span data-ttu-id="06a43-103">您可以使用「BizTalk 組件檢視工具」，檢視在本機伺服器上安裝的所有 BizTalk 組件和類型。</span><span class="sxs-lookup"><span data-stu-id="06a43-103">You can use the BizTalk Assembly Viewer to examine all BizTalk assemblies and types installed on the local server.</span></span>  
  
### <a name="to-view-all-biztalk-server-assemblies-installed-in-the-gac"></a><span data-ttu-id="06a43-104">若要檢視 GAC 中安裝的所有 BizTalk Server 組件</span><span class="sxs-lookup"><span data-stu-id="06a43-104">To view all BizTalk Server assemblies installed in the GAC</span></span>  
  
-   <span data-ttu-id="06a43-105">若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。</span><span class="sxs-lookup"><span data-stu-id="06a43-105">To open the BizTalk Assembly Viewer, double-click **My Computer**, and then double-click **BizTalk Server Assemblies**.</span></span>  
  
     <span data-ttu-id="06a43-106">安裝在電腦上全域組件快取 (GAC) 中的所有 BizTalk 組件隨即出現。</span><span class="sxs-lookup"><span data-stu-id="06a43-106">All BizTalk assemblies installed in the global assembly cache (GAC) on the computer appear.</span></span>  
  
     ![](../core/media/ebiz-deply-asblyvieweropenpage.gif "ebiz_deply_asblyvieweropenpage")  
<span data-ttu-id="06a43-107">組件檢視工具開啟頁面</span><span class="sxs-lookup"><span data-stu-id="06a43-107">Assembly Viewer open page</span></span>  
  
### <a name="to-view-types-attributes-and-references-for-a-biztalk-assembly"></a><span data-ttu-id="06a43-108">若要檢視 BizTalk 組件的類型、屬性與參考</span><span class="sxs-lookup"><span data-stu-id="06a43-108">To view types, attributes, and references for a BizTalk assembly</span></span>  
  
1.  <span data-ttu-id="06a43-109">若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。</span><span class="sxs-lookup"><span data-stu-id="06a43-109">To open the BizTalk Assembly Viewer, double-click **My Computer**, and then double-click **BizTalk Server Assemblies**.</span></span>  
  
2.  <span data-ttu-id="06a43-110">按兩下適當的組件。</span><span class="sxs-lookup"><span data-stu-id="06a43-110">Double click the appropriate assembly.</span></span>  
  
     <span data-ttu-id="06a43-111">在右邊窗格中會顯示 BizTalk 組件類型，</span><span class="sxs-lookup"><span data-stu-id="06a43-111">The BizTalk assembly types appear in the right pane.</span></span> <span data-ttu-id="06a43-112">而左邊窗格中則會顯示屬性和型別。</span><span class="sxs-lookup"><span data-stu-id="06a43-112">The attributes and types appear in the left pane.</span></span>  
  
     <span data-ttu-id="06a43-113">您也可以按一下瀏覽至已安裝的組件位置**程式碼基底**左上區段的 [工作] 窗格中的連結。</span><span class="sxs-lookup"><span data-stu-id="06a43-113">You can also navigate to the installed location of the assembly by clicking the **Codebase** link in the upper left section of the task pane.</span></span> <span data-ttu-id="06a43-114">(當 [Windows 檔案總管] 處於 [資料夾] 檢視模式時，無法檢視這個連結，因為資料夾清單會取代工作窗格)。</span><span class="sxs-lookup"><span data-stu-id="06a43-114">(You cannot view this link when Windows Explorer is in Folder view because the task pane is replaced by the folder list.)</span></span>  
  
### <a name="to-view-the-contents-of-a-type-in-a-biztalk-assembly"></a><span data-ttu-id="06a43-115">若要檢視 BizTalk Server 組件中的型別內容</span><span class="sxs-lookup"><span data-stu-id="06a43-115">To view the contents of a type in a BizTalk assembly</span></span>  
  
1.  <span data-ttu-id="06a43-116">若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。</span><span class="sxs-lookup"><span data-stu-id="06a43-116">To open the BizTalk Assembly Viewer, double-click **My Computer**, and then double-click **BizTalk Server Assemblies**.</span></span>  
  
2.  <span data-ttu-id="06a43-117">按兩下適當的組件。</span><span class="sxs-lookup"><span data-stu-id="06a43-117">Double click the appropriate assembly.</span></span>  
  
3.  <span data-ttu-id="06a43-118">在右邊窗格中，按兩下適當的型別。</span><span class="sxs-lookup"><span data-stu-id="06a43-118">In the right pane, double-click the appropriate type.</span></span>  
  
     <span data-ttu-id="06a43-119">**型別內容檢視器**視窗隨即開啟，並出現 XML 定義。</span><span class="sxs-lookup"><span data-stu-id="06a43-119">The **Type Content Viewer** window opens and the XML definition appears.</span></span>  
  
### <a name="to-add-a-biztalk-assembly-in-the-gac"></a><span data-ttu-id="06a43-120">若要在 GAC 中加入 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="06a43-120">To add a BizTalk assembly in the GAC</span></span>  
  
1.  <span data-ttu-id="06a43-121">若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。</span><span class="sxs-lookup"><span data-stu-id="06a43-121">To open the BizTalk Assembly Viewer, double-click **My Computer**, and then double-click **BizTalk Server Assemblies**.</span></span>  
  
2.  <span data-ttu-id="06a43-122">使用 [Windows 檔案總管]，巡覽到要加入至 GAC 中的組件。</span><span class="sxs-lookup"><span data-stu-id="06a43-122">Use Windows Explorer to navigate to the assembly that you want to add in the GAC.</span></span>  
  
3.  <span data-ttu-id="06a43-123">將組件拖放至 [BizTalk 組件檢視工具] 中。</span><span class="sxs-lookup"><span data-stu-id="06a43-123">Drag the assembly and drop it into the BizTalk Assembly Viewer.</span></span>  
  
     <span data-ttu-id="06a43-124">[BizTalk 組件檢視工具] 只接受 BizTalk Server 組件。</span><span class="sxs-lookup"><span data-stu-id="06a43-124">The BizTalk Assembly Viewer accepts only BizTalk Server assemblies.</span></span> <span data-ttu-id="06a43-125">如果在檢視工具放入非 BizTalk 的組件，則會加以忽略。</span><span class="sxs-lookup"><span data-stu-id="06a43-125">If you drop a non-BizTalk assembly in the viewer, it is ignored.</span></span>  
  
### <a name="to-remove-a-biztalk-assembly-from-the-gac"></a><span data-ttu-id="06a43-126">若要從 GAC 移除 BizTalk 組件</span><span class="sxs-lookup"><span data-stu-id="06a43-126">To remove a BizTalk assembly from the GAC</span></span>  
  
1.  <span data-ttu-id="06a43-127">若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。</span><span class="sxs-lookup"><span data-stu-id="06a43-127">To open the BizTalk Assembly Viewer, double-click **My Computer**, and then double-click **BizTalk Server Assemblies**.</span></span>  
  
2.  <span data-ttu-id="06a43-128">以滑鼠右鍵按一下您想要從 GAC 並按一下 移除組的件**刪除**。</span><span class="sxs-lookup"><span data-stu-id="06a43-128">Right-click the assembly you want to remove from the GAC and click **Delete**.</span></span>  
  
### <a name="to-search-for-a-type-in-all-biztalk-assemblies"></a><span data-ttu-id="06a43-129">若要在所有 BizTalk 組件中搜尋類型</span><span class="sxs-lookup"><span data-stu-id="06a43-129">To search for a type in all BizTalk assemblies</span></span>  
  
1.  <span data-ttu-id="06a43-130">若要開啟 BizTalk 組件檢視器，請按兩下**我的電腦**，然後按兩下**BizTalk Server 組件**。</span><span class="sxs-lookup"><span data-stu-id="06a43-130">To open the BizTalk Assembly Viewer, double-click **My Computer**, and then double-click **BizTalk Server Assemblies**.</span></span>  
  
2.  <span data-ttu-id="06a43-131">從功能表列中，按一下  **Biztalk Server 搜尋**圖示。</span><span class="sxs-lookup"><span data-stu-id="06a43-131">From the menu bar, click the **Biz Talk Server Search** icon.</span></span>  
  
3.  <span data-ttu-id="06a43-132">在 [搜尋] 視窗中，指定在類型**尋找類型**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="06a43-132">In the Search window, specify the type in the **Find Types** drop-down list.</span></span>  
  
4.  <span data-ttu-id="06a43-133">在**BizTalk Server 組件中尋找**下拉式清單中，選取要搜尋的組件。</span><span class="sxs-lookup"><span data-stu-id="06a43-133">In the **Look in BizTalk Server assemblies** drop-down list, select the assemblies to be searched.</span></span>  
  
5.  <span data-ttu-id="06a43-134">若要縮小搜尋範圍，以包含所指定的型別參考的類型，執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="06a43-134">To narrow your search to include only types that are referenced by a specified type, do the following:</span></span>  
  
    1.  <span data-ttu-id="06a43-135">按一下**進階搜尋準則**連結。</span><span class="sxs-lookup"><span data-stu-id="06a43-135">Click the **Advanced Search Criteria** link.</span></span>  
  
    2.  <span data-ttu-id="06a43-136">在**所參考的**下拉式清單中，選取型別。</span><span class="sxs-lookup"><span data-stu-id="06a43-136">In the **Which are referenced by** drop-down list, select the type.</span></span>  
  
    3.  <span data-ttu-id="06a43-137">按一下 **[搜尋]**。</span><span class="sxs-lookup"><span data-stu-id="06a43-137">Click **Search**.</span></span>  
  
         <span data-ttu-id="06a43-138">在搜尋結果中會顯示指定的類型。</span><span class="sxs-lookup"><span data-stu-id="06a43-138">The specified types appear in the search results.</span></span>  
  
         ![](../core/media/ebiz-depl-asblyviewtypes.gif "ebiz_depl_asblyviewtypes")  
<span data-ttu-id="06a43-139">BizTalk 組件類型</span><span class="sxs-lookup"><span data-stu-id="06a43-139">BizTalk Assembly Types</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06a43-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06a43-140">See Also</span></span>  
 [<span data-ttu-id="06a43-141">檢視 BizTalk 組件檢視器的組件</span><span class="sxs-lookup"><span data-stu-id="06a43-141">Viewing Assemblies with the BizTalk Assembly Viewer</span></span>](../core/viewing-assemblies-with-the-biztalk-assembly-viewer.md)