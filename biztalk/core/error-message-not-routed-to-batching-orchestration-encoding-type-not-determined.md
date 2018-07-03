---
title: 訊息無法傳送至批次處理協調流程，因為無法判斷編碼類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0d2ee38d-22c0-4fcf-bb68-b2ef00088c4c
caps.latest.revision: 9
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 777f23ccfc1b79e2fca4ece8e67370513723ac27
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36990183"
---
# <a name="the-message-cannot-be-routed-to-the-batching-orchestration-as-the-encoding-type-could-not-be-determined"></a>訊息無法傳送至批次處理協調流程，因為無法判斷編碼類型
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                             |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                     [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                                      |
| 產品版本 |                                                                 [!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]                                                                  |
|    事件識別碼     |                                                                                              -                                                                                              |
|  事件來源   |                                                   [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI                                                    |
|    元件    |                                                                                       批次引擎                                                                                       |
|  符號名稱  |                                                                                     UnknownEncodingType                                                                                     |
|  訊息文字   | 訊息無法路由傳送到批次處理協調流程，因為無法判斷編碼類型。 編碼類型必須是 X12 或 EDIFACT 批次處理的訊息。 |
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示非 EDI 批次元素已無法路由傳送到批次處理協調流程執行個體，即使交易集符合篩選準則進行批次處理。 交易集無法路由，批次處理協調流程執行個體因為 EDI。對於 EDIFACT 不 EncodingType 內容屬性升級為 X12 或 1 的 0 值。 當批次元素已路由傳送到路由協調流程中，BatchMarker 管線元件，但非 EDI 批次項目所對應並未轉換成 EDI 訊息時，就會發生此錯誤。 如此一來，路由協調流程無法判斷 EDI 標頭的編碼類型。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定非 EDI 訊息的對應來轉換成 EDI 訊息之前它會路由至路由協調流程。 您也必須包含自訂管線元件 （使用 BatchMarker 元件中） 或自訂協調流程來處理非 EDI 批次項目。 如需詳細資訊，請參閱 「 組合批次 EDI 交換 」，在[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助。