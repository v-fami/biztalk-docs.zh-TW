---
title: 無效的 AS2-若要設定合作對象名稱 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a203e5f2-d1d9-433f-b2bb-d679bb8fea58
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c06adc5a459f7dfd05508312494555fb2651114
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22257366"
---
# <a name="invalid-as2-to-name-configured-for-party"></a>無效的 AS2-若要設定合作對象名稱
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|InvalidAS2ToNameConfiguredError|  
|訊息文字|無效的 AS2-若要設定合作對象名稱： {0} 值： {1}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，AS2 編碼器或解碼器無法處理 AS2 訊息因為值的 AS2-To 標頭已設定為識別合作對象不符合 AS2 RFC 4130 中的規格。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定 AS2-To 標頭已設定為合作對象符合 AS2 RFC 4130 第 6.2 節的規格。