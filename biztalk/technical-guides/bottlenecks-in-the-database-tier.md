---
title: "資料庫層中的瓶頸 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55b37393-32dc-4717-bf62-48588c23dd78
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b741f1ffcd68f7a5c739731e5aa9a1db55be34c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="bottlenecks-in-the-database-tier"></a><span data-ttu-id="9b644-102">資料庫層中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="9b644-102">Bottlenecks in the Database Tier</span></span>
<span data-ttu-id="9b644-103">本節說明如何識別 MessageBox 資料庫、 追蹤資料庫和 BAM 主要匯入資料庫中的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="9b644-103">This section explains how to identify bottlenecks in the BizTalk MessageBox database, Tracking database, and BAM Primary Import database.</span></span> <span data-ttu-id="9b644-104">它也會說明如何避免磁碟爭用情況。</span><span class="sxs-lookup"><span data-stu-id="9b644-104">It also explains how to avoid disk contention.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b644-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="9b644-105">In This Section</span></span>  
  
-   [<span data-ttu-id="9b644-106">如何識別 MessageBox Database1 中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="9b644-106">How to Identify Bottlenecks in the MessageBox Database1</span></span>](../technical-guides/how-to-identify-bottlenecks-in-the-messagebox-database1.md)  
  
-   [<span data-ttu-id="9b644-107">如何識別追蹤資料庫中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="9b644-107">How to Identify Bottlenecks in the Tracking Database</span></span>](../technical-guides/how-to-identify-bottlenecks-in-the-tracking-database.md)  
  
-   [<span data-ttu-id="9b644-108">如何識別 BAM 主要匯入資料庫中的瓶頸</span><span class="sxs-lookup"><span data-stu-id="9b644-108">How to Identify Bottlenecks in the BAM Primary Import Database</span></span>](../technical-guides/how-to-identify-bottlenecks-in-the-bam-primary-import-database.md)  
  
-   [<span data-ttu-id="9b644-109">如何避免磁碟 Contention2</span><span class="sxs-lookup"><span data-stu-id="9b644-109">How to Avoid Disk Contention2</span></span>](../technical-guides/how-to-avoid-disk-contention2.md)