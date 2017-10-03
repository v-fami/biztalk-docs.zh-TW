---
title: "在匯入管理組件之前 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6e3c13dd-613a-4885-a5d2-ad3ee492ff25
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1c11849c379a4654bed78a8e86ba263e6da428c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="before-you-import-the-management-pack"></a><span data-ttu-id="30140-102">匯入管理組件之前</span><span class="sxs-lookup"><span data-stu-id="30140-102">Before You Import the Management Pack</span></span>
<span data-ttu-id="30140-103">最佳做法，您應該匯入 Windows Server 管理組件，您要使用的作業系統。</span><span class="sxs-lookup"><span data-stu-id="30140-103">As a best practice, you should import the Windows Server Management Pack for the operating system that you are using.</span></span> <span data-ttu-id="30140-104">在匯入之前[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]管理組件，採取下列動作：</span><span class="sxs-lookup"><span data-stu-id="30140-104">Before you import the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Management Pack, take the following actions:</span></span>  
  
-   <span data-ttu-id="30140-105">確定已安裝 Operations Manager 2007 R2/2012年。</span><span class="sxs-lookup"><span data-stu-id="30140-105">Ensure that Operations Manager 2007 R2/2012 is installed.</span></span>  
  
-   <span data-ttu-id="30140-106">您必須是 SCOM Administrators 群組或 SCOM 作者群組的成員。</span><span class="sxs-lookup"><span data-stu-id="30140-106">You must be a member of either the SCOM Administrators group or the SCOM Authors group.</span></span> <span data-ttu-id="30140-107">SCOM 管理伺服器上的本機管理員具有所有權利及權限授與給 SCOM Administrators 群組。</span><span class="sxs-lookup"><span data-stu-id="30140-107">Local administrators on the SCOM Management Server have all the rights and permissions that are granted to the SCOM Administrators group.</span></span>  
  
-   <span data-ttu-id="30140-108">設定 BizTalk Server 為 Operations Manager 中的受管理電腦上您想要管理每個 BizTalk Server 的 SCOM 代理程式的部署。</span><span class="sxs-lookup"><span data-stu-id="30140-108">Set up your BizTalk Servers as managed computers in Operations Manager by deploying the SCOM agents on each BizTalk Server that you want to manage.</span></span> <span data-ttu-id="30140-109">SCOM 代理程式部署涉及下列工作：</span><span class="sxs-lookup"><span data-stu-id="30140-109">The SCOM agent deployment involves the following tasks:</span></span>  
  
    -   <span data-ttu-id="30140-110">安裝 SCOM 代理程式。</span><span class="sxs-lookup"><span data-stu-id="30140-110">Install the SCOM agent.</span></span>  
  
    -   <span data-ttu-id="30140-111">建立 BizTalk SCOM 代理程式帳戶。</span><span class="sxs-lookup"><span data-stu-id="30140-111">Create a BizTalk SCOM agent account.</span></span>  
  
    -   <span data-ttu-id="30140-112">設定**執行身分**帳戶。</span><span class="sxs-lookup"><span data-stu-id="30140-112">Configure a **Run As** account.</span></span> <span data-ttu-id="30140-113">將執行身分帳戶加入至下列群組：</span><span class="sxs-lookup"><span data-stu-id="30140-113">Add the Run As account to the following groups:</span></span>  
  
        -   <span data-ttu-id="30140-114">BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="30140-114">BizTalk Groups.</span></span>  
  
        -   <span data-ttu-id="30140-115">BizTalk 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="30140-115">BizTalk Administrators.</span></span>  
  
        -   <span data-ttu-id="30140-116">SSO 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="30140-116">SSO Administrators.</span></span>  
  
        -   <span data-ttu-id="30140-117">SSO 分支機構系統管理員。</span><span class="sxs-lookup"><span data-stu-id="30140-117">SSO Affiliate Administrators.</span></span>  
  
    -   <span data-ttu-id="30140-118">開始監視。</span><span class="sxs-lookup"><span data-stu-id="30140-118">Initiate monitoring.</span></span>  
  
-   <span data-ttu-id="30140-119">在 Operation Manager 主控台中，受管理的電腦處於狀況良好。</span><span class="sxs-lookup"><span data-stu-id="30140-119">In Operation Manager Console, managed computers are in a healthy state.</span></span>  
  
-   <span data-ttu-id="30140-120">設定已設定，例如任何所需的執行身分帳戶或設定檔的任何使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="30140-120">Configure any user accounts that have to be set up, such as any required Run As accounts or profiles.</span></span> <span data-ttu-id="30140-121">此管理組件包含執行身分設定檔名為 「 BizTalk Server 監視帳戶 」 和 「 BizTalk Server 探索帳戶 」 來定義每個代理程式為基礎的特定認證。</span><span class="sxs-lookup"><span data-stu-id="30140-121">This management pack includes Run As profiles named “BizTalk Server Monitoring Account” and “BizTalk Server Discovery Account” to define specific credentials on a per-agent basis.</span></span> <span data-ttu-id="30140-122">您可能要在匯入管理組件之後，某些代理程式使用此執行身分設定檔。</span><span class="sxs-lookup"><span data-stu-id="30140-122">You may have to use this Run As profile for some agents after you import the management pack.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="30140-123">本節內容</span><span class="sxs-lookup"><span data-stu-id="30140-123">In this section</span></span>  
  
-   [<span data-ttu-id="30140-124">此管理組件中的檔案</span><span class="sxs-lookup"><span data-stu-id="30140-124">Files in This Management Pack</span></span>](../technical-guides/files-in-this-management-pack.md)  
  
-   [<span data-ttu-id="30140-125">建議的其他管理組件</span><span class="sxs-lookup"><span data-stu-id="30140-125">Recommended Additional Management Packs</span></span>](../technical-guides/recommended-additional-management-packs.md)