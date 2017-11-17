---
title: "記錄設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- auditing, configuring
ms.assetid: 5cd7aec1-bd38-4d37-9a79-b01eeb89337d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 058a1fce8105a3147fb2e537a9182e7d886bb953
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="logging-configuration"></a><span data-ttu-id="e0748-102">記錄設定</span><span class="sxs-lookup"><span data-stu-id="e0748-102">Logging Configuration</span></span>
<span data-ttu-id="e0748-103">在一起， [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]和[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]提供交易式和數位企業應用程式整合 (EAI) 的安全通訊醫院、 實務，等護士家庭的醫療保健業者。</span><span class="sxs-lookup"><span data-stu-id="e0748-103">Together, [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] and [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] offer secure transactional and digital Enterprise Application Integration (EAI) communications for health care providers such as hospitals, clinics, and nursing homes.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="e0748-104">可讓您來協調應用程式活動與交易處理，以動態方式將訊息路由、 驗證和轉換資料，以及透過各種不同的配接器的傳輸。</span><span class="sxs-lookup"><span data-stu-id="e0748-104"> provides the ability to coordinate application activity and transaction processing, dynamically route messages, validate and transform data, and transport over a variety of adapters.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="e0748-105">支援 American National Standards Institute ANSI accredited 健全狀況層級七 (HL7) 訊息標準門診和系統管理提供者網路中的應用程式用來交換醫療即時資料。</span><span class="sxs-lookup"><span data-stu-id="e0748-105"> supports the American National Standards Institute (ANSI)-accredited Health Level Seven (HL7) messaging standard used by clinical and administrative applications in provider networks to exchange medical data in real-time.</span></span>  
  
 <span data-ttu-id="e0748-106">通過 accelerator 系統 HL7 訊息可以是非常重要。</span><span class="sxs-lookup"><span data-stu-id="e0748-106">The HL7 messages that pass through the accelerator system can be very critical.</span></span> <span data-ttu-id="e0748-107">例如，資料可能是病患的就醫記錄或財務交易。</span><span class="sxs-lookup"><span data-stu-id="e0748-107">For example, the data could be a patient's medical record or a financial transaction.</span></span> <span data-ttu-id="e0748-108">若要確保 HL7 安全性與隱私權法規的相容性，系統管理員必須能夠執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="e0748-108">To ensure compliance with HL7 security and privacy regulations, system administrators must be able to do the following:</span></span>  
  
-   <span data-ttu-id="e0748-109">偵錯已擱置的訊息</span><span class="sxs-lookup"><span data-stu-id="e0748-109">Debug suspended messages</span></span>  
  
-   <span data-ttu-id="e0748-110">監視系統和檔案存取，持續地偵測潛在的入侵者，並降低風險的安全性漏洞</span><span class="sxs-lookup"><span data-stu-id="e0748-110">Monitor system and file access on an ongoing basis to detect potential intruders and reduce the risk of security breaches</span></span>  
  
 <span data-ttu-id="e0748-111">本章節提供讓您設定稽核和記錄檢查和稽核資料和事件記錄檔中，解譯及針對記錄的資料執行查詢的概念和程序資訊。</span><span class="sxs-lookup"><span data-stu-id="e0748-111">This section provides conceptual and procedural information to enable you to configure auditing and logging, examine and interpret audit data and event logs, and run queries against the logged data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0748-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="e0748-112">In This Section</span></span>  
  
-   [<span data-ttu-id="e0748-113">關於記錄處理程序</span><span class="sxs-lookup"><span data-stu-id="e0748-113">About the Logging Process</span></span>](../../adapters-and-accelerators/accelerator-hl7/about-the-logging-process.md)  
  
-   [<span data-ttu-id="e0748-114">設定記錄</span><span class="sxs-lookup"><span data-stu-id="e0748-114">Configuring Logging</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)