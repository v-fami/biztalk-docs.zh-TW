---
title: 如何新增常數值 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f46bf66e-caf2-4352-930f-c3c43a5717c3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48c6db99d656274f89ee5866f772db163de26c31
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976543"
---
# <a name="how-to-add-constant-values"></a><span data-ttu-id="6b81c-102">如何新增常數值</span><span class="sxs-lookup"><span data-stu-id="6b81c-102">How to Add Constant Values</span></span>
<span data-ttu-id="6b81c-103">在測試對應時，您有時候需要設定用於測試期間的常數值。</span><span class="sxs-lookup"><span data-stu-id="6b81c-103">When testing maps, you will sometimes want to set constant values for use during the test.</span></span>  
  
## <a name="set-constant-values-for-nodes-in-the-source-or-destination-schema-trees"></a><span data-ttu-id="6b81c-104">設定在來源或目的結構描述樹狀結構節點的常數值</span><span class="sxs-lookup"><span data-stu-id="6b81c-104">Set constant values for nodes in the source or destination schema trees</span></span>  
  
1. <span data-ttu-id="6b81c-105">在來源或目的結構描述樹狀結構中選取記錄或欄位。</span><span class="sxs-lookup"><span data-stu-id="6b81c-105">Select a record or field in the source or destination schema trees.</span></span>  
  
2. <span data-ttu-id="6b81c-106">在 [屬性] 視窗中，在**一般**類別中，使用**值**選取的記錄或欄位中輸入值的屬性。</span><span class="sxs-lookup"><span data-stu-id="6b81c-106">In the Properties window, in the **General** category, use the **Value** property to enter a value for the selected record or field.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="6b81c-107">您只可以將值與記錄其**內容**屬性設定為**純文字**或是**混合**。</span><span class="sxs-lookup"><span data-stu-id="6b81c-107">You can only associate a value with a record with its **Content** property set to **Text Only** or **Mixed**.</span></span>  
  
   <span data-ttu-id="6b81c-108">來源結構描述，如果您將設定中的節點**值**屬性設**\<空白\>**，產生的執行個體訊息的來源結構描述包含空值分別節點。</span><span class="sxs-lookup"><span data-stu-id="6b81c-108">For a node in source schema, if you set the **Value** property to **\<empty\>**, the generated instance message for the source schema contains an empty value for the respective node.</span></span>  
  
   <span data-ttu-id="6b81c-109">有時，您不會使用目標結構描述中的所有欄位，也就是說，目標結構描述中有些欄位會沒有任何連入連結。</span><span class="sxs-lookup"><span data-stu-id="6b81c-109">Sometimes, you do not use all the fields in the target schema, i.e. some of the fields in the target schema do not have any incoming links.</span></span> <span data-ttu-id="6b81c-110">在這種情況下，「 測試對應 」 作業會擲回錯誤，但前提**驗證 TestMap 輸入**或是**驗證 TestMap 輸出**屬性會設為**True**。</span><span class="sxs-lookup"><span data-stu-id="6b81c-110">In such cases, the Test Map operation throws error, provided that the **Validate TestMap Input** or **Validate TestMap Output** properties are set to **True**.</span></span> <span data-ttu-id="6b81c-111">若要避免在此情況下測試對應 」 錯誤，請設定**值**常數值 節點的屬性或**\<空白\>**。</span><span class="sxs-lookup"><span data-stu-id="6b81c-111">To avoid Test Map errors in such cases, set the **Value** property of the node to either a constant value or **\<empty\>**.</span></span> <span data-ttu-id="6b81c-112">使用**\<空\>** 如果您不想設定未使用的目標結構描述欄位的任意資料。</span><span class="sxs-lookup"><span data-stu-id="6b81c-112">Use **\<empty\>** if you do not want to set arbitrary data for unused target schema fields.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b81c-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b81c-113">See Also</span></span>  
[<span data-ttu-id="6b81c-114">驗證並測試對應</span><span class="sxs-lookup"><span data-stu-id="6b81c-114">Validate and test your maps</span></span>](../core/how-to-configure-map-validation-and-test-parameters.md)