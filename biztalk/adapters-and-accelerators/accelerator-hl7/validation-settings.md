---
title: "驗證設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, configuring
- configuring, validating
ms.assetid: ee08acac-99f9-4403-b2ae-01b80378aa58
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 574e4a27342680ef4a37f6b12059cbf97bd9584a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="validation-settings"></a><span data-ttu-id="bead0-102">驗證設定</span><span class="sxs-lookup"><span data-stu-id="bead0-102">Validation Settings</span></span>
<span data-ttu-id="bead0-103">使用[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]，您可以驗證您針對 HL7 標準的訊息。</span><span class="sxs-lookup"><span data-stu-id="bead0-103">Using [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)], you can validate your messages against the HL7 standard.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="bead0-104">可確保您傳送或接收的訊息具有符合標準 HL7 訊息結構和內文區段。</span><span class="sxs-lookup"><span data-stu-id="bead0-104"> ensures that the messages you send or receive have a message structure and body segment that conforms to the HL7 standard.</span></span> <span data-ttu-id="bead0-105">您也可以驗證 HL7 支援自訂資料型別，並允許尾端分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bead0-105">You can also validate HL7 supported custom data types, and allow trailing delimiters.</span></span> <span data-ttu-id="bead0-106">您使用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**驗證**索引標籤，設定驗證。</span><span class="sxs-lookup"><span data-stu-id="bead0-106">You use the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Validation** tab to configure validation.</span></span>  
  
