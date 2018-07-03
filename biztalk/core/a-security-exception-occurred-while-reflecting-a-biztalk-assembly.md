---
title: 反映 BizTalk 組件時發生安全性例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 301b85c7-8e67-482e-8666-67a91ca5c73d
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d07b1e5788ae696e94a3bbe326f2cfe79d1b76f
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36979927"
---
# <a name="a-security-exception-occurred-while-reflecting-a-biztalk-assembly"></a><span data-ttu-id="2237b-102">反映 BizTalk 組件時發生安全性例外狀況</span><span class="sxs-lookup"><span data-stu-id="2237b-102">A security exception occurred while reflecting a BizTalk assembly</span></span>
## <a name="details"></a><span data-ttu-id="2237b-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2237b-103">Details</span></span>  
  
|                 |                                                                                                                                                                                                                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="2237b-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2237b-104">Product Name</span></span>   |                                                                                                                                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                                                                                                 |
| <span data-ttu-id="2237b-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="2237b-105">Product Version</span></span> |                                                                                                                                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                                                                                                             |
|    <span data-ttu-id="2237b-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2237b-106">Event ID</span></span>     |                                                                                                                                                                         <span data-ttu-id="2237b-107">0</span><span class="sxs-lookup"><span data-stu-id="2237b-107">0</span></span>                                                                                                                                                                          |
|  <span data-ttu-id="2237b-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="2237b-108">Event Source</span></span>   |                                                                                                                                                                         <span data-ttu-id="2237b-109">0</span><span class="sxs-lookup"><span data-stu-id="2237b-109">0</span></span>                                                                                                                                                                          |
|    <span data-ttu-id="2237b-110">元件</span><span class="sxs-lookup"><span data-stu-id="2237b-110">Component</span></span>    |                                                                                                                                                                         <span data-ttu-id="2237b-111">0</span><span class="sxs-lookup"><span data-stu-id="2237b-111">0</span></span>                                                                                                                                                                          |
|  <span data-ttu-id="2237b-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2237b-112">Symbolic Name</span></span>  |                                                                                                                                                                         <span data-ttu-id="2237b-113">0</span><span class="sxs-lookup"><span data-stu-id="2237b-113">0</span></span>                                                                                                                                                                          |
|  <span data-ttu-id="2237b-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2237b-114">Message Text</span></span>   | <span data-ttu-id="2237b-115">反映 BizTalk 組件時發生安全性例外狀況 」{0}"。</span><span class="sxs-lookup"><span data-stu-id="2237b-115">A security exception occurred while reflecting BizTalk assembly "{0}".</span></span> <span data-ttu-id="2237b-116">組件若位於共用的網路資料夾時，可能會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="2237b-116">This problem may occur if the assembly is located in a shared network folder.</span></span> <span data-ttu-id="2237b-117">若要更正這個問題，請嘗試下列其中之一： 1。</span><span class="sxs-lookup"><span data-stu-id="2237b-117">To correct this problem, try one of the following: 1.</span></span> <span data-ttu-id="2237b-118">將組件與其相依項目複製到本機電腦。</span><span class="sxs-lookup"><span data-stu-id="2237b-118">Copy the assembly and its dependencies to the local machine.</span></span> <span data-ttu-id="2237b-119">2.</span><span class="sxs-lookup"><span data-stu-id="2237b-119">2.</span></span> <span data-ttu-id="2237b-120">調整.NET 組態的執行階段安全性原則以允許存取。</span><span class="sxs-lookup"><span data-stu-id="2237b-120">Adjust the .NET Configuration Runtime Security policy to permit access.</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="2237b-121">說明</span><span class="sxs-lookup"><span data-stu-id="2237b-121">Explanation</span></span>  
 <span data-ttu-id="2237b-122">嘗試發行不正確的.NET 原則的網路共用上的 BizTalk 組件時，會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="2237b-122">This error will occur when trying to publish a BizTalk assembly that is on a network share without the right .NET policy.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2237b-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2237b-123">User Action</span></span>  
 <span data-ttu-id="2237b-124">除了錯誤訊息中所述的特定步驟，複製 在本機的組件。</span><span class="sxs-lookup"><span data-stu-id="2237b-124">In addition to taking the specific steps outlined in the error message, copy the assembly locally.</span></span> <span data-ttu-id="2237b-125">或編輯原則，以授與完全信任近端內部網路。</span><span class="sxs-lookup"><span data-stu-id="2237b-125">Or edit the policy to grant full trust to the local intranet.</span></span>  
  
 <span data-ttu-id="2237b-126">**使用程式碼存取安全性原則工具 (Caspol.exe)**</span><span class="sxs-lookup"><span data-stu-id="2237b-126">**Using the Code Access Security Policy Tool (Caspol.exe)**</span></span>  
  
 <span data-ttu-id="2237b-127">您可以在本機電腦一般使用者權限的使用者層級來授與資料夾的信任。</span><span class="sxs-lookup"><span data-stu-id="2237b-127">You can grant trust to a folder on your local computer at the User level with normal user permissions.</span></span> <span data-ttu-id="2237b-128">授與信任的網路位置，您必須具有系統管理員權限，並變更電腦層級的安全性原則。</span><span class="sxs-lookup"><span data-stu-id="2237b-128">To grant trust to a network location, you must have administrator privileges and change the security policy at the Machine level.</span></span> <span data-ttu-id="2237b-129">電腦原則層級可獨立於使用者原則層級，以及電腦原則層級不授予完全信任之內部網路區域，即使使用者原則的。</span><span class="sxs-lookup"><span data-stu-id="2237b-129">The Machine policy level acts independently of the User policy level, and the machine policy level does not grant full trust to the Intranet zone even if the User policy does.</span></span> <span data-ttu-id="2237b-130">原則層級必須同意。</span><span class="sxs-lookup"><span data-stu-id="2237b-130">The policy levels must agree.</span></span>  
  
 <span data-ttu-id="2237b-131">**若要授與完全信任的本機資料夾**</span><span class="sxs-lookup"><span data-stu-id="2237b-131">**To grant full trust to a local folder**</span></span>  
  
-   <span data-ttu-id="2237b-132">在 Visual Studio 命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="2237b-132">Type the following command in the Visual Studio Command Prompt:</span></span>  
  
```  
caspol -u -ag All_Code -url   
C:\<FolderName>\<FolderName>\* FullTrust -n "<Name>" -d  
"<Description>"  
```  
  
 <span data-ttu-id="2237b-133">**若要授與完全信任的網路資料夾**</span><span class="sxs-lookup"><span data-stu-id="2237b-133">**To grant full trust to a network folder**</span></span>  
  
-   <span data-ttu-id="2237b-134">在 Visual Studio 命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="2237b-134">Type the following command in the Visual Studio Command Prompt:</span></span>  
  
```  
caspol -m -ag LocalIntranet_Zone -url   
\\<ServerName>\<FolderName>\* FullTrust -n "<Name>" -d   
"<Description>"  
```