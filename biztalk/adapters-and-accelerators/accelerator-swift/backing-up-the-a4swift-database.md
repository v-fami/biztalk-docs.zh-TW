---
title: "備份 A4SWIFT 資料庫 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- backing up A4SWIFT database
- A4SWIFT database, backing up
ms.assetid: 53e46380-5be7-4d4c-b04c-d917ab40c07c
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e4cd2cd1eadf3dc6f11a6e3178258caaaf88006d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="backing-up-the-a4swift-database"></a><span data-ttu-id="bed81-102">A4SWIFT 資料庫的備份</span><span class="sxs-lookup"><span data-stu-id="bed81-102">Backing Up the A4SWIFT Database</span></span>
<span data-ttu-id="bed81-103">您經常應該備份資料庫，BizTalk Server 和 A4SWIFT 系統較低的嚴重失敗的風險中。</span><span class="sxs-lookup"><span data-stu-id="bed81-103">You should routinely back up the databases in your BizTalk Server and A4SWIFT system to lower the risks of a catastrophic failure.</span></span> <span data-ttu-id="bed81-104">這些資料庫包括 BizTalk Server 來源系統，和 A4SWIFT 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bed81-104">These databases include those in your BizTalk Server source system, and the A4SWIFT database.</span></span> <span data-ttu-id="bed81-105">除了降低風險，這也可讓您清除 A4SWIFT 可以成長到極大的歷程記錄檔案。</span><span class="sxs-lookup"><span data-stu-id="bed81-105">In addition to lowering risks, this will also enable you to purge A4SWIFT history files that can grow to a significant size.</span></span>  
  
 <span data-ttu-id="bed81-106">如需 BizTalk Server 來源系統中的資料庫備份的詳細資訊，請參閱中的 「 備份和還原 BizTalk Server 資料庫 」 主題[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="bed81-106">For more information about backing up the databases in your BizTalk Server source system, see the "Backing Up and Restoring BizTalk Server Databases" topic in the [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span> <span data-ttu-id="bed81-107">本主題描述您用來備份 BizTalk 資料庫 「 備份 BizTalk Server 」 工作。</span><span class="sxs-lookup"><span data-stu-id="bed81-107">This topic describes the Backup BizTalk Server job that you use to back up BizTalk databases.</span></span>  
  
 <span data-ttu-id="bed81-108">如需 A4SWIFT 資料庫備份的詳細資訊，請參閱中的 < 如何以重新向上自訂資料庫 > 主題[!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="bed81-108">For information about backing up the A4SWIFT database, see the "How to Back Up Custom Databases" topic in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span> <span data-ttu-id="bed81-109">本主題描述如何修改備份 BizTalk Server 作業，以包含自訂 A4SWIFT 資料庫。</span><span class="sxs-lookup"><span data-stu-id="bed81-109">This topic describes how to modify the Backup BizTalk Server job to include the custom A4SWIFT database.</span></span>