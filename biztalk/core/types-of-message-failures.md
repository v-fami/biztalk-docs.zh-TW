---
title: 訊息失敗的類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transformation stage
- assembly stage
- errors, disassembly stage
- errors, assembly stage
- routing, errors
- errors, transformation stage
- errors, messages [HAT]
- errors, routing
- disassembly stage, errors
- messages, errors [HAT]
ms.assetid: 3a8e1c58-4b53-4439-837d-aaa233eb9158
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c8a3dc40d2b82e90332b27719adce36b27f78ebd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36984007"
---
# <a name="types-of-message-failures"></a><span data-ttu-id="05e91-102">訊息失敗的類型</span><span class="sxs-lookup"><span data-stu-id="05e91-102">Types of Message Failures</span></span>
<span data-ttu-id="05e91-103">本主題列出訊息失敗可能發生的不同點。</span><span class="sxs-lookup"><span data-stu-id="05e91-103">This topic lists different points where a message failure may occur.</span></span>  
  
 <span data-ttu-id="05e91-104">**反組譯碼階段中的失敗**</span><span class="sxs-lookup"><span data-stu-id="05e91-104">**Failures in the disassembly phase**</span></span>  
  
 <span data-ttu-id="05e91-105">處理作業也可能在解譯階段失敗；也就是說，在其中一個管線元件中失敗。</span><span class="sxs-lookup"><span data-stu-id="05e91-105">Processing might also fail during the disassembly phase; that is, failure in one of the pipeline components.</span></span> <span data-ttu-id="05e91-106">例如，由於處理伺服器上缺少解密憑證而造成解密失敗，或由於結構描述或訊息中的問題而造成剖析失敗。</span><span class="sxs-lookup"><span data-stu-id="05e91-106">For example, decryption failed due to absence of decryption cert on the processing server, or parsing failure due to problem either in the schema or in the message.</span></span>  
  
 <span data-ttu-id="05e91-107">**路由中的失敗**</span><span class="sxs-lookup"><span data-stu-id="05e91-107">**Failures in routing**</span></span>  
  
 <span data-ttu-id="05e91-108">在訊息成功解譯之後，下一個潛在的失敗點是路由；例如，使用者啟用協調流程的對應接收位置，但忘記登錄協調流程。</span><span class="sxs-lookup"><span data-stu-id="05e91-108">After a message disassembles successfully, the next potential failure point is routing; for example, users enable a corresponding receive location of an orchestration and forget to enlist the orchestration.</span></span> <span data-ttu-id="05e91-109">在此情況下，從接收位置拾取的訊息將路由失敗，而 MessageBox 資料庫會產生「路由失敗」報告。</span><span class="sxs-lookup"><span data-stu-id="05e91-109">In this case, the message picked up from the receive location fails routing and the MessageBox database generates a Routing Failure report.</span></span>  
  
 <span data-ttu-id="05e91-110">「路由失敗」報告會列在 [BizTalk Server 管理] 主控台中做為不可繼續的已擱置訊息。</span><span class="sxs-lookup"><span data-stu-id="05e91-110">Routing Failure reports are listed in the BizTalk Server Administration Console as non-resumable suspended messages.</span></span> <span data-ttu-id="05e91-111">每個「路由失敗」報告都包含發生路由失敗時取得的訊息屬性快照。</span><span class="sxs-lookup"><span data-stu-id="05e91-111">Each Routing Failure report contains a message property snap shot taken when the routing failure occurred.</span></span> <span data-ttu-id="05e91-112">您可以使用每個報告中的資訊來判斷其關聯訊息為何路由失敗。</span><span class="sxs-lookup"><span data-stu-id="05e91-112">You can use the information in each report to determine why routing failed for its associated message.</span></span> <span data-ttu-id="05e91-113">若關聯訊息可繼續，則您可以更正路由問題並繼續此訊息，以便處理作業繼續。</span><span class="sxs-lookup"><span data-stu-id="05e91-113">If the associated message is resumable, you can correct the routing problem and resume the message so that processing continues.</span></span> <span data-ttu-id="05e91-114">「路由失敗」報告會列在具有空白服務名稱與服務類型的結果清單中。</span><span class="sxs-lookup"><span data-stu-id="05e91-114">Routing Failure reports are listed in the results list with a blank service name and service type.</span></span> <span data-ttu-id="05e91-115">終止已擱置的執行個體時，預設為每分鐘執行的 Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb 工作會自動刪除與已擱置執行個體關聯的「路由失敗」報告。</span><span class="sxs-lookup"><span data-stu-id="05e91-115">When you terminate a suspended instance, the Routing Failure report associated with the suspended instance is automatically deleted by the Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb job that runs every minute by default.</span></span> <span data-ttu-id="05e91-116">如需 Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb 工作的詳細資訊，請參閱[資料庫結構與工作](../core/database-structure-and-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="05e91-116">For more information about the Operations_OperateOnInstances_OnMaster_BizTalkMsgBoxDb job, see [Database Structure and Jobs](../core/database-structure-and-jobs.md).</span></span>  
  
 <span data-ttu-id="05e91-117">**在轉換階段期間發生的失敗**</span><span class="sxs-lookup"><span data-stu-id="05e91-117">**Failures during the transformation phase**</span></span>  
  
- <span data-ttu-id="05e91-118">**接收的訊息**。</span><span class="sxs-lookup"><span data-stu-id="05e91-118">**Received Messages**.</span></span> <span data-ttu-id="05e91-119">從接收位置收到訊息時，可解譯訊息 (例如解密和剖析)，選擇性地透過接收埠指定的「輸入對應」將此訊息轉換為不同格式，並發佈至 MessageBox 以路由至協調流程或傳送埠。</span><span class="sxs-lookup"><span data-stu-id="05e91-119">When a message is received from Receive Location, the message is disassembled (for example, decrypted and parsed), the message might optionally be transformed to a different format via an Inbound Map specified on a receive Port, and published to the MessageBox for routing to an orchestration or a Send Port.</span></span> <span data-ttu-id="05e91-120">在此情況下，處理作業可能由於不正確的「輸入對應」，或由於結構描述或已接收訊息中的問題，而在轉換階段造成失敗。</span><span class="sxs-lookup"><span data-stu-id="05e91-120">In this case, processing may fail during transformation phase due to incorrect Inbound Map, or problems in the schema or in the message received.</span></span>  
  
- <span data-ttu-id="05e91-121">**將訊息傳送**。</span><span class="sxs-lookup"><span data-stu-id="05e91-121">**Sent Messages**.</span></span> <span data-ttu-id="05e91-122">要傳送訊息至傳送位置時，在傳送埠上設定的「輸出對應」可能選擇性地轉換訊息。</span><span class="sxs-lookup"><span data-stu-id="05e91-122">When a message is to be sent to a Send Location, an Outbound Map configured on Send Port might optionally transform the message.</span></span> <span data-ttu-id="05e91-123">然後組合已轉換的訊息並傳遞給配接器，進行最後傳輸至傳送位置。</span><span class="sxs-lookup"><span data-stu-id="05e91-123">Then the transformed message is assembled and handed to the adapter for final transmission to the Send Location.</span></span> <span data-ttu-id="05e91-124">在此情況下，處理作業可能由於不正確的「輸出對應」，或由於結構描述或來源訊息中的問題，而在轉換階段造成失敗。</span><span class="sxs-lookup"><span data-stu-id="05e91-124">In this case, processing may fail during transformation phase due to incorrect Outbound Map or problem in schema or source message.</span></span>  
  
  <span data-ttu-id="05e91-125">**在訊息組合階段失敗**</span><span class="sxs-lookup"><span data-stu-id="05e91-125">**Failures in the message assembly phase**</span></span>  
  
  <span data-ttu-id="05e91-126">處理作業也可能在訊息組合階段失敗；換句話說，在管線元件中發生失敗。</span><span class="sxs-lookup"><span data-stu-id="05e91-126">Processing can also fail during message assembly phase – in other words, failing in pipeline component.</span></span> <span data-ttu-id="05e91-127">在訊息成功組合之後，下一個潛在的失敗點變成傳輸至傳送位置；例如，傳送位置 (屬於夥伴) 可能關閉或不存在。</span><span class="sxs-lookup"><span data-stu-id="05e91-127">After a message successfully assembles, the next potential failure point becomes transmission to Send Location; for example, the Send Location (which belongs to the partner) might be down or not exist.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05e91-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05e91-128">See Also</span></span>  
 [<span data-ttu-id="05e91-129">調查協調流程、連接埠和訊息失敗</span><span class="sxs-lookup"><span data-stu-id="05e91-129">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)