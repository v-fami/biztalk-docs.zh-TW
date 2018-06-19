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
# <a name="as2-message-content-status-reports"></a>AS2 訊息內容狀態報告

## <a name="overview"></a>概觀
這些狀態報告會顯示 AS2 訊息或 MDN 的內容屬性、標頭和內容。 AS2 訊息內容狀態報告有三種：  
  
-   訊息電傳格式報告  
  
-   訊息解碼格式報告  
  
-   Mdn 訊息報告  
  
 您以滑鼠右鍵按一下 [AS2/MDN 狀態] 報告中的 AS2 訊息，然後按一下其中一種報告顯示**檢視訊息電傳格式**，**檢視訊息解碼格式**，或**檢視 Mdn訊息**。 MDN 命令會顯示 AS2 訊息相互關聯的 MDN。  
  
 這些報告只有在您針對相關合作對象，於 [AS2 屬性] 對話方塊的 [做為 AS2 訊息傳送者的合作對象] 或 [做為 AS2 訊息接收者的合作對象] 頁面中選取對應的 [將訊息儲存在不可否認性的資料庫中] 屬性時才會提供。 這些命令會將 AS2 訊息或 MDN 以電傳格式或解碼格式儲存在 BizTalkDTADb 資料庫中。  
  
 這份報告使用**訊息詳細資料屬性對話方塊**(請參閱 UI 的詳細資料[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]) 顯示訊息資料，以分隔到頁面的資訊：  
  
|頁面|顯示資料|  
|----------|--------------------|  
|**一般**|訊息的概觀資訊|  
|**內容**|與此訊息相關聯的內容屬性|  
|**訊息部分**|包含此訊息在個別的文件內容。 每份文件都可視為文字或二進位檔：<br /><br /> 檢視文字格式顯示 AS2 訊息或 MDN 的內容人類看得懂的格式，就像 EDI 文字檔案一樣。 這個檢視會顯示 AS2 標頭、EDI 結尾和 EDI 內容，每個區段一行。<br />-檢視二進位格式顯示 AS2 訊息或 MDN 的內容中非分隔的文字格式和 AS2 訊息或 MDN 中每個 ASCII 字元的十六進位表示的資料表。|