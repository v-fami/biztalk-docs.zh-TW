---
title: 準備災害復原 BizTalk Server |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 14c2c25d-30c5-4e90-a744-f084befa2c1d
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0f9d806f3f757200e425b2f922032cb8f8d26bc6
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36981567"
---
# <a name="preparing-the-disaster-recovery-biztalk-servers"></a><span data-ttu-id="478f7-102">準備災害復原 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="478f7-102">Preparing the Disaster Recovery BizTalk Servers</span></span>
<span data-ttu-id="478f7-103">安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在下列中的建議災害復原站台的執行階段伺服器[BizTalk Server 2010 安裝和升級指南](http://go.microsoft.com/fwlink/?LinkID=194815)(<http://go.microsoft.com/fwlink/?LinkID=194815>)。</span><span class="sxs-lookup"><span data-stu-id="478f7-103">Install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers at the disaster recovery site following the recommendations in [BizTalk Server 2010 Installation and Upgrade Guides](http://go.microsoft.com/fwlink/?LinkID=194815) (<http://go.microsoft.com/fwlink/?LinkID=194815>).</span></span> <span data-ttu-id="478f7-104">設定這些[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]使用 BizTalk 組態精靈 將它們加入實際執行的 BizTalk 群組的執行階段伺服器。</span><span class="sxs-lookup"><span data-stu-id="478f7-104">Configure these [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers using the BizTalk Configuration Wizard to join them to the production BizTalk group.</span></span> <span data-ttu-id="478f7-105">設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在災害復原站台 （包括災害復原企業單一登入主要密碼伺服器） 的執行階段伺服器請務必：</span><span class="sxs-lookup"><span data-stu-id="478f7-105">When configuring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers at the disaster recovery site (including the disaster recovery Enterprise Single Sign-On Master Secret server) make sure to:</span></span>  
  
- <span data-ttu-id="478f7-106">選取  **No** "這是主要密碼伺服器嗎？ 」 問題</span><span class="sxs-lookup"><span data-stu-id="478f7-106">Select **No** to the question “Is this the master secret server?”</span></span>  
  
- <span data-ttu-id="478f7-107">選取 **聯結**問題 「 是否要建立或加入 BizTalk Server 群組？ 」</span><span class="sxs-lookup"><span data-stu-id="478f7-107">Select **Join** to the question “Do you want to create or join a BizTalk Server group?”</span></span>  
  
  <span data-ttu-id="478f7-108">設定之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段嚴重損壞修復伺服器，建立對應至生產環境網站的主控件執行個體，但不會啟動這些主控件執行個體的災害復原網站上的 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="478f7-108">After configuring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time disaster recovery servers, create BizTalk host instances on the disaster recovery site that correspond to the production site host instances, but do not start these host instances.</span></span> <span data-ttu-id="478f7-109">例如，如果生產網站有三個主控件**傳送**，**接收**，並**協調流程**server1、 server2，以及 server3 的執行個體，建立三個對應DRserver1，DRserver2，DRserver3 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="478f7-109">For example, if the production site has three Hosts **Send**, **Receive**, and **Orchestration** with instances on server1, server2, and server3, create three corresponding host instances on DRserver1, DRserver2, DRserver3.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="478f7-110">所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關的 Windows 服務，例如在災害復原站台的規則引擎服務與 BizTalk 主控件執行個體應設為"disabled"在 服務管理員防止執行任何處理災害復原站台。</span><span class="sxs-lookup"><span data-stu-id="478f7-110">All [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related Windows services such as the BizTalk Host Instance and Rules Engine Service at the disaster recovery site should be set to “disabled” in the Services Manager to prevent the disaster recovery site from performing any processing.</span></span>  
  
 <span data-ttu-id="478f7-111">您可以安裝和設定不同數目的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]非生產環境中執行，才會進行災害復原網站中的執行階段伺服器。</span><span class="sxs-lookup"><span data-stu-id="478f7-111">You can install and configure a different number of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers in the disaster recovery site than are running in production.</span></span> <span data-ttu-id="478f7-112">不過，採用這種方法，以避免災害復原事件發生時，多載的災害復原網站中的伺服器時，請務必小心。</span><span class="sxs-lookup"><span data-stu-id="478f7-112">Use caution when taking this approach however, so as to avoid overloading the servers in the disaster recovery site if a disaster recovery event occurs.</span></span> <span data-ttu-id="478f7-113">指令碼完全還原 BizTalk 群組表示的一組資料庫，並執行所有必要的系統變更為 BizTalk 群組之後, 可以加入執行[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]BizTalk 群組的執行階段伺服器。</span><span class="sxs-lookup"><span data-stu-id="478f7-113">Once the BizTalk group as represented by the set of databases is fully restored, and all required system changes are performed for the BizTalk group, scripts can be run to join the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers to the BizTalk group.</span></span>