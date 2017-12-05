---
title: "範例商務案例 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTAHL7, business example
- examples, business processes
- health care organizations, business example
- business processes, example
ms.assetid: 54bfbe45-4638-4488-bbd8-c642926a35d3
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78229d903461fe2b84033b036ef02b2838832fc0
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="sample-business-scenario"></a><span data-ttu-id="7472f-102">範例商務案例</span><span class="sxs-lookup"><span data-stu-id="7472f-102">Sample Business Scenario</span></span>
<span data-ttu-id="7472f-103">醫療保健處理程序通常很複雜，而且涉及許多系統。</span><span class="sxs-lookup"><span data-stu-id="7472f-103">Health care processes are often complex and involve many systems.</span></span> <span data-ttu-id="7472f-104">範例是一位病患進入醫院，時發生的程序，並讓醫生傳送實驗室測試病患。</span><span class="sxs-lookup"><span data-stu-id="7472f-104">An example is the process that occurs when a patient enters a hospital, and a physician sends the patient for a lab test.</span></span> <span data-ttu-id="7472f-105">參與這個程序有五個合作對象：</span><span class="sxs-lookup"><span data-stu-id="7472f-105">Involved in this procedure are five parties:</span></span>  
  
-   <span data-ttu-id="7472f-106">顧及醫生</span><span class="sxs-lookup"><span data-stu-id="7472f-106">The attending physician</span></span>  
  
-   <span data-ttu-id="7472f-107">醫院註冊系統</span><span class="sxs-lookup"><span data-stu-id="7472f-107">The Hospital Registration System</span></span>  
  
-   <span data-ttu-id="7472f-108">臨床訂單輸入系統</span><span class="sxs-lookup"><span data-stu-id="7472f-108">The Clinical Order Entry System</span></span>  
  
-   <span data-ttu-id="7472f-109">實驗室系統</span><span class="sxs-lookup"><span data-stu-id="7472f-109">The Laboratory System</span></span>  
  
-   <span data-ttu-id="7472f-110">計費系統</span><span class="sxs-lookup"><span data-stu-id="7472f-110">The Billing System</span></span>  
  
 <span data-ttu-id="7472f-111">在此程序可能會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7472f-111">The following steps might occur in this process:</span></span>  
  
1.  <span data-ttu-id="7472f-112">顧及家裡有醫生註冊病患。</span><span class="sxs-lookup"><span data-stu-id="7472f-112">The attending doctor registers the patient.</span></span>  
  
    1.  <span data-ttu-id="7472f-113">ADT ^ O04 註冊訊息廣播醫院註冊系統。</span><span class="sxs-lookup"><span data-stu-id="7472f-113">An ADT^O04 registration message is broadcast by the Hospital Registration System.</span></span>  
  
    2.  <span data-ttu-id="7472f-114">ADT ^ 訂閱訊息，包括臨床訂單輸入系統和實驗室系統的所有部門都收到 O04 訊息。</span><span class="sxs-lookup"><span data-stu-id="7472f-114">The ADT^O04 message is received by all departments that subscribe to the message, including the Clinical Order Entry System and the Laboratory System.</span></span>  
  
2.  <span data-ttu-id="7472f-115">家裡有醫生排序從實驗室設備診斷研究。</span><span class="sxs-lookup"><span data-stu-id="7472f-115">The doctor orders a diagnostic study from the laboratory facility.</span></span>  
  
    1.  <span data-ttu-id="7472f-116">ORM ^ O01 訂單訊息從臨床訂單輸入系統的商務規則驗證之後傳送。</span><span class="sxs-lookup"><span data-stu-id="7472f-116">An ORM^O01 order message is sent from the Clinical Order Entry System, after validation of business rules.</span></span>  
  
    2.  <span data-ttu-id="7472f-117">ORM ^ 實驗室系統收到 O01 訊息。</span><span class="sxs-lookup"><span data-stu-id="7472f-117">The ORM^O01 message is received by the Laboratory System.</span></span>  
  
3.  <span data-ttu-id="7472f-118">實驗室接收訂單，並傳回確認訊息。</span><span class="sxs-lookup"><span data-stu-id="7472f-118">The laboratory receives the order, and returns a confirmation.</span></span>  
  
    1.  <span data-ttu-id="7472f-119">ORR ^ O02 訂單確認訊息傳送實驗室系統指出，可以執行順序。</span><span class="sxs-lookup"><span data-stu-id="7472f-119">An ORR^O02 order-confirmation message is sent by the Laboratory System, indicating that the order can be executed.</span></span>  
  
    2.  <span data-ttu-id="7472f-120">ORR ^ 臨床訂單輸入系統收到 O02 訊息。</span><span class="sxs-lookup"><span data-stu-id="7472f-120">The ORR^O02 message is received by the Clinical Order Entry System.</span></span>  
  
