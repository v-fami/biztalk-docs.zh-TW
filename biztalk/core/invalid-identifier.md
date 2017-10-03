---
title: "無效的識別項 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f87e1e42-457f-4d04-a1d2-6b796f3fa7b7
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 148b2c2d0b2ec4fb54e15fd8cb50b5dcf0af310a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-identifier"></a>無效的識別項
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|事件識別碼|0|  
|事件來源|0|  
|元件|0|  
|符號名稱|0|  
|訊息文字|"{0}"不是有效的識別項。 正在還原原始名稱。 （有效的識別項組成字母，後面接著零或多個字母或數字和不能包含空格）。|  
  
## <a name="explanation"></a>說明  
 此錯誤表示發佈結構描述不是有效的.net 識別項時定義的 web 方法。  
  
## <a name="user-action"></a>使用者動作  
 重新命名 web 方法，以有效的.net 識別項。 有效的識別項不能包含空格，和代號，後面接零或多個字母或數字所組成。