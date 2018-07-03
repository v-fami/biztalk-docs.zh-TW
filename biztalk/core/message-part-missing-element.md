---
title: 訊息部分遺失元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b519315f-d51d-4ca3-a0e6-d08bb920c6c5
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 412b25d2f7ea027de53818b032b50562faab9865
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37009439"
---
# <a name="message-part-missing-element"></a>訊息部分遺失元素
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                    |
|-----------------|--------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                 |
| 產品版本 |                             [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                             |
|    事件識別碼     |                                                         0                                                          |
|  事件來源   |                                                         0                                                          |
|    元件    |                                                         0                                                          |
|  符號名稱  |                                                         0                                                          |
|  訊息文字   | 訊息部分遺失元素。 更正服務描述"{0}」 訊息類型 」{1}「 部分 」{2}"，然後重新執行精靈 |
  
## <a name="explanation"></a>說明  
 此錯誤表示嘗試從中使用的服務並沒有用來識別訊息類型的元素標記。  
  
## <a name="user-action"></a>使用者動作  
 更正服務與適當的訊息類型，然後再次嘗試使用 （如果您擁有想要使用的 WCF 服務時）。 否則，請連絡服務提供者。  
  
 如需其他有關訊息的詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]幫助：  
  
-   [建構 Web 訊息](../core/constructing-web-messages.md)