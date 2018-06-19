---
title: 如何備份 BAM 入口網站 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8cea02e6-e387-4048-a1f3-d7c3c562f470
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27e7308e54505c795e35ffa2fbb2d287c1a49ec4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247118"
---
# <a name="how-to-back-up-the-bam-portal"></a><span data-ttu-id="a20e2-102">如何備份 BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="a20e2-102">How to Back Up the BAM Portal</span></span>
<span data-ttu-id="a20e2-103">如果您使用商務活動監控 (BAM)，必須備份 BAM 入口網站做為備份 BizTalk Server 的一部分。</span><span class="sxs-lookup"><span data-stu-id="a20e2-103">If you are using Business Activity Monitoring (BAM), you must back up the BAM portal as part of backing up your BizTalk server.</span></span> <span data-ttu-id="a20e2-104">如果您未使用 BAM，則此程序是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="a20e2-104">If you are not using BAM, this procedure is optional.</span></span>  
  
 <span data-ttu-id="a20e2-105">網際網路資訊服務 (IIS) 版本而定您要備份的備份程序的某些部分與相當不同。</span><span class="sxs-lookup"><span data-stu-id="a20e2-105">Certain portions of the backup process differ markedly depending on which version of Internet Information Services (IIS) you are backing up.</span></span> <span data-ttu-id="a20e2-106">IIS 6.0 可讓您分別備份應用程式集區設定和網站組態，您可以加密組態備份檔案使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="a20e2-106">IIS 6.0 permits you to back up the application pool configuration and web site configuration separately, and you can encrypt the configuration backup files using a password.</span></span>  
  
 <span data-ttu-id="a20e2-107">IIS 7.0 會將應用程式集區和網站的組態設定儲存至單一檔案，applicationHost.config。ApplicationHost.config 檔案並未加密，但帳戶密碼，如果有的話，會加密檔案中。</span><span class="sxs-lookup"><span data-stu-id="a20e2-107">IIS 7.0 saves configuration settings for both the application pool and web site to a single file, applicationHost.config. The applicationHost.config file is not encrypted, but account passwords, if any, are encrypted in the file.</span></span> <span data-ttu-id="a20e2-108">加密會使用您要備份的電腦中的憑證來執行。</span><span class="sxs-lookup"><span data-stu-id="a20e2-108">Encryption is performed using the certificate from the computer you are backing up.</span></span> <span data-ttu-id="a20e2-109">此設定無法還原到它的來源以外的電腦。</span><span class="sxs-lookup"><span data-stu-id="a20e2-109">This configuration cannot be restored to a computer other than the one from which it originated.</span></span>  
  
 <span data-ttu-id="a20e2-110">您無法備份 BAM 入口網站設定使用 IIS 7.0 管理員;您必須使用**Appcmd.exe**命令列工具。</span><span class="sxs-lookup"><span data-stu-id="a20e2-110">You cannot back up the BAM portal configuration using the IIS 7.0 Manager; you must use the **Appcmd.exe** command-line tool.</span></span> <span data-ttu-id="a20e2-111">如需 Appcmd 的詳細資訊，請參閱[http://go.microsoft.com/fwlink/?LinkId=147497](http://go.microsoft.com/fwlink/?LinkId=147497)。</span><span class="sxs-lookup"><span data-stu-id="a20e2-111">For more information about Appcmd, see [http://go.microsoft.com/fwlink/?LinkId=147497](http://go.microsoft.com/fwlink/?LinkId=147497).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="a20e2-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="a20e2-112">Prerequisites</span></span>  
 <span data-ttu-id="a20e2-113">您必須以「系統管理員」群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="a20e2-113">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
### <a name="to-back-up-the-bam-portal-iis-70"></a><span data-ttu-id="a20e2-114">若要備份 BAM 入口網站 (IIS 7.0)</span><span class="sxs-lookup"><span data-stu-id="a20e2-114">To back up the BAM portal (IIS 7.0)</span></span>  
  
1.  <span data-ttu-id="a20e2-115">按一下 **[開始]**，然後按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="a20e2-115">Click **Start**, and then click **Run**.</span></span>  
  
2.  <span data-ttu-id="a20e2-116">在 執行 對話方塊中，開啟 方塊中，輸入下列命令： `runas /user:` *computername*`\`*accountname* `cmd`，然後按一下 **確定**或按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a20e2-116">On the Run dialog, in the Open box, type the following: `runas /user:`*computername*`\`*accountname* `cmd`, and then click **OK** or press **Enter**.</span></span>  
  
     <span data-ttu-id="a20e2-117">*Accountname*必須是本機電腦上 administrators 群組的成員。</span><span class="sxs-lookup"><span data-stu-id="a20e2-117">*Accountname* must be a member of the administrators group on the local computer.</span></span>  
  
3.  <span data-ttu-id="a20e2-118">出現提示時，輸入的密碼*accountname*，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a20e2-118">When prompted, type the password for *accountname*, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="a20e2-119">型別`cd %windir%\system32\inetsrv`，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a20e2-119">Type `cd %windir%\system32\inetsrv`, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="a20e2-120">型別`appcmd add backup “` *backupname*`”`，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a20e2-120">Type `appcmd add backup “`*backupname*`”`, and then press **Enter**.</span></span>  
  
     <span data-ttu-id="a20e2-121">您沒有輸入備份的名稱。</span><span class="sxs-lookup"><span data-stu-id="a20e2-121">You do not have to enter a backup name.</span></span> <span data-ttu-id="a20e2-122">如果未設定，就會自動產生。</span><span class="sxs-lookup"><span data-stu-id="a20e2-122">If not set, it will be autogenerated.</span></span> <span data-ttu-id="a20e2-123">自動產生的備份名稱的範例是"20090224T123302。 」</span><span class="sxs-lookup"><span data-stu-id="a20e2-123">An example of an autogenerated backup name is “20090224T123302.”</span></span>  
  
     <span data-ttu-id="a20e2-124">若要查看現有的設定備份清單，請輸入`appcmd list backup`，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a20e2-124">To see a list of existing configuration backups, type `appcmd list backup`, and then press **Enter**.</span></span> <span data-ttu-id="a20e2-125">使用者所建立的備份會儲存在 **%windir%\system32\inetsrv\backup**目錄。</span><span class="sxs-lookup"><span data-stu-id="a20e2-125">Backups created by the user are saved in the **%windir%\system32\inetsrv\backup** directory.</span></span> <span data-ttu-id="a20e2-126">若要查看所提供的備份選項的清單**appcmd.exe**，型別`appcmd backup /?`，然後按下**Enter**。</span><span class="sxs-lookup"><span data-stu-id="a20e2-126">To see a list of the backup options provided by **appcmd.exe**, type `appcmd backup /?`, and then press **Enter**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a20e2-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a20e2-127">See Also</span></span>  
 <span data-ttu-id="a20e2-128">[備份執行 BizTalk Server 的電腦](../core/backing-up-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="a20e2-128">[Backing Up a Computer Running BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) </span></span>  
 <span data-ttu-id="a20e2-129">[復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="a20e2-129">[Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span></span>  
 [<span data-ttu-id="a20e2-130">BAM 入口網站</span><span class="sxs-lookup"><span data-stu-id="a20e2-130">BAM Portal</span></span>](../core/bam-portal.md)