---
title: ACK 處理序模型 |Microsoft Docs
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
ms.openlocfilehash: 98fac157c3c3bfa62825fd3c5cb59c68aac528e6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970631"
---
# <a name="ack-process-model"></a><span data-ttu-id="6abe0-102">ACK 處理序模型</span><span class="sxs-lookup"><span data-stu-id="6abe0-102">ACK Process Model</span></span>
<span data-ttu-id="6abe0-103">下列步驟順序說明通知 (ACK) 處理序模型：</span><span class="sxs-lookup"><span data-stu-id="6abe0-103">The following sequence of steps describes the acknowledgment (ACK) process model:</span></span>  
  
1. <span data-ttu-id="6abe0-104">當許可人員記錄病患住院資訊到許可系統 (ADT) 中時，系統就會產生的觸發程序事件。</span><span class="sxs-lookup"><span data-stu-id="6abe0-104">When the admissions personnel log patient admission information into the Admissions System (ADT), the system generates a trigger event.</span></span>  
  
2. <span data-ttu-id="6abe0-105">ADT 系統會產生 HL7 編碼病患註冊訊息 (ADT ^ A04) 並將其傳遞到 BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="6abe0-105">The ADT system generates an HL7-encoded Patient Registration message (ADT^A04) and delivers it to BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]).</span></span>  
  
3. <span data-ttu-id="6abe0-106">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] ADT 系統套用的 MLLP 包裝函式 ^ A04 訊息和路由傳送至[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎。</span><span class="sxs-lookup"><span data-stu-id="6abe0-106">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] system applies an MLLP wrapper on the ADT^A04 message and routes it to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine.</span></span>  
  
   -   <span data-ttu-id="6abe0-107">預先設定的 「 原始模式 」 通知的需求</span><span class="sxs-lookup"><span data-stu-id="6abe0-107">Requirement of 'Original Mode' Acknowledgment is preconfigured</span></span>  
  
   -   <span data-ttu-id="6abe0-108">MSH 15 和 16 具有 null 值</span><span class="sxs-lookup"><span data-stu-id="6abe0-108">MSH 15 and 16 have null values</span></span>  
  
4. <span data-ttu-id="6abe0-109">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會驗證訊息，並發生驗證成功時，它會產生通知訊息的狀態**MSA01 = AA**。</span><span class="sxs-lookup"><span data-stu-id="6abe0-109">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine validates the message and if successful validation occurs, it generates the ACK message with the status **MSA01 = AA**.</span></span>  
  
5. <span data-ttu-id="6abe0-110">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎轉換 ADT ^ A04 住它使用 MLLP 包裝函式，並將其路由至實驗室的資訊系統 (LIS) 的訊息。</span><span class="sxs-lookup"><span data-stu-id="6abe0-110">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine transforms the ADT^A04 message by enclosing it with MLLP wrappers and routing it to the Lab Information System (LIS).</span></span>  
  
   - [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="6abe0-111"> 預先設定增強式模式通知</span><span class="sxs-lookup"><span data-stu-id="6abe0-111"> preconfigures 'Enhanced Mode' Acknowledgment</span></span>  
  
   - <span data-ttu-id="6abe0-112">MSH 15 和 16 = AL</span><span class="sxs-lookup"><span data-stu-id="6abe0-112">MSH 15 and 16 = AL</span></span>  
  
6. <span data-ttu-id="6abe0-113">LIS 介面層驗證標頭認可訊息，並產生狀態接受 ACK **MSA1 = CA**。</span><span class="sxs-lookup"><span data-stu-id="6abe0-113">The LIS Interface Layer validates the header by committing the message and generating an ACCEPT ACK with the status **MSA1 = CA**.</span></span> <span data-ttu-id="6abe0-114">介面層將 MLLP 包裝函式的訊息路由傳送[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎。</span><span class="sxs-lookup"><span data-stu-id="6abe0-114">The interface layer routes the message with the MLLP wrapper to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine.</span></span>  
  
7. <span data-ttu-id="6abe0-115">LIS 介面層會驗證整個訊息，並產生具有狀態應用程式通知**MSA1 = AA**。</span><span class="sxs-lookup"><span data-stu-id="6abe0-115">The LIS Interface Layer validates the entire message and generates an APPLICATION ACK with the status **MSA1 = AA**.</span></span> <span data-ttu-id="6abe0-116">介面層將 MLLP 包裝函式的訊息路由傳送[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎。</span><span class="sxs-lookup"><span data-stu-id="6abe0-116">The interface layer routes the message with the MLLP wrapper to the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine.</span></span>  
  
   - [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="6abe0-117"> 預先設定了 '需要通知' 認可通知</span><span class="sxs-lookup"><span data-stu-id="6abe0-117"> preconfigures 'ACK Required' acknowledging the acknowledgment</span></span>  
  
   - <span data-ttu-id="6abe0-118">MSH 15 = AL，這表示接收系統必須認可的認可接受訊息通知</span><span class="sxs-lookup"><span data-stu-id="6abe0-118">MSH 15 = AL, which indicates that the receiving system must acknowledge the ACK with a Commit Accept Message</span></span>  
  
8. <span data-ttu-id="6abe0-119">LIS 介面層會將訊息傳遞至格式需求根據應用程式層。</span><span class="sxs-lookup"><span data-stu-id="6abe0-119">The LIS Interface layer delivers the message to the Application Layer in accordance with the format requirement.</span></span>  
  
9. <span data-ttu-id="6abe0-120">[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]介面引擎會驗證從 LIS 介面層 （在步驟 7） 接收到通知，並回到 LIS 介面層，具有狀態的通知以回應**MSA1 = CA**。</span><span class="sxs-lookup"><span data-stu-id="6abe0-120">The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Interface Engine validates the ACK received from the LIS Interface Layer (in step 7 above) and responds with an ACK back to the LIS Interface Layer with the status **MSA1= CA**.</span></span>  
  
10. <span data-ttu-id="6abe0-121">LIS 系統的使用者會檢閱病患資訊。</span><span class="sxs-lookup"><span data-stu-id="6abe0-121">A user of the LIS System reviews the Patient information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6abe0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6abe0-122">See Also</span></span>  
 <span data-ttu-id="6abe0-123">[建立及處理通知](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span><span class="sxs-lookup"><span data-stu-id="6abe0-123">[Creating and Processing Acknowledgments](../../adapters-and-accelerators/accelerator-hl7/creating-and-processing-acknowledgments.md) </span></span>  
 [<span data-ttu-id="6abe0-124">程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6abe0-124">Programming Guide</span></span>](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)