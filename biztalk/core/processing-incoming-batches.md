---
title: "處理內送的批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98f47903-933a-4bde-b320-f7689c3d8366
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca3781d9b7c1ed2190a8334f272c04d304669ace
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="processing-incoming-batches"></a><span data-ttu-id="c3671-102">處理內送批次</span><span class="sxs-lookup"><span data-stu-id="c3671-102">Processing Incoming Batches</span></span>
<span data-ttu-id="c3671-103">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 接收批次處理的 EDI 交換時，可以將交換分割為其交易集、以個別的方式處理每個交易集，或保留交換，以群組的方式處理所有的交易集。</span><span class="sxs-lookup"><span data-stu-id="c3671-103">When [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] receives a batched EDI interchange, it can either split the interchange into its transaction sets, processing each one separately, or it can preserve the interchange, processing all transaction sets as a group.</span></span>  
  
 <span data-ttu-id="c3671-104">決定批次中處理**本機主機設定**中的單向協議索引標籤頁面**協議屬性**適用於 X12 和 EDIFACT 協議 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c3671-104">You determine batch processing in the **Local Host Settings** page of the one-way agreement tabs in the **Agreement Properties** dialog box for both X12 and EDIFACT agreements.</span></span> <span data-ttu-id="c3671-105">保留交換時，您可以選擇發生錯誤時要擱置交換或交易集。</span><span class="sxs-lookup"><span data-stu-id="c3671-105">When you preserve the interchange, you have the choice to suspend either the interchange or the transaction sets if an error occurs.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3671-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="c3671-106">In This Section</span></span>  
  
-   [<span data-ttu-id="c3671-107">分割批次的 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="c3671-107">Splitting a Batched EDI Interchange</span></span>](../core/splitting-a-batched-edi-interchange.md)  
  
-   [<span data-ttu-id="c3671-108">分割 HIPAA 子文件</span><span class="sxs-lookup"><span data-stu-id="c3671-108">Splitting HIPAA Subdocuments</span></span>](../core/splitting-hipaa-subdocuments.md)  
  
-   [<span data-ttu-id="c3671-109">保留收到的批次 EDI 交換</span><span class="sxs-lookup"><span data-stu-id="c3671-109">Preserving a Received Batched EDI Interchange</span></span>](../core/preserving-a-received-batched-edi-interchange.md)