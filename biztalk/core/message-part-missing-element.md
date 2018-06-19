---
title: 訊息部分遺失元素 |Microsoft 文件
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
ms.openlocfilehash: 1dd5a423a34d8b6ddf8f4689351b0f6dbcef53c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263038"
---
# <a name="message-part-missing-element"></a>訊息部分遺失元素
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|訊息部分遺失元素。 更正服務描述"{0}"訊息類型 」 {1} 「 部分 」 {2}"，然後再重新執行精靈|  
  
## <a name="explanation"></a>說明  
 此錯誤表示嘗試從中使用服務不需要識別的訊息類型的項目標記。  
  
## <a name="user-action"></a>使用者動作  
 更正服務與適當的訊息類型，然後再次嘗試使用 （如果您擁有想要使用的 WCF 服務）。 否則，請連絡服務提供者。  
  
 如需有關訊息的詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [建構 Web 訊息](../core/constructing-web-messages.md)