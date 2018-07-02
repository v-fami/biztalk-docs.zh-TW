---
title: 單一登入： 事件 10563 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c944cc4-7fe0-41cc-9608-ee954e8222e0
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 49fc95cf7c257febd6ab631dcc016598dd2e4e24
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36976502"
---
# <a name="single-sign-on-event-10563"></a>單一登入： 事件 10563
## <a name="details"></a>詳細資料  
  
|                 |                                                                      |
|-----------------|----------------------------------------------------------------------|
|  產品名稱   |                      企業單一登入                       |
| 產品版本 |      [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]      |
|    事件識別碼     |                                10563                                 |
|  事件來源   |                                ENTSSO                                |
|    元件    |                                 不適用                                  |
|  符號名稱  |                       SSO_WARN_PERFMON_FAILED                        |
|  訊息文字   | 效能監控無法 start.%r<br /><br /> 錯誤碼： %1 |
  
## <a name="explanation"></a>說明  
 效能監視無法啟動。 系統會繼續正常執行，但效能監視將無法使用。  
  
## <a name="user-action"></a>使用者動作  
 它可能需要先解除安裝再重新安裝 perfmon 的公用程式。