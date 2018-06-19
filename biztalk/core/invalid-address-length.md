---
title: 無效的位址長度 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8e16eb6-e77e-4361-ac91-0730004c4433
caps.latest.revision: 16
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2df1666fbbd399ef71852b9b9049959830749e99
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257582"
---
# <a name="invalid-address-length"></a><span data-ttu-id="7d17a-102">無效的位址長度</span><span class="sxs-lookup"><span data-stu-id="7d17a-102">Invalid address length</span></span>
## <a name="details"></a><span data-ttu-id="7d17a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="7d17a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7d17a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="7d17a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="7d17a-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="7d17a-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="7d17a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="7d17a-106">Event ID</span></span>|<span data-ttu-id="7d17a-107">0</span><span class="sxs-lookup"><span data-stu-id="7d17a-107">0</span></span>|  
|<span data-ttu-id="7d17a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="7d17a-108">Event Source</span></span>|<span data-ttu-id="7d17a-109">0</span><span class="sxs-lookup"><span data-stu-id="7d17a-109">0</span></span>|  
|<span data-ttu-id="7d17a-110">元件</span><span class="sxs-lookup"><span data-stu-id="7d17a-110">Component</span></span>|<span data-ttu-id="7d17a-111">0</span><span class="sxs-lookup"><span data-stu-id="7d17a-111">0</span></span>|  
|<span data-ttu-id="7d17a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="7d17a-112">Symbolic Name</span></span>|<span data-ttu-id="7d17a-113">0</span><span class="sxs-lookup"><span data-stu-id="7d17a-113">0</span></span>|  
|<span data-ttu-id="7d17a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="7d17a-114">Message Text</span></span>|<span data-ttu-id="7d17a-115">無效的位址長度。指定的位址長度為 {0} 個字元，限制為 {1} 個字元</span><span class="sxs-lookup"><span data-stu-id="7d17a-115">Invalid address length; specified address length is {0} characters, limit is {1} characters</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="7d17a-116">說明</span><span class="sxs-lookup"><span data-stu-id="7d17a-116">Explanation</span></span>  
 <span data-ttu-id="7d17a-117">您提供超過 255 個字元的 WCF 傳輸的最大長度的位址。</span><span class="sxs-lookup"><span data-stu-id="7d17a-117">You provided an address that exceeds the maximum length of 255 characters for a WCF transport.</span></span> <span data-ttu-id="7d17a-118">這是 BizTalk Server 中，不是由 WCF 所加諸的限制。</span><span class="sxs-lookup"><span data-stu-id="7d17a-118">This is a limitation imposed by BizTalk Server, not by WCF.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="7d17a-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="7d17a-119">User Action</span></span>  
 <span data-ttu-id="7d17a-120">您可以使用下列程序來設定有效的位址。</span><span class="sxs-lookup"><span data-stu-id="7d17a-120">Use the following procedure to configure a valid address.</span></span>  
  
#### <a name="to-configure-a-valid-address"></a><span data-ttu-id="7d17a-121">若要設定有效的位址</span><span class="sxs-lookup"><span data-stu-id="7d17a-121">To configure a valid address</span></span>  
  
1.  <span data-ttu-id="7d17a-122">按一下**啟動**，按一下 **所有程式**，按一下  **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** ，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="7d17a-122">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="7d17a-123">在 主控台根目錄中，展開**BizTalk Server 管理**，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="7d17a-123">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="7d17a-124">找出您的應用程式，然後再找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="7d17a-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="7d17a-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="7d17a-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="7d17a-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="7d17a-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="7d17a-127">在 連接埠**類型**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="7d17a-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="7d17a-128">按一下**設定**。</span><span class="sxs-lookup"><span data-stu-id="7d17a-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="7d17a-129">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**一般**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7d17a-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="7d17a-130">在**位址 (URI)** 文字方塊中，確認位址不能超過 255 個字元的最大長度。</span><span class="sxs-lookup"><span data-stu-id="7d17a-130">In the **Address (URI)** text box, ensure the address does not exceed the maximum length of 255 characters.</span></span>