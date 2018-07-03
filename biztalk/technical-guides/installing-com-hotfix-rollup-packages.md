---
title: 安裝 COM + Hotfix 彙總套件 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 587ae3da-db65-4da8-9d3b-89effb91b197
caps.latest.revision: 2
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 110dced7d3931e1987ccf966efffb700e1c5555b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37020516"
---
# <a name="installing-com-hotfix-rollup-packages"></a><span data-ttu-id="59cfd-102">安裝 COM + Hotfix 彙總套件</span><span class="sxs-lookup"><span data-stu-id="59cfd-102">Installing COM+ Hotfix Rollup Packages</span></span>
> [!NOTE]  
>  <span data-ttu-id="59cfd-103">本主題是只適用於 Windows Server 2003。</span><span class="sxs-lookup"><span data-stu-id="59cfd-103">This topic is applicable only for Windows Server 2003.</span></span>  
  
 <span data-ttu-id="59cfd-104">您應該安裝最新版的 Windows Server 2003 COM + hotfix 彙總套件和 Distributed Transaction Coordinator (DTC) 彙總套件的最新版本。</span><span class="sxs-lookup"><span data-stu-id="59cfd-104">You should install the last version of the Windows Server 2003 COM+ hotfix rollup package and latest version of the Distributed Transaction Coordinator (DTC) rollup package.</span></span> <span data-ttu-id="59cfd-105">這是因為封裝包含許多效能和穩定性修正。</span><span class="sxs-lookup"><span data-stu-id="59cfd-105">This is because the packages include many performance and stability fixes.</span></span>  
  
 <span data-ttu-id="59cfd-106">您應該執行的所有電腦上安裝這些彙總套件[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]和執行 SQL Server 上的所有電腦。</span><span class="sxs-lookup"><span data-stu-id="59cfd-106">You should install these rollups on all computers running [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and on all computers running SQL Server.</span></span> <span data-ttu-id="59cfd-107">彙總套件是您在高輸送量的狀況下順利執行的 BizTalk 解決方案特別重要。</span><span class="sxs-lookup"><span data-stu-id="59cfd-107">The rollups are especially important for your BizTalk solution to perform well in high-throughput scenarios.</span></span>  
  
 <span data-ttu-id="59cfd-108">已修正的 DTC 問題如下所示：</span><span class="sxs-lookup"><span data-stu-id="59cfd-108">The DTC issues that have been fixed are as follows:</span></span>  
  
- <span data-ttu-id="59cfd-109">未預期的 DTC 關機</span><span class="sxs-lookup"><span data-stu-id="59cfd-109">Unexpected DTC shutdown</span></span>  
  
- <span data-ttu-id="59cfd-110">記憶體片段相關的問題</span><span class="sxs-lookup"><span data-stu-id="59cfd-110">Memory fragmentation issues</span></span>  
  
- <span data-ttu-id="59cfd-111">DTC 可能會停止回應負載</span><span class="sxs-lookup"><span data-stu-id="59cfd-111">DTC may stop responding under load</span></span>  
  
- <span data-ttu-id="59cfd-112">DTC 可能會造成流失記憶體，或搭配使用時停止回應 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59cfd-112">DTC may leak memory or stop responding when used with [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]</span></span>  
  
- <span data-ttu-id="59cfd-113">DTC 的負載下的效能已改善</span><span class="sxs-lookup"><span data-stu-id="59cfd-113">Performance of DTC under load has been improved</span></span>  
  
## <a name="installing-the-com-rollup-package"></a><span data-ttu-id="59cfd-114">安裝 COM + 彙總套件</span><span class="sxs-lookup"><span data-stu-id="59cfd-114">Installing the COM+ Rollup Package</span></span>  
 <span data-ttu-id="59cfd-115">COM + 已不再發行彙總套件。</span><span class="sxs-lookup"><span data-stu-id="59cfd-115">COM+ is no longer releasing rollup packages.</span></span> <span data-ttu-id="59cfd-116">請遵循這項資訊來安裝最後一個的 COM + 封裝：</span><span class="sxs-lookup"><span data-stu-id="59cfd-116">Follow this information to install the last COM+ package:</span></span>  
  
-   <span data-ttu-id="59cfd-117">COM + 彙總套件的最終版本是"Windows Server 2003 Post-service Pack 2 COM + 1.5 Hotfix 彙總套件 12年"。</span><span class="sxs-lookup"><span data-stu-id="59cfd-117">The final version of the COM+ rollup is the “Windows Server 2003 Post-Service Pack 2 COM+ 1.5 Hotfix Rollup Package 12”.</span></span> <span data-ttu-id="59cfd-118">任何版本的 Windows Server 2003，即使未安裝 service pack 會安裝此 hotfix。</span><span class="sxs-lookup"><span data-stu-id="59cfd-118">This hotfix will install on any version of Windows Server 2003, even those without a service pack installed.</span></span> <span data-ttu-id="59cfd-119">此 hotfix 的詳細資訊可在 Microsoft 知識庫文件 934016， [「 可用性的 Windows Server 2003 Post-service Pack 2 COM + 1.5 Hotfix 彙總套件 12年"](http://go.microsoft.com/fwlink/?LinkId=158756) (http://go.microsoft.com/fwlink/?LinkId=158756)。</span><span class="sxs-lookup"><span data-stu-id="59cfd-119">More information about this hotfix can be found in Microsoft Knowledge Base article 934016, ["Availability of Windows Server 2003 Post-Service Pack 2 COM+ 1.5 Hotfix Rollup Package 12"](http://go.microsoft.com/fwlink/?LinkId=158756) (http://go.microsoft.com/fwlink/?LinkId=158756).</span></span>  
  
## <a name="installing-the-dtc-rollup-package"></a><span data-ttu-id="59cfd-120">安裝 DTC 的彙總套件</span><span class="sxs-lookup"><span data-stu-id="59cfd-120">Installing the DTC Rollup Package</span></span>  
 <span data-ttu-id="59cfd-121">DTC 會發行為獨立的 COM + 的彙總套件。</span><span class="sxs-lookup"><span data-stu-id="59cfd-121">DTC will be releasing rollup packages independent of COM+.</span></span> <span data-ttu-id="59cfd-122">請遵循這項資訊來安裝最新的 DTC 套件：</span><span class="sxs-lookup"><span data-stu-id="59cfd-122">Follow this information to install the latest DTC package:</span></span>  
  
-   <span data-ttu-id="59cfd-123">撰寫本文時為最新的 DTC hotfix 彙總套件會是 「 套件 16 」。</span><span class="sxs-lookup"><span data-stu-id="59cfd-123">As of this writing, the latest DTC hotfix rollup is “Package 16”.</span></span> <span data-ttu-id="59cfd-124">此 hotfix 的詳細資訊可在 Microsoft 知識庫文件 958013， [「 Windows Server 2003 MS DTC Hotfix 彙總套件 16 中所修正的 MS DTC 問題清單 」](http://support.microsoft.com/kb/979919) (http://support.microsoft.com/kb/979919)。</span><span class="sxs-lookup"><span data-stu-id="59cfd-124">More information about this hotfix can be found in Microsoft Knowledge Base article 958013, ["List of the MS DTC issues that are fixed in Windows Server 2003 MS DTC Hotfix Rollup Package 16"](http://support.microsoft.com/kb/979919) (http://support.microsoft.com/kb/979919).</span></span>  
  
     <span data-ttu-id="59cfd-125">搜尋，即可找到有關最新的 DTC hotfix 彙總套件知識庫文章[ http://support.microsoft.com ](http://support.microsoft.com/)片語 （包括引號）：</span><span class="sxs-lookup"><span data-stu-id="59cfd-125">The KB article about the latest DTC hotfix rollup package can be found by searching [http://support.microsoft.com](http://support.microsoft.com/) for the phrase (including the quotes):</span></span>  
  
    ```  
    "MS DTC Hotfix Rollup Package"  
    ```  
  
     <span data-ttu-id="59cfd-126">下列查詢會為您的這項搜尋。</span><span class="sxs-lookup"><span data-stu-id="59cfd-126">The following query does this search for you.</span></span> <span data-ttu-id="59cfd-127">選擇最新的密碼：</span><span class="sxs-lookup"><span data-stu-id="59cfd-127">Choose the latest one:</span></span>  
  
     [<span data-ttu-id="59cfd-128">http://support.microsoft.com/search/default.aspx?query="MS+DTC+Hotfix+Rollup+Package"</span><span class="sxs-lookup"><span data-stu-id="59cfd-128">http://support.microsoft.com/search/default.aspx?query="MS+DTC+Hotfix+Rollup+Package"</span></span>](http://support.microsoft.com/search/default.aspx?query=%22MS+DTC+Hotfix+Rollup+Package%22)