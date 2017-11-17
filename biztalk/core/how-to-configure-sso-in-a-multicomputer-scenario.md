---
title: "如何在多重電腦實例中設定 SSO |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, SSO
- SSO database, clustering
- clustering, Master Secret server
- SSO, configuring
- configuring, Master Secret server
- Master Secret server, clustering
- clustering, SSO database
- Master Secret server, configuring
- SSO, multiple computers
ms.assetid: 4511a03d-96f2-45f0-9891-e8b3e253499c
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45bfa58c1fc11a76109f56938b8e1b43790935f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-sso-in-a-multicomputer-scenario"></a><span data-ttu-id="afb78-102">如何在多重電腦實例中設定 SSO</span><span class="sxs-lookup"><span data-stu-id="afb78-102">How to Configure SSO in a Multicomputer Scenario</span></span>
<span data-ttu-id="afb78-103">本節包含在三部電腦實例中設定「企業單一登入」(SSO) 的指示。</span><span class="sxs-lookup"><span data-stu-id="afb78-103">This section contains instructions for configuring Enterprise Single Sign-On (SSO) in a three-computer scenario.</span></span>  
  
 <span data-ttu-id="afb78-104">在下列實例中，電腦 A 是主要密碼伺服器，電腦 B 是「單一登入」伺服器，而電腦 C 則保存 SSO 資料庫。</span><span class="sxs-lookup"><span data-stu-id="afb78-104">In the following scenario, computer A is the master secret server, computer B is the Single Sign-On server, and computer C holds the SSO database.</span></span> <span data-ttu-id="afb78-105">電腦 B 可做為執行階段伺服器、管理伺服器 (SSO 的管理子服務使用此伺服器以管理 SSO 資料庫) 或對應伺服器 (SSO 的管理與用戶端子服務使用此伺服器以管理對應)。</span><span class="sxs-lookup"><span data-stu-id="afb78-105">Computer B can act as a runtime server, as an administration server (administration sub services of SSO use this server for managing the SSO database), or as a mapping server (administration and client sub services of SSO use this server to manage mappings).</span></span>  
  
 <span data-ttu-id="afb78-106">若您要在環境中新增更多 SSO 伺服器，請遵循設定電腦 B 的步驟。任何新的 SSO 伺服器都將指向現有的 SSO 資料庫，而且不可以做為主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="afb78-106">If you want to add more SSO servers to your environment, follow the steps for configuring computer B. Any new SSO servers will point to the existing SSO database, and cannot be the master secret server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afb78-107">建議您在與「單一登入」伺服器和 SSO 資料庫不同的電腦上設定主要密碼伺服器。</span><span class="sxs-lookup"><span data-stu-id="afb78-107">It is recommended that you configure the master secret server on a different computer from the Single Sign-On server and the SSO database.</span></span>  
  
### <a name="to-configure-the-master-secret-server-and-create-the-sso-database-on-computer-a"></a><span data-ttu-id="afb78-108">若要在電腦 A 設定主要密碼伺服器並建立 SSO 資料庫</span><span class="sxs-lookup"><span data-stu-id="afb78-108">To configure the master secret server and create the SSO database on Computer A</span></span>  
  
1.  <span data-ttu-id="afb78-109">執行 BizTalk Server 自訂安裝，而且只安裝「企業單一登入主要密碼伺服器」元件。</span><span class="sxs-lookup"><span data-stu-id="afb78-109">Perform a custom installation of BizTalk Server, and install only the Enterprise Single Sign-On Master Secret Server component.</span></span>  
  
2.  <span data-ttu-id="afb78-110">執行 [組態精靈]，在主要密碼伺服器上設定 SSO。</span><span class="sxs-lookup"><span data-stu-id="afb78-110">Run the Configuration Wizard to configure SSO on the master secret server.</span></span> <span data-ttu-id="afb78-111">在**組態問題**頁面上，選取選項以**建立新的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="afb78-111">On the **Configuration Questions** page, select the option to **Create a new SSO system**.</span></span>  
  
