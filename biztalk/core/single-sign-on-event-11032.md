---
title: 單一登入： 事件 11032 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3d58cf9d-6806-4580-8014-7eff88d5cc5f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4dc69ecf447f0917f843a0f80a0a25b1ed0b6e0a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37022044"
---
# <a name="single-sign-on-event-11032"></a>單一登入： 事件 11032
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                  |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                            企業單一登入                                                                                                                             |
| 產品版本 |                                                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                            |
|    事件識別碼     |                                                                                                                                      11032                                                                                                                                       |
|  事件來源   |                                                                                                                                      ENTSSO                                                                                                                                      |
|    元件    |                                                                                                                                       不適用                                                                                                                                        |
|  符號名稱  |                                                                                                                     SSO_INFO_PS_WIN_CHANGE_MAPPING_DISABLED                                                                                                                      |
|  訊息文字   | Windows 密碼變更。 已偵測到此 Windows 帳戶的對應，但忽略，因為它是 disabled.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> Windows 帳戶: %2 %r<br /><br /> 應用程式: %3 %r<br /><br /> 外部帳戶: %4 %r<br /><br /> 用戶端使用者： %5 |
  
## <a name="explanation"></a>說明  
 已偵測到此 Windows 帳戶的對應，但忽略，因為它已停用。  
  
## <a name="user-action"></a>使用者動作  
  
-   若要啟用對應，請參閱[如何啟用使用者對應](../core/how-to-enable-a-user-mapping.md)。