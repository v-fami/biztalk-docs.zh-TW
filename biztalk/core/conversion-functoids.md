---
title: 轉換運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0cd7abcf-f524-4e85-b8d5-d6123767490f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 192db4b03f80674f2eb90be2255a8682454bde2b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22237886"
---
# <a name="conversion-functoids"></a><span data-ttu-id="a03d5-102">轉換運算質</span><span class="sxs-lookup"><span data-stu-id="a03d5-102">Conversion Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="a03d5-103">概觀</span><span class="sxs-lookup"><span data-stu-id="a03d5-103">Overview</span></span>
<span data-ttu-id="a03d5-104">**轉換**運算質可用數字和與其 ASCII 相等項，之間進行轉換，以將基底 10 個數字轉換成其基底 8 和基底 16 的對等項目。</span><span class="sxs-lookup"><span data-stu-id="a03d5-104">**Conversion** functoids are used to convert between numbers and their ASCII equivalents, and to convert base 10 numbers to their base 8 and base 16 equivalents.</span></span>  
  
 <span data-ttu-id="a03d5-105">所有轉換運算質都接受單一參數。</span><span class="sxs-lookup"><span data-stu-id="a03d5-105">All of the conversion functoids take a single input parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a03d5-106">因為基礎類型系統中，變更**轉換**在這個版本的 BizTalk 對應工具運算質會產生比在舊版中產生稍微不同的結果。</span><span class="sxs-lookup"><span data-stu-id="a03d5-106">Due to changes in the underlying type system, the **Conversion** functoids in this version of BizTalk Mapper produce slightly different results than those produced in previous versions.</span></span> <span data-ttu-id="a03d5-107">例如，在舊版的 BizTalk 對應工具的輸入的值為-20 到**十六進位**運算質產生輸出結果為 0xFFEC。</span><span class="sxs-lookup"><span data-stu-id="a03d5-107">For example, in previous versions of BizTalk Mapper an input value of -20 to the **Hexadecimal** functoid resulted in an output of 0xFFEC.</span></span> <span data-ttu-id="a03d5-108">在此版本中，當輸入值同樣為 -20，則產生的輸出為 0xFFFFFFEC。</span><span class="sxs-lookup"><span data-stu-id="a03d5-108">In this version, the same input value of -20 will result in an output of 0xFFFFFFEC.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="a03d5-109">可用的運算質</span><span class="sxs-lookup"><span data-stu-id="a03d5-109">Available functoids</span></span>  
 <span data-ttu-id="a03d5-110">**轉換**運算質為：</span><span class="sxs-lookup"><span data-stu-id="a03d5-110">The **Conversion** functoids are:</span></span> 

* <span data-ttu-id="a03d5-111">ASCII 到字元</span><span class="sxs-lookup"><span data-stu-id="a03d5-111">ASCII to Character</span></span>
* <span data-ttu-id="a03d5-112">字元到 ASCII</span><span class="sxs-lookup"><span data-stu-id="a03d5-112">Character to ASCII</span></span>
* <span data-ttu-id="a03d5-113">十六進位</span><span class="sxs-lookup"><span data-stu-id="a03d5-113">Hexadecimal</span></span>
* <span data-ttu-id="a03d5-114">八進位</span><span class="sxs-lookup"><span data-stu-id="a03d5-114">Octal</span></span>

<span data-ttu-id="a03d5-115">這些運算質描述[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="a03d5-115">These functoids are described [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 

## <a name="see-also"></a><span data-ttu-id="a03d5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a03d5-116">See Also</span></span>  
 [<span data-ttu-id="a03d5-117">如何新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="a03d5-117">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
