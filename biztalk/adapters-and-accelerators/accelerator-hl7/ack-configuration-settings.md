---
title: "通知設定的設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- acknowledgements, configuring
- configuring, acknowledgements
ms.assetid: 46e92560-7b1e-4d53-9de8-8ded4de90695
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 93dea42fd084f22b4644f0acbb21860d69f75027
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="ack-configuration-settings"></a><span data-ttu-id="4d10d-102">通知設定</span><span class="sxs-lookup"><span data-stu-id="4d10d-102">ACK Configuration Settings</span></span>
<span data-ttu-id="4d10d-103">[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]剖析器產生根據交易夥伴管理 (TPM) 設定的通知。</span><span class="sxs-lookup"><span data-stu-id="4d10d-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] parser generates acknowledgments based on Trading Partner Management (TPM) settings.</span></span> <span data-ttu-id="4d10d-104">這些是相依於交易夥伴資訊通知 (ACK) 設定。</span><span class="sxs-lookup"><span data-stu-id="4d10d-104">The acknowledgment (ACK) settings are dependent on partner information.</span></span> <span data-ttu-id="4d10d-105">不使用結構描述型別。</span><span class="sxs-lookup"><span data-stu-id="4d10d-105">Schema type is not used.</span></span> <span data-ttu-id="4d10d-106">當[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]接收通知訊息與 MSH15 欄位包含 AL、 SU 或增，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]可能會傳送此訊息的 ACK 標頭和 TPM 設定剖析的結果為基礎的通知。</span><span class="sxs-lookup"><span data-stu-id="4d10d-106">When [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] receives an ACK message with the MSH15 field containing AL, SU or ER, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] may send an ACK for this message based on the result of parsing the ACK header and TPM configuration.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="4d10d-107">擷取夥伴通知設定，並傳回下列五個值之一：</span><span class="sxs-lookup"><span data-stu-id="4d10d-107"> retrieves the partner ACK settings and returns one of the following five values:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4d10d-108">HL7 規格會強制您使用 1 到 4，並填入 MSH15 ACK 訊息欄位所產生的項目。</span><span class="sxs-lookup"><span data-stu-id="4d10d-108">The HL7 specification mandates that you use items 1 through 4 and to populate the MSH15 field of an ACK message that you generate.</span></span> <span data-ttu-id="4d10d-109">項目 5 是[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]-特定代表不是用來產生通知。</span><span class="sxs-lookup"><span data-stu-id="4d10d-109">Item 5 is [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]-specific and denotes not to generate an ACK.</span></span>  
  
1.  <span data-ttu-id="4d10d-110">AL – 永遠</span><span class="sxs-lookup"><span data-stu-id="4d10d-110">AL – Always</span></span>  
  
2.  <span data-ttu-id="4d10d-111">NE – 永遠不會</span><span class="sxs-lookup"><span data-stu-id="4d10d-111">NE – Never</span></span>  
  
3.  <span data-ttu-id="4d10d-112">SU-成功</span><span class="sxs-lookup"><span data-stu-id="4d10d-112">SU – Success</span></span>  
  
4.  <span data-ttu-id="4d10d-113">ER： 錯誤</span><span class="sxs-lookup"><span data-stu-id="4d10d-113">ER – Error</span></span>  
  
5.  <span data-ttu-id="4d10d-114">否-不會產生 ACK</span><span class="sxs-lookup"><span data-stu-id="4d10d-114">NO – Do not generate an ACK</span></span>  
  
## <a name="ack-configuration-inconsistency"></a><span data-ttu-id="4d10d-115">通知組態不一致</span><span class="sxs-lookup"><span data-stu-id="4d10d-115">ACK configuration inconsistency</span></span>  
 <span data-ttu-id="4d10d-116">在通知組態使用者介面設定與訊息執行個體 MSH15 和 MSH16 欄位內的值之間不一致的情況下[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]兩個通知產生觸發程序的其中一個在需要時傳送通知。</span><span class="sxs-lookup"><span data-stu-id="4d10d-116">In the case of inconsistency between the ACK configuration user interface settings and values inside the message instance MSH15 and MSH16 fields, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sends an ACK when one of the two ACK generation triggers require it.</span></span> <span data-ttu-id="4d10d-117">在其他的不一致的情況下執行個體中的資料將會覆寫組態使用者介面中的設定。</span><span class="sxs-lookup"><span data-stu-id="4d10d-117">In the case of other inconsistencies, the data in the instance will override the setting in the configuration user interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d10d-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d10d-118">See Also</span></span>  
 <span data-ttu-id="4d10d-119">[設定訊息通知](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="4d10d-119">[Configuring Message Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/configuring-message-acknowledgments.md) </span></span>  
 [<span data-ttu-id="4d10d-120">建立及處理通知</span><span class="sxs-lookup"><span data-stu-id="4d10d-120">Creating and Processing Acknowledgments</span></span>](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md)