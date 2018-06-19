---
title: 如何部署追蹤設定檔與追蹤設定檔管理公用程式 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracking profiles, deploying
- deploying, tracking profiles
- bttdeploy.exe [BAM]
- managing [BAM], deploying tracking profiles
ms.assetid: b3023379-cae1-45fc-a773-2660d3e4abf1
caps.latest.revision: 15
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2dde3f351c583be9037127c060d02c98d12b2fcb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
ms.locfileid: "25970116"
---
# <a name="how-to-deploy-tracking-profiles-with-the-tracking-profiles-management-utility"></a><span data-ttu-id="ab7bb-102">如何使用追蹤設定檔管理公用程式部署追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ab7bb-102">How to Deploy Tracking Profiles with the Tracking Profiles Management Utility</span></span>
<span data-ttu-id="ab7bb-103">商務經理人會要求方案開發人員建立新的追蹤設定檔或修改現有的設定檔，加強對組織特定商務程序的管理與監控。</span><span class="sxs-lookup"><span data-stu-id="ab7bb-103">A business manager asks a solutions developer to create a new tracking profile or modify an existing one to better manage and monitor a specific business process for your organization.</span></span>  
  
 <span data-ttu-id="ab7bb-104">方案開發人員使用追蹤設定檔編輯器 (TPE) 定義商務分析師需要的資料。</span><span class="sxs-lookup"><span data-stu-id="ab7bb-104">The solutions developer uses the Tracking Profile Editor (TPE) to define the data that the business analyst requires.</span></span>  
  
 <span data-ttu-id="ab7bb-105">方案開發人員建立或修改追蹤設定檔之後，系統管理員可以使用 bttdeploy.exe 命令列公用程式進行部署，以便使方案開發人員所做的變更生效並開始收集資料。</span><span class="sxs-lookup"><span data-stu-id="ab7bb-105">After a solutions developer creates or modifies the tracking profile, an administrator uses the bttdeploy.exe command line utility to deploy it so that the changes take affect and the data is collected.</span></span> <span data-ttu-id="ab7bb-106">方案開發人員可以使用 TPE 部署追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="ab7bb-106">The solutions developer can deploy tracking profiles with the TPE.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ab7bb-107">您必須部署追蹤設定檔才能部署追蹤設定檔關聯的組件。</span><span class="sxs-lookup"><span data-stu-id="ab7bb-107">You must deploy the assemblies associated with the tracking profile before you deploy the tracking profile.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ab7bb-108">您必須使用此工具的 BizTalk® 系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="ab7bb-108">You must have BizTalk® Administrator privileges to use this tool.</span></span>  
  
### <a name="to-deploy-the-tracking-profile-from-the-command-line-utility"></a><span data-ttu-id="ab7bb-109">若要從命令列公用程式部署追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="ab7bb-109">To deploy the tracking profile from the command-line utility</span></span>  
  
1.  <span data-ttu-id="ab7bb-110">從命令提示字元中，移動到目錄\<安裝路徑\>\Program Files\Microsoft BizTalk Server\<版本\>\Tracking\\。</span><span class="sxs-lookup"><span data-stu-id="ab7bb-110">From a command prompt, move to the directory \<installation path\>\Program Files\Microsoft BizTalk Server \<version\>\Tracking\\.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ab7bb-111">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="ab7bb-111">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
2.  <span data-ttu-id="ab7bb-112">型別**bttdeploy.exe\<設定檔名稱\>.btt**。</span><span class="sxs-lookup"><span data-stu-id="ab7bb-112">Type **bttdeploy.exe \<profile name\>.btt**.</span></span>  
  
3.  <span data-ttu-id="ab7bb-113">按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="ab7bb-113">Press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab7bb-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="ab7bb-114">See Also</span></span>  
 <span data-ttu-id="ab7bb-115">[管理 BAM 動態基礎結構](../core/managing-the-bam-dynamic-infrastructure.md) </span><span class="sxs-lookup"><span data-stu-id="ab7bb-115">[Managing the BAM Dynamic Infrastructure](../core/managing-the-bam-dynamic-infrastructure.md) </span></span>  
 <span data-ttu-id="ab7bb-116">[BAM 安全性建議](../core/bam-security-recommendations.md) </span><span class="sxs-lookup"><span data-stu-id="ab7bb-116">[BAM Security Recommendations](../core/bam-security-recommendations.md) </span></span>  
 [<span data-ttu-id="ab7bb-117">商務活動監控 (BAM)</span><span class="sxs-lookup"><span data-stu-id="ab7bb-117">Business Activity Monitoring (BAM)</span></span>](../core/business-activity-monitoring-bam.md)