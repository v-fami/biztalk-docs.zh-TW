---
title: 單一登入： 事件 10748 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b4b18ea-6565-4c0b-89f8-30a8c67601ba
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7d83f0bfec0137e0788b55ca6aa5857f3dcfcc50
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276502"
---
# <a name="single-sign-on-event-10748"></a><span data-ttu-id="dc81f-102">單一登入： 事件 10748</span><span class="sxs-lookup"><span data-stu-id="dc81f-102">Single Sign-On: Event 10748</span></span>
## <a name="details"></a><span data-ttu-id="dc81f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="dc81f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dc81f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="dc81f-104">Product Name</span></span>|<span data-ttu-id="dc81f-105">企業單一登入</span><span class="sxs-lookup"><span data-stu-id="dc81f-105">Enterprise Single Sign-On</span></span>|  
|<span data-ttu-id="dc81f-106">產品版本</span><span class="sxs-lookup"><span data-stu-id="dc81f-106">Product Version</span></span>|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|<span data-ttu-id="dc81f-107">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="dc81f-107">Event ID</span></span>|<span data-ttu-id="dc81f-108">10748</span><span class="sxs-lookup"><span data-stu-id="dc81f-108">10748</span></span>|  
|<span data-ttu-id="dc81f-109">事件來源</span><span class="sxs-lookup"><span data-stu-id="dc81f-109">Event Source</span></span>|<span data-ttu-id="dc81f-110">ENTSSO</span><span class="sxs-lookup"><span data-stu-id="dc81f-110">ENTSSO</span></span>|  
|<span data-ttu-id="dc81f-111">元件</span><span class="sxs-lookup"><span data-stu-id="dc81f-111">Component</span></span>|<span data-ttu-id="dc81f-112">N\A</span><span class="sxs-lookup"><span data-stu-id="dc81f-112">N\A</span></span>|  
|<span data-ttu-id="dc81f-113">符號名稱</span><span class="sxs-lookup"><span data-stu-id="dc81f-113">Symbolic Name</span></span>|<span data-ttu-id="dc81f-114">SSO_WARN_PS_ADAPTER_NOT_RUNNING</span><span class="sxs-lookup"><span data-stu-id="dc81f-114">SSO_WARN_PS_ADAPTER_NOT_RUNNING</span></span>|  
|<span data-ttu-id="dc81f-115">訊息文字</span><span class="sxs-lookup"><span data-stu-id="dc81f-115">Message Text</span></span>|<span data-ttu-id="dc81f-116">無法連絡目的地配接器。</span><span class="sxs-lookup"><span data-stu-id="dc81f-116">Could not contact the destination adapter.</span></span><br /><br /> <span data-ttu-id="dc81f-117">它可能無法執行或 initialized.%r</span><span class="sxs-lookup"><span data-stu-id="dc81f-117">It may not be running or initialized.%r</span></span><br /><br /> <span data-ttu-id="dc81f-118">追蹤識別碼: %1 %r</span><span class="sxs-lookup"><span data-stu-id="dc81f-118">Tracking ID: %1%r</span></span><br /><br /> <span data-ttu-id="dc81f-119">配接器: %2 %r</span><span class="sxs-lookup"><span data-stu-id="dc81f-119">Adapter: %2%r</span></span><br /><br /> <span data-ttu-id="dc81f-120">SSO 伺服器名稱: %3 %r</span><span class="sxs-lookup"><span data-stu-id="dc81f-120">SSO Server Name: %3%r</span></span><br /><br /> <span data-ttu-id="dc81f-121">錯誤碼： %4</span><span class="sxs-lookup"><span data-stu-id="dc81f-121">Error Code: %4</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="dc81f-122">說明</span><span class="sxs-lookup"><span data-stu-id="dc81f-122">Explanation</span></span>  
 <span data-ttu-id="dc81f-123">這個警告事件表示密碼同步處理無法連絡指定的密碼同步配接器。</span><span class="sxs-lookup"><span data-stu-id="dc81f-123">This Warning event indicates that Password Synchronization could not contact the specified password sync adapter.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="dc81f-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="dc81f-124">User Action</span></span>  
 <span data-ttu-id="dc81f-125">若要解決這個警告，請執行下列一或多個動作：</span><span class="sxs-lookup"><span data-stu-id="dc81f-125">To resolve this warning, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="dc81f-126">請檢查外部介面卡。</span><span class="sxs-lookup"><span data-stu-id="dc81f-126">Check the external adapter.</span></span>  
  
-   <span data-ttu-id="dc81f-127">您可以使用 MMC 嵌入式管理單元或命令列工具來啟用配接器。</span><span class="sxs-lookup"><span data-stu-id="dc81f-127">Use the MMC Snap-In or command line tools to enable the adapter.</span></span>  
  
-   <span data-ttu-id="dc81f-128">請檢查系統和應用程式事件日誌中的相關錯誤。</span><span class="sxs-lookup"><span data-stu-id="dc81f-128">Check the system and application event logs for associated errors.</span></span>  
  
 <span data-ttu-id="dc81f-129">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="dc81f-129">For more information, see the following resources:</span></span>  
  
-   [<span data-ttu-id="dc81f-130">如何管理密碼同步處理</span><span class="sxs-lookup"><span data-stu-id="dc81f-130">How to Administer Password Synchronization</span></span>](../core/how-to-administer-password-synchronization.md)