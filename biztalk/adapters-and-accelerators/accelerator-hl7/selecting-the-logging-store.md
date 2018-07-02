---
title: 選取記錄存放區 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuring, auditing
- configuring, logging
- logging, configuring
- auditing, configuring
ms.assetid: 6ba64c59-3a15-4c10-b44f-18e0e432c6d3
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 199726853eae4faf6efe67f622a8df2cbab1ccd1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986031"
---
# <a name="selecting-the-logging-store"></a><span data-ttu-id="c0f7d-102">選取記錄存放區</span><span class="sxs-lookup"><span data-stu-id="c0f7d-102">Selecting the Logging Store</span></span>
<span data-ttu-id="c0f7d-103">Microsoft[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]提供的選項，例如選取不同的記錄存放區中，組合[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]Management Instrumentation (WMI) [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]，和[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-103">Microsoft [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] provides you with the option to select a combination of different logging stores, such as [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Management Instrumentation (WMI), [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], and [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log.</span></span>  

 <span data-ttu-id="c0f7d-104">您使用[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管來設定記錄存放區。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-104">You use the [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer to configure the logging store.</span></span>  

 <span data-ttu-id="c0f7d-105">使用下列程序來開啟[!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管，並選取的記錄存放區。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-105">Use the following procedures to open [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer and select the logging store.</span></span>  

### <a name="to-open-btahl7-configuration-explorer"></a><span data-ttu-id="c0f7d-106">若要開啟 BTAHL7 設定總管</span><span class="sxs-lookup"><span data-stu-id="c0f7d-106">To open BTAHL7 Configuration Explorer</span></span>  

-   <span data-ttu-id="c0f7d-107">按一下 **開始**，按一下**程式**，按一下  **Microsoft BizTalk\<版本\>Accelerator for HL7**，然後按一下  **BTAHL7 設定總管**。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-107">Click **Start**, click **Programs**, click **Microsoft BizTalk \<version\> Accelerator for HL7**, and then click **BTAHL7 Configuration Explorer**.</span></span>  

### <a name="to-select-the--logging-store"></a><span data-ttu-id="c0f7d-108">若要選取的記錄存放區</span><span class="sxs-lookup"><span data-stu-id="c0f7d-108">To select the  logging store</span></span>  

1. <span data-ttu-id="c0f7d-109">在 [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]組態總管，請在**全域設定**索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="c0f7d-109">In [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] Configuration Explorer, on the **Global Settings** tab, do the following:</span></span>  


   |     <span data-ttu-id="c0f7d-110">使用</span><span class="sxs-lookup"><span data-stu-id="c0f7d-110">Use this</span></span>      |                                                                                                                                     <span data-ttu-id="c0f7d-111">以進行此動作</span><span class="sxs-lookup"><span data-stu-id="c0f7d-111">To do this</span></span>                                                                                                                                     |
   |-------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   |      <span data-ttu-id="c0f7d-112">**WMI**</span><span class="sxs-lookup"><span data-stu-id="c0f7d-112">**WMI**</span></span>      |                                                                                                      <span data-ttu-id="c0f7d-113">如果您想要產生 BTAHL7 WMI 通知，請選取此選項。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-113">Select this option if you want to generate WMI notifications for BTAHL7.</span></span>                                                                                                      |
   |      <span data-ttu-id="c0f7d-114">**SQL**</span><span class="sxs-lookup"><span data-stu-id="c0f7d-114">**SQL**</span></span>      |                     <span data-ttu-id="c0f7d-115">選取此選項，如果您想要使用[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]做為您的記錄存放區。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-115">Select this option if you want to use [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] as your  logging store.</span></span> <span data-ttu-id="c0f7d-116">**注意：** BTAHL7 會自動建立所需的記錄，如果它們尚不存在的資料表。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-116">**Note:**  BTAHL7 automatically creates the tables required for  logging if they do not exist.</span></span>                     |
   |  <span data-ttu-id="c0f7d-117">**[SQL Server]**</span><span class="sxs-lookup"><span data-stu-id="c0f7d-117">**SQL Server**</span></span>   | <span data-ttu-id="c0f7d-118">型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]名稱。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-118">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] name.</span></span> <span data-ttu-id="c0f7d-119">這是必要的當您選取**SQL**選項。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-119">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="c0f7d-120">允許的長度上限為 64 個字元。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-120">The maximum allowed length is 64 characters.</span></span><br /><br /> <span data-ttu-id="c0f7d-121">預設的伺服器和資料庫名稱是設定的 BTAHL7 資料庫。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-121">The default server and database name is the configured BTAHL7 database.</span></span> |
   | <span data-ttu-id="c0f7d-122">**資料庫名稱**</span><span class="sxs-lookup"><span data-stu-id="c0f7d-122">**Database name**</span></span> |                                      <span data-ttu-id="c0f7d-123">型別[!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)]資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-123">Type the [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)] database name.</span></span> <span data-ttu-id="c0f7d-124">這是必要的當您選取**SQL**選項。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-124">This is required when you select the **SQL** option.</span></span> <span data-ttu-id="c0f7d-125">允許的最大長度為 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-125">The maximum allowed length is 128 characters.</span></span>                                      |
   |  <span data-ttu-id="c0f7d-126">**事件記錄檔**</span><span class="sxs-lookup"><span data-stu-id="c0f7d-126">**Event  Log**</span></span>   |          <span data-ttu-id="c0f7d-127">選取此選項，如果您想要使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]做為您的記錄存放區的事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-127">Select this option if you want to use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Log as your  logging store.</span></span> <span data-ttu-id="c0f7d-128">您使用[!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)]事件檢視器來檢視事件訊息。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-128">You use the [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Event Viewer to view event messages.</span></span>          |


2. <span data-ttu-id="c0f7d-129">按一下 **[儲存]**。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-129">Click **Save**.</span></span>  

   > [!NOTE]
   >  <span data-ttu-id="c0f7d-130">地區設定的記錄事件訊息代理程式所記錄的事件記錄服務帳戶的地區設定而定。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-130">The locale of the events logged by the  Logging event broker depend on the locale of the  Logging Service account.</span></span>  
   > 
   > [!NOTE]
   >  <span data-ttu-id="c0f7d-131">變更記錄的服務帳戶密碼時，您應該先將變更的密碼，在 Microsoft[!INCLUDE[btsAD](../../includes/btsad-md.md)]目錄服務，然後重新啟動服務後執行的每部伺服器上的記錄服務密碼變更的記錄。</span><span class="sxs-lookup"><span data-stu-id="c0f7d-131">When changing the  Logging Service account password, you should first change the password in Microsoft [!INCLUDE[btsAD](../../includes/btsad-md.md)] directory service, and then restart the  Logging Service after changing the  Logging Service password on every server running it.</span></span>  

## <a name="see-also"></a><span data-ttu-id="c0f7d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0f7d-132">See Also</span></span>  
 <span data-ttu-id="c0f7d-133">[訊息批次處理](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span><span class="sxs-lookup"><span data-stu-id="c0f7d-133">[Message Batching](../../adapters-and-accelerators/accelerator-hl7/message-batching.md) </span></span>  
 [<span data-ttu-id="c0f7d-134">記錄設定</span><span class="sxs-lookup"><span data-stu-id="c0f7d-134">Logging Configuration</span></span>](../../adapters-and-accelerators/accelerator-hl7/logging-configuration.md)