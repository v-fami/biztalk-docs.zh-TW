---
title: "匯入監視管理組件的 BizTalk Server 2013 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bee2bfe9-4eb0-46d4-8eee-75182202080c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c6dff55cce17d9b9159a8eca754f91373621929
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="import-the-biztalk-server-2013-monitoring-management-pack"></a><span data-ttu-id="dd58f-102">匯入監視管理組件的 BizTalk Server 2013</span><span class="sxs-lookup"><span data-stu-id="dd58f-102">Import the BizTalk Server 2013 Monitoring Management Pack</span></span>
<span data-ttu-id="dd58f-103">如需如何匯入管理組件的指示，請參閱 「 如何匯入管理組件[Operations Manager 2007 R2/2012年](http://go.microsoft.com/fwlink/?LinkId=142351)(http://go.microsoft.com/fwlink/?LinkId=142351)。</span><span class="sxs-lookup"><span data-stu-id="dd58f-103">For instructions about how to import a management pack, see How to Import a Management Pack in [Operations Manager 2007 R2/2012](http://go.microsoft.com/fwlink/?LinkId=142351) (http://go.microsoft.com/fwlink/?LinkId=142351).</span></span> <span data-ttu-id="dd58f-104">之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]匯入管理組件，請遵循這些程序來完成初始設定：</span><span class="sxs-lookup"><span data-stu-id="dd58f-104">After the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack is imported, follow these procedures to finish your initial configuration:</span></span>  
  
### <a name="to-configure-the-management-pack"></a><span data-ttu-id="dd58f-105">若要設定的管理組件</span><span class="sxs-lookup"><span data-stu-id="dd58f-105">To configure the management pack</span></span>  
  
1.  <span data-ttu-id="dd58f-106">建立新的管理組件儲存覆寫和其他自訂。</span><span class="sxs-lookup"><span data-stu-id="dd58f-106">Create a new management pack in which you store overrides and other customizations.</span></span>  
  
2.  <span data-ttu-id="dd58f-107">若要啟用代理程式 Proxy 設定，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="dd58f-107">To enable the Agent Proxy setting, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="dd58f-108">開啟 Operations 主控台，然後按一下 [系統管理] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dd58f-108">Open the Operations console and then click the Administration button.</span></span>  
  
    2.  <span data-ttu-id="dd58f-109">在 [系統管理員] 窗格中，按一下**代理程式管理**。</span><span class="sxs-lookup"><span data-stu-id="dd58f-109">In the Administrator pane, click **Agent Managed**.</span></span>  
  
    3.  <span data-ttu-id="dd58f-110">按兩下清單中的代理程式。</span><span class="sxs-lookup"><span data-stu-id="dd58f-110">Double-click an agent in the list.</span></span>  
  
    4.  <span data-ttu-id="dd58f-111">在 [安全性] 索引標籤上選取**允許此代理程式作為 proxy 並探索其他電腦上的受管理的物件**。</span><span class="sxs-lookup"><span data-stu-id="dd58f-111">On the Security tab, select **Allow this agent to act as a proxy and discover managed objects on other computers**.</span></span>  
  
    5.  <span data-ttu-id="dd58f-112">針對每個 BizTalk 伺服器已安裝的代理程式重複步驟 3 到 4。</span><span class="sxs-lookup"><span data-stu-id="dd58f-112">Repeat steps 3 through 4 for each agent that is installed on a BizTalk Server.</span></span>