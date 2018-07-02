---
title: 嘗試將 AS2 訊息解碼時發生 BTS MIME 錯誤 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65cb5ece-78e4-4b83-b126-4d8c588b2c61
caps.latest.revision: 13
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 629e09e950a6c49263230f23725002eee9be905b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36985919"
---
# <a name="a-bts-mime-error-was-encountered-when-attempting-to-decode-an-as2-message"></a>嘗試將 AS2 訊息解碼時發生 BTS MIME 錯誤
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                    |
|-----------------|------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                         [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                         |
| 產品版本 |                                     [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                     |
|    事件識別碼     |                                                                 -                                                                  |
|  事件來源   |                                                         BizTalk Server EDI                                                         |
|    元件    |                                                             AS2 引擎                                                             |
|  符號名稱  |                                                                 -                                                                  |
|  訊息文字   | 嘗試將 AS2 訊息解碼時發生 BTS MIME 錯誤。  AS2-從： {0}，AS2-到： {1}，MessageId: {2}，錯誤： {3} |
  
## <a name="explanation"></a>說明  
 當使用 BizTalk MIME 元件處理某些部分的MIME 處理時會發生此錯誤。  
  
## <a name="user-action"></a>使用者動作  
 完整的錯誤訊息提供 MIME 元件發生之問題的相關資訊。 請參閱 BTS MIME 錯誤資訊以便診斷問題 （這是因為 AS2 元件會使用 BizTalk MIME 元件組件的 MIME 處理）。