---
title: 正在準備嚴重損壞修復 BizTalk Server |Microsoft 文件
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
ms.openlocfilehash: 9379136f0845c7c4c987170747a28bd3c50206c4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22302142"
---
# <a name="preparing-the-disaster-recovery-biztalk-servers"></a><span data-ttu-id="dce02-102">正在準備嚴重損壞修復 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="dce02-102">Preparing the Disaster Recovery BizTalk Servers</span></span>
<span data-ttu-id="dce02-103">安裝[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]遵循中的建議的災害復原站台執行階段伺服器[BizTalk Server 2010 安裝和升級指南](http://go.microsoft.com/fwlink/?LinkID=194815)(http://go.microsoft.com/fwlink/?LinkID=194815)。</span><span class="sxs-lookup"><span data-stu-id="dce02-103">Install [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers at the disaster recovery site following the recommendations in [BizTalk Server 2010 Installation and Upgrade Guides](http://go.microsoft.com/fwlink/?LinkID=194815) (http://go.microsoft.com/fwlink/?LinkID=194815).</span></span> <span data-ttu-id="dce02-104">設定這些[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]加入實際執行的 BizTalk 群組中使用 BizTalk 組態精靈的執行階段伺服器。</span><span class="sxs-lookup"><span data-stu-id="dce02-104">Configure these [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers using the BizTalk Configuration Wizard to join them to the production BizTalk group.</span></span> <span data-ttu-id="dce02-105">設定時[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]在災害復原站台 （包括災害復原企業單一登入主要密碼伺服器） 的執行階段伺服器，請務必：</span><span class="sxs-lookup"><span data-stu-id="dce02-105">When configuring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers at the disaster recovery site (including the disaster recovery Enterprise Single Sign-On Master Secret server) make sure to:</span></span>  
  
-   <span data-ttu-id="dce02-106">選取**否**「 這是主要密碼伺服器嗎？ 」 問題的答案</span><span class="sxs-lookup"><span data-stu-id="dce02-106">Select **No** to the question “Is this the master secret server?”</span></span>  
  
-   <span data-ttu-id="dce02-107">選取**聯結**問題 「 是否要建立或加入 BizTalk Server 群組？ 」</span><span class="sxs-lookup"><span data-stu-id="dce02-107">Select **Join** to the question “Do you want to create or join a BizTalk Server group?”</span></span>  
  
 <span data-ttu-id="dce02-108">設定之後[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行階段嚴重損壞修復伺服器，對應至生產環境網站的主控件執行個體，但不是會啟動這些主控件執行個體的災害復原站台上建立 BizTalk 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="dce02-108">After configuring the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time disaster recovery servers, create BizTalk host instances on the disaster recovery site that correspond to the production site host instances, but do not start these host instances.</span></span> <span data-ttu-id="dce02-109">例如，如果將生產站台具有三個主控件**傳送**，**接收**，和**協調流程**server1 server2，且伺服器 3 上的執行個體，建立三個對應DRserver1，DRserver2，DRserver3 主控件執行個體。</span><span class="sxs-lookup"><span data-stu-id="dce02-109">For example, if the production site has three Hosts **Send**, **Receive**, and **Orchestration** with instances on server1, server2, and server3, create three corresponding host instances on DRserver1, DRserver2, DRserver3.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dce02-110">所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-相關 Windows 服務，例如，規則引擎服務在災害復原站台與 BizTalk 主控件執行個體應設為"disabled"在 服務管理員防止執行任何處理的災害復原站台。</span><span class="sxs-lookup"><span data-stu-id="dce02-110">All [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]-related Windows services such as the BizTalk Host Instance and Rules Engine Service at the disaster recovery site should be set to “disabled” in the Services Manager to prevent the disaster recovery site from performing any processing.</span></span>  
  
 <span data-ttu-id="dce02-111">您可以安裝和設定不同數目的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]災害復原站台比生產環境中正在執行中的執行階段伺服器。</span><span class="sxs-lookup"><span data-stu-id="dce02-111">You can install and configure a different number of [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers in the disaster recovery site than are running in production.</span></span> <span data-ttu-id="dce02-112">不過，採用這個方法，以避免多載在災害復原站台伺服器，如果發生嚴重損壞修復事件時，請務必小心。</span><span class="sxs-lookup"><span data-stu-id="dce02-112">Use caution when taking this approach however, so as to avoid overloading the servers in the disaster recovery site if a disaster recovery event occurs.</span></span> <span data-ttu-id="dce02-113">一旦完全還原所表示的一組資料庫的 BizTalk 群組，並針對 BizTalk 群組所執行的所有必要的系統變更，可以執行指令碼為聯結[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]至 BizTalk 群組的執行階段伺服器。</span><span class="sxs-lookup"><span data-stu-id="dce02-113">Once the BizTalk group as represented by the set of databases is fully restored, and all required system changes are performed for the BizTalk group, scripts can be run to join the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run-time servers to the BizTalk group.</span></span>