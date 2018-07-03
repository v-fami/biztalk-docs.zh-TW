---
title: 如何編輯 XPath 選取器以處理多個記錄 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, editing multiple records
- Business Rules Framework, code samples
- Business Rules Framework, programming
ms.assetid: ef7e1f8d-2e29-4cef-b558-0090648bffc0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e69748feaeb877c816cc086ba978e53e8398baf
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37018350"
---
# <a name="how-to-edit-xpath-selector-to-process-multiple-records"></a><span data-ttu-id="36f12-102">如何編輯 XPath 選取器以處理多個記錄</span><span class="sxs-lookup"><span data-stu-id="36f12-102">How to Edit XPath Selector to Process Multiple Records</span></span>
<span data-ttu-id="36f12-103">個別的子 TypedXmlDocuments 會建立當 TypedXmlDocument 判斷提示到引擎;請參閱[Assert](../core/assert.md)。</span><span class="sxs-lookup"><span data-stu-id="36f12-103">Separate child TypedXmlDocuments are created when a TypedXmlDocument is asserted into the engine; see [Assert](../core/assert.md).</span></span> <span data-ttu-id="36f12-104">此引擎根據規則中所定義的 XPath 選取器以決定建立哪個子 TypedXmlDocuments。</span><span class="sxs-lookup"><span data-stu-id="36f12-104">The engine determines which child TypedXmlDocuments to create based on the XPath selectors defined in the rules.</span></span> <span data-ttu-id="36f12-105">當您在編輯器中建置規則時，XPath 選取器的值預設為在 [事實總管] 的 [XML 結構描述] 索引標籤中選取的節點上方的節點。</span><span class="sxs-lookup"><span data-stu-id="36f12-105">When you build rules in the Composer, the XPath Selector value defaults to the node above the node selected in the XML Schemas tab in the Facts Explorer.</span></span> <span data-ttu-id="36f12-106">XPath 欄位的值預設為選取的節點本身，相對於其父節點而言。</span><span class="sxs-lookup"><span data-stu-id="36f12-106">The XPath Field value defaults to the selected node itself, relative to its parent node.</span></span>  
  
 <span data-ttu-id="36f12-107">在某些情況下，您可能要自訂建置規則時編輯器所建立的預設 XPath。</span><span class="sxs-lookup"><span data-stu-id="36f12-107">In some situations you may want to customize the default XPath that the Composer creates when building rules.</span></span> <span data-ttu-id="36f12-108">假設下列範例 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="36f12-108">Assume the following sample XML document.</span></span>  
  
