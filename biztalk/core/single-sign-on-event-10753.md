---
title: 單一登入： 事件 10753 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6b538083-180b-4a15-bedf-aac4fc351c30
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 10fb7980b8c039c6ef02e52952564c581e88054b
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36969079"
---
# <a name="single-sign-on-event-10753"></a>單一登入： 事件 10753
## <a name="details"></a>詳細資料  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10753                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                            不適用                             |
|  符號名稱  |                  ENTSSO_E_MAPPING_EXISTS                   |
|  訊息文字   |                對應已經存在。                 |
  
## <a name="explanation"></a>說明  
 此對應已經存在，已在使用中的 Windows 帳戶或外部的帳戶。  
  
## <a name="user-action"></a>使用者動作  
 檢查現有的對應與您嘗試建立的對應。 如果您已經想要的對應存在，使用它，並刪除您新的一個。 如果沒有，請刪除您的新帳戶，並重新建立它。