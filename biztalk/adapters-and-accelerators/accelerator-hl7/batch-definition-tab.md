---
title: 批次定義索引標籤 |Microsoft Docs
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
ms.openlocfilehash: d8eb06321fc5025efa17796a79cddcbe2d14ef9e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970815"
---
# <a name="batch-definition-tab"></a><span data-ttu-id="d9431-102">批次定義索引標籤</span><span class="sxs-lookup"><span data-stu-id="d9431-102">Batch Definition Tab</span></span>
<span data-ttu-id="d9431-103">您使用**批次定義**啟用中的輸入批次，批次 / 批次出批次處理，索引標籤，然後選取 可用的結構描述的輸出批次。</span><span class="sxs-lookup"><span data-stu-id="d9431-103">You use the **Batch Definition** tab to enable inbound batching, batch in/batch out batching, and select available schemas for outbound batching.</span></span>  

 <span data-ttu-id="d9431-104">在  **BTAHL7 設定總管**對話方塊的 **批次定義**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="d9431-104">In the **BTAHL7 Configuration Explorer** dialog box, on the **Batch Definition** tab, do the following:</span></span>  


|                   <span data-ttu-id="d9431-105">使用</span><span class="sxs-lookup"><span data-stu-id="d9431-105">Use this</span></span>                   |                                                                                                                                                            <span data-ttu-id="d9431-106">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="d9431-106">To do this</span></span>                                                                                                                                                            |
|----------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|          <span data-ttu-id="d9431-107">**需要的片段**</span><span class="sxs-lookup"><span data-stu-id="d9431-107">**Fragmentation required**</span></span>          |                                                           <span data-ttu-id="d9431-108">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="d9431-108">Select one of the following options:</span></span><br /><br /> <span data-ttu-id="d9431-109">-   **是**。</span><span class="sxs-lookup"><span data-stu-id="d9431-109">-   **Yes**.</span></span> <span data-ttu-id="d9431-110">若要啟用片段。</span><span class="sxs-lookup"><span data-stu-id="d9431-110">To enable fragmentation.</span></span><br /><span data-ttu-id="d9431-111">-   **否**。</span><span class="sxs-lookup"><span data-stu-id="d9431-111">-   **No**.</span></span> <span data-ttu-id="d9431-112">若要停用片段。</span><span class="sxs-lookup"><span data-stu-id="d9431-112">To disable fragmentation.</span></span> <span data-ttu-id="d9431-113">**附註：** 新的合作對象**所需的分散程度**預設為**否**。</span><span class="sxs-lookup"><span data-stu-id="d9431-113">**Note:**  For a new party, **Fragmentation Required** defaults to **No**.</span></span>                                                           |
| <span data-ttu-id="d9431-114">**可復原交換所需的支援**</span><span class="sxs-lookup"><span data-stu-id="d9431-114">**Recoverable interchange support required**</span></span> | <span data-ttu-id="d9431-115">選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="d9431-115">Select one of the following options:</span></span><br /><br /> <span data-ttu-id="d9431-116">-   **True**。</span><span class="sxs-lookup"><span data-stu-id="d9431-116">-   **True**.</span></span> <span data-ttu-id="d9431-117">若要啟用可復原交換的支援。</span><span class="sxs-lookup"><span data-stu-id="d9431-117">To enable recoverable interchange support.</span></span><br /><span data-ttu-id="d9431-118">-   **FALSE**。</span><span class="sxs-lookup"><span data-stu-id="d9431-118">-   **FALSE**.</span></span> <span data-ttu-id="d9431-119">若要停用可復原交換的支援。</span><span class="sxs-lookup"><span data-stu-id="d9431-119">To disable recoverable interchange support.</span></span> <span data-ttu-id="d9431-120">**附註：** 新的合作對象，如**片段所需**預設為**FALSE**和才會啟用的值**片段所需**是**否**。</span><span class="sxs-lookup"><span data-stu-id="d9431-120">**Note:**  For a new party, **Fragmentation Required** defaults to **FALSE** and is enabled only if the value of **Fragmentation Required** is **No**.</span></span> |
|             <span data-ttu-id="d9431-121">**選取訊息**</span><span class="sxs-lookup"><span data-stu-id="d9431-121">**Select Messages**</span></span>              |                              <span data-ttu-id="d9431-122">選取您想要以批次傳送，從 可用的訊息 視窗，然後按一下 向右箭號來移動的訊息類型 (**>>**)。</span><span class="sxs-lookup"><span data-stu-id="d9431-122">Select the message types you want to send as a batch from the Available Messages window and then click the Move to right arrow (**>>**).</span></span><br /><br /> <span data-ttu-id="d9431-123">批次內送通知訊息，您必須加入通知訊息類型。</span><span class="sxs-lookup"><span data-stu-id="d9431-123">To batch incoming ACK messages, you must add the ACK message type.</span></span> <span data-ttu-id="d9431-124">您這樣做，藉由部署的 ACK 訊息結構描述。</span><span class="sxs-lookup"><span data-stu-id="d9431-124">You do so by deploying the ACK message schema.</span></span>                              |
|      <span data-ttu-id="d9431-125">**選取訊息通知**</span><span class="sxs-lookup"><span data-stu-id="d9431-125">**Select Message Acknowledgments**</span></span>      |                               <span data-ttu-id="d9431-126">選取您想要的訊息類型[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]要以批次傳送通知，從 [可用的訊息通知] 視窗中，然後按一下 [移至 [向右箭號 (**>>**)。</span><span class="sxs-lookup"><span data-stu-id="d9431-126">Select the message types for which you want [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] to send the acknowledgments as a batch from the Available Message Acks window, and then click the Move to right arrow (**>>**).</span></span>                                |

