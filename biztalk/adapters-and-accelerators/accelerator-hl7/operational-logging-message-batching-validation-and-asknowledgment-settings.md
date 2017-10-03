---
title: "作業記錄、 訊息批次、 驗證和 asknowledgment 設定 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- BTAHL7, administering
- managing
- BTAHL7, managing
- administering
ms.assetid: c7376de4-4e1d-47e2-acf7-0a32e7a4b073
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b3282d69fc572c4aa32888f9a3ed8a806deef5c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="operational-logging-message-batching-validation-and-asknowledgment-settings"></a><span data-ttu-id="89c7a-102">作業記錄、 訊息批次、 驗證和 asknowledgment 設定</span><span class="sxs-lookup"><span data-stu-id="89c7a-102">Operational logging, message batching, validation and asknowledgment settings</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="89c7a-103">[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]包含伺服器和一系列的工具為企業應用程式整合 (EAI)，自動化商務程序，並加速商業夥伴之間的互動。</span><span class="sxs-lookup"><span data-stu-id="89c7a-103"> [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] encompasses a server and series of tools for enterprise application integration (EAI), automating business processes, and facilitating interactions with business partners.</span></span> <span data-ttu-id="89c7a-104">根據[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]平台，BTAHL7 會升級任何使用 HL7 標準的設備的醫療應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="89c7a-104">Built on the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] platform, BTAHL7 promotes medical application integration for any facility using the HL7 standard.</span></span> <span data-ttu-id="89c7a-105">HL7 包含標準交換、 整合和擷取電子門診活動及管理中的資訊。</span><span class="sxs-lookup"><span data-stu-id="89c7a-105">HL7 contains standards for exchanging, integrating, and retrieving electronic information in clinical practice and management.</span></span>  
  
 <span data-ttu-id="89c7a-106">分析師-使用者介面設定交易夥伴、 訊息通知、 訊息批次處理，及您的商務程序需要的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="89c7a-106">Interface user analysts configure trading partners, message acknowledgments, message batching, and other details that your business process requires.</span></span>  
  
 <span data-ttu-id="89c7a-107">本章節提供可讓您有效地監視和維護 BTAHL7 應用程式環境的概念和程序資訊。</span><span class="sxs-lookup"><span data-stu-id="89c7a-107">This section provides conceptual and procedural information that enables you to effectively monitor and maintain your BTAHL7 application environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89c7a-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="89c7a-108">In This Section</span></span>  
  
-   [<span data-ttu-id="89c7a-109">記錄設定</span><span class="sxs-lookup"><span data-stu-id="89c7a-109">Logging Configuration</span></span>](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)  
  
-   [<span data-ttu-id="89c7a-110">訊息批次</span><span class="sxs-lookup"><span data-stu-id="89c7a-110">Message Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)  
  
-   [<span data-ttu-id="89c7a-111">驗證設定</span><span class="sxs-lookup"><span data-stu-id="89c7a-111">Validation Settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/validation-settings.md)  
  
-   [<span data-ttu-id="89c7a-112">MSH 欄位覆寫</span><span class="sxs-lookup"><span data-stu-id="89c7a-112">MSH Field Overrides</span></span>](../../adapters-and-accelerators/accelerator-hl7/msh-field-overrides.md)  
  
-   [<span data-ttu-id="89c7a-113">通知設定</span><span class="sxs-lookup"><span data-stu-id="89c7a-113">Acknowledgment Settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md)  
  
-   [<span data-ttu-id="89c7a-114">擴充編碼支援</span><span class="sxs-lookup"><span data-stu-id="89c7a-114">Extended Encoding Support</span></span>](../../adapters-and-accelerators/accelerator-hl7/extended-encoding-support.md)