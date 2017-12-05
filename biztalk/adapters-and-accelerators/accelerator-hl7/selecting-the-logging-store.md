---
title: "選取記錄存放區 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- auditing, configuring
ms.assetid: 6ba64c59-3a15-4c10-b44f-18e0e432c6d3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0518b536db16d641b77a61cfeb4851990a7bca0a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="selecting-the-logging-store"></a><span data-ttu-id="48abe-102">選取記錄存放區</span><span class="sxs-lookup"><span data-stu-id="48abe-102">Selecting the Logging Store</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="48abe-103">[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]選項，例如選取多種不同的記錄存放區中，為您提供[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]Management Instrumentation (WMI) [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，和[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="48abe-103"> [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] provides you with the option to select a combination of different logging stores, such as [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI), [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], and [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log.</span></span>  
  
 <span data-ttu-id="48abe-104">您使用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管來設定記錄存放區。</span><span class="sxs-lookup"><span data-stu-id="48abe-104">You use the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer to configure the logging store.</span></span>  
  
 <span data-ttu-id="48abe-105">使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管，並選取的記錄存放區。</span><span class="sxs-lookup"><span data-stu-id="48abe-105">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and select the logging store.</span></span>  
  
### <a name="to-open-btahl7-configuration-explorer"></a><span data-ttu-id="48abe-106">若要開啟 BTAHL7 組態總管</span><span class="sxs-lookup"><span data-stu-id="48abe-106">To open BTAHL7 Configuration Explorer</span></span>  
  
-   <span data-ttu-id="48abe-107">按一下**啟動**，按一下 **程式**，按一下  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 Configuration 總管**。</span><span class="sxs-lookup"><span data-stu-id="48abe-107">Click **Start**, click **Programs**, click **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  
  
### <a name="to-select-the--logging-store"></a><span data-ttu-id="48abe-108">若要選取的記錄存放區</span><span class="sxs-lookup"><span data-stu-id="48abe-108">To select the  logging store</span></span>  
  
1.  <span data-ttu-id="48abe-109">在[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]Configuration 總管上**通用設定**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="48abe-109">In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, on the **Global Settings** tab, do the following:</span></span>  
  
    |<span data-ttu-id="48abe-110">使用</span><span class="sxs-lookup"><span data-stu-id="48abe-110">Use this</span></span>|<span data-ttu-id="48abe-111">動作</span><span class="sxs-lookup"><span data-stu-id="48abe-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="48abe-112">**WMI**</span><span class="sxs-lookup"><span data-stu-id="48abe-112">**WMI**</span></span>|<span data-ttu-id="48abe-113">如果您想要產生 BTAHL7 WMI 通知，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="48abe-113">Select this option if you want to generate WMI notifications for BTAHL7.</span></span>|  
    |<span data-ttu-id="48abe-114">**SQL**</span><span class="sxs-lookup"><span data-stu-id="48abe-114">**SQL**</span></span>|<span data-ttu-id="48abe-115">選取此選項，如果您想要使用[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]做為您的記錄存放區。</span><span class="sxs-lookup"><span data-stu-id="48abe-115">Select this option if you want to use [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] as your  logging store.</span></span> <span data-ttu-id="48abe-116">**注意：** BTAHL7 會自動建立所需的記錄，如果它們尚不存在的資料表。</span><span class="sxs-lookup"><span data-stu-id="48abe-116">**Note:**  BTAHL7 automatically creates the tables required for  logging if they do not exist.</span></span>|  
    |<span data-ttu-id="48abe-117">**[SQL Server]**</span><span class="sxs-lookup"><span data-stu-id="48abe-117">**SQL Server**</span></span>|<span data-ttu-id="48abe-118">型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]名稱。</span><span class="sxs-lookup"><span data-stu-id="48abe-118">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] name.</span></span> <span data-ttu-id="48abe-119">這是必要的當您選取**SQL**選項。</span><span class="sxs-lookup"><span data-stu-id="48abe-119">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="48abe-120">允許的長度上限為 64 個字元。</span><span class="sxs-lookup"><span data-stu-id="48abe-120">The maximum allowed length is 64 characters.</span></span><br /><br /> <span data-ttu-id="48abe-121">預設的伺服器和資料庫名稱是已設定的 BTAHL7 資料庫。</span><span class="sxs-lookup"><span data-stu-id="48abe-121">The default server and database name is the configured BTAHL7 database.</span></span>|  
    |<span data-ttu-id="48abe-122">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="48abe-122">**Database name**</span></span>|<span data-ttu-id="48abe-123">型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="48abe-123">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database name.</span></span> <span data-ttu-id="48abe-124">這是必要的當您選取**SQL**選項。</span><span class="sxs-lookup"><span data-stu-id="48abe-124">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="48abe-125">最大允許的長度為 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="48abe-125">The maximum allowed length is 128 characters.</span></span>|  
    |<span data-ttu-id="48abe-126">**事件記錄檔**</span><span class="sxs-lookup"><span data-stu-id="48abe-126">**Event  Log**</span></span>|<span data-ttu-id="48abe-127">選取此選項，如果您想要使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]做為您的記錄存放區的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="48abe-127">Select this option if you want to use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log as your  logging store.</span></span> <span data-ttu-id="48abe-128">您使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器來檢視事件訊息。</span><span class="sxs-lookup"><span data-stu-id="48abe-128">You use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer to view event messages.</span></span>|  
  
2.  <span data-ttu-id="48abe-129">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="48abe-129">Click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48abe-130">地區設定的記錄所記錄的事件 broker 的事件記錄服務帳戶的地區設定而定。</span><span class="sxs-lookup"><span data-stu-id="48abe-130">The locale of the events logged by the  Logging event broker depend on the locale of the  Logging Service account.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="48abe-131">變更記錄服務帳戶密碼時，您應該先變更中的密碼[!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsAD](../../includes/btsad-md.md)]目錄服務，然後重新啟動服務後執行的每部伺服器上的記錄服務密碼變更的記錄。</span><span class="sxs-lookup"><span data-stu-id="48abe-131">When changing the  Logging Service account password, you should first change the password in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsAD](../../includes/btsad-md.md)] directory service, and then restart the  Logging Service after changing the  Logging Service password on every server running it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48abe-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="48abe-132">See Also</span></span>  
 <span data-ttu-id="48abe-133">[訊息批次](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span><span class="sxs-lookup"><span data-stu-id="48abe-133">[Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span></span>  
 [<span data-ttu-id="48abe-134">記錄設定</span><span class="sxs-lookup"><span data-stu-id="48abe-134">Logging Configuration</span></span>](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)