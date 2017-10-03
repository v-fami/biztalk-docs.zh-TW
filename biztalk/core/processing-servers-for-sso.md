---
title: "SSO 的處理伺服器 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO, processing servers
- processing servers [SSO]
ms.assetid: 9e80a456-974a-49b3-bb64-2e4713036cfb
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 972e1a3b01394cbf63fb0c8094586d2beda73c3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="processing-servers-for-sso"></a><span data-ttu-id="7ffb7-102">SSO 的處理伺服器</span><span class="sxs-lookup"><span data-stu-id="7ffb7-102">Processing Servers for SSO</span></span>
<span data-ttu-id="7ffb7-103">在多部電腦的環境中，當主要密碼伺服器與 SSO 資料庫已經建立後，您可以在後續電腦上安裝「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="7ffb7-103">In a multi-computer environment, after the master secret server and SSO database have been created, you can install Enterprise Single Sign-On on subsequent computers.</span></span> <span data-ttu-id="7ffb7-104">一般而言，這些電腦上也會安裝 BizTalk Server 或 Host Integration Server。</span><span class="sxs-lookup"><span data-stu-id="7ffb7-104">These are typically the computers on which either BizTalk Server or Host Integration Server is installed as well.</span></span>  
  
 <span data-ttu-id="7ffb7-105">初始安裝程序與第一部電腦一樣。</span><span class="sxs-lookup"><span data-stu-id="7ffb7-105">The initial installation process is the same as on the first computer.</span></span> <span data-ttu-id="7ffb7-106">不過組態稍微不同。</span><span class="sxs-lookup"><span data-stu-id="7ffb7-106">Configuration, however, becomes slightly different.</span></span> <span data-ttu-id="7ffb7-107">由於主要密碼伺服器與 SSO 資料庫已在進行中，選取**聯結**當 「 組態精靈 」 詢問時，**建立新的 SSO 系統**或**加入現有的系統**.</span><span class="sxs-lookup"><span data-stu-id="7ffb7-107">Since the master secret server and the SSO database are already in place, select **Join** when the Configuration Wizard asks, **Create a new SSO system** or **Join an existing system**.</span></span>  
  
 <span data-ttu-id="7ffb7-108">請注意，在一部電腦上設定群組期間，可以加入其他電腦上並非為此群組所設定的 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7ffb7-108">Note that it is possible during configuration for a group on one computer to join an SSO database on a different computer that is not the database configured for that group.</span></span> <span data-ttu-id="7ffb7-109">雖然這是可行的，但是不建議您這麼做。</span><span class="sxs-lookup"><span data-stu-id="7ffb7-109">While this is possible, it is not recommended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ffb7-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ffb7-110">See Also</span></span>  
 [<span data-ttu-id="7ffb7-111">從舊版的 SSO 升級</span><span class="sxs-lookup"><span data-stu-id="7ffb7-111">Upgrading from a Previous Version of SSO</span></span>](../core/upgrading-from-a-previous-version-of-sso.md)