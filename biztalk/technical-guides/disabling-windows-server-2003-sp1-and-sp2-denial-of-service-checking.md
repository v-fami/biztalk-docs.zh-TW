---
title: 停用 Windows Server 2003 SP1 與 SP2 阻絕服務檢查 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8822c1e4-d146-4361-b25a-7b81cd5cdd3b
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 688ff81133e60d5be5ef2f9d6826b9b6ca93919c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979263"
---
# <a name="disabling-windows-server-2003-sp1-and-sp2-denial-of-service-checking"></a><span data-ttu-id="629fd-102">停用 Windows Server 2003 SP1 與 SP2 阻絕服務檢查</span><span class="sxs-lookup"><span data-stu-id="629fd-102">Disabling Windows Server 2003 SP1 and SP2 Denial of Service Checking</span></span>
> [!NOTE]  
>  <span data-ttu-id="629fd-103">本主題是只適用於 Windows Server 2003。</span><span class="sxs-lookup"><span data-stu-id="629fd-103">This topic is applicable only for Windows Server 2003.</span></span>  
  
 <span data-ttu-id="629fd-104">您應該停用 Windows Server 2003 Service Pack 1 和 Service Pack 2 的阻絕服務檢查。</span><span class="sxs-lookup"><span data-stu-id="629fd-104">You should disable the Windows Server 2003 Service Pack 1 and Service Pack 2 denial of service checking.</span></span> <span data-ttu-id="629fd-105">這是因為在某些高負載情況下，Windows Server 2003 SP1 和 SP2 的阻絕服務檢查可能不正確地識別有效的 TCP/IP 連線為阻絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="629fd-105">This is because under certain high-load scenarios, Windows Server 2003 SP1 and SP2 denial of service checking may incorrectly identify valid TCP/IP connections as a denial of service attack.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="629fd-106">您應該停用這項功能只能在內部網路案例中的，當您確定您將不會發生實際的阻絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="629fd-106">You should disable this feature only in an intranet scenario when you are sure you will not suffer from actual denial of service attacks.</span></span>  
  
## <a name="how-denial-of-service-can-affect-tcpip-connections"></a><span data-ttu-id="629fd-107">阻絕服務可能會如何影響 TCP/IP 連接</span><span class="sxs-lookup"><span data-stu-id="629fd-107">How Denial of Service Can Affect TCP/IP Connections</span></span>  
 <span data-ttu-id="629fd-108">Windows Server 2003 SP1 和 SP2 實作的安全性功能會減少佇列的並行 TCP/IP 連線到伺服器的大小。</span><span class="sxs-lookup"><span data-stu-id="629fd-108">Windows Server 2003 SP1 and SP2 implement a security feature that reduces the size of the queue for concurrent TCP/IP connections to the server.</span></span> <span data-ttu-id="629fd-109">此功能可防止阻絕服務的攻擊。</span><span class="sxs-lookup"><span data-stu-id="629fd-109">This feature helps prevent denial of service attacks.</span></span> <span data-ttu-id="629fd-110">在沈重的負載情況下在 Windows Server 2003 SP1 或更新版本的 TCP/IP 通訊協定可能不正確地識別有效的 TCP/IP 連線為阻絕服務攻擊。</span><span class="sxs-lookup"><span data-stu-id="629fd-110">Under heavy load conditions, the TCP/IP protocol in Windows Server 2003 SP1 or later may incorrectly identify valid TCP/IP connections as a denial of service attack.</span></span> <span data-ttu-id="629fd-111">這可能是因為當[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]負載過重。</span><span class="sxs-lookup"><span data-stu-id="629fd-111">This may occur when [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] is under heavy load.</span></span>  
  
