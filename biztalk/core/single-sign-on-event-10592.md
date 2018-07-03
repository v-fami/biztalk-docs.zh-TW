---
title: 單一登入： 事件 10592 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e044f9bd-c384-4f08-81f0-699e0c774c45
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b9fdf7259de2217c2e6cd616f58b3b1118bf991c
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37017254"
---
# <a name="single-sign-on-event-10592"></a>單一登入： 事件 10592
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                    |
|-----------------|----------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                             企業單一登入                                                              |
| 產品版本 |                                             [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                             |
|    事件識別碼     |                                                                       10592                                                                        |
|  事件來源   |                                                                       ENTSSO                                                                       |
|    元件    |                                                                        不適用                                                                         |
|  符號名稱  |                                                           SSO_WARN_TICKET_DECRYPT_FAILED                                                           |
|  訊息文字   | 票證無法解密。 票證無效或它可能會有 expired.%r<br /><br /> 應用程式名稱: %1 %r<br /><br /> 錯誤碼： %2 |
  
## <a name="explanation"></a>說明  
 票證無效，或可能已過期。  
  
## <a name="user-action"></a>使用者動作  
 請確認您想要使用的票證有效，且尚未過期。