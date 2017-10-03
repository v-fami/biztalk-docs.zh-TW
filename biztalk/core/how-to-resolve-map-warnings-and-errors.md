---
title: "如何解析對應警告和錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a3e7f3-c96c-4d3d-9f7c-d2bfd9ace4fd
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a2983a53bb47aa66d1564772d0f8e033132e5a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-resolve-map-warnings-and-errors"></a><span data-ttu-id="4ee86-102">如何解析對應警告和錯誤</span><span class="sxs-lookup"><span data-stu-id="4ee86-102">How to Resolve Map Warnings and Errors</span></span>
<span data-ttu-id="4ee86-103">當您編譯對應時，可能會發現編譯程序所導致的警告與錯誤。</span><span class="sxs-lookup"><span data-stu-id="4ee86-103">When you compile a map, you may find that warnings and errors result from the compilation process.</span></span>  
  
## <a name="resolve-warnings-and-errors-when-building-a-map"></a><span data-ttu-id="4ee86-104">解析建置對應時的警告和錯誤</span><span class="sxs-lookup"><span data-stu-id="4ee86-104">Resolve warnings and errors when building a map</span></span>  
  
1.  <span data-ttu-id="4ee86-105">對於連結與運算質錯誤，在**錯誤清單**視窗中，按兩下任何描述。</span><span class="sxs-lookup"><span data-stu-id="4ee86-105">For link and functoid errors, in the **Error List** window, double-click any description.</span></span>  
  
     <span data-ttu-id="4ee86-106">就會反白顯示與該錯誤關聯的連結、運算質或結構描述。</span><span class="sxs-lookup"><span data-stu-id="4ee86-106">The link, functoid, or the schema node associated with the error is highlighted.</span></span> <span data-ttu-id="4ee86-107">解析問題。</span><span class="sxs-lookup"><span data-stu-id="4ee86-107">Resolve the issue.</span></span>  
  
2.  <span data-ttu-id="4ee86-108">檢閱**描述**區域**錯誤清單**視窗來判斷其他錯誤。</span><span class="sxs-lookup"><span data-stu-id="4ee86-108">Review the **Description** area in the **Error List** window to determine additional errors.</span></span>  
  
3.  <span data-ttu-id="4ee86-109">按一下**輸出**視窗索引標籤以檢視其他警告與錯誤訊息資訊。</span><span class="sxs-lookup"><span data-stu-id="4ee86-109">Click the **Output** window tab to view additional warning and error message information.</span></span>  
  
4.  <span data-ttu-id="4ee86-110">在您解決所有問題之後，以滑鼠右鍵按一下方案總管 中的對應檔案名稱，然後按一下**測試對應**或**建置方案**、 為情況下可能要。</span><span class="sxs-lookup"><span data-stu-id="4ee86-110">After you have resolved all issues, right-click the map file name in Solution Explorer, and then click **Test Map** or **Build Solution**, as the case may be.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ee86-111">若發生警告，則問題可能存在幾個格線頁上。</span><span class="sxs-lookup"><span data-stu-id="4ee86-111">If a warning appears, the problem might exist over several grid pages.</span></span> <span data-ttu-id="4ee86-112">例如，您有一筆記錄的格線頁 1 (名為**項目**) 來源結構描述樹狀結構中，連結到記錄 (名為**數目**) 目的結構描述樹狀結構中。</span><span class="sxs-lookup"><span data-stu-id="4ee86-112">For example, you have grid page 1 with a record (named **Item**) in the source schema tree linked to a record (named **Number**) in the destination schema tree.</span></span> <span data-ttu-id="4ee86-113">2 的格線頁中，您有一筆記錄 (名為**產品**) 在來源結構描述樹狀結構連結到相同**數目**記錄目的地結構描述樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4ee86-113">On grid page 2 you have a record (named **Product**) in the source schema tree linked to the same **Number** record in the destination schema tree.</span></span> <span data-ttu-id="4ee86-114">在此案例中，會產生警告訊息通知您有多個輸入相同的記錄。</span><span class="sxs-lookup"><span data-stu-id="4ee86-114">In this scenario, a warning message is generated stating that you have multiple inputs to the same record.</span></span> <span data-ttu-id="4ee86-115">不過您檢視格線頁 1，如果您看到只有一個輸入**數目**記錄。</span><span class="sxs-lookup"><span data-stu-id="4ee86-115">However if you view grid page 1, you see only one input into the **Number** record.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="4ee86-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ee86-116">See Also</span></span>  
 <span data-ttu-id="4ee86-117">[編譯和測試對應](../core/compiling-and-testing-maps.md) </span><span class="sxs-lookup"><span data-stu-id="4ee86-117">[Compiling and Testing Maps](../core/compiling-and-testing-maps.md) </span></span>  
 <span data-ttu-id="4ee86-118">[BizTalk 對應工具 」 錯誤](../core/biztalk-mapper-errors.md) </span><span class="sxs-lookup"><span data-stu-id="4ee86-118">[BizTalk Mapper Errors](../core/biztalk-mapper-errors.md) </span></span>  
 [<span data-ttu-id="4ee86-119">地圖疑難排解</span><span class="sxs-lookup"><span data-stu-id="4ee86-119">Troubleshooting Maps</span></span>](../core/troubleshooting-maps.md)