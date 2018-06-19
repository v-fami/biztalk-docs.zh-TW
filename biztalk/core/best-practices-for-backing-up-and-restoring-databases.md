---
title: 備份和還原資料庫的最佳作法 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- best practices, maintaining
- restoring, best practices
- best practices, backing up
- backing up, restoring
- backing up, best practices
- maintaining, best practices
- best practices, restoring
ms.assetid: 649ca56b-3cc1-49ad-9f74-ba1521e65ee1
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2543f09c5118e58bd18ea2add113811fb733d884
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22231174"
---
# <a name="best-practices-for-backing-up-and-restoring-databases"></a><span data-ttu-id="cdf63-102">備份和還原資料庫的最佳作法</span><span class="sxs-lookup"><span data-stu-id="cdf63-102">Best Practices for Backing Up and Restoring Databases</span></span>
<span data-ttu-id="cdf63-103">請檢視下列最佳作法，以協助確保您可以備份和還原 BizTalk Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="cdf63-103">Review the following best practices to help ensure that you can backup and restore your BizTalk Server databases.</span></span>  
  
-   <span data-ttu-id="cdf63-104">**開發備份和還原策略，並加以測試。**</span><span class="sxs-lookup"><span data-stu-id="cdf63-104">**Develop backup and restore strategies and test them.**</span></span>  
  
     <span data-ttu-id="cdf63-105">如果擁有好的計畫，當您的資料因為硬體失敗而遺失時，便可以快速地還原。</span><span class="sxs-lookup"><span data-stu-id="cdf63-105">With a good plan, you can quickly recover your data if it is lost due to hardware failure.</span></span>  
  
-   <span data-ttu-id="cdf63-106">**管理磁碟空間和封存先前的備份檔案。**</span><span class="sxs-lookup"><span data-stu-id="cdf63-106">**Manage disk space and archive previous backup files.**</span></span>  
  
     <span data-ttu-id="cdf63-107">備份 BizTalk Server 工作不會刪除過期的備份檔案，所以您必須管理那些備份檔案以回收磁碟空間。</span><span class="sxs-lookup"><span data-stu-id="cdf63-107">The Backup BizTalk Server job does not delete outdated backup files, so you need to manage those backup files to conserve disk space.</span></span> <span data-ttu-id="cdf63-108">在為資料庫建立新的完整備份後，您應該將過期的備份檔案移動到封存儲存裝置以回收主要磁碟上的空間。</span><span class="sxs-lookup"><span data-stu-id="cdf63-108">After you have created a new full backup of your databases, you should move the outdated backup files onto an archival storage device to reclaim space on the primary disk.</span></span>  
  
-   <span data-ttu-id="cdf63-109">**不要在同一部電腦或您要備份的磁碟上儲存備份。**</span><span class="sxs-lookup"><span data-stu-id="cdf63-109">**Do not store backups on the same computer or disk that you are backing up.**</span></span>  
  
     <span data-ttu-id="cdf63-110">您應該為備份指定與原始資料所在之電腦不同的電腦或磁碟。</span><span class="sxs-lookup"><span data-stu-id="cdf63-110">You should specify a computer or disk for your backup that is different from the computer with the original data.</span></span> <span data-ttu-id="cdf63-111">否則，當硬體失敗時，您將會遺失所有的資料。</span><span class="sxs-lookup"><span data-stu-id="cdf63-111">Otherwise, you will lose all of your data if the hardware fails.</span></span>  
  
-   <span data-ttu-id="cdf63-112">**保留複本。**</span><span class="sxs-lookup"><span data-stu-id="cdf63-112">**Retain copies.**</span></span>  
  
     <span data-ttu-id="cdf63-113">至少保留三份媒體的複本。</span><span class="sxs-lookup"><span data-stu-id="cdf63-113">Keep at least three copies of the media.</span></span> <span data-ttu-id="cdf63-114">保留至少一個異地適當受控制的環境。</span><span class="sxs-lookup"><span data-stu-id="cdf63-114">Keep at least one copy off-site in a properly controlled environment.</span></span>  
  
-   <span data-ttu-id="cdf63-115">**執行試驗。**</span><span class="sxs-lookup"><span data-stu-id="cdf63-115">**Perform trial restorations.**</span></span>  
  
     <span data-ttu-id="cdf63-116">一個月至少執行一次試驗復原，以確認您的檔案已適當備份。</span><span class="sxs-lookup"><span data-stu-id="cdf63-116">Perform a trial restoration at least once a month to verify that your files were properly backed up.</span></span> <span data-ttu-id="cdf63-117">試驗復原可以揭露您在驗證軟體是否正常運作時沒有出現的硬體問題。</span><span class="sxs-lookup"><span data-stu-id="cdf63-117">A trial restoration can uncover hardware problems that do not show up when you verify that your software is functioning properly.</span></span> <span data-ttu-id="cdf63-118">不要等到您的硬碟失敗時，才嘗試是否可以還原您的系統和資料庫。</span><span class="sxs-lookup"><span data-stu-id="cdf63-118">Do not wait until your hard disk fails to see if you can restore your system and databases.</span></span>  
  
-   <span data-ttu-id="cdf63-119">**保護裝置和媒體。**</span><span class="sxs-lookup"><span data-stu-id="cdf63-119">**Secure devices and media.**</span></span>  
  
     <span data-ttu-id="cdf63-120">請同時保護儲存裝置和備份媒體。</span><span class="sxs-lookup"><span data-stu-id="cdf63-120">Secure both the storage device and the backup media.</span></span> <span data-ttu-id="cdf63-121">可能有人會藉由將資料還原到另一個自己是系統管理員的伺服器，從偷來的媒體存取資料。</span><span class="sxs-lookup"><span data-stu-id="cdf63-121">It is possible for someone to access the data from a stolen medium by restoring the data to another server for which they are an administrator.</span></span>  
  
-   <span data-ttu-id="cdf63-122">**監控備份和還原程序。**</span><span class="sxs-lookup"><span data-stu-id="cdf63-122">**Monitor the backup and restore process.**</span></span>  
  
     <span data-ttu-id="cdf63-123">為確保備份和還原程序成功，您應該監控用來備份和還原 BizTalk Server 的 SQL Server Agent 作業。</span><span class="sxs-lookup"><span data-stu-id="cdf63-123">To ensure that the backup and restore process was successful, you should monitor the SQL Server Agent jobs used to backup and restore BizTalk Server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdf63-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdf63-124">See Also</span></span>  
 [<span data-ttu-id="cdf63-125">備份和還原 BizTalk Server 資料庫</span><span class="sxs-lookup"><span data-stu-id="cdf63-125">Backing Up and Restoring the BizTalk Server Databases</span></span>](../core/backing-up-and-restoring-the-biztalk-server-databases.md)