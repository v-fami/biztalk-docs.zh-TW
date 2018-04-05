---
title: 錯誤-沒有迴圈的多個輸入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.multipleInputsWithoutLooping
ms.assetid: 7e55ad22-06a8-4a56-839d-a30b82819a68
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93a8a11b25c3c1df52827bdbf4098f0cd37bdd8b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error---multiple-inputs-without-looping"></a><span data-ttu-id="546f3-102">錯誤-多個沒有迴圈的輸入</span><span class="sxs-lookup"><span data-stu-id="546f3-102">Error - Multiple Inputs Without Looping</span></span>
<span data-ttu-id="546f3-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="546f3-103">**Error Code**</span></span>  
  
 <span data-ttu-id="546f3-104">btm1004</span><span class="sxs-lookup"><span data-stu-id="546f3-104">btm1004</span></span>  
  
 <span data-ttu-id="546f3-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="546f3-105">**Explanation**</span></span>  
  
 <span data-ttu-id="546f3-106">多個連結連接目的結構描述，只適用於當指定節點的祖系節點的其中一個連線到指定的節點**迴圈**運算質。</span><span class="sxs-lookup"><span data-stu-id="546f3-106">Multiple links are connected to the indicated node in the destination schema, which is only valid when one of the ancestor nodes of the indicated node is connected to a **Looping** functoid.</span></span>  
  
 <span data-ttu-id="546f3-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="546f3-107">**User Action**</span></span>  
  
 <span data-ttu-id="546f3-108">移除目的結構描述中指定之節點的所有連結，只保留一個連結，或將指定節點的其中一個上階節點連接到迴圈運算質。</span><span class="sxs-lookup"><span data-stu-id="546f3-108">Either remove all but one of the links to the indicated node in the destination schema, or connect one of the ancestor nodes of the indicated node to a looping functoid.</span></span>