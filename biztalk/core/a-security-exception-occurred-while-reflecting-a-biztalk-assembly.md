---
title: "反映 BizTalk 組件時發生安全性例外狀況 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 301b85c7-8e67-482e-8666-67a91ca5c73d
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cca28c534b910479be3ae6ad26bd1e0a27a1637d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="a-security-exception-occurred-while-reflecting-a-biztalk-assembly"></a><span data-ttu-id="e97a4-102">反映 BizTalk 組件時發生安全性例外狀況</span><span class="sxs-lookup"><span data-stu-id="e97a4-102">A security exception occurred while reflecting a BizTalk assembly</span></span>
## <a name="details"></a><span data-ttu-id="e97a4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e97a4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e97a4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e97a4-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="e97a4-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="e97a4-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="e97a4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e97a4-106">Event ID</span></span>|<span data-ttu-id="e97a4-107">0</span><span class="sxs-lookup"><span data-stu-id="e97a4-107">0</span></span>|  
|<span data-ttu-id="e97a4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="e97a4-108">Event Source</span></span>|<span data-ttu-id="e97a4-109">0</span><span class="sxs-lookup"><span data-stu-id="e97a4-109">0</span></span>|  
|<span data-ttu-id="e97a4-110">元件</span><span class="sxs-lookup"><span data-stu-id="e97a4-110">Component</span></span>|<span data-ttu-id="e97a4-111">0</span><span class="sxs-lookup"><span data-stu-id="e97a4-111">0</span></span>|  
|<span data-ttu-id="e97a4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e97a4-112">Symbolic Name</span></span>|<span data-ttu-id="e97a4-113">0</span><span class="sxs-lookup"><span data-stu-id="e97a4-113">0</span></span>|  
|<span data-ttu-id="e97a4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e97a4-114">Message Text</span></span>|<span data-ttu-id="e97a4-115">反映 BizTalk 組件 "{0}" 時發生安全性例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e97a4-115">A security exception occurred while reflecting BizTalk assembly "{0}".</span></span> <span data-ttu-id="e97a4-116">組件若位於共用的網路資料夾時，可能會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="e97a4-116">This problem may occur if the assembly is located in a shared network folder.</span></span> <span data-ttu-id="e97a4-117">若要修正這個問題，請嘗試下列其中一種： 1。</span><span class="sxs-lookup"><span data-stu-id="e97a4-117">To correct this problem, try one of the following: 1.</span></span> <span data-ttu-id="e97a4-118">將組件與其相依項目複製到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="e97a4-118">Copy the assembly and its dependencies to the local machine.</span></span> <span data-ttu-id="e97a4-119">2.</span><span class="sxs-lookup"><span data-stu-id="e97a4-119">2.</span></span> <span data-ttu-id="e97a4-120">調整.NET 組態的執行階段安全性原則以允許存取。</span><span class="sxs-lookup"><span data-stu-id="e97a4-120">Adjust the .NET Configuration Runtime Security policy to permit access.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e97a4-121">說明</span><span class="sxs-lookup"><span data-stu-id="e97a4-121">Explanation</span></span>  
 <span data-ttu-id="e97a4-122">嘗試發行不正確的.NET 原則的網路共用上的 BizTalk 組件時，會發生這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e97a4-122">This error will occur when trying to publish a BizTalk assembly that is on a network share without the right .NET policy.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e97a4-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e97a4-123">User Action</span></span>  
 <span data-ttu-id="e97a4-124">除了錯誤訊息中所述的特定步驟，將複製本機的組件。</span><span class="sxs-lookup"><span data-stu-id="e97a4-124">In addition to taking the specific steps outlined in the error message, copy the assembly locally.</span></span> <span data-ttu-id="e97a4-125">或編輯原則以授與完全信任近端內部網路。</span><span class="sxs-lookup"><span data-stu-id="e97a4-125">Or edit the policy to grant full trust to the local intranet.</span></span>  
  
 <span data-ttu-id="e97a4-126">**使用程式碼存取安全性原則工具 (Caspol.exe)**</span><span class="sxs-lookup"><span data-stu-id="e97a4-126">**Using the Code Access Security Policy Tool (Caspol.exe)**</span></span>  
  
 <span data-ttu-id="e97a4-127">您可以在使用者層級，與一般使用者權限在本機電腦上授與信任的資料夾。</span><span class="sxs-lookup"><span data-stu-id="e97a4-127">You can grant trust to a folder on your local computer at the User level with normal user permissions.</span></span> <span data-ttu-id="e97a4-128">若要將信任授與網路位置，您必須具有系統管理員權限，並變更電腦層級的安全性原則。</span><span class="sxs-lookup"><span data-stu-id="e97a4-128">To grant trust to a network location, you must have administrator privileges and change the security policy at the Machine level.</span></span> <span data-ttu-id="e97a4-129">電腦原則層級做獨立於使用者原則層級，而電腦原則層級不授與完全信任給內部網路區域即使使用者原則。</span><span class="sxs-lookup"><span data-stu-id="e97a4-129">The Machine policy level acts independently of the User policy level, and the machine policy level does not grant full trust to the Intranet zone even if the User policy does.</span></span> <span data-ttu-id="e97a4-130">原則層級必須一致。</span><span class="sxs-lookup"><span data-stu-id="e97a4-130">The policy levels must agree.</span></span>  
  
 <span data-ttu-id="e97a4-131">**若要授與完全信任的本機資料夾**</span><span class="sxs-lookup"><span data-stu-id="e97a4-131">**To grant full trust to a local folder**</span></span>  
  
-   <span data-ttu-id="e97a4-132">在 Visual Studio 命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="e97a4-132">Type the following command in the Visual Studio Command Prompt:</span></span>  
  
```  
caspol -u -ag All_Code -url   
C:\<FolderName>\<FolderName>\* FullTrust -n "<Name>" -d  
"<Description>"  
```  
  
 <span data-ttu-id="e97a4-133">**若要授與完全信任的網路資料夾**</span><span class="sxs-lookup"><span data-stu-id="e97a4-133">**To grant full trust to a network folder**</span></span>  
  
-   <span data-ttu-id="e97a4-134">在 Visual Studio 命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="e97a4-134">Type the following command in the Visual Studio Command Prompt:</span></span>  
  
```  
caspol -m -ag LocalIntranet_Zone -url   
\\<ServerName>\<FolderName>\* FullTrust -n "<Name>" -d   
"<Description>"  
```