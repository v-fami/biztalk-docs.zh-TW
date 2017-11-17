---
title: "無法取得資料庫或伺服器名稱 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0590f43b-0aec-491f-bca5-c50ab12552a5
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 16c694acdc78b704eb6f2578df99239442fd897e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="could-not-get-the-database-or-the-server-names"></a><span data-ttu-id="10255-102">無法取得資料庫或伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="10255-102">Could not get the database or the server names</span></span>
## <a name="details"></a><span data-ttu-id="10255-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="10255-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="10255-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="10255-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="10255-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="10255-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="10255-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="10255-106">Event ID</span></span>|-|  
|<span data-ttu-id="10255-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="10255-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="10255-108">EDI</span><span class="sxs-lookup"><span data-stu-id="10255-108"> EDI</span></span>|  
|<span data-ttu-id="10255-109">元件</span><span class="sxs-lookup"><span data-stu-id="10255-109">Component</span></span>|<span data-ttu-id="10255-110">EDI 引擎</span><span class="sxs-lookup"><span data-stu-id="10255-110">EDI Engine</span></span>|  
|<span data-ttu-id="10255-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="10255-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="10255-112">訊息文字</span><span class="sxs-lookup"><span data-stu-id="10255-112">Message Text</span></span>|<span data-ttu-id="10255-113">無法取得資料庫或伺服器名稱</span><span class="sxs-lookup"><span data-stu-id="10255-113">Could not get the database or the server names</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="10255-114">說明</span><span class="sxs-lookup"><span data-stu-id="10255-114">Explanation</span></span>  
 <span data-ttu-id="10255-115">此錯誤表示 BizTalk 無法從登錄讀取 BizTalkMgmtDb 名稱和伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="10255-115">This error indicates BizTalk could not read the BizTalkMgmtDb name and Server name from registry.</span></span> <span data-ttu-id="10255-116">這項錯誤的可能原因在於未設定 BizTalk 群組。</span><span class="sxs-lookup"><span data-stu-id="10255-116">One possible reason for this error is the BizTalk Group is not configured.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="10255-117">使用者動作</span><span class="sxs-lookup"><span data-stu-id="10255-117">User Action</span></span>  
 <span data-ttu-id="10255-118">若要解決這個錯誤，請設定 BizTalk 群組：</span><span class="sxs-lookup"><span data-stu-id="10255-118">To resolve this error, configure the BizTalk Group:</span></span>  
  
1.  <span data-ttu-id="10255-119">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="10255-119">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="10255-120">展開 [主控台根目錄] 中的 [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="10255-120">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)].</span></span>  
  
3.  <span data-ttu-id="10255-121">以滑鼠右鍵按一下**BizTalk 群組**。</span><span class="sxs-lookup"><span data-stu-id="10255-121">Right-click **BizTalk Group**.</span></span>  
  
4.  <span data-ttu-id="10255-122">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="10255-122">Click **Properties**.</span></span>  
  
5.  <span data-ttu-id="10255-123">在左窗格中，按一下 **一般**。</span><span class="sxs-lookup"><span data-stu-id="10255-123">In the left pane, click **General**.</span></span>  
  
6.  <span data-ttu-id="10255-124">確認**伺服器**名稱和**資料庫**名稱正確無誤。</span><span class="sxs-lookup"><span data-stu-id="10255-124">Verify the **Server** name and **Database** name are correct.</span></span>