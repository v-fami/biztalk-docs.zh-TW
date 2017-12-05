---
title: "安全性與隱私權的標準 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, privacy standards
- privacy standards
- security
- security, about security
- BizTalk Accelerator for SWIFT, security
- security, BizTalk Accelerator for SWIFT
ms.assetid: 5794b25f-8a73-4f5b-97ef-1b0f61775c4b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be03cce0c0d482563ac12bbd3b60cead04b2ccfa
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
---
# <a name="security-and-privacy-standards"></a><span data-ttu-id="8f6dc-102">安全性與隱私權的標準</span><span class="sxs-lookup"><span data-stu-id="8f6dc-102">Security and privacy standards</span></span>
<span data-ttu-id="8f6dc-103">財務服務應用程式和整合解決方案開發使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]通常受到原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安全性功能。</span><span class="sxs-lookup"><span data-stu-id="8f6dc-103">Financial Services applications and integration solutions developed using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] are generally secured by native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security features.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="8f6dc-104">會使用積極的安全性機制，例如既定網際網路加密訊息標準及傳輸通訊協定簽署憑證，[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證，以及企業單一登入安全[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式、 資料和執行階段。</span><span class="sxs-lookup"><span data-stu-id="8f6dc-104"> uses aggressive security mechanisms such as de facto Internet encrypted messaging standards and transport protocols, signing certificates, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and Enterprise Single Sign-On to secure [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, data, and runtime.</span></span>  
  
 <span data-ttu-id="8f6dc-105">使用建立解決方案[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] 2000年[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，A4SWIFT 可以幫助您符合協會全球 Interbank 財務 Telecommunication (SWIFT) 財務交易的安全性和隱私權指導方針。</span><span class="sxs-lookup"><span data-stu-id="8f6dc-105">Solutions built with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] 2000, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], and A4SWIFT can help you to meet the security and privacy guidelines for Society for Worldwide Interbank Financial Telecommunication (SWIFT) financial transactions.</span></span>  
  
 <span data-ttu-id="8f6dc-106">除了原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安全性功能，A4SWIFT 提供特定的使用者訊息項目、 修復、 核准，以及提交 SWIFT 訊息所保護的使用者層級安全性。</span><span class="sxs-lookup"><span data-stu-id="8f6dc-106">In addition to native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security features, A4SWIFT provides user-level security specific to securing end-user message entry, repair, approval, and submission of SWIFT messages.</span></span> <span data-ttu-id="8f6dc-107">此安全性達成方式是使用[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]用數位簽章技術也可以使用 A4SWIFT 執行階段服務驗證憑證和資料完整性。</span><span class="sxs-lookup"><span data-stu-id="8f6dc-107">This security is achieved by using [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] digital signing technologies and by using A4SWIFT runtime services to verify certificate and data integrity.</span></span>  
  
 <span data-ttu-id="8f6dc-108">請務必考量您 SWIFT 的訊息和輸入或編輯使用者，在傳輸中和 while 時，所包含的資訊保護的量值[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]加以處理和儲存。</span><span class="sxs-lookup"><span data-stu-id="8f6dc-108">It is important to consider measures for securing your SWIFT messages and the information they contain when they are entered or edited by end-users, in transit, and while [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] processes and stores them.</span></span>  
  
 <span data-ttu-id="8f6dc-109">在一起，BizTalk Server 和 A4SWIFT 提供平台、 基礎結構，以及工具設計、 開發和執行安全通訊的 SWIFT 和工作流程自動化系統。</span><span class="sxs-lookup"><span data-stu-id="8f6dc-109">Together, BizTalk Server and A4SWIFT provide the platform, infrastructure, and tools for designing, developing, and executing secure SWIFT messaging and workflow automation systems.</span></span>  
  
 <span data-ttu-id="8f6dc-110">當實作安全性，您必須設計和開發許多區域。</span><span class="sxs-lookup"><span data-stu-id="8f6dc-110">When implementing security, you must design and develop many areas.</span></span> <span data-ttu-id="8f6dc-111">下列清單是這些區域的高層級檢視：</span><span class="sxs-lookup"><span data-stu-id="8f6dc-111">The following list is a high-level view of these areas:</span></span>  
  
-   <span data-ttu-id="8f6dc-112">開發的 IT 安全性原則</span><span class="sxs-lookup"><span data-stu-id="8f6dc-112">Develop an IT security policy</span></span>  
  
-   <span data-ttu-id="8f6dc-113">設計和實作防禦策略</span><span class="sxs-lookup"><span data-stu-id="8f6dc-113">Design and implement a defense strategy</span></span>  
  
-   <span data-ttu-id="8f6dc-114">設計和實作伺服器鎖定策略</span><span class="sxs-lookup"><span data-stu-id="8f6dc-114">Design and implement a server lockdown strategy</span></span>  
  
-   <span data-ttu-id="8f6dc-115">設計和實作掃描策略</span><span class="sxs-lookup"><span data-stu-id="8f6dc-115">Design and implement an antivirus strategy</span></span>  
  
-   <span data-ttu-id="8f6dc-116">設計和實作備份和還原策略</span><span class="sxs-lookup"><span data-stu-id="8f6dc-116">Design and implement a backup and restore strategy</span></span>  
  
-   <span data-ttu-id="8f6dc-117">設計和實作更新管理策略</span><span class="sxs-lookup"><span data-stu-id="8f6dc-117">Design and implement an update management strategy</span></span>  
  
-   <span data-ttu-id="8f6dc-118">設計和實作的稽核和入侵偵測策略</span><span class="sxs-lookup"><span data-stu-id="8f6dc-118">Design and implement an auditing and intrusion detection strategy</span></span>  
  
-   <span data-ttu-id="8f6dc-119">設計事件回應計劃</span><span class="sxs-lookup"><span data-stu-id="8f6dc-119">Design an incident response plan</span></span>  
  
 <span data-ttu-id="8f6dc-120">本主題中提供的資訊不會涵蓋上述清單中的所有資訊或提供財務服務相容的解決方案。</span><span class="sxs-lookup"><span data-stu-id="8f6dc-120">The information provided in this topic does not cover all the information in the preceding list or deliver a financial services-compliant solution.</span></span> <span data-ttu-id="8f6dc-121">本主題的目的是方法的提供很好的起點，並協助底線結構化和完整對於安全性的重要性。</span><span class="sxs-lookup"><span data-stu-id="8f6dc-121">The purpose of this topic is to provide a good starting point and to help underscore the importance of a structured and comprehensive approach to security.</span></span>  
  
 <span data-ttu-id="8f6dc-122">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="8f6dc-122">This section contains:</span></span>  
  
-   [<span data-ttu-id="8f6dc-123">BizTalk Server 安全性功能</span><span class="sxs-lookup"><span data-stu-id="8f6dc-123">BizTalk Server Security Features</span></span>](../../adapters-and-accelerators/accelerator-swift/biztalk-server-security-features.md)  
  
-   [<span data-ttu-id="8f6dc-124">訊息修復和新送出 A4SWIFT 安全性功能</span><span class="sxs-lookup"><span data-stu-id="8f6dc-124">A4SWIFT Security Features for Message Repair and New Submission</span></span>](../../adapters-and-accelerators/accelerator-swift/a4swift-security-features-for-message-repair-and-new-submission.md)  
  
-   [<span data-ttu-id="8f6dc-125">InfoPath 安全性</span><span class="sxs-lookup"><span data-stu-id="8f6dc-125">InfoPath Security</span></span>](../../adapters-and-accelerators/accelerator-swift/infopath-security.md)  
  
-   [<span data-ttu-id="8f6dc-126">伺服器執行階段安全性</span><span class="sxs-lookup"><span data-stu-id="8f6dc-126">Server Runtime Security</span></span>](../../adapters-and-accelerators/accelerator-swift/server-runtime-security.md)  
  
-   [<span data-ttu-id="8f6dc-127">Windows SharePoint Services 安全性</span><span class="sxs-lookup"><span data-stu-id="8f6dc-127">Windows SharePoint Services Security</span></span>](../../adapters-and-accelerators/accelerator-swift/windows-sharepoint-services-security.md)  
  
-   [<span data-ttu-id="8f6dc-128">A4SWIFT Web 服務安全性</span><span class="sxs-lookup"><span data-stu-id="8f6dc-128">A4SWIFT Web Service Security</span></span>](../../adapters-and-accelerators/accelerator-swift/a4swift-web-service-security.md)  
  
-   [<span data-ttu-id="8f6dc-129">安全性摘要</span><span class="sxs-lookup"><span data-stu-id="8f6dc-129">Security Summary</span></span>](../../adapters-and-accelerators/accelerator-swift/security-summary.md)