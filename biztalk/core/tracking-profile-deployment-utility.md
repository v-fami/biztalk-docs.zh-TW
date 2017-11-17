---
title: "追蹤設定檔部署公用程式 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d631b7c-a40f-4cee-88a4-3d932ab7fde0
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c4d261069b83741413e255a3f8bacd6dd9260d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-profile-deployment-utility"></a><span data-ttu-id="2febe-102">追蹤設定檔部署公用程式</span><span class="sxs-lookup"><span data-stu-id="2febe-102">Tracking Profile Deployment Utility</span></span>
<span data-ttu-id="2febe-103">開發人員使用 bttdeploy 公用程式，對 BAM 基礎結構套用或移除追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="2febe-103">Developers use the bttdeploy utility to apply tracking profiles to and remove them from the BAM infrastructure.</span></span> <span data-ttu-id="2febe-104">使用 bttdeploy 公用程式的效用等同於在「追蹤設定檔編輯器」(TPE) 中按一下 [套用追蹤設定檔] 功能表選項。</span><span class="sxs-lookup"><span data-stu-id="2febe-104">Using the bttdeploy utility is functionally equivalent to clicking the Apply Tracking Profile menu option in the Tracking Profile Editor (TPE).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2febe-105">在支援使用者帳戶控制 (UAC) 的系統上，您可能需要使用系統管理權限來執行工具。</span><span class="sxs-lookup"><span data-stu-id="2febe-105">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
 <span data-ttu-id="2febe-106">**使用方式**</span><span class="sxs-lookup"><span data-stu-id="2febe-106">**Usage**</span></span>  
  
 <span data-ttu-id="2febe-107">**bttdeploy.exe [選項] 的檔案名稱**</span><span class="sxs-lookup"><span data-stu-id="2febe-107">**bttdeploy.exe [options] file name**</span></span>  
  
|<span data-ttu-id="2febe-108">選項</span><span class="sxs-lookup"><span data-stu-id="2febe-108">Option</span></span>|<span data-ttu-id="2febe-109">Description</span><span class="sxs-lookup"><span data-stu-id="2febe-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2febe-110">/h 或 /?</span><span class="sxs-lookup"><span data-stu-id="2febe-110">/h or /?</span></span>|<span data-ttu-id="2febe-111">選擇項：顯示 bttdeploy 的語法摘要。</span><span class="sxs-lookup"><span data-stu-id="2febe-111">Optional: Displays the syntax summary for bttdeploy.</span></span>|  
|<span data-ttu-id="2febe-112">/mgdb \<name> [，連接埠] >\\< 資料庫名稱\></span><span class="sxs-lookup"><span data-stu-id="2febe-112">/mgdb \<server name[,port]>\\<database name\></span></span>|<span data-ttu-id="2febe-113">選擇項：指定要套用設定檔的管理伺服器、連接埠及資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="2febe-113">Optional: Specifies the management server, port, and database name to which to apply the profile.</span></span> <span data-ttu-id="2febe-114">**注意：**使用這個參數時，是選擇性的連接埠。</span><span class="sxs-lookup"><span data-stu-id="2febe-114">**Note:**  When using this parameter, the port is optional.</span></span>|  
|<span data-ttu-id="2febe-115">/remove</span><span class="sxs-lookup"><span data-stu-id="2febe-115">/remove</span></span>|<span data-ttu-id="2febe-116">選擇項：指定要從 BAM 資料庫移除追蹤設定檔。</span><span class="sxs-lookup"><span data-stu-id="2febe-116">Optional: Specifies that the tracking profile is to be removed from the BAM database.</span></span>|  
|<span data-ttu-id="2febe-117">filename</span><span class="sxs-lookup"><span data-stu-id="2febe-117">filename</span></span>|<span data-ttu-id="2febe-118">要套用或移除的追蹤設定檔檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="2febe-118">The name of the tracking profile file to apply or remove.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2febe-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2febe-119">See Also</span></span>  
 <span data-ttu-id="2febe-120">[追蹤設定檔編輯器](../core/tracking-profile-editor.md) </span><span class="sxs-lookup"><span data-stu-id="2febe-120">[Tracking Profile Editor](../core/tracking-profile-editor.md) </span></span>  
 [<span data-ttu-id="2febe-121">如何移除被遺棄的追蹤設定檔</span><span class="sxs-lookup"><span data-stu-id="2febe-121">How to Remove Orphaned Tracking Profiles</span></span>](../core/how-to-remove-orphaned-tracking-profiles.md)