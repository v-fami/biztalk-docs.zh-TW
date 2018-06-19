---
title: 單一登入： 事件 10762 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 516e120d-e72b-4f40-9a81-9131ea247dd0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 487fbeb0f077950605432861a9118eacd93f2c89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22276582"
---
# <a name="single-sign-on-event-10762"></a>單一登入： 事件 10762
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10762|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|ENTSSO_E_WRONG_THREAD|  
|訊息文字|SSO 用戶端元件已經在錯誤的執行緒上呼叫。 因為它有一項交易，所以目前被鎖定至執行緒。|  
  
## <a name="explanation"></a>說明  
 元件只能是多執行緒時不需要交易。 這個元件有交易，所以它已鎖定至執行緒。  
  
## <a name="user-action"></a>使用者動作  
 設定您的應用程式，讓它不會呼叫 SSO 用戶端元件在多個執行緒上使用交易時。