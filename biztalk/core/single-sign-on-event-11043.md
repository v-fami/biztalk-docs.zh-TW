---
title: 單一登入： 事件 11043 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 128d68fb-1905-49b3-9b67-30a9442569cc
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 99faeaefdd029995944033cdb77c6636e716ed5a
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37024540"
---
# <a name="single-sign-on-event-11043"></a>單一登入： 事件 11043
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                                                                                   |
|-----------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                                             企業單一登入                                                                                                                                             |
| 產品版本 |                                                                                                                            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                                             |
|    事件識別碼     |                                                                                                                                                       11043                                                                                                                                                       |
|  事件來源   |                                                                                                                                                      ENTSSO                                                                                                                                                       |
|    元件    |                                                                                                                                                        不適用                                                                                                                                                        |
|  符號名稱  |                                                                                                                                       SSO_WARN_PS_ADAPTER_REPORTED_FAILURE                                                                                                                                        |
|  訊息文字   | 密碼同步配接器報告在嘗試變更外部密碼時失敗。 在 SSO 資料庫中未更新外部密碼。%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 外部帳戶: %3 %r<br /><br /> 錯誤訊息: %4 %r<br /><br /> 錯誤碼： %5 |
  
## <a name="explanation"></a>說明  
 當 ENTSSO 密碼同步配接器來傳送密碼變更時，ENTSSO 會讓它在 SSO 資料庫中之前，先，必須是已成功變更外部密碼。 在此情況下，並未發生。  
  
## <a name="user-action"></a>使用者動作  
 請注意警告訊息中的資訊，請連絡系統管理員。