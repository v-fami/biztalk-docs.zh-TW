---
title: "批次處理的已知的問題 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, known issues
- known issues, batching
ms.assetid: 25c645eb-845d-483a-8f77-398e7dfe0c8f
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b47246662c5945f8ef09040ec7a8aa49326f59db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="batching-known-issues"></a><span data-ttu-id="cb05e-102">批次處理的已知的問題</span><span class="sxs-lookup"><span data-stu-id="cb05e-102">Batching Known Issues</span></span>
<span data-ttu-id="cb05e-103">本節包含可協助您避免批次錯誤的有用資訊。</span><span class="sxs-lookup"><span data-stu-id="cb05e-103">This section contains useful information that may help you avoid batching errors.</span></span>  
  
## <a name="batch-trailer-segment-fts-and-bts-fields-are-accepted-even-if-they-are-strings"></a><span data-ttu-id="cb05e-104">批次 （FTS 和 BTS） 欄位所接受，即使它們是字串的結尾區段</span><span class="sxs-lookup"><span data-stu-id="cb05e-104">Batch trailer segment (FTS and BTS) fields are accepted even if they are strings</span></span>  
 <span data-ttu-id="cb05e-105">HL7 FTS 與 BTS HL7 的各種版本不同的區段中指定的欄位。</span><span class="sxs-lookup"><span data-stu-id="cb05e-105">HL7 specifies the fields in FTS and BTS segments differently in the various versions of HL7.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="cb05e-106">定義的所有欄位，以字串資料類型，以避免不一致。</span><span class="sxs-lookup"><span data-stu-id="cb05e-106"> defines all of the fields as String data type to avoid inconsistency.</span></span>  
  
## <a name="data-type-of-an-ack-to-a-batch-message"></a><span data-ttu-id="cb05e-107">資料類型的批次訊息的通知</span><span class="sxs-lookup"><span data-stu-id="cb05e-107">Data type of an ACK to a batch message</span></span>  
 <span data-ttu-id="cb05e-108">在批次訊息，如果來源合作對象的片段已關閉，然後 MSH10 回應中產生的通知 (ACK) 訊息欄位 (訊息控制項 ID) 就是 GUID，而不是 MSH10 欄位批次訊息中的任何其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="cb05e-108">In an acknowledgment (ACK) message generated in response to a batch message, if fragmentation for source party is turned off, then the MSH10 field (message control ID) will be a GUID, rather than any other data type of the MSH10 field in the batch message.</span></span>  
  
