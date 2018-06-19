---
title: 單一登入： 事件 10612 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b9d9e6f5-06b8-4989-a0dc-6e2e5980443b
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a85361bf9946efc283683d41ed0d08187e4d8754
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22271270"
---
# <a name="single-sign-on-event-10612"></a>單一登入： 事件 10612
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10612|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_TRANSACTION_TIMEOUT|  
|訊息文字|交易逾時超過此作業的建議最大值。 請參閱 details.%r 文件<br /><br /> 交易識別碼: %1 %r<br /><br /> 交易逾時： %2 分鐘 （輸入 0 表示無限逾時） %r<br /><br /> 最大建議的值： %3 分鐘|  
  
## <a name="explanation"></a>說明  
 交易已進入具有非常多的逾時值的系統。 如果 ENTSSO 系統輪詢 SSO 資料庫鎖定的長時間執行交易時，系統將最終會離線。  
  
## <a name="user-action"></a>使用者動作  
 使用者不必採取任何動作。