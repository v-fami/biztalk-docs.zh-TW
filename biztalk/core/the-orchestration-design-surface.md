---
title: 協調流程設計介面 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5fb190b-60d7-45e4-9883-7b3d2ed6b0c0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f943c1543cf50e4ecb1f25627cbccd7b4d72eab5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279806"
---
# <a name="the-orchestration-design-surface"></a><span data-ttu-id="ef08f-102">協調流程設計介面</span><span class="sxs-lookup"><span data-stu-id="ef08f-102">The Orchestration Design Surface</span></span>
<span data-ttu-id="ef08f-103">協調流程設計介面是一套可以用來建立 BizTalk 協調流程的視覺化設計工具，也是協調流程設計師的中央元件。</span><span class="sxs-lookup"><span data-stu-id="ef08f-103">The Orchestration Design Surface is a visual designer that you can use to create a BizTalk Orchestration, and is the central component of Orchestration Designer.</span></span> <span data-ttu-id="ef08f-104">它是一張畫布，可以讓您從工具箱拖曳圖形到上面，然後再設定圖形。</span><span class="sxs-lookup"><span data-stu-id="ef08f-104">It is a canvas that you can drag shapes onto from the Toolbox, and then configure the shapes.</span></span> <span data-ttu-id="ef08f-105">這個設計介面是 Visual Studio 編輯器視窗，所以會佔用其他 Visual Studio 編輯器視窗所使用的主視窗區域。</span><span class="sxs-lookup"><span data-stu-id="ef08f-105">As a Visual Studio editor window, it occupies the main window area used by other Visual Studio editor windows.</span></span>  
  
 <span data-ttu-id="ef08f-106">![協調流程設計師](../core/media/b96c16e5-58a2-4d8e-b66c-485864846cec.gif "b96c16e5-58a2-4d8e-b66c-485864846cec")</span><span class="sxs-lookup"><span data-stu-id="ef08f-106">![Orchestration Designers](../core/media/b96c16e5-58a2-4d8e-b66c-485864846cec.gif "b96c16e5-58a2-4d8e-b66c-485864846cec")</span></span>  
