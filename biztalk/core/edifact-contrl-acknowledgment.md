---
title: "EDIFACT CONTRL 通知 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95e1c244-d700-48d3-9416-032ead6d4d6d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ddbc35fecd2412632f0c4a81750a3662e6e7bf11
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="edifact-contrl-acknowledgment"></a><span data-ttu-id="9883c-102">EDIFACT CONTRL 通知</span><span class="sxs-lookup"><span data-stu-id="9883c-102">EDIFACT CONTRL Acknowledgment</span></span>
<span data-ttu-id="9883c-103">CONTRL 通知 (ACK) 可以做為 EDIFACT 編碼訊息的技術和功能通知。</span><span class="sxs-lookup"><span data-stu-id="9883c-103">The CONTRL acknowledgment (ACK) serves as both technical and functional acknowledgment for EDIFACT-encoded messages.</span></span> <span data-ttu-id="9883c-104">如果是做為技術通知，CONTRL 訊息會指示接收交換。</span><span class="sxs-lookup"><span data-stu-id="9883c-104">As a technical acknowledgment, the CONTRL message indicates receipt of an interchange.</span></span> <span data-ttu-id="9883c-105">如果是做為功能通知，CONTRL 訊息會指示接收或拒絕已接收的交換、群組或訊息，並列出錯誤或不支援的功能。</span><span class="sxs-lookup"><span data-stu-id="9883c-105">As a functional acknowledgment, the CONTRL message indicates acceptance or rejection of the received interchange, group, or message, with a list of errors or unsupported functionality.</span></span>  
  
 <span data-ttu-id="9883c-106">完整的 CONTRL 訊息是做為功能通知。</span><span class="sxs-lookup"><span data-stu-id="9883c-106">The full CONTRL message serves as the functional ACK.</span></span> <span data-ttu-id="9883c-107">技術通知會重複使用功能通知的區段。</span><span class="sxs-lookup"><span data-stu-id="9883c-107">Sections of the functional ACK are reused for the technical ACK.</span></span> <span data-ttu-id="9883c-108">如果您已在合作對象屬性中選取技術和功能通知，傳送合作對象或全域屬性，BizTalk Server 會產生兩則 CONTRL 訊息： 技術 CONTRL 通知和功能 CONTRL 通知。</span><span class="sxs-lookup"><span data-stu-id="9883c-108">If you have selected both technical and functional ACKs in the party properties for a sending party or in global properties, BizTalk Server will generate two CONTRL messages: a technical CONTRL ACK and a functional CONTRL ACK.</span></span>  
  
 <span data-ttu-id="9883c-109">CONTRL 通知符合 EFACT_<VERSION\<版本號碼\>number>_contrl.xsd 結構描述。</span><span class="sxs-lookup"><span data-stu-id="9883c-109">The CONTRL ACK conforms to the EFACT_\<Version number\>_CONTRL.xsd schema.</span></span>  
  
## <a name="technical-acknowledgement"></a><span data-ttu-id="9883c-110">技術通知</span><span class="sxs-lookup"><span data-stu-id="9883c-110">Technical Acknowledgement</span></span>  
 <span data-ttu-id="9883c-111">技術通知表示交換的接收者：</span><span class="sxs-lookup"><span data-stu-id="9883c-111">A technical ACK implies that the recipient of the interchange:</span></span>  
  
-   <span data-ttu-id="9883c-112">已經接收主旨交換；</span><span class="sxs-lookup"><span data-stu-id="9883c-112">has received the subject interchange;</span></span>  
  
-   <span data-ttu-id="9883c-113">確認已檢查主旨交換的部分，以便確保複製至報告 UCI 區段的資料元素句法正確；</span><span class="sxs-lookup"><span data-stu-id="9883c-113">acknowledges the parts of the subject interchange that have been checked in order to ensure that the data elements copied into the reporting UCI segment are syntactically correct;</span></span>  
  
-   <span data-ttu-id="9883c-114">已經接受責任，會將主旨交換的其他部分，告知通知或拒絕的傳送者；</span><span class="sxs-lookup"><span data-stu-id="9883c-114">has accepted responsibility for notifying the sender of acknowledgement or rejection of the other parts of the subject interchange;</span></span>  
  
-   <span data-ttu-id="9883c-115">已採取合理的預防措施，確保已將此等訊息通知傳送者。</span><span class="sxs-lookup"><span data-stu-id="9883c-115">and has taken reasonable precautions in order to ensure that the sender is so notified.</span></span>  
  
