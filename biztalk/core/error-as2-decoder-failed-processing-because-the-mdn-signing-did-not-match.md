---
title: AS2 解碼器處理失敗，因為 MDN 簽章不符合我們的要求 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9a42d344-fc28-4bc4-9328-46158f15a008
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cc0660a64ff0aeb35976ad1aa45a602d8db0913a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22239974"
---
# <a name="the-as2-decoder-failed-processing-because-the-mdn-signing-did-not-match-our-request"></a>AS2 解碼器處理失敗，因為 MDN 簽章不符合我們的要求
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|AS2DecoderMdnSigningMismatchFailureDuringProcessing|  
|訊息文字|AS2 解碼器處理失敗，因為 MDN 簽章不符合我們的要求。  MDN 訊息的詳細資料如下： AS2-從:"{0}"AS2-到:"\ {1 \}"MessageID:"\ {2 \}"OriginalMessageID:"\ {3\}"|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示接收管線無法處理內送 MDN 是因為在已簽署的 MDN，但簽章未要求 MDN 或將 MDN 是不帶正負號，但簽章要求 mdn。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列其中一項：  
  
1.  變更以符合要求 MDN 簽章要求。 若要這樣做，請開啟合作對象當做 AS2 訊息接收者 頁面的 AS2 屬性 對話方塊中，與所選取的 要求 MDN 屬性，選取或清除 要求簽署的 MDN 屬性。  
  
2.  若要解決與否，是否應該簽署 Mdn 原始 AS2 訊息接收者，請連絡。