<span data-ttu-id="ef08f-107">協調流程設計介面</span><span class="sxs-lookup"><span data-stu-id="ef08f-107">Orchestration Design Surface</span></span>  
  
 <span data-ttu-id="ef08f-108">協調流程的名稱會顯示在 [協調流程設計介面] 視窗最上方的索引標籤上，以及 Visual Studio 視窗的標題列上。</span><span class="sxs-lookup"><span data-stu-id="ef08f-108">The name of the orchestration is displayed on the top tab of the Orchestration Design Surface window and in the Visual Studio window title bar.</span></span>  
  
 <span data-ttu-id="ef08f-109">在設計介面本身分成三個區域: 「 處理區域和兩個連接埠介面 」。</span><span class="sxs-lookup"><span data-stu-id="ef08f-109">The design surface itself is divided into three areas: the Process Area and two Port Surfaces.</span></span> <span data-ttu-id="ef08f-110">中央的「處理區域」包含會描述協調流程之實際處理流程的圖形。</span><span class="sxs-lookup"><span data-stu-id="ef08f-110">The central Process Area contains shapes that describe the actual process flow of the orchestration.</span></span> <span data-ttu-id="ef08f-111">Flanked 兩端的連接埠介面 」，其中包含只連接埠和角色連結圖形互動**傳送**和**接收**處理區域 中的圖形。</span><span class="sxs-lookup"><span data-stu-id="ef08f-111">It is flanked on both sides by Port Surfaces, which contain only Port and Role Link shapes that interact with the **Send** and **Receive** shapes in the Process Area.</span></span>  
  
 <span data-ttu-id="ef08f-112">**流程領域**</span><span class="sxs-lookup"><span data-stu-id="ef08f-112">**Process Area**</span></span>  
  
 <span data-ttu-id="ef08f-113">「處理區域」是協調流程設計師之協調流程設計介面的主要部分，永遠位於協調流程設計介面的水平置中位置。</span><span class="sxs-lookup"><span data-stu-id="ef08f-113">The Process Area is the main part of the Orchestration Design Surface of Orchestration Designer, and is always horizontally centered in the Orchestration Design Surface.</span></span>  
  
 <span data-ttu-id="ef08f-114">「處理區域」的兩邊都是「連接埠介面」。</span><span class="sxs-lookup"><span data-stu-id="ef08f-114">On either side of the Process Area you see Port Surfaces.</span></span> <span data-ttu-id="ef08f-115">**開始**圖形位於設計介面的頂端和協調流程會隨著向下加入圖形。</span><span class="sxs-lookup"><span data-stu-id="ef08f-115">The **Begin** shape is placed at the top of the design surface and the orchestration grows downward as you add shapes.</span></span>  
  
 <span data-ttu-id="ef08f-116">**連接埠介面**</span><span class="sxs-lookup"><span data-stu-id="ef08f-116">**Port Surfaces**</span></span>  
  
 <span data-ttu-id="ef08f-117">協調流程設計介面中會顯示兩個「連接埠介面」，分別位於「處理區域」兩側。</span><span class="sxs-lookup"><span data-stu-id="ef08f-117">Two Port Surfaces are displayed in the Orchestration Design Surface, one on either side of the Process Area.</span></span> <span data-ttu-id="ef08f-118">連接埠介面 」 可以包含兩種類型的圖形：**連接埠**和**角色連結**。</span><span class="sxs-lookup"><span data-stu-id="ef08f-118">Port Surfaces can contain two kinds of shapes: **Ports** and **Role Links**.</span></span> <span data-ttu-id="ef08f-119">這些圖形互動**傳送**和**接收**處理區域 中的圖形。</span><span class="sxs-lookup"><span data-stu-id="ef08f-119">These shapes interact with the **Send** and **Receive** shapes in the Process Area.</span></span>  
  
 <span data-ttu-id="ef08f-120">不論您將使用哪個「連接埠介面」來處理圖形，都不會造成任何差異，圖形在左右「連接埠介面」上的功能都一樣。</span><span class="sxs-lookup"><span data-stu-id="ef08f-120">It makes no difference which Port Surface you use for a shape; that is, the shape functions identically on either the right or the left Port Surface.</span></span> <span data-ttu-id="ef08f-121">有了這個可以放置新連接埠的「連接埠介面」，您就可以建立交叉接點較少且更容易管理的協調流程。</span><span class="sxs-lookup"><span data-stu-id="ef08f-121">Having two Port Surfaces on which to place new ports lets you create orchestrations with fewer crisscrossing connectors that therefore are easier to read.</span></span>  
  
 <span data-ttu-id="ef08f-122">這兩個「連接埠介面」都可以摺疊或展開，方法是按兩下介面或是按一下雙箭頭圖示。</span><span class="sxs-lookup"><span data-stu-id="ef08f-122">Both Port Surfaces can be collapsed or expanded by double-clicking on them or by clicking on the double arrow icon.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ef08f-123">在許多協調流程設計師工作中，您都必須選取各種不同的項目，例如結構描述或協調流程。</span><span class="sxs-lookup"><span data-stu-id="ef08f-123">Many Orchestration Designer tasks require you to select various items such as schemas or orchestrations.</span></span> <span data-ttu-id="ef08f-124">如果這些項目不在目前的專案中，請務必記得在您的專案中加入組件的參考，且參考的組件必須包含您想要選取的項目。</span><span class="sxs-lookup"><span data-stu-id="ef08f-124">If these items are not in the current project, you must remember to add a reference in your project to the assembly that contains the item that you want to select.</span></span> <span data-ttu-id="ef08f-125">若要這樣做，請以滑鼠右鍵按一下專案，然後選取**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="ef08f-125">To do this, right-click the project and select **Add Reference**.</span></span>  
  
 <span data-ttu-id="ef08f-126">**支援縮放**</span><span class="sxs-lookup"><span data-stu-id="ef08f-126">**Zoom Support**</span></span>  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="ef08f-127"> 提供縮放協調流程設計師介面的功能。</span><span class="sxs-lookup"><span data-stu-id="ef08f-127"> provides the ability to zoom in or zoom out of the Orchestration designer surface.</span></span> <span data-ttu-id="ef08f-128">如果要使用縮放支援，請完成下列其中一個步驟：</span><span class="sxs-lookup"><span data-stu-id="ef08f-128">You can use zoom support by completing one of the following steps:</span></span>  
  
-   <span data-ttu-id="ef08f-129">以滑鼠右鍵按一下協調流程設計師介面，然後按一下**縮放**功能表選項。</span><span class="sxs-lookup"><span data-stu-id="ef08f-129">Right-click the Orchestration designer surface and click the **Zoom** menu option.</span></span> <span data-ttu-id="ef08f-130">接著，您可以選取想要套用的縮放比例。</span><span class="sxs-lookup"><span data-stu-id="ef08f-130">You can then select the percentage of magnification that you would like to apply.</span></span>  
  
-   <span data-ttu-id="ef08f-131">使用 CTRL + 滑鼠滾輪的組合以放大或縮小。按住 CTRL 鍵，同時上下轉動滑鼠滾輪。</span><span class="sxs-lookup"><span data-stu-id="ef08f-131">Use the CTRL + MWHEEL combination to zoom in or zoom out. Hold down the CTRL button and simultaneously rotate the mouse wheel up or down.</span></span> <span data-ttu-id="ef08f-132">使用 CTRL+滑鼠滾輪上移的組合可將介面縮小，CTRL+滑鼠滾輪下移的組合則可將介面放大。</span><span class="sxs-lookup"><span data-stu-id="ef08f-132">Use the CTRL+MWHEELUP combination to zoom out and the CTRL+MWHEELDOWN combination to zoom in.</span></span>