---
title: HL7 加速器，在 BizTalk Server 中的合作對象 索引標籤 |Microsoft 文件
description: 若要檢視現有的合作對象，請使用 BTAHL7 組態總管和 BizTalk Server 中設定通知
ms.custom: ''
ms.date: 08/14/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e01052c8-25c5-4736-8403-33f16fbd3fb7
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d8572da051d046d46b6e895f11f07d3f9d9771c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206134"
---
# <a name="parties-in-btahl7-configuration-explorer"></a><span data-ttu-id="8ba07-103">BTAHL7 組態總管 中的合作對象</span><span class="sxs-lookup"><span data-stu-id="8ba07-103">Parties in BTAHL7 Configuration Explorer</span></span>
<span data-ttu-id="8ba07-104">您使用**合作對象**索引標籤來檢視可用的合作對象，並指定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態特定合作對象，以及設定通知的內容。</span><span class="sxs-lookup"><span data-stu-id="8ba07-104">You use the **Parties** tab to view the available parties and specify [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] configuration for a particular party that you choose, and to configure properties for acknowledgments.</span></span> 

## <a name="parties-ui-explained"></a><span data-ttu-id="8ba07-105">合作對象 UI 說明</span><span class="sxs-lookup"><span data-stu-id="8ba07-105">Parties UI explained</span></span>
<span data-ttu-id="8ba07-106">**合作對象** 索引標籤包含的左邊和右邊的窗格。</span><span class="sxs-lookup"><span data-stu-id="8ba07-106">The **Parties** tab contains both a left and right pane.</span></span> <span data-ttu-id="8ba07-107">可用的合作對象會出現在左窗格中。</span><span class="sxs-lookup"><span data-stu-id="8ba07-107">The available parties appear in the left pane.</span></span> <span data-ttu-id="8ba07-108">右窗格包含下列索引標籤，選取合作對象：</span><span class="sxs-lookup"><span data-stu-id="8ba07-108">The right pane contains the following tabs for the selected party:</span></span>  
  
-   <span data-ttu-id="8ba07-109">**合作對象別名**。</span><span class="sxs-lookup"><span data-stu-id="8ba07-109">**Party Aliases**.</span></span> <span data-ttu-id="8ba07-110">您可以使用此索引標籤來檢視從左窗格中選取的合作對象的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8ba07-110">Use this tab to view information about the party you have selected from the left pane.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ba07-111">您可以使用 BizTalk 總管 中建立合作對象。</span><span class="sxs-lookup"><span data-stu-id="8ba07-111">You use BizTalk Explorer to create parties.</span></span>  
  
-   <span data-ttu-id="8ba07-112">**批次定義**。</span><span class="sxs-lookup"><span data-stu-id="8ba07-112">**Batch Definition**.</span></span> <span data-ttu-id="8ba07-113">使用此索引標籤來設定[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]批次處理。</span><span class="sxs-lookup"><span data-stu-id="8ba07-113">Use this tab to configure [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] batching.</span></span>  
  
-   <span data-ttu-id="8ba07-114">**批次排程**。</span><span class="sxs-lookup"><span data-stu-id="8ba07-114">**Batch Schedule**.</span></span> <span data-ttu-id="8ba07-115">若要啟用輸出批次中使用此索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8ba07-115">Use this tab to activate outbound batches.</span></span>  
  
-   <span data-ttu-id="8ba07-116">**通知**。</span><span class="sxs-lookup"><span data-stu-id="8ba07-116">**Acknowledgment**.</span></span> <span data-ttu-id="8ba07-117">您可以使用這個索引標籤，指定輸入和產生通知的屬性。</span><span class="sxs-lookup"><span data-stu-id="8ba07-117">Use this tab to specify the properties for inbound and generated acknowledgments.</span></span>  
  
-   <span data-ttu-id="8ba07-118">**驗證**。</span><span class="sxs-lookup"><span data-stu-id="8ba07-118">**Validation**.</span></span> <span data-ttu-id="8ba07-119">您可以使用此索引標籤，選取輸入和產生訊息的訊息驗證選項。</span><span class="sxs-lookup"><span data-stu-id="8ba07-119">Use this tab to select the message validation options for inbound and generated messages.</span></span>  
  
-   <span data-ttu-id="8ba07-120">**MSH 對應**。</span><span class="sxs-lookup"><span data-stu-id="8ba07-120">**MSH Map**.</span></span> <span data-ttu-id="8ba07-121">若要啟用內送訊息的訊息標頭轉換中使用此索引標籤。</span><span class="sxs-lookup"><span data-stu-id="8ba07-121">Use this tab to enable message header transformations for inbound messages.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8ba07-122">您必須設定合作對象別名、 批次定義、 批次的排程，以及所有交易的合作對象的通知資訊。</span><span class="sxs-lookup"><span data-stu-id="8ba07-122">You must configure party aliases, batch definitions, batch schedules, and acknowledgment information for all trading parties.</span></span>  
    > 
    >  <span data-ttu-id="8ba07-123">您可以重新整理 合作對象 清單中，按下 F5，或以滑鼠右鍵按一下合作對象 清單中，並選取**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="8ba07-123">You can refresh the parties list by pressing F5, or by right-clicking the parties list, and select **Refresh**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="8ba07-124">後續的步驟</span><span class="sxs-lookup"><span data-stu-id="8ba07-124">Next steps</span></span>  
  
-   [<span data-ttu-id="8ba07-125">合作對象別名 索引標籤</span><span class="sxs-lookup"><span data-stu-id="8ba07-125">Party Aliases Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/party-aliases-tab.md)  
  
-   [<span data-ttu-id="8ba07-126">批次定義索引標籤</span><span class="sxs-lookup"><span data-stu-id="8ba07-126">Batch Definition Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/batch-definition-tab.md)  
  
-   [<span data-ttu-id="8ba07-127">批次排程 索引標籤</span><span class="sxs-lookup"><span data-stu-id="8ba07-127">Batch Schedule Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/batch-schedule-tab.md)  
  
-   [<span data-ttu-id="8ba07-128">通知 索引標籤</span><span class="sxs-lookup"><span data-stu-id="8ba07-128">Acknowledgment Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-tab.md)  
  
-   [<span data-ttu-id="8ba07-129">驗證索引標籤</span><span class="sxs-lookup"><span data-stu-id="8ba07-129">Validation Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/validation-tab.md)  
  
-   [<span data-ttu-id="8ba07-130">MSH 對應 索引標籤</span><span class="sxs-lookup"><span data-stu-id="8ba07-130">MSH Map Tab</span></span>](../../adapters-and-accelerators/accelerator-hl7/msh-map-tab.md)