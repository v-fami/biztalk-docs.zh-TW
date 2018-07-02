---
title: 手動指定新的主要密碼伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3fa44143-8d29-49ba-9c71-96be2c9ded67
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2b9453ade3d447e874609d1357e2383a5c21686f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36975095"
---
# <a name="designating-a-new-master-secret-server-manually"></a><span data-ttu-id="b3afc-102">手動指定新的主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="b3afc-102">Designating a New Master Secret Server Manually</span></span>
<span data-ttu-id="b3afc-103">叢集的硬體可能十分昂貴。</span><span class="sxs-lookup"><span data-stu-id="b3afc-103">Cluster hardware can be expensive.</span></span> <span data-ttu-id="b3afc-104">如果硬體成本方面的問題，您可以考慮以手動方式指定為主要密碼伺服器期間的失敗案例的另一個企業單一登入 (SSO) 伺服器。</span><span class="sxs-lookup"><span data-stu-id="b3afc-104">If hardware cost is a concern, you can consider manually designating another Enterprise Single Sign-On (SSO) server to be the master secret server during failure scenarios.</span></span> <span data-ttu-id="b3afc-105">使用此選項，在 [SSO] 群組中的任何其他 SSO 伺服器可以提升為主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="b3afc-105">Using this option, any other SSO server in the SSO group can be promoted to the master secret server.</span></span> <span data-ttu-id="b3afc-106">當主要已關閉時，您可以手動升級其中一部 SSO 伺服器，為主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="b3afc-106">When the master is down, you can manually promote one of the SSO servers to be the master secret server.</span></span> <span data-ttu-id="b3afc-107">這項技術的最大的缺點是，您無法編輯現有的部署，重新啟動現有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]服務，或部署新的 BizTalk 應用程式，直到您升級新的主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="b3afc-107">The biggest disadvantage of this technique is that you cannot edit the existing deployments, restart the existing [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] services, or deploy new BizTalk applications until you promote a new master secret server.</span></span>  
  
 <span data-ttu-id="b3afc-108">若要讓無縫式的程序，您必須實作一些監視機制，讓您將會儘速探索失敗。</span><span class="sxs-lookup"><span data-stu-id="b3afc-108">To make the process seamless, you will need to implement some monitoring mechanism so you will discover the failure as soon as possible.</span></span> <span data-ttu-id="b3afc-109">您也可以使用監視的應用程式，例如 System Center Operations Manager，以自動化升級程序。</span><span class="sxs-lookup"><span data-stu-id="b3afc-109">You can also automate the promotion process by using a monitoring application such as System Center Operations Manager.</span></span>  
  
 <span data-ttu-id="b3afc-110">如需有關如何以手動方式將主要密碼伺服器的詳細資訊，請參閱 <<c0> [ 如何移動主要密碼伺服器](http://go.microsoft.com/fwlink/?LinkId=156841)(<http://go.microsoft.com/fwlink/?LinkId=156841>) 中[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。</span><span class="sxs-lookup"><span data-stu-id="b3afc-110">For more information about manually moving the master secret server, see [How to Move the Master Secret Server](http://go.microsoft.com/fwlink/?LinkId=156841) (<http://go.microsoft.com/fwlink/?LinkId=156841>) in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Help.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3afc-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3afc-111">See Also</span></span>  
 [<span data-ttu-id="b3afc-112">叢集主要密碼伺服器</span><span class="sxs-lookup"><span data-stu-id="b3afc-112">Clustering the Master Secret Server</span></span>](../technical-guides/clustering-the-master-secret-server.md)