## <a name="modifying-the-registry-entry"></a><span data-ttu-id="629fd-112">修改的登錄項目</span><span class="sxs-lookup"><span data-stu-id="629fd-112">Modifying the Registry Entry</span></span>  
 <span data-ttu-id="629fd-113">如需詳細資訊，請參閱 Microsoft 知識庫文章 899599， ["的 BizTalk Server 主控件執行個體失敗，而且 BizTalk Server 為基礎的伺服器處理大量文件時，將會寫入應用程式記錄檔的 「 一般網路 」 錯誤 」](http://go.microsoft.com/fwlink/?LinkId=158860) (<http://go.microsoft.com/fwlink/?LinkId=158860>).</span><span class="sxs-lookup"><span data-stu-id="629fd-113">For more information, see Microsoft Knowledge Base article 899599, ["A BizTalk Server Host instance fails, and a 'General Network' error is written to the Application log when the BizTalk Server-based server processes a high volume of documents"](http://go.microsoft.com/fwlink/?LinkId=158860) (<http://go.microsoft.com/fwlink/?LinkId=158860>).</span></span> <span data-ttu-id="629fd-114">請遵循這篇文章中的指示，建立**SynAttackProtect**該主控件執行 SQL Server 的電腦上的登錄項目[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]資料庫和執行的任何電腦上[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]執行 Windows Server2003 SP1 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="629fd-114">Follow the instructions in this article to create the **SynAttackProtect** registry entry on computers running SQL Server that host [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] databases and on any computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] that are running Windows Server 2003 SP1 or later.</span></span>  
  
## <a name="tuning-registry-settings-that-govern-the-level-of-denial-of-service-attack-protection"></a><span data-ttu-id="629fd-115">調整控管的阻絕服務攻擊的保護層級的登錄設定</span><span class="sxs-lookup"><span data-stu-id="629fd-115">Tuning Registry Settings that Govern the Level of Denial of Service Attack Protection</span></span>  
 <span data-ttu-id="629fd-116">在某些情況下，您可能想要維護阻斷服務保護，但降低阻絕服務功能套用的積極程度。</span><span class="sxs-lookup"><span data-stu-id="629fd-116">In certain scenarios you may want to maintain denial of service protection but reduce how aggressively the denial of service functionality is applied.</span></span> <span data-ttu-id="629fd-117">您可遵循下列步驟來微調阻斷服務保護功能的預設行為：</span><span class="sxs-lookup"><span data-stu-id="629fd-117">It is possible to tune the default behavior of the denial of service protection feature by following these steps:</span></span>  
  
1.  <span data-ttu-id="629fd-118">請確認**SynAttackProtect** REG_DWORD 值設定登錄項目**1**述[ http://go.microsoft.com/fwlink/?LinkId=111477 ](http://go.microsoft.com/fwlink/?LinkId=111477)。</span><span class="sxs-lookup"><span data-stu-id="629fd-118">Ensure that the **SynAttackProtect** registry entry is set to a REG_DWORD value of **1** as described at [http://go.microsoft.com/fwlink/?LinkId=111477](http://go.microsoft.com/fwlink/?LinkId=111477).</span></span>  
  
2.  <span data-ttu-id="629fd-119">設定**TcpMaxHalfOpen**登錄項目述[ http://go.microsoft.com/fwlink/?LinkId=111478 ](http://go.microsoft.com/fwlink/?LinkId=111478)。</span><span class="sxs-lookup"><span data-stu-id="629fd-119">Configure the **TcpMaxHalfOpen** registry entry as described at [http://go.microsoft.com/fwlink/?LinkId=111478](http://go.microsoft.com/fwlink/?LinkId=111478).</span></span>  
  
3.  <span data-ttu-id="629fd-120">設定**TcpMaxHalfOpenRetried**登錄項目述[ http://go.microsoft.com/fwlink/?LinkId=111479 ](http://go.microsoft.com/fwlink/?LinkId=111479)。</span><span class="sxs-lookup"><span data-stu-id="629fd-120">Configure the **TcpMaxHalfOpenRetried** registry entry as described at [http://go.microsoft.com/fwlink/?LinkId=111479](http://go.microsoft.com/fwlink/?LinkId=111479).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="629fd-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="629fd-121">See Also</span></span>  
 [<span data-ttu-id="629fd-122">作業整備檢查清單</span><span class="sxs-lookup"><span data-stu-id="629fd-122">Operational Readiness Checklists</span></span>](../technical-guides/operational-readiness-checklists.md)