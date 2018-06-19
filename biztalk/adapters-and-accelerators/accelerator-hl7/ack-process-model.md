---
title: ACK 處理序模型 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- acknowledgements, process flow
- ACK process model
ms.assetid: 3c6a5eef-57ef-41f7-9782-e1cbc4dd78e1
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 846ecf4d8eee4eca0e8a75a3444a1478b7db5910
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22205918"
---
# <a name="ack-process-model"></a><span data-ttu-id="217d4-102">ACK 處理序模型</span><span class="sxs-lookup"><span data-stu-id="217d4-102">ACK Process Model</span></span>
<span data-ttu-id="217d4-103">下列步驟順序說明通知 (ACK) 的處理序模型：</span><span class="sxs-lookup"><span data-stu-id="217d4-103">The following sequence of steps describes the acknowledgment (ACK) process model:</span></span>  
  
1.  <span data-ttu-id="217d4-104">當許可人員記錄病患許可資訊到許可系統 (ADT) 時，系統就會產生觸發程序事件。</span><span class="sxs-lookup"><span data-stu-id="217d4-104">When the admissions personnel log patient admission information into the Admissions System (ADT), the system generates a trigger event.</span></span>  
  
2.  <span data-ttu-id="217d4-105">ADT 系統會產生 HL7 編碼病患登錄訊息 (ADT ^ A04) 並將其傳遞至 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="217d4-105">The ADT system generates an HL7-encoded Patient Registration message (ADT^A04) and delivers it to BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).</span></span>  
  
3.  <span data-ttu-id="217d4-106">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]系統 ADT 上套用的 MLLP 包裝函式 ^ A04 訊息和路由傳送至[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎介面。</span><span class="sxs-lookup"><span data-stu-id="217d4-106">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] system applies an MLLP wrapper on the ADT^A04 message and routes it to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine.</span></span>  
  
    -   <span data-ttu-id="217d4-107">預先設定的 「 原始模式 」 通知需求</span><span class="sxs-lookup"><span data-stu-id="217d4-107">Requirement of 'Original Mode' Acknowledgment is preconfigured</span></span>  
  
    -   <span data-ttu-id="217d4-108">MSH 15 和 16 具有 null 值</span><span class="sxs-lookup"><span data-stu-id="217d4-108">MSH 15 and 16 have null values</span></span>  
  
4.  <span data-ttu-id="217d4-109">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會驗證訊息，並在驗證成功時，它會產生通知訊息的狀態**MSA01 = AA**。</span><span class="sxs-lookup"><span data-stu-id="217d4-109">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine validates the message and if successful validation occurs, it generates the ACK message with the status **MSA01 = AA**.</span></span>  
  
5.  <span data-ttu-id="217d4-110">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎轉換 ADT ^ A04 封閉式與 MLLP 包裝函式和實驗室資訊系統 (LIS) 路由傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="217d4-110">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine transforms the ADT^A04 message by enclosing it with MLLP wrappers and routing it to the Lab Information System (LIS).</span></span>  
  
    -   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="217d4-111">預先設定了加強模式通知</span><span class="sxs-lookup"><span data-stu-id="217d4-111"> preconfigures 'Enhanced Mode' Acknowledgment</span></span>  
  
    -   <span data-ttu-id="217d4-112">MSH 15 和 16 = AL</span><span class="sxs-lookup"><span data-stu-id="217d4-112">MSH 15 and 16 = AL</span></span>  
  
6.  <span data-ttu-id="217d4-113">LIS 介面層級驗證標頭認可訊息，以及產生接受通知狀態由**MSA1 = CA**。</span><span class="sxs-lookup"><span data-stu-id="217d4-113">The LIS Interface Layer validates the header by committing the message and generating an ACCEPT ACK with the status **MSA1 = CA**.</span></span> <span data-ttu-id="217d4-114">介面層路由傳送訊息的 MLLP 包裝函式與[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎介面。</span><span class="sxs-lookup"><span data-stu-id="217d4-114">The interface layer routes the message with the MLLP wrapper to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine.</span></span>  
  
7.  <span data-ttu-id="217d4-115">LIS 介面層會驗證整個訊息，並產生狀態與應用程式通知**MSA1 = AA**。</span><span class="sxs-lookup"><span data-stu-id="217d4-115">The LIS Interface Layer validates the entire message and generates an APPLICATION ACK with the status **MSA1 = AA**.</span></span> <span data-ttu-id="217d4-116">介面層路由傳送訊息的 MLLP 包裝函式與[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]引擎介面。</span><span class="sxs-lookup"><span data-stu-id="217d4-116">The interface layer routes the message with the MLLP wrapper to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine.</span></span>  
  
    -   [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="217d4-117">預先設定了 '需要通知' 認可通知</span><span class="sxs-lookup"><span data-stu-id="217d4-117"> preconfigures 'ACK Required' acknowledging the acknowledgment</span></span>  
  
    -   <span data-ttu-id="217d4-118">MSH 15 = AL，指出接收的系統必須認可的認可接受訊息通知</span><span class="sxs-lookup"><span data-stu-id="217d4-118">MSH 15 = AL, which indicates that the receiving system must acknowledge the ACK with a Commit Accept Message</span></span>  
  
8.  <span data-ttu-id="217d4-119">LIS 介面層會將訊息傳遞至格式需求根據應用程式層。</span><span class="sxs-lookup"><span data-stu-id="217d4-119">The LIS Interface layer delivers the message to the Application Layer in accordance with the format requirement.</span></span>  
  
9. <span data-ttu-id="217d4-120">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會驗證從 LIS 介面層 （在步驟 7 上述） 接收到 ACK，並會回到 LIS 介面層，狀態通知以回應**MSA1 = CA**。</span><span class="sxs-lookup"><span data-stu-id="217d4-120">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine validates the ACK received from the LIS Interface Layer (in step 7 above) and responds with an ACK back to the LIS Interface Layer with the status **MSA1= CA**.</span></span>  
  
10. <span data-ttu-id="217d4-121">LIS 系統的使用者檢閱病患資訊。</span><span class="sxs-lookup"><span data-stu-id="217d4-121">A user of the LIS System reviews the Patient information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="217d4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="217d4-122">See Also</span></span>  
 <span data-ttu-id="217d4-123">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="217d4-123">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 [<span data-ttu-id="217d4-124">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="217d4-124">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)