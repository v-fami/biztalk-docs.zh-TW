---
title: 批次定義索引標籤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.tab.batchdefinition
helpviewer_keywords:
- Batch Definition tab [Configuration Explorer]
- batching, configuring
- configuring, batching
ms.assetid: fe8685ef-5de5-4337-8691-8e4094056ace
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2270625a6e4512f2a99bea7a06812b601b48d44c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22204510"
---
# <a name="batch-definition-tab"></a><span data-ttu-id="5e1d5-102">批次定義索引標籤</span><span class="sxs-lookup"><span data-stu-id="5e1d5-102">Batch Definition Tab</span></span>
<span data-ttu-id="5e1d5-103">您使用**批次定義**索引標籤上，以在 輸入批次處理，批次 / 出批次處理，批次，然後選取 為輸出批次處理的可用結構描述。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-103">You use the **Batch Definition** tab to enable inbound batching, batch in/batch out batching, and select available schemas for outbound batching.</span></span>  
  
 <span data-ttu-id="5e1d5-104">在**BTAHL7 Configuration 總管**對話方塊**批次定義**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="5e1d5-104">In the **BTAHL7 Configuration Explorer** dialog box, on the **Batch Definition** tab, do the following:</span></span>  
  
|<span data-ttu-id="5e1d5-105">使用</span><span class="sxs-lookup"><span data-stu-id="5e1d5-105">Use this</span></span>|<span data-ttu-id="5e1d5-106">動作</span><span class="sxs-lookup"><span data-stu-id="5e1d5-106">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="5e1d5-107">**所需的片段**</span><span class="sxs-lookup"><span data-stu-id="5e1d5-107">**Fragmentation required**</span></span>|<span data-ttu-id="5e1d5-108">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="5e1d5-108">Select one of the following options:</span></span><br /><br /> <span data-ttu-id="5e1d5-109">-   **[是]**。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-109">-   **Yes**.</span></span> <span data-ttu-id="5e1d5-110">若要啟用片段。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-110">To enable fragmentation.</span></span><br /><span data-ttu-id="5e1d5-111">-   **否**。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-111">-   **No**.</span></span> <span data-ttu-id="5e1d5-112">若要停用片段。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-112">To disable fragmentation.</span></span> <span data-ttu-id="5e1d5-113">**注意：** 新合作對象，**片段所需**預設為**否**。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-113">**Note:**  For a new party, **Fragmentation Required** defaults to **No**.</span></span>|  
|<span data-ttu-id="5e1d5-114">**可復原交換所需的支援**</span><span class="sxs-lookup"><span data-stu-id="5e1d5-114">**Recoverable interchange support required**</span></span>|<span data-ttu-id="5e1d5-115">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="5e1d5-115">Select one of the following options:</span></span><br /><br /> <span data-ttu-id="5e1d5-116">-   **True**。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-116">-   **True**.</span></span> <span data-ttu-id="5e1d5-117">若要啟用可復原交換支援。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-117">To enable recoverable interchange support.</span></span><br /><span data-ttu-id="5e1d5-118">-   **FALSE**。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-118">-   **FALSE**.</span></span> <span data-ttu-id="5e1d5-119">若要停用可復原交換支援。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-119">To disable recoverable interchange support.</span></span> <span data-ttu-id="5e1d5-120">**注意：** 新合作對象，**片段所需**預設為**FALSE** ，才會啟用的值**片段所需**是**否**。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-120">**Note:**  For a new party, **Fragmentation Required** defaults to **FALSE** and is enabled only if the value of **Fragmentation Required** is **No**.</span></span>|  
|<span data-ttu-id="5e1d5-121">**選取訊息**</span><span class="sxs-lookup"><span data-stu-id="5e1d5-121">**Select Messages**</span></span>|<span data-ttu-id="5e1d5-122">選取您想要做為批次傳送，從 可用的訊息 視窗，然後按一下 向右箭號來移動訊息類型 (**>>**)。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-122">Select the message types you want to send as a batch from the Available Messages window and then click the Move to right arrow (**>>**).</span></span><br /><br /> <span data-ttu-id="5e1d5-123">若批次內送通知訊息，您必須新增 ACK 訊息類型。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-123">To batch incoming ACK messages, you must add the ACK message type.</span></span> <span data-ttu-id="5e1d5-124">您所部署的 ACK 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-124">You do so by deploying the ACK message schema.</span></span>|  
|<span data-ttu-id="5e1d5-125">**選取訊息通知**</span><span class="sxs-lookup"><span data-stu-id="5e1d5-125">**Select Message Acknowledgments**</span></span>|<span data-ttu-id="5e1d5-126">選取您想要的訊息類型[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]以做為批次傳送通知，從 [可用的訊息通知] 視窗中，然後按一下向右箭號來移動 (**>>**)。</span><span class="sxs-lookup"><span data-stu-id="5e1d5-126">Select the message types for which you want [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] to send the acknowledgments as a batch from the Available Message Acks window, and then click the Move to right arrow (**>>**).</span></span>|