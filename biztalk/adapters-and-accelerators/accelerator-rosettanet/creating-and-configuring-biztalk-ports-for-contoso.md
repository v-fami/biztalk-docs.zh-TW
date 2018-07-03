---
title: 建立和設定 BizTalk 連接埠以供 Contoso |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports, creating
- private process tutorial, creating ports
- creating, ports
- configuring, ports
- private process tutorial, configuring ports
- ports, configuring
ms.assetid: 179af692-e14c-40da-9c43-1a7d0b6beb1f
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e7453fb35758aaca4eea3d8b05be4a7a7584085
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36996503"
---
# <a name="creating-and-configuring-biztalk-ports-for-contoso"></a><span data-ttu-id="24306-102">建立和設定 BizTalk 連接埠以供 Contoso</span><span class="sxs-lookup"><span data-stu-id="24306-102">Creating and Configuring BizTalk Ports for Contoso</span></span>
<span data-ttu-id="24306-103">在本節中，您需要將目前的解決方案整合到 Microsoft® BizTalk Server 上。</span><span class="sxs-lookup"><span data-stu-id="24306-103">In this section, you integrate your current solution into Microsoft® BizTalk Server.</span></span> <span data-ttu-id="24306-104">在那之前，您必須先在全域組件快取 (GAC) 中安裝您的組件，然後在組態資料庫中設定該組件。</span><span class="sxs-lookup"><span data-stu-id="24306-104">Before you do this, you install your assembly in the Global Assembly Cache (GAC), and then configure it in the Configuration database.</span></span> <span data-ttu-id="24306-105">接著，您使用 SQL 配接器和 HTTP 配接器建立與設定傳送埠。</span><span class="sxs-lookup"><span data-stu-id="24306-105">You then create and configure send ports using a SQL adapter and a HTTP adapter.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="24306-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="24306-106">In This Section</span></span>  
  
-   [<span data-ttu-id="24306-107">步驟 1：指派強式名稱給 Contoso 組件</span><span class="sxs-lookup"><span data-stu-id="24306-107">Step 1: Assigning a Strong Name to the Contoso Assembly</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-1-assigning-a-strong-name-to-the-contoso-assembly.md)  
  
-   [<span data-ttu-id="24306-108">步驟 2： 為 Contoso 3A2 價格與可用性查詢/回應實例建立連接埠</span><span class="sxs-lookup"><span data-stu-id="24306-108">Step 2: Creating Ports for the Contoso 3A2 Price and Availability Query/Response Scenario</span></span>](step-2-create-ports-for-contoso-3a2-price-and-availability-query.md)