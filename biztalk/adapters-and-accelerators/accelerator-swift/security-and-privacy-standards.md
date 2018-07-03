---
title: 安全性和隱私權標準 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security, privacy standards
- privacy standards
- security
- security, about security
- BizTalk Accelerator for SWIFT, security
- security, BizTalk Accelerator for SWIFT
ms.assetid: 5794b25f-8a73-4f5b-97ef-1b0f61775c4b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 61daf6e28b03174af2b32a61c758a39b4cd16ff9
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980599"
---
# <a name="security-and-privacy-standards"></a><span data-ttu-id="31f05-102">安全性和隱私權標準</span><span class="sxs-lookup"><span data-stu-id="31f05-102">Security and privacy standards</span></span>
<span data-ttu-id="31f05-103">使用 Microsoft 財務服務應用程式和整合方案開發[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]通常會受到原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安全性功能。</span><span class="sxs-lookup"><span data-stu-id="31f05-103">Financial Services applications and integration solutions developed using Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] are generally secured by native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security features.</span></span> [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="31f05-104"> 使用主動的安全性機制，例如現行的網際網路加密訊息的標準和傳輸通訊協定，簽署憑證時，[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]驗證和企業單一登入來保護[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]應用程式、 資料和執行階段。</span><span class="sxs-lookup"><span data-stu-id="31f05-104"> uses aggressive security mechanisms such as de facto Internet encrypted messaging standards and transport protocols, signing certificates, [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Authentication, and Enterprise Single Sign-On to secure [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] applications, data, and runtime.</span></span>  

 <span data-ttu-id="31f05-105">建置與 Microsoft 的解決方案[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]2000年[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]，A4SWIFT 可以幫助您符合 Society 全球 Interbank 財務電信 (SWIFT) 的財務交易的安全性和隱私權的指導方針。</span><span class="sxs-lookup"><span data-stu-id="31f05-105">Solutions built with Microsoft [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] 2000, [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], and A4SWIFT can help you to meet the security and privacy guidelines for Society for Worldwide Interbank Financial Telecommunication (SWIFT) financial transactions.</span></span>  

 <span data-ttu-id="31f05-106">除了原生[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]安全性功能，A4SWIFT 提供特定使用者訊息項目、 修復、 核准及提交 SWIFT 訊息所保護的使用者層級安全性。</span><span class="sxs-lookup"><span data-stu-id="31f05-106">In addition to native [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] security features, A4SWIFT provides user-level security specific to securing end-user message entry, repair, approval, and submission of SWIFT messages.</span></span> <span data-ttu-id="31f05-107">此安全性之後，即可使用[!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)]數位簽章技術並利用 A4SWIFT 執行階段服務來驗證憑證和資料的完整性。</span><span class="sxs-lookup"><span data-stu-id="31f05-107">This security is achieved by using [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] digital signing technologies and by using A4SWIFT runtime services to verify certificate and data integrity.</span></span>  

 <span data-ttu-id="31f05-108">請務必措施來保護您 SWIFT 的訊息與輸入或編輯使用者，在傳輸中和 while 時，所包含的資訊，請考慮[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]處理，並將其儲存。</span><span class="sxs-lookup"><span data-stu-id="31f05-108">It is important to consider measures for securing your SWIFT messages and the information they contain when they are entered or edited by end-users, in transit, and while [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] processes and stores them.</span></span>  

 <span data-ttu-id="31f05-109">在一起，BizTalk Server 和 A4SWIFT 提供平台、 基礎結構與工具來設計、 開發以及執行安全通訊的 SWIFT 和工作流程自動化系統。</span><span class="sxs-lookup"><span data-stu-id="31f05-109">Together, BizTalk Server and A4SWIFT provide the platform, infrastructure, and tools for designing, developing, and executing secure SWIFT messaging and workflow automation systems.</span></span>  

 <span data-ttu-id="31f05-110">當實作安全性，您必須設計和開發許多區域。</span><span class="sxs-lookup"><span data-stu-id="31f05-110">When implementing security, you must design and develop many areas.</span></span> <span data-ttu-id="31f05-111">下列清單是這些區域的高層級檢視：</span><span class="sxs-lookup"><span data-stu-id="31f05-111">The following list is a high-level view of these areas:</span></span>  

- <span data-ttu-id="31f05-112">開發 IT 安全性原則</span><span class="sxs-lookup"><span data-stu-id="31f05-112">Develop an IT security policy</span></span>  

- <span data-ttu-id="31f05-113">設計和實作的防禦策略</span><span class="sxs-lookup"><span data-stu-id="31f05-113">Design and implement a defense strategy</span></span>  

- <span data-ttu-id="31f05-114">設計和實作伺服器鎖定策略</span><span class="sxs-lookup"><span data-stu-id="31f05-114">Design and implement a server lockdown strategy</span></span>  

- <span data-ttu-id="31f05-115">設計和實作的防毒軟體的策略</span><span class="sxs-lookup"><span data-stu-id="31f05-115">Design and implement an antivirus strategy</span></span>  

- <span data-ttu-id="31f05-116">設計和實作備份和還原策略</span><span class="sxs-lookup"><span data-stu-id="31f05-116">Design and implement a backup and restore strategy</span></span>  

- <span data-ttu-id="31f05-117">設計和實作更新管理策略</span><span class="sxs-lookup"><span data-stu-id="31f05-117">Design and implement an update management strategy</span></span>  

- <span data-ttu-id="31f05-118">設計和實作稽核和入侵偵測策略</span><span class="sxs-lookup"><span data-stu-id="31f05-118">Design and implement an auditing and intrusion detection strategy</span></span>  

- <span data-ttu-id="31f05-119">設計事件回應計劃</span><span class="sxs-lookup"><span data-stu-id="31f05-119">Design an incident response plan</span></span>  

  <span data-ttu-id="31f05-120">本主題中所提供的資訊不會討論上述清單中的所有資訊或提供金融服務規範的解決方案。</span><span class="sxs-lookup"><span data-stu-id="31f05-120">The information provided in this topic does not cover all the information in the preceding list or deliver a financial services-compliant solution.</span></span> <span data-ttu-id="31f05-121">本主題的目的是方法的提供不錯的起點，並協助底線結構化且完善，對安全性的重要性。</span><span class="sxs-lookup"><span data-stu-id="31f05-121">The purpose of this topic is to provide a good starting point and to help underscore the importance of a structured and comprehensive approach to security.</span></span>  

  <span data-ttu-id="31f05-122">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="31f05-122">This section contains:</span></span>  

- [<span data-ttu-id="31f05-123">BizTalk Server 安全性功能</span><span class="sxs-lookup"><span data-stu-id="31f05-123">BizTalk Server Security Features</span></span>](../../adapters-and-accelerators/accelerator-swift/biztalk-server-security-features.md)  

- [<span data-ttu-id="31f05-124">A4SWIFT Message Repair 和 New Submission 的安全性功能</span><span class="sxs-lookup"><span data-stu-id="31f05-124">A4SWIFT Security Features for Message Repair and New Submission</span></span>](../../adapters-and-accelerators/accelerator-swift/a4swift-security-features-for-message-repair-and-new-submission.md)  

- [<span data-ttu-id="31f05-125">InfoPath 安全性</span><span class="sxs-lookup"><span data-stu-id="31f05-125">InfoPath Security</span></span>](../../adapters-and-accelerators/accelerator-swift/infopath-security.md)  

- [<span data-ttu-id="31f05-126">伺服器執行階段安全性</span><span class="sxs-lookup"><span data-stu-id="31f05-126">Server Runtime Security</span></span>](../../adapters-and-accelerators/accelerator-swift/server-runtime-security.md)  

- [<span data-ttu-id="31f05-127">Windows SharePoint Services 安全性</span><span class="sxs-lookup"><span data-stu-id="31f05-127">Windows SharePoint Services Security</span></span>](../../adapters-and-accelerators/accelerator-swift/windows-sharepoint-services-security.md)  

- [<span data-ttu-id="31f05-128">A4SWIFT Web 服務安全性</span><span class="sxs-lookup"><span data-stu-id="31f05-128">A4SWIFT Web Service Security</span></span>](../../adapters-and-accelerators/accelerator-swift/a4swift-web-service-security.md)  

- [<span data-ttu-id="31f05-129">安全性摘要</span><span class="sxs-lookup"><span data-stu-id="31f05-129">Security Summary</span></span>](../../adapters-and-accelerators/accelerator-swift/security-summary.md)
