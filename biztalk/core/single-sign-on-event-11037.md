---
title: 單一登入： 事件 11037 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b523ff56-112e-4798-97d2-b1b19e130ec7
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ceec837a53d4cad3c236373a907497795efbd12a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36998895"
---
# <a name="single-sign-on-event-11037"></a>單一登入： 事件 11037
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                       |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                               企業單一登入                                                                                                               |
| 產品版本 |                                                                                              [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                               |
|    事件識別碼     |                                                                                                                         11037                                                                                                                         |
|  事件來源   |                                                                                                                        ENTSSO                                                                                                                         |
|    元件    |                                                                                                                          不適用                                                                                                                          |
|  符號名稱  |                                                                                                              SSO_INFO_PS_MAPPING_INVALID                                                                                                              |
|  訊息文字   | 外部密碼變更。 因為對應不再有效，所以外部帳戶的密碼未變更。%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 外部帳戶： %4 |
  
## <a name="explanation"></a>說明  
 對應不再是應用程式使用者群組的一部分。  
  
## <a name="user-action"></a>使用者動作  
 訊息列出外部帳戶和應用程式的名稱。 您可以使用這項資訊來找出對應不再有效的原因。