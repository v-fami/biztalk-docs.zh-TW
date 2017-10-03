---
title: "設定 CIDX 解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- CIDX, process configuration
- creating, CIDX solutions
- CIDX, connecting to Elemica network
- agreements, CIDX
- process configuration, CIDX
- CIDX, agreements
- PIPs, importing for CIDX
- CIDX, PIPs
- CIDX, creating solutions
- CIDX, importing PIPs
- PIPs, CIDX
ms.assetid: 7f1f159f-3b09-4efd-907b-9a75f7f3ecd1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab617efc701551f1d5bcbae2a292676cc4f33251
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="setting-up-a-cidx-solution"></a><span data-ttu-id="24c64-102">設定 CIDX 解決方案</span><span class="sxs-lookup"><span data-stu-id="24c64-102">Setting Up a CIDX Solution</span></span>
<span data-ttu-id="24c64-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 支援 CIDX (化學產業資料交換) XML 訊息交換 (CIDX Chem eStandards 2.0 版和 3.0 版)。</span><span class="sxs-lookup"><span data-stu-id="24c64-103">Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] support for CIDX (Chemical Industry Data Exchange) XML message exchange (CIDX Chem eStandards versions 2.0 and 3.0).</span></span> <span data-ttu-id="24c64-104">本主題說明如何執行下列動作來設定 CIDX 解決方案：</span><span class="sxs-lookup"><span data-stu-id="24c64-104">This topic describes how to set up a CIDX solution by doing the following:</span></span>  
  
-   <span data-ttu-id="24c64-105">設定程序組態</span><span class="sxs-lookup"><span data-stu-id="24c64-105">Setting up a process configuration</span></span>  
  
-   <span data-ttu-id="24c64-106">設定協議</span><span class="sxs-lookup"><span data-stu-id="24c64-106">Setting up an agreement</span></span>  
  
-   <span data-ttu-id="24c64-107">套用 PIP</span><span class="sxs-lookup"><span data-stu-id="24c64-107">Applying a PIP</span></span>  
  
-   <span data-ttu-id="24c64-108">匯入以 XSD 為基礎的 PIP</span><span class="sxs-lookup"><span data-stu-id="24c64-108">Importing an XSD-based PIP</span></span>  
  
-   <span data-ttu-id="24c64-109">連線到 Elemica 網路</span><span class="sxs-lookup"><span data-stu-id="24c64-109">Connecting to the Elemica Network</span></span>  
  
## <a name="setting-up-a-cidx-process-configuration"></a><span data-ttu-id="24c64-110">設定 CIDX 程序組態</span><span class="sxs-lookup"><span data-stu-id="24c64-110">Setting Up a CIDX Process Configuration</span></span>  
 <span data-ttu-id="24c64-111">若要設定 CIDX eStandards 訊息交換，您必須建立具有下列屬性的程序組態：</span><span class="sxs-lookup"><span data-stu-id="24c64-111">To set up a CIDX eStandards message exchange, you need to create a process configuration that has the following properties:</span></span>  
  
-   <span data-ttu-id="24c64-112">**標準**屬性設定為處理序組態設定中的**CIDX**</span><span class="sxs-lookup"><span data-stu-id="24c64-112">**Standard** property in the process configuration settings set to **CIDX**</span></span>  
  
-   <span data-ttu-id="24c64-113">**單向動作**屬性設定為處理序組態設定中的**，則為 True**</span><span class="sxs-lookup"><span data-stu-id="24c64-113">**Is Single Action** property in the process configuration settings set to **True**</span></span>  
  
-   <span data-ttu-id="24c64-114">**0A1 協議**屬性設定為交易夥伴協議中的**No 0A1**</span><span class="sxs-lookup"><span data-stu-id="24c64-114">**0A1 agreement** property in the trading partner agreement set to **No 0A1**</span></span>  
  
 <span data-ttu-id="24c64-115">如需詳細資訊，請參閱[設定 CIDX eStandards 訊息交換](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)。</span><span class="sxs-lookup"><span data-stu-id="24c64-115">For more information, see [Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md).</span></span>  
  
## <a name="creating-a-cidx-agreement"></a><span data-ttu-id="24c64-116">建立 CIDX 協議</span><span class="sxs-lookup"><span data-stu-id="24c64-116">Creating a CIDX Agreement</span></span>  
 <span data-ttu-id="24c64-117">要設定 CIDX eStandards 訊息交換，您必須建立具有下列屬性的協議：</span><span class="sxs-lookup"><span data-stu-id="24c64-117">To set up a CIDX eStandards message exchange, you need to create an agreement that has the following properties:</span></span>  
  
-   <span data-ttu-id="24c64-118">**RNIF 版本**協議設定中設定為屬性**V01.10.00**</span><span class="sxs-lookup"><span data-stu-id="24c64-118">**RNIF Version** property in the agreement settings set to **V01.10.00**</span></span>  
  
-   <span data-ttu-id="24c64-119">**0A1 協議**協議設定中設定為屬性**No 0A1**</span><span class="sxs-lookup"><span data-stu-id="24c64-119">**0A1 agreement** property in the agreement settings set to **No 0A1**</span></span>  
  
 <span data-ttu-id="24c64-120">如需詳細資訊，請參閱[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)。</span><span class="sxs-lookup"><span data-stu-id="24c64-120">For more information, see [Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md).</span></span>  
  
