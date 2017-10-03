---
title: "單一登入： 事件 10753 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6b538083-180b-4a15-bedf-aac4fc351c30
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6fc43f8ffba195b7a0156a9004d140f1e3c585db
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10753"></a>單一登入： 事件 10753
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10753|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|ENTSSO_E_MAPPING_EXISTS|  
|訊息文字|對應已經存在。|  
  
## <a name="explanation"></a>說明  
 對應已經存在，已在使用中的 Windows 帳戶或外部的帳戶。  
  
## <a name="user-action"></a>使用者動作  
 檢查現有的對應與您嘗試建立的對應。 如果您想要已的對應存在，使用它，並刪除新。 如果沒有，請刪除新，並重新建立它。