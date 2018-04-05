---
title: 維護 BizTalk Server1 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- BizTalk Server, maintaining
ms.assetid: dd1e4497-839a-4686-b213-da100b6b5226
caps.latest.revision: 18
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e56d1cb915a91136058a6c1d4a670416903e8aef
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="maintaining-biztalk-server1"></a><span data-ttu-id="42b3f-102">維護 BizTalk Server1</span><span class="sxs-lookup"><span data-stu-id="42b3f-102">Maintaining BizTalk Server1</span></span>
<span data-ttu-id="42b3f-103">本節提供有關如何備份與還原 BizTalk Server 及 Microsoft BizTalk Server 資料庫、如何封存及清除 [BizTalk 追蹤] (BizTalkDTADb) 資料庫中的資料，以及如何移動某些較常被移動的 BizTalk Server 資料庫之詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="42b3f-103">This section provides information about how to back up and restore BizTalk Server and the Microsoft BizTalk Server databases, how to archive and purge data from the BizTalk Tracking (BizTalkDTADb) database, and how to move some of the more commonly moved BizTalk Server databases.</span></span> <span data-ttu-id="42b3f-104">它會提供備份和還原程序的概觀，以及維護 BizTalk 追蹤資料庫的建議。</span><span class="sxs-lookup"><span data-stu-id="42b3f-104">It provides an overview of the backup and restoration process, as well as recommendations for maintaining the BizTalk Tracking database.</span></span> <span data-ttu-id="42b3f-105">它提供有關以手動方式從測試環境中的 BizTalk MessageBox 資料庫清除資料。</span><span class="sxs-lookup"><span data-stu-id="42b3f-105">It provides information on manually purging data from the BizTalk MessageBox database in a test environment.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42b3f-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="42b3f-106">In This Section</span></span>  
  
-   [<span data-ttu-id="42b3f-107">備份和還原 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="42b3f-107">Backing Up and Restoring BizTalk Server</span></span>](../core/backing-up-and-restoring-biztalk-server.md)  
  
-   [<span data-ttu-id="42b3f-108">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="42b3f-108">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)  
  
-   [<span data-ttu-id="42b3f-109">移動 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="42b3f-109">Moving BizTalk Server Databases</span></span>](../core/moving-biztalk-server-databases.md)  
  
-   [<span data-ttu-id="42b3f-110">如何從測試環境中的 MessageBox 資料庫手動清除資料</span><span class="sxs-lookup"><span data-stu-id="42b3f-110">How to Manually Purge Data from the MessageBox Database in a Test Environment</span></span>](../core/how-to-manually-purge-data-from-the-messagebox-database-in-a-test-environment.md)