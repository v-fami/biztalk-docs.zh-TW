---
title: BizTalk 訊息內文項目編碼方式則無效 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b407e5c3-4655-4b2f-8ecc-30eb080ec47c
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1b1835371e5c042d3ddc46558cbf97970f6bfc6c
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/23/2018
---
# <a name="biztalk-message-body-element-encoding-is-invalid"></a><span data-ttu-id="ae06d-102">BizTalk 訊息內文項目編碼不正確</span><span class="sxs-lookup"><span data-stu-id="ae06d-102">BizTalk message body element encoding is invalid</span></span>
## <a name="details"></a><span data-ttu-id="ae06d-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ae06d-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ae06d-104">제품 이름</span><span class="sxs-lookup"><span data-stu-id="ae06d-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="ae06d-105">제품 버전</span><span class="sxs-lookup"><span data-stu-id="ae06d-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="ae06d-106">이벤트 ID</span><span class="sxs-lookup"><span data-stu-id="ae06d-106">Event ID</span></span>|<span data-ttu-id="ae06d-107">0</span><span class="sxs-lookup"><span data-stu-id="ae06d-107">0</span></span>|  
|<span data-ttu-id="ae06d-108">이벤트 원본</span><span class="sxs-lookup"><span data-stu-id="ae06d-108">Event Source</span></span>|<span data-ttu-id="ae06d-109">0</span><span class="sxs-lookup"><span data-stu-id="ae06d-109">0</span></span>|  
|<span data-ttu-id="ae06d-110">구성 요소</span><span class="sxs-lookup"><span data-stu-id="ae06d-110">Component</span></span>|<span data-ttu-id="ae06d-111">0</span><span class="sxs-lookup"><span data-stu-id="ae06d-111">0</span></span>|  
|<span data-ttu-id="ae06d-112">심볼 이름</span><span class="sxs-lookup"><span data-stu-id="ae06d-112">Symbolic Name</span></span>|<span data-ttu-id="ae06d-113">0</span><span class="sxs-lookup"><span data-stu-id="ae06d-113">0</span></span>|  
|<span data-ttu-id="ae06d-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ae06d-114">Message Text</span></span>|<span data-ttu-id="ae06d-115">BizTalk 訊息內文元素編碼"{0}"無效。</span><span class="sxs-lookup"><span data-stu-id="ae06d-115">BizTalk message body element encoding "{0}" is invalid.</span></span> <span data-ttu-id="ae06d-116">預期的編碼方式:"xml"，"base64"、"hex"或"string"</span><span class="sxs-lookup"><span data-stu-id="ae06d-116">Expected encoding: "xml", "base64", "hex", or "string"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ae06d-117">說明</span><span class="sxs-lookup"><span data-stu-id="ae06d-117">Explanation</span></span>  
 <span data-ttu-id="ae06d-118">此錯誤表示 BizTalk 內文範本選項用於外寄訊息中。不過，指定 BizTalk 內文的編碼類型不正確。</span><span class="sxs-lookup"><span data-stu-id="ae06d-118">This error indicates the use of the BizTalk body template option for the outgoing messages; however, the encoding type specified for the BizTalk body is invalid.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ae06d-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ae06d-119">User Action</span></span>  
 <span data-ttu-id="ae06d-120">您可以使用下列程序來設定編碼類型。</span><span class="sxs-lookup"><span data-stu-id="ae06d-120">Use the following procedure to configure the encoding type.</span></span>  
  
#### <a name="to-configure-the-encoding-type"></a><span data-ttu-id="ae06d-121">若要設定的編碼類型</span><span class="sxs-lookup"><span data-stu-id="ae06d-121">To configure the encoding type</span></span>  
  
1.  <span data-ttu-id="ae06d-122">按一下**啟動**，按一下 **所有程式**，按一下  [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)]，然後按一下**BizTalk Server 管理**。</span><span class="sxs-lookup"><span data-stu-id="ae06d-122">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="ae06d-123">在 主控台根目錄中，展開[!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)]，依序展開**BizTalk 群組**，然後展開**應用程式**。</span><span class="sxs-lookup"><span data-stu-id="ae06d-123">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="ae06d-124">응용 프로그램을 찾은 다음 전송을 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ae06d-124">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="ae06d-125">전송 이름을 마우스 오른쪽 단추로 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae06d-125">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="ae06d-126">**속성**을 클릭합니다.</span><span class="sxs-lookup"><span data-stu-id="ae06d-126">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="ae06d-127">在 連接埠 **類型** 清單中，選取正確的連接埠。</span><span class="sxs-lookup"><span data-stu-id="ae06d-127">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="ae06d-128">按一下  **設定**。</span><span class="sxs-lookup"><span data-stu-id="ae06d-128">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="ae06d-129">在**WCF [***傳輸類型***] 傳輸屬性**對話方塊中，按一下 [**訊息**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ae06d-129">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Messages** tab.</span></span>  
  
9. <span data-ttu-id="ae06d-130">在 **輸出 WCF 訊息內文** 區段中，按一下 **範本-由範本指定內容** 選項按鈕。</span><span class="sxs-lookup"><span data-stu-id="ae06d-130">In the **Outbound WCF message body** section, click the **Template – Content specified by template** radio button.</span></span> <span data-ttu-id="ae06d-131">在 **XML** BizTalk 主體的格式應該是文字方塊中，</span><span class="sxs-lookup"><span data-stu-id="ae06d-131">In the **XML** text box, the format of the BizTalk body should be</span></span>   
    <span data-ttu-id="ae06d-132">\<**bts 訊息主體 xmlns ="http://www.microsoft.com/schemas/bts2007"編碼方式 ="[xml&#124;base64&#124;十六進位&#124;字串]"/** \> (有效的值，也就是區分大小寫，編碼為 xml&#124;base64&#124;十六進位&#124;字串)</span><span class="sxs-lookup"><span data-stu-id="ae06d-132">\<**bts-msg-body xmlns="http://www.microsoft.com/schemas/bts2007" encoding="[xml&#124;base64&#124;hex&#124;string]"/**\>  (valid values, which are case-sensitive, for encoding are xml&#124;base64&#124;hex&#124;string)</span></span>