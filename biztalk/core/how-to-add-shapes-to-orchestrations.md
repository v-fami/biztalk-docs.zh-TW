---
title: 如何新增圖形至協調流程 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- shapes, orchestrations
- orchestrations, shapes
- Construct Message shape [Orchestration Designer]
- Message Assignment shape [Orchestration Designer]
- Scope shape [Orchestration Designer]
ms.assetid: d39eb12c-cdc6-4918-93d9-536db1dfb889
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9fa6634adb20ffcf927da0af6f58e9daa2800ac
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22246950"
---
# <a name="how-to-add-shapes-to-orchestrations"></a><span data-ttu-id="3ce88-102">如何新增圖形至協調流程</span><span class="sxs-lookup"><span data-stu-id="3ce88-102">How to Add Shapes to Orchestrations</span></span>
<span data-ttu-id="3ce88-103">本節描述在您的協調流程中新增及移除圖形的程序。</span><span class="sxs-lookup"><span data-stu-id="3ce88-103">This section describes the procedures for adding and removing shapes in your orchestration.</span></span> <span data-ttu-id="3ce88-104">如需可用圖形的詳細資訊，請參閱[協調流程圖形](../core/orchestration-shapes.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce88-104">For more information about the available shapes, see [Orchestration Shapes](../core/orchestration-shapes.md).</span></span>  
  
### <a name="to-add-a-shape-to-an-orchestration"></a><span data-ttu-id="3ce88-105">若要將圖形新增至協調流程</span><span class="sxs-lookup"><span data-stu-id="3ce88-105">To add a shape to an orchestration</span></span>  
  
1.  <span data-ttu-id="3ce88-106">在工具箱中，在**BizTalk 協調流程**索引標籤上，將圖形的連接線，拖曳到協調流程設計介面上。</span><span class="sxs-lookup"><span data-stu-id="3ce88-106">In the Toolbox, on the **BizTalk Orchestrations** tab, drag the shape onto a connecting line on the Orchestration Design Surface.</span></span>  
  
     <span data-ttu-id="3ce88-107">-或者-</span><span class="sxs-lookup"><span data-stu-id="3ce88-107">—Or—</span></span>  
  
2.  <span data-ttu-id="3ce88-108">以滑鼠右鍵按一下的連接線或圖形預留位置您要加入圖形，指向**插入圖形**，然後按一下您想要新增的圖形名稱。</span><span class="sxs-lookup"><span data-stu-id="3ce88-108">Right-click the connecting line or the shape placeholder where you want to add the shape, point to **Insert Shape**, and then click the shape name you want to add.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3ce88-109">尚未完全設定的圖形上會出現「智慧標籤」。</span><span class="sxs-lookup"><span data-stu-id="3ce88-109">A Smart Tag appears on shapes that are not yet fully configured.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ce88-110">**轉換**圖形和**訊息指派**圖形只能存在於**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="3ce88-110">**Transform** shapes and **Message Assignment** shapes can only exist within a **Construct Message** shape.</span></span> <span data-ttu-id="3ce88-111">如果您加入其中一種圖形以外的協調流程**建構訊息**圖形，它會自動放置於新**建構訊息**圖形。</span><span class="sxs-lookup"><span data-stu-id="3ce88-111">If you add one of these shapes to your orchestration outside of a **Construct Message** shape, it is placed automatically inside a new **Construct Message** shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ce88-112">**攔截例外狀況**和**補償**區塊只能存在於下列**範圍**圖形。</span><span class="sxs-lookup"><span data-stu-id="3ce88-112">**Catch Exception** and **Compensation** blocks can only exist following a **Scope** shape.</span></span>  
  
### <a name="to-remove-a-shape-from-an-orchestration"></a><span data-ttu-id="3ce88-113">若要從協調流程移除圖形</span><span class="sxs-lookup"><span data-stu-id="3ce88-113">To remove a shape from an orchestration</span></span>  
  
1.  <span data-ttu-id="3ce88-114">以滑鼠右鍵按一下設計介面上的圖形，然後按一下**刪除**。</span><span class="sxs-lookup"><span data-stu-id="3ce88-114">Right-click the shape on the design surface, and then click **Delete**.</span></span>  
  
     <span data-ttu-id="3ce88-115">-或者-</span><span class="sxs-lookup"><span data-stu-id="3ce88-115">—Or—</span></span>  
  
2.  <span data-ttu-id="3ce88-116">選取圖形，然後按**刪除**索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3ce88-116">Select the shape and press the **DELETE** key.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce88-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce88-117">See Also</span></span>  
 [<span data-ttu-id="3ce88-118">建立協調流程</span><span class="sxs-lookup"><span data-stu-id="3ce88-118">Creating Orchestrations</span></span>](../core/creating-orchestrations.md)