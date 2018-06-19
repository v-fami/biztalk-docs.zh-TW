---
title: 如何偵測運算質組態問題 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 32afc333-934c-4ffb-b1b5-61af07157200
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f8561156091c992e9329ef7d9627589eff9e0ed6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25968964"
---
# <a name="how-to-detect-configuration-issues-for-a-functoid"></a><span data-ttu-id="cc259-102">如何偵測運算質的組態問題</span><span class="sxs-lookup"><span data-stu-id="cc259-102">How to Detect Configuration Issues for a Functoid</span></span>
<span data-ttu-id="cc259-103">使用對應時，您可能會遇到運算質和/或連結組態的問題。</span><span class="sxs-lookup"><span data-stu-id="cc259-103">While working with maps, you might encounter issues with configuration of a functoid and/or link.</span></span> <span data-ttu-id="cc259-104">BizTalk 對應工具使用虛擬化機制，有助於快速識別和運算質組態相關的問題。</span><span class="sxs-lookup"><span data-stu-id="cc259-104">The BizTalk Mapper uses a visualization mechanism to help quickly identify problems associated with a functoid configuration.</span></span> <span data-ttu-id="cc259-105">此視覺化指示會呈現為運算質圖示上的警告註解 (如例如![運算質 IntelliSense](../core/media/mapper-functoidintellisense.gif "Mapper_FunctoidIntelliSense")) 關聯性檢視中。</span><span class="sxs-lookup"><span data-stu-id="cc259-105">This visual indication renders as a warning annotation on the functoid icon (for e.g. ![Functoid IntelliSense](../core/media/mapper-functoidintellisense.gif "Mapper_FunctoidIntelliSense")) in the relationship view.</span></span> <span data-ttu-id="cc259-106">本主題提供有關如何偵測運算質組態問題的資訊。</span><span class="sxs-lookup"><span data-stu-id="cc259-106">This topic provides information about how to detect the configuration issues for a functoid.</span></span>  
  
 <span data-ttu-id="cc259-107">當對應工具偵測到運算質未正確設定時，就會顯示警告狀態圖示。</span><span class="sxs-lookup"><span data-stu-id="cc259-107">The warning status icon appears when the Mapper detects that a functoid is not properly configured.</span></span> <span data-ttu-id="cc259-108">將滑鼠指標移到運算質上方也會顯示對應工具識別之問題的簡短資訊。</span><span class="sxs-lookup"><span data-stu-id="cc259-108">Moving the mouse over the functoid also displays brief information of the issue identified by the Mapper.</span></span> <span data-ttu-id="cc259-109">例如，如果運算質未達到有效輸入數目下限，運算值的工具提示會說明需要的輸入參數數目。</span><span class="sxs-lookup"><span data-stu-id="cc259-109">For example, if a functoid does not have minimum number of valid inputs, the tooltip for the functoid mentions the number of input parameters required.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="cc259-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="cc259-110">Prerequisites</span></span>  
 <span data-ttu-id="cc259-111">此作業需要執行中的 BizTalk 對應工具。</span><span class="sxs-lookup"><span data-stu-id="cc259-111">This operation requires that BizTalk Mapper is running.</span></span>  
  
### <a name="to-detect-configuration-issues-for-a-functoid"></a><span data-ttu-id="cc259-112">偵測運算質的組態問題</span><span class="sxs-lookup"><span data-stu-id="cc259-112">To detect configuration issues for a functoid</span></span>  
  
1.  <span data-ttu-id="cc259-113">將必要的運算質從工具箱拖曳到格線頁。</span><span class="sxs-lookup"><span data-stu-id="cc259-113">Drag the required functoid from the toolbox onto the grid page.</span></span> <span data-ttu-id="cc259-114">您會看到運算質帶有警告圖示。</span><span class="sxs-lookup"><span data-stu-id="cc259-114">You see the functoid with a warning icon.</span></span>  
  
2.  <span data-ttu-id="cc259-115">您可以執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="cc259-115">You can do one of the following:</span></span>  
  
    -   <span data-ttu-id="cc259-116">將滑鼠指標移到運算質上方。</span><span class="sxs-lookup"><span data-stu-id="cc259-116">Move the mouse pointer on the functoid.</span></span> <span data-ttu-id="cc259-117">工具提示會顯示關於錯誤和您必須採取之動作的資訊。</span><span class="sxs-lookup"><span data-stu-id="cc259-117">The tooltip displays information about the error and what you need to do.</span></span>  
  
         <span data-ttu-id="cc259-118">下圖顯示設定「加法」運算質時所出現含錯誤資訊的工具提示。</span><span class="sxs-lookup"><span data-stu-id="cc259-118">The following figure displays a tooltip with error information while configuring the functoid “Addition.”</span></span>  
  
         <span data-ttu-id="cc259-119">![運算質組態中的錯誤偵測](../core/media/errordetectionfunctoid.gif "ErrorDetectionFunctoid")</span><span class="sxs-lookup"><span data-stu-id="cc259-119">![Error detection in functoid configuration](../core/media/errordetectionfunctoid.gif "ErrorDetectionFunctoid")</span></span>  
  
    -   <span data-ttu-id="cc259-120">按兩下運算質。</span><span class="sxs-lookup"><span data-stu-id="cc259-120">Double-click the functoid.</span></span> <span data-ttu-id="cc259-121">**設定\<運算質\>運算質**對話方塊會顯示針對輸入參數的警告圖示。</span><span class="sxs-lookup"><span data-stu-id="cc259-121">The **Configure \<Functoid\> Functoid** dialog box displays warning icons against the input parameters.</span></span> <span data-ttu-id="cc259-122">這表示所選運算質未設定輸入參數。</span><span class="sxs-lookup"><span data-stu-id="cc259-122">This indicates that the input parameters of the selected functoid are not configured.</span></span>  
  
         <span data-ttu-id="cc259-123">下圖顯示關於「加法」運算質之輸入參數的錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="cc259-123">The following figure displays error information about input parameters for the “Addition” functoid.</span></span>  
  
         <span data-ttu-id="cc259-124">![運算質未設定時顯示的警告](../core/media/configure-input-parameters-warningicon.gif "Configure_input_parameters_WarningIcon")</span><span class="sxs-lookup"><span data-stu-id="cc259-124">![Warning displayed when functoid is not configured](../core/media/configure-input-parameters-warningicon.gif "Configure_input_parameters_WarningIcon")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc259-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="cc259-125">See Also</span></span>  
 [<span data-ttu-id="cc259-126">在 BizTalk 對應工具中使用增強功能</span><span class="sxs-lookup"><span data-stu-id="cc259-126">Using Enhanced Features in BizTalk Mapper</span></span>](../core/using-enhanced-features-in-biztalk-mapper.md)