---
title: ACK 組態設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, configuring
- configuring, acknowledgements
ms.assetid: 46e92560-7b1e-4d53-9de8-8ded4de90695
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06cedaee1ca0ad574920cfb646f69d63157c8e67
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36968055"
---
# <a name="ack-configuration-settings"></a><span data-ttu-id="f15ff-102">ACK 組態設定</span><span class="sxs-lookup"><span data-stu-id="f15ff-102">ACK Configuration Settings</span></span>
<span data-ttu-id="f15ff-103">Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]剖析器會產生交易夥伴管理 (TPM) 設定為基礎的通知。</span><span class="sxs-lookup"><span data-stu-id="f15ff-103">The Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] parser generates acknowledgments based on Trading Partner Management (TPM) settings.</span></span> <span data-ttu-id="f15ff-104">通知 (ACK) 設定需仰賴夥伴資訊。</span><span class="sxs-lookup"><span data-stu-id="f15ff-104">The acknowledgment (ACK) settings are dependent on partner information.</span></span> <span data-ttu-id="f15ff-105">不使用結構描述型別。</span><span class="sxs-lookup"><span data-stu-id="f15ff-105">Schema type is not used.</span></span> <span data-ttu-id="f15ff-106">當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]收到通知訊息與 MSH15 欄位包含 AL、 SU 或 ER，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可能會傳送此訊息的 ACK 標頭和 TPM 設定剖析的結果為基礎的認可。</span><span class="sxs-lookup"><span data-stu-id="f15ff-106">When [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives an ACK message with the MSH15 field containing AL, SU or ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] may send an ACK for this message based on the result of parsing the ACK header and TPM configuration.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f15ff-107"> 擷取夥伴通知的設定，並傳回下列五個值之一：</span><span class="sxs-lookup"><span data-stu-id="f15ff-107"> retrieves the partner ACK settings and returns one of the following five values:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f15ff-108">HL7 規格會強制您使用 1 到 4，並填入您所產生的 ACK 訊息 MSH15 欄位的項目。</span><span class="sxs-lookup"><span data-stu-id="f15ff-108">The HL7 specification mandates that you use items 1 through 4 and to populate the MSH15 field of an ACK message that you generate.</span></span> <span data-ttu-id="f15ff-109">項目 5 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]-特定和代表不產生通知。</span><span class="sxs-lookup"><span data-stu-id="f15ff-109">Item 5 is [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]-specific and denotes not to generate an ACK.</span></span>  
  
1.  <span data-ttu-id="f15ff-110">AL – 一律</span><span class="sxs-lookup"><span data-stu-id="f15ff-110">AL – Always</span></span>  
  
2.  <span data-ttu-id="f15ff-111">NE – 永遠不會</span><span class="sxs-lookup"><span data-stu-id="f15ff-111">NE – Never</span></span>  
  
3.  <span data-ttu-id="f15ff-112">SU-成功</span><span class="sxs-lookup"><span data-stu-id="f15ff-112">SU – Success</span></span>  
  
4.  <span data-ttu-id="f15ff-113">ER-錯誤</span><span class="sxs-lookup"><span data-stu-id="f15ff-113">ER – Error</span></span>  
  
5.  <span data-ttu-id="f15ff-114">否，不會產生通知</span><span class="sxs-lookup"><span data-stu-id="f15ff-114">NO – Do not generate an ACK</span></span>  
  
## <a name="ack-configuration-inconsistency"></a><span data-ttu-id="f15ff-115">ACK 組態不一致</span><span class="sxs-lookup"><span data-stu-id="f15ff-115">ACK configuration inconsistency</span></span>  
 <span data-ttu-id="f15ff-116">在通知組態使用者介面設定與訊息執行個體 MSH15 和 MSH16 欄位內的值之間不一致的情況下[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]其中兩個通知產生觸發程序需要它時，會傳送通知。</span><span class="sxs-lookup"><span data-stu-id="f15ff-116">In the case of inconsistency between the ACK configuration user interface settings and values inside the message instance MSH15 and MSH16 fields, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK when one of the two ACK generation triggers require it.</span></span> <span data-ttu-id="f15ff-117">在其他的不一致的情況下執行個體中的資料會覆寫組態使用者介面中的設定。</span><span class="sxs-lookup"><span data-stu-id="f15ff-117">In the case of other inconsistencies, the data in the instance will override the setting in the configuration user interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15ff-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f15ff-118">See Also</span></span>  
 <span data-ttu-id="f15ff-119">[設定訊息通知](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="f15ff-119">[Configuring Message Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md) </span></span>  
 [<span data-ttu-id="f15ff-120">建立及處理通知</span><span class="sxs-lookup"><span data-stu-id="f15ff-120">Creating and Processing Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)