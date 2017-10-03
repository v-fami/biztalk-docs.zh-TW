---
title: "Microsoft BizTalk Accelerator for SWIFT 的文件 |Microsoft 文件"
description: "若要安裝、 設定、 部署、 開始、 安全、 開發、 快速連結和疑難排解 BizTalk Server 中的此 SWIFT 加速器"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a742cd84-a159-461b-a410-6e75a45e7d8b
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 843c20229371e213a1409f3bf3c6d297bf16211a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="microsoft-biztalk-accelerator-for-swift-documentation"></a><span data-ttu-id="42dba-103">Microsoft BizTalk Accelerator for SWIFT 的文件</span><span class="sxs-lookup"><span data-stu-id="42dba-103">Microsoft BizTalk Accelerator for SWIFT documentation</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="42dba-104">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]是增益集來[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]，並利用開放式標準為基礎的工具和執行階段功能[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]實作協會全球 Interbank 財務 Telecommunication (SWIFT) 訊息支援格式。</span><span class="sxs-lookup"><span data-stu-id="42dba-104"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] is an add-in to [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)], and leverages the open standards-based tools and run-time facilities of [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] to implement support for Society for Worldwide Interbank Financial Telecommunication (SWIFT) message formats.</span></span>  
  
 <span data-ttu-id="42dba-105">這會加入功能簡化了企業採用[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]做為一般用途的中介軟體整合平台。</span><span class="sxs-lookup"><span data-stu-id="42dba-105">This added functionality makes it easier for businesses to adopt [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] as a general-purpose middleware integration platform.</span></span> <span data-ttu-id="42dba-106">使用 A4SWIFT、 客戶、 合作夥伴和系統整合者可以簡化開發、 部署和支援的整合方案的核心涵蓋了金融服務應用程式基礎結構和商務程序。</span><span class="sxs-lookup"><span data-stu-id="42dba-106">With A4SWIFT, customers, partners, and system integrators can streamline the development, deployment, and support of integration solutions for core financial services application infrastructure and business processes.</span></span>  

## <a name="install-configure-and-deploy"></a><span data-ttu-id="42dba-107">安裝、 設定和部署</span><span class="sxs-lookup"><span data-stu-id="42dba-107">Install, configure, and deploy</span></span>
<span data-ttu-id="42dba-108">[安裝、 設定及部署](../../adapters-and-accelerators/accelerator-swift/install-configure-and-deploy-the-biztalk-accelerator-for-swift.md)示範如何安裝和設定 BizTalk Server 上 acclerator。</span><span class="sxs-lookup"><span data-stu-id="42dba-108">[Install, configure, and deploy](../../adapters-and-accelerators/accelerator-swift/install-configure-and-deploy-the-biztalk-accelerator-for-swift.md) shows you how to install and configure the acclerator on your BizTalk Server.</span></span> <span data-ttu-id="42dba-109">您也可以設定執行階段、 訊息修復和 FIN 回應。</span><span class="sxs-lookup"><span data-stu-id="42dba-109">You can also configure the runtime, message repair, and FIN response.</span></span> 

<span data-ttu-id="42dba-110">使用本章節也設定網路組態，並部署您的伺服器。</span><span class="sxs-lookup"><span data-stu-id="42dba-110">Use this section to also set up a network configuration, and deploy your servers.</span></span> 

## <a name="get-started"></a><span data-ttu-id="42dba-111">快速入門</span><span class="sxs-lookup"><span data-stu-id="42dba-111">Get started</span></span>
<span data-ttu-id="42dba-112">[使用者入門](../../adapters-and-accelerators/accelerator-swift/getting-started-with-biztalk-accelerator-for-swift.md)包含一些端對端教學課程。</span><span class="sxs-lookup"><span data-stu-id="42dba-112">[Getting started](../../adapters-and-accelerators/accelerator-swift/getting-started-with-biztalk-accelerator-for-swift.md) includes some end-to-end tutorials.</span></span>  

## <a name="messaging"></a><span data-ttu-id="42dba-113">Messaging (傳訊)</span><span class="sxs-lookup"><span data-stu-id="42dba-113">Messaging</span></span>  
<span data-ttu-id="42dba-114">[執行階段中，訊息修復、 FIN 回應和傳訊](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md)描述資料如何流過 SWIFT 組合器和解譯器、 說明訊息修復、 說明不同的成品會如何處理訊息等等。</span><span class="sxs-lookup"><span data-stu-id="42dba-114">[Runtime, message repair, FIN response, and messaging](../../adapters-and-accelerators/accelerator-swift/runtime-message-repair-fin-response-and-messaging.md) describes how data flows through the SWIFT assembler and disassembler, explains message repair, explains how the different artifacts handle messages, and more.</span></span> 

## <a name="security"></a><span data-ttu-id="42dba-115">安全性</span><span class="sxs-lookup"><span data-stu-id="42dba-115">Security</span></span>  
<span data-ttu-id="42dba-116">[安全性與隱私權的標準](../../adapters-and-accelerators/accelerator-swift/security-and-privacy-standards.md)提供更多詳細資料，在 BizTalk Server 中，是由執行階段和 SWIFT 的安全性使用者和群組。</span><span class="sxs-lookup"><span data-stu-id="42dba-116">[Security and privacy standards](../../adapters-and-accelerators/accelerator-swift/security-and-privacy-standards.md) provides more details on security in BizTalk Server, the runtime, and the SWIFT users and groups.</span></span> 

## <a name="developing-apps"></a><span data-ttu-id="42dba-117">開發應用程式</span><span class="sxs-lookup"><span data-stu-id="42dba-117">Developing apps</span></span>  
<span data-ttu-id="42dba-118">[程式設計人員指南](../../adapters-and-accelerators/accelerator-swift/programmers-guide-frr-nak-sample-and-tools.md)包含 FRR NAK 處理常式範例，以及工具。</span><span class="sxs-lookup"><span data-stu-id="42dba-118">[Programmers guide](../../adapters-and-accelerators/accelerator-swift/programmers-guide-frr-nak-sample-and-tools.md) includes FRR NAK handler sample, and tools.</span></span>

## <a name="operations"></a><span data-ttu-id="42dba-119">作業</span><span class="sxs-lookup"><span data-stu-id="42dba-119">Operations</span></span>  
<span data-ttu-id="42dba-120">[操作工作](../../adapters-and-accelerators/accelerator-swift/operational-tasks.md)討論訊息修復，正在驗證及核准訊息，並提供有關使用 商務規則引擎 (BRE)，以及其他更多的資訊。</span><span class="sxs-lookup"><span data-stu-id="42dba-120">[Operational tasks](../../adapters-and-accelerators/accelerator-swift/operational-tasks.md) discusses message repair, verifying and approving messages, and provides info on using Business Rules Engine (BRE), and more.</span></span> 

## <a name="troubleshoot"></a><span data-ttu-id="42dba-121">疑難排解</span><span class="sxs-lookup"><span data-stu-id="42dba-121">Troubleshoot</span></span>  
<span data-ttu-id="42dba-122">[疑難排解](../../adapters-and-accelerators/accelerator-swift/troubleshooting-and-known-issues.md)列出此快速鍵，以不同的組件的一些指引，也會列出一些已知的問題。</span><span class="sxs-lookup"><span data-stu-id="42dba-122">[Troubleshooting](../../adapters-and-accelerators/accelerator-swift/troubleshooting-and-known-issues.md) lists some guidance on the different parts to this accelerator, and also lists some known issues.</span></span>
