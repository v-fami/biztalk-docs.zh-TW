---
title: 如何備份 BizTalk Server 組態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14f89050-c204-4d44-a875-299e690489ef
caps.latest.revision: 12
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad54aba8f8f49adeb8534bdbe28add15f0fe9638
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22247654"
---
# <a name="how-to-back-up-the-biztalk-server-configuration"></a><span data-ttu-id="39453-102">如何備份 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="39453-102">How to Back Up The BizTalk Server Configuration</span></span>
<span data-ttu-id="39453-103">做為備份的一部分[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]，您應該備份執行的電腦相關聯的組態設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="39453-103">As part of backing up [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], you should back up the configuration settings associated with the computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="39453-104">當您遇到硬體失敗而需要更換電腦時，如果預先備有原始組態檔的複本，就能大幅簡化還原程序。</span><span class="sxs-lookup"><span data-stu-id="39453-104">Having a copy of the original configuration file greatly simplifies the restoration process if you have a hardware failure that requires you to replace the computer.</span></span>  
  
 <span data-ttu-id="39453-105">執行每一部電腦的組態設定[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]會儲存在 BizTalk Server 組態管理員 」 建立的 XML 檔案。</span><span class="sxs-lookup"><span data-stu-id="39453-105">The configuration settings for each computer running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] are stored in an XML file created by the BizTalk Server Configuration Manager.</span></span> <span data-ttu-id="39453-106">每當變更 BizTalk Server 組態時，您應該將更新的組態檔匯出至備份位置。</span><span class="sxs-lookup"><span data-stu-id="39453-106">Any time you change the configuration of your BizTalk servers, you should export the updated configuration file to your backup location.</span></span> <span data-ttu-id="39453-107">這有助於確保組態檔可在必須更換 BizTalk Server 的狀況中派上用場。</span><span class="sxs-lookup"><span data-stu-id="39453-107">This helps to ensure that the configuration file is available if you have to replace your BizTalk server.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="39453-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="39453-108">Prerequisites</span></span>  
 <span data-ttu-id="39453-109">您必須以 BizTalk Server 系統管理員群組的成員身分登入，才能執行這個程序。</span><span class="sxs-lookup"><span data-stu-id="39453-109">You must be logged on as a member of the BizTalk Server Administrators group to perform this procedure.</span></span>  
  
### <a name="to-back-up-the-biztalk-server-configuration"></a><span data-ttu-id="39453-110">備份 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="39453-110">To back up the BizTalk Server configuration</span></span>  
  
1.  <span data-ttu-id="39453-111">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft BizTalk Server**，然後按一下  **BizTalk Server 組態**。</span><span class="sxs-lookup"><span data-stu-id="39453-111">Click **Start**, click **All Programs**, click **Microsoft BizTalk Server**, and then click **BizTalk Server Configuration**.</span></span>  
  
2.  <span data-ttu-id="39453-112">在**Microsoft BizTalk Server 組態**，按一下 **匯出組態**。</span><span class="sxs-lookup"><span data-stu-id="39453-112">In **Microsoft BizTalk Server Configuration**, click **Export Configuration**.</span></span>  
  
3.  <span data-ttu-id="39453-113">在**存**對話方塊中，瀏覽至您用來儲存備份的位置。</span><span class="sxs-lookup"><span data-stu-id="39453-113">In the **Save As** dialog box, browse to the location where you store your backups.</span></span>  
  
4.  <span data-ttu-id="39453-114">在**檔案名稱**方塊中，輸入組態檔的名稱，然後按一下**儲存**。</span><span class="sxs-lookup"><span data-stu-id="39453-114">In the **File name** box, type a name for the configuration file, and then click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39453-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="39453-115">See Also</span></span>  
 <span data-ttu-id="39453-116">[備份執行 BizTalk Server 的電腦](../core/backing-up-a-computer-running-biztalk-server.md) </span><span class="sxs-lookup"><span data-stu-id="39453-116">[Backing Up a Computer Running BizTalk Server](../core/backing-up-a-computer-running-biztalk-server.md) </span></span>  
 [<span data-ttu-id="39453-117">如何復原 BizTalk Server 組態</span><span class="sxs-lookup"><span data-stu-id="39453-117">How to Recover the BizTalk Server Configuration</span></span>](../core/how-to-recover-the-biztalk-server-configuration.md)