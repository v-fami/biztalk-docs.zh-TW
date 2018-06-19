---
title: 錯誤-索引運算質沒有任何索引 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.indexFunctoidHasNoIndex
ms.assetid: a523705e-6134-4d98-8ea6-dbfc7b43dae5
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0159d308c9befc90590d281351409ba571921a53
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968436"
---
# <a name="error---index-functoid-has-no-index"></a><span data-ttu-id="edd1f-102">錯誤-索引運算質沒有任何索引</span><span class="sxs-lookup"><span data-stu-id="edd1f-102">Error - Index Functoid Has No Index</span></span>
<span data-ttu-id="edd1f-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="edd1f-103">**Error Code**</span></span>  
  
 <span data-ttu-id="edd1f-104">btm1014</span><span class="sxs-lookup"><span data-stu-id="edd1f-104">btm1014</span></span>  
  
 <span data-ttu-id="edd1f-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="edd1f-105">**Explanation**</span></span>  
  
 <span data-ttu-id="edd1f-106">已提供任何索引值為指定**索引**運算質。</span><span class="sxs-lookup"><span data-stu-id="edd1f-106">No index value(s) have been provided for the indicated **Index** functoid.</span></span>  
  
 <span data-ttu-id="edd1f-107">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="edd1f-107">**User Action**</span></span>  
  
 <span data-ttu-id="edd1f-108">提供適當的索引輸入參數數目為指定**索引**運算質，其由迴圈的數目決定適當的數字**記錄**節點**欄位**巢狀來源結構描述中的節點。</span><span class="sxs-lookup"><span data-stu-id="edd1f-108">Provide an appropriate number of index input parameters for the indicated **Index** functoid, where the appropriate number is determined by the number of looping **Record** nodes within which the **Field** node in the source schema is nested.</span></span> <span data-ttu-id="edd1f-109">若要建立索引輸入的參數，請選取指定的運算質，按一下省略符號 (**...**) 相關聯的按鈕**輸入參數**屬性在 microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後使用![ ] (../core/media/bts-tls-paraminsert.gif "bts_tls_paraminsert")按鈕內**設定\<運算質\>運算質**對話方塊以新增一或多個常數輸入的參數，其中第一個代表直屬父索引迴圈**記錄**節點，然後後續索引輸入參數代表越來越外層的上階迴圈**記錄**節點。</span><span class="sxs-lookup"><span data-stu-id="edd1f-109">To created index input parameters, select the indicated functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then use the  ![](../core/media/bts-tls-paraminsert.gif "bts_tls_paraminsert") button within the **Configure \<Functoid\> Functoid** dialog box to add one or more constant input parameters, where the first one represents an index into the immediate parent looping **Record** node, and subsequent index input parameters represent increasingly remote ancestor looping **Record** nodes.</span></span>