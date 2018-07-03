---
title: 如何更新 BAM 成品 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Update-All command [BAM]
- managing [BAM definitions], updating artifacts
- updating, artifacts
- artifacts, updating
ms.assetid: bc28159e-df51-499b-bd51-7b682b849891
caps.latest.revision: 19
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 083940baf4d6e51e15bc91f4ee7e867d50750c83
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011767"
---
# <a name="how-to-update-bam-artifacts"></a><span data-ttu-id="6845e-102">如何更新 BAM 成品</span><span class="sxs-lookup"><span data-stu-id="6845e-102">How to Update BAM Artifacts</span></span>
<span data-ttu-id="6845e-103">系統管理員可以使用**update-all 來**命令來更新部署到 BAM 主要匯入資料庫中的成品。</span><span class="sxs-lookup"><span data-stu-id="6845e-103">Administrators use the **update-all** command to update artifacts deployed in the BAM Primary Import database.</span></span> <span data-ttu-id="6845e-104">提供的 BAM 定義檔案必須是包含所要更新之成品相關資訊的 XML 檔案或 Excel 活頁簿。</span><span class="sxs-lookup"><span data-stu-id="6845e-104">The supplied BAM definition is either an XML file or an Excel Workbook containing information about the artifacts to be updated.</span></span>  
  
### <a name="to-update-bam-artifacts"></a><span data-ttu-id="6845e-105">,若要更新 BAM 成品</span><span class="sxs-lookup"><span data-stu-id="6845e-105">To update BAM Artifacts</span></span>  
  
1. <span data-ttu-id="6845e-106">開啟命令提示字元，如下所示： 按一下**開始**，按一下**執行**，型別**cmd**，然後按一下 **確定**。</span><span class="sxs-lookup"><span data-stu-id="6845e-106">Open a command prompt as follows: Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2. <span data-ttu-id="6845e-107">瀏覽到 [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking。</span><span class="sxs-lookup"><span data-stu-id="6845e-107">Navigate to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking.</span></span>  
  
3. <span data-ttu-id="6845e-108">型別**bm update-all 來-DefinitionFile:\<def 檔\>**。</span><span class="sxs-lookup"><span data-stu-id="6845e-108">Type **bm update-all -DefinitionFile:\<def file\>**.</span></span>  
  
4. <span data-ttu-id="6845e-109">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="6845e-109">Press **ENTER**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6845e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6845e-110">See Also</span></span>  
 <span data-ttu-id="6845e-111">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="6845e-111">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="6845e-112">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="6845e-112">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="6845e-113">BAM 管理公用程式</span><span class="sxs-lookup"><span data-stu-id="6845e-113">BAM Management Utility</span></span>](../core/bam-management-utility.md)