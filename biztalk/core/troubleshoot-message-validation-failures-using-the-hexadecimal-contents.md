---
title: "疑難排解訊息驗證失敗，藉由檢視十六進位內容的擱置訊息 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5cf14cd9-2d4b-43a3-9738-52bfd879e1e4
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2f7dc0f24a85f206831e3706bd03f2206aaa2c15
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-message-validation-failures-by-viewing-the-hexadecimal-contents-of-suspended-messages"></a><span data-ttu-id="730be-102">透過檢視十六進位內容的擱置訊息，對訊息驗證失敗的疑難排解</span><span class="sxs-lookup"><span data-stu-id="730be-102">Troubleshooting Message Validation Failures by Viewing the Hexadecimal Contents of Suspended Messages</span></span>
<span data-ttu-id="730be-103">如果因驗證失敗而擱置訊息，檢視十六進位表示的訊息部分，可能有助於判斷驗證失敗的原因。</span><span class="sxs-lookup"><span data-stu-id="730be-103">If a message is suspended due to validation failures, it may be helpful to view the hexadecimal representation of the message parts to determine the cause of the validation failure.</span></span> <span data-ttu-id="730be-104">本主題列出執行步驟來檢視十六進位表示的擱置訊息部分。</span><span class="sxs-lookup"><span data-stu-id="730be-104">This topic lists steps that can be followed to view the hexadecimal representation of the parts of a suspended message.</span></span>  
  
## <a name="use-the-message-details-dialog-box-to-view-message-parts"></a><span data-ttu-id="730be-105">使用訊息詳細資料對話方塊以檢視訊息部分</span><span class="sxs-lookup"><span data-stu-id="730be-105">Use the Message Details dialog box to view message parts</span></span>  
 <span data-ttu-id="730be-106">請依照下列步驟檢視十六進位表示的訊息部分：</span><span class="sxs-lookup"><span data-stu-id="730be-106">Follow these steps to view the hexadecimal representation of message parts:</span></span>  
  
1.  <span data-ttu-id="730be-107">使用**查詢**在 BizTalk 管理主控台，來傳回含有一或多個擱置訊息的結果集的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="730be-107">Use the **Query** tab in the BizTalk Administration Console to return a result set with one or more suspended messages.</span></span> <span data-ttu-id="730be-108">請參閱[如何搜尋訊息](../core/how-to-search-for-messages.md)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="730be-108">See [How to Search for Messages](../core/how-to-search-for-messages.md) for more information.</span></span>  
  
2.  <span data-ttu-id="730be-109">按兩下您想要調查並顯示擱置的訊息**訊息詳細資料**訊息對話方塊。</span><span class="sxs-lookup"><span data-stu-id="730be-109">Double-click the suspended message that you want to investigate to display the **Message Details** dialog box for the message.</span></span>  
  
3.  <span data-ttu-id="730be-110">按一下左窗格中的訊息部分**訊息詳細資料**對話方塊來顯示訊息部分。</span><span class="sxs-lookup"><span data-stu-id="730be-110">Click a message part in the left hand pane of the **Message Details** dialog box to display the message part.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="730be-111">訊息可能有 0 個、1 個或多個訊息部分，</span><span class="sxs-lookup"><span data-stu-id="730be-111">Messages may have 0, 1 or many message parts.</span></span> <span data-ttu-id="730be-112">但是最常有一個稱為「內文」的訊息部分。</span><span class="sxs-lookup"><span data-stu-id="730be-112">Most often messages have single message part that is called "body".</span></span>  
  
4.  <span data-ttu-id="730be-113">按一下**二進位** 索引標籤的右側窗格中**訊息詳細資料**對話方塊來顯示訊息部分的十六進位表示法。</span><span class="sxs-lookup"><span data-stu-id="730be-113">Click the **Binary** tab in the right hand pane of the **Message Details** dialog box to display the hexadecimal representation of the message part.</span></span>  
  
5.  <span data-ttu-id="730be-114">檢查十六進位表示的訊息部分字元是否有下列項目：</span><span class="sxs-lookup"><span data-stu-id="730be-114">Check the hexadecimal representation of characters in message parts for the following:</span></span>  
  
    -   <span data-ttu-id="730be-115">遺漏或無效的位元組順序標記。</span><span class="sxs-lookup"><span data-stu-id="730be-115">Missing or invalid byte order mark.</span></span> <span data-ttu-id="730be-116">如需有關位元組順序標記，請參閱[http://go.microsoft.com/fwlink/?LinkId=196380](http://go.microsoft.com/fwlink/?LinkId=196380)。</span><span class="sxs-lookup"><span data-stu-id="730be-116">For more information about byte order marks see [http://go.microsoft.com/fwlink/?LinkId=196380](http://go.microsoft.com/fwlink/?LinkId=196380).</span></span>  
  
    -   <span data-ttu-id="730be-117">Unix 和 Windows 在編碼分行符號方面的差異。</span><span class="sxs-lookup"><span data-stu-id="730be-117">Differences between the encoding of linebreaks in Unix and Windows.</span></span> <span data-ttu-id="730be-118">Unix 使用十六進位換行字元 (0A) 表示分行符號，而 Windows 則同時使用十六進位歸位字元 (0D) 和換行字元 (0A) 表示分行符號。</span><span class="sxs-lookup"><span data-stu-id="730be-118">Unix uses hex linefeed (0A) to indicate a line break where Windows uses both hex carriage return (0D) and linefeed (0A) to indicate a line break.</span></span>  
  
    -   <span data-ttu-id="730be-119">訊息部分中的無效控制字元。</span><span class="sxs-lookup"><span data-stu-id="730be-119">Invalid control character(s) in message parts.</span></span> <span data-ttu-id="730be-120">未出現在純文字中的控制字元可能會顯示在二進位檢視中。</span><span class="sxs-lookup"><span data-stu-id="730be-120">Control characters in message parts that do not show up in the text view may be visible in the binary view.</span></span>  
  
    -   <span data-ttu-id="730be-121">訊息部分中間的無效 nul 字元可能會使訊息部分遭截斷。</span><span class="sxs-lookup"><span data-stu-id="730be-121">Invalid nul character(s) in the middle of a message part can cause the message part to be truncated.</span></span> <span data-ttu-id="730be-122">nul 字元是以十六進位 (00) 表示。</span><span class="sxs-lookup"><span data-stu-id="730be-122">The nul character is represented as hex (00).</span></span>  
  
    -   <span data-ttu-id="730be-123">位置一般檔案中的無效字元位移。</span><span class="sxs-lookup"><span data-stu-id="730be-123">Invalid character offset in positional flat files.</span></span> <span data-ttu-id="730be-124">顯示十六進位表示的訊息部分，可檢視位置一般檔案中的資料位移。</span><span class="sxs-lookup"><span data-stu-id="730be-124">Display the hexadecimal representation of a message part to view the offset of data in a positional flat file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="730be-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="730be-125">See Also</span></span>  
 [<span data-ttu-id="730be-126">調查協調流程、 連接埠和訊息失敗</span><span class="sxs-lookup"><span data-stu-id="730be-126">Investigating Orchestration, Port, and Message Failures</span></span>](../core/investigating-orchestration-port-and-message-failures.md)