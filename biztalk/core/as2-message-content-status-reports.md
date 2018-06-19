---
title: AS2 訊息內容狀態報告 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6244aa59-a80d-450b-ab95-9a5e14c0c40e
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3b2dadb3231136255dcf532e5054c1a6228880f8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230486"
---
# <a name="as2-message-content-status-reports"></a><span data-ttu-id="a76c5-102">AS2 訊息內容狀態報告</span><span class="sxs-lookup"><span data-stu-id="a76c5-102">AS2 Message Content Status Reports</span></span>

## <a name="overview"></a><span data-ttu-id="a76c5-103">概觀</span><span class="sxs-lookup"><span data-stu-id="a76c5-103">Overview</span></span>
<span data-ttu-id="a76c5-104">這些狀態報告會顯示 AS2 訊息或 MDN 的內容屬性、標頭和內容。</span><span class="sxs-lookup"><span data-stu-id="a76c5-104">These status reports display the context properties, headers and payload of an AS2 message or an MDN.</span></span> <span data-ttu-id="a76c5-105">AS2 訊息內容狀態報告有三種：</span><span class="sxs-lookup"><span data-stu-id="a76c5-105">There are three AS2 message content status reports:</span></span>  
  
-   <span data-ttu-id="a76c5-106">訊息電傳格式報告</span><span class="sxs-lookup"><span data-stu-id="a76c5-106">Message Wire Format report</span></span>  
  
-   <span data-ttu-id="a76c5-107">訊息解碼格式報告</span><span class="sxs-lookup"><span data-stu-id="a76c5-107">Message Decoded Format report</span></span>  
  
-   <span data-ttu-id="a76c5-108">Mdn 訊息報告</span><span class="sxs-lookup"><span data-stu-id="a76c5-108">Mdn Message report</span></span>  
  
 <span data-ttu-id="a76c5-109">您以滑鼠右鍵按一下 [AS2/MDN 狀態] 報告中的 AS2 訊息，然後按一下其中一種報告顯示**檢視訊息電傳格式**，**檢視訊息解碼格式**，或**檢視 Mdn訊息**。</span><span class="sxs-lookup"><span data-stu-id="a76c5-109">You display one of these reports by right-clicking an AS2 message within the AS2/MDN status report, and then clicking **View Message Wire Format**, **View Message Decoded Format**, or **View Mdn Message**.</span></span> <span data-ttu-id="a76c5-110">MDN 命令會顯示 AS2 訊息相互關聯的 MDN。</span><span class="sxs-lookup"><span data-stu-id="a76c5-110">The MDN command will display the MDN that is correlated to the AS2 message.</span></span>  
  
 <span data-ttu-id="a76c5-111">這些報告只有在您針對相關合作對象，於 [AS2 屬性] 對話方塊的 [做為 AS2 訊息傳送者的合作對象] 或 [做為 AS2 訊息接收者的合作對象] 頁面中選取對應的 [將訊息儲存在不可否認性的資料庫中] 屬性時才會提供。</span><span class="sxs-lookup"><span data-stu-id="a76c5-111">Each of these reports is available only if you have selected the corresponding "Store messages in non-repudiation database" properties in the Party as AS2 Message Sender page or Party as AS2 Message Receiver page of the AS2 Properties dialog box for the related party.</span></span> <span data-ttu-id="a76c5-112">這些命令會將 AS2 訊息或 MDN 以電傳格式或解碼格式儲存在 BizTalkDTADb 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="a76c5-112">The commands store AS2 messages or MDNs in wire format or decoded format in the BizTalkDTADb database.</span></span>  
  
 <span data-ttu-id="a76c5-113">這份報告使用**訊息詳細資料屬性對話方塊**(請參閱 UI 的詳細資料[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]) 顯示訊息資料，以分隔到頁面的資訊：</span><span class="sxs-lookup"><span data-stu-id="a76c5-113">This report uses the **Message Details Properties Dialog Box** (see the UI details [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]) to display message data, with information separated into pages:</span></span>  
  
|<span data-ttu-id="a76c5-114">頁面</span><span class="sxs-lookup"><span data-stu-id="a76c5-114">Page</span></span>|<span data-ttu-id="a76c5-115">顯示資料</span><span class="sxs-lookup"><span data-stu-id="a76c5-115">Data Displayed</span></span>|  
|----------|--------------------|  
|<span data-ttu-id="a76c5-116">**一般**</span><span class="sxs-lookup"><span data-stu-id="a76c5-116">**General**</span></span>|<span data-ttu-id="a76c5-117">訊息的概觀資訊</span><span class="sxs-lookup"><span data-stu-id="a76c5-117">Overview information about the message</span></span>|  
|<span data-ttu-id="a76c5-118">**內容**</span><span class="sxs-lookup"><span data-stu-id="a76c5-118">**Context**</span></span>|<span data-ttu-id="a76c5-119">與此訊息相關聯的內容屬性</span><span class="sxs-lookup"><span data-stu-id="a76c5-119">Context properties associated with this message</span></span>|  
|<span data-ttu-id="a76c5-120">**訊息部分**</span><span class="sxs-lookup"><span data-stu-id="a76c5-120">**Message Parts**</span></span>|<span data-ttu-id="a76c5-121">包含此訊息在個別的文件內容。</span><span class="sxs-lookup"><span data-stu-id="a76c5-121">Individual document payload contained within this message.</span></span> <span data-ttu-id="a76c5-122">每份文件都可視為文字或二進位檔：</span><span class="sxs-lookup"><span data-stu-id="a76c5-122">Each document can be viewed as either text or binary:</span></span><br /><br /> <span data-ttu-id="a76c5-123">檢視文字格式顯示 AS2 訊息或 MDN 的內容人類看得懂的格式，就像 EDI 文字檔案一樣。</span><span class="sxs-lookup"><span data-stu-id="a76c5-123">-   Text Format view shows the contents of the AS2 message or MDN in human-readable form, as in an EDI text file.</span></span> <span data-ttu-id="a76c5-124">這個檢視會顯示 AS2 標頭、EDI 結尾和 EDI 內容，每個區段一行。</span><span class="sxs-lookup"><span data-stu-id="a76c5-124">This view shows the AS2 headers, EDI trailers, and EDI payload, with each segment on a separate line.</span></span><br /><span data-ttu-id="a76c5-125">-檢視二進位格式顯示 AS2 訊息或 MDN 的內容中非分隔的文字格式和 AS2 訊息或 MDN 中每個 ASCII 字元的十六進位表示的資料表。</span><span class="sxs-lookup"><span data-stu-id="a76c5-125">-   Binary Format view shows the contents of the AS2 message or MDN in non-delimited text format and a table of the hexadecimal representations for each ASCII character in the AS2 message or MDN.</span></span>|