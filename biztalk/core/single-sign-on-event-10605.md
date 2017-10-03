---
title: "單一登入： 事件 10605 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c9812b4-43bc-43c4-be8f-6f57c432bda6
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3e7d0fb4befaacd8734f866f2c11c7446d4e5854
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10605"></a>單一登入： 事件 10605
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10605|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_ERROR_DTC_IMPORT|  
|訊息文字|無法匯入 DTC 交易。 請檢查 MSDTC 已正確設定為支援遠端作業。 請參閱 details.%r 文件<br /><br /> 錯誤碼： %1|  
  
## <a name="explanation"></a>說明  
 Microsoft 分散式交易協調器 (MSDTC) 發生問題。  
  
## <a name="user-action"></a>使用者動作  
 如需 MSDTC 問題的說明，請參閱[疑難排解 MSDTC 問題的](../core/troubleshooting-problems-with-msdtc.md)。