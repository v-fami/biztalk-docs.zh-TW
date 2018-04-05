---
title: 全域設定 索引標籤 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- btahl7.configurationexplorer.tab.globalsettings
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- Global Settings tab [Configuration Explorer]
- auditing, configuring
ms.assetid: 057189f7-9072-4841-950f-371ba1f73a15
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 022ad14cc93b55c7ad928c06358f2714531b40b8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="global-settings-tab"></a><span data-ttu-id="06bbd-102">全域設定 索引標籤</span><span class="sxs-lookup"><span data-stu-id="06bbd-102">Global Settings Tab</span></span>
<span data-ttu-id="06bbd-103">您使用**通用設定**索引標籤以設定所使用的記錄存放區[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="06bbd-103">You use the **Global Settings** tab to configure the logging store used by [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].</span></span>  
  
 <span data-ttu-id="06bbd-104">在**BTAHL7 Configuration 總管**對話方塊**通用設定**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="06bbd-104">In the **BTAHL7 Configuration Explorer** dialog box, on the **Global Settings** tab, do the following:</span></span>  
  
|<span data-ttu-id="06bbd-105">使用</span><span class="sxs-lookup"><span data-stu-id="06bbd-105">Use this</span></span>|<span data-ttu-id="06bbd-106">動作</span><span class="sxs-lookup"><span data-stu-id="06bbd-106">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="06bbd-107">**WMI**</span><span class="sxs-lookup"><span data-stu-id="06bbd-107">**WMI**</span></span>|<span data-ttu-id="06bbd-108">選取此選項，如果您想要產生[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]BTAHL7 的 Management Instrumentation (WMI) 通知。</span><span class="sxs-lookup"><span data-stu-id="06bbd-108">Select this option if you want to generate [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI) notifications for BTAHL7.</span></span>|  
|<span data-ttu-id="06bbd-109">**SQL**</span><span class="sxs-lookup"><span data-stu-id="06bbd-109">**SQL**</span></span>|<span data-ttu-id="06bbd-110">選取此選項，如果您想要使用[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]為 BTAHL7 您記錄存放區。</span><span class="sxs-lookup"><span data-stu-id="06bbd-110">Select this option if you want to use [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] as your logging store for BTAHL7.</span></span> <span data-ttu-id="06bbd-111">**注意：** BTAHL7 會自動建立所需的記錄，如果它們尚不存在的資料表。</span><span class="sxs-lookup"><span data-stu-id="06bbd-111">**Note:**  BTAHL7 automatically creates the tables required for logging if they do not exist.</span></span>|  
|<span data-ttu-id="06bbd-112">**[SQL Server]**</span><span class="sxs-lookup"><span data-stu-id="06bbd-112">**SQL Server**</span></span>|<span data-ttu-id="06bbd-113">型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]名稱。</span><span class="sxs-lookup"><span data-stu-id="06bbd-113">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] name.</span></span> <span data-ttu-id="06bbd-114">這是必要的當您選取**SQL**選項。</span><span class="sxs-lookup"><span data-stu-id="06bbd-114">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="06bbd-115">允許的長度上限為 64 個字元。</span><span class="sxs-lookup"><span data-stu-id="06bbd-115">The maximum allowed length is 64 characters.</span></span><br /><br /> <span data-ttu-id="06bbd-116">預設的伺服器和資料庫名稱是已設定的 BTAHL7 資料庫。</span><span class="sxs-lookup"><span data-stu-id="06bbd-116">The default server and database name is the configured BTAHL7 database.</span></span>|  
|<span data-ttu-id="06bbd-117">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="06bbd-117">**Database name**</span></span>|<span data-ttu-id="06bbd-118">型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="06bbd-118">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database name.</span></span> <span data-ttu-id="06bbd-119">這是必要的當您選取**SQL**選項。</span><span class="sxs-lookup"><span data-stu-id="06bbd-119">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="06bbd-120">最大允許的長度為 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="06bbd-120">The maximum allowed length is 128 characters.</span></span>|  
|<span data-ttu-id="06bbd-121">**事件記錄檔**</span><span class="sxs-lookup"><span data-stu-id="06bbd-121">**Event Log**</span></span>|<span data-ttu-id="06bbd-122">選取此選項，如果您想要使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]BTAHL7 的記錄存放區為事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="06bbd-122">Select this option if you want to use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log as the logging store for BTAHL7.</span></span> <span data-ttu-id="06bbd-123">您使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器來檢視事件訊息。</span><span class="sxs-lookup"><span data-stu-id="06bbd-123">You use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer to view event messages.</span></span>|