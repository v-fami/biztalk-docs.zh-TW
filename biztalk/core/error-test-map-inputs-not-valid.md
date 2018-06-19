---
title: 錯誤-無效的測試對應輸入 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.testMapInputsNotValid
ms.assetid: d885d366-92a3-4d2a-8e2b-58e06960864f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 912b70bcd74180a20d54da11dffdab79f54fc5b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22242174"
---
# <a name="error---test-map-inputs-not-valid"></a><span data-ttu-id="e1ae9-102">錯誤-無效的測試對應輸入</span><span class="sxs-lookup"><span data-stu-id="e1ae9-102">Error - Test Map Inputs Not Valid</span></span>
<span data-ttu-id="e1ae9-103">**錯誤碼**</span><span class="sxs-lookup"><span data-stu-id="e1ae9-103">**Error Code**</span></span>  
  
 <span data-ttu-id="e1ae9-104">btm1036</span><span class="sxs-lookup"><span data-stu-id="e1ae9-104">btm1036</span></span>  
  
 <span data-ttu-id="e1ae9-105">**說明**</span><span class="sxs-lookup"><span data-stu-id="e1ae9-105">**Explanation**</span></span>  
  
 <span data-ttu-id="e1ae9-106">已為 「 測試對應 」 作業指定任何輸入執行個體訊息檔案，以及 TestMap 輸入的類型未設定為**產生執行個體**。</span><span class="sxs-lookup"><span data-stu-id="e1ae9-106">No input instance message file has been specified for the Test Map operation, and the type of the TestMap input is not set to **Generate Instance**.</span></span> <span data-ttu-id="e1ae9-107">當值**TestMap 輸入**對應屬性未設定為**產生執行個體**，您必須指定執行個體訊息檔案**TestMap 輸入執行個體**對應屬性。</span><span class="sxs-lookup"><span data-stu-id="e1ae9-107">When the value of the **TestMap Input** map property is not set to **Generate Instance**, you must specify an instance message file for the **TestMap Input Instance** map property.</span></span>  
  
 <span data-ttu-id="e1ae9-108">**使用者動作**</span><span class="sxs-lookup"><span data-stu-id="e1ae9-108">**User Action**</span></span>  
  
 <span data-ttu-id="e1ae9-109">視需要設定下列其中一個對應屬性：</span><span class="sxs-lookup"><span data-stu-id="e1ae9-109">As appropriate, set one or the other of the following map properties:</span></span>  
  
-   <span data-ttu-id="e1ae9-110">**TestMap 輸入執行個體。**</span><span class="sxs-lookup"><span data-stu-id="e1ae9-110">**TestMap Input Instance.**</span></span> <span data-ttu-id="e1ae9-111">以滑鼠右鍵按一下相關對應，在 [方案總管] 中，按一下**屬性**，然後在**測試對應**索引標籤中**屬性頁**對話方塊對應中，按一下省略符號 （**...**) 中的值欄位按鈕**TestMap 輸入執行個體**屬性。</span><span class="sxs-lookup"><span data-stu-id="e1ae9-111">Right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, click the ellipsis (**...**) button in the value field of the **TestMap Input Instance** property.</span></span> <span data-ttu-id="e1ae9-112">使用**選取輸入檔案**對話方塊中，選取執行個體訊息是否符合對應的來源結構描述的檔案。</span><span class="sxs-lookup"><span data-stu-id="e1ae9-112">Using the **Select Input File** dialog box, select an instance message file that conforms to the source schema of the map.</span></span> <span data-ttu-id="e1ae9-113">或者，您可以直接在值欄位輸入此檔案的路徑**TestMap 輸入執行個體**屬性。</span><span class="sxs-lookup"><span data-stu-id="e1ae9-113">Alternatively, you can type the path of this file directly into the value field of the **TestMap Input Instance** property.</span></span>  
  
-   <span data-ttu-id="e1ae9-114">**TestMap 輸入。**</span><span class="sxs-lookup"><span data-stu-id="e1ae9-114">**TestMap Input.**</span></span> <span data-ttu-id="e1ae9-115">若要避免指定輸入執行個體訊息檔案，以滑鼠右鍵按一下相關對應，在 方案總管 中，按一下**屬性**，然後在**測試對應**索引標籤中**屬性頁**地圖上，使用下拉式清單中的值欄位 對話方塊**TestMap 輸入**屬性，以選取**產生執行個體**。</span><span class="sxs-lookup"><span data-stu-id="e1ae9-115">To avoid specifying an input instance message file, right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, use the drop-down list in the value field of the **TestMap Input** property to select **Generate Instance**.</span></span> <span data-ttu-id="e1ae9-116">在此情況下，您不需要指定檔案以供**TestMap 輸入執行個體**屬性。</span><span class="sxs-lookup"><span data-stu-id="e1ae9-116">In this case, you need not specify a file for the **TestMap Input Instance** property.</span></span>