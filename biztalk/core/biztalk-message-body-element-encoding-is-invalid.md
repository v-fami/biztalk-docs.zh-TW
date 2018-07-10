---
title: BizTalk 訊息內文元素編碼無效 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b407e5c3-4655-4b2f-8ecc-30eb080ec47c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c6bca7046606461dd3368224364c21dd48ea5dfb
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36967967"
---
# <a name="biztalk-message-body-element-encoding-is-invalid"></a><span data-ttu-id="0eec2-102">BizTalk 訊息內文元素編碼不正確</span><span class="sxs-lookup"><span data-stu-id="0eec2-102">BizTalk message body element encoding is invalid</span></span>
## <a name="details"></a><span data-ttu-id="0eec2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0eec2-103">Details</span></span>  
  
|                 |                                                                                                                |
|-----------------|----------------------------------------------------------------------------------------------------------------|
|  <span data-ttu-id="0eec2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0eec2-104">Product Name</span></span>   |               [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]               |
| <span data-ttu-id="0eec2-105">產品版本</span><span class="sxs-lookup"><span data-stu-id="0eec2-105">Product Version</span></span> |                           [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                           |
|    <span data-ttu-id="0eec2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0eec2-106">Event ID</span></span>     |                                                       <span data-ttu-id="0eec2-107">0</span><span class="sxs-lookup"><span data-stu-id="0eec2-107">0</span></span>                                                        |
|  <span data-ttu-id="0eec2-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0eec2-108">Event Source</span></span>   |                                                       <span data-ttu-id="0eec2-109">0</span><span class="sxs-lookup"><span data-stu-id="0eec2-109">0</span></span>                                                        |
|    <span data-ttu-id="0eec2-110">元件</span><span class="sxs-lookup"><span data-stu-id="0eec2-110">Component</span></span>    |                                                       <span data-ttu-id="0eec2-111">0</span><span class="sxs-lookup"><span data-stu-id="0eec2-111">0</span></span>                                                        |
|  <span data-ttu-id="0eec2-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0eec2-112">Symbolic Name</span></span>  |                                                       <span data-ttu-id="0eec2-113">0</span><span class="sxs-lookup"><span data-stu-id="0eec2-113">0</span></span>                                                        |
|  <span data-ttu-id="0eec2-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0eec2-114">Message Text</span></span>   | <span data-ttu-id="0eec2-115">BizTalk 訊息內文元素編碼"{0}"無效。</span><span class="sxs-lookup"><span data-stu-id="0eec2-115">BizTalk message body element encoding "{0}" is invalid.</span></span> <span data-ttu-id="0eec2-116">預期的編碼方式:"xml"，"none"|"base64"、"hex"或"string"</span><span class="sxs-lookup"><span data-stu-id="0eec2-116">Expected encoding: "xml", "base64", "hex", or "string"</span></span> |
  
## <a name="explanation"></a><span data-ttu-id="0eec2-117">說明</span><span class="sxs-lookup"><span data-stu-id="0eec2-117">Explanation</span></span>  
 <span data-ttu-id="0eec2-118">此錯誤表示 BizTalk 內文 範本選項用於外寄訊息中;不過，指定 BizTalk 內文的編碼類型無效。</span><span class="sxs-lookup"><span data-stu-id="0eec2-118">This error indicates the use of the BizTalk body template option for the outgoing messages; however, the encoding type specified for the BizTalk body is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0eec2-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0eec2-119">User Action</span></span>  
 <span data-ttu-id="0eec2-120">您可以使用下列程序來設定編碼類型。</span><span class="sxs-lookup"><span data-stu-id="0eec2-120">Use the following procedure to configure the encoding type.</span></span>  
  
#### <a name="to-configure-the-encoding-type"></a><span data-ttu-id="0eec2-121">若要設定的編碼類型</span><span class="sxs-lookup"><span data-stu-id="0eec2-121">To configure the encoding type</span></span>  
  
1. <span data-ttu-id="0eec2-122">按一下 **開始**，按一下**所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理]**。</span><span class="sxs-lookup"><span data-stu-id="0eec2-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2. <span data-ttu-id="0eec2-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="0eec2-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3. <span data-ttu-id="0eec2-124">找出您的應用程式，然後找出您的傳輸。</span><span class="sxs-lookup"><span data-stu-id="0eec2-124">Locate your application and then locate your transport.</span></span>  
  
4. <span data-ttu-id="0eec2-125">以滑鼠右鍵按一下傳輸名稱。</span><span class="sxs-lookup"><span data-stu-id="0eec2-125">Right-click the transport name.</span></span>  
  
5. <span data-ttu-id="0eec2-126">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="0eec2-126">Click **Properties**.</span></span>  
  
6. <span data-ttu-id="0eec2-127">在 連接埠**型別**清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="0eec2-127">In the port **Type** list, select the correct port.</span></span>  
  
7. <span data-ttu-id="0eec2-128">按一下 **設定**。</span><span class="sxs-lookup"><span data-stu-id="0eec2-128">Click **Configure**.</span></span>  
  
8. <span data-ttu-id="0eec2-129">在 [ **WCF [**<em>傳輸類型</em>**] 傳輸屬性**] 對話方塊中，按一下 [**訊息**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0eec2-129">In the **WCF [**<em>transport type</em>**] Transport Properties** dialog box, click the **Messages** tab.</span></span>  
  
9. <span data-ttu-id="0eec2-130">在 **輸出 WCF 訊息內文**區段中，按一下**範本-由範本指定內容**選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="0eec2-130">In the **Outbound WCF message body** section, click the **Template – Content specified by template** radio button.</span></span> <span data-ttu-id="0eec2-131">在 [ **XML** BizTalk 內文的格式應為文字] 方塊中，</span><span class="sxs-lookup"><span data-stu-id="0eec2-131">In the **XML** text box, the format of the BizTalk body should be</span></span>   
    <span data-ttu-id="0eec2-132">\<**bts 訊息主體 xmlns ="<http://www.microsoft.com/schemas/bts2007>"編碼 ="[xml&#124;base64&#124;十六進位&#124;字串]"/** \> (有效的值，也就是區分大小寫，編碼為 xml&#124;base64&#124;十六進位&#124;字串)</span><span class="sxs-lookup"><span data-stu-id="0eec2-132">\<**bts-msg-body xmlns="<http://www.microsoft.com/schemas/bts2007>" encoding="[xml&#124;base64&#124;hex&#124;string]"/**\>  (valid values, which are case-sensitive, for encoding are xml&#124;base64&#124;hex&#124;string)</span></span>