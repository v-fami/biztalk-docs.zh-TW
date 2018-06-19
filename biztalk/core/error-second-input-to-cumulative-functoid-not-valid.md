---
title: 錯誤-無效的累計運算質第二個輸入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.secondInputToCumulativeNotValid
ms.assetid: e41a58a7-e0a2-4284-bd19-279578a8915d
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0228beda57b961d515471e42760abe3ab92db54
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968516"
---
# <a name="error---second-input-to-cumulative-functoid-not-valid"></a><span data-ttu-id="2b146-102">錯誤-第二個輸入無效的累計運算質</span><span class="sxs-lookup"><span data-stu-id="2b146-102">Error - Second Input to Cumulative Functoid Not Valid</span></span>
<span data-ttu-id="2b146-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="2b146-103">**Error Code**</span></span>  
  
 <span data-ttu-id="2b146-104">btm1031</span><span class="sxs-lookup"><span data-stu-id="2b146-104">btm1031</span></span>  
  
 <span data-ttu-id="2b146-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="2b146-105">**Explanation**</span></span>  
  
 <span data-ttu-id="2b146-106">指定**累計**運算質有不是有效的第二個輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="2b146-106">The indicated **Cumulative** functoid has a second input parameter that is not valid.</span></span> <span data-ttu-id="2b146-107">累計運算質的第二個輸入的參數必須是正整數，表示將在其上執行累積在來源結構描述中的範圍。</span><span class="sxs-lookup"><span data-stu-id="2b146-107">The second input parameter to cumulative functoids must be a positive integer that indicates the range within the source schema over which the accumulation will be performed.</span></span>  
  
 <span data-ttu-id="2b146-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="2b146-108">**User Action**</span></span>  
  
 <span data-ttu-id="2b146-109">選取指定**累計**運算質，按一下省略符號 (**...**) 相關聯的按鈕**順序運算質輸入**屬性在 microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後在**設定\<運算質\>運算質**對話方塊方塊中，確定第二個輸入的參數，如果有的話，是正整數。</span><span class="sxs-lookup"><span data-stu-id="2b146-109">Select the indicated **Cumulative** functoid, click the ellipsis (**...**) button associated with the **Order Functoid Inputs** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then in the **Configure \<Functoid\> Functoid** dialog box, ensure that the second input parameter, if any, is a positive integer.</span></span>