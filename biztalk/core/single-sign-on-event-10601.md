---
title: 單一登入： 事件 10601 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2624025e-b7a8-43b9-aa7e-6811a2fc3278
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ea1dfbcc36cc83498aa316cedeab8fc46a2f4dd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36987735"
---
# <a name="single-sign-on-event-10601"></a>單一登入： 事件 10601
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                                                                                                              |
|-----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                                                                  企業單一登入                                                                                                                   |
| 產品版本 |                                                                                                  [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                                                                  |
|    事件識別碼     |                                                                                                                            10601                                                                                                                             |
|  事件來源   |                                                                                                                            ENTSSO                                                                                                                            |
|    元件    |                                                                                                                             不適用                                                                                                                              |
|  符號名稱  |                                                                                                                    SSO_WARN_INVALID_FLAGS                                                                                                                    |
|  訊息文字   | 指定的旗標不適用於建立這個類型的應用程式。<br /><br /> 請參閱 details.%r 文件<br /><br /> 應用程式名稱: %1 %r<br /><br /> 指定的旗標: %2 %r<br /><br /> 允許的旗標: %3 %r<br /><br /> 不允許的旗標： %4 |
  
## <a name="explanation"></a>說明  
 指定的旗標不適用於建立這個類型的應用程式。 警告列出而言，應用程式，以及允許的旗標和不可。  
  
## <a name="user-action"></a>使用者動作  
 重新建立應用程式的警告訊息中所述的指導方針。