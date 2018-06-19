---
title: 訊息類型，而不支援部分 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0bfb042-feda-4282-a7fa-c13be4ff6254
caps.latest.revision: 10
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e3e6cc0f5d4a2ae18ff6bcb5fa0dc8ef605d730
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22263102"
---
# <a name="message-types-without-parts-are-not-supported"></a>不支援沒有部分訊息類型
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|不支援部分訊息類型。 更正服務描述"{0}"訊息類型 」 {1}"，然後再重新執行精靈。|  
  
## <a name="explanation"></a>說明  
 此錯誤表示嘗試從中使用的服務並沒有定義的訊息類型。  
  
## <a name="user-action"></a>使用者動作  
 更正服務與適當的訊息類型，然後再次嘗試使用 （如果您擁有想要使用的 WCF 服務）。 否則，請連絡服務提供者。  如需有關訊息的詳細資訊，請參閱下列資源中的[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]協助：  
  
-   [建構 Web 訊息](../core/constructing-web-messages.md)