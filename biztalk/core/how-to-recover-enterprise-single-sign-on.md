---
title: 如何復原企業單一登入 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 845e6ff7-88a8-4ab4-b307-f9275d44600e
caps.latest.revision: 14
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d56953fcab29b53f23ba3097296a74aeb67a17c8
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973119"
---
# <a name="how-to-recover-enterprise-single-sign-on"></a><span data-ttu-id="6b102-102">如何復原企業單一登入</span><span class="sxs-lookup"><span data-stu-id="6b102-102">How to Recover Enterprise Single Sign-On</span></span>
<span data-ttu-id="6b102-103">在復原 BizTalk Server 之前，您必須先復原「企業單一登入」(SSO)。</span><span class="sxs-lookup"><span data-stu-id="6b102-103">Before you can recover BizTalk Server, you must first recover Enterprise Single Sign-On (SSO).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6b102-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="6b102-104">Prerequisites</span></span>  
  
-   <span data-ttu-id="6b102-105">您必須以「單一登入系統管理員」群組成員及「系統管理員」群組成員的身分登入，才可執行此工作。</span><span class="sxs-lookup"><span data-stu-id="6b102-105">You must be logged on as a member of the Single Sign-On Administrators group and a member of the Administrators group to perform this task.</span></span>  
  
-   <span data-ttu-id="6b102-106">您必須具有在 SSO 組態期間使用的密碼。</span><span class="sxs-lookup"><span data-stu-id="6b102-106">You must have the password used during SSO configuration.</span></span>  
  
-   <span data-ttu-id="6b102-107">所有資料庫在遠端伺服器都保持完整。</span><span class="sxs-lookup"><span data-stu-id="6b102-107">All databases are intact on the remote server.</span></span>  
  
-   <span data-ttu-id="6b102-108">備份主要密碼檔要保持完整，並儲存在安全的地方。</span><span class="sxs-lookup"><span data-stu-id="6b102-108">The backup master secret file is intact and stored in a safe place.</span></span>  
  
### <a name="to-recover-enterprise-single-sign-on"></a><span data-ttu-id="6b102-109">復原企業單一登入</span><span class="sxs-lookup"><span data-stu-id="6b102-109">To recover Enterprise Single Sign-On</span></span>  
  
1. <span data-ttu-id="6b102-110">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 組態**。</span><span class="sxs-lookup"><span data-stu-id="6b102-110">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
2. <span data-ttu-id="6b102-111">在 Microsoft BizTalk Server 組態，在主控台樹狀目錄中，按一下**企業 SSO**。</span><span class="sxs-lookup"><span data-stu-id="6b102-111">In Microsoft BizTalk Server Configuration, in the console tree, click **Enterprise SSO**.</span></span>  
  
3. <span data-ttu-id="6b102-112">在 [詳細資料] 窗格中，選取**啟用企業單一登入此電腦上**，然後按一下**加入現有的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="6b102-112">In the details pane, select **Enable Enterprise Single Sign-On on this computer**, and then click **Join an existing SSO system**.</span></span>  
  
4. <span data-ttu-id="6b102-113">在 **資料存放區**，輸入裝載 SSO 資料庫與 SSO 資料庫名稱的 SQL server 的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b102-113">In **Data stores**, enter the name of the SQL server hosting the SSO database and the name of the SSO database.</span></span>  
  
5. <span data-ttu-id="6b102-114">在  **Windows 服務**，輸入您原來安裝和設定 BizTalk Server 時，您會使用 SSO 服務帳戶的使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="6b102-114">In **Windows service**, enter the user name and password for the SSO service account that you used when you originally installed and configured BizTalk Server.</span></span>  
  
   > [!NOTE]
   >  <span data-ttu-id="6b102-115">您可使用不同的帳戶，但此帳戶必須是「單一登入系統管理員」群組的成員。</span><span class="sxs-lookup"><span data-stu-id="6b102-115">You can use a different account, but it must be a member of the Single Sign-On Administrators group.</span></span>  
  
6. <span data-ttu-id="6b102-116">按一下 [套用組態]。</span><span class="sxs-lookup"><span data-stu-id="6b102-116">Click **Apply Configuration**.</span></span>  
  
    <span data-ttu-id="6b102-117">未擷取任何主要密碼的警告會出現。</span><span class="sxs-lookup"><span data-stu-id="6b102-117">A warning that no master secrets were retrieved is displayed.</span></span> <span data-ttu-id="6b102-118">您可使用事件檢視器檢查企業單一登入服務現在是否已啟動且在電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="6b102-118">You can use Event Viewer to verify that the Enterprise Single Sign-On service is now started and running on the computer.</span></span>  
  
7. <span data-ttu-id="6b102-119">按一下 **檔案**，然後按一下**結束**。</span><span class="sxs-lookup"><span data-stu-id="6b102-119">Click **File**, and then click **Exit**.</span></span>  
  
8. <span data-ttu-id="6b102-120">按一下 **開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6b102-120">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="6b102-121">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="6b102-121">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="6b102-122">**cd Program Files\Common Files\Enterprise Single Sign-on**</span><span class="sxs-lookup"><span data-stu-id="6b102-122">**cd Program Files\Common Files\Enterprise Single Sign-On**</span></span>  
  
10. <span data-ttu-id="6b102-123">在命令提示字元中，輸入：</span><span class="sxs-lookup"><span data-stu-id="6b102-123">At the command prompt, type:</span></span>  
  
     <span data-ttu-id="6b102-124">**ssoconfig-restoreSecret***\<backupfile  \>*</span><span class="sxs-lookup"><span data-stu-id="6b102-124">**ssoconfig -restoreSecret**  *\<backupfile\>*</span></span>  
  
     <span data-ttu-id="6b102-125">何處*\<backupfile\>* 是您備份主要祕密檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="6b102-125">where *\<backupfile\>* is the name of the master secret file that you backed up.</span></span>  
  
     <span data-ttu-id="6b102-126">當**ssoconfig**備份檔案密碼，提示您輸入的密碼 SSO 組態期間指定。</span><span class="sxs-lookup"><span data-stu-id="6b102-126">When **ssoconfig** prompts you for the backup file password, enter the password that was specified during SSO configuration.</span></span> <span data-ttu-id="6b102-127">如果密碼不正確， **ssoconfig**顯示下列訊息：</span><span class="sxs-lookup"><span data-stu-id="6b102-127">If the password is correct, **ssoconfig** displays the following message:</span></span>  
  
     <span data-ttu-id="6b102-128">**作業已順利完成**</span><span class="sxs-lookup"><span data-stu-id="6b102-128">**The operation completed successfully**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b102-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b102-129">See Also</span></span>  
 <span data-ttu-id="6b102-130">[復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="6b102-130">[Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span></span>  
 [<span data-ttu-id="6b102-131">設定企業 SSO 使用 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="6b102-131">Configuring Enterprise SSO Using the BizTalk Server Configuration</span></span>](http://msdn.microsoft.com/library/f63d1aec-a8c7-4e76-a67f-19af69e252f0)