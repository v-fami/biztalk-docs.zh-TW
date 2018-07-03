---
title: 單一登入： 事件 10850 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 04e2af52-d35b-491a-a983-d80442dd6aef
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0430d5d7ea3ff2a0fabf9c9698acffe15b644f24
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37011359"
---
# <a name="single-sign-on-event-10850"></a>單一登入： 事件 10850
## <a name="details"></a>詳細資料  
  
|                 |                                                                     |
|-----------------|---------------------------------------------------------------------|
|  產品名稱   |                      企業單一登入                      |
| 產品版本 |     [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]      |
|    事件識別碼     |                                10850                                |
|  事件來源   |                               ENTSSO                                |
|    元件    |                                 不適用                                 |
|  符號名稱  |                 ENTSSO_E_ENABLED_NOT_ALLOWED_CREATE                 |
|  訊息文字   | 無法以指定的「啟用」旗標建立應用程式。 |
  
## <a name="explanation"></a>說明  
 在啟用應用程式之前，必須建立應用程式並輸入其每個欄位的欄位資訊 (例如使用者識別碼和密碼)。 無法建立已設定「已啟用」欄位的應用程式。  
  
## <a name="user-action"></a>使用者動作  
 再次建立應用程式 (使用「建立應用程式 API」或「建立新分支機構應用程式精靈」)。 當應用程式已完成且已填入欄位時，啟用應用程式。