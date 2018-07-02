---
title: 範例商務案例 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BTAHL7, business example
- examples, business processes
- health care organizations, business example
- business processes, example
ms.assetid: 54bfbe45-4638-4488-bbd8-c642926a35d3
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a6b88bd76a1fac2ebfa5c2f75a6abbf78aab75b7
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36966903"
---
# <a name="sample-business-scenario"></a><span data-ttu-id="d0e5c-102">商務案例範例</span><span class="sxs-lookup"><span data-stu-id="d0e5c-102">Sample Business Scenario</span></span>
<span data-ttu-id="d0e5c-103">醫療保健的程序通常很複雜，而且牽涉到許多系統。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-103">Health care processes are often complex and involve many systems.</span></span> <span data-ttu-id="d0e5c-104">範例是發生於某個病患進入醫院中，程序，並讓醫生傳送實驗室測試病患。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-104">An example is the process that occurs when a patient enters a hospital, and a physician sends the patient for a lab test.</span></span> <span data-ttu-id="d0e5c-105">參與此程序有五個合作對象：</span><span class="sxs-lookup"><span data-stu-id="d0e5c-105">Involved in this procedure are five parties:</span></span>  
  
- <span data-ttu-id="d0e5c-106">參加醫生</span><span class="sxs-lookup"><span data-stu-id="d0e5c-106">The attending physician</span></span>  
  
- <span data-ttu-id="d0e5c-107">醫院註冊系統</span><span class="sxs-lookup"><span data-stu-id="d0e5c-107">The Hospital Registration System</span></span>  
  
- <span data-ttu-id="d0e5c-108">臨床訂單輸入系統</span><span class="sxs-lookup"><span data-stu-id="d0e5c-108">The Clinical Order Entry System</span></span>  
  
- <span data-ttu-id="d0e5c-109">實驗室系統</span><span class="sxs-lookup"><span data-stu-id="d0e5c-109">The Laboratory System</span></span>  
  
- <span data-ttu-id="d0e5c-110">計費系統</span><span class="sxs-lookup"><span data-stu-id="d0e5c-110">The Billing System</span></span>  
  
  <span data-ttu-id="d0e5c-111">在此程序可能會執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d0e5c-111">The following steps might occur in this process:</span></span>  
  
1.  <span data-ttu-id="d0e5c-112">參加醫生註冊病患。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-112">The attending doctor registers the patient.</span></span>  
  
    1.  <span data-ttu-id="d0e5c-113">ADT ^ O04 註冊訊息廣播醫院註冊系統。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-113">An ADT^O04 registration message is broadcast by the Hospital Registration System.</span></span>  
  
    2.  <span data-ttu-id="d0e5c-114">ADT ^ 訂閱訊息，包括臨床訂單輸入系統和實驗室系統的所有部門都收到 O04 訊息。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-114">The ADT^O04 message is received by all departments that subscribe to the message, including the Clinical Order Entry System and the Laboratory System.</span></span>  
  
2.  <span data-ttu-id="d0e5c-115">醫生排序從實驗室設備的診斷研究。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-115">The doctor orders a diagnostic study from the laboratory facility.</span></span>  
  
    1.  <span data-ttu-id="d0e5c-116">ORM ^ O01 訂單訊息會從臨床訂單輸入系統的商務規則驗證之後傳送。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-116">An ORM^O01 order message is sent from the Clinical Order Entry System, after validation of business rules.</span></span>  
  
    2.  <span data-ttu-id="d0e5c-117">ORM ^ 與實驗系統收到 O01 訊息。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-117">The ORM^O01 message is received by the Laboratory System.</span></span>  
  
3.  <span data-ttu-id="d0e5c-118">實驗室環境接收訂單，並會傳回確認。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-118">The laboratory receives the order, and returns a confirmation.</span></span>  
  
    1.  <span data-ttu-id="d0e5c-119">ORR ^ O02 訂單確認訊息系統傳送的實驗室，表示可以執行的順序。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-119">An ORR^O02 order-confirmation message is sent by the Laboratory System, indicating that the order can be executed.</span></span>  
  
    2.  <span data-ttu-id="d0e5c-120">ORR ^ 臨床訂單輸入系統收到 O02 訊息。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-120">The ORR^O02 message is received by the Clinical Order Entry System.</span></span>  
  
