---
title: 單一登入： 事件 10806 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 23650d6b-b6a4-4c41-96cd-476e5b0f7f63
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fd3f432a408cffcbd1ccd27508550fd0888c5213
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22277174"
---
# <a name="single-sign-on-event-10806"></a>單一登入： 事件 10806
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|企業單一登入|  
|產品版本|[!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]|  
|事件識別碼|10806|  
|事件來源|ENTSSO|  
|元件|不適用|  
|符號名稱|ENTSSO_E_APP_ASSIGNED_TO_ADAPTER|  
|訊息文字|無法刪除應用程式，因為它目前指派給配接器。|  
  
## <a name="explanation"></a>說明  
 指派給配接器時，無法刪除應用程式。  
  
## <a name="user-action"></a>使用者動作  
 取消指派從配接器，應用程式，然後再刪除它。