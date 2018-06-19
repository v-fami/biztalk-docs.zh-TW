---
title: 管理 BTARN 組態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Accelerator for RosettaNet, administering
- administering
ms.assetid: 8db2851e-6aaf-49d9-a3f0-dee187595c01
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48df2985716fe4ab1d94ba695dba5f4e108dc42b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22206766"
---
# <a name="administering-the-btarn-configuration"></a><span data-ttu-id="46251-102">管理 BTARN 組態</span><span class="sxs-lookup"><span data-stu-id="46251-102">Administering the BTARN Configuration</span></span>
<span data-ttu-id="46251-103">[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] 管理主控台可讓您從一個使用者介面管理 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組態的所有層面。</span><span class="sxs-lookup"><span data-stu-id="46251-103">The [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Management Console lets you administer all facets of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration from one user interface.</span></span> <span data-ttu-id="46251-104">[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 組態包括程序組態、主要組織、交易夥伴與交易夥伴協議。</span><span class="sxs-lookup"><span data-stu-id="46251-104">The [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] configuration includes process configurations, home organizations, partners, and trading partner agreements.</span></span> <span data-ttu-id="46251-105">從[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管理主控台中，您可以管理憑證、 管理執行個體[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]™、 檢視事件，並檢視效能記錄檔及警示。</span><span class="sxs-lookup"><span data-stu-id="46251-105">From the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console, you can also manage certificates, administer instances of [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]™, view events, and view performance logs and alerts.</span></span>  
  
 <span data-ttu-id="46251-106">如需您可以從執行的所有作業的概觀[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管理主控台中，請參閱[使用 BTARN 管理主控台](../../adapters-and-accelerators/accelerator-rosettanet/using-the-btarn-management-console.md)。</span><span class="sxs-lookup"><span data-stu-id="46251-106">For an overview of all operations that you can perform from the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console, see [Using the BTARN Management Console](../../adapters-and-accelerators/accelerator-rosettanet/using-the-btarn-management-console.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46251-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="46251-107">In This Section</span></span>  
  
-   [<span data-ttu-id="46251-108">使用 BTARN 管理主控台</span><span class="sxs-lookup"><span data-stu-id="46251-108">Using the BTARN Management Console</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/using-the-btarn-management-console.md)  
  
-   [<span data-ttu-id="46251-109">設定 BTARN 傳送和接收管線</span><span class="sxs-lookup"><span data-stu-id="46251-109">Setting BTARN Send and Receive Pipelines</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/setting-btarn-send-and-receive-pipelines.md)  
  
-   [<span data-ttu-id="46251-110">啟用 BAM 追蹤</span><span class="sxs-lookup"><span data-stu-id="46251-110">Enabling BAM Tracking</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/enabling-bam-tracking.md)  
  
-   [<span data-ttu-id="46251-111">建立或編輯程序組態</span><span class="sxs-lookup"><span data-stu-id="46251-111">Creating or Editing a Process Configuration</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-process-configuration.md)  
  
-   [<span data-ttu-id="46251-112">建立或編輯主要組織</span><span class="sxs-lookup"><span data-stu-id="46251-112">Creating or Editing a Home Organization</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-home-organization.md)  
  
-   [<span data-ttu-id="46251-113">建立或編輯夥伴</span><span class="sxs-lookup"><span data-stu-id="46251-113">Creating or Editing a Partner</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-a-partner.md)  
  
-   [<span data-ttu-id="46251-114">建立或編輯協議</span><span class="sxs-lookup"><span data-stu-id="46251-114">Creating or Editing an Agreement</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-or-editing-an-agreement.md)