## <a name="applying-a-pip-for-cidx"></a><span data-ttu-id="24c64-121">對 CIDX 套用 PIP</span><span class="sxs-lookup"><span data-stu-id="24c64-121">Applying a PIP for CIDX</span></span>  
 <span data-ttu-id="24c64-122">若要將 PIP 套用至 CIDX 實作，將**標準**程序組態設定檔中的屬性**CIDX**。</span><span class="sxs-lookup"><span data-stu-id="24c64-122">To apply a PIP to a CIDX implementation, set the **Standard** property in the process configuration profile to **CIDX**.</span></span> <span data-ttu-id="24c64-123">當您完成之後，您將能夠輸入的值**訊息標準**，**標準版本**，和**承載繫結識別碼**。</span><span class="sxs-lookup"><span data-stu-id="24c64-123">After you have finished, you will be able to enter values for the **Message standard**, **Standard version**, and **Payload binding ID**.</span></span> <span data-ttu-id="24c64-124">您可以在 CIDX Chem eStandards 的規格中找到這些值。</span><span class="sxs-lookup"><span data-stu-id="24c64-124">You can find these values in the CIDX Chem eStandards specification.</span></span>  
  
## <a name="importing-an-xsd-based-pip-for-cidx"></a><span data-ttu-id="24c64-125">對 CIDX 匯入以 XSD 為基礎的 PIP</span><span class="sxs-lookup"><span data-stu-id="24c64-125">Importing an XSD-based PIP for CIDX</span></span>  
 <span data-ttu-id="24c64-126">若要對 CIDX，匯入以 XSD 為基礎的 PIP，您必須從在 CIDX.org 下載 PIP 的 ZIP 檔案[http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361)。</span><span class="sxs-lookup"><span data-stu-id="24c64-126">To import an XSD-based PIP for CIDX, you need to download the PIP's ZIP file from CIDX.org at [http://go.microsoft.com/FWLink/?LinkID=33859](http://go.microsoft.com/FWLink/?LinkID=62361).</span></span> <span data-ttu-id="24c64-127">請依照下列所述匯入程序[匯入以 XSD 為基礎的 PIP](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)。</span><span class="sxs-lookup"><span data-stu-id="24c64-127">Follow the import procedure described in [Importing an XSD-based PIP](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md).</span></span>  
  
## <a name="connecting-to-the-elemica-network"></a><span data-ttu-id="24c64-128">連線到 Elemica 網路</span><span class="sxs-lookup"><span data-stu-id="24c64-128">Connecting to the Elemica Network</span></span>  
 <span data-ttu-id="24c64-129">您可以使用 Elemica Connectivity Pack 中的專案檔，自訂 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 以連接到 Elemica。</span><span class="sxs-lookup"><span data-stu-id="24c64-129">You can customize [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] to connect to Elemica using project files in the Elemica Connectivity Pack.</span></span> <span data-ttu-id="24c64-130">您可以下載 Connectivity Pack 從[http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195)。</span><span class="sxs-lookup"><span data-stu-id="24c64-130">You can download the Connectivity Pack from [http://go.microsoft.com/fwlink/?LinkId=46195](http://go.microsoft.com/fwlink/?LinkId=46195).</span></span> <span data-ttu-id="24c64-131">如需詳細資訊，請參閱 < 連接到 Elemica 網路利用 BizTalk Accelerator for RosettaNet 3.0 > 技術白皮書在 MSDN 上[http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539)。</span><span class="sxs-lookup"><span data-stu-id="24c64-131">For more information, see the “Connecting to the Elemica Network with BizTalk Accelerator for RosettaNet 3.0” white paper on MSDN at [http://go.microsoft.com/fwlink/?linkid=46539](http://go.microsoft.com/fwlink/?linkid=46539).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24c64-132">《利用 BizTalk Accelerator for RosettaNet 3.0 連線至 Elemica 網路》白皮書 (英文) 中的資訊對 [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)] 有效。</span><span class="sxs-lookup"><span data-stu-id="24c64-132">The information in the "Connecting to the Elemica Network with BizTalk Accelerator for RosettaNet 3.0" white paper is valid for [!INCLUDE[BTARN_CurrentVersion_abbrev](../../includes/btarn-currentversion-abbrev-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c64-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="24c64-133">See Also</span></span>  
 <span data-ttu-id="24c64-134">[CIDX 支援](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md) </span><span class="sxs-lookup"><span data-stu-id="24c64-134">[CIDX Support](../../adapters-and-accelerators/accelerator-rosettanet/cidx-support.md) </span></span>  
 <span data-ttu-id="24c64-135">[CIDX 訊息標準](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md) </span><span class="sxs-lookup"><span data-stu-id="24c64-135">[CIDX Messaging Standards](../../adapters-and-accelerators/accelerator-rosettanet/cidx-messaging-standards.md) </span></span>  
 <span data-ttu-id="24c64-136">[設定 CIDX eStandards 訊息交換](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md) </span><span class="sxs-lookup"><span data-stu-id="24c64-136">[Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md) </span></span>  
 <span data-ttu-id="24c64-137">[建立或編輯協議](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md) </span><span class="sxs-lookup"><span data-stu-id="24c64-137">[Creating or Editing an Agreement](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md) </span></span>  
 [<span data-ttu-id="24c64-138">匯入以 XSD 為基礎的 PIP</span><span class="sxs-lookup"><span data-stu-id="24c64-138">Importing an XSD-based PIP</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/importing-an-xsd-based-pip.md)