---
title: 無效的 AS2-從合作對象設定名稱 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cde739bd-f6f7-4e4a-8f02-9a99e9d82fc9
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c370476eeccc085783c761cefb41a52eead8e208
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22256974"
---
# <a name="invalid-as2-from-name-configured-for-party"></a>無效的 AS2-從設定合作對象名稱
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|AS2 引擎|  
|符號名稱|InvalidAS2FromNameConfiguredError|  
|訊息文字|無效的 AS2-從合作對象設定名稱： {0} 值： {1}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，AS2 編碼器或解碼器無法處理 AS2 訊息因為 AS2 的值-從已設定為識別合作對象不符合 AS2 RFC 4130 中規格的標頭。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請確定 AS2-從已設定為合作對象符合 AS2 RFC 4130 第 6.2 部分中的規格，而且再有訊息重新傳送的標頭。