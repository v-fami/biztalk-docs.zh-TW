---
title: "建立或編輯程序組態 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- process configuration, modifying
- process configuration, creating
- creating, process configuration
- modifying, process configuration
ms.assetid: 39cc2c93-0986-48d3-8c6f-4280ec9af4e0
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9130ab7370f8f6e1fcbe75bc7a85a6c74dfe328
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-or-editing-a-process-configuration"></a><span data-ttu-id="20897-102">建立或編輯程序組態</span><span class="sxs-lookup"><span data-stu-id="20897-102">Creating or Editing a Process Configuration</span></span>
<span data-ttu-id="20897-103">本章節描述如何建立或編輯流程組態，以實作的 「 交易夥伴介面程序 (PIP) 」，在[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="20897-103">This section describes how to create or edit a process configuration to implement a Partner Interface Process (PIP) in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="20897-104">RosettaNet PIP 定義兩個交易夥伴之間的商務程序對話。</span><span class="sxs-lookup"><span data-stu-id="20897-104">A RosettaNet PIP defines a business-process dialog between two trading partners.</span></span> <span data-ttu-id="20897-105">在[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]、 PIP 建立與夥伴，您必須先建立程序組態。</span><span class="sxs-lookup"><span data-stu-id="20897-105">In [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], to create a PIP with a partner, you must first create a process configuration.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="20897-106">使用此設定檔儲存 PIP 的所有組態特性。</span><span class="sxs-lookup"><span data-stu-id="20897-106"> uses this profile to store all configuration characteristics of the PIP.</span></span> <span data-ttu-id="20897-107">之後，您便可使用此組態，建立交易夥伴的協議。</span><span class="sxs-lookup"><span data-stu-id="20897-107">You can then use this configuration to create an agreement with the partner.</span></span>  
  
 <span data-ttu-id="20897-108">如需程序組態屬性，與建立或編輯程序組態的程序的資訊，請參閱[如何建立或編輯程序組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="20897-108">For information about process configuration properties, and procedures for creating or editing a process configuration, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span></span>  
  
 <span data-ttu-id="20897-109">建立新程序組態時，您的設定必須根據 RosettaNet 組織所維護的 PIP 規格文件。</span><span class="sxs-lookup"><span data-stu-id="20897-109">In creating a new process configuration, you must base the settings on the PIP specification document maintained by the RosettaNet organization.</span></span> <span data-ttu-id="20897-110">所有的程序組態設定都來自 PIP 規格，而 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 在大部分設定填入的預設值，都是欄位最常用的值。</span><span class="sxs-lookup"><span data-stu-id="20897-110">All process configuration settings come from the PIP specifications, and [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] populates most of the settings with default values that are the most typically used values for the fields.</span></span> <span data-ttu-id="20897-111">您必須確認設定與適當的 PIP 規格中的值一致。</span><span class="sxs-lookup"><span data-stu-id="20897-111">You must verify that the settings correspond to the values in the appropriate PIP specification.</span></span> <span data-ttu-id="20897-112">如需您所輸入的 PIP 設定如何對應至 PIP 規格中的指導方針的詳細資訊，請參閱[使用 PIP 規格建立程序組態](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="20897-112">For more information about how the PIP settings that you enter map to the guidance in the PIP specification, see [Using the PIP Specification to Create a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md).</span></span>  
  
 <span data-ttu-id="20897-113">程序組態可以是 RosettaNet 或 CIDX (化學工業資料交換)。</span><span class="sxs-lookup"><span data-stu-id="20897-113">The process configuration can be for either RosettaNet or CIDX (Chemical Industry Data Exchange).</span></span> <span data-ttu-id="20897-114">如需有關 CIDX 組態資訊，請參閱[設定 CIDX eStandards 訊息交換](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)。</span><span class="sxs-lookup"><span data-stu-id="20897-114">For information about a CIDX configuration, see [Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md).</span></span>  
  
 <span data-ttu-id="20897-115">當有使用中的程序時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援變更程序組態。</span><span class="sxs-lookup"><span data-stu-id="20897-115">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support changing a process configuration while there are active processes.</span></span> <span data-ttu-id="20897-116">如果您變更協議，則使用中的程序將會結束，並出現失敗。</span><span class="sxs-lookup"><span data-stu-id="20897-116">If you do so, the active processes will complete with failures.</span></span> <span data-ttu-id="20897-117">所有新的程序將會成功挑選新的組態設定。</span><span class="sxs-lookup"><span data-stu-id="20897-117">All new processes will successfully pick up the new configuration settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="20897-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="20897-118">In This Section</span></span>  
  
-   [<span data-ttu-id="20897-119">如何建立或編輯程序組態</span><span class="sxs-lookup"><span data-stu-id="20897-119">How to Create or Edit a Process Configuration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)  
  
-   [<span data-ttu-id="20897-120">使用 PIP 規格建立程序組態</span><span class="sxs-lookup"><span data-stu-id="20897-120">Using the PIP Specification to Create a Process Configuration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)  
  
-   [<span data-ttu-id="20897-121">授權與不可否認性屬性</span><span class="sxs-lookup"><span data-stu-id="20897-121">Authorization and Non-Repudiation Properties</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)  
  
-   [<span data-ttu-id="20897-122">設定 CIDX eStandards 訊息交換</span><span class="sxs-lookup"><span data-stu-id="20897-122">Setting Up CIDX eStandards Message Exchange</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)