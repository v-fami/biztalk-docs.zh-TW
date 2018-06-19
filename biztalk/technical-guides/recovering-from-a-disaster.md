---
title: 從損壞中復原 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eefb036b-7254-407d-a203-66708c07f67d
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ff6d7ba22180995d41fa536717804483931c7ad0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22301934"
---
# <a name="recovering-from-a-disaster"></a><span data-ttu-id="4c3d6-102">從損壞中復原</span><span class="sxs-lookup"><span data-stu-id="4c3d6-102">Recovering from a Disaster</span></span>
<span data-ttu-id="4c3d6-103">本節詳細說明的步驟，將實際執行的作業傳送到災害復原站台。</span><span class="sxs-lookup"><span data-stu-id="4c3d6-103">This section details the steps to transfer production operations to the disaster recovery site.</span></span> <span data-ttu-id="4c3d6-104">本章節的目的，如線上生產系統被指 「 來源 」 系統。</span><span class="sxs-lookup"><span data-stu-id="4c3d6-104">For the purposes of this section, the online production system is referred to as the “source” system.</span></span> <span data-ttu-id="4c3d6-105">災害復原站台被指 「 目的地 」 系統。</span><span class="sxs-lookup"><span data-stu-id="4c3d6-105">The disaster recovery site is referred to as the “destination” system.</span></span> <span data-ttu-id="4c3d6-106">本節提供災害復原程序的概觀。</span><span class="sxs-lookup"><span data-stu-id="4c3d6-106">This section provides an overview of the disaster recovery process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4c3d6-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="4c3d6-107">In This Section</span></span>  
  
-   [<span data-ttu-id="4c3d6-108">還原 BizTalk 群組</span><span class="sxs-lookup"><span data-stu-id="4c3d6-108">Restoring the BizTalk Group</span></span>](../technical-guides/restoring-the-biztalk-group.md)  
  
-   [<span data-ttu-id="4c3d6-109">復原執行階段電腦</span><span class="sxs-lookup"><span data-stu-id="4c3d6-109">Recovering the Runtime Computers</span></span>](../technical-guides/recovering-the-runtime-computers.md)  
  
-   [<span data-ttu-id="4c3d6-110">復原其他應用程式</span><span class="sxs-lookup"><span data-stu-id="4c3d6-110">Recovering Additional Applications</span></span>](../technical-guides/recovering-additional-applications.md)  
  
-   [<span data-ttu-id="4c3d6-111">疑難排解記錄傳送</span><span class="sxs-lookup"><span data-stu-id="4c3d6-111">Troubleshooting Log Shipping</span></span>](../technical-guides/troubleshooting-log-shipping.md)