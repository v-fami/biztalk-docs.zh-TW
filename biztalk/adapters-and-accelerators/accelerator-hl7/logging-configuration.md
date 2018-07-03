---
title: 記錄設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- auditing, configuring
ms.assetid: 5cd7aec1-bd38-4d37-9a79-b01eeb89337d
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 83e15247158dd21c237064692931a83f6885f05e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002455"
---
# <a name="logging-configuration"></a><span data-ttu-id="f30dd-102">記錄組態</span><span class="sxs-lookup"><span data-stu-id="f30dd-102">Logging Configuration</span></span>
<span data-ttu-id="f30dd-103">在一起，MicrosoftBizTalk 伺服器和[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]提供交易式和數位企業應用程式整合 (EAI) 的安全通訊醫院、 實務課程等護理住家的醫療保健業者。</span><span class="sxs-lookup"><span data-stu-id="f30dd-103">Together, MicrosoftBizTalk Server and [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] offer secure transactional and digital Enterprise Application Integration (EAI) communications for health care providers such as hospitals, clinics, and nursing homes.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f30dd-104"> 讓您能夠協調應用程式活動和交易處理、 以動態方式將訊息路由傳送、 驗證和轉換資料，並透過各種不同的配接器的傳輸。</span><span class="sxs-lookup"><span data-stu-id="f30dd-104"> provides the ability to coordinate application activity and transaction processing, dynamically route messages, validate and transform data, and transport over a variety of adapters.</span></span> [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]<span data-ttu-id="f30dd-105"> 支援 American National Standards Institute ANSI accredited 健全狀況層級 7 (HL7) 傳訊臨床和系統管理提供者網路中的應用程式用來交換即時的醫療資料的標準。</span><span class="sxs-lookup"><span data-stu-id="f30dd-105"> supports the American National Standards Institute (ANSI)-accredited Health Level Seven (HL7) messaging standard used by clinical and administrative applications in provider networks to exchange medical data in real-time.</span></span>  
  
 <span data-ttu-id="f30dd-106">HL7 訊息通過加速器系統可以是非常重要。</span><span class="sxs-lookup"><span data-stu-id="f30dd-106">The HL7 messages that pass through the accelerator system can be very critical.</span></span> <span data-ttu-id="f30dd-107">例如，資料可能是某個病患的醫療記錄或財務交易。</span><span class="sxs-lookup"><span data-stu-id="f30dd-107">For example, the data could be a patient's medical record or a financial transaction.</span></span> <span data-ttu-id="f30dd-108">若要確保 HL7 安全性與隱私權法規的合規性，系統管理員必須能夠執行下列作業：</span><span class="sxs-lookup"><span data-stu-id="f30dd-108">To ensure compliance with HL7 security and privacy regulations, system administrators must be able to do the following:</span></span>  
  
- <span data-ttu-id="f30dd-109">偵錯已擱置的訊息</span><span class="sxs-lookup"><span data-stu-id="f30dd-109">Debug suspended messages</span></span>  
  
- <span data-ttu-id="f30dd-110">監視系統和檔案來偵測可能入侵者並減少安全性缺口的風險持續不斷的存取</span><span class="sxs-lookup"><span data-stu-id="f30dd-110">Monitor system and file access on an ongoing basis to detect potential intruders and reduce the risk of security breaches</span></span>  
  
  <span data-ttu-id="f30dd-111">本節提供概念和程序的資訊，讓您設定稽核和記錄檢查和解譯稽核資料和事件記錄檔，並針對記錄的資料執行查詢。</span><span class="sxs-lookup"><span data-stu-id="f30dd-111">This section provides conceptual and procedural information to enable you to configure auditing and logging, examine and interpret audit data and event logs, and run queries against the logged data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f30dd-112">本節內容</span><span class="sxs-lookup"><span data-stu-id="f30dd-112">In This Section</span></span>  
  
-   [<span data-ttu-id="f30dd-113">關於記錄處理程序</span><span class="sxs-lookup"><span data-stu-id="f30dd-113">About the Logging Process</span></span>](../../adapters-and-accelerators/accelerator-hl7/about-the-logging-process.md)  
  
-   [<span data-ttu-id="f30dd-114">設定記錄</span><span class="sxs-lookup"><span data-stu-id="f30dd-114">Configuring Logging</span></span>](../../adapters-and-accelerators/accelerator-hl7/configuring-logging.md)