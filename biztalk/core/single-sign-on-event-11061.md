---
title: 單一登入： 事件 11061 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 52fb18e2-4482-4cdb-b8ed-d579a95acd7c
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e86ad25248952697e27fc732ddead6732065acf7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277470"
---
# <a name="single-sign-on-event-11061"></a>單一登入： 事件 11061
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|11061|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|SSO_WARN_BAD_PASSWORD_FILTER|  
|訊息文字|密碼篩選字串無效。 任何密碼篩選將不會 used.%r<br /><br /> 應用程式名稱: %1 %r<br /><br /> 密碼篩選字串: %2 %r<br /><br /> 處理的 Token 數目: %3 %r<br /><br /> 其他資料: %4 %r<br /><br /> 錯誤碼： %5|  
  
## <a name="explanation"></a>說明  
 已手動建立了無效的密碼篩選器。 在此程序中的某個時間點所導入錯誤 （請參閱錯誤位置的警告文字中的 「 密碼篩選字串 」）。  
  
## <a name="user-action"></a>使用者動作  
 若要建立密碼篩選器，使用 建立密碼篩選精靈，請參閱[如何使用密碼篩選](../core/how-to-use-password-filters.md)。