4.  <span data-ttu-id="7472f-121">完成測試時，實驗室會將結果傳送至家裡有醫生和其他部門。</span><span class="sxs-lookup"><span data-stu-id="7472f-121">On completion of the tests, the laboratory sends the results to the doctor and other departments.</span></span>  
  
    1.  <span data-ttu-id="7472f-122">ORU ^ 從實驗室系統 R01 測試結果訊息傳送。</span><span class="sxs-lookup"><span data-stu-id="7472f-122">An ORU^R01 test-results message is sent from the Laboratory System.</span></span>  
  
    2.  <span data-ttu-id="7472f-123">ORU ^ R01 收到訊息時臨床訂單輸入系統和計費系統。</span><span class="sxs-lookup"><span data-stu-id="7472f-123">The ORU^R01 message is received by the Clinical Order Entry System and the Billing System.</span></span>  
  
    3.  <span data-ttu-id="7472f-124">介面引擎會送出電子郵件訊息中，以 doctor，收到其無線 PDA 的實驗室結果。</span><span class="sxs-lookup"><span data-stu-id="7472f-124">The Interface Engine sends out an e-mail message to the doctor, who receives the lab results on his wireless PDA.</span></span>  
  
## <a name="the-btahl7-solution"></a><span data-ttu-id="7472f-125">BTAHL7 方案</span><span class="sxs-lookup"><span data-stu-id="7472f-125">The BTAHL7 Solution</span></span>  
 <span data-ttu-id="7472f-126">以上所述的範例商務案例是需要整合醫療保健系統的範例。</span><span class="sxs-lookup"><span data-stu-id="7472f-126">The sample business scenario outlined above is an example of a health care system that needs integration.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="7472f-127">BizTalk Server 與[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 提供此功能的下列功能的案例的解決方案：</span><span class="sxs-lookup"><span data-stu-id="7472f-127">BizTalk Server with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) provides a solution for this scenario that features the following functionality:</span></span>  
  
1.  [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="7472f-128">整合的所有系統參與中樞-支點安排方式。</span><span class="sxs-lookup"><span data-stu-id="7472f-128"> integrates all of the systems involved in a hub-and-spoke arrangement.</span></span> <span data-ttu-id="7472f-129">每個系統會直接與通訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7472f-129">Each system communicates directly with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="7472f-130">它們並沒有直接與彼此通訊。</span><span class="sxs-lookup"><span data-stu-id="7472f-130">They do not have to communicate directly to each other.</span></span>  
  
2.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="7472f-131">原生處理 HL7 編碼訊息。</span><span class="sxs-lookup"><span data-stu-id="7472f-131"> handles HL7-encoded messages natively.</span></span> <span data-ttu-id="7472f-132">需要任何自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="7472f-132">No custom coding is required.</span></span>  
  
3.  <span data-ttu-id="7472f-133">ADT ^ O04 註冊訊息廣播給所有訂閱的系統。</span><span class="sxs-lookup"><span data-stu-id="7472f-133">The ADT^O04 registration message is broadcast to all systems that subscribe to it.</span></span> <span data-ttu-id="7472f-134">發行者訂閱者的訊息模型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供有彈性地設定和維護的訂閱訊息的系統清單。</span><span class="sxs-lookup"><span data-stu-id="7472f-134">The publisher-subscriber messaging model for [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides flexibility in setting up and maintaining the list of systems subscribing to the message.</span></span> <span data-ttu-id="7472f-135">您可以新增至系統，或它們從清單中刪除訂用帳戶而不會影響系統的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="7472f-135">You can add systems to or delete them from the subscription list without affecting the rest of the system.</span></span>  
  
4.  <span data-ttu-id="7472f-136">商務規則，用來驗證 ORM ^ 可以動態變更 O01 訂單訊息，而不會影響系統的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="7472f-136">The business rule used to validate the ORM^O01 order message can be changed dynamically without affecting the rest of the system.</span></span>  
  
5.  [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="7472f-137">可以設定為自動產生 ORR ^ O02 訂單 (ACK) 訊息。</span><span class="sxs-lookup"><span data-stu-id="7472f-137"> can be configured to automatically generate the ORR^O02 order-confirmation (ACK) message.</span></span>  
  
6.  <span data-ttu-id="7472f-138">如有必要，您可以任何與其他人進行傳送，訊息批次，並在收到的批次中處理它們。</span><span class="sxs-lookup"><span data-stu-id="7472f-138">If necessary, you can batch any of the messages with others for sending, and process them on receipt from within the batch.</span></span>  
  
7.  <span data-ttu-id="7472f-139">您可以驗證所有的訊息在引擎也可以根據[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]HL7 組織發佈 2 X 結構描述。</span><span class="sxs-lookup"><span data-stu-id="7472f-139">You can validate all messages in the engine and against the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2X schemas published by the HL7 organization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7472f-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="7472f-140">See Also</span></span>  
 [<span data-ttu-id="7472f-141">BizTalk Server 如何解決商務需求</span><span class="sxs-lookup"><span data-stu-id="7472f-141">How BizTalk Server Solves the Business Need</span></span>](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)