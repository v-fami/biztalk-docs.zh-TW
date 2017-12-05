---
title: "錯誤-索引運算質不是有效的第一個輸入 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.map.error.firstInputToIndexNotValid
ms.assetid: f7dbe9cc-9cfa-4fc7-af3e-1241cb2b50a9
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 163de330945cc085648188dffcb75821c11ec5d6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="error---first-input-to-index-functoid-not-valid"></a><span data-ttu-id="d2b1c-102">錯誤-索引運算質不是有效的第一個輸入</span><span class="sxs-lookup"><span data-stu-id="d2b1c-102">Error - First Input to Index Functoid Not Valid</span></span>
<span data-ttu-id="d2b1c-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="d2b1c-103">**Error Code**</span></span>  
  
 <span data-ttu-id="d2b1c-104">btm1015</span><span class="sxs-lookup"><span data-stu-id="d2b1c-104">btm1015</span></span>  
  
 <span data-ttu-id="d2b1c-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="d2b1c-105">**Explanation**</span></span>  
  
 <span data-ttu-id="d2b1c-106">第一個輸入的參數所指定**索引**運算質不是來自**欄位**迴圈節點**記錄**來源結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="d2b1c-106">The first input parameter to the indicated **Index** functoid is not from a **Field** node within a looping **Record** node in the source schema.</span></span>  
  
 <span data-ttu-id="d2b1c-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="d2b1c-107">**User Action**</span></span>  
  
 <span data-ttu-id="d2b1c-108">建立適當的輸入的連結之間拖曳**欄位**迴圈節點**記錄**中來源結構描述與所指定的節點**索引**運算質。</span><span class="sxs-lookup"><span data-stu-id="d2b1c-108">Create the appropriate input link by dragging between a **Field** node within a looping **Record** node in the source schema and the indicated **Index** functoid.</span></span> <span data-ttu-id="d2b1c-109">可能需要開啟**設定\<運算質\>運算質**對話方塊中，選取 指定**索引**運算質，然後按一下省略符號 (**...**) 相關聯的按鈕**輸入參數**屬性在 microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]為了確保新建立的連結是第一個輸入的參數所指定的 [屬性] 視窗**索引**運算質。</span><span class="sxs-lookup"><span data-stu-id="d2b1c-109">It may be necessary to open the **Configure \<Functoid\> Functoid** dialog box by selecting the indicated **Index** functoid and clicking the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window in order to ensure that the newly created link is the first input parameter to the indicated **Index** functoid.</span></span>