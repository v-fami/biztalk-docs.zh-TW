---
title: 單一登入： 事件 10551 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 33434989-08d8-4d13-a3cc-4c5543add69c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 30c4b315744749d232c30f4cc28c4d297a0f5243
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22270742"
---
# <a name="single-sign-on-event-10551"></a>單一登入： 事件 10551
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10551|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_INVALID_USER|  
|訊息文字|無法建立對應，因為此應用程式的指定使用者無效。%r<br /><br /> 網域名稱: %1 %r<br /><br /> 使用者名稱: %2 %r<br /><br /> 應用程式名稱: %3 %r<br /><br /> 應用程式使用者： %4|  
  
## <a name="explanation"></a>說明  
 指定的使用者無效。 這可能是打字的錯誤。  
  
## <a name="user-action"></a>使用者動作  
 檢查警告資訊中列出的使用者名稱，確認它是正確的，然後再次建立對應。