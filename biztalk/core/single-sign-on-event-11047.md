---
title: 單一登入： 事件 11047 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aa4eb1ae-45a6-4e0c-9af6-6bf1ed63acfb
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8f1ee4f5eaea1dac2cb2033d4585e2f89807588e
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "36991863"
---
# <a name="single-sign-on-event-11047"></a>單一登入： 事件 11047
## <a name="details"></a>詳細資料  
  
|                 |                                                                                                                                                         |
|-----------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
|  產品名稱   |                                                                企業單一登入                                                                |
| 產品版本 |                                               [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]                                                |
|    事件識別碼     |                                                                          11047                                                                          |
|  事件來源   |                                                                         ENTSSO                                                                          |
|    元件    |                                                                           不適用                                                                           |
|  符號名稱  |                                                                 SSO_ERROR_SSOSQL_FAILED                                                                 |
|  訊息文字   | 無法建立 SSOSQL。 若要修正此問題，請重新安裝 SSO 或從 Visual Studio 命令 prompt.%r 嘗試 'regasm SSOSQL.dll'<br /><br /> 錯誤碼： %1 |
  
## <a name="explanation"></a>說明  
 這可能被因安裝錯誤。  
  
## <a name="user-action"></a>使用者動作  
 若要修正此問題，請重新安裝 SSO 或從 Visual Studio 命令提示字元嘗試 'regasm SSOSQL.dll'。