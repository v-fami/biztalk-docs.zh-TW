---
title: 如何列出 BAM 基礎結構的變更 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- definitions [BAM], listing infrastructure changes
- managing [BAM definitions], listing infrastructure changes
- Get-Changes command [BAM]
- infrastructure, listing changes [BAM]
ms.assetid: 3feacd7d-6f42-4626-835b-0dc3befc9fd6
caps.latest.revision: 23
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4c0d2efc67e4329502b0eac7a11ddbd72f8bcee
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998079"
---
# <a name="how-to-list-changes-to-the-bam-infrastructure"></a><span data-ttu-id="9cdcd-102">如何列出 BAM 基礎結構的變更</span><span class="sxs-lookup"><span data-stu-id="9cdcd-102">How to List Changes to the BAM Infrastructure</span></span>
<span data-ttu-id="9cdcd-103">系統管理員可以使用**取得變更**命令，列出目前已部署 BAM 定義資訊的 BAM 管理公用程式。</span><span class="sxs-lookup"><span data-stu-id="9cdcd-103">Administrators use the **get-changes** command of the BAM Management utility to list current information about a deployed BAM definition.</span></span> <span data-ttu-id="9cdcd-104">您也可以使用 get-changes 命令來列出目前 BAM 主要匯入資料庫中的部署成品。</span><span class="sxs-lookup"><span data-stu-id="9cdcd-104">You can also use the get-changes command to list current deployment artifacts in the BAM Primary Import database.</span></span>  
  
 <span data-ttu-id="9cdcd-105">所列資訊包括成功的部署和解除部署、BAM 定義檔的名稱、BAM 組態檔的名稱、與定義檔關聯之所有活動和檢視的名稱，以及套用變更的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="9cdcd-105">The information includes successful deployments and undeployments, the name of the BAM definition file, the name of the BAM configuration file, the names of all activities and views associated with the definition file, and the user account that applied the change.</span></span> <span data-ttu-id="9cdcd-106">get-changes 清單中顯示部署和定義移除情形及其關聯識別碼。</span><span class="sxs-lookup"><span data-stu-id="9cdcd-106">The get-changes list shows deployments and definition removals with their associated identification numbers.</span></span>  
  
### <a name="to-list-changes-to-the-bam-definition"></a><span data-ttu-id="9cdcd-107">若要列出 BAM 定義的變更</span><span class="sxs-lookup"><span data-stu-id="9cdcd-107">To list changes to the BAM definition</span></span>  
  
1. <span data-ttu-id="9cdcd-108">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="9cdcd-108">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="9cdcd-109">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="9cdcd-109">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3. <span data-ttu-id="9cdcd-110">型別**bm 取得變更。**</span><span class="sxs-lookup"><span data-stu-id="9cdcd-110">Type **bm get-changes.**</span></span>  
  
4. <span data-ttu-id="9cdcd-111">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="9cdcd-111">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdcd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cdcd-112">See Also</span></span>  
 <span data-ttu-id="9cdcd-113">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="9cdcd-113">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="9cdcd-114">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="9cdcd-114">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="9cdcd-115">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="9cdcd-115">BAM Management Utility</span></span>](../core/bam-management-utility.md)