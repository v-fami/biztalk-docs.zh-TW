---
title: 如何逐一查看商務規則中的 ArrayList |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Business Rules Framework, ArrayList
- business rules, arrays
- Business Rules Framework, programming
ms.assetid: 935e8648-72dc-4128-986c-72b0487bc074
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9010907cfe9fb6d79a8d9fcead533376b014640e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970788"
---
# <a name="how-to-iterate-arraylist-in-business-rules"></a><span data-ttu-id="04521-102">如何逐一查看商務規則中的 ArrayList</span><span class="sxs-lookup"><span data-stu-id="04521-102">How to Iterate ArrayList in Business Rules</span></span>
<span data-ttu-id="04521-103">本節提供範例逐一查看成員**ArrayList**商務規則中。</span><span class="sxs-lookup"><span data-stu-id="04521-103">This section provides an example of iterating through members of an **ArrayList** in business rules.</span></span>  
  
 <span data-ttu-id="04521-104">假設您有**ArrayList**集合與**MyClass**物件。</span><span class="sxs-lookup"><span data-stu-id="04521-104">Assume you have an **ArrayList** with a collection of **MyClass** objects.</span></span> <span data-ttu-id="04521-105">您的商務規則看起來將如下所示。</span><span class="sxs-lookup"><span data-stu-id="04521-105">Your business rules would look like the following.</span></span>  
  
## <a name="rule-a"></a><span data-ttu-id="04521-106">規則 A</span><span class="sxs-lookup"><span data-stu-id="04521-106">Rule A</span></span>  
 <span data-ttu-id="04521-107">IF 1==1</span><span class="sxs-lookup"><span data-stu-id="04521-107">IF 1==1</span></span>  
  
 <span data-ttu-id="04521-108">THEN Assert (ArrayList.GetEnumerator)</span><span class="sxs-lookup"><span data-stu-id="04521-108">THEN Assert (ArrayList.GetEnumerator)</span></span>  
  
 <span data-ttu-id="04521-109">**IEnumerator**類型判斷提示至工作記憶體中，因為規則條件 (1 = = 1) 一律評估為 true。</span><span class="sxs-lookup"><span data-stu-id="04521-109">An **IEnumerator** type is asserted into the working memory, because the rule condition (1==1) always evaluates to true.</span></span>  
  
## <a name="rule-b"></a><span data-ttu-id="04521-110">規則 B</span><span class="sxs-lookup"><span data-stu-id="04521-110">Rule B</span></span>  
 <span data-ttu-id="04521-111">IF IEnumerator.MoveNext</span><span class="sxs-lookup"><span data-stu-id="04521-111">IF IEnumerator.MoveNext</span></span>  
  
 <span data-ttu-id="04521-112">THEN    Assert (IEnumerator.get_Current)</span><span class="sxs-lookup"><span data-stu-id="04521-112">THEN    Assert (IEnumerator.get_Current)</span></span>  
  
 <span data-ttu-id="04521-113">Update (IEnumerator)</span><span class="sxs-lookup"><span data-stu-id="04521-113">Update (IEnumerator)</span></span>  
  
 <span data-ttu-id="04521-114">規則重複處理透過**ArrayList**，每個**MyClass**集合中的物件判斷提示至工作記憶體。</span><span class="sxs-lookup"><span data-stu-id="04521-114">As the rule iterates through the **ArrayList**, each **MyClass** object in the collection is asserted into the working memory.</span></span>  
  
## <a name="rule-c"></a><span data-ttu-id="04521-115">規則 C</span><span class="sxs-lookup"><span data-stu-id="04521-115">Rule C</span></span>  
 <span data-ttu-id="04521-116">IF MyClass.MyProperty==2</span><span class="sxs-lookup"><span data-stu-id="04521-116">IF MyClass.MyProperty==2</span></span>  
  
 <span data-ttu-id="04521-117">然後\<執行某個動作...\></span><span class="sxs-lookup"><span data-stu-id="04521-117">THEN \<Do Something...\></span></span>  
  
 <span data-ttu-id="04521-118">當物件的屬性值與條件相符時，此規則便會執行動作。</span><span class="sxs-lookup"><span data-stu-id="04521-118">This rule executes action(s) when the property value of the object is matched in the condition.</span></span>