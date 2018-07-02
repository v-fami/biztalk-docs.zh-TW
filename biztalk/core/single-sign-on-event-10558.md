---
title: 單一登入： 事件 10558 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84637b67-09df-4c1e-b9f2-85a738ba0d7a
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d9a281d6a6ca20a274db4b3ffe5b2697ff812c2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36974864"
---
# <a name="single-sign-on-event-10558"></a>單一登入： 事件 10558
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                              |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                  企業單一登入                                                                                   |
| 產品版本 |                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                  |
|    事件識別碼     |                                                                                            10558                                                                                             |
|  事件來源   |                                                                                            ENTSSO                                                                                            |
|    元件    |                                                                                             不適用                                                                                              |
|  符號名稱  |                                                                                  SSO_WARN_USER_OWN_MAPPINGS                                                                                  |
|  訊息文字   | 只允許應用程式使用者控制自己的 mappings.%r<br /><br /> 網域名稱: %1 %r<br /><br /> 使用者名稱: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 用戶端使用者： %4 |
  
## <a name="explanation"></a>說明  
 嘗試透過應用程式使用者控制不同使用者的對應。 但這種作法並不合法。  
  
## <a name="user-action"></a>使用者動作  
 只針對這些特定的對應應用程式使用者可以控制對應。