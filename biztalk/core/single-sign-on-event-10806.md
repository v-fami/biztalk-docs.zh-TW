---
title: 單一登入： 事件 10806 |Microsoft Docs
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
ms.openlocfilehash: be61b0a48dde7b1c8de9ec716f4f9426c39fa0cd
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37002695"
---
# <a name="single-sign-on-event-10806"></a>單一登入： 事件 10806
## <a name="details"></a>詳細資料  
  
|                 |                                                                                   |
|-----------------|-----------------------------------------------------------------------------------|
|  產品名稱   |                             企業單一登入                             |
| 產品版本 |            [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]             |
|    事件識別碼     |                                       10806                                       |
|  事件來源   |                                      ENTSSO                                       |
|    元件    |                                        不適用                                        |
|  符號名稱  |                         ENTSSO_E_APP_ASSIGNED_TO_ADAPTER                          |
|  訊息文字   | 無法刪除應用程式，因為它目前指派給配接器。 |
  
## <a name="explanation"></a>說明  
 指派給配接器時，無法刪除應用程式。  
  
## <a name="user-action"></a>使用者動作  
 取消指派的應用程式從配接器，然後再刪除它。