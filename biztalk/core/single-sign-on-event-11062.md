---
title: 單一登入： 事件 11062 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 55c7c2ea-c671-4853-ac64-8cb80bba98b0
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50df4834f92eff7cc679c051f529f4dbaefc4335
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36970136"
---
# <a name="single-sign-on-event-11062"></a>單一登入： 事件 11062
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                        |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                       企業單一登入                                                                                        |
| 產品版本 |                                                                       [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                       |
|    事件識別碼     |                                                                                                 11062                                                                                                  |
|  事件來源   |                                                                                                 ENTSSO                                                                                                 |
|    元件    |                                                                                                  不適用                                                                                                   |
|  符號名稱  |                                                                                    SSO_WARN_PASSWORD_FILTER_FAILED                                                                                     |
|  訊息文字   | 密碼篩選失敗。 任何密碼篩選將不會 used.%r<br /><br /> 應用程式名稱: %1 %r<br /><br /> 密碼篩選字串: %2 %r<br /><br /> 其他資料: %3 %r<br /><br /> 錯誤碼： %4 |
  
## <a name="explanation"></a>說明  
 建立密碼篩選條件時發生錯誤，無法建立篩選條件。  
  
## <a name="user-action"></a>使用者動作  
 若要建立密碼篩選器使用 建立密碼篩選器精靈，請參閱[如何使用密碼篩選](../core/how-to-use-password-filters.md)。