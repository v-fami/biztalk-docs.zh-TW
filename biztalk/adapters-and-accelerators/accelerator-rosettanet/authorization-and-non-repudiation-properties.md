---
title: 授權與不可否認性屬性 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- authorization properties
- non-repudiation, properties
ms.assetid: e752b95b-9dae-4403-8f3e-3a0a50acd519
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7018ac2d66455359215db78b17e80414d176f99f
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
ms.locfileid: "22208174"
---
# <a name="authorization-and-non-repudiation-properties"></a><span data-ttu-id="a35cb-102">授權與不可否認性屬性</span><span class="sxs-lookup"><span data-stu-id="a35cb-102">Authorization and Non-Repudiation Properties</span></span>
<span data-ttu-id="a35cb-103">本主題說明交易夥伴介面程序 (PIP) 的 `Is Authorization Required`、`Non-Repudiation of Origin and Content` 和 `Non-Repudiation Required (Acknowledgement of Receipt)` 屬性的行為。</span><span class="sxs-lookup"><span data-stu-id="a35cb-103">This topic describes the behavior of the `Is Authorization Required`, `Non-Repudiation of Origin and Content`, and `Non-Repudiation Required (Acknowledgement of Receipt)` properties of Partner Interface Processes (PIPs).</span></span> <span data-ttu-id="a35cb-104">它也會描述這些屬性的組合， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]支援。</span><span class="sxs-lookup"><span data-stu-id="a35cb-104">It also describes the combinations of these properties that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] supports.</span></span>  
  
 <span data-ttu-id="a35cb-105">您可以設定這些屬性上**活動**的程序組態設定 區段中的程序組態屬性 索引標籤[!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="a35cb-105">You set these properties on the **Activity** tab of the Process Configuration properties in the Process Configuration Settings section of the [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console.</span></span> <span data-ttu-id="a35cb-106">如需詳細資訊，請參閱[如何建立或編輯程序組態](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="a35cb-106">For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span></span>  
  
## <a name="property-behavior"></a><span data-ttu-id="a35cb-107">屬性行為</span><span class="sxs-lookup"><span data-stu-id="a35cb-107">Property Behavior</span></span>  
 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="a35cb-108"> 根據 `Is Authorization Required`、`Non-Repudiation of Origin and Content` 和 `Non-Repudiation Required (Acknowledgement of Receipt)` 屬性的設定表現下列行為。</span><span class="sxs-lookup"><span data-stu-id="a35cb-108"> exhibits the following behavior according to the settings of the `Is Authorization Required`, `Non-Repudiation of Origin and Content`, and `Non-Repudiation Required (Acknowledgement of Receipt)` properties.</span></span>  
  
|<span data-ttu-id="a35cb-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a35cb-109">Property</span></span>|<span data-ttu-id="a35cb-110">屬性值為 True 時的行為</span><span class="sxs-lookup"><span data-stu-id="a35cb-110">Behavior when True</span></span>|<span data-ttu-id="a35cb-111">屬性值為 False 時的行為</span><span class="sxs-lookup"><span data-stu-id="a35cb-111">Behavior when False</span></span>|  
|--------------|------------------------|-------------------------|  
|`Is Authorization Required`|<span data-ttu-id="a35cb-112">必須簽署內送動作或信號訊息;否則，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]會拒絕該訊息。</span><span class="sxs-lookup"><span data-stu-id="a35cb-112">Incoming action or signal messages must be signed; otherwise, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] will reject the message.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="a35cb-113"> 若個人/角色未經授權執行活動，不接受商務文件。</span><span class="sxs-lookup"><span data-stu-id="a35cb-113"> does not accept the business document if the individual/role is not authorized to perform the activity.</span></span>|<span data-ttu-id="a35cb-114">不需要對內送動作或信號訊息進行簽署，</span><span class="sxs-lookup"><span data-stu-id="a35cb-114">Incoming action or signal messages do not have to be signed.</span></span> <span data-ttu-id="a35cb-115">但仍可使用訊息 RNIF 標頭部分中的交易夥伴 DUNS 編號進行簡單的授權。</span><span class="sxs-lookup"><span data-stu-id="a35cb-115">Simple authorization will still be applied with the partner DUNS number from the RNIF header parts of the message.</span></span>|  
|`Non-Repudiation of Origin and Content`|<span data-ttu-id="a35cb-116">簽署外寄動作或信號訊息。</span><span class="sxs-lookup"><span data-stu-id="a35cb-116">Outgoing action or signal messages will be signed.</span></span> <span data-ttu-id="a35cb-117">動作訊息將以原始接收格式，存放在 BTARNDATA 資料庫中的 MessageStorageOut 資料表。</span><span class="sxs-lookup"><span data-stu-id="a35cb-117">Action messages will be stored in their original received form in the MessageStorageOut table of the BTARNDATA database.</span></span>|<span data-ttu-id="a35cb-118">不存放外寄動作或信號訊息。</span><span class="sxs-lookup"><span data-stu-id="a35cb-118">Outgoing action or signal messages will not be stored.</span></span>|  
|`Non-Repudiation Required (Acknowledgement of Receipt)`|<span data-ttu-id="a35cb-119">必須簽署內送動作或信號訊息。</span><span class="sxs-lookup"><span data-stu-id="a35cb-119">Incoming action or signal messages must be signed.</span></span> <span data-ttu-id="a35cb-120">內送訊息將存放在 BTARNDATA 資料庫的 MessageStorageIn 表格中。</span><span class="sxs-lookup"><span data-stu-id="a35cb-120">The incoming message will be stored in the MessageStorageIn table in the BTARNDATA database.</span></span> <span data-ttu-id="a35cb-121">通知中必須含有訊息摘要。</span><span class="sxs-lookup"><span data-stu-id="a35cb-121">A message digest must be included in the acknowledgement.</span></span>|<span data-ttu-id="a35cb-122">不存放內送動作或信號訊息。</span><span class="sxs-lookup"><span data-stu-id="a35cb-122">Incoming action or signal messages will not be stored.</span></span>|  
  
## <a name="property-support"></a><span data-ttu-id="a35cb-123">支援的屬性</span><span class="sxs-lookup"><span data-stu-id="a35cb-123">Property Support</span></span>  
 <span data-ttu-id="a35cb-124">下表顯示 `Is Authorization Required`、`Non-Repudiation of Origin and Content` 和 `Non-Repudiation Required (Acknowledgement of Receipt)` 屬性組合的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 支援。</span><span class="sxs-lookup"><span data-stu-id="a35cb-124">The following table shows [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] support for combinations of the `Is Authorization Required`, `Non-Repudiation of Origin and Content`, and `Non-Repudiation Required (Acknowledgement of Receipt)` properties.</span></span>  
  
> [!IMPORTANT]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="a35cb-125"> 必須簽署同時動作訊息與信號訊息或動作訊息和都單一訊息。</span><span class="sxs-lookup"><span data-stu-id="a35cb-125"> must either sign both action messages and signal messages, or neither action messages nor single messages.</span></span> [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]<span data-ttu-id="a35cb-126"> 並不支援簽署動作，但不是簽署信號，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="a35cb-126"> does not support signing actions, but not signing signals, or vice versa.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a35cb-127">若 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 對輸出訊息加上簽章，就必須將此訊息儲存在 BTARNARCHIVE 資料庫的 MessageStorageOut 資料表內。</span><span class="sxs-lookup"><span data-stu-id="a35cb-127">If [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] signs an outbound message, it must save the message in the MessageStorageOut table of the BTARNArchive database.</span></span>  
  
|<span data-ttu-id="a35cb-128">需要授權</span><span class="sxs-lookup"><span data-stu-id="a35cb-128">Is Authorization Required</span></span>|<span data-ttu-id="a35cb-129">來源與內容的不可否認性</span><span class="sxs-lookup"><span data-stu-id="a35cb-129">Non-Repudiation of Origin and Content</span></span>|<span data-ttu-id="a35cb-130">接收通知 - 需要不可否認性</span><span class="sxs-lookup"><span data-stu-id="a35cb-130">Non-Repudiation Required (Acknowledgement of Receipt)</span></span>|<span data-ttu-id="a35cb-131">BTARN 是否支援？</span><span class="sxs-lookup"><span data-stu-id="a35cb-131">Supported by BTARN?</span></span>|  
|-------------------------------|--------------------------------------------|--------------------------------------------------------------|-------------------------|  
|`False`|`False`|`False`|<span data-ttu-id="a35cb-132">是</span><span class="sxs-lookup"><span data-stu-id="a35cb-132">Yes</span></span>|  
|`False`|`False`|`True`|<span data-ttu-id="a35cb-133">否\*</span><span class="sxs-lookup"><span data-stu-id="a35cb-133">No\*</span></span>|  
|`False`|`True`|`False`|<span data-ttu-id="a35cb-134">否**</span><span class="sxs-lookup"><span data-stu-id="a35cb-134">No**</span></span>|  
|`False`|`True`|`True`|<span data-ttu-id="a35cb-135">否\*\*\*</span><span class="sxs-lookup"><span data-stu-id="a35cb-135">No\*\*\*</span></span>|  
|`True`|`False`|`False`|<span data-ttu-id="a35cb-136">是****</span><span class="sxs-lookup"><span data-stu-id="a35cb-136">Yes****</span></span>|  
|`True`|`False`|`True`|<span data-ttu-id="a35cb-137">是****</span><span class="sxs-lookup"><span data-stu-id="a35cb-137">Yes****</span></span>|  
|`True`|`True`|`False`|<span data-ttu-id="a35cb-138">是</span><span class="sxs-lookup"><span data-stu-id="a35cb-138">Yes</span></span>|  
|`True`|`True`|`True`|<span data-ttu-id="a35cb-139">是</span><span class="sxs-lookup"><span data-stu-id="a35cb-139">Yes</span></span>|  
  
 <span data-ttu-id="a35cb-140">\* [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援這種組合，因為它需要簽署信號，但不簽署動作。</span><span class="sxs-lookup"><span data-stu-id="a35cb-140">\* [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support this combination because it requires that signals be signed and actions not be signed.</span></span>  
  
 <span data-ttu-id="a35cb-141">** [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援這種組合，因為它要求簽署動作，但並不簽署信號。</span><span class="sxs-lookup"><span data-stu-id="a35cb-141">** [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support this combination because it requires that actions be signed and signals not be signed.</span></span>  
  
 <span data-ttu-id="a35cb-142">\*\*\* [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 不支援這種組合，因為設為不可否認性`True`對於動作與信號表示[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]執行授權。</span><span class="sxs-lookup"><span data-stu-id="a35cb-142">\*\*\* [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] does not support this combination because setting non-repudiation to `True` for both actions and signals means that [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] is performing authorization.</span></span> <span data-ttu-id="a35cb-143">因此，此組合無效。</span><span class="sxs-lookup"><span data-stu-id="a35cb-143">Therefore, this combination is not valid.</span></span>  
  
 <span data-ttu-id="a35cb-144">**** 當您將 `Is Authorization Required` 設為 `True` 且將 `Non-Repudiation of Origin and Content` 設為 `False` 時，[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 會將訊息儲存在不可否認性資料表中。</span><span class="sxs-lookup"><span data-stu-id="a35cb-144">**** When you set `Is Authorization Required` to `True` and `Non-Repudiation of Origin and Content` to `False`, [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] stores the message in the non-repudiation table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a35cb-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a35cb-145">See Also</span></span>  
 [<span data-ttu-id="a35cb-146">如何建立或編輯程序設定</span><span class="sxs-lookup"><span data-stu-id="a35cb-146">How to Create or Edit a Process Configuration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md)