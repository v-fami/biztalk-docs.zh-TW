---
title: EDI 訊息內容狀態報告 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29acab25-354d-42f0-b6e3-37ebca47addb
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 62dbb260bb23e3ed5de7e8d416158a0e142c6c32
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22238862"
---
# <a name="edi-message-content-status-report"></a><span data-ttu-id="0a369-102">EDI 訊息內容狀態報告</span><span class="sxs-lookup"><span data-stu-id="0a369-102">EDI Message Content Status Report</span></span>

## <a name="overview"></a><span data-ttu-id="0a369-103">概觀</span><span class="sxs-lookup"><span data-stu-id="0a369-103">Overview</span></span>
<span data-ttu-id="0a369-104">此狀態報告會顯示交易集的標頭和內容。</span><span class="sxs-lookup"><span data-stu-id="0a369-104">This status report displays the headers and payload of a transaction set.</span></span> <span data-ttu-id="0a369-105">這個報表顯示以滑鼠右鍵按一下 交易集內交易集詳細資料狀態報告中，然後按一下**檢視交易集內容**。</span><span class="sxs-lookup"><span data-stu-id="0a369-105">You display this report by right-clicking a transaction set within the Transaction Set Details status report, and then clicking **View Transaction Set Content**.</span></span>  
  
 <span data-ttu-id="0a369-106">此報表是您已選取時，才可以使用**儲存交易集/內容 reporting**相關合作對象 [EDI 屬性] 對話方塊的 [一般] 頁面中的屬性。</span><span class="sxs-lookup"><span data-stu-id="0a369-106">This report is available only if you have selected the **Store transaction set/payload for reporting** property in the General Page of the EDI Properties dialog box for the related party.</span></span>  
  
 <span data-ttu-id="0a369-107">此報告會提供兩個內容檢視：</span><span class="sxs-lookup"><span data-stu-id="0a369-107">This report provides two views of the content:</span></span>  
  
-   <span data-ttu-id="0a369-108">[文字格式] 檢視：以一般人可讀取的格式顯示交易集的內容，就像 EDI 文字檔案一樣。</span><span class="sxs-lookup"><span data-stu-id="0a369-108">A Text Format view that shows the contents of the transaction set in human-readable form, as in an EDI text file.</span></span> <span data-ttu-id="0a369-109">這個檢視會顯示 ST 標頭、交易集內容和 SE 結尾，每個區段一行。</span><span class="sxs-lookup"><span data-stu-id="0a369-109">This view shows the ST header, the transaction set payload, and the SE trailer, with each segment on a separate line.</span></span>  
  
-   <span data-ttu-id="0a369-110">[二進位格式] 檢視：以不分隔的文字格式顯示交易集的內容，交易集的每個 ASCII 字元一個十六進位表示的資料表。</span><span class="sxs-lookup"><span data-stu-id="0a369-110">A Binary Format view that shows the contents of the transaction set in non-delimited text format and a table of the hexadecimal representations for each ASCII character in the transaction set.</span></span>  
  
