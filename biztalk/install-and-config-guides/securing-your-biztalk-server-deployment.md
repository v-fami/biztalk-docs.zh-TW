---
title: 部署的安全性概觀 |Microsoft 文件
description: 關於安全性、 加密、 BizTalk Server 部署中的使用者群組的快速連結
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a1c5a000-9f6b-49db-bd87-8c694240a192
caps.latest.revision: 20
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf5ff5db17739e2db407bdb52bd3f9aad4e61b74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22299542"
---
# <a name="securing-your-biztalk-server-deployment"></a><span data-ttu-id="74828-103">保護 BizTalk Server 部署的安全</span><span class="sxs-lookup"><span data-stu-id="74828-103">Securing Your BizTalk Server Deployment</span></span>
<span data-ttu-id="74828-104">在您完成 BizTalk 的安裝與設定後，本節中的主題將提供關於設定防火牆連接埠、網際網路通訊協定安全性 (IPSec)，以及安全通訊端層 (SSL) 安全性的連結。</span><span class="sxs-lookup"><span data-stu-id="74828-104">The topics in this section provide the links about configuring firewall ports, Internet protocol security (IPSec), and secure sockets layer (SSL) security after you have installed and configured BizTalk.</span></span>  
  
-   <span data-ttu-id="74828-105">如需如何在 Web 伺服器中實作 SSL 的詳細資訊，請參閱 [http://go.microsoft.com/fwlink/p/?LinkId=193059](http://go.microsoft.com/fwlink/p/?LinkId=193059)。</span><span class="sxs-lookup"><span data-stu-id="74828-105">For more information about how to implement SSL in a Web server, see [http://go.microsoft.com/fwlink/p/?LinkId=193059](http://go.microsoft.com/fwlink/p/?LinkId=193059).</span></span>  
  
-   <span data-ttu-id="74828-106">如需如何在 SQL Server 與其用戶端之間啟用加密 (例如，處理伺服器與管理用戶端) 的詳細資訊，請參閱[透明資料加密 (TDE)](https://msdn.microsoft.com/library/bb934049.aspx)。</span><span class="sxs-lookup"><span data-stu-id="74828-106">For more information about how to enable encryption between SQL Server and its clients such as processing servers and administration clients, see [Transparent Data Encryption (TDE)](https://msdn.microsoft.com/library/bb934049.aspx).</span></span>  
  
-   <span data-ttu-id="74828-107">如需如何設定內部部署伺服器的身分識別管理的詳細資訊，請參閱 [Identity Manager ](https://docs.microsoft.com/microsoft-identity-manager/)。</span><span class="sxs-lookup"><span data-stu-id="74828-107">For more information about how to configure identity management for your on-premises servers, see [Identity Manager ](https://docs.microsoft.com/microsoft-identity-manager/).</span></span>  
  
 <span data-ttu-id="74828-108">除了本節中的主題以外，您還應該檢視下列資訊：</span><span class="sxs-lookup"><span data-stu-id="74828-108">In addition to the topics in this section, you should review the following information:</span></span>  
  
-   <span data-ttu-id="74828-109">如需規劃和維護安全部署的概念資訊，請參閱[安全性規劃](../core/planning-for-security.md)。</span><span class="sxs-lookup"><span data-stu-id="74828-109">For conceptual information about planning and maintaining a secure deployment, see [Planning for Security](../core/planning-for-security.md).</span></span>  
  
-   <span data-ttu-id="74828-110">如需設定系統管理員與系統使用者存取權的詳細資訊，請參閱[管理 BizTalk Server 安全性](../core/managing-biztalk-server-security.md)。</span><span class="sxs-lookup"><span data-stu-id="74828-110">For information about configuring access for administrators and system users, see [Managing BizTalk Server Security](../core/managing-biztalk-server-security.md).</span></span>  
  
-   <span data-ttu-id="74828-111">如需 BizTalk Server 安全性功能的詳細資訊，請參閱[安全和保護您的 BizTalk 訊息](../core/secure-and-protect-your-biztalk-messages.md)。</span><span class="sxs-lookup"><span data-stu-id="74828-111">For more information about security features in BizTalk Server, see [Secure and protect your BizTalk messages](../core/secure-and-protect-your-biztalk-messages.md).</span></span>  
  
-   <span data-ttu-id="74828-112">如需如何實作安全性訊息的詳細資訊，請參閱[實作訊息安全性](../core/implementing-message-security.md)。</span><span class="sxs-lookup"><span data-stu-id="74828-112">For more information about how to implement secure messages, see [Implementing Message Security](../core/implementing-message-security.md).</span></span>  
  
-   <span data-ttu-id="74828-113">如需 BizTalk Server 使用的 Windows 群組和使用者帳戶的詳細資訊，請參閱 [BizTalk Server 中的 Windows 群組和使用者帳戶](../core/windows-groups-and-user-accounts-in-biztalk-server.md)。</span><span class="sxs-lookup"><span data-stu-id="74828-113">For more information about Windows groups and user accounts that BizTalk Server uses, see [Windows Groups and User Accounts in BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).</span></span>  
  
## <a name="additional-configuration-topics"></a><span data-ttu-id="74828-114">其他設定主題</span><span class="sxs-lookup"><span data-stu-id="74828-114">Additional Configuration Topics</span></span>  
 
 [<span data-ttu-id="74828-115">設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="74828-115">Configure BizTalk Server</span></span>](../install-and-config-guides/configure-biztalk-server.md)  
  
 [<span data-ttu-id="74828-116">在 Azure VM 上設定 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="74828-116">Configuring BizTalk Server on an Azure VM</span></span>](http://msdn.microsoft.com/library/azure/jj248689.aspx)  
  
[<span data-ttu-id="74828-117">設定叢集中的 BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="74828-117">Configure BizTalk Server in a Cluster</span></span>](../install-and-config-guides/configure-biztalk-server-in-a-cluster.md)
    
  
## <a name="see-also"></a><span data-ttu-id="74828-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74828-118">See Also</span></span>  
 <span data-ttu-id="74828-119">[存取控制和資料安全性](../core/access-control-and-data-security.md) </span><span class="sxs-lookup"><span data-stu-id="74828-119">[Access Control and Data Security](../core/access-control-and-data-security.md) </span></span>  
 <span data-ttu-id="74828-120">[最低安全性使用者權限](../core/minimum-security-user-rights.md) </span><span class="sxs-lookup"><span data-stu-id="74828-120">[Minimum Security User Rights](../core/minimum-security-user-rights.md) </span></span>  
 <span data-ttu-id="74828-121">[安全性規劃](../core/planning-for-security.md) </span><span class="sxs-lookup"><span data-stu-id="74828-121">[Planning for Security](../core/planning-for-security.md) </span></span>  
 [<span data-ttu-id="74828-122">設計 BizTalk Server 的系統架構</span><span class="sxs-lookup"><span data-stu-id="74828-122">Designing the System Architectures for BizTalk Server</span></span>](../core/designing-the-system-architectures-for-biztalk-server.md)   
