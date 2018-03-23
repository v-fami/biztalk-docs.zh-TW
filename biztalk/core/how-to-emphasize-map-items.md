---
title: 如何強調對應項目 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a2732b36-ca57-4566-ba26-da27a3082f32
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d6bb03969a044c6a474f5d2d1c1e5e1a5067cf81
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="how-to-emphasize-map-items"></a><span data-ttu-id="d6f8f-102">如何強調對應項目</span><span class="sxs-lookup"><span data-stu-id="d6f8f-102">How to Emphasize Map Items</span></span>
<span data-ttu-id="d6f8f-103">在 BizTalk 對應工具中，當您選取對應項目時，所有相關聯的連結和運算質都會強調顯示。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-103">In the BizTalk Mapper, when you select a map item, all the associated links and functoids are emphasized.</span></span> <span data-ttu-id="d6f8f-104">當對應含有許多連結，而令人難以識別關係和相關的結構描述項目時，這項功能非常有用。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-104">This is useful in maps with many links, where it is difficult to identify a relationship and the related schema items.</span></span>  
  
 <span data-ttu-id="d6f8f-105">當您選取連結、運算質或結構描述項目時，BizTalk 對應工具會強調顯示相關的關係和結構描述項目。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-105">When you select a link, a functoid, or a schema element, the BizTalk Mapper emphasizes the related relationship and schema elements.</span></span> <span data-ttu-id="d6f8f-106">對於選取的對應項目而言，所有的連入連結和連出連結 (採用遞迴方式) 都會以粗體醒目顯示，而所有其他對應項目則會變成灰色。下列螢幕擷取畫面顯示選取的對應項目會變成彩色粗體，而其他對應項目會變得較不醒目。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-106">For the selected map item, all the incoming links and the outgoing links (recursively) are highlighted in bold, and all the other map items are greyed out. The following screenshot shows the selected map item in bold and color and the other map items appear lighter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d6f8f-107">在此情況下，相關的關係表示所有的連結、運算質或結構描述項目都直接或間接連結至選取的對應項目。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-107">In this context, a related relationship means all the links, functoids, or schema elements directly or indirectly linked to the selected map item.</span></span>  
  
 <span data-ttu-id="d6f8f-108">![強調對應項目](../core/media/mapper-intelliselect.gif "Mapper_IntelliSelect")</span><span class="sxs-lookup"><span data-stu-id="d6f8f-108">![Emphasizing a map item](../core/media/mapper-intelliselect.gif "Mapper_IntelliSelect")</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d6f8f-109">필수 구성 요소</span><span class="sxs-lookup"><span data-stu-id="d6f8f-109">Prerequisites</span></span>  
 <span data-ttu-id="d6f8f-110">此作業需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-110">This operation requires that BizTalk Mapper is running.</span></span>  
  
## <a name="to-emphasize-a-map-item"></a><span data-ttu-id="d6f8f-111">若要強調顯示對應項目</span><span class="sxs-lookup"><span data-stu-id="d6f8f-111">To emphasize a map item</span></span>  
  
-   <span data-ttu-id="d6f8f-112">按一下對應項目 (連結、運算質或結構描述項目)。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-112">Click a map item (a link, a functoid, or a schema element).</span></span> <span data-ttu-id="d6f8f-113">您可以看見，與目前格線頁中所選對應項目相關聯的所有其他連結和運算質 (包括結構描述節點) 都已醒目顯示。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-113">You can see that all the other links and functoids (including the schema nodes) associated with the selected map item in the current grid page are highlighted.</span></span>  
  
     <span data-ttu-id="d6f8f-114">有時候，選取的節點可能會有關係存在於其他格線頁中。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-114">Sometimes, for the selected node, there might be relationships existing in other grid pages.</span></span> <span data-ttu-id="d6f8f-115">在此情況下，BizTalk 對應工具會在目前格線頁中強調顯示此執行個體，同時醒目顯示選取的節點的其他關係所在的頁面索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d6f8f-115">In such a case, the BizTalk Mapper emphasizes the instance in current grid page and also highlights the page tab where the other related relationship to the selected node exists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6f8f-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6f8f-116">See Also</span></span>  
 [<span data-ttu-id="d6f8f-117">使用 BizTalk 對應工具中的增強的功能</span><span class="sxs-lookup"><span data-stu-id="d6f8f-117">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)