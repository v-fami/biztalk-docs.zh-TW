---
title: 全域設定 索引標籤 |Microsoft Docs
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
ms.openlocfilehash: 5c19cfb387ba3cce61d21c467c1c91674204d4c4
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998679"
---
# <a name="global-settings-tab"></a><span data-ttu-id="89a48-102">全域設定 索引標籤</span><span class="sxs-lookup"><span data-stu-id="89a48-102">Global Settings Tab</span></span>
<span data-ttu-id="89a48-103">您使用**全域設定**索引標籤以設定使用的記錄存放區[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="89a48-103">You use the **Global Settings** tab to configure the logging store used by [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].</span></span>  

 <span data-ttu-id="89a48-104">在  **BTAHL7 設定總管**對話方塊的 **全域設定**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="89a48-104">In the **BTAHL7 Configuration Explorer** dialog box, on the **Global Settings** tab, do the following:</span></span>  


|     <span data-ttu-id="89a48-105">使用</span><span class="sxs-lookup"><span data-stu-id="89a48-105">Use this</span></span>      |                                                                                                                                                <span data-ttu-id="89a48-106">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="89a48-106">To do this</span></span>                                                                                                                                                |
|-------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      <span data-ttu-id="89a48-107">**WMI**</span><span class="sxs-lookup"><span data-stu-id="89a48-107">**WMI**</span></span>      |                                                                 <span data-ttu-id="89a48-108">選取此選項，如果您想要產生[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]BTAHL7 的 Management Instrumentation (WMI) 通知。</span><span class="sxs-lookup"><span data-stu-id="89a48-108">Select this option if you want to generate [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI) notifications for BTAHL7.</span></span>                                                                  |
|      <span data-ttu-id="89a48-109">**SQL**</span><span class="sxs-lookup"><span data-stu-id="89a48-109">**SQL**</span></span>      | <span data-ttu-id="89a48-110">選取此選項，如果您想要使用 Microsoft[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]作為 BTAHL7 您記錄存放區。</span><span class="sxs-lookup"><span data-stu-id="89a48-110">Select this option if you want to use Microsoft [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] as your logging store for BTAHL7.</span></span> <span data-ttu-id="89a48-111">**注意：** BTAHL7 會自動建立所需的記錄，如果它們尚不存在的資料表。</span><span class="sxs-lookup"><span data-stu-id="89a48-111">**Note:**  BTAHL7 automatically creates the tables required for logging if they do not exist.</span></span> |
|  <span data-ttu-id="89a48-112">**[SQL Server]**</span><span class="sxs-lookup"><span data-stu-id="89a48-112">**SQL Server**</span></span>   |            <span data-ttu-id="89a48-113">型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]名稱。</span><span class="sxs-lookup"><span data-stu-id="89a48-113">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] name.</span></span> <span data-ttu-id="89a48-114">這是必要的當您選取**SQL**選項。</span><span class="sxs-lookup"><span data-stu-id="89a48-114">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="89a48-115">允許的長度上限為 64 個字元。</span><span class="sxs-lookup"><span data-stu-id="89a48-115">The maximum allowed length is 64 characters.</span></span><br /><br /> <span data-ttu-id="89a48-116">預設的伺服器和資料庫名稱是設定的 BTAHL7 資料庫。</span><span class="sxs-lookup"><span data-stu-id="89a48-116">The default server and database name is the configured BTAHL7 database.</span></span>            |
| <span data-ttu-id="89a48-117">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="89a48-117">**Database name**</span></span> |                                                 <span data-ttu-id="89a48-118">型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="89a48-118">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database name.</span></span> <span data-ttu-id="89a48-119">這是必要的當您選取**SQL**選項。</span><span class="sxs-lookup"><span data-stu-id="89a48-119">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="89a48-120">允許的最大長度為 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="89a48-120">The maximum allowed length is 128 characters.</span></span>                                                 |
|   <span data-ttu-id="89a48-121">**事件記錄檔**</span><span class="sxs-lookup"><span data-stu-id="89a48-121">**Event Log**</span></span>   |                <span data-ttu-id="89a48-122">選取此選項，如果您想要使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]為 BTAHL7 的記錄存放區的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="89a48-122">Select this option if you want to use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log as the logging store for BTAHL7.</span></span> <span data-ttu-id="89a48-123">您使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器來檢視事件訊息。</span><span class="sxs-lookup"><span data-stu-id="89a48-123">You use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer to view event messages.</span></span>                 |

