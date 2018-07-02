---
title: 單一登入： 事件 10551 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33434989-08d8-4d13-a3cc-4c5543add69c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8a014d9fa9adec99a05eba3f4a0f17047e2e1175
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36973487"
---
# <a name="single-sign-on-event-10551"></a>單一登入： 事件 10551
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                               |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                   企業單一登入                                                                                                   |
| 產品版本 |                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                   |
|    事件識別碼     |                                                                                                             10551                                                                                                             |
|  事件來源   |                                                                                                            ENTSSO                                                                                                             |
|    元件    |                                                                                                              不適用                                                                                                              |
|  符號名稱  |                                                                                                     SSO_WARN_INVALID_USER                                                                                                     |
|  訊息文字   | 無法建立對應，因為此應用程式的指定使用者無效。%r<br /><br /> 網域名稱: %1 %r<br /><br /> 使用者名稱: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 應用程式使用者： %4 |
  
## <a name="explanation"></a>說明  
 指定的使用者無效。 這可能是打字的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 檢查警告資訊中列出的使用者名稱，確認它是正確的，然後再次建立對應。