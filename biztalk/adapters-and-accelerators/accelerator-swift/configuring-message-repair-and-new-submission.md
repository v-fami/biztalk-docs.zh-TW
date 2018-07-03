---
title: 設定 Message Repair 和 New Submission |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Message Repair and New Submission, configuring
- A4SWIFT, Message Repair and New Submission
- configuring, Message Repair and New Submission
ms.assetid: e3e5e865-109c-469e-8b5b-c2675583d5a5
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0544adb9fc2ffa60bfc3b69ebee1937e5eb7a18a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36995791"
---
# <a name="configuring-message-repair-and-new-submission"></a><span data-ttu-id="59505-102">設定 Message Repair 和 New Submission</span><span class="sxs-lookup"><span data-stu-id="59505-102">Configuring Message Repair and New Submission</span></span>
<span data-ttu-id="59505-103">您必須執行的步驟來設定 Microsoft Message Repair 和 New Submission 功能以下幾節[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="59505-103">You must perform the steps in the following sections to configure the Message Repair and New Submission feature of Microsoft [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)], as shown in the following figure.</span></span>  
  
 <span data-ttu-id="59505-104">![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-message-repair-configuration.gif "A4SWIFT_Message_Repair_Configuration")</span><span class="sxs-lookup"><span data-stu-id="59505-104">![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-message-repair-configuration.gif "A4SWIFT_Message_Repair_Configuration")</span></span>  
  
 <span data-ttu-id="59505-105">在 [A4SWIFT 安裝精靈] 中，您可以選擇安裝 Message Repair 和 New Submission、 FIN 回應對帳 (FRR) 或 Message Repair 和 New Submission 沒有 FRR 或不含 Message Repair 和 New Submission 的 FRR。</span><span class="sxs-lookup"><span data-stu-id="59505-105">In the A4SWIFT Installation Wizard, you can choose to install Message Repair and New Submission and FIN Response Reconciliation (FRR), or Message Repair and New Submission without FRR, or FRR without Message Repair and New Submission.</span></span> <span data-ttu-id="59505-106">如此一來，這一節的指示請勿假設您已安裝且設定 FRR。</span><span class="sxs-lookup"><span data-stu-id="59505-106">As a result, the instructions in this section do not assume that you are installing and configuring FRR.</span></span> <span data-ttu-id="59505-107">它們執行動作，不過，假設您已執行中的步驟[A4SWIFT 元件組態指南](../../adapters-and-accelerators/accelerator-swift/a4swift-component-configuration-guide.md)一節。</span><span class="sxs-lookup"><span data-stu-id="59505-107">They do, however, assume that you have performed the steps in the [A4SWIFT Component Configuration Guide](../../adapters-and-accelerators/accelerator-swift/a4swift-component-configuration-guide.md) section.</span></span>  
  
 <span data-ttu-id="59505-108">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="59505-108">This section contains:</span></span>  
  
-   [<span data-ttu-id="59505-109">安裝憑證</span><span class="sxs-lookup"><span data-stu-id="59505-109">Installing Certificates</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-certificates.md)  
  
-   [<span data-ttu-id="59505-110">設定 A4SWIFT 屬性</span><span class="sxs-lookup"><span data-stu-id="59505-110">Setting A4SWIFT Properties</span></span>](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md)  
  
-   [<span data-ttu-id="59505-111">新增 A4SWIFT 使用者和更新 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="59505-111">Adding A4SWIFT Users and Updating Windows Groups</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-a4swift-users-and-updating-windows-groups.md)  
  
-   [<span data-ttu-id="59505-112">新增角色和部門</span><span class="sxs-lookup"><span data-stu-id="59505-112">Adding Roles and Departments</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-roles-and-departments.md)  
  
-   [<span data-ttu-id="59505-113">部署 A4SWIFT 信封結構描述</span><span class="sxs-lookup"><span data-stu-id="59505-113">Deploying A4SWIFT Envelope Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-envelope-schemas.md)  
  
-   [<span data-ttu-id="59505-114">發佈 InfoPath 表單範本</span><span class="sxs-lookup"><span data-stu-id="59505-114">Publishing InfoPath Form Templates</span></span>](http://msdn.microsoft.com/2947e1ad-8c44-4cdb-bbde-7683e186b41b)