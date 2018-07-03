---
title: 單一登入： 事件 11008 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d7e11dbc-7596-45fa-ae54-a6e79498e60e
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7f3a77dcfb89a3040cf6c1acb71a053d57393591
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36983727"
---
# <a name="single-sign-on-event-11008"></a>單一登入： 事件 11008
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                           |
|-----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                 企業單一登入                                                                 |
| 產品版本 |                                                [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                 |
|    事件識別碼     |                                                                           11008                                                                           |
|  事件來源   |                                                                          ENTSSO                                                                           |
|    元件    |                                                                            不適用                                                                            |
|  符號名稱  |                                                                   SSO_WARN_CHECK_GROUP                                                                    |
|  訊息文字   | 檢查群組成員資格 failed.%r<br /><br /> 群組名稱: %1 %r<br /><br /> 帳戶名稱: %2 %r<br /><br /> 其他資料: %3 %r<br /><br /> 錯誤碼： %4 |
  
## <a name="explanation"></a>說明  
 這是最有可能因網路問題、 跨網域使用或的網域控制站混合層級 (例如，如果您的系統會使用兩個網域控制站時，才[!INCLUDE[btsWinSvr2k8R2](../includes/btswinsvr2k8r2-md.md)]和[!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)])。  
  
## <a name="user-action"></a>使用者動作  
 請檢查您的網路系統管理員，以查看是否有任何網路問題，或者您的系統有任何跨網域使用或的網域控制站混合層級。