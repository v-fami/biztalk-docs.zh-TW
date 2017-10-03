---
title: "進階備份和 Restore2 資訊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa6a3527-4889-40ae-aacb-b8ea75be0329
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6991e417afaee807d999f7123f7a853dbd955eb3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="advanced-information-about-backup-and-restore"></a><span data-ttu-id="b3ec0-102">關於備份和還原的進階資訊</span><span class="sxs-lookup"><span data-stu-id="b3ec0-102">Advanced Information About Backup and Restore</span></span>
<span data-ttu-id="b3ec0-103">此處所列的主題描述備份和還原程序，在更詳細說明和適用於具有全盤瞭解的進階使用者[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b3ec0-103">The topics listed here describe the backup and restore processes in more detail and are intended to be used by advanced users with a thorough understanding of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="b3ec0-104">標示的交易、 完整的備份和記錄檔的相關資訊，請參閱[標示的交易、 完整備份和記錄檔備份](http://go.microsoft.com/fwlink/?LinkId=151565)(http://go.microsoft.com/fwlink/?LinkId=151565)。</span><span class="sxs-lookup"><span data-stu-id="b3ec0-104">For information about marked transaction, full backups, and logs, see [Marked Transactions, Full Backups, and Log Backups](http://go.microsoft.com/fwlink/?LinkId=151565) (http://go.microsoft.com/fwlink/?LinkId=151565).</span></span>  
  
-   <span data-ttu-id="b3ec0-105">如需有關資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]記錄傳送，請參閱[BizTalk Server 記錄傳送](http://go.microsoft.com/fwlink/?LinkId=151566)(http://go.microsoft.com/fwlink/?LinkId=151566)。</span><span class="sxs-lookup"><span data-stu-id="b3ec0-105">For information about [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] log shipping, see [BizTalk Server Log Shipping](http://go.microsoft.com/fwlink/?LinkId=151566) (http://go.microsoft.com/fwlink/?LinkId=151566).</span></span>  
  
-   <span data-ttu-id="b3ec0-106">如需有關排程備份資訊[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]作業，請參閱[如何排程 「 備份 BizTalk Server 」 工作](http://go.microsoft.com/fwlink/?LinkId=151568)(http://go.microsoft.com/fwlink/?LinkId=151568)。</span><span class="sxs-lookup"><span data-stu-id="b3ec0-106">For information about scheduling backup [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] job, see [How to Schedule the Backup BizTalk Server Job](http://go.microsoft.com/fwlink/?LinkId=151568) (http://go.microsoft.com/fwlink/?LinkId=151568).</span></span>  
  
-   <span data-ttu-id="b3ec0-107">如需備份自訂資料庫的詳細資訊，請參閱[如何備份自訂資料庫](http://go.microsoft.com/fwlink/?LinkId=151569)(http://go.microsoft.com/fwlink/?LinkId=151569)。</span><span class="sxs-lookup"><span data-stu-id="b3ec0-107">For information about backing up custom databases, see [How to Back Up Custom Databases](http://go.microsoft.com/fwlink/?LinkId=151569) (http://go.microsoft.com/fwlink/?LinkId=151569).</span></span>  
  
-   <span data-ttu-id="b3ec0-108">如需建立連結的伺服器資訊，請參閱[如何建立連結的伺服器](http://go.microsoft.com/fwlink/?LinkId=151570)(http://go.microsoft.com/fwlink/?LinkId=151570)。</span><span class="sxs-lookup"><span data-stu-id="b3ec0-108">For information about creating a linked server, see [How to Create a Linked Server](http://go.microsoft.com/fwlink/?LinkId=151570) (http://go.microsoft.com/fwlink/?LinkId=151570).</span></span>  
  
-   <span data-ttu-id="b3ec0-109">如需檢視還原備份的記錄資訊，請參閱[檢視歷程記錄的還原備份](http://go.microsoft.com/fwlink/?LinkId=151572)(http://go.microsoft.com/fwlink/?LinkId=151572)。</span><span class="sxs-lookup"><span data-stu-id="b3ec0-109">For information about viewing the history of restored backups, see [Viewing the History of Restored Backups](http://go.microsoft.com/fwlink/?LinkId=151572) (http://go.microsoft.com/fwlink/?LinkId=151572).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3ec0-110">本節內容</span><span class="sxs-lookup"><span data-stu-id="b3ec0-110">In This Section</span></span>  
  
-   [<span data-ttu-id="b3ec0-111">BizTalk Server 記錄傳送使用 Windows 叢集名稱和 IP 位址</span><span class="sxs-lookup"><span data-stu-id="b3ec0-111">BizTalk Server Log Shipping Using a Windows Cluster Name and IP Address</span></span>](../technical-guides/biztalk-server-log-shipping-using-a-windows-cluster-name-and-ip-address.md)  
  
-   [<span data-ttu-id="b3ec0-112">從暖備份還原生產環境</span><span class="sxs-lookup"><span data-stu-id="b3ec0-112">Restoring Production from a Warm Backup</span></span>](../technical-guides/restoring-production-from-a-warm-backup.md)