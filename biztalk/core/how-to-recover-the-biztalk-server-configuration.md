---
title: 如何復原 BizTalk Server 組態 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c1d39e50-4296-49c7-bd1e-63b1325af168
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 179ff0690c7c07dcf58bf2d7fd92a885435509cc
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36980335"
---
# <a name="how-to-recover-the-biztalk-server-configuration"></a><span data-ttu-id="0fc3b-102">如何復原 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="0fc3b-102">How to Recover the BizTalk Server Configuration</span></span>
<span data-ttu-id="0fc3b-103">在復原 BizTalk Server 的過程中，您還必須匯入當初安裝 BizTalk Server 時所建立的組態檔。</span><span class="sxs-lookup"><span data-stu-id="0fc3b-103">As part of recovering your BizTalk server, you must also import the configuration file that you created when you installed BizTalk Server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0fc3b-104">必要條件</span><span class="sxs-lookup"><span data-stu-id="0fc3b-104">Prerequisites</span></span>  
 <span data-ttu-id="0fc3b-105">您必須以「系統管理員」群組成員的身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="0fc3b-105">You must be logged on as a member of the Administrators group to perform this procedure.</span></span>  
  
### <a name="to-recover-the-biztalk-server-configuration"></a><span data-ttu-id="0fc3b-106">復原 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="0fc3b-106">To recover the BizTalk Server configuration</span></span>  
  
1. <span data-ttu-id="0fc3b-107">使用「記事本」編輯先前備份的 BizTalk Server 組態檔，然後輸入所有 BizTalk Server 服務的使用者帳戶密碼。</span><span class="sxs-lookup"><span data-stu-id="0fc3b-107">Using Notepad, edit the BizTalk Server configuration file that you previously backed up, and enter the user account passwords for all of the BizTalk Server services.</span></span>  
  
2. <span data-ttu-id="0fc3b-108">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 組態**。</span><span class="sxs-lookup"><span data-stu-id="0fc3b-108">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Configuration**.</span></span>  
  
3. <span data-ttu-id="0fc3b-109">在  **Microsoft BizTalk Server 組態**，按一下**匯入組態**。</span><span class="sxs-lookup"><span data-stu-id="0fc3b-109">In **Microsoft BizTalk Server Configuration**, click **Import Configuration**.</span></span>  
  
    <span data-ttu-id="0fc3b-110">確認所有功能的前面都沒有顯示無效圖示。</span><span class="sxs-lookup"><span data-stu-id="0fc3b-110">Verify that there are no invalidation icons appearing in front of any feature.</span></span> <span data-ttu-id="0fc3b-111">如果有任何功能發生組態錯誤，請立即修正錯誤。</span><span class="sxs-lookup"><span data-stu-id="0fc3b-111">If any of the features have configuration errors, now is the time to correct them.</span></span>  
  
4. <span data-ttu-id="0fc3b-112">按一下 [套用組態]。</span><span class="sxs-lookup"><span data-stu-id="0fc3b-112">Click **Apply Configuration**.</span></span>  
  
    <span data-ttu-id="0fc3b-113">設定完成所有 BizTalk Server 功能之後，請關閉組態視窗。</span><span class="sxs-lookup"><span data-stu-id="0fc3b-113">After all of the BizTalk Server features are configured, close the configuration window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fc3b-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fc3b-114">See Also</span></span>  
 <span data-ttu-id="0fc3b-115">[復原執行 BizTalk Server 的電腦](../core/recovering-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="0fc3b-115">[Recovering a Computer Running BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md) </span></span>  
 [<span data-ttu-id="0fc3b-116">如何備份 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="0fc3b-116">How to Back Up The BizTalk Server Configuration</span></span>](../core/how-to-back-up-the-biztalk-server-configuration.md)