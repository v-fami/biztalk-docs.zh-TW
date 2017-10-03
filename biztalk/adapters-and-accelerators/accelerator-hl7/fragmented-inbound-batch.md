---
title: "分割輸入批次 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, fragmenting messages
- messages, fragmenting
- fragmenting messages
ms.assetid: 5844710e-f662-48a3-bf1a-bc1ba91e678a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0807bbe83ea2f477a7e1625488ebbecf578f3adc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="fragmented-inbound-batch"></a><span data-ttu-id="25e49-102">分散的傳入批次</span><span class="sxs-lookup"><span data-stu-id="25e49-102">Fragmented Inbound Batch</span></span>
<span data-ttu-id="25e49-103">您可以設定[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]接收訊息批次，從擷取訊息批次，並再將個別的訊息路由至目的地系統。</span><span class="sxs-lookup"><span data-stu-id="25e49-103">You can configure [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] to receive a message batch, extract the messages from the batch, and then route the individual messages to the destination system.</span></span> <span data-ttu-id="25e49-104">如果您啟用分散的片段，為個別的訊息; 輸入批次片段否則，批次是處理，做為單一 'batch' 或交換路由傳送。</span><span class="sxs-lookup"><span data-stu-id="25e49-104">If you enable fragmentation, the inbound batch fragments into individual messages; otherwise, the batch is processed and routed as a single 'batch' or interchange.</span></span> <span data-ttu-id="25e49-105">您可以使用 BTAHL7 Configuration 總管來啟用批次處理。</span><span class="sxs-lookup"><span data-stu-id="25e49-105">You use BTAHL7 Configuration Explorer to enable batching.</span></span> <span data-ttu-id="25e49-106">如需啟用批次處理的詳細資訊，請參閱[設定批次處理](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)。</span><span class="sxs-lookup"><span data-stu-id="25e49-106">For more information about enabling batching, see [Configuring Batching](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md).</span></span>  
  
 <span data-ttu-id="25e49-107">下列說明典型的分散輸入批次的案例：</span><span class="sxs-lookup"><span data-stu-id="25e49-107">The following describes a typical fragmented inbound batch scenario:</span></span>  
  
1.  <span data-ttu-id="25e49-108">A，系統上執行的特定業務應用程式會將訊息批次傳送至 BTAHL7。</span><span class="sxs-lookup"><span data-stu-id="25e49-108">A line-of-business application, running on System A, sends a message batch to BTAHL7.</span></span>  
  
     <span data-ttu-id="25e49-109">批次訊息可以是兩個不同的格式。</span><span class="sxs-lookup"><span data-stu-id="25e49-109">Batch messages can be in two different formats.</span></span> <span data-ttu-id="25e49-110">BTAHL7 可以處理下列格式：</span><span class="sxs-lookup"><span data-stu-id="25e49-110">BTAHL7 can process the following formats:</span></span>  
  
    -   <span data-ttu-id="25e49-111">格式 1： 包含一個檔案標頭和結尾 (FHS/FTS) 配對和一或多個批次標頭和結尾 (BHS/BTS)。</span><span class="sxs-lookup"><span data-stu-id="25e49-111">Format 1: Includes one file header and trailer (FHS/FTS) pair and one or more batch header and trailers (BHS/BTS).</span></span>  
  
        ```  
        FHS  
        BHS  
        MSH  
        .............  
        MSH  
        ...........  
        BTS  
        BHS  
        MSH  
        ..............  
        MSH  
        ...............  
        BTS  
        FTS  
        ```  
  
    -   <span data-ttu-id="25e49-112">格式 2： 不包含 HL7 定義檔和批次的包裝函式，並擱置一系列的資料流中的訊息。</span><span class="sxs-lookup"><span data-stu-id="25e49-112">Format 2: Does not contain HL7 defined file and batch wrappers, and suspends a series are messages in a stream.</span></span>  
  
        ```  
        MSH  
        .......  
        MSH  
        ........  
        MSH  
        .........  
        ```  
  
2.  <span data-ttu-id="25e49-113">BTAHL7 會建立個別的訊息批次，然後驗證適當的結構描述的個別訊息。</span><span class="sxs-lookup"><span data-stu-id="25e49-113">BTAHL7 creates individual messages from the batch and then verifies the individual messages against the appropriate schemas.</span></span>  
  
3.  <span data-ttu-id="25e49-114">BTAHL7 會為每個批次擷取的訊息傳送給系統的個別通知訊息。</span><span class="sxs-lookup"><span data-stu-id="25e49-114">BTAHL7 sends a separate acknowledgment message to System A for each message extracted from the batch.</span></span>  
  
4.  <span data-ttu-id="25e49-115">BTAHL7 會將個別的訊息路由至目的地系統根據個別訊息，而不是訊息批次標頭中的路由資訊。</span><span class="sxs-lookup"><span data-stu-id="25e49-115">BTAHL7 routes the individual messages to the destination system based on the routing information in the individual messages, rather than the message batch header.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="25e49-116">BTAHL7 不會驗證批次和檔案的標頭/結尾時**FHS3**欄位 （傳送合作對象） 包含已啟用的分散程度的交易夥伴。</span><span class="sxs-lookup"><span data-stu-id="25e49-116">BTAHL7 does not validate batch and file headers/trailers when the **FHS3** field (sending party) contains a trading partner that has fragmentation enabled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25e49-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25e49-117">See Also</span></span>  
 [<span data-ttu-id="25e49-118">設定批次處理</span><span class="sxs-lookup"><span data-stu-id="25e49-118">Configuring Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-batching.md)