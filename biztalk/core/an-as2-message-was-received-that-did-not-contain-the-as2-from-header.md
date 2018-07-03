---
title: 收到的 AS2 訊息不包含 AS2-From 標頭 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 899f9b21-b321-49a3-84bd-a5410c883968
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8471dfe16338f71785062eca4484ca53185931d
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37005263"
---
# <a name="an-as2-message-was-received-that-did-not-contain-the-as2-from-header"></a>收到的 AS2 訊息不包含 AS2-From 標頭
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |          收到的 AS2 訊息不包含 AS2-From 標頭          |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於內送 AS2 訊息不含代表訊息來源的 AS2-From 標頭，因此 BizTalk Server 無法處理該訊息。 AS2 訊息必須具有 AS2-From 標頭。 將會擱置訊息，如果它不需要 AS2-From 標頭。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   請確定傳送合作對象將 AS2-To 標頭與 AS2 訊息，再將它傳送的 HTTP、 AS2 和 MIME 標頭。