---
title: "不支援的安全性演算法套件 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11696fed-c3a8-4b11-8249-9f99f7abc8f2
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 43cce7cd315c3bdfa3835014c2cf1f6a8c7077f5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unsupported-security-algorithm-suite"></a><span data-ttu-id="0c983-102">不支援的安全性演算法套件</span><span class="sxs-lookup"><span data-stu-id="0c983-102">Unsupported security algorithm suite</span></span>
## <a name="details"></a><span data-ttu-id="0c983-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0c983-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0c983-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0c983-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="0c983-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0c983-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="0c983-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0c983-106">Event ID</span></span>|<span data-ttu-id="0c983-107">0</span><span class="sxs-lookup"><span data-stu-id="0c983-107">0</span></span>|  
|<span data-ttu-id="0c983-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0c983-108">Event Source</span></span>|<span data-ttu-id="0c983-109">0</span><span class="sxs-lookup"><span data-stu-id="0c983-109">0</span></span>|  
|<span data-ttu-id="0c983-110">元件</span><span class="sxs-lookup"><span data-stu-id="0c983-110">Component</span></span>|<span data-ttu-id="0c983-111">0</span><span class="sxs-lookup"><span data-stu-id="0c983-111">0</span></span>|  
|<span data-ttu-id="0c983-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0c983-112">Symbolic Name</span></span>|<span data-ttu-id="0c983-113">0</span><span class="sxs-lookup"><span data-stu-id="0c983-113">0</span></span>|  
|<span data-ttu-id="0c983-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0c983-114">Message Text</span></span>|<span data-ttu-id="0c983-115">不支援的安全性演算法組合： {0}</span><span class="sxs-lookup"><span data-stu-id="0c983-115">Unsupported security algorithm suite: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0c983-116">說明</span><span class="sxs-lookup"><span data-stu-id="0c983-116">Explanation</span></span>  
 <span data-ttu-id="0c983-117">當接收位置或傳送埠的安全性演算法套件屬性設定不正確的值時，就會發生此錯誤。</span><span class="sxs-lookup"><span data-stu-id="0c983-117">This error occurs when the security algorithm suite property of a receive location or send port is set to an incorrect value.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0c983-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0c983-118">User Action</span></span>  
 <span data-ttu-id="0c983-119">請確定的交易通訊協定屬性設為有效的值。</span><span class="sxs-lookup"><span data-stu-id="0c983-119">Ensure that transaction protocol property is set to a valid value.</span></span>  
  
1.  <span data-ttu-id="0c983-120">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="0c983-120">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="0c983-121">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0c983-121">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="0c983-122">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="0c983-122">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="0c983-123">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="0c983-123">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="0c983-124">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="0c983-124">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="0c983-125">在 連接埠**類型**清單中，選取**Wcf-nettcp**。</span><span class="sxs-lookup"><span data-stu-id="0c983-125">In the port **Type** list, select **WCF-NetTcp**.</span></span>  
  
7.  <span data-ttu-id="0c983-126">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="0c983-126">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="0c983-127">在**Wcf-nettcp 傳輸屬性**對話方塊中，按一下 [**安全性**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0c983-127">In the **WCF-NetTcp Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="0c983-128">在**訊息安全性**區段中，請確認值**演算法套件**正確無誤。</span><span class="sxs-lookup"><span data-stu-id="0c983-128">In the **Message security** section, ensure that the values for **Algorithm suite** are correct.</span></span>