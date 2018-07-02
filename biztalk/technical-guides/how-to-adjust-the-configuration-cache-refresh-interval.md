---
title: 如何調整設定快取重新整理間隔 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 63c6c998-e9c0-48f1-a36a-f1fcb916321b
caps.latest.revision: 3
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a861b6a4b4bc3f60dc2d3a50cb1c27d47e07b46a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985655"
---
# <a name="how-to-adjust-the-configuration-cache-refresh-interval"></a><span data-ttu-id="8f854-102">如何調整設定快取重新整理間隔</span><span class="sxs-lookup"><span data-stu-id="8f854-102">How to Adjust the Configuration Cache Refresh Interval</span></span>
<span data-ttu-id="8f854-103">設定快取重新整理間隔會定義 BizTalk Server 用來更新端點的組態的時間週期。</span><span class="sxs-lookup"><span data-stu-id="8f854-103">The configuration cache refresh interval defines the time period in which BizTalk Server updates the configuration of the endpoints.</span></span> <span data-ttu-id="8f854-104">當您啟動 BizTalk Server 時，BizTalk Server 管理，例如 MessageBox 資料庫、 伺服器屬性、 配接器和到追蹤資料庫的連接中的所有項目會儲存在組態快取中。</span><span class="sxs-lookup"><span data-stu-id="8f854-104">When you start BizTalk Server, all items in BizTalk Server administration, such as MessageBox databases, server properties, adapters, and connections to the Tracking database, are stored in the configuration cache.</span></span> <span data-ttu-id="8f854-105">組態重新整理間隔會重新整理快取中的所有項目。</span><span class="sxs-lookup"><span data-stu-id="8f854-105">All items in the cache are refreshed by the configuration refresh interval.</span></span> <span data-ttu-id="8f854-106">根據預設，這是每隔 60 秒，但伺服器資料庫連線和伺服器屬性除外。</span><span class="sxs-lookup"><span data-stu-id="8f854-106">By default this is every 60 seconds, except for the server database connections and server properties.</span></span> <span data-ttu-id="8f854-107">這表示，如果您變更 BizTalk 群組，例如 SMTP 主機的一般屬性所做的變更會挑選 60 秒內。</span><span class="sxs-lookup"><span data-stu-id="8f854-107">This means that if you change the general properties for a BizTalk group, such as the SMTP host, the changes are picked up within 60 seconds.</span></span> <span data-ttu-id="8f854-108">直到您重新整理，不會反映系統目前開啟的執行個體的 BizTalk Server 管理主控台之外所做的變更。</span><span class="sxs-lookup"><span data-stu-id="8f854-108">System changes made outside the currently open instance of the BizTalk Server Administration console are not reflected until you refresh it.</span></span>  
  
 <span data-ttu-id="8f854-109">設定快取重新整理間隔是 BizTalk 群組屬性的一部分。</span><span class="sxs-lookup"><span data-stu-id="8f854-109">The configuration cache refresh interval is part of the BizTalk group properties.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="8f854-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="8f854-110">Prerequisites</span></span>  
 <span data-ttu-id="8f854-111">若要執行本主題中的程序，您必須為 BizTalk Server 系統管理員群組的成員登入。</span><span class="sxs-lookup"><span data-stu-id="8f854-111">To perform the procedure in this topic, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
### <a name="to-adjust-the-cache-refresh-interval"></a><span data-ttu-id="8f854-112">若要調整快取重新整理間隔</span><span class="sxs-lookup"><span data-stu-id="8f854-112">To adjust the cache refresh interval</span></span>  
  
1. <span data-ttu-id="8f854-113">按一下 **開始**，按一下**所有程式**，按一下  **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="8f854-113">Click **Start**, click **All Programs**, click **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="8f854-114">在主控台樹狀目錄中，依序展開[!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**，以滑鼠右鍵按一下**BizTalk 群組**，然後按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="8f854-114">In the console tree, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, right-click **BizTalk Group**, and then click **Settings**.</span></span>  
  
3. <span data-ttu-id="8f854-115">在 [ **BizTalk 設定儀表板**對話方塊中，選取**一般**] 索引標籤。針對**組態重新整理間隔**屬性，輸入或選取的時間 （以秒為單位），所有項目中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理快取必須設定快取重新整理之間的等候，然後按一下 **[確定]**.</span><span class="sxs-lookup"><span data-stu-id="8f854-115">In the **BizTalk Settings Dashboard** dialog box, select the **General** tab. For the **Configuration refresh interval** property, type or select the time (in seconds) that all items in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] administration cache must wait between configuration cache refreshes, and then click **OK**.</span></span>  
  
   > [!NOTE]  
   >  <span data-ttu-id="8f854-116">重新整理時所涵蓋的項目包括 MessageBox 資料庫、伺服器屬性、配接器，以及追蹤資料庫的連線。</span><span class="sxs-lookup"><span data-stu-id="8f854-116">Items involved in the refresh include the MessageBox databases, server properties, adapters, and connections to the Tracking database.</span></span>  
  
   > [!NOTE]  
   >  <span data-ttu-id="8f854-117">根據預設，設定快取中的所有物件會重新都整理每隔 60 秒，但伺服器資料庫連線和伺服器屬性除外。</span><span class="sxs-lookup"><span data-stu-id="8f854-117">By default, all objects in the configuration cache are refreshed every 60 seconds, except for the server database connections and server properties.</span></span>