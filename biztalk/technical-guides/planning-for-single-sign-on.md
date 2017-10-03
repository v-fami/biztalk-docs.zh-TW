---
title: "單一登入規劃 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d1bc220-4087-4603-ac15-6bb0c62c59d4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0bc35c53193ac8e48c9169131b637dc1d7a581fc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="planning-for-single-sign-on"></a><span data-ttu-id="4d48f-102">規劃 單一登入</span><span class="sxs-lookup"><span data-stu-id="4d48f-102">Planning for Single Sign-On</span></span>
<span data-ttu-id="4d48f-103">企業單一登入 (SSO) 時的重要元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境。</span><span class="sxs-lookup"><span data-stu-id="4d48f-103">Enterprise Single Sign-On (SSO) is a critical component of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment.</span></span> <span data-ttu-id="4d48f-104">[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行的階段無法運作，而 SSO 服務，因為所有[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]配接器組態資訊會加密並儲存在 SSO 資料庫和[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]存取這項資訊透過 SSO 服務。</span><span class="sxs-lookup"><span data-stu-id="4d48f-104">The [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] run time cannot function without the SSO service because all [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] adapter configuration information is encrypted and stored in the SSO database and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] accesses this information via the SSO service.</span></span> <span data-ttu-id="4d48f-105">如果 SSO 服務不會執行 BizTalk server 上，或如果 SSO 服務並沒有 SSO 主要密碼伺服器的存取，不能存取此配接器組態資訊。</span><span class="sxs-lookup"><span data-stu-id="4d48f-105">This adapter configuration information is not accessible if the SSO service is not running on the BizTalk server or if the SSO service does not have access to the SSO master secret server.</span></span>  
  
 <span data-ttu-id="4d48f-106">SSO 實作應該包含下列的計劃。</span><span class="sxs-lookup"><span data-stu-id="4d48f-106">Your SSO implementation should include the following plans.</span></span>  
  
## <a name="backing-up-the-master-secret"></a><span data-ttu-id="4d48f-107">備份主要密碼</span><span class="sxs-lookup"><span data-stu-id="4d48f-107">Backing Up the Master Secret</span></span>  
 <span data-ttu-id="4d48f-108">如果 SSO 主要密碼伺服器失敗且遺失金鑰，或者是金鑰損毀，您將無法擷取儲存在 SSO 資料庫中的資料。</span><span class="sxs-lookup"><span data-stu-id="4d48f-108">If the SSO master secret server fails and you lose the key, or if the key becomes corrupted, you will not be able to retrieve data stored in the SSO database.</span></span> <span data-ttu-id="4d48f-109">您必須備份主要密碼，否則會有遺失 SSO 資料庫資料的風險。</span><span class="sxs-lookup"><span data-stu-id="4d48f-109">You must back up the master secret, or you risk losing data from the SSO database.</span></span> <span data-ttu-id="4d48f-110">因此務必絕對 SSO 主要密碼已備份，以及儲存在安全的位置。</span><span class="sxs-lookup"><span data-stu-id="4d48f-110">Therefore it is absolutely critical that the SSO master secret is backed up and stored in a secure location.</span></span> <span data-ttu-id="4d48f-111">如需 SSO 主要密碼備份的詳細資訊，請參閱[如何重新設定主要密碼](http://go.microsoft.com/fwlink/?LinkId=151395)(http://go.microsoft.com/fwlink/?LinkId=151395)。</span><span class="sxs-lookup"><span data-stu-id="4d48f-111">For information about backing up the SSO master secret, see [How to Back Up the Master Secret](http://go.microsoft.com/fwlink/?LinkId=151395) (http://go.microsoft.com/fwlink/?LinkId=151395).</span></span>  
  
## <a name="configuring-sso-for-high-availability"></a><span data-ttu-id="4d48f-112">設定 SSO 的高可用性</span><span class="sxs-lookup"><span data-stu-id="4d48f-112">Configuring SSO for High Availability</span></span>  
 <span data-ttu-id="4d48f-113">因為 SSO 是讓這類的重要元件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]環境中，SSO 主要密碼伺服器應設定為高可用性。</span><span class="sxs-lookup"><span data-stu-id="4d48f-113">Because SSO is such a critical component of a [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] environment, the SSO master secret server should be configured for high availability.</span></span> <span data-ttu-id="4d48f-114">如果可能的話，應該叢集企業單一登入服務主要密碼伺服器上的依照下列中的步驟[叢集主要密碼伺服器](../technical-guides/clustering-the-master-secret-server.md)。</span><span class="sxs-lookup"><span data-stu-id="4d48f-114">If at all possible, the Enterprise Single Sign-On service on the master secret server should be clustered by following the steps in [Clustering the Master Secret Server](../technical-guides/clustering-the-master-secret-server.md).</span></span> <span data-ttu-id="4d48f-115">您無法存取 Windows Server 叢集，所以您仍然可以提供企業單一登入服務主要密碼伺服器上的高可用性依照主題中說明的步驟[指定新的主機密碼伺服器手動](../technical-guides/designating-a-new-master-secret-server-manually.md)。</span><span class="sxs-lookup"><span data-stu-id="4d48f-115">In the event that you do not have access to a Windows Server cluster, you can still provide high availability for the Enterprise Single Sign-On service on the master secret server by following the steps documented in the topic [Designating a New Master Secret Server Manually](../technical-guides/designating-a-new-master-secret-server-manually.md).</span></span>  
  
## <a name="following-established-sso-security-recommendations"></a><span data-ttu-id="4d48f-116">下列已建立的 SSO 安全性建議</span><span class="sxs-lookup"><span data-stu-id="4d48f-116">Following Established SSO Security Recommendations</span></span>  
 <span data-ttu-id="4d48f-117">請依照下列主題所述的 SSO 安全性建議[SSO 安全性建議](http://go.microsoft.com/fwlink/?LinkId=155753)(http://go.microsoft.com/fwlink/?LinkId=155753)。</span><span class="sxs-lookup"><span data-stu-id="4d48f-117">Follow SSO security recommendations described in the topic [SSO Security Recommendations](http://go.microsoft.com/fwlink/?LinkId=155753) (http://go.microsoft.com/fwlink/?LinkId=155753).</span></span>