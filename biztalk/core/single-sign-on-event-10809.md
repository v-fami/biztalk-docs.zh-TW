---
title: 單一登入： 事件 10809 |Microsoft Docs
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7331d12b-1000-4a60-83b3-f092968e0e51
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4d4bf5ba006af8c479abc621accdc28296c0eae3
ms.sourcegitcommit: 266308ec5c6a9d8d80ff298ee6051b4843c5d626
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37016061"
---
# <a name="single-sign-on-event-10809"></a>單一登入： 事件 10809
## <a name="details"></a>詳細資料  
  
|                 |                                                                   |
|-----------------|-------------------------------------------------------------------|
|  產品名稱   |                     企業單一登入                     |
| 產品版本 |    [!INCLUDE[btsSSOVersion](../includes/btsssoversion-md.md)]     |
|    事件識別碼     |                               10809                               |
|  事件來源   |                              ENTSSO                               |
|    元件    |                                不適用                                |
|  符號名稱  |                  ENTSSO_E_HISSO_APP_NOT_ENABLED                   |
|  訊息文字   | 應用程式未啟用主控件初始化的單一登入。 |
  
## <a name="explanation"></a>說明  
 應用程式未啟用主控件初始化的單一登入。  
  
## <a name="user-action"></a>使用者動作  
 使用系統管理工具來設定主應用程式起始單一登入。 這將會設定  
  
 在應用程式上的 SSO_FLAG_SSO_EXTERNAL_TO_WINDOWS 旗標。