## <a name="btahl7-configuration-explorer-and-create-batch-orchestrations-are-not-two-way-synchronized"></a><span data-ttu-id="cb05e-109">BTAHL7 Configuration 總管 」 和 「 建立批次協調流程不是雙向同步處理</span><span class="sxs-lookup"><span data-stu-id="cb05e-109">BTAHL7 Configuration Explorer and Create Batch orchestrations are not two-way synchronized</span></span>  
 <span data-ttu-id="cb05e-110">貴用戶無法檢視批次控制排程的目前狀態，即使您按下 F5 中的[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管 中，而可能同時檢查[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]目前組態總管和狀況與活動追蹤 (HAT) 工具批次控制排程的狀態。</span><span class="sxs-lookup"><span data-stu-id="cb05e-110">You may not able to view the current status of the batch control schedule even if you press F5 in [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, and may have to check both [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and the Health and Activity Tracking (HAT) tool for the current status of the batch control schedule.</span></span>  
  
## <a name="two-parsing-errors-logged-when-messages-in-batch-inbatch-out-scenario-contain-validation-errors"></a><span data-ttu-id="cb05e-111">兩個剖析錯誤時記錄訊息中批次處理 / 批次出案例包含驗證錯誤</span><span class="sxs-lookup"><span data-stu-id="cb05e-111">Two parsing errors logged when messages in Batch In/Batch Out scenario contain validation errors</span></span>  
 <span data-ttu-id="cb05e-112">當第一個訊息批次中在 / 批次出情節 （不含批次標頭中批次處理多個訊息） 都會包含驗證錯誤[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]事件記錄檔中記錄兩個錯誤。</span><span class="sxs-lookup"><span data-stu-id="cb05e-112">When the first message in the Batch In/Batch Out scenario (multiple messages batched without batch headers) contains validation errors, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] logs two errors in the Event Log.</span></span> <span data-ttu-id="cb05e-113">第一個錯誤相關的批次中的第一個訊息，訊息的其餘部分都屬於第二個錯誤。</span><span class="sxs-lookup"><span data-stu-id="cb05e-113">The first error pertains to the first message in the batch, and the second error pertains to the remainder of the messages.</span></span>  
  
## <a name="subscription-using-the-btsmessagetype-property-for-the-batch-inbatch-out-scenario-with-fragmentation-disabled-is-not-supported"></a><span data-ttu-id="cb05e-114">使用 BTS 的訂用帳戶。MessageType 屬性批次中不支援與停用的片段的批次出案例</span><span class="sxs-lookup"><span data-stu-id="cb05e-114">Subscription using the BTS.MessageType property for the Batch In/Batch Out scenario with fragmentation disabled is not supported</span></span>  
 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="cb05e-115">不支援訂用帳戶使用**BTS。MessageType**屬性批次中 / 片段停用，可能包含多個訊息類型的交換與批次出案例。</span><span class="sxs-lookup"><span data-stu-id="cb05e-115"> does not support subscription using the **BTS.MessageType** property for the Batch In/Batch Out scenario with fragmentation disabled as an interchange that may consist of multiple message types.</span></span>  
  
## <a name="entire-batch-suspended-after-erroneous-message-in-the-batch-inbatch-out-scenario"></a><span data-ttu-id="cb05e-116">處理批次中的錯誤訊息後被擱置整個批次中 / 批次出案例</span><span class="sxs-lookup"><span data-stu-id="cb05e-116">Entire batch suspended after erroneous message in the Batch In/Batch Out scenario</span></span>  
 <span data-ttu-id="cb05e-117">如果發生嚴重的剖析器錯誤訊息 (比方說，[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]不會剖析 MSH 9 或無法載入訊息的 MSH 12 或內文結構描述) 發生分散的批次中在批次出案例中，錯誤訊息將遭擱置之後的任何資料即使 / 如果可復原交換支援已啟用。</span><span class="sxs-lookup"><span data-stu-id="cb05e-117">If a message with fatal parser errors (for example, [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] does not parse MSH 9 or MSH 12 or body schema for the message failed to load) is encountered in a fragmented Batch In/Batch Out scenario, any data after the erroneous message is suspended even if the recoverable interchange support has been enabled.</span></span>  
  
## <a name="batch-of-acks-get-routed-to-the-source-party-of-the-first-message-in-batch-inbatch-out-scenario"></a><span data-ttu-id="cb05e-118">認可的批次會路由至第一個訊息批次中的來源合作對象中 / 批次出案例</span><span class="sxs-lookup"><span data-stu-id="cb05e-118">Batch of Acks get routed to the source party of the first message in Batch In/Batch Out Scenario</span></span>  
 <span data-ttu-id="cb05e-119">在批次處理中 / 批次出案例的批次認可取得路由，根據來源合作對象資訊的第一個訊息，因為這項功能會假設輸入中的所有訊息批都次的來源和目的合作對象都相同。</span><span class="sxs-lookup"><span data-stu-id="cb05e-119">In Batch In/ Batch Out scenario batch of Acks get routed based on the source party information of the first message, because this functionality assume that for all the messages in inbound batch the source and destination parties are same.</span></span>  
  
## <a name="batch-of-acks-does-not-get-routed-to-the-source-party-when-two-way-receive-port-is-used-in-batch-in-batch-out-scenario"></a><span data-ttu-id="cb05e-120">認可的批次不會不會路由至雙向時的來源合作對象接收批次中使用連接埠中 / 批次出案例</span><span class="sxs-lookup"><span data-stu-id="cb05e-120">Batch of Acks does not get routed to the source party when two-way receive port is used in Batch In/ Batch Out scenario</span></span>  
 <span data-ttu-id="cb05e-121">如果要求-回應接收的埠 ACK/NACK 批次並不會路由至 BIBO 實例的來源合作對象。</span><span class="sxs-lookup"><span data-stu-id="cb05e-121">In case of request-response receive port the ACK/NACK batch does not get routed to the source party for BIBO scenario.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb05e-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb05e-122">See Also</span></span>  
 [<span data-ttu-id="cb05e-123">已知問題</span><span class="sxs-lookup"><span data-stu-id="cb05e-123">Known Issues</span></span>](../../adapters-and-accelerators/accelerator-hl7/known-issues1.md)