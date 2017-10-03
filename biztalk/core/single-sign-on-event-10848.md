---
title: "單一登入： 事件 10848 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61888420-29a6-4c64-a884-1b074b586f21
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9511d46a43180626a31f36c9f887b0ac532e088a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10848"></a>單一登入： 事件 10848
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10848|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|ENTSSO_E_DIRECT_SYNC_NOT_ALLOWED_AMBIGUOUS|  
|訊息文字|因為欄位模稜兩可，所以不允許這個應用程式的直接密碼同步。|  
  
## <a name="explanation"></a>說明  
 如果有兩個以上的欄位，則只有唯一一個必須標示為密碼同步。  
  
## <a name="user-action"></a>使用者動作  
 若要修正這種情況，您必須刪除應用程式然後重新建立，讓應用程式遵循這些準則。