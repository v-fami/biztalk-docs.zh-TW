---
title: "設定傳送埠篩選條件運算式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send ports, context properties
- filtering, send ports
- send ports, filtering
- context properties, send ports
- context properties, filtering
- filtering, context properties
ms.assetid: 48c7c83b-9464-4ed9-bd8d-cf5b75e16702
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b94497f4e1412f81c36df3195994aafa32ecc451
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-filter-expressions-on-send-ports"></a><span data-ttu-id="d0cf8-102">設定傳送埠的篩選條件運算式</span><span class="sxs-lookup"><span data-stu-id="d0cf8-102">Setting Filter Expressions on Send Ports</span></span>
<span data-ttu-id="d0cf8-103">您設定篩選條件運算式中的內容屬性來控制連接埠所傳送的內容傳送埠上。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-103">You set context properties in filter expressions on the send port to control what the port sends.</span></span> <span data-ttu-id="d0cf8-104">您可以設定篩選條件運算式，以提供您在篩選屬性的方式彈性的運算子的數字 (相等或不等，存在，大於、 大於或等於、 小於且小於或等於)。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-104">You can set the filter expressions with a number of operators that offer you flexibility in how you filter the property (equality or inequality, exists, greater than, great than or equal to, less than, and less than or equal to).</span></span>  
  
### <a name="to-set-the-filter-expression-on-a-send-port"></a><span data-ttu-id="d0cf8-105">若要設定傳送埠上的篩選條件運算式</span><span class="sxs-lookup"><span data-stu-id="d0cf8-105">To set the filter expression on a send port</span></span>  
  
1.  <span data-ttu-id="d0cf8-106">在 BizTalk Server 管理主控台中，展開**BizTalk Server 管理**， **BizTalk 群組**，**應用程式**，和**BizTalk 應用程式1** （或另一個應用程式）。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, **BizTalk Group**, **Applications**, and **BizTalk Application 1** (or another application).</span></span> <span data-ttu-id="d0cf8-107">按一下**傳送埠**。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-107">Click **Send Ports**.</span></span>  
  
2.  <span data-ttu-id="d0cf8-108">以滑鼠右鍵按一下您想要設定的篩選運算式，然後按一下 傳送埠**屬性**。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-108">Right-click the send port that you want to set the filter expression for, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d0cf8-109">在 傳送埠屬性 對話方塊的主控台樹狀目錄中，按一下 **篩選**。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-109">In the console tree of the Send Port Properties dialog box, click **Filters**.</span></span>  
  
4.  <span data-ttu-id="d0cf8-110">按一下文字方塊中的**屬性**資料行，然後選取 [內容] 屬性從**屬性**下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-110">Click the text box in the **Property** column, and then select the context property from the **Property** drop-down list.</span></span>  
  
5.  <span data-ttu-id="d0cf8-111">按一下**運算子**方塊中的資料列的屬性，並從下拉式清單中選取屬性的運算子。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-111">Click the **Operator** box in the row for the property, and select the operator for the property from the drop-down list.</span></span>  
  
6.  <span data-ttu-id="d0cf8-112">按一下**值**方塊中的資料列的屬性和輸入的值運算式。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-112">Click the **Value** box in the row for the property, and type a value expression.</span></span>  
  
7.  <span data-ttu-id="d0cf8-113">如果您要加入另一個子句的篩選條件運算式，請按一下**Group By**方塊中的資料列的屬性，然後選取**和**或**或**判斷的關聯性子句。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-113">If you need to add another  clause for the filter expression, click the **Group By** box in the row for the property, and select **And** or **Or** to determine the relationship of the clauses.</span></span>  
  
8.  <span data-ttu-id="d0cf8-114">重複步驟 4 到 6 來新增另一個篩選子句。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-114">Repeat steps 4 through 6 to add another filter clause.</span></span>  
  
9. <span data-ttu-id="d0cf8-115">確認篩選條件運算式是正確的底部窗格**篩選**窗格。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-115">Verify that the filter expression is correct in the pane at the bottom of the **Filters** pane.</span></span>  
  
10. <span data-ttu-id="d0cf8-116">當您加入所有篩選子句時，按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="d0cf8-116">When you have added all filter clauses, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0cf8-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0cf8-117">See Also</span></span>  
 <span data-ttu-id="d0cf8-118">[處理 HL7 訊息](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span><span class="sxs-lookup"><span data-stu-id="d0cf8-118">[Processing HL7 Messages](../../adapters-and-accelerators/accelerator-hl7/processing-hl7-messages.md) </span></span>  
 [<span data-ttu-id="d0cf8-119">使用內容屬性</span><span class="sxs-lookup"><span data-stu-id="d0cf8-119">Using Context Properties</span></span>](../../adapters-and-accelerators/accelerator-hl7/using-context-properties.md)