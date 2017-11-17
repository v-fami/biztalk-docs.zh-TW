---
title: "建立 Contoso LOB 結構描述與對應 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, LOB
- LOBs, schemas
- private process tutorial, creating LOB schemas
- private process tutorial, creating maps
- maps
ms.assetid: fda8852a-51d8-4987-a187-834883a06d9b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f204efd00858f3f4204848f4fb4a0dcef5233b3c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="creating-the-contoso-lob-schemas-and-maps"></a><span data-ttu-id="12a6b-102">建立 Contoso LOB 結構描述與對應</span><span class="sxs-lookup"><span data-stu-id="12a6b-102">Creating the Contoso LOB Schemas and Maps</span></span>
<span data-ttu-id="12a6b-103">在本節中，您將建立 Contoso 組織用於 ERP 系統的商務營運系統 (LOB) 結構描述。</span><span class="sxs-lookup"><span data-stu-id="12a6b-103">In this section, you create the line-of-business (LOB) schemas that the Contoso organization uses in their ERP system.</span></span> <span data-ttu-id="12a6b-104">您使用「[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] 對應工具」建立內部 Contoso 訊息與輸入和輸出 RosettaNet 訊息類型之間的轉換。</span><span class="sxs-lookup"><span data-stu-id="12a6b-104">You use the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Mapper tool to create data transformations between the internal Contoso messages and the inbound and outbound RosettaNet message types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="12a6b-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="12a6b-105">In This Section</span></span>  
  
-   [<span data-ttu-id="12a6b-106">步驟 1： 為 Contoso 價格與可用性要求建立新的 BizTalk 解決方案</span><span class="sxs-lookup"><span data-stu-id="12a6b-106">Step 1: Creating a New BizTalk Solution for the Contoso Price and Availability Request</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-create-new-biztalk-solution-for-contoso-price-and-availability-request.md)  
  
-   <span data-ttu-id="12a6b-107">[步驟 2： 建立 Contoso LOB 應用程式的結構描述的價格與可用性專案中使用 [BizTalk 編輯器]](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-contoso-lob-application-schema-for-price-and-availability.md)</span><span class="sxs-lookup"><span data-stu-id="12a6b-107">[Step 2: Creating the Contoso LOB Application Schemas for the Price and Availability Project Using BizTalk Editor](../../adapters-and-accelerators/accelerator-rosettanet/step-2-create-contoso-lob-application-schema-for-price-and-availability.md)</span></span>  
  
-   [<span data-ttu-id="12a6b-108">步驟 3： 建立 Contoso LOB 應用程式對應的價格與可用性專案使用 BizTalk 對應工具</span><span class="sxs-lookup"><span data-stu-id="12a6b-108">Step 3: Creating the Contoso LOB Application Maps for the Price and Availability Project Using BizTalk Mapper</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-create-contoso-lob-application-map-for-price-and-availability-in-mapper.md)