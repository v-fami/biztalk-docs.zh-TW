---
title: 錯誤-原生輸入的檔案不存在 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.nativeInputFileDoesNotExist
ms.assetid: 17713896-8557-4bf1-b5f0-871b905ae15e
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 333849007c808a20130f10dfb1f22a756024a4c2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22241886"
---
# <a name="error---native-input-file-does-not-exist"></a><span data-ttu-id="69d80-102">錯誤-原生輸入的檔案不存在</span><span class="sxs-lookup"><span data-stu-id="69d80-102">Error - Native Input File Does Not Exist</span></span>
<span data-ttu-id="69d80-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="69d80-103">**Error Code**</span></span>  
  
 <span data-ttu-id="69d80-104">btm1040</span><span class="sxs-lookup"><span data-stu-id="69d80-104">btm1040</span></span>  
  
 <span data-ttu-id="69d80-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="69d80-105">**Explanation**</span></span>  
  
 <span data-ttu-id="69d80-106">針對「測試對應」作業所指定的原生輸入執行個體訊息檔案不存在。</span><span class="sxs-lookup"><span data-stu-id="69d80-106">The native input instance message file specified for the Test Map operation does not exist.</span></span> <span data-ttu-id="69d80-107">當值**TestMap 輸入**對應屬性設定為**原生**，您必須指定現有的原生執行個體訊息檔案的**TestMap 輸入執行個體**對應屬性。</span><span class="sxs-lookup"><span data-stu-id="69d80-107">When the value of the **TestMap Input** map property is set to **Native**, you must specify an existing native instance message file for the **TestMap Input Instance** map property.</span></span>  
  
 <span data-ttu-id="69d80-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="69d80-108">**User Action**</span></span>  
  
 <span data-ttu-id="69d80-109">以滑鼠右鍵按一下相關對應，在 [方案總管] 中，按一下**屬性**，然後在**測試對應**索引標籤中**屬性頁**對話方塊對應中，按一下省略符號 （**...**) 中的值欄位按鈕**TestMap 輸入執行個體**屬性。</span><span class="sxs-lookup"><span data-stu-id="69d80-109">Right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, click the ellipsis (**...**) button in the value field of the **TestMap Input Instance** property.</span></span> <span data-ttu-id="69d80-110">在**選取輸入檔案**對話方塊中，選取現有的原生執行個體符合對應的來源結構描述的訊息檔案。</span><span class="sxs-lookup"><span data-stu-id="69d80-110">In the **Select Input File** dialog box, select an existing native instance message file that conforms to the source schema of the map.</span></span> <span data-ttu-id="69d80-111">或者，您可以直接在值欄位輸入此原生檔案的路徑**TestMap 輸入執行個體**屬性。</span><span class="sxs-lookup"><span data-stu-id="69d80-111">Alternatively, you can type the path of this native file directly into the value field of the **TestMap Input Instance** property.</span></span>