## <a name="configuring-validation-settings"></a><span data-ttu-id="bead0-107">設定驗證設定</span><span class="sxs-lookup"><span data-stu-id="bead0-107">Configuring Validation Settings</span></span>  
 <span data-ttu-id="bead0-108">您使用**驗證** 索引標籤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管 (在高階**合作對象** 索引標籤) 來設定驗證設定。</span><span class="sxs-lookup"><span data-stu-id="bead0-108">You use the **Validation** tab of [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer (under the high-level **Parties** tab) to configure validation settings.</span></span> <span data-ttu-id="bead0-109">您可以選取下列類型的驗證：</span><span class="sxs-lookup"><span data-stu-id="bead0-109">You can select the following types of validation:</span></span>  
  
-   <span data-ttu-id="bead0-110">語法、 結構和內文區段，依據訊息結構描述圖解驗證</span><span class="sxs-lookup"><span data-stu-id="bead0-110">Syntax, structure, and schematic validation on body segments, based on the message schema</span></span>  
  
-   <span data-ttu-id="bead0-111">HL7 標準驗證自訂資料類型 （DT、 TS、 TM 和曼非斯）</span><span class="sxs-lookup"><span data-stu-id="bead0-111">HL7 standard validation on custom data types (DT, TS, TM, and TN)</span></span>  
  
-   <span data-ttu-id="bead0-112">欄位分隔符號 （允許尾端分隔符號） 的驗證</span><span class="sxs-lookup"><span data-stu-id="bead0-112">Validation of field delimiters (trailing delimiters are allowed)</span></span>  
  
 <span data-ttu-id="bead0-113">使用此索引標籤，您也可以設定用於此合作對象的訊息上的驗證結構描述命名空間。</span><span class="sxs-lookup"><span data-stu-id="bead0-113">Using this tab, you can also set the schema namespace used for the validation on the messages for this party.</span></span>  
  
 <span data-ttu-id="bead0-114">下圖顯示[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管**驗證** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bead0-114">The following figure shows the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer **Validation** tab.</span></span>  
  
 <span data-ttu-id="bead0-115">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-val.gif "hl7_ops_val")</span><span class="sxs-lookup"><span data-stu-id="bead0-115">![](../../adapters-and-accelerators/accelerator-hl7/media/hl7-ops-val.gif "hl7_ops_val")</span></span>  
<span data-ttu-id="bead0-116">BTAHL7 組態總管驗證索引標籤</span><span class="sxs-lookup"><span data-stu-id="bead0-116">BTAHL7 Configuration Explorer Validation tab</span></span>  
  
 <span data-ttu-id="bead0-117">您可以使用下列程序來設定驗證設定。</span><span class="sxs-lookup"><span data-stu-id="bead0-117">Use the following procedures to configure validation settings.</span></span>  
  
#### <a name="to-open-btahl7-configuration-explorer"></a><span data-ttu-id="bead0-118">若要開啟 BTAHL7 組態總管</span><span class="sxs-lookup"><span data-stu-id="bead0-118">To open BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="bead0-119">按一下**啟動**，按一下 **程式**，按一下  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="bead0-119">Click **Start**, click **Programs**, click **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
#### <a name="to-configure-validation-settings"></a><span data-ttu-id="bead0-120">若要設定驗證設定</span><span class="sxs-lookup"><span data-stu-id="bead0-120">To configure validation settings</span></span>  
  
1.  <span data-ttu-id="bead0-121">在 BTAHL7 組態總管，於**驗證**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="bead0-121">In BTAHL7 Configuration Explorer on the **Validation** tab, do the following:</span></span>  
  
    |<span data-ttu-id="bead0-122">使用</span><span class="sxs-lookup"><span data-stu-id="bead0-122">Use this</span></span>|<span data-ttu-id="bead0-123">動作</span><span class="sxs-lookup"><span data-stu-id="bead0-123">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="bead0-124">**驗證主體區段**</span><span class="sxs-lookup"><span data-stu-id="bead0-124">**Validate body segments**</span></span>|<span data-ttu-id="bead0-125">選取此選項以執行語法、 結構和結構描述驗證。</span><span class="sxs-lookup"><span data-stu-id="bead0-125">Select this option to perform syntax, structure, and schema validation.</span></span>|  
    |<span data-ttu-id="bead0-126">**驗證的自訂資料類型**</span><span class="sxs-lookup"><span data-stu-id="bead0-126">**Validate custom data type**</span></span>|<span data-ttu-id="bead0-127">選取此選項可在 DT、 TS、 TM 和曼非斯自訂資料型別上執行 HL7 標準驗證。</span><span class="sxs-lookup"><span data-stu-id="bead0-127">Select this option to perform HL7 standard validation on DT, TS, TM, and TN custom data types.</span></span>|  
    |<span data-ttu-id="bead0-128">**允許尾端分隔符號 （分隔符號）**</span><span class="sxs-lookup"><span data-stu-id="bead0-128">**Allow trailing delimiters (separators)**</span></span>|<span data-ttu-id="bead0-129">選取此選項可啟用訊息執行個體中的尾端欄位分隔符號。</span><span class="sxs-lookup"><span data-stu-id="bead0-129">Select this option to enable trailing field delimiters in message instances.</span></span>|  
    |<span data-ttu-id="bead0-130">**結構描述命名空間**</span><span class="sxs-lookup"><span data-stu-id="bead0-130">**Schema Namespace**</span></span>|<span data-ttu-id="bead0-131">輸入結構描述命名空間位置。</span><span class="sxs-lookup"><span data-stu-id="bead0-131">Type the schema namespace location.</span></span> <span data-ttu-id="bead0-132">預設值是 http://microsoft.com/HealthCare/HL7/2X。</span><span class="sxs-lookup"><span data-stu-id="bead0-132">The default value is http://microsoft.com/HealthCare/HL7/2X.</span></span>|  
  
2.  <span data-ttu-id="bead0-133">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="bead0-133">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bead0-134">請參閱</span><span class="sxs-lookup"><span data-stu-id="bead0-134">See Also</span></span>  
 <span data-ttu-id="bead0-135">[記錄設定](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="bead0-135">[Logging Configuration](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md) </span></span>  
 <span data-ttu-id="bead0-136">[通知設定](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md) </span><span class="sxs-lookup"><span data-stu-id="bead0-136">[Acknowledgment Settings](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md) </span></span>  
[<span data-ttu-id="bead0-137">作業記錄、訊息批次處理、驗證和通知設定</span><span class="sxs-lookup"><span data-stu-id="bead0-137">Operational logging, message batching, validation and asknowledgment settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/operational-logging-message-batching-validation-and-asknowledgment-settings.md)