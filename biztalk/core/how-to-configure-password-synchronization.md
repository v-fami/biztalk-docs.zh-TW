---
title: "如何設定密碼同步化 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Password Synchronization [SSO], replay files
- Password Synchronization [SSO], maximum age
- SSOCONFIG command line utility
- Password Synchronization [SSO], SSOCONFIG command line utility
- Password Synchronization [SSO], configuring
- configuring, Password Synchronization [SSO]
ms.assetid: 04000dfc-02b9-4d50-babe-8bc8a07a33b7
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb913c1719f4833ef36cf9f73f6a96432217f2af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-password-synchronization"></a><span data-ttu-id="127c1-102">如何設定密碼同步化</span><span class="sxs-lookup"><span data-stu-id="127c1-102">How to Configure Password Synchronization</span></span>
<span data-ttu-id="127c1-103">使用 SSOCONFIG 命令列公用程式可設定您的密碼同步設定。</span><span class="sxs-lookup"><span data-stu-id="127c1-103">Use the SSOCONFIG command line utility to configure your password synchronization settings.</span></span>  
  
### <a name="to-specify-the-directory-for-replay-files"></a><span data-ttu-id="127c1-104">指定重新執行檔案的目錄</span><span class="sxs-lookup"><span data-stu-id="127c1-104">To specify the directory for replay files</span></span>  
  
1.  <span data-ttu-id="127c1-105">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="127c1-105">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="127c1-106">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="127c1-106">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="127c1-107">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="127c1-107">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="127c1-108">預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="127c1-108">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="127c1-109">型別**ssoconfig replayfiles\<重新執行檔案目錄 > &#124; 預設**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="127c1-109">Type **ssoconfig -replayfiles \<replay files directory> &#124; -default** and press Enter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="127c1-110">變更服務帳戶時不會刪除重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="127c1-110">Replay files are not deleted when you change the service account.</span></span> <span data-ttu-id="127c1-111">若變更此帳戶，您需要手動刪除重新執行檔案。</span><span class="sxs-lookup"><span data-stu-id="127c1-111">If you change this account, you will need to delete the replay files manually.</span></span>  
  
#### <a name="to-display-or-change-maximum-password-synchronization-age"></a><span data-ttu-id="127c1-112">顯示或變更最長密碼同步時間</span><span class="sxs-lookup"><span data-stu-id="127c1-112">To display or change maximum password synchronization age</span></span>  
  
1.  <span data-ttu-id="127c1-113">在 **[開始]** 功能表上，按一下 **[執行]**。</span><span class="sxs-lookup"><span data-stu-id="127c1-113">On the **Start** menu, click **Run**.</span></span>  
  
2.  <span data-ttu-id="127c1-114">在**執行**] 對話方塊中，輸入**cmd**，然後按一下 [**確定**。</span><span class="sxs-lookup"><span data-stu-id="127c1-114">In the **Run** dialog box, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="127c1-115">在命令列，移至「企業單一登入」安裝目錄。</span><span class="sxs-lookup"><span data-stu-id="127c1-115">At the command line, go to the Enterprise Single Sign-On installation directory.</span></span> <span data-ttu-id="127c1-116">預設值是\<磁碟機 >: \Program Files\Common Files\Enterprise Single Sign-on。</span><span class="sxs-lookup"><span data-stu-id="127c1-116">The default is \<drive>:\Program Files\Common Files\Enterprise Single Sign-On.</span></span>  
  
4.  <span data-ttu-id="127c1-117">型別**ssoconfig-syncage\<以小時為單位的最大密碼存在時間 >**按下 Enter。</span><span class="sxs-lookup"><span data-stu-id="127c1-117">Type **ssoconfig -syncage \<maximum password age in hours>** and press Enter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="127c1-118">SSOCONFIG 公用程式會使用 SQL Server 電腦上的時間做為系統時間。</span><span class="sxs-lookup"><span data-stu-id="127c1-118">The SSOCONFIG utility uses the time on the SQL Server computer as its system time.</span></span> <span data-ttu-id="127c1-119">使用任何與時間有關的命令時請謹記這點。</span><span class="sxs-lookup"><span data-stu-id="127c1-119">Remember this when using any commands related to time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="127c1-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="127c1-120">See Also</span></span>  
 [<span data-ttu-id="127c1-121">密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="127c1-121">Password Synchronization</span></span>](../core/password-synchronization2.md)