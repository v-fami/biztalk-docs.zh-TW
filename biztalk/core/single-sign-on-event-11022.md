---
title: "單一登入： 事件 11022 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c65ca12b-dda8-408b-9512-39df6f8e035b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccae36e9beef672e6c5fb7917c88341ce4bb3c08
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11022"></a>單一登入： 事件 11022
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11022|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_EXTERNAL_TO_EXTERNAL_MAPPING_CONFLICT_NOT_ALLOWED|  
|訊息文字|外部密碼變更可能已造成不同的外部帳戶 changed.%r<br /><br /> 這不讓因為這個外部系統的配接器已設定為允許對應 conflicts.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> Windows 帳戶: %3 %r<br /><br /> 外部帳戶 1: %4 %r<br /><br /> 外部帳戶 2: %5|  
  
## <a name="explanation"></a>說明  
 這是參考用訊息報告的外部密碼變更可能已造成不同的外部帳戶變更失敗。  
  
## <a name="user-action"></a>使用者動作  
 雖然沒有任何變更 （因為此系統設定為不允許對應衝突），您應該確認立即，此嘗試與您的知識和授權。 如果是的話，不不需要任何動作。 如果沒有，找出變更其中起始，並確認它安全地在系統中的位置。