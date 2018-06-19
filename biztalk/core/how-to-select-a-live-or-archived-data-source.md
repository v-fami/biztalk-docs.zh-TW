---
title: 如何選取即時或封存資料來源 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Management database, archived data
- Management database, real-time data
- HAT, real-time data
- archived data, Management database
- HAT, archived data
- real-time data, HAT
- real-time data, Management database
- archived data, HAT
ms.assetid: e2325823-22e1-4a1a-865b-15757b215b29
caps.latest.revision: 17
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7172a822a71e2b0d7dc621e6c1e11b055b723bd3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22255286"
---
# <a name="how-to-select-a-live-or-archived-data-source"></a><span data-ttu-id="0d1bb-102">如何選取即時或封存的資料來源</span><span class="sxs-lookup"><span data-stu-id="0d1bb-102">How to Select a Live or Archived Data Source</span></span>
<span data-ttu-id="0d1bb-103">BizTalktracking 可讓您存取封存資料和即時資料。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-103">BizTalktracking enables you to access both archived and live data.</span></span> <span data-ttu-id="0d1bb-104">您可以選取即時或封存資料來源從主要**BizTalk Server 管理**節點 BizTalk Server 管理主控台。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-104">You select a live or archived data source from the main **BizTalk Server Administration** node BizTalk Server Administration Console.</span></span>  <span data-ttu-id="0d1bb-105">預設來源是從「BizTalk 管理」資料庫擷取的即時資料。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-105">The default source is live data, retrieved from the BizTalk Management database.</span></span> <span data-ttu-id="0d1bb-106">若您選擇使用封存的資料，則必須選取要使用的適當伺服器與資料庫。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-106">If you choose to work with archived data, you must select the appropriate server/s and database/s with which to work.</span></span>  
  
-   <span data-ttu-id="0d1bb-107">封存資料：分析封存資料可讓您檢查商務及系統這兩者中的趨勢，因為您可以視需要回溯以前的資料。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-107">Archived data: Analyzing archived data enables you to examine trends both in your business and on your system, because you can look as far back as necessary.</span></span> <span data-ttu-id="0d1bb-108">若選取封存資料，則也必須選取包含封存資料的適當 SQL Server 和 SQL 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-108">If you select archived data, you must also select the appropriate SQL Servers and SQL databases that contain the archived data.</span></span>  
  
     <span data-ttu-id="0d1bb-109">封存的資料由所選取指定**連接至現有的追蹤資料庫...**.</span><span class="sxs-lookup"><span data-stu-id="0d1bb-109">Archived data is designated by selecting **Connect to an existing tracking database…**.</span></span>  
  
-   <span data-ttu-id="0d1bb-110">即時資料：分析即時資料可讓您監控協調流程和管線，這樣就能找出及修正開發或執行環境中的問題。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-110">Live data: Analyzing live data enables you to monitor orchestrations and pipelines, so that you can identify and fix problems in the development or staging environment.</span></span> <span data-ttu-id="0d1bb-111">監控即時資料也可以校正系統中的問題，像是訊息遭到擱置的原因。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-111">Monitoring live data also enables you to correct problems in your system, such as why messages are being suspended.</span></span>  
  
     <span data-ttu-id="0d1bb-112">藉由選取指定即時資料**連接至現有的群組...**.</span><span class="sxs-lookup"><span data-stu-id="0d1bb-112">Live data is designated by selecting **Connect to an existing group…**.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0d1bb-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="0d1bb-113">Prerequisites</span></span>  
 <span data-ttu-id="0d1bb-114">您必須以「BizTalk Server 操作員」群組的成員身分登入，才能執行此程序。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-114">You must be logged on as a member of the BizTalk Server Operators group to perform this procedure.</span></span>  
  
### <a name="to-select-live-data"></a><span data-ttu-id="0d1bb-115">選取即時資料</span><span class="sxs-lookup"><span data-stu-id="0d1bb-115">To select live data</span></span>  
  
1.  <span data-ttu-id="0d1bb-116">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-116">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0d1bb-117">按一下主要**BizTalk Server 管理**節點。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-117">Click the main  **BizTalk Server Administration** node.</span></span>  
  
3.  <span data-ttu-id="0d1bb-118">按一下**連接至現有的群組...**</span><span class="sxs-lookup"><span data-stu-id="0d1bb-118">Click **Connect to an existing group…**</span></span>  
  
4.  <span data-ttu-id="0d1bb-119">在**SQL Server 名稱**方塊中，輸入裝載 BizTalk 管理資料庫伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-119">In the **SQL Server name** box, type the name of the server that hosts the BizTalk Management database.</span></span>  
  
5.  <span data-ttu-id="0d1bb-120">在**資料庫名稱**下拉式清單方塊中，選取**BizTalkMgmtDb**。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-120">In the **Database name** drop-down list box, select **BizTalkMgmtDb**.</span></span>  
  
6.  <span data-ttu-id="0d1bb-121">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-121">Click **OK**.</span></span>  
  
### <a name="to-select-archived-data"></a><span data-ttu-id="0d1bb-122">選取封存的資料</span><span class="sxs-lookup"><span data-stu-id="0d1bb-122">To select archived data</span></span>  
  
1.  <span data-ttu-id="0d1bb-123">按一下**啟動**，按一下 **程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下  **BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-123">Click **Start**, click **Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0d1bb-124">按一下主要**BizTalk Server 管理**節點。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-124">Click the main  **BizTalk Server Administration** node.</span></span>  
  
3.  <span data-ttu-id="0d1bb-125">按一下**連接至現有的追蹤資料庫...**</span><span class="sxs-lookup"><span data-stu-id="0d1bb-125">Click **Connect to an existing tracking database…**</span></span>  
  
4.  <span data-ttu-id="0d1bb-126">在**SQL Server 名稱**方塊中，輸入裝載 BizTalk 管理資料庫伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-126">In the **SQL Server name** box, type the name of the server that hosts the BizTalk Management database.</span></span>  
  
5.  <span data-ttu-id="0d1bb-127">在**資料庫名稱**下拉式清單方塊中，選取**BizTalkMgmtDb**。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-127">In the **Database name** drop-down list box, select **BizTalkMgmtDb**.</span></span>  
  
6.  <span data-ttu-id="0d1bb-128">按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0d1bb-128">Click **OK**.</span></span>