---
title: 建立 Contoso 解決方案 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- private process tutorial, creating solutions
ms.assetid: 02f5326a-68bd-418a-af81-684a73056e2c
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a2ed65010926f04e99eb126980870368c5d4a512
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000127"
---
# <a name="creating-the-contoso-solution"></a><span data-ttu-id="2ec43-102">建立 Contoso 解決方案</span><span class="sxs-lookup"><span data-stu-id="2ec43-102">Creating the Contoso Solution</span></span>
<span data-ttu-id="2ec43-103">本節描述您應該在 Contoso 組織中遵循的步驟。</span><span class="sxs-lookup"><span data-stu-id="2ec43-103">This section details the steps that you have to follow for the Contoso organization.</span></span> <span data-ttu-id="2ec43-104">第一個步驟是新增連絡人的資訊和夥伴協議，為兩個組織使用 Microsoft®[!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="2ec43-104">The first step is to add the contact information and partner agreements for the two organizations using the Microsoft® [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.</span></span> <span data-ttu-id="2ec43-105">然後，建立商務營運系統 (LOB) 結構描述，並在那些結構描述及其各自的 RosettaNet 架構交易夥伴介面程序 (PIP) 結構描述之間建構對應。</span><span class="sxs-lookup"><span data-stu-id="2ec43-105">You then create line-of-business (LOB) schemas, and construct a mapping between those schemas and their respective RosettaNet-based Partner Interface Process (PIP) schemas.</span></span> <span data-ttu-id="2ec43-106">接著，使用 SQL 配接器設定連接埠資訊，以便與 ERP 系統進行通訊，並使用 HTTP 配接器將資訊傳送至 Fabrikam。</span><span class="sxs-lookup"><span data-stu-id="2ec43-106">Next, you configure port information using the SQL adapter for communicating with the ERP system, and the HTTP adapter for sending information to Fabrikam.</span></span> <span data-ttu-id="2ec43-107">最後一個步驟是自訂私用程序協調流程，以使用 BizTalk Server 中的 商務規則引擎 (BRE)。</span><span class="sxs-lookup"><span data-stu-id="2ec43-107">The last step is to customize the private process orchestration to use the Business Rule Engine (BRE) in BizTalk Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ec43-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="2ec43-108">In This Section</span></span>  
  
-   [<span data-ttu-id="2ec43-109">為 Contoso 建立組織及交易夥伴協議</span><span class="sxs-lookup"><span data-stu-id="2ec43-109">Creating Organizations and Trading Partner Agreement for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-organizations-and-trading-partner-agreement-for-contoso.md)  
  
-   [<span data-ttu-id="2ec43-110">建立 Contoso LOB 結構描述與對應</span><span class="sxs-lookup"><span data-stu-id="2ec43-110">Creating the Contoso LOB Schemas and Maps</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-the-contoso-lob-schemas-and-maps.md)  
  
-   [<span data-ttu-id="2ec43-111">建立與設定 BizTalk 連接埠以供 Contoso 使用</span><span class="sxs-lookup"><span data-stu-id="2ec43-111">Creating and Configuring BizTalk Ports for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-biztalk-ports-for-contoso.md)  
  
-   [<span data-ttu-id="2ec43-112">建立與修改 Contoso 私用程序</span><span class="sxs-lookup"><span data-stu-id="2ec43-112">Creating and Modifying the Private Process for Contoso</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-modifying-the-private-process-for-contoso.md)