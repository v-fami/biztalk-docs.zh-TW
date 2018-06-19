---
title: 錯誤-索引運算質有太多索引 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.indexFunctoidHasTooManyIndices
ms.assetid: 5dd2d5b4-3f7a-45be-b6f4-708b0a76805a
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3a22b49a921b957c0fb36f9e6b6925c991cc3cf6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968940"
---
# <a name="error---index-functoid-has-too-many-indexes"></a><span data-ttu-id="539e3-102">錯誤-索引運算質有太多索引</span><span class="sxs-lookup"><span data-stu-id="539e3-102">Error - Index Functoid Has Too Many Indexes</span></span>
<span data-ttu-id="539e3-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="539e3-103">**Error Code**</span></span>  
  
 <span data-ttu-id="539e3-104">btm1016</span><span class="sxs-lookup"><span data-stu-id="539e3-104">btm1016</span></span>  
  
 <span data-ttu-id="539e3-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="539e3-105">**Explanation**</span></span>  
  
 <span data-ttu-id="539e3-106">指定**索引**運算質有太多索引輸入的參數指定。</span><span class="sxs-lookup"><span data-stu-id="539e3-106">The indicated **Index** functoid has too many index input parameters specified.</span></span> <span data-ttu-id="539e3-107">索引輸入參數數目不能超過上階迴圈的數目**記錄**節點**欄位**節點指定為巢狀的第一個輸入的參數。</span><span class="sxs-lookup"><span data-stu-id="539e3-107">The number of index input parameters must not exceed the number of ancestor looping **Record** nodes within which the **Field** node specified as the first input parameter is nested.</span></span>  
  
 <span data-ttu-id="539e3-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="539e3-108">**User Action**</span></span>  
  
 <span data-ttu-id="539e3-109">選取指定**索引**運算質，按一下省略符號 (**...**) 相關聯的按鈕**輸入參數**屬性在 microsoft[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]屬性 視窗中，然後在**設定\<運算質\>運算質**對話方塊中，刪除多餘的索引輸入參數，選取並按一下![ ] (../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete")為每個按鈕。</span><span class="sxs-lookup"><span data-stu-id="539e3-109">Select the indicated **Index** functoid, click the ellipsis (**...**) button associated with the **Input Parameters** property in the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window, and then in the **Configure \<Functoid\> Functoid** dialog box, delete the excess index input parameters by selecting and clicking the  ![](../core/media/bts-tls-paramdelete.gif "bts_tls_paramdelete") button for each of them.</span></span>