3.  <span data-ttu-id="afb78-112">在**Windows 帳戶**頁面上，指定 SSO 服務的服務帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="afb78-112">On the **Windows Accounts** page, specify the service account credentials for the SSO service.</span></span> <span data-ttu-id="afb78-113">這必須是 SSO 系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="afb78-113">This must be a member of the SSO Administrators group.</span></span>  
  
4.  <span data-ttu-id="afb78-114">在**資料庫組態**頁面上，指定 SQL Server （電腦 C） 的位置以及 SSO 資料庫 (SSODB) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="afb78-114">On the **Database Configurations** page, specify the location of the SQL Server (computer C) and the name of the SSO database (SSODB).</span></span>  
  
5.  <span data-ttu-id="afb78-115">指定選項以備份主要密碼。</span><span class="sxs-lookup"><span data-stu-id="afb78-115">Specify the options to back up the Master Secret.</span></span>  
  
6.  <span data-ttu-id="afb78-116">完成組態。</span><span class="sxs-lookup"><span data-stu-id="afb78-116">Complete the configuration.</span></span>  
  
### <a name="to-configure-the-sso-server-on-computer-b"></a><span data-ttu-id="afb78-117">在電腦 B 設定 SSO 伺服器</span><span class="sxs-lookup"><span data-stu-id="afb78-117">To configure the SSO server on Computer B</span></span>  
  
1.  <span data-ttu-id="afb78-118">在電腦 B 上安裝「企業單一登入」。</span><span class="sxs-lookup"><span data-stu-id="afb78-118">Install Enterprise Single Sign-On on Computer B.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="afb78-119">這可以是 BizTalk Server 或 Host Integration Server 電腦、Web 伺服器或僅限 SSO 伺服器 (SSO 執行階段元件)。</span><span class="sxs-lookup"><span data-stu-id="afb78-119">This can be a BizTalk Server or Host Integration Server computer, a Web server, or an SSO-only server (SSO runtime components).</span></span>  
  
2.  <span data-ttu-id="afb78-120">執行 [組態精靈] 以設定 SSO。</span><span class="sxs-lookup"><span data-stu-id="afb78-120">Run the Configuration Wizard to configure SSO.</span></span> <span data-ttu-id="afb78-121">在**組態問題**頁面上，選取選項以**加入現有的 SSO 系統**。</span><span class="sxs-lookup"><span data-stu-id="afb78-121">On the **Configuration Questions** page, select the option to **Join an existing SSO system**.</span></span>  
  
3.  <span data-ttu-id="afb78-122">在**Windows 帳戶**頁面上，指定 SSO 服務的服務帳戶認證。</span><span class="sxs-lookup"><span data-stu-id="afb78-122">On the **Windows Accounts** page, specify the service account credentials for the SSO service.</span></span> <span data-ttu-id="afb78-123">這必須是 SSO 系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="afb78-123">This must be a member of the SSO Administrators group.</span></span>  
  
4.  <span data-ttu-id="afb78-124">在**資料庫組態**頁面上，指向 SQL Server （電腦 C） 的位置以及 SSO 資料庫 (SSODB) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="afb78-124">On the **Database Configurations** page, point to the location of the SQL Server (computer C) and the name of the SSO database (SSODB).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb78-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afb78-125">See Also</span></span>  
 <span data-ttu-id="afb78-126">[如何叢集化主要密碼伺服器](../core/how-to-cluster-the-master-secret-server1.md) </span><span class="sxs-lookup"><span data-stu-id="afb78-126">[How to Cluster the Master Secret Server](../core/how-to-cluster-the-master-secret-server1.md) </span></span>  
 [<span data-ttu-id="afb78-127">安裝 SSO</span><span class="sxs-lookup"><span data-stu-id="afb78-127">Installing SSO</span></span>](../core/installing-sso.md)