---
title: 單一登入： 事件 10855 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ba244f8e-bc61-475f-913c-475ebf1c69ee
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c2d5914cc119a68c109b883c888b3898bc7db07e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36986447"
---
# <a name="single-sign-on-event-10855"></a>單一登入： 事件 10855

|                 |                                                                        |
|-----------------|------------------------------------------------------------------------|
|  產品名稱   |                       企業單一登入                        |
| 產品版本 |       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]       |
|    事件識別碼     |                                 10855                                  |
|  事件來源   |                                 ENTSSO                                 |
|    元件    |                                  不適用                                   |
|  符號名稱  |                    ENTSSO_E_PASSWORD_FILTER_FAILED                     |
|  訊息文字   | 無法傳回認證，因為密碼篩選失敗。 |

## <a name="explanation"></a>說明  
 密碼篩選器不是有效的。 這最可能的原因是，篩選手動建立，但不建議這麼做。  

## <a name="user-action"></a>使用者動作  
 建立密碼篩選器一次使用 建立篩選器精靈。