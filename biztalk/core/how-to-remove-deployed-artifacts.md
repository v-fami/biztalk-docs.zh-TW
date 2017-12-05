---
title: "如何移除已部署的成品 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [BAM definitions], undeploying artifacts
- Remove-All command
- undeploying, artifacts [BAM]
- artifacts, undeploying [BAM]
ms.assetid: 90135965-d18e-4a71-9877-d2b0c3caf59f
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f1d3e395223840dd4caa534130061fac33e89b78
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-remove-deployed-artifacts"></a><span data-ttu-id="15ac1-102">如何移除已部署的成品</span><span class="sxs-lookup"><span data-stu-id="15ac1-102">How to Remove Deployed Artifacts</span></span>
<span data-ttu-id="15ac1-103">系統管理員使用**移除 all**命令移除 BAM 主要匯入資料庫中所部署的成品。</span><span class="sxs-lookup"><span data-stu-id="15ac1-103">Administrators use the **remove-all** command to remove artifacts deployed in the BAM Primary Import database.</span></span> <span data-ttu-id="15ac1-104">提供的 BAM 定義檔案必須是包含所要移除之成品相關資訊的 XML 檔案或 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="15ac1-104">The supplied BAM definition is either an XML file or an Excel Workbook containing information about the artifacts to be removed.</span></span>  
  
### <a name="to-remove-deployed-artifacts"></a><span data-ttu-id="15ac1-105">移除已部署的成品</span><span class="sxs-lookup"><span data-stu-id="15ac1-105">To remove deployed artifacts</span></span>  
  
1.  <span data-ttu-id="15ac1-106">開啟命令提示字元，如下所示： 按一下**啟動**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="15ac1-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="15ac1-107">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="15ac1-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3.  <span data-ttu-id="15ac1-108">型別**bm 移除 all-DefinitionFile:\<def 檔\>**。</span><span class="sxs-lookup"><span data-stu-id="15ac1-108">Type **bm remove-all -DefinitionFile:\<def file\>**.</span></span>  
  
4.  <span data-ttu-id="15ac1-109">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="15ac1-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15ac1-110">請參閱</span><span class="sxs-lookup"><span data-stu-id="15ac1-110">See Also</span></span>  
 <span data-ttu-id="15ac1-111">[如何將 BAM 成品新增至應用程式](../core/how-to-add-a-bam-artifact-to-an-application.md) </span><span class="sxs-lookup"><span data-stu-id="15ac1-111">[How to Add a BAM Artifact to an Application](../core/how-to-add-a-bam-artifact-to-an-application.md) </span></span>  
 <span data-ttu-id="15ac1-112">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="15ac1-112">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="15ac1-113">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="15ac1-113">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="15ac1-114">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="15ac1-114">BAM Management Utility</span></span>](../core/bam-management-utility.md)