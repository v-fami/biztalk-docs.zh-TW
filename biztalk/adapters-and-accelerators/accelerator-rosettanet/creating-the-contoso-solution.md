---
title: "建立 Contoso 解決方案 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: private process tutorial, creating solutions
ms.assetid: 02f5326a-68bd-418a-af81-684a73056e2c
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e09928a724d99822d652b12daa959a7f7f380bc4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-contoso-solution"></a><span data-ttu-id="e94e0-102">建立 Contoso 解決方案</span><span class="sxs-lookup"><span data-stu-id="e94e0-102">Creating the Contoso Solution</span></span>
<span data-ttu-id="e94e0-103">本節描述您應該在 Contoso 組織中遵循的步驟。</span><span class="sxs-lookup"><span data-stu-id="e94e0-103">This section details the steps that you have to follow for the Contoso organization.</span></span> <span data-ttu-id="e94e0-104">第一個步驟是使用 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 管理主控台，為兩個組織新增連絡人資訊和夥伴協議。</span><span class="sxs-lookup"><span data-stu-id="e94e0-104">The first step is to add the contact information and partner agreements for the two organizations using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.</span></span> <span data-ttu-id="e94e0-105">然後，建立商務營運系統 (LOB) 結構描述，並在那些結構描述及其各自的 RosettaNet 架構交易夥伴介面程序 (PIP) 結構描述之間建構對應。</span><span class="sxs-lookup"><span data-stu-id="e94e0-105">You then create line-of-business (LOB) schemas, and construct a mapping between those schemas and their respective RosettaNet-based Partner Interface Process (PIP) schemas.</span></span> <span data-ttu-id="e94e0-106">接著，使用 SQL 配接器設定連接埠資訊，以便與 ERP 系統進行通訊，並使用 HTTP 配接器將資訊傳送至 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="e94e0-106">Next, you configure port information using the SQL adapter for communicating with the ERP system, and the HTTP adapter for sending information to Fabrikam.</span></span> <span data-ttu-id="e94e0-107">最後一個步驟是自訂私用程序協調流程，以便在 [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 中使用「商務規則引擎」(BRE)。</span><span class="sxs-lookup"><span data-stu-id="e94e0-107">The last step is to customize the private process orchestration to use the Business Rule Engine (BRE) in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e94e0-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="e94e0-108">In This Section</span></span>  
  
-   [<span data-ttu-id="e94e0-109">建立組織及交易夥伴協議 contoso</span><span class="sxs-lookup"><span data-stu-id="e94e0-109">Creating Organizations and Trading Partner Agreement for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-organizations-and-trading-partner-agreement-for-contoso.md)  
  
-   [<span data-ttu-id="e94e0-110">建立 Contoso LOB 結構描述與對應</span><span class="sxs-lookup"><span data-stu-id="e94e0-110">Creating the Contoso LOB Schemas and Maps</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-lob-schemas-and-maps.md)  
  
-   [<span data-ttu-id="e94e0-111">建立和設定 BizTalk 連接埠 contoso</span><span class="sxs-lookup"><span data-stu-id="e94e0-111">Creating and Configuring BizTalk Ports for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-biztalk-ports-for-contoso.md)  
  
-   [<span data-ttu-id="e94e0-112">建立與修改 Contoso 私用程序</span><span class="sxs-lookup"><span data-stu-id="e94e0-112">Creating and Modifying the Private Process for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-modifying-the-private-process-for-contoso.md)