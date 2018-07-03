---
title: 維護 BTARN 資料庫 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- maintaining databases
- databases, maintaining
ms.assetid: b048f68c-1e12-42e3-b7bb-2a87fe977f4e
caps.latest.revision: 4
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 496e83311c4ede6446bad8893fbe37b22cf8420d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37000767"
---
# <a name="maintaining-btarn-databases"></a><span data-ttu-id="663de-102">維護 BTARN 資料庫</span><span class="sxs-lookup"><span data-stu-id="663de-102">Maintaining BTARN Databases</span></span>
<span data-ttu-id="663de-103">Microsoft®[!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)]資料庫可成長太大，其大小會影響系統效能。</span><span class="sxs-lookup"><span data-stu-id="663de-103">Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] databases can grow so large that their size can affect system performance.</span></span> <span data-ttu-id="663de-104">這可能是由資料表中留下未使用的項目 (例如孤立的附件或未使用的摘要) 等特定情況所引起的，</span><span class="sxs-lookup"><span data-stu-id="663de-104">This can result from specific circumstances that leave unused entries in the tables, such as orphan attachments or unused digests.</span></span> <span data-ttu-id="663de-105">也可能是因為未刪除資料表中的舊項目。</span><span class="sxs-lookup"><span data-stu-id="663de-105">It can also occur from not deleting old entries in the tables.</span></span> <span data-ttu-id="663de-106">請依照本章節的程序來維護您的 [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] 資料庫，以免影響效能。</span><span class="sxs-lookup"><span data-stu-id="663de-106">Follow the procedures in this section to maintain your [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] databases so there is no effect on performance.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="663de-107">本節內容</span><span class="sxs-lookup"><span data-stu-id="663de-107">In This Section</span></span>  
  
-   [<span data-ttu-id="663de-108">維護不可否認性資料庫資料表</span><span class="sxs-lookup"><span data-stu-id="663de-108">Maintaining the Non-Repudiation Database Tables</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/maintaining-the-non-repudiation-database-tables.md)  
  
-   [<span data-ttu-id="663de-109">刪除摘要</span><span class="sxs-lookup"><span data-stu-id="663de-109">Deleting Digests</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/deleting-digests.md)  
  
-   [<span data-ttu-id="663de-110">刪除孤立的附件</span><span class="sxs-lookup"><span data-stu-id="663de-110">Deleting Orphan Attachments</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/deleting-orphan-attachments.md)