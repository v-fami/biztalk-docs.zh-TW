---
title: 字串運算質 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d73be02-9c93-481f-81e4-39b60bcfa2df
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06bcb1d42a5e72a57765d17c18a48b6f4808d412
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22278526"
---
# <a name="string-functoids"></a><span data-ttu-id="a9af6-102">字串運算質</span><span class="sxs-lookup"><span data-stu-id="a9af6-102">String Functoids</span></span>

## <a name="overview"></a><span data-ttu-id="a9af6-103">概觀</span><span class="sxs-lookup"><span data-stu-id="a9af6-103">Overview</span></span>
<span data-ttu-id="a9af6-104">**字串**運算質可用以管理字串以標準方式，例如轉換成全為大寫或小寫，字串串連，判斷字串長度判定、 空白字元修剪等等。</span><span class="sxs-lookup"><span data-stu-id="a9af6-104">**String** functoids are used to manipulate strings in standard ways such as conversions to all uppercase or all lowercase, string concatenation, determination of string length, white space trimming, and so on.</span></span>  
  
 <span data-ttu-id="a9af6-105">運算質**大寫**，**小寫**，**大小**，**字串右空白位置修剪**，和**字串左空白位置修剪**只接受一個輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="a9af6-105">The functoids **Uppercase**, **Lowercase**, **Size**, **String Right Trim**, and **String Left Trim** accept only one input parameter.</span></span> <span data-ttu-id="a9af6-106">運算質**字串尋找**，**字串左字元回傳**，和**字串右字元回傳**接受兩個輸入參數。</span><span class="sxs-lookup"><span data-stu-id="a9af6-106">The functoids **String Find**, **String Left**, and **String Right** accept two input parameters.</span></span> <span data-ttu-id="a9af6-107">**字串擷取**運算質接受三個輸入，而**字串串連**運算質接受 1 到 100 之間的輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="a9af6-107">The **String Extract** functoid accepts three inputs, whereas the **String Concatenate** functoid accepts input parameters between 1 and 100.</span></span>  
  
 <span data-ttu-id="a9af6-108">兩個**字串**運算質是指在字串中字元的數字位置：**字串擷取**和**字串尋找**。</span><span class="sxs-lookup"><span data-stu-id="a9af6-108">Two **String** functoids refer to the numeric position of a character in a string: **String Extract** and **String Find**.</span></span> <span data-ttu-id="a9af6-109">這些運算質從字元位置 1 開始計數，而不是從 0 開始。</span><span class="sxs-lookup"><span data-stu-id="a9af6-109">These functoids begin counting character positions at 1, not 0.</span></span>  
  
 <span data-ttu-id="a9af6-110">這兩個字串修剪運算質，**字串左空白位置修剪**和**字串右空白位置修剪**，移除所有空白字元 （空格、 定位點等） 左邊或右邊 （作為可能的情況下） 指定的字串。</span><span class="sxs-lookup"><span data-stu-id="a9af6-110">The two string trimming functoids, **String Left Trim** and **String Right Trim**, remove all white space characters (spaces, tabs, and so on) from the left  or right (as the case may be) of the specified string.</span></span>  

## <a name="available-functoids"></a><span data-ttu-id="a9af6-111">可用的運算質</span><span class="sxs-lookup"><span data-stu-id="a9af6-111">Available functoids</span></span> 
 <span data-ttu-id="a9af6-112">**字串**運算質為：</span><span class="sxs-lookup"><span data-stu-id="a9af6-112">The **String** functoids are:</span></span> 

* <span data-ttu-id="a9af6-113">小寫</span><span class="sxs-lookup"><span data-stu-id="a9af6-113">Lowercase</span></span>
* <span data-ttu-id="a9af6-114">大小</span><span class="sxs-lookup"><span data-stu-id="a9af6-114">Size</span></span>
* <span data-ttu-id="a9af6-115">字串串連</span><span class="sxs-lookup"><span data-stu-id="a9af6-115">String Concatenate</span></span>
* <span data-ttu-id="a9af6-116">字串擷取</span><span class="sxs-lookup"><span data-stu-id="a9af6-116">String Extract</span></span>
* <span data-ttu-id="a9af6-117">字串尋找</span><span class="sxs-lookup"><span data-stu-id="a9af6-117">String Find</span></span>
* <span data-ttu-id="a9af6-118">字串左字元回傳</span><span class="sxs-lookup"><span data-stu-id="a9af6-118">String Left</span></span>
* <span data-ttu-id="a9af6-119">字串左空白位置修剪</span><span class="sxs-lookup"><span data-stu-id="a9af6-119">String Left Trim</span></span>
* <span data-ttu-id="a9af6-120">字串右字元回傳</span><span class="sxs-lookup"><span data-stu-id="a9af6-120">String Right</span></span>
* <span data-ttu-id="a9af6-121">字串右空白位置修剪</span><span class="sxs-lookup"><span data-stu-id="a9af6-121">String Right Trim</span></span>
* <span data-ttu-id="a9af6-122">大寫</span><span class="sxs-lookup"><span data-stu-id="a9af6-122">Uppercase</span></span>

<span data-ttu-id="a9af6-123">這些運算質的詳細[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="a9af6-123">More details on these functoids [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a9af6-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9af6-124">See Also</span></span>  
-  [<span data-ttu-id="a9af6-125">如何新增基本運算質至對應</span><span class="sxs-lookup"><span data-stu-id="a9af6-125">How to Add Basic Functoids to a Map</span></span>](../core/how-to-add-basic-functoids-to-a-map.md)   
-  <span data-ttu-id="a9af6-126">**字串運算質參考**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="a9af6-126">**String Functoids Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>