```  
<Order>  
   <Orderline>  
      <Hat style="Baseball">                        
         <Cost>10</Cost>  
      </Hat>  
      <Shirt color="Black">  
         <Cost>20</Cost>  
      </Shirt>  
      <Total></Total>  
   </Orderline>  
   <Orderline>  
      <Hat style="Bowler">                        
         <Cost>20</Cost>  
      </Hat>  
      <Shirt color="Red">  
         <Cost>20</Cost>  
      </Shirt>  
      <Total></Total>  
   </Orderline>  
</Order>  
```  
  
 <span data-ttu-id="36f12-109">假設您要建置計算每個 Orderline 的 Total 值的規則。</span><span class="sxs-lookup"><span data-stu-id="36f12-109">Assume that you want to build a rule that calculates the Total value for each Orderline.</span></span> <span data-ttu-id="36f12-110">您的規則看起來將如下所示。</span><span class="sxs-lookup"><span data-stu-id="36f12-110">Your rule would look like the following.</span></span>  
  
 <span data-ttu-id="36f12-111">IF 1==1</span><span class="sxs-lookup"><span data-stu-id="36f12-111">IF 1==1</span></span>  
  
 <span data-ttu-id="36f12-112">然後<strong>/順序 Orderline/</strong>總計 = (<strong>/順序/Orderline/Hat/</strong>成本 + <strong>/順序/Orderline/Shirt/</strong>成本)</span><span class="sxs-lookup"><span data-stu-id="36f12-112">THEN <strong>/Order/Orderline/</strong>Total = (<strong>/Order/Orderline/Hat/</strong>Cost + <strong>/Order/Orderline/Shirt/</strong>Cost)</span></span>  
  
 <span data-ttu-id="36f12-113">XPath 的粗體字部分表示 [選取器] 部分，其餘則代表 [欄位] XPath。</span><span class="sxs-lookup"><span data-stu-id="36f12-113">The bold portion of the XPaths indicate the Selector portion and the remainder represents the Field XPath.</span></span> <span data-ttu-id="36f12-114">這些是由編輯器建置的預設。</span><span class="sxs-lookup"><span data-stu-id="36f12-114">These are the defaults built by the Composer.</span></span> <span data-ttu-id="36f12-115">執行此原則，不過，會導致建立 6 個物件 — 2 個 Orderline 物件、 2 個 Hat 物件和 2 個 Shirt 物件。</span><span class="sxs-lookup"><span data-stu-id="36f12-115">Running this policy, however, would result in the creation of 6 objects—2 Orderline objects, 2 Hat objects, and 2 Shirt objects.</span></span> <span data-ttu-id="36f12-116">會為 Hat 與 Shirt 物件的每個組合計算 Orderline 總計，而且總計永遠會設為相同值，該值為上次執行規則的結果。</span><span class="sxs-lookup"><span data-stu-id="36f12-116">The Orderline totals would be calculated for each combination of Hat and Shirt objects and the totals would always be set to the same value, which resulted from the last execution of the rule.</span></span> <span data-ttu-id="36f12-117">此規則會引發 8 次。</span><span class="sxs-lookup"><span data-stu-id="36f12-117">The rule would fire 8 times.</span></span> <span data-ttu-id="36f12-118">這並非此實例的目的。</span><span class="sxs-lookup"><span data-stu-id="36f12-118">This is not what is intended in this scenario.</span></span>  
  
 <span data-ttu-id="36f12-119">一個解決方式是依照下列內容編輯 XPath 值。</span><span class="sxs-lookup"><span data-stu-id="36f12-119">One solution would be to edit the XPath values to be as follows.</span></span>  
  
 <span data-ttu-id="36f12-120">IF 1==1</span><span class="sxs-lookup"><span data-stu-id="36f12-120">IF 1==1</span></span>  
  
 <span data-ttu-id="36f12-121">然後<strong>/順序 Orderline/</strong>總計 = (<strong>/順序/Orderline/</strong>Hat/成本 + <strong>/順序/Orderline/</strong>Shirt/成本)</span><span class="sxs-lookup"><span data-stu-id="36f12-121">THEN <strong>/Order/Orderline/</strong>Total = (<strong>/Order/Orderline/</strong>Hat/Cost + <strong>/Order/Orderline/</strong>Shirt/Cost)</span></span>  
  
 <span data-ttu-id="36f12-122">三個欄位的選取器 XPath 值已經全部設定為相同的 /Order/Orderline 值，而欄位 XPath 值也已經分別編輯。</span><span class="sxs-lookup"><span data-stu-id="36f12-122">The Selector XPath values for all three fields have been set to the same /Order/Orderline value and the Field XPath values have been edited accordingly.</span></span> <span data-ttu-id="36f12-123">這可藉由在 [XML 結構描述] 索引標籤中選取節點時，於 [屬性] 視窗內變更 [XPath 選取器] 與 [XPath 欄位] 值來完成。這應該在拖曳欄位至規則引數之前完成。</span><span class="sxs-lookup"><span data-stu-id="36f12-123">This is done by changing the XPath Selector and XPath Field values in the Properties window when a node is selected in the XML Schemas tab. This should be done prior to dragging the field into a rule argument.</span></span>  
  
 <span data-ttu-id="36f12-124">利用此變更來執行原則，將使得每個 Orderline 的 [總計] 值可依據該 Orderline 中 Shirt 與 Hat 節點的 [成本] 值正確計算。</span><span class="sxs-lookup"><span data-stu-id="36f12-124">Executing the policy with this change would result in the Total value being correctly calculated for each Orderline based on the Cost values of the Shirt and Hat nodes within that Orderline.</span></span>