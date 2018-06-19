---
title: 空白的 AS2 訊息已接收並暫停 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 349f7134-d039-44ab-b2b3-d378d38dfd38
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90c8221c7e0bd5b297b33118b8672fbe55612244
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22230126"
---
# <a name="an-empty-as2-message-was-received-and-suspended"></a>空白的 AS2 訊息已接收並暫停
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|-|  
|訊息文字|收到空白的 AS2 訊息。  將擱置此訊息。|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示 BizTalk Server 無法處理內送 AS2 訊息，因為訊息不包含主體。 主體必須以兩個歸位字元 / 摘要分隔標頭。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，執行下列作業：  
  
-   請確定傳送合作對象將 AS2 訊息內文 （從標頭以兩個歸位字元 / 摘要分隔），再將它傳送。