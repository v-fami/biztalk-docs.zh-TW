---
title: 檢查清單： 封存和清除 BizTalk 追蹤資料庫 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- archiving [Tracking database], checklist
- checklists, purging [Tracking database]
- purging, checklist
- checklists, archiving [Tracking database]
ms.assetid: dccbf471-2add-498e-b292-287d9a94161b
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 22e97ac12e6b6b304318f57f309767ec7c63815f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22232238"
---
# <a name="checklist-archiving-and-purging-the-biztalk-tracking-database"></a><span data-ttu-id="93be7-102">檢查清單：封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="93be7-102">Checklist: Archiving and Purging the BizTalk Tracking Database</span></span>
|<span data-ttu-id="93be7-103">步驟</span><span class="sxs-lookup"><span data-stu-id="93be7-103">Step</span></span>|<span data-ttu-id="93be7-104">參考</span><span class="sxs-lookup"><span data-stu-id="93be7-104">Reference</span></span>|  
|----------|---------------|  
|<span data-ttu-id="93be7-105">閱讀「封存和清除」概觀，以更熟悉封存和清除追蹤資料的程序。</span><span class="sxs-lookup"><span data-stu-id="93be7-105">Read the Archiving and Purging overview to become more familiar with the process of archiving and purging tracking data.</span></span>|[<span data-ttu-id="93be7-106">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="93be7-106">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)|  
|<span data-ttu-id="93be7-107">雖然您可使用登入認證來執行 DTA 清除和封存工作，但是為了提高安全性，您應該以必要的 SQL Server 認證設定 BTS_BACKUP_USERS 角色，以執行 DTA 清除和封存工作。</span><span class="sxs-lookup"><span data-stu-id="93be7-107">Although you can run the DTA Purge and Archive job using your logon credentials, for added security, you should configure the BTS_BACKUP_USERS role with the necessary SQL Server credentials to run the DTA Purge and Archive job.</span></span> <span data-ttu-id="93be7-108">如此可協助避免權限提升的情形發生。</span><span class="sxs-lookup"><span data-stu-id="93be7-108">This helps to prevent elevation of privileges.</span></span>|[<span data-ttu-id="93be7-109">如何設定 BTS_BACKUP_USERS 角色以封存和清除來自 BizTalk 追蹤資料庫的資料</span><span class="sxs-lookup"><span data-stu-id="93be7-109">How to Configure the BTS_BACKUP_USERS Role for Archiving and Purging Data from the BizTalk Tracking Database</span></span>](../core/configure-bts_backup_users-role-to-archive-and-purge-from-tracking-database.md)|  
|<span data-ttu-id="93be7-110">設定 DTA 清除和封存工作。</span><span class="sxs-lookup"><span data-stu-id="93be7-110">Configure the DTA Purge and Archive job.</span></span>|[<span data-ttu-id="93be7-111">如何設定 DTA 清除與封存作業</span><span class="sxs-lookup"><span data-stu-id="93be7-111">How to Configure the DTA Purge and Archive Job</span></span>](../core/how-to-configure-the-dta-purge-and-archive-job.md)|  
|<span data-ttu-id="93be7-112">執行 DTA 清除和封存工作，此工作會封存 BizTalk 追蹤 (BizTalkDTADb) 資料庫中的資料，並清除舊資料。</span><span class="sxs-lookup"><span data-stu-id="93be7-112">Run the DTA Purge and Archive job, which archives the data in your BizTalk Tracking (BizTalkDTADb) database and purges old data.</span></span>|[<span data-ttu-id="93be7-113">如何從 BizTalk 追蹤資料庫清除資料</span><span class="sxs-lookup"><span data-stu-id="93be7-113">How to Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)|  
|<span data-ttu-id="93be7-114">您可以選擇從 BizTalk 追蹤 (BizTalkDTADb) 資料庫手動清除資料。</span><span class="sxs-lookup"><span data-stu-id="93be7-114">Optionally, you can manually purge data from the BizTalk Tracking (BizTalkDTADb) database.</span></span>|[<span data-ttu-id="93be7-115">如何從 BizTalk 追蹤資料庫手動清除資料</span><span class="sxs-lookup"><span data-stu-id="93be7-115">How to Manually Purge Data from the BizTalk Tracking Database</span></span>](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)|  
|<span data-ttu-id="93be7-116">從 BizTalk 追蹤 (BizTalkDTADb) 資料庫啟用封存資料的自動驗證。</span><span class="sxs-lookup"><span data-stu-id="93be7-116">Enable automatic validation of the archived data from the BizTalk Tracking (BizTalkDTADb) database.</span></span>|[<span data-ttu-id="93be7-117">如何啟用自動封存驗證</span><span class="sxs-lookup"><span data-stu-id="93be7-117">How to Enable Automatic Archive Validation</span></span>](../core/how-to-enable-automatic-archive-validation.md)|  
|<span data-ttu-id="93be7-118">將追蹤的訊息複製到 BizTalk 追蹤 (BizTalkDTADb) 資料庫。</span><span class="sxs-lookup"><span data-stu-id="93be7-118">Copy tracked messages into the BizTalk Tracking (BizTalkDTADb) database.</span></span> <span data-ttu-id="93be7-119">若要使用「DTA 清除與封存」清除與封存工作來清除資料，則這是有必要的。</span><span class="sxs-lookup"><span data-stu-id="93be7-119">This is required in order to purge data using the DTA Purge and Archive job.</span></span>|[<span data-ttu-id="93be7-120">如何將追蹤的訊息複製到 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="93be7-120">How to Copy Tracked Messages into the BizTalk Tracking Database</span></span>](../core/how-to-copy-tracked-messages-into-the-biztalk-tracking-database.md)|  
  
## <a name="see-also"></a><span data-ttu-id="93be7-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93be7-121">See Also</span></span>  
 [<span data-ttu-id="93be7-122">封存和清除 BizTalk 追蹤資料庫</span><span class="sxs-lookup"><span data-stu-id="93be7-122">Archiving and Purging the BizTalk Tracking Database</span></span>](../core/archiving-and-purging-the-biztalk-tracking-database.md)