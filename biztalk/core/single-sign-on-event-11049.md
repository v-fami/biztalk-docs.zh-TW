---
title: 單一登入： 事件 11049 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 031ec1a6-4b2b-46b2-9dbb-5525d758651f
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b86cf3d5361a912cd976d8a27e83981b71237e2
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36997503"
---
# <a name="single-sign-on-event-11049"></a>單一登入： 事件 11049
## <a name="details"></a>詳細資料  
  
|                 |                                                                |
|-----------------|----------------------------------------------------------------|
|  產品名稱   |                   企業單一登入                    |
| 產品版本 |   [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]   |
|    事件識別碼     |                             11049                              |
|  事件來源   |                             ENTSSO                             |
|    元件    |                              不適用                               |
|  符號名稱  |                      SSO_ERROR_DTC_FAILED                      |
|  訊息文字   | 無法取得 MSDTC。 SSO 需要 MSDTC，才能正常運作。 |
  
## <a name="explanation"></a>說明  
 ENTSSO 系統無法連接至 Microsoft 分散式交易協調器 (MSDTC)。  
  
## <a name="user-action"></a>使用者動作  
 請檢查 MSDTC 目前是否正在運作。  
  
 如需 MSDTC 問題的說明，請參閱 < [MSDTC 問題疑難排解](../core/troubleshooting-problems-with-msdtc.md)。