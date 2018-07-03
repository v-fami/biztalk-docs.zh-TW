---
title: 單一登入： 事件 10590 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fd8c3804-5c84-403f-881b-e4b101c2323a
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc2ac48ecf1279c1a8347e8f1ab3bcd1367854ff
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37006767"
---
# <a name="single-sign-on-event-10590"></a>單一登入： 事件 10590
## <a name="details"></a>詳細資料  
  
|                 |                                                            |
|-----------------|------------------------------------------------------------|
|  產品名稱   |                 企業單一登入                  |
| 產品版本 | [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)] |
|    事件識別碼     |                           10590                            |
|  事件來源   |                           ENTSSO                           |
|    元件    |                            不適用                             |
|  符號名稱  |                  SSO_ERROR_OUT_OF_SERVICE                  |
|  訊息文字   |        企業單一登入 」 即將離線。         |
  
## <a name="explanation"></a>說明  
 ENTSSO 系統通常會檢查 ENTSSO 資料庫的更新每隔 30 秒。 如果資料庫無法使用指定的時間 （通常為 5 分鐘），系統本身會離線。 處於此狀態，系統不會回應要求的認證。 仍可能會有一些離線和系統管理活動。  
  
## <a name="user-action"></a>使用者動作  
 此錯誤表示 ENTSSO 資料庫已離線。 您應該立即調查。