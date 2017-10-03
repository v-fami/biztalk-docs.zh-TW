---
title: "表單產生器公用程式來產生 MT MX InfoPath 表單 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f2fd51-c492-499b-89aa-1b44ed5c9669
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1f85780b8c72f14d630871c98e10f9f85798aa53
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="form-generator-utility-to-generate-mtmx-infopath-forms"></a><span data-ttu-id="51e60-102">表單產生器公用程式產生 MT/MX InfoPath 表單</span><span class="sxs-lookup"><span data-stu-id="51e60-102">Form Generator Utility to Generate MT/MX InfoPath Forms</span></span>
<span data-ttu-id="51e60-103">本文件的目的是要說明如何產生和發佈 MT 與 MX InfoPath 2010 的表單，表單產生器公用程式使用。</span><span class="sxs-lookup"><span data-stu-id="51e60-103">The purpose of this document is to explain how to generate and publish MT and MX InfoPath 2010 forms using Form Generator Utility.</span></span> <span data-ttu-id="51e60-104">這些表單由 Message Repair 和 New Submission 功能[!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="51e60-104">These forms are used by the Message Repair and New Submission feature of [!INCLUDE[A4SWIFT_CurrentVersion_abbrev](../../includes/a4swift-currentversion-abbrev-md.md)].</span></span>  
  
 <span data-ttu-id="51e60-105">此部分包含：</span><span class="sxs-lookup"><span data-stu-id="51e60-105">This section contains:</span></span>  
  
-   [<span data-ttu-id="51e60-106">實作範例</span><span class="sxs-lookup"><span data-stu-id="51e60-106">Implementing the Sample</span></span>](../../adapters-and-accelerators/accelerator-swift/implementing-the-sample.md)  
  
-   [<span data-ttu-id="51e60-107">MT 訊息的範例</span><span class="sxs-lookup"><span data-stu-id="51e60-107">Examples of MT Messages</span></span>](../../adapters-and-accelerators/accelerator-swift/examples-of-mt-messages.md)  
  
-   [<span data-ttu-id="51e60-108">產生類別 0 和 MT121 表單</span><span class="sxs-lookup"><span data-stu-id="51e60-108">Generating Category 0 and MT121 Forms</span></span>](../../adapters-and-accelerators/accelerator-swift/generating-category-0-and-mt121-forms.md)  
  
-   [<span data-ttu-id="51e60-109">MX 訊息的範例</span><span class="sxs-lookup"><span data-stu-id="51e60-109">Examples of MX Messages</span></span>](../../adapters-and-accelerators/accelerator-swift/examples-of-mx-messages.md)  
  
-   [<span data-ttu-id="51e60-110">產生和發行 SharePoint 網站上的 MT/MX 表單</span><span class="sxs-lookup"><span data-stu-id="51e60-110">Generating and Publishing MT/MX Forms on the SharePoint Site</span></span>](../../adapters-and-accelerators/accelerator-swift/generating-and-publishing-mt-mx-forms-on-the-sharepoint-site.md)  
  
-   [<span data-ttu-id="51e60-111">發行 （建立新的訊息） 的 MT 訊息執行個體檔案</span><span class="sxs-lookup"><span data-stu-id="51e60-111">Publishing the MT Message Instance File (Creating New Messages)</span></span>](../../adapters-and-accelerators/accelerator-swift/publishing-the-mt-message-instance-file-creating-new-messages.md)  
  
-   [<span data-ttu-id="51e60-112">發行 MX 訊息執行個體檔案 （建立新的訊息）</span><span class="sxs-lookup"><span data-stu-id="51e60-112">Publishing the MX Message Instance File (Creating New Messages)</span></span>](../../adapters-and-accelerators/accelerator-swift/publishing-the-mx-message-instance-file-creating-new-messages.md)  
  
-   [<span data-ttu-id="51e60-113">多個檢視 MX InfoPath 表單</span><span class="sxs-lookup"><span data-stu-id="51e60-113">Multiple Views of MX InfoPath forms</span></span>](../../adapters-and-accelerators/accelerator-swift/multiple-views-of-mx-infopath-forms.md)