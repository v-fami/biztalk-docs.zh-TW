---
title: "設定連結 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10050c28-0944-4073-afd2-54cd6c8d79a2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e3da50b626eeb65a137deb8a1a7ef4f2ee3e0609
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-links"></a><span data-ttu-id="31087-102">設定連結</span><span class="sxs-lookup"><span data-stu-id="31087-102">Configuring Links</span></span>

## <a name="overview"></a><span data-ttu-id="31087-103">概觀</span><span class="sxs-lookup"><span data-stu-id="31087-103">Overview</span></span>
<span data-ttu-id="31087-104">在顯示的格線頁中選取連結時，連結的屬性會顯示在 [[!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] 屬性] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="31087-104">Links have properties that are displayed in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Properties window when a link is selected in the displayed grid page.</span></span> <span data-ttu-id="31087-105">如需與連結相關聯之屬性的參考資訊，請參閱**連結屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="31087-105">For reference information about the properties associated with links, see **Link Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> 

## <a name="source-target-and-label"></a><span data-ttu-id="31087-106">來源、 目標和標籤</span><span class="sxs-lookup"><span data-stu-id="31087-106">Source, target and label</span></span>  
 <span data-ttu-id="31087-107">下列屬性會設定對應中的連結：</span><span class="sxs-lookup"><span data-stu-id="31087-107">The following properties configure links in a map:</span></span>  
  
-   <span data-ttu-id="31087-108">**來源連結**。</span><span class="sxs-lookup"><span data-stu-id="31087-108">**Source Links**.</span></span> <span data-ttu-id="31087-109">您使用**來源連結**屬性可設定從輸入執行個體訊息將會用來建構輸出執行個體訊息資料的本質。</span><span class="sxs-lookup"><span data-stu-id="31087-109">You use the **Source Links** property to configure the nature of the data from an input instance message that will be used to construct the output instance message.</span></span> <span data-ttu-id="31087-110">依照預設且最常用的選擇為使用輸入執行個體訊息的項目或屬性值。</span><span class="sxs-lookup"><span data-stu-id="31087-110">The default, and most common choice, is to use the element or attribute value from the input instance message.</span></span> <span data-ttu-id="31087-111">也有其他選擇，包括使用輸入執行個體訊息的項目名稱或屬性。</span><span class="sxs-lookup"><span data-stu-id="31087-111">Other choices are possible, including the use of the name of the element or attribute from the input instance message.</span></span> <span data-ttu-id="31087-112">如需這個屬性及其可用選項的詳細資訊，請參閱**連結屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="31087-112">For more information about this property and its available choices, see **Link Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
-   <span data-ttu-id="31087-113">**目標連結**。</span><span class="sxs-lookup"><span data-stu-id="31087-113">**Target Links**.</span></span> <span data-ttu-id="31087-114">您使用**目標連結**設定 BizTalk 對應工具如何比對節點階層層級的屬性。</span><span class="sxs-lookup"><span data-stu-id="31087-114">You use the **Target Links** property to configure how BizTalk Mapper will match node-hierarchy levels.</span></span> <span data-ttu-id="31087-115">依照預設，當輸出執行個體訊息建立時，會簡維來源結構描述階層。</span><span class="sxs-lookup"><span data-stu-id="31087-115">By default, source schema hierarchies are flattened as the output instance message is created.</span></span> <span data-ttu-id="31087-116">您也可以選擇保留階層，由上往下或由下往上比對連結。</span><span class="sxs-lookup"><span data-stu-id="31087-116">You can also choose to have hierarchies preserved, matching links from either the top down or from the bottom up.</span></span> <span data-ttu-id="31087-117">如需這個屬性及其可用選項的詳細資訊，請參閱**連結屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="31087-117">For more information about this property and its available choices, see **Link Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
-   <span data-ttu-id="31087-118">**標籤**。</span><span class="sxs-lookup"><span data-stu-id="31087-118">**Label**.</span></span> <span data-ttu-id="31087-119">您使用**標籤**屬性以建立連結比預設會使用 XPath 值更容易讀取的名稱。</span><span class="sxs-lookup"><span data-stu-id="31087-119">You use the **Label** property to create a more readable name for the link than the XPath value that is used by default.</span></span> <span data-ttu-id="31087-120">當連結用以作為表格驅動迴圈的輸入時，設定此屬性特別有用。</span><span class="sxs-lookup"><span data-stu-id="31087-120">Configuring this property is especially helpful when the link is used as an input for table-driven looping.</span></span> <span data-ttu-id="31087-121">如需此屬性及其可用選項以及表格驅動迴圈的詳細資訊，請參閱**連結屬性** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]。</span><span class="sxs-lookup"><span data-stu-id="31087-121">For more information about this property and its available choices, and about table-driven looping, see **Link Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> <span data-ttu-id="31087-122">另請參閱[表格迴圈和表格擷取程式運算質](../core/table-looping-and-table-extractor-functoids.md)分別。</span><span class="sxs-lookup"><span data-stu-id="31087-122">Also see [Table Looping and Table Extractor Functoids](../core/table-looping-and-table-extractor-functoids.md), respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31087-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31087-123">See Also</span></span>  
  [<span data-ttu-id="31087-124">如何編輯連結屬性</span><span class="sxs-lookup"><span data-stu-id="31087-124">How to Edit Link Properties</span></span>](../core/how-to-edit-link-properties.md)