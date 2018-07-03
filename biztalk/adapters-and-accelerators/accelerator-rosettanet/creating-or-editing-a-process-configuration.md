---
title: 建立或編輯程序組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- process configuration, modifying
- process configuration, creating
- creating, process configuration
- modifying, process configuration
ms.assetid: 39cc2c93-0986-48d3-8c6f-4280ec9af4e0
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32300e84d2c9102baaa68a57045fefc103d0d9e5
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37013159"
---
# <a name="creating-or-editing-a-process-configuration"></a><span data-ttu-id="90b37-102">建立或編輯程序組態</span><span class="sxs-lookup"><span data-stu-id="90b37-102">Creating or Editing a Process Configuration</span></span>
<span data-ttu-id="90b37-103">本節說明如何建立或編輯流程組態，以在 Microsoft 中實作交易夥伴介面程序 (PIP) [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="90b37-103">This section describes how to create or edit a process configuration to implement a Partner Interface Process (PIP) in Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span> <span data-ttu-id="90b37-104">RosettaNet PIP 定義兩個交易夥伴之間的商務程序對話。</span><span class="sxs-lookup"><span data-stu-id="90b37-104">A RosettaNet PIP defines a business-process dialog between two trading partners.</span></span> <span data-ttu-id="90b37-105">在  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]，以建立 PIP 與合作夥伴，您必須先建立程序組態。</span><span class="sxs-lookup"><span data-stu-id="90b37-105">In [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], to create a PIP with a partner, you must first create a process configuration.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="90b37-106"> 您可以使用此設定檔儲存 PIP 的所有組態特性。</span><span class="sxs-lookup"><span data-stu-id="90b37-106"> uses this profile to store all configuration characteristics of the PIP.</span></span> <span data-ttu-id="90b37-107">之後，您便可使用此組態，建立交易夥伴的協議。</span><span class="sxs-lookup"><span data-stu-id="90b37-107">You can then use this configuration to create an agreement with the partner.</span></span>  
  
 <span data-ttu-id="90b37-108">如需程序組態屬性，與建立或編輯程序組態的程序的詳細資訊，請參閱[如何建立或編輯流程組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="90b37-108">For information about process configuration properties, and procedures for creating or editing a process configuration, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span></span>  
  
 <span data-ttu-id="90b37-109">建立新程序組態時，您的設定必須根據 RosettaNet 組織所維護的 PIP 規格文件。</span><span class="sxs-lookup"><span data-stu-id="90b37-109">In creating a new process configuration, you must base the settings on the PIP specification document maintained by the RosettaNet organization.</span></span> <span data-ttu-id="90b37-110">所有的程序組態設定都來自 PIP 規格，而 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 在大部分設定填入的預設值，都是欄位最常用的值。</span><span class="sxs-lookup"><span data-stu-id="90b37-110">All process configuration settings come from the PIP specifications, and [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] populates most of the settings with default values that are the most typically used values for the fields.</span></span> <span data-ttu-id="90b37-111">您必須確認設定與適當的 PIP 規格中的值一致。</span><span class="sxs-lookup"><span data-stu-id="90b37-111">You must verify that the settings correspond to the values in the appropriate PIP specification.</span></span> <span data-ttu-id="90b37-112">如需有關您所輸入的 PIP 設定如何對應至 PIP 規格中的指導方針的詳細資訊，請參閱 <<c0> [ 使用 PIP 規格建立程序組態](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="90b37-112">For more information about how the PIP settings that you enter map to the guidance in the PIP specification, see [Using the PIP Specification to Create a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md).</span></span>  
  
 <span data-ttu-id="90b37-113">程序組態可以是 RosettaNet 或 CIDX (化學工業資料交換)。</span><span class="sxs-lookup"><span data-stu-id="90b37-113">The process configuration can be for either RosettaNet or CIDX (Chemical Industry Data Exchange).</span></span> <span data-ttu-id="90b37-114">如需有關 CIDX 組態資訊，請參閱[設定 CIDX eStandards 訊息交換](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)。</span><span class="sxs-lookup"><span data-stu-id="90b37-114">For information about a CIDX configuration, see [Setting Up CIDX eStandards Message Exchange](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md).</span></span>  
  
 <span data-ttu-id="90b37-115">當有使用中的程序時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援變更程序組態。</span><span class="sxs-lookup"><span data-stu-id="90b37-115">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support changing a process configuration while there are active processes.</span></span> <span data-ttu-id="90b37-116">如果您變更協議，則使用中的程序將會結束，並出現失敗。</span><span class="sxs-lookup"><span data-stu-id="90b37-116">If you do so, the active processes will complete with failures.</span></span> <span data-ttu-id="90b37-117">所有新的程序將會成功挑選新的組態設定。</span><span class="sxs-lookup"><span data-stu-id="90b37-117">All new processes will successfully pick up the new configuration settings.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="90b37-118">本節內容</span><span class="sxs-lookup"><span data-stu-id="90b37-118">In This Section</span></span>  
  
-   [<span data-ttu-id="90b37-119">如何建立或編輯程序設定</span><span class="sxs-lookup"><span data-stu-id="90b37-119">How to Create or Edit a Process Configuration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)  
  
-   [<span data-ttu-id="90b37-120">使用 PIP 規格建立程序設定</span><span class="sxs-lookup"><span data-stu-id="90b37-120">Using the PIP Specification to Create a Process Configuration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/using-the-pip-specification-to-create-a-process-configuration.md)  
  
-   [<span data-ttu-id="90b37-121">授權與不可否認性屬性</span><span class="sxs-lookup"><span data-stu-id="90b37-121">Authorization and Non-Repudiation Properties</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/authorization-and-non-repudiation-properties.md)  
  
-   [<span data-ttu-id="90b37-122">設定 CIDX eStandards 訊息交換</span><span class="sxs-lookup"><span data-stu-id="90b37-122">Setting Up CIDX eStandards Message Exchange</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/setting-up-cidx-estandards-message-exchange.md)