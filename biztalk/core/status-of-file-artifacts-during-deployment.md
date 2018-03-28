---
title: 在部署期間檔案成品的狀態 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- artifacts, status
- deploying [artifacts], status
ms.assetid: 6d0f7336-c2cb-4aa4-9f1d-55fb85fe78bf
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a1f57716741bb61c7a9f6f012aed14ec04c8e250
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2018
---
# <a name="status-of-file-artifacts-during-deployment"></a><span data-ttu-id="18491-102">部署期間檔案成品的狀態</span><span class="sxs-lookup"><span data-stu-id="18491-102">Status of File Artifacts During Deployment</span></span>
<span data-ttu-id="18491-103">在執行前置或後置處理指令碼時，您可能需要知道在檔案系統上有哪些以檔案為基礎的成品。</span><span class="sxs-lookup"><span data-stu-id="18491-103">You may need to know what file-based artifacts exist on the file system when a pre- or post-processing script executes.</span></span> <span data-ttu-id="18491-104">例如，您可能想要讓後置處理指令碼在解除安裝期間執行，並且要它從檔案系統刪除特定成品檔案。</span><span class="sxs-lookup"><span data-stu-id="18491-104">For example, you might want a post-processing script to run during uninstallation and delete a certain artifact file from the file system.</span></span> <span data-ttu-id="18491-105">以檔案為基礎的成品，除了在 BizTalk 資料庫有其表示之外，在本機檔案系統上也有其檔案。</span><span class="sxs-lookup"><span data-stu-id="18491-105">File-based artifacts are artifacts that can exist as files on the local file system, in addition to their representation in the BizTalk databases.</span></span> <span data-ttu-id="18491-106">以檔案為基礎的成品範例包括 COM 元件、.NET 組件、BizTalk 組件、BAM 成品、臨機操作檔案、指令碼和繫結檔案。</span><span class="sxs-lookup"><span data-stu-id="18491-106">Examples of file-based artifacts are COM components, .NET assemblies, BizTalk assemblies, BAM artifacts, ad hoc files, scripts, and binding files.</span></span>  
  
 <span data-ttu-id="18491-107">下表摘要說明部署程序期間每個時間點的成品檔案狀態。</span><span class="sxs-lookup"><span data-stu-id="18491-107">The following table summarizes the status of the artifact files at each point in the deployment process.</span></span>  
  
|<span data-ttu-id="18491-108">部署程序時間點</span><span class="sxs-lookup"><span data-stu-id="18491-108">Point in the Deployment Process</span></span>|<span data-ttu-id="18491-109">應用程式成品檔案的狀態</span><span class="sxs-lookup"><span data-stu-id="18491-109">Status of Application Artifact Files</span></span>|  
|-------------------------------------|------------------------------------------|  
|<span data-ttu-id="18491-110">安裝前</span><span class="sxs-lookup"><span data-stu-id="18491-110">Pre-installation</span></span>|<span data-ttu-id="18491-111">本機檔案系統上只有 System.BizTalk.File 型別的檔案。\*</span><span class="sxs-lookup"><span data-stu-id="18491-111">Only files of the type System.BizTalk.File exist on the local file system.\*</span></span>|  
|<span data-ttu-id="18491-112">安裝後</span><span class="sxs-lookup"><span data-stu-id="18491-112">Post-installation</span></span>|<span data-ttu-id="18491-113">本機檔案系統上有所有的檔案。\*</span><span class="sxs-lookup"><span data-stu-id="18491-113">All files exist on the local file system.\*</span></span>|  
|<span data-ttu-id="18491-114">解除安裝前</span><span class="sxs-lookup"><span data-stu-id="18491-114">Pre-uninstallation</span></span>|<span data-ttu-id="18491-115">本機檔案系統上有所有的檔案。\*</span><span class="sxs-lookup"><span data-stu-id="18491-115">All files exist on the local file system.\*</span></span>|  
|<span data-ttu-id="18491-116">解除安裝後</span><span class="sxs-lookup"><span data-stu-id="18491-116">Post-uninstallation</span></span>|<span data-ttu-id="18491-117">已從本機檔案系統刪除所有檔案。</span><span class="sxs-lookup"><span data-stu-id="18491-117">All files have been deleted from the local file system.</span></span>|  
|<span data-ttu-id="18491-118">匯入前</span><span class="sxs-lookup"><span data-stu-id="18491-118">Pre-import</span></span>|<span data-ttu-id="18491-119">本機檔案系統上沒有檔案，除非在本機電腦上安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="18491-119">No files exist on the local file system unless the application has been installed on the local computer.</span></span>|  
|<span data-ttu-id="18491-120">匯入後</span><span class="sxs-lookup"><span data-stu-id="18491-120">Post-import</span></span>|<span data-ttu-id="18491-121">本機檔案系統上沒有檔案，除非在本機電腦上安裝應用程式。</span><span class="sxs-lookup"><span data-stu-id="18491-121">No files exist on the local file system unless the application has been installed on the local computer.</span></span>|  
  
 <span data-ttu-id="18491-122">\* 本機檔案系統上的檔案存在，只有當將檔案加入至應用程式時，已指定有效的目的地位置。</span><span class="sxs-lookup"><span data-stu-id="18491-122">\* Files exist on the local file system only if a valid destination location was specified when the file was added to the application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18491-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18491-123">See Also</span></span>  
 [<span data-ttu-id="18491-124">使用前置和後置處理指令碼自訂應用程式部署</span><span class="sxs-lookup"><span data-stu-id="18491-124">Using Pre- and Post-processing Scripts to Customize Application Deployment</span></span>](../core/using-pre-and-post-processing-scripts-to-customize-application-deployment.md)