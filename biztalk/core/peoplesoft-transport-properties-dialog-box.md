---
title: "PeopleSoft 傳輸屬性對話方塊 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PeopleSoft
helpviewer_keywords: PeopleSoft Transport Properties dialog box
ms.assetid: 660f0a0b-e076-4f4e-8b2a-6d976acfc5ce
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50362e60b982a2d304efea8c26f58019148e5c16
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="peoplesoft-transport-properties-dialog-box"></a><span data-ttu-id="98d5d-102">PeopleSoft 傳輸屬性對話方塊</span><span class="sxs-lookup"><span data-stu-id="98d5d-102">PeopleSoft Transport Properties Dialog Box</span></span>
<span data-ttu-id="98d5d-103">使用 [PeopleSoft Transport 傳輸屬性] 對話方塊設定配接器必要屬性。</span><span class="sxs-lookup"><span data-stu-id="98d5d-103">Use the PeopleSoft Transport Properties dialog box to set the adapter-required properties.</span></span>  
  
|<span data-ttu-id="98d5d-104">使用</span><span class="sxs-lookup"><span data-stu-id="98d5d-104">Use this</span></span>|<span data-ttu-id="98d5d-105">動作</span><span class="sxs-lookup"><span data-stu-id="98d5d-105">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="98d5d-106">**配接器必要屬性**</span><span class="sxs-lookup"><span data-stu-id="98d5d-106">**Adapter Required Properties**</span></span>||  
|<span data-ttu-id="98d5d-107">應用程式伺服器路徑</span><span class="sxs-lookup"><span data-stu-id="98d5d-107">Application server path</span></span>|<span data-ttu-id="98d5d-108">輸入 PeopleSoft server 的路徑 (例如， `//psserver.domain.com:9000`)。</span><span class="sxs-lookup"><span data-stu-id="98d5d-108">Type the path for the PeopleSoft server (for example, `//psserver.domain.com:9000`).</span></span>|  
|<span data-ttu-id="98d5d-109">JAVA_HOME</span><span class="sxs-lookup"><span data-stu-id="98d5d-109">JAVA_HOME</span></span>|<span data-ttu-id="98d5d-110">輸入 JAVA_HOME 位置的名稱 (例如， `<drive:>\jdk1.4.2_08`)。</span><span class="sxs-lookup"><span data-stu-id="98d5d-110">Type the name for the JAVA_HOME location (for example, `<drive:>\jdk1.4.2_08`).</span></span>|  
|<span data-ttu-id="98d5d-111">密碼</span><span class="sxs-lookup"><span data-stu-id="98d5d-111">Password</span></span>|<span data-ttu-id="98d5d-112">輸入這個使用者的密碼。</span><span class="sxs-lookup"><span data-stu-id="98d5d-112">Type the password for this user.</span></span>|  
|<span data-ttu-id="98d5d-113">PeopleSoft 8.x JAR 檔案</span><span class="sxs-lookup"><span data-stu-id="98d5d-113">PeopleSoft 8.x JAR files</span></span>|<span data-ttu-id="98d5d-114">輸入 PeopleSoft JAR 檔案的位置路徑 (例如， `<drive:>\JAR_FILES\Peoplesoft_8.4\psjoa.jar`)。</span><span class="sxs-lookup"><span data-stu-id="98d5d-114">Type the path for the location of the PeopleSoft JAR files (for example, `<drive:>\JAR_FILES\Peoplesoft_8.4\psjoa.jar`).</span></span>|  
|<span data-ttu-id="98d5d-115">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="98d5d-115">User name</span></span>|<span data-ttu-id="98d5d-116">輸入使用者名稱，然後按一下**確定**。</span><span class="sxs-lookup"><span data-stu-id="98d5d-116">Type the name of the user, and click **OK**.</span></span>|  
|<span data-ttu-id="98d5d-117">**其他參數**</span><span class="sxs-lookup"><span data-stu-id="98d5d-117">**Additional Parameters**</span></span>||  
|<span data-ttu-id="98d5d-118">資料庫日期格式</span><span class="sxs-lookup"><span data-stu-id="98d5d-118">Database Date Format</span></span>|<span data-ttu-id="98d5d-119">輸入您想要出現日期的格式 (例如，**YYYY MM DD**)。</span><span class="sxs-lookup"><span data-stu-id="98d5d-119">Type the format in which you want dates to appear (for example,**YYYY-MM-DD**).</span></span><br /><br /> <span data-ttu-id="98d5d-120">當日期做為索引鍵使用時，格式將不同。</span><span class="sxs-lookup"><span data-stu-id="98d5d-120">The date has a different format when used as a key.</span></span>|  
|<span data-ttu-id="98d5d-121">**並行控制**</span><span class="sxs-lookup"><span data-stu-id="98d5d-121">**Concurrency Control**</span></span>||  
|<span data-ttu-id="98d5d-122">同時呼叫數目上限</span><span class="sxs-lookup"><span data-stu-id="98d5d-122">Max Concurrent Calls</span></span>|<span data-ttu-id="98d5d-123">輸入的數值**同時呼叫數目上限**。</span><span class="sxs-lookup"><span data-stu-id="98d5d-123">Type a numeric value for the **Max Concurrent Calls**.</span></span> <span data-ttu-id="98d5d-124">此數目代表同時呼叫的數目上限，例如 200。</span><span class="sxs-lookup"><span data-stu-id="98d5d-124">This number represents the maximum number of concurrent calls, for example, 200.</span></span><br /><br /> <span data-ttu-id="98d5d-125">此欄位 的預設值為 -1，表示不會提供保護 。</span><span class="sxs-lookup"><span data-stu-id="98d5d-125">The default value for this field is -1, meaning no protection occurs.</span></span>|  
|<span data-ttu-id="98d5d-126">**連接**</span><span class="sxs-lookup"><span data-stu-id="98d5d-126">**Connection**</span></span>||  
|<span data-ttu-id="98d5d-127">工作階段數目上限</span><span class="sxs-lookup"><span data-stu-id="98d5d-127">Maximum number of sessions</span></span>|<span data-ttu-id="98d5d-128">輸入代表工作階段數目上限的數目。</span><span class="sxs-lookup"><span data-stu-id="98d5d-128">Type a number to represent the maximum number of sessions.</span></span><br /><br /> <span data-ttu-id="98d5d-129">預設的連線次數為 40。</span><span class="sxs-lookup"><span data-stu-id="98d5d-129">The default number of connections is 40.</span></span>|  
|<span data-ttu-id="98d5d-130">**重新整理代理程式**</span><span class="sxs-lookup"><span data-stu-id="98d5d-130">**Refresh Agent**</span></span>||  
|<span data-ttu-id="98d5d-131">重新整理代理程式</span><span class="sxs-lookup"><span data-stu-id="98d5d-131">Refresh Agent</span></span>|<span data-ttu-id="98d5d-132">選取**是**如**重新整理代理程式**強制 runtimeagent.exe 和 browsingagent.exe 程序在必要時自動重新啟動。</span><span class="sxs-lookup"><span data-stu-id="98d5d-132">Select **Yes** for the **Refresh Agent** to force the runtimeagent.exe and the browsingagent.exe processes to restart automatically when required.</span></span><br /><br /> <span data-ttu-id="98d5d-133">例如，您希望程序在與伺服器中斷連線時自動重新啟動，或是您在伺服器加上其他項目，但是該項目並未出現在配接器精靈的選項中。</span><span class="sxs-lookup"><span data-stu-id="98d5d-133">For example, you want the process to restart automatically if it loses connection with the server, or if you add something to the server and it does not appear in the Adapter Wizard for selection.</span></span>|  
|<span data-ttu-id="98d5d-134">**單一登入**</span><span class="sxs-lookup"><span data-stu-id="98d5d-134">**Single Sign-On**</span></span>||  
|<span data-ttu-id="98d5d-135">分支機構應用程式</span><span class="sxs-lookup"><span data-stu-id="98d5d-135">Affiliate Application</span></span>|<span data-ttu-id="98d5d-136">只有在您使用單一登入 (SSO) 時，才需從清單中選取分支機構應用程式。</span><span class="sxs-lookup"><span data-stu-id="98d5d-136">Select the affiliate application from the list only if you are using Single Sign-ON (SSO).</span></span>|  
|<span data-ttu-id="98d5d-137">使用 SSO</span><span class="sxs-lookup"><span data-stu-id="98d5d-137">Use SSO</span></span>|<span data-ttu-id="98d5d-138">選取**是**如果您使用 SSO; 密碼就不需要在此情況下。</span><span class="sxs-lookup"><span data-stu-id="98d5d-138">Select **Yes** if you are using SSO; a password is not required in this case.</span></span> <span data-ttu-id="98d5d-139">**注意：**如果您已輸入密碼，而且您想要使用單一登入，以滑鼠右鍵按一下欄位和選取的密碼**將密碼**。</span><span class="sxs-lookup"><span data-stu-id="98d5d-139">**Note:**  If you already entered a password and you want to use Single Sign-On, right-click the Password field and select **Nullify Password**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98d5d-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98d5d-140">See Also</span></span>  
 [<span data-ttu-id="98d5d-141">BizTalk Adapter for PeopleSoft Enterprise 的 UI 參考</span><span class="sxs-lookup"><span data-stu-id="98d5d-141">UI Reference for BizTalk Adapter for PeopleSoft Enterprise</span></span>](../core/ui-reference-for-biztalk-adapter-for-peoplesoft-enterprise.md)