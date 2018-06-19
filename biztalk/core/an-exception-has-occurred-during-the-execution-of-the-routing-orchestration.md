---
title: 路由協調流程執行期間發生例外狀況 |Microsoft 文件
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 68ec8921-ba05-496e-8dcc-fd8994fcb8b7
caps.latest.revision: 8
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7e865ec091330a863cb2bab90bbafd9b891edb05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/20/2017
ms.locfileid: "22229966"
---
# <a name="an-exception-has-occurred-during-the-execution-of-the-routing-orchestration"></a>路由協調流程執行期間發生例外狀況
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|產品版本|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|事件識別碼|-|  
|事件來源|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]EDI|  
|元件|批次處理引擎|  
|符號名稱|ExceptionOccuredDuringRouting|  
|訊息文字|路由協調流程執行期間發生例外狀況。 ErrorMessage = {0}|  
  
## <a name="explanation"></a>說明  
 這個錯誤/警告/資訊事件表示，由於發生 [錯誤訊息] 欄位指出的錯誤情況，因此路由協調流程無法正確地處理每份 XML 批次元素。  
  
## <a name="user-action"></a>使用者動作  
 若要解決這個錯誤，請根據 [錯誤訊息] 欄位判斷發生的錯誤情況並解決錯誤，然後再重新提交訊息。