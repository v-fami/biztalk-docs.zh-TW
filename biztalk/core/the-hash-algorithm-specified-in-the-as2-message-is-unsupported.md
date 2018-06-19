---
title: AS2 訊息中指定的雜湊演算法不支援 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1b292238-f964-4275-bbfa-e21c9150abf7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f6d16c7a3336a798c18b484bc50ff3e2f0c69764
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22279294"
---
# <a name="the-hash-algorithm-specified-in-the-as2-message-is-unsupported"></a>AS2 訊息中指定的雜湊演算法不支援
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|UnsupportedAS2HashAlgorithmError|  
|訊息文字|不支援 AS2 訊息中指定的雜湊演算法。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法產生指定 MDN 因為指定收到的 AS2 訊息的簽署回條 micalg 標頭中的 MIC 雜湊演算法不是有效的值。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，訊息變更 MD5 或 SHA1 演算法的傳送者與重新傳送訊息。