## <a name="functional-acknowledgement"></a><span data-ttu-id="9883c-116">功能通知</span><span class="sxs-lookup"><span data-stu-id="9883c-116">Functional Acknowledgement</span></span>  
 <span data-ttu-id="9883c-117">功能通知表示交換的接收者：</span><span class="sxs-lookup"><span data-stu-id="9883c-117">A functional ACK implies that the recipient of the interchange:</span></span>  
  
-   <span data-ttu-id="9883c-118">已經接收已通知交換的參考層級；</span><span class="sxs-lookup"><span data-stu-id="9883c-118">has received the referenced levels(s) of the interchange acknowledged;</span></span>  
  
-   <span data-ttu-id="9883c-119">已經檢查已通知參考層級內沒有嚴重的語法錯誤，以防進一步處理交換；</span><span class="sxs-lookup"><span data-stu-id="9883c-119">has checked that there are no fatal syntactic errors in the acknowledged referenced level that prevents further processing of the interchange;</span></span>  
  
-   <span data-ttu-id="9883c-120">已經檢查服務區段的所有已通知部分語意正確 (若無報告任何錯誤)；</span><span class="sxs-lookup"><span data-stu-id="9883c-120">has checked that all acknowledged parts of service segments are semantically correct (if no errors are reported);</span></span>  
  
-   <span data-ttu-id="9883c-121">會遵守服務區段之已通知參考層級內所要求的動作；</span><span class="sxs-lookup"><span data-stu-id="9883c-121">will comply with the actions requested in the acknowledged referenced-levels of the service segments;</span></span>  
  
-   <span data-ttu-id="9883c-122">已經接受責任，若稍後在相關部分偵測到上述語法或語意錯誤，或該部分於已傳送的 CONTRL 訊息被通知之後，因為某些原因無法處理，不會以傳送 CONTRL 訊息的方式，而會以其他方式通知傳送者；</span><span class="sxs-lookup"><span data-stu-id="9883c-122">has accepted responsibility for notifying the sender by other means than sending a CONTRL message if any syntactic or semantic errors as described above, are later detected in the relevant part, or the part cannot be processed for some other reason after the part has been acknowledged in a submitted CONTRL message;</span></span>  
  
-   <span data-ttu-id="9883c-123">已採取合理的預防措施，以確保偵測這類錯誤並已通知傳送者。</span><span class="sxs-lookup"><span data-stu-id="9883c-123">and has taken reasonable precautions in order to ensure that such errors are detected and that the sender is notified.</span></span>  
  
 <span data-ttu-id="9883c-124">拒絕表示交換的接收者：</span><span class="sxs-lookup"><span data-stu-id="9883c-124">Rejection implies that the recipient of the interchange:</span></span>  
  
-   <span data-ttu-id="9883c-125">因為 CONTRL 訊息內所述原因，無法通知主旨交換或其相關部分；</span><span class="sxs-lookup"><span data-stu-id="9883c-125">cannot acknowledge the subject interchange, or the relevant parts of it, for reasons indicated in the CONTRL message;</span></span>  
  
-   <span data-ttu-id="9883c-126">不會針對主旨交換遭拒絕之部分內的商務資訊，採取任何進一步動作。</span><span class="sxs-lookup"><span data-stu-id="9883c-126">and will not take any further action on business information contained in the rejected part of the subject interchange.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9883c-127">本節內容</span><span class="sxs-lookup"><span data-stu-id="9883c-127">In This Section</span></span>  
  
-   [<span data-ttu-id="9883c-128">EDIFACT CONTRL 訊息作為技術通知</span><span class="sxs-lookup"><span data-stu-id="9883c-128">EDIFACT CONTRL Message as Technical Acknowledgment</span></span>](../core/edifact-contrl-message-as-technical-acknowledgment.md)  
  
-   [<span data-ttu-id="9883c-129">EDIFACT CONTRL 訊息作為功能通知</span><span class="sxs-lookup"><span data-stu-id="9883c-129">EDIFACT CONTRL Message as Functional Acknowledgment</span></span>](../core/edifact-contrl-message-as-functional-acknowledgment.md)  
  
## <a name="see-also"></a><span data-ttu-id="9883c-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="9883c-130">See Also</span></span>  
 [<span data-ttu-id="9883c-131">EDI 通知結構</span><span class="sxs-lookup"><span data-stu-id="9883c-131">EDI Acknowledgment Structure</span></span>](../core/edi-acknowledgment-structure.md)