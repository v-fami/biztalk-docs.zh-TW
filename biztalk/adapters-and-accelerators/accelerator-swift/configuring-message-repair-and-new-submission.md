---
title: "設定 Message Repair 和 New Submission |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Message Repair and New Submission, configuring
- A4SWIFT, Message Repair and New Submission
- configuring, Message Repair and New Submission
ms.assetid: e3e5e865-109c-469e-8b5b-c2675583d5a5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 00e42bcfc5e744aa005e2e0a790dfc505b7a834d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-message-repair-and-new-submission"></a><span data-ttu-id="8b876-102">設定訊息修復和新送出</span><span class="sxs-lookup"><span data-stu-id="8b876-102">Configuring Message Repair and New Submission</span></span>
<span data-ttu-id="8b876-103">您必須執行的步驟，在以下章節來設定的 Message Repair 和 New Submission 功能[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)]，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="8b876-103">You must perform the steps in the following sections to configure the Message Repair and New Submission feature of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)], as shown in the following figure.</span></span>  
  
 ![](../../adapters-and-accelerators/accelerator-swift/media/a4swift-message-repair-configuration.gif "A4SWIFT_Message_Repair_Configuration")  
  
 <span data-ttu-id="8b876-104">在 [A4SWIFT 安裝精靈] 中，您可以選擇安裝 Message Repair 和 New Submission 和 FIN 回應對帳 (FRR) 或訊息修復和新送出，而不需 FRR 或不含 Message Repair 和 New Submission FRR。</span><span class="sxs-lookup"><span data-stu-id="8b876-104">In the A4SWIFT Installation Wizard, you can choose to install Message Repair and New Submission and FIN Response Reconciliation (FRR), or Message Repair and New Submission without FRR, or FRR without Message Repair and New Submission.</span></span> <span data-ttu-id="8b876-105">如此一來，本節中的指示請勿假設您安裝與設定 FRR。</span><span class="sxs-lookup"><span data-stu-id="8b876-105">As a result, the instructions in this section do not assume that you are installing and configuring FRR.</span></span> <span data-ttu-id="8b876-106">它們執行動作，不過，假設您已經執行中的步驟[A4SWIFT 元件組態指南](../../adapters-and-accelerators/accelerator-swift/a4swift-component-configuration-guide.md)> 一節。</span><span class="sxs-lookup"><span data-stu-id="8b876-106">They do, however, assume that you have performed the steps in the [A4SWIFT Component Configuration Guide](../../adapters-and-accelerators/accelerator-swift/a4swift-component-configuration-guide.md) section.</span></span>  
  
 <span data-ttu-id="8b876-107">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="8b876-107">This section contains:</span></span>  
  
-   [<span data-ttu-id="8b876-108">安裝憑證</span><span class="sxs-lookup"><span data-stu-id="8b876-108">Installing Certificates</span></span>](../../adapters-and-accelerators/accelerator-swift/installing-certificates.md)  
  
-   [<span data-ttu-id="8b876-109">設定 A4SWIFT 屬性</span><span class="sxs-lookup"><span data-stu-id="8b876-109">Setting A4SWIFT Properties</span></span>](../../adapters-and-accelerators/accelerator-swift/setting-a4swift-properties.md)  
  
-   [<span data-ttu-id="8b876-110">新增 A4SWIFT 使用者及更新 Windows 群組</span><span class="sxs-lookup"><span data-stu-id="8b876-110">Adding A4SWIFT Users and Updating Windows Groups</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-a4swift-users-and-updating-windows-groups.md)  
  
-   [<span data-ttu-id="8b876-111">新增角色與部門</span><span class="sxs-lookup"><span data-stu-id="8b876-111">Adding Roles and Departments</span></span>](../../adapters-and-accelerators/accelerator-swift/adding-roles-and-departments.md)  
  
-   [<span data-ttu-id="8b876-112">部署 A4SWIFT 信封結構描述</span><span class="sxs-lookup"><span data-stu-id="8b876-112">Deploying A4SWIFT Envelope Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/deploying-a4swift-envelope-schemas.md)  
  
-   [<span data-ttu-id="8b876-113">發佈 InfoPath 表單範本</span><span class="sxs-lookup"><span data-stu-id="8b876-113">Publishing InfoPath Form Templates</span></span>](http://msdn.microsoft.com/en-us/2947e1ad-8c44-4cdb-bbde-7683e186b41b)