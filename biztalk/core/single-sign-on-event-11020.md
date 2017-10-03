---
title: "單一登入： 事件 11020 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa6a0d72-ece6-4094-9263-dbf69bb068c8
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 444a61beec74a9d7141df79d05d8863cc10d6dc6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-11020"></a>單一登入： 事件 11020
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11020|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_INFO_WINDOWS_TO_WINDOWS_MAPPING_CONFLICT_ALLOWED|  
|訊息文字|Windows 密碼變更將造成不同的 Windows 帳戶 changed.%r<br /><br /> 這被允許的因為這個外部系統的配接器已設定為允許對應 conflicts.%r<br /><br /> 追蹤識別碼: %1 %r<br /><br /> 配接器: %2 %r<br /><br /> 外部帳戶: %3 %r<br /><br /> Windows 帳戶 1: %4 %r<br /><br /> Windows 帳戶 2: %5|  
  
## <a name="explanation"></a>說明  
 這是資訊訊息，指出 Windows 密碼變更將造成不同 Windows 帳戶變更。  
  
## <a name="user-action"></a>使用者動作  
 您應該立即確認這項變更為了與您的知識和授權。 如果是的話，不不需要任何動作。 如果沒有，找出變更其中起始，並確認它安全地在系統中的位置。