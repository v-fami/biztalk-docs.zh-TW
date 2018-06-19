---
title: 步驟 9： 驗證和建置對應專案 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- validating, maps
- message enrichment tutorial, maps
- maps, building
- maps, validating
ms.assetid: 10716b0b-702c-48bb-85a9-d58d8f33b68b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c1eb4580a9c89534204e492aebdd21988a6ce0e6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206470"
---
# <a name="step-9-validate-and-build-the-map-project"></a><span data-ttu-id="dd44c-102">步驟 9： 驗證和建置對應專案</span><span class="sxs-lookup"><span data-stu-id="dd44c-102">Step 9: Validate and Build the Map Project</span></span>
<span data-ttu-id="dd44c-103">在此步驟中，您會使用**驗證對應**命令來判斷對應包含任何內部不一致，或是有其他問題，可避免對其有效地使用對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="dd44c-103">In this step, you use the **Validate Map** command to determine if the map contains any internal inconsistencies, or has other issues that would prevent it from being used effectively for mapping schemas.</span></span> <span data-ttu-id="dd44c-104">您也可以建置此專案以產生組件，其中包含您所建立的資源 （結構描述和對應）。</span><span class="sxs-lookup"><span data-stu-id="dd44c-104">You also build the project to generate an assembly that contains the resources (schemas and the map) that you created.</span></span> <span data-ttu-id="dd44c-105">這也可確保您到目前為止完成的工作中沒有編譯錯誤。</span><span class="sxs-lookup"><span data-stu-id="dd44c-105">This also ensures that there are no compile errors in the work that you have completed so far.</span></span>  
  
### <a name="to-validate-the-map-project"></a><span data-ttu-id="dd44c-106">若要驗證對應專案</span><span class="sxs-lookup"><span data-stu-id="dd44c-106">To validate the map project</span></span>  
  
1.  <span data-ttu-id="dd44c-107">在 方案總管 中，以滑鼠右鍵按一下**DoorbellMap.btm**對應，，然後按一下 **驗證對應**。</span><span class="sxs-lookup"><span data-stu-id="dd44c-107">In Solution Explorer, right-click the **DoorbellMap.btm** map, and then click **Validate Map**.</span></span>  
  
2.  <span data-ttu-id="dd44c-108">請在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="dd44c-108">Ensure that a success message appears in the output window.</span></span> <span data-ttu-id="dd44c-109">因為您不對應至目的結構描述中所有可用的項目，可能會出現一些警告。</span><span class="sxs-lookup"><span data-stu-id="dd44c-109">Some warnings may appear because you are not mapping to all available elements in the destination schema.</span></span>  
  
     <span data-ttu-id="dd44c-110">如果沒有成功訊息隨即出現，疑難排解對應專案。</span><span class="sxs-lookup"><span data-stu-id="dd44c-110">If no success message appears, troubleshoot the map project.</span></span>  
  
### <a name="to-build-the-map-project"></a><span data-ttu-id="dd44c-111">若要建置對應專案</span><span class="sxs-lookup"><span data-stu-id="dd44c-111">To build the map project</span></span>  
  
-   <span data-ttu-id="dd44c-112">在 方案總管 中，以滑鼠右鍵按一下**BTAHL7 專案**，然後按一下 **建置**。</span><span class="sxs-lookup"><span data-stu-id="dd44c-112">In Solution Explorer, right-click **BTAHL7 Project**, and then click **Build**.</span></span> <span data-ttu-id="dd44c-113">請在 [輸出] 視窗中出現的成功訊息。</span><span class="sxs-lookup"><span data-stu-id="dd44c-113">Ensure that a success message appears in the output window.</span></span>  
  
     <span data-ttu-id="dd44c-114">如果沒有成功訊息隨即出現，疑難排解對應專案。</span><span class="sxs-lookup"><span data-stu-id="dd44c-114">If no success message appears, troubleshoot the map project.</span></span>  
  
 <span data-ttu-id="dd44c-115">若要繼續[步驟 10： 建立協調流程](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md)。</span><span class="sxs-lookup"><span data-stu-id="dd44c-115">Proceed to [Step 10: Create an Orchestration](../../adapters-and-accelerators/accelerator-hl7/step-10-create-an-orchestration.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd44c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd44c-116">See Also</span></span>  
 [<span data-ttu-id="dd44c-117">訊息擴充教學課程</span><span class="sxs-lookup"><span data-stu-id="dd44c-117">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)