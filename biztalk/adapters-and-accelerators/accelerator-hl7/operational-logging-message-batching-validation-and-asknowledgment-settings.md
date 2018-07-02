---
title: 作業記錄、 訊息批次處理、 驗證和通知設定 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BTAHL7, administering
- managing
- BTAHL7, managing
- administering
ms.assetid: c7376de4-4e1d-47e2-acf7-0a32e7a4b073
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 015182a6b091ccbba7452df4c44ed4e4f45c336e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974679"
---
# <a name="operational-logging-message-batching-validation-and-asknowledgment-settings"></a><span data-ttu-id="ffc54-102">作業記錄、 訊息批次處理、 驗證和通知設定</span><span class="sxs-lookup"><span data-stu-id="ffc54-102">Operational logging, message batching, validation and asknowledgment settings</span></span>
<span data-ttu-id="ffc54-103">Microsoft[!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)]包含伺服器和一系列的工具，適用於企業應用程式整合 (EAI)，自動化商務程序，並促進與商業夥伴之間的互動。</span><span class="sxs-lookup"><span data-stu-id="ffc54-103">Microsoft [!INCLUDE[btaBTAHL7NoNumber](../../includes/btabtahl7nonumber-md.md)] encompasses a server and series of tools for enterprise application integration (EAI), automating business processes, and facilitating interactions with business partners.</span></span> <span data-ttu-id="ffc54-104">建置於[!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]平台，BTAHL7 會升級任何使用 HL7 標準的設施的醫療應用程式整合。</span><span class="sxs-lookup"><span data-stu-id="ffc54-104">Built on the [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] platform, BTAHL7 promotes medical application integration for any facility using the HL7 standard.</span></span> <span data-ttu-id="ffc54-105">HL7 包含標準的交換、 整合，以及擷取電子臨床練習和管理的資訊。</span><span class="sxs-lookup"><span data-stu-id="ffc54-105">HL7 contains standards for exchanging, integrating, and retrieving electronic information in clinical practice and management.</span></span>  
  
 <span data-ttu-id="ffc54-106">分析師-使用者介面設定交易夥伴、 訊息通知、 訊息批次處理，及您的商務程序需要的其他詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ffc54-106">Interface user analysts configure trading partners, message acknowledgments, message batching, and other details that your business process requires.</span></span>  
  
 <span data-ttu-id="ffc54-107">本節提供概念和程序可讓您有效監控和維護 BTAHL7 應用程式環境的資訊。</span><span class="sxs-lookup"><span data-stu-id="ffc54-107">This section provides conceptual and procedural information that enables you to effectively monitor and maintain your BTAHL7 application environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ffc54-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="ffc54-108">In This Section</span></span>  
  
-   [<span data-ttu-id="ffc54-109">記錄設定</span><span class="sxs-lookup"><span data-stu-id="ffc54-109">Logging Configuration</span></span>](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)  
  
-   [<span data-ttu-id="ffc54-110">訊息批次處理</span><span class="sxs-lookup"><span data-stu-id="ffc54-110">Message Batching</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-batching.md)  
  
-   [<span data-ttu-id="ffc54-111">驗證設定</span><span class="sxs-lookup"><span data-stu-id="ffc54-111">Validation Settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/validation-settings.md)  
  
-   [<span data-ttu-id="ffc54-112">MSH 欄位覆寫</span><span class="sxs-lookup"><span data-stu-id="ffc54-112">MSH Field Overrides</span></span>](../../adapters-and-accelerators/accelerator-hl7/msh-field-overrides.md)  
  
-   [<span data-ttu-id="ffc54-113">通知設定</span><span class="sxs-lookup"><span data-stu-id="ffc54-113">Acknowledgment Settings</span></span>](../../adapters-and-accelerators/accelerator-hl7/acknowledgment-settings.md)  
  
-   [<span data-ttu-id="ffc54-114">支援擴充編碼</span><span class="sxs-lookup"><span data-stu-id="ffc54-114">Extended Encoding Support</span></span>](../../adapters-and-accelerators/accelerator-hl7/extended-encoding-support.md)