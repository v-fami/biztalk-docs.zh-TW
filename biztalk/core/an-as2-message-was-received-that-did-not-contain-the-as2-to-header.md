---
title: 收到的 AS2 訊息不包含 AS2-To 標頭 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 343a9b41-fcd9-4508-ac65-9b6e05ec6496
caps.latest.revision: 11
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0a2390406d202bebd74f45efd84fd3aae6db1137
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983463"
---
# <a name="an-as2-message-was-received-that-did-not-contain-the-as2-to-header"></a>收到的 AS2 訊息不包含 AS2-To 標頭
## <a name="details"></a>詳細資料  
  
|                 |                                                                                        |
|-----------------|----------------------------------------------------------------------------------------|
|  產品名稱   |   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]   |
| 產品版本 |               [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]               |
|    事件識別碼     |                                           -                                            |
|  事件來源   | [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI |
|    元件    |                                       AS2 引擎                                       |
|  符號名稱  |                                           -                                            |
|  訊息文字   |           收到的 AS2 訊息不包含 AS2-To 標頭           |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法處理內送 AS2 訊息，因為訊息不包含 AS2-To 標頭指出訊息的來源。 AS2 訊息必須具有 AS2-To 標頭。 將會擱置訊息，如果它不需要 AS2-To 標頭。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   請確定傳送合作對象將 AS2-To 標頭與 AS2 訊息，再將它傳送的 HTTP、 AS2 和 MIME 標頭。