---
title: "處理錯誤的錯誤 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 602be8a5-1f28-457d-8e12-ba06cff65491
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dafc64afb24ce8bb7995e7852a778b17a556f018
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="error-handling-errors"></a><span data-ttu-id="325e0-102">錯誤處理錯誤</span><span class="sxs-lookup"><span data-stu-id="325e0-102">Error Handling Errors</span></span>
<span data-ttu-id="325e0-103">診斷及解決 WCF 錯誤處理錯誤的資訊。</span><span class="sxs-lookup"><span data-stu-id="325e0-103">Information for diagnosing and resolving WCF Error Handling errors.</span></span>  

## <a name="error-handling-options-disable-location-on-failure-and-suspend-request-message-on-failure-should-not-both-be-set-to-false"></a><span data-ttu-id="325e0-104">錯誤處理選項 [停用失敗的位置] 和 「 擱置失敗的要求訊息 」 應該不能兩者都設定為 false</span><span class="sxs-lookup"><span data-stu-id="325e0-104">Error handling options "Disable location on failure" and "Suspend request message on failure" should not both be set to false</span></span>    
||<span data-ttu-id="325e0-105">詳細資料</span><span class="sxs-lookup"><span data-stu-id="325e0-105">Details</span></span>|  
|-|-|  
|<span data-ttu-id="325e0-106">產品名稱</span><span class="sxs-lookup"><span data-stu-id="325e0-106">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="325e0-107">產品版本</span><span class="sxs-lookup"><span data-stu-id="325e0-107">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="325e0-108">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="325e0-108">Event ID</span></span>|<span data-ttu-id="325e0-109">0</span><span class="sxs-lookup"><span data-stu-id="325e0-109">0</span></span>|  
|<span data-ttu-id="325e0-110">事件來源</span><span class="sxs-lookup"><span data-stu-id="325e0-110">Event Source</span></span>|<span data-ttu-id="325e0-111">0</span><span class="sxs-lookup"><span data-stu-id="325e0-111">0</span></span>|  
|<span data-ttu-id="325e0-112">元件</span><span class="sxs-lookup"><span data-stu-id="325e0-112">Component</span></span>|<span data-ttu-id="325e0-113">0</span><span class="sxs-lookup"><span data-stu-id="325e0-113">0</span></span>|  
|<span data-ttu-id="325e0-114">符號名稱</span><span class="sxs-lookup"><span data-stu-id="325e0-114">Symbolic Name</span></span>|<span data-ttu-id="325e0-115">0</span><span class="sxs-lookup"><span data-stu-id="325e0-115">0</span></span>|  
|<span data-ttu-id="325e0-116">訊息文字</span><span class="sxs-lookup"><span data-stu-id="325e0-116">Message Text</span></span>|<span data-ttu-id="325e0-117">錯誤處理選項 [停用失敗的位置] 並 「 暫停失敗的要求訊息 」 應該不能兩者都設定為 false 後可能會發生訊息遺失。</span><span class="sxs-lookup"><span data-stu-id="325e0-117">The error handling options "Disable location on failure" and "Suspend request message on failure" should not both be set to false since message loss may occur.</span></span> <span data-ttu-id="325e0-118">請將一個或兩個選項設定為 true</span><span class="sxs-lookup"><span data-stu-id="325e0-118">Please set one or both options to true</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="325e0-119">說明</span><span class="sxs-lookup"><span data-stu-id="325e0-119">Explanation</span></span>  
 <span data-ttu-id="325e0-120">Wcf-netmsmq 配接器的選項中**停用失敗的位置**和**擱置失敗的要求訊息**應該不能兩者都選取。</span><span class="sxs-lookup"><span data-stu-id="325e0-120">In the WCF-NetMsmq adapter, the options **Disable location on failure** and **Suspend request message on failure** should not both be selected.</span></span> <span data-ttu-id="325e0-121">為接收位置會繼續接收無效的訊息，雖然這些訊息不是暫停，且儲存在訊息方塊中，可能會發生訊息遺失。</span><span class="sxs-lookup"><span data-stu-id="325e0-121">Message loss may occur as the receive location continues to receive invalid messages, while these messages are not suspended and stored in the Message Box.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="325e0-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="325e0-122">User Action</span></span>  
 <span data-ttu-id="325e0-123">您可以使用下列程序來設定介面卡設定。</span><span class="sxs-lookup"><span data-stu-id="325e0-123">Use the following procedure to configure adapter settings.</span></span>    

1. <span data-ttu-id="325e0-124">開啟 [BizTalk Server 管理] 。</span><span class="sxs-lookup"><span data-stu-id="325e0-124">Open **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="325e0-125">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="325e0-125">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand **Applications**.</span></span>  
  
3.  <span data-ttu-id="325e0-126">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="325e0-126">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="325e0-127">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="325e0-127">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="325e0-128">選取**屬性**。</span><span class="sxs-lookup"><span data-stu-id="325e0-128">Select **Properties**.</span></span>  
  
6.  <span data-ttu-id="325e0-129">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="325e0-129">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="325e0-130">選取 **[設定]**。</span><span class="sxs-lookup"><span data-stu-id="325e0-130">Select **Configure**.</span></span>  
  
8.  <span data-ttu-id="325e0-131">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，選取**訊息** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="325e0-131">In the **WCF [***transport type***] Transport Properties** dialog box, select the **Messages** tab.</span></span>  
  
9. <span data-ttu-id="325e0-132">在**錯誤處理**區段中，確定 **停用失敗的位置**或**擱置失敗的要求訊息**已核取。</span><span class="sxs-lookup"><span data-stu-id="325e0-132">In the **Error Handling** section, ensure either **Disable location on failure** or **Suspend request message on failure** is checked.</span></span>