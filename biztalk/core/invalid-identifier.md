---
title: 無效的識別項 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f87e1e42-457f-4d04-a1d2-6b796f3fa7b7
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41b349991d0e0d6949754c804fcd1ebf16ea7ad1
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37012349"
---
# <a name="invalid-identifier"></a>無效的識別項
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                                           |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                            [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]                                             |
| 產品版本 |                                                        [!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]                                                         |
|    事件識別碼     |                                                                                     0                                                                                     |
|  事件來源   |                                                                                     0                                                                                     |
|    元件    |                                                                                     0                                                                                     |
|  符號名稱  |                                                                                     0                                                                                     |
|  訊息文字   | 「{0}"不是有效的識別項。 正在還原原始名稱。 （有效的識別碼後面接著零或多個字母或數字的字母所組成的而且不能包含空格）。 |
  
## <a name="explanation"></a>說明  
 此錯誤表示發佈結構描述不是有效的.net 識別項時定義的 web 方法。  
  
## <a name="user-action"></a>使用者動作  
 重新命名 web 方法，以有效的.net 識別項。 有效的識別碼後面接著零或多個字母或數字的字母所組成，且不得包含空格。