4.  <span data-ttu-id="d0e5c-121">測試完成時，實驗室環境會將結果傳送至醫生和其他部門。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-121">On completion of the tests, the laboratory sends the results to the doctor and other departments.</span></span>  
  
    1.  <span data-ttu-id="d0e5c-122">ORU ^ R01 測試結果的訊息傳來與實驗系統。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-122">An ORU^R01 test-results message is sent from the Laboratory System.</span></span>  
  
    2.  <span data-ttu-id="d0e5c-123">ORU ^ R01 收到訊息時臨床訂單輸入系統和計費系統。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-123">The ORU^R01 message is received by the Clinical Order Entry System and the Billing System.</span></span>  
  
    3.  <span data-ttu-id="d0e5c-124">介面引擎會送出電子郵件訊息中，醫生，他無線 PDA 的實驗室結果會接收到。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-124">The Interface Engine sends out an e-mail message to the doctor, who receives the lab results on his wireless PDA.</span></span>  
  
## <a name="the-btahl7-solution"></a><span data-ttu-id="d0e5c-125">BTAHL7 方案</span><span class="sxs-lookup"><span data-stu-id="d0e5c-125">The BTAHL7 Solution</span></span>  
 <span data-ttu-id="d0e5c-126">以上所述的範例商務案例是健康照護系統整合所需的範例。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-126">The sample business scenario outlined above is an example of a health care system that needs integration.</span></span> <span data-ttu-id="d0e5c-127">Microsoft BizTalk Accelerator for HL7 MicrosoftBizTalk 伺服器 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) 提供的解決方案，此案例中，具有下列功能：</span><span class="sxs-lookup"><span data-stu-id="d0e5c-127">MicrosoftBizTalk Server with Microsoft BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) provides a solution for this scenario that features the following functionality:</span></span>  
  
1. [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="d0e5c-128"> 將所有參與中樞-支點安排系統相整合。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-128"> integrates all of the systems involved in a hub-and-spoke arrangement.</span></span> <span data-ttu-id="d0e5c-129">每個系統會直接與通訊[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-129">Each system communicates directly with [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="d0e5c-130">它們不必向彼此直接通訊。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-130">They do not have to communicate directly to each other.</span></span>  
  
2. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="d0e5c-131"> 原生處理 HL7 編碼訊息。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-131"> handles HL7-encoded messages natively.</span></span> <span data-ttu-id="d0e5c-132">需要任何自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-132">No custom coding is required.</span></span>  
  
3. <span data-ttu-id="d0e5c-133">ADT ^ O04 註冊訊息廣播給所有訂閱的系統。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-133">The ADT^O04 registration message is broadcast to all systems that subscribe to it.</span></span> <span data-ttu-id="d0e5c-134">發行者訂閱傳訊模型[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]提供設定和維護的訂閱訊息的系統清單中的彈性。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-134">The publisher-subscriber messaging model for [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] provides flexibility in setting up and maintaining the list of systems subscribing to the message.</span></span> <span data-ttu-id="d0e5c-135">您可以新增至系統，或刪除這些訂用帳戶清單中，而不會影響系統的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-135">You can add systems to or delete them from the subscription list without affecting the rest of the system.</span></span>  
  
4. <span data-ttu-id="d0e5c-136">商務規則，用來驗證 ORM ^ 可以動態變更 O01 訂單訊息，而不會影響系統的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-136">The business rule used to validate the ORM^O01 order message can be changed dynamically without affecting the rest of the system.</span></span>  
  
5. [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="d0e5c-137"> 可以設定為自動產生 ORR ^ O02 訂單 (ACK) 訊息。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-137"> can be configured to automatically generate the ORR^O02 order-confirmation (ACK) message.</span></span>  
  
6. <span data-ttu-id="d0e5c-138">如有必要，您可以任何與其他人進行傳送，訊息批次，並在收到的批次中處理它們。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-138">If necessary, you can batch any of the messages with others for sending, and process them on receipt from within the batch.</span></span>  
  
7. <span data-ttu-id="d0e5c-139">您可以驗證所有的訊息引擎中，而是針對[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]HL7 組織發佈 2 X 結構描述。</span><span class="sxs-lookup"><span data-stu-id="d0e5c-139">You can validate all messages in the engine and against the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]2X schemas published by the HL7 organization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e5c-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0e5c-140">See Also</span></span>  
 [<span data-ttu-id="d0e5c-141">BizTalk Server 如何解決商務需求</span><span class="sxs-lookup"><span data-stu-id="d0e5c-141">How BizTalk Server Solves the Business Need</span></span>](../../adapters-and-accelerators/accelerator-hl7/how-biztalk-server-solves-the-business-need2.md)