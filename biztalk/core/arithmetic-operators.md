---
title: "算術運算子 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d73e153c-aac1-4cea-92d8-af4a1bea6e6a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4b3d66a990437929176835228efa1a74a5fa8683
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="arithmetic-operators"></a><span data-ttu-id="63844-102">算術運算子</span><span class="sxs-lookup"><span data-stu-id="63844-102">Arithmetic Operators</span></span>
<span data-ttu-id="63844-103">商務規則架構可支援使用加法、減法、乘法、除法和餘數運算子來建立商務規則。</span><span class="sxs-lookup"><span data-stu-id="63844-103">The Business Rules Framework supports using the addition, subtraction, multiplication, division, and remainder (modulo) operators in creating business rules.</span></span> <span data-ttu-id="63844-104">下表描述可用的算數運算子。</span><span class="sxs-lookup"><span data-stu-id="63844-104">The following table describes the arithmetic operators.</span></span>  
  
|<span data-ttu-id="63844-105">算術運算子</span><span class="sxs-lookup"><span data-stu-id="63844-105">Arithmetic operator</span></span>|<span data-ttu-id="63844-106">Description</span><span class="sxs-lookup"><span data-stu-id="63844-106">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="63844-107">**加入**</span><span class="sxs-lookup"><span data-stu-id="63844-107">**Add**</span></span>|<span data-ttu-id="63844-108">代表加法運算子 (arg1 加到 arg2)。</span><span class="sxs-lookup"><span data-stu-id="63844-108">Represents the addition operator (arg1 added to arg2).</span></span>|  
|<span data-ttu-id="63844-109">**減去**</span><span class="sxs-lookup"><span data-stu-id="63844-109">**Subtract**</span></span>|<span data-ttu-id="63844-110">代表減法運算子 (arg2 減 arg1)。</span><span class="sxs-lookup"><span data-stu-id="63844-110">Represents the subtraction operator (arg1 subtracted from arg2).</span></span>|  
|<span data-ttu-id="63844-111">**相乘**</span><span class="sxs-lookup"><span data-stu-id="63844-111">**Multiply**</span></span>|<span data-ttu-id="63844-112">代表乘法運算子 (arg1 乘以 arg2)。</span><span class="sxs-lookup"><span data-stu-id="63844-112">Represents the multiplication operator (arg1 multiplied by arg2).</span></span>|  
|<span data-ttu-id="63844-113">**Divide**</span><span class="sxs-lookup"><span data-stu-id="63844-113">**Divide**</span></span>|<span data-ttu-id="63844-114">代表除法運算子 (arg1 除以 arg2)。</span><span class="sxs-lookup"><span data-stu-id="63844-114">Represents the division operator (arg1 divided by arg2).</span></span>|  
|<span data-ttu-id="63844-115">**餘數**</span><span class="sxs-lookup"><span data-stu-id="63844-115">**Remainder**</span></span>|<span data-ttu-id="63844-116">代表餘數運算子 (arg1 除以 arg2 的餘數)。</span><span class="sxs-lookup"><span data-stu-id="63844-116">Represents the remainder operator (arg1 modulo arg2).</span></span>|  
  
 <span data-ttu-id="63844-117">當運算元的類型不同時，便會發生自動數值升級，將較小的運算元類型轉換成較大的運算元類型。</span><span class="sxs-lookup"><span data-stu-id="63844-117">When operands are of different types, automatic numeric promotion occurs with the smaller operand type being converted to the larger operand type.</span></span> <span data-ttu-id="63844-118">例如，如果**新增**運算子搭配的第一個運算元**int**類型和第二個運算元**長**類型，第一個運算元的類型會轉換成**長**執行之前**新增**作業。</span><span class="sxs-lookup"><span data-stu-id="63844-118">For example, if the **Add** operator is used with the first operand of **int** type and the second operand of **long** type, the type of the first operand is converted to **long** before performing the **Add** operation.</span></span> <span data-ttu-id="63844-119">如果兩個運算元都可以升級成一般類型，則規則引擎也可以支援雙重升級。</span><span class="sxs-lookup"><span data-stu-id="63844-119">The rule engine also supports double promotion if both the operands can be promoted to a common type.</span></span> <span data-ttu-id="63844-120">例如，如果**新增**運算子搭配的第一個運算元**int**類型和第二個運算元**uint**類型，這兩個運算元的類型會轉換成**長**執行之前**新增**作業。</span><span class="sxs-lookup"><span data-stu-id="63844-120">For example, if the **Add** operator is used with the first operand of **int** type and the second operand of **uint** type, the types of both operands are converted to **long** before performing the **Add** operation.</span></span>  
  
## <a name="to-use-a-logical-operator-in-a-business-rule"></a><span data-ttu-id="63844-121">在商務規則中使用邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="63844-121">To use a logical operator in a business rule</span></span>  
 <span data-ttu-id="63844-122">使用下列程序可在商務規則中使用邏輯運算子。</span><span class="sxs-lookup"><span data-stu-id="63844-122">Use the following procedure to use a logical operator in a business rule.</span></span>  
  
1.  <span data-ttu-id="63844-123">在 事實總管 視窗中，按一下**詞彙** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="63844-123">In the Facts Explorer window, click the **Vocabularies** tab.</span></span>  
  
2.  <span data-ttu-id="63844-124">展開**詞彙**，依序展開**函式**，依序展開**1.0 版-已發佈**，然後將拖曳**新增/減/乘/除/餘數**到 條件窗格 / 執行 窗格。</span><span class="sxs-lookup"><span data-stu-id="63844-124">Expand **Vocabularies**, expand **Functions**, expand **Version 1.0 - Published**, and then drag the **Add/Subtract/Multiply/Divide/Remainder** to the Conditions pane/Actions pane.</span></span>  
  
3.  <span data-ttu-id="63844-125">指定左運算子和右運算子的值。</span><span class="sxs-lookup"><span data-stu-id="63844-125">Specify values for left and right operators.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63844-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="63844-126">See Also</span></span>  
 [<span data-ttu-id="63844-127">邏輯運算子</span><span class="sxs-lookup"><span data-stu-id="63844-127">Logical Operators</span></span>](../core/logical-operators.md)