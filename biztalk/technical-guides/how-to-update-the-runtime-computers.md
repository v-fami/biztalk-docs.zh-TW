---
title: 如何更新執行階段電腦 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 576a7065-04b6-436c-acf9-28c8d6e40107
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca8edb4da6b59c33f87100ee3669bb2472d4350c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/01/2017
ms.locfileid: "26010895"
---
# <a name="how-to-update-the-runtime-computers"></a><span data-ttu-id="ec8ea-102">如何更新執行階段電腦</span><span class="sxs-lookup"><span data-stu-id="ec8ea-102">How to Update the Runtime Computers</span></span>
<span data-ttu-id="ec8ea-103">在目的系統[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]設定執行階段電腦[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]組態精靈，在實際執行環境中執行的生產環境 BizTalk 群組的一部分。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-103">The destination system [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers are configured with the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Configuration Wizard as part of the production BizTalk group running in the production environment.</span></span> <span data-ttu-id="ec8ea-104">嚴重損壞修復環境中還原的實際執行的 BizTalk 群組時，必須在每個更新設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]讓它指向嚴重損壞修復的執行階段電腦[!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)]時若嘗試連接到已還原的執行個體實際執行的 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-104">When the production BizTalk group is restored in the disaster recovery environment, settings must be updated on each [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computer so that it points to the disaster recovery [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instance(s) when it attempts to connect to the restored production BizTalk group.</span></span> <span data-ttu-id="ec8ea-105">在目的系統還原 BizTalk 群組之後，使用下列程序來更新[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-105">After the BizTalk group is restored in the destination system, use the following procedure to update the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers.</span></span>  
  
### <a name="to-update-the-biztalk-server-runtime-computers"></a><span data-ttu-id="ec8ea-106">若要更新 BizTalk Server 執行階段電腦</span><span class="sxs-lookup"><span data-stu-id="ec8ea-106">To update the BizTalk Server runtime computers</span></span>  
  
1.  <span data-ttu-id="ec8ea-107">將編輯的 SampleUpdateInfo.xml 檔案複製至 files\microsoft BizTalk Server\Schema\Restore 目錄，每個 32 位元的 BizTalk server 上或 \Program Files (x86) \Microsoft BizTalk Server\Bins32\Schema\Restore 目錄上每個 64 位元 BizTalk目的系統中的伺服器。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-107">Copy the edited SampleUpdateInfo.xml file to the \Program Files\Microsoft BizTalk Server\Schema\Restore directory on every 32 bit BizTalk server or to the \Program Files (x86)\Microsoft BizTalk Server\Bins32\Schema\Restore directory on every 64 bit BizTalk server in the destination system.</span></span>  
  
2.  <span data-ttu-id="ec8ea-108">每個 BizTalk 伺服器上，開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-108">On each BizTalk server, open a command prompt.</span></span> <span data-ttu-id="ec8ea-109">按一下**啟動**，按一下 **執行**，型別**cmd**，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-109">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec8ea-110">在 64 位元電腦上，您必須開啟 64 位元命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-110">On 64-bit computers, you must open a 64-bit command prompt.</span></span>  
  
3.  <span data-ttu-id="ec8ea-111">在命令提示中，巡覽至 files\microsoft BizTalk Server\Schema\Restore （32 位元的電腦上） 或 （在 64 位元電腦） 上的 \Program 檔案 (x86) \Microsoft BizTalk Server\Bins32\Schema\Restore 並輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ec8ea-111">At the command-prompt, navigate to \Program Files\Microsoft BizTalk Server\Schema\Restore (on 32 bit computers) or to \Program Files (x86)\Microsoft BizTalk Server\Bins32\Schema\Restore (on 64 bit computers) and type this command:</span></span>  
  
    ```  
    cscript UpdateRegistry.vbs SampleUpdateInfo.xml  
    ```  
  
4.  <span data-ttu-id="ec8ea-112">啟用並重新啟動所有 BizTalk 主控件執行個體和 BizTalk 伺服器上其他所有的 BizTalk 服務在目的系統。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-112">Enable and restart all BizTalk Host instances and all other BizTalk Services on the BizTalk servers in the destination system.</span></span>  
  
5.  <span data-ttu-id="ec8ea-113">每個 BizTalk 伺服器上重新啟動 WMI 目的系統中。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-113">Restart WMI on each BizTalk server in the destination system.</span></span> <span data-ttu-id="ec8ea-114">按一下**啟動**，按一下 **執行**，型別**services.msc**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-114">Click **Start**, click **Run**, type **services.msc**, and then click **OK**.</span></span> <span data-ttu-id="ec8ea-115">在**服務**MMC 嵌入式管理單元，以滑鼠右鍵按一下**Windows Management Instrumentation**選取**重新啟動**。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-115">In the **Services** MMC snap-in, right-click **Windows Management Instrumentation** and select **Restart**.</span></span>  
  
6.  <span data-ttu-id="ec8ea-116">每個 BizTalk 伺服器上，開啟[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，以滑鼠右鍵按一下**BizTalk 群組**，然後選取**移除**。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-116">On each BizTalk server, open the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, right-click **BizTalk Group**, and then select **Remove**.</span></span>  
  
7.  <span data-ttu-id="ec8ea-117">以滑鼠右鍵按一下**BizTalk Server 2010 管理**，選取**連接至現有的群組**、 選取的 SQL Server 資料庫執行個體和資料庫對應至 BizTalk 管理資料庫的名稱BizTalk 群組，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-117">Right-click **BizTalk Server 2010 Administration**, select **Connect to Existing Group**, select the SQL Server database instance and database name that corresponds to the BizTalk Management database for the BizTalk group, and then click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ec8ea-118">在更新之後，[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段電腦，您可能也需要更新**SSO 伺服器名稱**示**群組內容**對話方塊可以在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-118">After updating the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime computers, you may also need to update the **SSO Server name** as displayed in the **Group Properties** dialog box available in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="ec8ea-119">若要更新**SSO 伺服器名稱**，啟動[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台中，按一下以展開[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理，以滑鼠右鍵按一下**BizTalk 群組**節點，然後選取**屬性**顯示**一般** 索引標籤[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理主控台。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-119">To update the **SSO Server name**, launch the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console, click to expand [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration, right-click the **BizTalk Group** node and select **Properties** to display the **General** tab of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span> <span data-ttu-id="ec8ea-120">然後，在**SSO 伺服器名稱**文字方塊中，輸入此電腦將會使用存取配接器的組態資訊，然後按一下 企業單一登入伺服器的名稱**確定**。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-120">Then, in the **SSO Server name** textbox, enter the name of the Enterprise Single Sign-On server that this computer will use to access the configuration information for the adapters and click **OK**.</span></span> <span data-ttu-id="ec8ea-121">這是用來連接到 SSO 資料庫之 SSO 伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="ec8ea-121">This is the name of the SSO server used to connect to the SSO database.</span></span>  
  
8.  <span data-ttu-id="ec8ea-122">重新啟動每個 BizTalk 執行階段伺服器上的下列 Windows 服務：</span><span class="sxs-lookup"><span data-stu-id="ec8ea-122">Restart the following Windows services on each BizTalk runtime server:</span></span>  
  
    -   <span data-ttu-id="ec8ea-123">企業 SSO 服務</span><span class="sxs-lookup"><span data-stu-id="ec8ea-123">Enterprise SSO Service</span></span>  
  
    -   <span data-ttu-id="ec8ea-124">規則引擎更新服務</span><span class="sxs-lookup"><span data-stu-id="ec8ea-124">Rule Engine Update Service</span></span>  
  
    -   <span data-ttu-id="ec8ea-125">BizTalk 主控件執行個體</span><span class="sxs-lookup"><span data-stu-id="ec8ea-125">BizTalk Host Instances</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec8ea-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="ec8ea-126">See Also</span></span>  
 [<span data-ttu-id="ec8ea-127">復原執行階段電腦</span><span class="sxs-lookup"><span data-stu-id="ec8ea-127">Recovering the Runtime Computers</span></span>](../technical-guides/recovering-the-runtime-computers.md)