---
title: "未預期的根項目 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecccf57e-9295-4a6d-95b6-efec662478cf
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5119b9b896b3b37b24b9b3151c5e11664dda8774
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="unexpected-root-element"></a>未預期的根項目
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|未預期的根項目|  
  
## <a name="explanation"></a>說明  
 標頭屬性不是處於\<標頭 >...\</headers > 格式。 這種情況通常適用於 InboundHeaders 和 OutboundCustomHeaders。  
  
## <a name="user-action"></a>使用者動作  
 請確認標頭屬性中的格式\<標頭 >...\</headers >。