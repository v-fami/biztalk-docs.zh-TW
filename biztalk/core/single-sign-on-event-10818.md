---
title: "單一登入： 事件 10818 |Microsoft 文件"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ad54646-4285-42e5-a270-d56935742a95
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: be2c40fa5da46f5045b55c815be9f6f8048cda67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
---
# <a name="single-sign-on-event-10818"></a>單一登入： 事件 10818
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10818|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|ENTSSO_E_AMBIGUOUS_SYNC_FIELDS|  
|訊息文字|應用程式必須具有兩個欄位，或只有一個欄位必須標示為同步。|  
  
## <a name="explanation"></a>說明  
 如果有兩個以上的欄位，則只有唯一一個必須標示為密碼同步。  
  
## <a name="user-action"></a>使用者動作  
 若要修正這種情況，您必須刪除應用程式然後重新建立，讓應用程式遵循這些準則。