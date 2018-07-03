---
title: 不支援 AS2 訊息中指定的雜湊演算法 |Microsoft Docs
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
ms.openlocfilehash: 8c3c46f65fb71ef810fc4e657df01e0065757cae
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37008591"
---
# <a name="the-hash-algorithm-specified-in-the-as2-message-is-unsupported"></a>不支援 AS2 訊息中指定的雜湊演算法
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                            UnsupportedAS2HashAlgorithmError                            |
|  訊息文字   |            不支援 AS2 訊息中指定的雜湊演算法。             |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，接收管線無法產生 MDN 所指定因為收到的 AS2 訊息的簽署回條 micalg 標頭中指定的 MIC 雜湊演算法不是有效的值。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，將傳送者的訊息變更演算法 MD5 或 SHA1，與重新傳送訊息。